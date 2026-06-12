---
title: "Skype (possibly QT) font behaviour varies from Terminal and GUI launch?"
date: 2009-01-27
forum: Arch and derivatives
---

### Post by lswest on 2009-01-27
Well, I've been wracking my mind about this for the past 2 days, and come up blank.  I decided I'd ask here then (and I posted this in the ArchLinux forums as well, but 2 minds, or in this case forums, are probably better than one)

My problem is this:

Skype (static build, installed using a slightly pieced together PKGBUILD) on an arch64 install is completely ugly font-wise when started from GUI (read: double-clicking the launcher in Nautilus, running it from cairo-dock, or from gmrun or gnome-do) it all results in what you can see on the right of the screenshot I have included.  I tried searching for info, but since I'm really not sure where the problem lies I was unable to find anything, forgive me if this was covered already in another thread).

If, however, I run the same launcher (symbolic link in /usr/bin to a script that just cd's to the opt directory where Skype is and executes the launcher) from a terminal, you see the nicely rendered DejaVu Serif 9px font that I want skype to be using (left Skype in screenshot).  I can go with the assumption that qtconfig has configued my qt4 toolkit fine, as it renders fine from terminal, I'm assuming it's merely one setting in the GUI that's wrong, but I have no idea where to start.  Anyone got any suggestions?

Thanks in advance,
Lswest

P.S. I use the skype static build because the bin32-skype doesn't display avatars for me, in case anyone's curious.  Also, this is the only QT app I use, I have tried QT4 Design and had no problems with it from a GUI launch, so I believe it affects only Skype for the moment.

---

### Post by smartboyathome on 2009-01-27
I am guessing you havae something in your .bashrc which fixes skype. This doesn't affect the GUI, just the terminal.

---

### Post by lswest on 2009-01-27
Thanks for the reply, I thought so too, but I don't really see what part of my .zshrc could have much of an impact on it, since most of the .zshrc is focused on making the prompt and setting up a few bindkeys.  That, and the usual that's generated when installing and setting up zsh.  Any suggestions would be welcome!

```
autoload colors; colors
autoload -U url-quote-magic
zle -N self-insert url-quote-magic

RPROMPT="%{$fg[red]%}[%{$fg[cyan]%}%* on %D%{$fg[red]%}]%{$reset_color%}" # Prompt for right side of screen

# prompt (if running screen, show window #)
if [ x$WINDOW != x ]; then
    # [5:lswest@lswest-laptop:~]% 
    export PS1="%{$fg[blue]%}[%{$fg[cyan]%}$WINDOW%{$fg[blue]%}:%{$fg[green]%}%n%{$fg[cyan]%}@%{$fg[green]%}%m%{$fg[blue]%}:%{$fg[magenta]%}%~%{$fg[blue]%}]%{$reset_color%}%# "
else
    # [lswest@lswest-laptop:~]% 
    export PS1="%{$fg[blue]%}[%{$fg[green]%}%n%{$fg[cyan]%}@%{$fg[green]%}%m%{$fg[blue]%}:%{$fg[magenta]%}%~%{$fg[blue]%}]%{$reset_color%}%# "
fi
export RPRMOPT="%{$reset_color%}"

# format titles for screen and rxvt
function title() {
  # escape '%' chars in $1, make nonprintables visible
  a=${(V)1//\%/\%\%}
 
  # Truncate command, and join lines.
  a=$(print -Pn "%40>...>$a" | tr -d "\n")
 
  case $TERM in
  screen*)
    print -Pn "\ek$a:$3\e\\" # screen title (in ^A")
    ;;
  xterm*|rxvt)
    print -Pn "\e]2;$2 | $a:$3\a" # plain xterm title
    ;;
  esac
}

# precmd is called just before the prompt is printed
function precmd() {
  title "zsh" "$USER@%m" "%55<...<%~"
}
 
# preexec is called just before any command line is executed
function preexec() {
  title "$1" "$USER@%m" "%35<...<%~"
}

# Lines configured by zsh-newuser-install
HISTFILE=~/.histfile
HISTSIZE=1000
SAVEHIST=1000
setopt extendedglob
bindkey -e
# End of lines configured by zsh-newuser-install
# The following lines were added by compinstall
zstyle :compinstall filename '/home/lswest/.zshrc'

autoload -Uz compinit
compinit
# End of lines added by compinstall

#alias
alias ls="ls -la --classify --color=always"

##Set some keybindings
###############################################
typeset -g -A key
bindkey '^?' backward-delete-char
bindkey '^[[7~' beginning-of-line
bindkey '^[[5~' up-line-or-history
bindkey '^[[3~' delete-char
bindkey '^[[8~' end-of-line
bindkey '^[[6~' down-line-or-history
bindkey '^[[A' up-line-or-search
bindkey '^[[D' backward-char
bindkey '^[[B' down-line-or-search
bindkey '^[[C' forward-char 
bindkey '^[[2~' overwrite-mode
#################################################

export LC_CTYPE="en_US.utf8"
```

---

### Post by lswest on 2009-01-29
A bit of an update:

I re-installed Arch while making a new /home partition as someone in the Arch Linux Forums suggested (he suspected some shared .config caused it), but no such luck.  The behaviour is still there, but affects the terminal launch as well, until I set LC_CTYPE="en_US.UTF8", after which it launches fine from the terminal, but no the GUI.

I added that export to /etc/profile.d/locale.sh, and refer to it in my .bash_profile now, I will see if that solves it upon reboot.  If anyone knows that this isn't going to work, please let me know what will.

Thanks in advance,
Lswest

P.S. I posted this here for reference for anyone else who might be experiencing this issue, and will edit this post as to whether or not this solved it on reboot.

*EDIT* No such luck, and it seems the locale has no affect on skype anymore, changing it from the terminal using export now has no influence on Skype...very strange

*EDIT 2* Fixed it...turns out I forgot to move /opt/skype_2.0.0.72/skype.conf to /etc/dbus-1/system.d/skype.conf

---

