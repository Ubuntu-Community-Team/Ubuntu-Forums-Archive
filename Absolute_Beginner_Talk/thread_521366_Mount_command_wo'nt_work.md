---
title: "Mount command wo'nt work"
date: 2007-08-09
forum: Absolute Beginner Talk
---

### Post by ncwalker on 2007-08-09
I am trying to set-up a NFS on a P3. I am using Ubuntu 7.04 Server on the server and Ubuntu 7.04 Desktop on the Desktop. Using the instructions at [https://help.ubuntu.com/community/SettingUpNFSHowTo](https://help.ubuntu.com/community/SettingUpNFSHowTo)

I followed the instructions and changed my /etc/exports to the following

```
/home 192.168.0.0/255.255.255.0(rw,sync)
/usr/local 192.168.0.0/255.255.255.0(rw,sync)
```

When I export the shares the terminal responds like this: 

```
exportfs: /etc/exports [2]: Neither 'subtree_check' or 'no_subtree_check' specified for export "192.168.0.0/255.255.255.0:/home".
Assuming default behaviour ('subtree_check'). 
NOTE: this default will change with nfs-utils version 1.1.0
exportfs: /etc/exports [3]: Neither 'subtree_check' or 'no_subtree_check' specified for export " 192.168.0.0/255.255.255.0:/usr/local".
Assuming default behaviour ('subtree_check').
NOTE: this default will change with nfs-utils version 1.1.0
```

Is this O.K.?

When I try to mount :

```
sudo mount 192.168.0.100:/home /home/ncwalker/networkh
```

the terminal appears to get stuck.

What can I do to make it work? 

Many thanks!

---

### Post by Cypher on 2007-08-09
On the server, type "exports" and see what is exported and how.

---

### Post by iver2435 on 2007-08-09
try this command:

```
sudo mount -t nfs 192.168.0.100:/home /home/ncwalker/networkh
```

this specifies NFS as the filesystem type to be mounted.  Don't know if that will fix it, but it's worth a try.

Also, verify that you can ping the other host.  I had some weird problems with my NFS server at home recently and it was because (for some unknown reason) I couldn't make even a low-level connection to it.  Once I figured out the issue and restored the connection, it worked just fine ( imagine that! lol )

As another suggestion, you may want to try restarting the NFS daemon.  To do so type:

```
sudo /etc/init.d/nfs-kernel-server restart
```

BTW, that stuff after the exportfs command is fine, it's not an error.

If after trying my suggestions you're still having issues, post a follow up with any terminal output.

---

### Post by ncwalker on 2007-08-09
Thanks for all the suggestions.  Here's what I've got so far:

I tried to run the command exports on the server and it says command not found (Is there a directory I should include?  (sorry :) )

If I type the command export I get a whole bunch of stuff

```
declare -x COLORTERM="gnome-terminal"
declare -x DBUS_SESSION_BUS_ADDRESS="unix:abstract=/tmp/dbus-EXmOaayZLE,guid=7525965baf7bd80a0528b80046bbafc1"
declare -x DESKTOP_SESSION="gnome"
declare -x DESKTOP_STARTUP_ID=""
declare -x DISPLAY=":0.0"
declare -x GDMSESSION="gnome"
declare -x GDM_XSERVER_LOCATION="local"
declare -x GNOME_DESKTOP_SESSION_ID="Default" 
declare -x GNOME_KEYRING_SOCKET="/tmp/keyring-ocFODW/socket"
declare -x GTK_RC_FILES="/etc/gtk/gtkrc:/home/ncwalker/.gtkrc-1.2-gnome2"
declare -x HISTCONTROL="ignoreboth"
declare -x HOME="/home/ncwalker" 
declare -x LANG="en_CA.UTF-8"
declare -x LESSCLOSE="/usr/bin/lesspipe %s %s"
declare -x LESSOPEN="| /usr/bin/lesspipe %s"
declare -x LOGNAME="ncwalker"
declare -x LS_COLORS="no=00:fi=00:di=01;34:ln=01;36:pi=40;33:so=01;35:do=01;35:bd=40;33;01:cd=40;33;01:or=40;31;01:su=37;41:sg=30;43:tw=30;42:ow=34;42:st=37;44:ex=01;32:*.tar=01;31:*.tgz=01;31:*.arj=01;31:*.taz=01;31:*.lzh=01;31:*.zip=01;31:*.z=01;31:*.Z=01;31:*.gz=01;31:*.bz2=01;31:*.deb=01;31:*.rpm=01;31:*.jar=01;31:*.jpg=01;35:*.jpeg=01;35:*.gif=01;35:*.bmp=01;35:*.pbm=01;35:*.pgm=01;35:*.ppm=01;35:*.tga=01;35:*.xbm=01;35:*.xpm=01;35:*.tif=01;35:*.tiff=01;35:*.png=01;35:*.mov=01;35:*.mpg=01;35:*.mpeg=01;35:*.avi=01;35:*.fli=01;35:*.gl=01;35:*.dl=01;35:*.xcf=01;35:*.xwd=01;35:*.flac=01;35:*.mp3=01;35:*.mpc=01;35:*.ogg=01;35:*.wav=01;35:" 
declare -x OLDPWD
declare -x PATH="/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games"
declare -x PWD="/home/ncwalker"
declare -x SESSION_MANAGER="local/bluescreen:/tmp/.ICE-unix/6115" 
declare -x SHELL="/bin/bash"
declare -x SHLVL="1"
declare -x SSH_AGENT_PID="6154"
declare -x SSH_AUTH_SOCK="/tmp/ssh-HZVKcO6115/agent.6115"
declare -x TERM="xterm" 
declare -x USER="ncwalker"
declare -x USERNAME="ncwalker"
declare -x WINDOWID="41943135"
declare -x XAUTHORITY="/home/ncwalker/.Xauthority"
```

I restarted the NFS daemon (no change)

On the client when I try the 
sudo mount -t nfs 192.168.0.100:/home /home/ncwalker/networkh it seems to get stuck still.

BTW does the directory networkh need to exist on the client already?  I created it but I wasn't sure if I was supposed to.

The ping idea brings up a problem from the server I can successfully ping the router, an XP machine I haven't even dealt with yet, and the client in question but on the client I can only ping the router, the XP machine, but not the server.  How would I follow up with that?

---

### Post by ncwalker on 2007-08-09
I got it.

A friend suggested looking at firewall settings onthe server and sure enough.  The firewall is blocking everything.  That's why it isn't working.

O.K. new question.

I am running webmin ver. 1.350 and the firewall options are as follows: 

Allow all traffic
Do network address translation on external interface eth0
Block all incoming connections on external interface eth0
Block all except SSH and IDENT on external interface eth0
Block all except SSH and IDENT ping and high ports on interface eth0

which one should I choose?

Thanks for the help !

Another question how do you mark a thread that is solved?

---

