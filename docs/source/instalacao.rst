------------
 Instalação
------------

Esta ferramenta foi desenvolvida em Python 3.7, faz uso de algumas bibliotecas
de terceiros, e acessa bancos ORACLE e Access (mdb). Logo, os seguintes
requisitos devem ser instalados previamente, e os respectivos diretórios de
binários devem ser inseridos na variável de ambiente *PATH*:

  - `Python 3.7+ amd64`_
  - `Microsoft Access Database Engine 2016 x64`_
  - `Visual C++ Redistributable for Visual Studio 2015-2019`_ (vcredist140)
  - `Oracle Instant Client Basic 19.3`_

.. _Python 3.7+ amd64: https://www.python.org/downloads/
.. _Microsoft Access Database Engine 2016 x64: https://www.microsoft.com/en-us/download/details.aspx?id=54920
.. _Visual C++ Redistributable for Visual Studio 2015-2019: https://www.microsoft.com/en-us/download/details.aspx?id=48145
.. _Oracle Instant Client Basic 19.3: https://download.oracle.com/otn_software/nt/instantclient/19300/instantclient-basiclite-windows.x64-19.3.0.0.0dbru.zip

O módulo de importação de dados, em particular, foi desenvolvido em C++ e os
binários foram compilados para Windows (x86).

A distribuição do BIAT está sendo feita no formato *wheel*, com todas as
bibliotecas sendo disponibilizadas localmente para dispensar acesso à internet.
Aconselha-se instalar o pacote em um ambiente virtual a fim de isolar a
instalação de outros projetos que usem estas mesmas bibliotecas mas em outras
versões. Para criá-lo, executar os seguintes comandos no terminal::

    # Diretório onde estão as bibliotecas formato whl
    set wheels=c:\Users\biat\wheels

    # Instalação do módulo de criação de ambiente virtual
    python -m pip install virtualenv -f %wheels%

    # Criação do ambiente virtual
    python -m virtualenv --no-download -p caminho_pasta_python\python.exe venv

    # Ativação do ambiente virtual
    venv\Scripts\activate

Para instalação das dependências::

    pip install shapely -f %wheels% --no-index --compile
    pip install cosmos-osm -f %wheels% --compile

Instalação do BIAT::

    pip install biat -f %wheels% --compile

Criação de atalho para a interface gráfica::

    mklink biat-gui.exe venv\Scripts\biat-gui.exe
