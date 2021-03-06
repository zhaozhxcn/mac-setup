# Zsh

We'll install `zsh` for all the features offered by `oh-my-zsh`. The installation and usage is really intutive. The `Env.sh` is a config file we maintain so as to not pollute the `~/.zshrc` too much. `Env.sh` holds aliases, exports, path changes etc.

### Zsh

Install zsh and zsh completions using homebrew

        brew install zsh zsh-completions

Install oh-my-zsh on top of zsh to getting additional functionality

        curl -L https://github.com/robbyrussell/oh-my-zsh/raw/master/tools/install.sh | sh

edit the `.zshrc` by opening the file in a text editor

        ZSH_THEME=pygmalion
        alias zshconfig="subl ~/.zshrc"
        alias envconfig="subl ~/Projects/config/env.sh"
        plugins=(git colored-man colorize github jira vagrant virtualenv pip python brew osx zsh-syntax-highlighting)

### Env.sh
~~~
    #!/bin/zsh

    # PATH
    export PATH="/usr/local/share/python:/usr/local/bin:/usr/bin:/bin:/usr/sbin:/sbin"
    export EDITOR='subl -w'
    # export PYTHONPATH=$PYTHONPATH
    # export MANPATH="/usr/local/man:$MANPATH"

    # Virtual Environment
    export WORKON_HOME=$HOME/.virtualenvs
    export PROJECT_HOME=$HOME/Projects
    source /usr/local/bin/virtualenvwrapper.sh

    # Owner
    export USER_NAME="YOUR NAME"
    eval "$(rbenv init -)"

    # FileSearch
    function f() { find . -iname "*$1*" ${@:2} }
    function r() { grep "$1" ${@:2} -R . }

    #mkdir and cd
    function mkcd() { mkdir -p "$@" && cd "$_"; }

    # Aliases
    alias cppcompile='c++ -std=c++11 -stdlib=libc++'
    alias portfolio='cd ~/Projects/portfolio'
~~~