---
title: "No inicia sesión ubuntu luego de modificar .bashc"
date: 2015-04-06
forum: Argentina Team
---

### Post by ruben19 on 2015-04-06
Hola gente!! Soy novato en Ubuntu y quise probar los "alias" ya que estoy haciendo un Tp para la facu y repetía muchos comando en el terminal. Leí el pequeño tutorial de la siguiente pagina:

[http://felinfo.blogspot.com.ar/2011/12/creacion-y-uso-de-alias-de-comandos.html](http://felinfo.blogspot.com.ar/2011/12/creacion-y-uso-de-alias-de-comandos.html)

y salio todo perfecto, hasta que se me ocurrió modificar el archivo ".bashrc" para que mis alias estén siempre que inicie sesión. El problema es que luego de modificarlo con el comando "nano" y guardarlo, cerré el terminal y lo abrí nuevamente pero el terminal estaba vacío, no promp, NADA!! si escribia algo al ratito saltaba un error muy rapido y se cerraba el terminal.

Luego reinicie la compu, pensando que era solamente un error del sistema, pero al querer loguearme se pone negra la pantalla y vuelve a la pantalla de bloqueo pidiendo mi contraseña. Solamente puedo ingresar como invitado pero no puedo llegar a mis archivos. Leí en algunos lugares que apretar CTRL + ALT + F1 y loguearse en modo texto, pero no puedo hacerlo, ingreso pero un error aparece rápido y vuelve a pedirme mi usuario y contraseña. Pude filmar el error y acá subo una imagen:

[http://www.subeimagenes.com/img/error-1273877.html](http://www.subeimagenes.com/img/error-1273877.html)

Según lo que se ve es: "-bash: xmalloc: ../.././builtins/evalfile.c:162: no se pueden asignar 2798619 bytes (2910130176 bytes asignados)"

Luego de esto me pide nuevamente usuario y contraseña, ocurriendo siempre lo mismo.

Ya trate de ingresar en modo recuperación , que permite ingresar a modo texto en modo root, pero no se que podría hacer desde ahí.

Ojala puedan ayudarme, por que tengo que entregar un trabajo para esta semana y no puedo por lo menos extraer mis documentos. Saludos y un abrazo grande

---

### Post by gmunioz on 2015-04-08
Ingresa en modo recuperación.
Selecciona network -- root
En la terminal ejecuta:
> apt-get update
apt-get dist-upgrade
apt-get install mc
mc

Iniciará Midnight Commander, un administrador de archivos
en modo semigráfico.
Navega hasta /home/tu_usuario/ y elimina el archivo .bashrc con F8
Si el que editaste es el principal, navega hasta /etc/skel y edítalo con F4, seleccionando nano como editor
Este es su contenido original:

> # ~/.bashrc: executed by bash(1) for non-login shells.
# see /usr/share/doc/bash/examples/startup-files (in the package bash-doc)
# for examples

# If not running interactively, don't do anything
case $- in
    *i*) ;;
      *) return;;
esac

# don't put duplicate lines or lines starting with space in the history.
# See bash(1) for more options
HISTCONTROL=ignoreboth

# append to the history file, don't overwrite it
shopt -s histappend

# for setting history length see HISTSIZE and HISTFILESIZE in bash(1)
HISTSIZE=1000
HISTFILESIZE=2000

# check the window size after each command and, if necessary,
# update the values of LINES and COLUMNS.
shopt -s checkwinsize

# If set, the pattern "**" used in a pathname expansion context will
# match all files and zero or more directories and subdirectories.
#shopt -s globstar

# make less more friendly for non-text input files, see lesspipe(1)
[ -x /usr/bin/lesspipe ] && eval "$(SHELL=/bin/sh lesspipe)"

# set variable identifying the chroot you work in (used in the prompt below)
if [ -z "${debian_chroot:-}" ] && [ -r /etc/debian_chroot ]; then
    debian_chroot=$(cat /etc/debian_chroot)
fi

# set a fancy prompt (non-color, unless we know we "want" color)
case "$TERM" in
    xterm-color) color_prompt=yes;;
esac

# uncomment for a colored prompt, if the terminal has the capability; turned
# off by default to not distract the user: the focus in a terminal window
# should be on the output of commands, not on the prompt
#force_color_prompt=yes

if [ -n "$force_color_prompt" ]; then
    if [ -x /usr/bin/tput ] && tput setaf 1 >&/dev/null; then
	# We have color support; assume it's compliant with Ecma-48
	# (ISO/IEC-6429). (Lack of such support is extremely rare, and such
	# a case would tend to support setf rather than setaf.)
	color_prompt=yes
    else
	color_prompt=
    fi
fi

if [ "$color_prompt" = yes ]; then
    PS1='${debian_chroot:+($debian_chroot)}\[\033[01;32m\]\u@\h\[\033[00m\]:\[\033[01;34m\]\w\[\033[00m\]\$ '
else
    PS1='${debian_chroot:+($debian_chroot)}\u@\h:\w\$ '
fi
unset color_prompt force_color_prompt

# If this is an xterm set the title to user@host:dir
case "$TERM" in
xterm*|rxvt*)
    PS1="\[\e]0;${debian_chroot:+($debian_chroot)}\u@\h: \w\a\]$PS1"
    ;;
*)
    ;;
esac

# enable color support of ls and also add handy aliases
if [ -x /usr/bin/dircolors ]; then
    test -r ~/.dircolors && eval "$(dircolors -b ~/.dircolors)" || eval "$(dircolors -b)"
    alias ls='ls --color=auto'
    #alias dir='dir --color=auto'
    #alias vdir='vdir --color=auto'

    alias grep='grep --color=auto'
    alias fgrep='fgrep --color=auto'
    alias egrep='egrep --color=auto'
fi

# colored GCC warnings and errors
#export GCC_COLORS='error=01;31:warning=01;35:note=01;36:caret=01;32:locus=01:quote=01'

# some more ls aliases
alias ll='ls -alF'
alias la='ls -A'
alias l='ls -CF'

# Add an "alert" alias for long running commands.  Use like so:
#   sleep 10; alert
alias alert='notify-send --urgency=low -i "$([ $? = 0 ] && echo terminal || echo error)" "$(history|tail -n1|sed -e '\''s/^\s*[0-9]\+\s*//;s/[;&|]\s*alert$//'\'')"'

# Alias definitions.
# You may want to put all your additions into a separate file like
# ~/.bash_aliases, instead of adding them here directly.
# See /usr/share/doc/bash-doc/examples in the bash-doc package.

if [ -f ~/.bash_aliases ]; then
    . ~/.bash_aliases
fi

# enable programmable completion features (you don't need to enable
# this, if it's already enabled in /etc/bash.bashrc and /etc/profile
# sources /etc/bash.bashrc).
if ! shopt -oq posix; then
  if [ -f /usr/share/bash-completion/bash_completion ]; then
    . /usr/share/bash-completion/bash_completion
  elif [ -f /etc/bash_completion ]; then
    . /etc/bash_completion
  fi
fi


---

