---
title: "help with shared objects"
date: 2007-07-25
forum: Absolute Beginner Talk
---

### Post by rbprogrammer on 2007-07-25
is there a way to have my own directory with my custom shared objects in it??

for example, i have a folder [FONT="Courier New"]/home/hbin[/FONT] for all my programs that i installed manually. or pretty much any program that i wrote myself.  then in [FONT="Courier New"]/home/username/.profile[/FONT] i had put: ```

# set PATH so it includes home bin if it exists
if [ -d /home/hbin ] ; then
    PATH=/home/hbin:"${PATH}"
fi

```
this allows me to have a folder that contains my binaries so at the terminal i just have to type the name of the file, not the absolute path.

i want kind of the same thing for my shared objects.  i went to [http://www.ibm.com/developerworks/library/l-shobj/](http://www.ibm.com/developerworks/library/l-shobj/) and i found out how to make shared objects, now i want to be able to put them in [FONT="Courier New"]/home/hlib[/FONT], so that programs can open them without me having to put them in [FONT="Courier New"]/lib, /usr/lib, etc..[/FONT]

any help is appreciated :) ..

---

### Post by pmg on 2007-07-26
Do you want these shared objects to be used by anyone on the system, or do you want to control it by userid.  If you want to set it up by userid, add the path to the environment variable **LD_LIBRARY_PATH**.  Multiple directories are separated by : just like with **PATH**.

If you want to set it up for the whole system to see/use, create a file in /etc/ld.so.conf.d/ and put the absolute path to the directory in it.  If you have multiple directories you want to include, put one per line.  Then run the command **sudo /sbin/ldconfig** which will rebuild dynamic linker cache "/etc/ld.so.cache" to include the new directories.

For more details look at **man ldconfig** and **man ld.so**.

---

### Post by rbprogrammer on 2007-07-30
everytime i use:
```
export LD_LIBRARY_PATH=.:$LD_LIBRARY_PATH
```
the program works flawlessly, but when i exit the terminal session the [FONT="Courier New"]LD_LIBRARY_PATH[/FONT] is deleted

