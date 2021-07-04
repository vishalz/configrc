
# Install Packages

1. build essential and cmake 
1. zsh and antigen 
1. tmux
1. vim and vundle 
1. git
1. vscode


## Install software from Ubuntu repositroies

```bash

    sudo apt update 
    sudo apt upgrade -y 
    sudo apt install build-essential cmake 
    sudo apt install curl wget vim-gtk git tmux htop tree
    sudo apt install jq 
    sudo snap install code --classic 
    
```

## Setup zsh for user

### Install antigen and set zsh as user's default shell

```bash

    cd ~
    sudo apt install zsh
    su - ${USER}
    curl -L git.io/antigen > antigen.zsh
    touch ~/.zshrc 
    chsh -s $(which zsh) 
    
```

### Copy following into ~/.zshrc

```bash
    # set vim as EDITOR
    export EDITOR=vim

    # set caps key to escape for vim
    setxkbmap -option caps:escape

    # Load Antigen
    source  ~/antigen.zsh

    # Load Antigen configurations
    antigen init ~/.antigenrc

    #Fix for vim lightline 
    export TERM=xterm-256color
    

```

### Configure anitgen plugins

Add following to the ~/.antigenrc

```bash
    # Load oh-my-zsh library.
    antigen use oh-my-zsh

    # Load bundles from the default repo (oh-my-zsh).
    antigen bundle vi-mode
    antigen bundle git
    antigen bundle command-not-found
    antigen bundle history-substring-search
    antigen bundle history


    # Load bundles from external repos.
    antigen bundle zsh-users/zsh-completions
    antigen bundle zsh-users/zsh-autosuggestions
    antigen bundle zsh-users/zsh-syntax-highlighting

    # Select theme
    antigen theme robbyrussell

    # Tell Antigen that you're done.
    antigen apply
```

### Log out and log back in or

```bash

    su - ${USER}

```

## Tmux set up

```bash

      bind P paste-buffer 
      bind-key -T copy-mode-vi v send-keys -X begin-slection
      bind-key -T copy-mode-vi y send-keys -X copy-slection
      bind-key -T copy-mode-vi r send-keys -X rectangle-toggle

```

## vim setup

### Intall and setup vundle for vim

1. Clone vundle

```bash
  git clone https://github.com/VundleVim/Vundle.vim.git ~/.vim/bundle/Vundle.vim

```

### Copy Following into ~/.vimrc

```bash
  " vundle setup begin
    set nocompatible              " be iMproved, required
    filetype off                  " required

    " set the runtime path to include Vundle and initialize
    set rtp+=~/.vim/bundle/Vundle.vim

    call vundle#begin('~/.vim/bundle/')

    " let Vundle manage Vundle, required
    Plugin 'VundleVim/Vundle.vim'

    " Install other plugins
    Plugin 'ycm-core/YouCompleteMe'
    Plugin 'altercation/vim-colors-solarized'
    Plugin 'itchyny/lightline.vim'
    "Plugin 'plasticboy/vim-markdown'
    Plugin 'preservim/nerdtree' 

    " The following are examples of different formats supported.
    " Keep Plugin commands between vundle#begin/end.

    " All of your Plugins must be added before the following line
    call vundle#end()            " required
    filetype plugin indent on    " required

    " To ignore plugin indent changes, instead use:
    "filetype plugin on
    "
    " Brief help
    " :PluginList       - lists configured plugins
    " :PluginInstall    - installs plugins; append `!` to update or just :PluginUpdate
    " :PluginSearch foo - searches for foo; append `!` to refresh local cache
    " :PluginClean      - confirms removal of unused plugins; append `!` to auto-approve removal
    "
    " see :h vundle for more details or wiki for FAQ
    " Put your non-Plugin stuff after this line


    " vundle setup end

    "You Complete Me Configuration begin
    let g:ycm_autoclose_preview_window_after_completion = 1


    "You Complete Me Configuration end


    "vim colors solarized configuration start 
    syntax enable
    if has('gui_running')
        set background=light
    else
        set background=dark
    endif
    colorscheme solarized

    "vim colors solarized configuration end 


    "disable search highlighting
    set nohlsearch

    "display line numbers
    set number

    "enable vim syntax colors option
    syntax on

    "enable file type detection and indentation
    filetype plugin indent on

    "replace tabs with spaces
    set tabstop=2
    set shiftwidth=2
    set softtabstop=2
    set expandtab

    " disable auto highlighting of Matched Parentheses
    let g:loaded_matchparen=1

    " split to right 
    " set splitright


    "Enable clipboard
    set clipboard=unnamedplus

    "fix for vim lightline
    set laststatus=2
    set noshowmode
    let g:lightline = {'colorscheme': 'solarized'}

    "vim gdb support 
    let g:termdebug_popup = 0
    let g:termdebug_wide = 163
    
    " Nerdtree mappings 
    nnoremap <C-t> :NERDTreeToggle<CR>

```

## Configure git global settings

```bash

  git config --global user.email "youreamil@email.com" 
  git config --global user.name  "your name"
  git config --global credential.helper cache
  git config --global credential.helper 'cache --timeout 7200`
  git config --global color.ui auto 
  git config --global core.editor vim 
  git config --global core.pager 'less -FRX'

```

