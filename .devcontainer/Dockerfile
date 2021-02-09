FROM amazonlinux
## SYSTEM SETUP
RUN yum update -y
RUN yum groupinstall "Development Tools" -y
RUN yum install -y wget
## AWS CLI
RUN wget --quiet "https://awscli.amazonaws.com/awscli-exe-linux-x86_64.zip" -O ~/awscliv2.zip \
    && unzip ~/awscliv2.zip \
    && ./aws/install \
    && aws --version \
    && rm aws/install \
    && rm ~/awscliv2.zip
## Parallel 
RUN wget --quiet "https://ftpmirror.gnu.org/parallel/parallel-20200222.tar.bz2" -O ~/parallel-20200222.tar.bz2 \
    && bzip2 -dc ~/parallel-20200222.tar.bz2 | tar xvf - \
    && cd parallel-20200222 \
    && ./configure && make && make install \
    && rm -rf parallel-20200222 \
    && rm ~/parallel-20200222.tar.bz2
## VSCODE USER Setup
RUN adduser vscode 
RUN usermod -aG wheel vscode
USER vscode
## VSCODE USER Conda install
RUN wget --quiet "https://repo.anaconda.com/miniconda/Miniconda3-latest-Linux-x86_64.sh" -O ~/conda.sh \
    && bash ~/conda.sh -b -p ~/conda \
    && echo ". ~/conda/etc/profile.d/conda.sh" >> ~/.bashrc \
    && echo "conda activate base" >> ~/.bashrc \
    && rm ~/conda.sh