ie:
before:
```
$ export
declare -x COLORTERM=""
declare -x DBUS_SESSION_BUS_ADDRESS="unix:abstract=/tmp/dbus-130G1YkMJw,guid=eb0cf21dd48d5b9bc396830046ad77fa"
declare -x DESKTOP_SESSION="default"
declare -x DISPLAY=":0.0"
declare -x DM_CONTROL="/var/run/xdmctl"
declare -x GS_LIB="/home/mike/.fonts"
declare -x GTK2_RC_FILES="/home/mike/.gtkrc-2.0-kde:/home/mike/.kde/share/config/gtkrc-2.0"
declare -x GTK_RC_FILES="/etc/gtk/gtkrc:/home/mike/.gtkrc:/home/mike/.kde/share/config/gtkrc"
declare -x HISTCONTROL="ignoreboth"
declare -x HOME="/home/mike"
declare -x KDE_FULL_SESSION="true"
declare -x KDE_MULTIHEAD="false"
declare -x KONSOLE_DCOP="DCOPRef(konsole-14943,konsole)"
declare -x KONSOLE_DCOP_SESSION="DCOPRef(konsole-14943,session-1)"
declare -x LANG="en_US.UTF-8"
declare -x **LD_LIBRARY_PATH**=".:"
declare -x LESSCLOSE="/usr/bin/lesspipe %s %s"
declare -x LESSOPEN="| /usr/bin/lesspipe %s"
declare -x LOGNAME="mike"
declare -x LS_COLORS="no=00:fi=00:di=01;34:ln=01;36:pi=40;33:so=01;35:do=01;35:bd=40;33;01:cd=40;33;01:or=40;31;01:su=37;41:sg=30;43:tw=30;42:ow=34;42:st=37;44:ex=01;32:*.tar=01;31:*.tgz=01;31:*.arj=01;31:*.taz=01;31:*.lzh=01;31:*.zip=01;31:*.z=01;31:*.Z=01;31:*.gz=01;31:*.bz2=01;31:*.deb=01;31:*.rpm=01;31:*.jar=01;31:*.jpg=01;35:*.jpeg=01;35:*.gif=01;35:*.bmp=01;35:*.pbm=01;35:*.pgm=01;35:*.ppm=01;35:*.tga=01;35:*.xbm=01;35:*.xpm=01;35:*.tif=01;35:*.tiff=01;35:*.png=01;35:*.mov=01;35:*.mpg=01;35:*.mpeg=01;35:*.avi=01;35:*.fli=01;35:*.gl=01;35:*.dl=01;35:*.xcf=01;35:*.xwd=01;35:*.flac=01;35:*.mp3=01;35:*.mpc=01;35:*.ogg=01;35:*.wav=01;35:"
declare -x OLDPWD
declare -x PATH="/home/hbin:/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games"
declare -x PWD="/home/mike/Desktop/SharedObject"
declare -x SESSION_MANAGER="local/mwd5025:/tmp/.ICE-unix/5519"
declare -x SHELL="/bin/bash"
declare -x SHLVL="1"
declare -x SSH_AGENT_PID="5464"
declare -x SSH_AUTH_SOCK="/tmp/ssh-OKvbxG5425/agent.5425"
declare -x TERM="xterm"
declare -x USER="mike"
declare -x WINDOWID="58720263"
declare -x XCURSOR_THEME="kubuntu"
declare -x XDM_MANAGED="/var/run/xdmctl/xdmctl-:0,maysd,mayfn,sched,rsvd,method=classic"

```
after closing that terminal then opening another, i get:
```
$ export
declare -x COLORTERM=""
declare -x DBUS_SESSION_BUS_ADDRESS="unix:abstract=/tmp/dbus-130G1YkMJw,guid=eb0cf21dd48d5b9bc396830046ad77fa"
declare -x DESKTOP_SESSION="default"
declare -x DISPLAY=":0.0"
declare -x DM_CONTROL="/var/run/xdmctl"
declare -x GS_LIB="/home/mike/.fonts"
declare -x GTK2_RC_FILES="/home/mike/.gtkrc-2.0-kde:/home/mike/.kde/share/config/gtkrc-2.0"
declare -x GTK_RC_FILES="/etc/gtk/gtkrc:/home/mike/.gtkrc:/home/mike/.kde/share/config/gtkrc"
declare -x HISTCONTROL="ignoreboth"
declare -x HOME="/home/mike"
declare -x KDE_FULL_SESSION="true"
declare -x KDE_MULTIHEAD="false"
declare -x KONSOLE_DCOP="DCOPRef(konsole-15040,konsole)"
declare -x KONSOLE_DCOP_SESSION="DCOPRef(konsole-15040,session-1)"
declare -x LANG="en_US.UTF-8"
declare -x LESSCLOSE="/usr/bin/lesspipe %s %s"
declare -x LESSOPEN="| /usr/bin/lesspipe %s"
declare -x LOGNAME="mike"
declare -x LS_COLORS="no=00:fi=00:di=01;34:ln=01;36:pi=40;33:so=01;35:do=01;35:bd=40;33;01:cd=40;33;01:or=40;31;01:su=37;41:sg=30;43:tw=30;42:ow=34;42:st=37;44:ex=01;32:*.tar=01;31:*.tgz=01;31:*.arj=01;31:*.taz=01;31:*.lzh=01;31:*.zip=01;31:*.z=01;31:*.Z=01;31:*.gz=01;31:*.bz2=01;31:*.deb=01;31:*.rpm=01;31:*.jar=01;31:*.jpg=01;35:*.jpeg=01;35:*.gif=01;35:*.bmp=01;35:*.pbm=01;35:*.pgm=01;35:*.ppm=01;35:*.tga=01;35:*.xbm=01;35:*.xpm=01;35:*.tif=01;35:*.tiff=01;35:*.png=01;35:*.mov=01;35:*.mpg=01;35:*.mpeg=01;35:*.avi=01;35:*.fli=01;35:*.gl=01;35:*.dl=01;35:*.xcf=01;35:*.xwd=01;35:*.flac=01;35:*.mp3=01;35:*.mpc=01;35:*.ogg=01;35:*.wav=01;35:"
declare -x OLDPWD
declare -x PATH="/home/hbin:/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games"
declare -x PWD="/home/mike"
declare -x SESSION_MANAGER="local/mwd5025:/tmp/.ICE-unix/5519"
declare -x SHELL="/bin/bash"
declare -x SHLVL="1"
declare -x SSH_AGENT_PID="5464"
declare -x SSH_AUTH_SOCK="/tmp/ssh-OKvbxG5425/agent.5425"
declare -x TERM="xterm"
declare -x USER="mike"
declare -x WINDOWID="58720263"
declare -x XCURSOR_THEME="kubuntu"
declare -x XDM_MANAGED="/var/run/xdmctl/xdmctl-:0,maysd,mayfn,sched,rsvd,method=classic"

```

---

### Post by pmg on 2007-07-31
> **rbprogrammer said:**
> ...the program works flawlessly, but when i exit the terminal session the [FONT="Courier New"]LD_LIBRARY_PATH[/FONT] is deleted

**LD_LIBRARY_PATH** is an environment variable just like **PATH**.  You'll need to set it just like you do **PATH** in your .profile file.

I would also recommend not using . in LD_LIBRARY_PATH, for the same reason it's bad to have it in PATH, which is it might be possible for you to run some code you don't intend to, by being in a directory with something in it you didn't know of.  It's less likely to happen here then with PATH, but it's still a significant security exposure.

---

