# FROM --platform=linux/amd64 mcr.microsoft.com/devcontainers/cpp:0-debian-11
FROM --platform=linux/amd64 ubuntu:20.04
# ARG base_img=ubuntu:18.04
# FROM --platform=linux/arm64 ${base_img} 

ARG DEBIAN_FRONTEND=noninteractive
ENV HOME /root

SHELL ["/bin/bash", "-c"]

# ARG REINSTALL_CMAKE_VERSION_FROM_SOURCE="none"

# # Optionally install the cmake for vcpkg
# COPY ./reinstall-cmake.sh /tmp/

# RUN if [ "${REINSTALL_CMAKE_VERSION_FROM_SOURCE}" != "none" ]; then \
#         chmod +x /tmp/reinstall-cmake.sh && /tmp/reinstall-cmake.sh ${REINSTALL_CMAKE_VERSION_FROM_SOURCE}; \
#     fi \
#     && rm -f /tmp/reinstall-cmake.sh

# # Optional args
# ARG cuda=0
# #ARG uid=1001
# #ARG gid=1000
# ARG ostype=Linux
# # ARG pyro_git_url=https://github.com/pyro-ppl/pyro.git

# # # Configurable settings
# #ENV USER_NAME pyromancer
# ENV CONDA_DIR /opt/conda
# ENV WORK_DIR /home/${USER_NAME}/workspace
# ENV PATH ${CONDA_DIR}/bin:${PATH}

# Install linux utils
RUN apt-get update && apt-get install -y --no-install-recommends \
         build-essential \
         clang \
         cmake \
         git \
         gdb \
         wget \
         iputils-ping \
         ca-certificates && \
    rm -rf /var/lib/apt/lists/*

RUN cd ${HOME} && \
    wget --no-check-certificate --quiet \
        https://boostorg.jfrog.io/artifactory/main/release/1.82.0/source/boost_1_82_0.tar.gz && \
        tar xzf ./boost_1_82_0.tar.gz && \
        cd ./boost_1_82_0 && \
        ./bootstrap.sh && \
        ./b2 install && \
        cd .. && \
        rm -rf ./boost_1_82_0

# # Change to default user
# RUN bash -c 'if [ ${ostype} == Linux ]; then groupadd -r --gid ${gid} ${USER_NAME}; fi && \
#      useradd -r --create-home --shell /bin/bash --uid ${uid} --gid ${gid} ${USER_NAME}' && \
#      mkdir -p ${CONDA_DIR} ${WORK_DIR} && chown ${USER_NAME} ${CONDA_DIR} ${WORK_DIR}
# USER ${USER_NAME}

# RUN bash -c 'useradd -r --create-home --shell /bin/bash --uid ${uid} --gid ${gid} ${USER_NAME}' && \
#      mkdir -p ${CONDA_DIR} ${WORK_DIR} && chown ${USER_NAME} ${CONDA_DIR} ${WORK_DIR}
# USER ${USER_NAME}

# Install conda
# RUN wget -O ~/miniconda.sh \
#     https://repo.continuum.io/miniconda/Miniconda${python_version%%.*}-latest-Linux-x86_64.sh && \ 
# RUN wget -O ~/miniconda.sh \ 
#     https://repo.anaconda.com/miniconda/Miniconda3-latest-MacOSX-arm64.sh && \
#     bash ~/miniconda.sh -f -b -p ${CONDA_DIR} && \
#     rm ~/miniconda.sh && \
#     conda install python3

# CMD ["sudo ln -s md5sum /bin/md5"]
# CMD ["chmod +x Miniconda3-latest-MacOSX-arm64.sh"]
# CMD ["./Miniconda3-latest-MacOSX-arm64.sh -b -p $HOME/miniconda3 -b"]
# ENV PATH=/$HOME/miniconda3/bin:$PATH
# CMD ["conda update -y conda"]
# RUN rm Miniconda3-latest-MacOSX-arm64.sh

# # Move to home directory; and copy the install script
# WORKDIR ${WORK_DIR}
# # COPY install.sh ${WORK_DIR}/install.sh

# # Install python 2/3, PyTorch and Pyro
# RUN cd ${WORK_DIR} && conda update -n base conda -c defaults && bash install.sh

# # Run Jupyter notebook
# (Ref: http://jupyter-notebook.readthedocs.io/en/latest/public_server.html#docker-cmd)
# EXPOSE 8888
# CMD ["jupyter", "notebook", "--port=8888", "--no-browser", "--ip=0.0.0.0"]








# # https://mjtdev.medium.com/how-to-conda-miniconda-anaconda-in-docker-in-2022-5579cafc44fd
# RUN mkdir -p /opt/conda
# RUN wget https://repo.anaconda.com/miniconda/Miniconda3-latest-Linux-x86_64.sh -O /opt/conda/miniconda.sh && bash /opt/conda/miniconda.sh -b -u -p /opt/miniconda
# RUN rm -rf /opt/conda/miniconda.sh

# Run the software in conda base environment 
# CMD ["/opt/miniconda/bin/conda", "run", "--no-capture-output", "-n", "base", "python" "app.py"]
#/opt/conda/bin/conda init bash



# [Optional] Uncomment this section to install additional vcpkg ports.
# RUN su vscode -c "${VCPKG_ROOT}/vcpkg install boost"

# [Optional] Uncomment this section to install additional packages.
# RUN apt-get update && export DEBIAN_FRONTEND=noninteractive \
#     && apt-get -y install --no-install-recommends <your-package-list-here>


# Once ready to productionize run 
# conda env export > environment.yml
# SHELL ["/opt/miniconda/bin/conda", "run", "--no-capture-output", "-n", "base", "/bin/bash", "-c"]
# SHELL ["/bin/bash","-l", "-c"]

# ENV PATH /opt/miniconda/bin:$PATH 

# RUN conda init bash && \
#     conda config --add channels jolespin && \
#     conda config --add channels bioconda && \
#     conda config --add channels conda-forge && \
#     conda update conda -y && \
#     # conda install -c conda-forge mamba -y && \
#     conda clean -afy




# And uncomment the following:
# COPY .devcontainer/environment.yml /tmp 
#RUN conda create --name test-env
# RUN . /opt/miniconda/bin/activate && conda env update --name base --file /tmp/environment.yml
#RUN . /opt/miniconda/bin/activate && conda env update --name test-env --file /tmp/environment.yml
# RUN conda env create -f /tmp/environment.yml
# RUN . /opt/miniconda/bin/activate && conda env create -f /tmp/environment.yml

# RUN echo "source activate" > ~/.bashrc
# RUN echo "conda init && conda activate test-env" >> ~/.bashrc
# ENTRYPOINT ["bash", "-l", "-c"]


