---
title: "new ubuntu server, help"
date: 2007-04-12
forum: Absolute Beginner Talk
---

### Post by mishkin on 2007-04-12
I"m 100% new to linux and ubuntu, previously I had a windows server with remote desktop

I have login details for ssh, I downloaded putty and ran it logged in but now have no idea what to do next.

Could someone run me through the steps to install a program simular to remote desktop so I can see the graphicalness of ubuntu and go from there.

Thanks

---

### Post by annda on 2007-04-12
i think we need a few more details. am i right that you installed ubuntu server edition and are trying to access it from windows?

in that case there is no graphical desktop. you need to install a window manager first.

---

### Post by mishkin on 2007-04-12
I didn't install it myself, the people at layeredtech did

and yes I'm trying from windows xp

I want to be able to control it simular to how I'd control a windows 2003 server with remote desktop

---

### Post by annda on 2007-04-12
hmm, i don't know how the layeredtech guys do it and what they installed. you definitely need to use their support.

if they gave you only ssh login data, you probably have a barebone server. you can upload files etc. i suppose you have apache & co. installed but no desktop.

if you just want to see what ubuntu is like, download the [live cd]("http://www.ubuntu.com/getubuntu/download") and try it out. you don't have to install anything to try ubuntu.

---

### Post by mishkin on 2007-04-12
I already tryed out the live cd...

I can't exactly just forget about the server it's paid for the month

theres gotta be a way to install that stuff I need

---

### Post by FuriousLettuce on 2007-04-12
You will have a command-line only server. You will be able to access it through ssh (if you need to transfer files over as if it were a webserver, google WinSCP). 

If you want more specific information, you need to tell us more (e.g., do you physically own the server or is it remote, is it a file/web/XYZ server?, what will you use it for?)

---

### Post by mishkin on 2007-04-12
I don't pysically own it I'm in Canada It's in texas

I plan to use it to upload torrents at private trackers

---

### Post by FuriousLettuce on 2007-04-12
So have you been given a web address for it (eg. xyz.com). In which case, you can use WinSCP to upload the files, and you'll have to create a simple FTP setup / HTML page so that people can access the torrent files. I think that you're probably asking in the wrong place - it's not Ubuntu specific information you need, you'd be best off asking the people you're leasing the server from. 

Just so you know, it's unlikely you'll get a graphical interface like you would on Remote Desktop

---

### Post by annda on 2007-04-12
when you log in, you should be able to install stuff, unless there are some restrictions that layeredtech put there.

a good guide is here:
[http://www.psychocats.net/ubuntu/installingsoftware](http://www.psychocats.net/ubuntu/installingsoftware)

---

### Post by mishkin on 2007-04-12
no web address

If I can get something where I can see the gnome desktop I can install a ftp server and wine with utorrent... I don't need a website to distribute the torrents the tracker does that

---

### Post by mishkin on 2007-04-12
for example for the ftp server I was told if I input the following command I"ll get a gui that I can go through to install "sudo apt-get install proftpd gproftpd" 

I do that in the puty thing and I get nothing

---

### Post by compmodder26 on 2007-04-12
The thing is, if they really installed the server version, there is not desktop installed by default.  To get to it remotely, you will have to use SSH to log in.  You can then from there begin to install stuff.  But first, you have to contact them to ask how you can remotely connect to it.  This problem would be better addressed by contacting them.

**edit:** man this is a bad day for reading for me.  Anyway, you are logged in.  So what is the message you receive when you type "sudo apt-get install proftpd gproftpd"?

---

### Post by mishkin on 2007-04-12
It doesn't say anything, it just shows eliakd@ubuntu: like it does on every line

---

### Post by thornomad on 2007-04-12
at the command line run the "id" command and see if you are in the "admin" group ... if you are not, I don't think you can run a "sudo" command ... so, that would give you the repeating line with nothing happening when you try the apt-get install option.

---

### Post by FuriousLettuce on 2007-04-12
The other thing is, try it without the 'sudo' - if they've customised it enough, you may have effectively root privaliges without needing sudo.

---

### Post by mishkin on 2007-04-12
I managed to install rtorrent following a guide

I did Su and entered my root pass and it worked

trying to install ftp atm with not much luck I'll add the error here in a bit

edit:

"root@ubuntu:/home/eliakis/libtorrent-0.11.1/rtorrent-0.7.1# apt-get install proftpd gproftpd
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package proftpd"

trying to follow the guide here but first step isn't working
[http://ubuntuforums.org/showthread.php?p=429783#post429783](http://ubuntuforums.org/showthread.php?p=429783#post429783)

---

### Post by FuriousLettuce on 2007-04-12
it must not be available in your repositories. Post the output of 
```

cat /etc/apt/sources.list

```
so we can see your source list.

---

### Post by mishkin on 2007-04-12
root@ubuntu:~# root@ubuntu:~# root@ubuntu:~# cat /etc/apt/sources.list
bash: root@ubuntu:~#: command not found
root@ubuntu:~# bash: root@ubuntu:~#: command not found
bash: bash:: command not found
root@ubuntu:~# root@ubuntu:~# # deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dappermain restricted
bash: root@ubuntu:~#: command not found
root@ubuntu:~# root@ubuntu:~# # deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapperupdates main restricted
bash: root@ubuntu:~#: command not found
root@ubuntu:~# root@ubuntu:~# # deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) dapper-ecurity main restricted
bash: root@ubuntu:~#: command not found
root@ubuntu:~# root@ubuntu:~#
bash: root@ubuntu:~#: command not found
root@ubuntu:~# root@ubuntu:~# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper min restricted
bash: root@ubuntu:~#: command not found
root@ubuntu:~# bash: deb: command not found
bash: bash:: command not found
root@ubuntu:~# root@ubuntu:~# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dappr main restricted
bash: root@ubuntu:~#: command not found
root@ubuntu:~# bash: deb-src: command not found
bash: bash:: command not found
root@ubuntu:~# root@ubuntu:~#
bash: root@ubuntu:~#: command not found
root@ubuntu:~# root@ubuntu:~# ## Major bug fix updates produced after the finalrelease of the
bash: root@ubuntu:~#: command not found
root@ubuntu:~# root@ubuntu:~# ## distribution.
bash: root@ubuntu:~#: command not found
root@ubuntu:~# root@ubuntu:~# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper-udates main restricted
bash: root@ubuntu:~#: command not found
root@ubuntu:~# bash: deb: command not found
bash: bash:: command not found
root@ubuntu:~# root@ubuntu:~# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dappr-updates main restricted
bash: root@ubuntu:~#: command not found
root@ubuntu:~# bash: deb-src: command not found
bash: bash:: command not found
root@ubuntu:~# root@ubuntu:~#
bash: root@ubuntu:~#: command not found
root@ubuntu:~# root@ubuntu:~# ## Uncomment the following two lines to add softwre from the 'universe'
bash: root@ubuntu:~#: command not found
root@ubuntu:~# root@ubuntu:~# ## repository.
bash: root@ubuntu:~#: command not found
root@ubuntu:~# root@ubuntu:~# ## N.B. software from this repository is ENTIRELYUNSUPPORTED by the Ubuntu
bash: root@ubuntu:~#: command not found
root@ubuntu:~# root@ubuntu:~# ## team, and may not be under a free licence. Plese satisfy yourself as to
bash: root@ubuntu:~#: command not found
root@ubuntu:~# root@ubuntu:~# ## your rights to use the software. Also, please ote that software in
bash: root@ubuntu:~#: command not found
root@ubuntu:~# root@ubuntu:~# ## universe WILL NOT receive any review or update from the Ubuntu security
bash: root@ubuntu:~#: command not found
root@ubuntu:~# root@ubuntu:~# ## team.
root@ubuntu:~# ## repository.
bash: root@ubuntu:~#: command not found
root@ubuntu:~# root@ubuntu:~# # deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapperuniverse
bash: root@ubuntu:~#: command not found
root@ubuntu:~# root@ubuntu:~# # deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) daper universe
bash: root@ubuntu:~#: command not found
root@ubuntu:~# root@ubuntu:~#
bash: root@ubuntu:~#: command not found
root@ubuntu:~# root@ubuntu:~# ## Uncomment the following two lines to add softwre from the 'backports'
bash: root@ubuntu:~#: command not found
root@ubuntu:~# root@ubuntu:~# ## repository.
bash: root@ubuntu:~#: command not found
root@ubuntu:~# root@ubuntu:~# ## N.B. software from this repository may not hav been tested as
bash: root@ubuntu:~#: command not found
root@ubuntu:~# root@ubuntu:~# ## extensively as that contained in the main relese, although it includes
bash: root@ubuntu:~#: command not found
root@ubuntu:~# root@ubuntu:~# ## newer versions of some applications which may rovide useful features.
bash: root@ubuntu:~#: command not found
root@ubuntu:~# root@ubuntu:~# ## Also, please note that software in backports WLL NOT receive any review
bash: root@ubuntu:~#: command not found
root@ubuntu:~# root@ubuntu:~# ## or updates from the Ubuntu security team.
bash: root@ubuntu:~#: command not found
root@ubuntu:~# root@ubuntu:~# # deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapperbackports main restricted universe multiverse
bash: root@ubuntu:~#: command not found
root@ubuntu:~# # deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper-backports ain restricted universe multiverse
root@ubuntu:~# root@ubuntu:~# # deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) daper-backports main restricted universe multiverse
bash: root@ubuntu:~#: command not found
root@ubuntu:~# root@ubuntu:~#
bash: root@ubuntu:~#: command not found
root@ubuntu:~# root@ubuntu:~#
bash: root@ubuntu:~#: command not found
root@ubuntu:~# root@ubuntu:~# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-secuity main restricted
bash: root@ubuntu:~#: command not found
bash: deb: command not found
root@ubuntu:~# bash: deb: command not found
bash: bash:: command not found
root@ubuntu:~# root@ubuntu:~# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-ecurity main restricted
bash: root@ubuntu:~#: command not found
root@ubuntu:~# bash: deb-src: command not found
bash: bash:: command not found
root@ubuntu:~# root@ubuntu:~# # deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-seurity universe
bash: root@ubuntu:~#: command not found
root@ubuntu:~# root@ubuntu:~# # deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dappe-security universe
bash: root@ubuntu:~#: command not found


I don't think I actually downloaded the files it needs...

---

### Post by FuriousLettuce on 2007-04-12
Argh! There's something messed up there - that should appear as a simple list, not as if each list were a new command.

---

### Post by mishkin on 2007-04-12
don't know what coulda happened it's a fresh install of ubuntu server all I did was install rtorrent

---

### Post by FuriousLettuce on 2007-04-12
NB: This isn't related to that wierd 'cat' problem (which could be something to do with the keyboard input settings used by putty - try setting the keyboard to VT100 in the putty configuration (before you click connect)), but the tutorial that you're following, that says it will give you a GUI, won't. gproftpd is the GUI, but you won't be able to use it without a proper desktop set up (window manager etc). You're better off attempting to do everything by command line (like using rtorrent instead of installing a graphical torrent manager). 

To get the FTP server set up, use the second half of the tutorial you linked to (the command line section). The way to get proftpd set up is to enable your universe repositories. To do this, type 
```
nano /etc/apt/sources.list
```
The last two lines have a hash (#) at the beginning, and should end in dapper-security universe (check the spelling there - the output you posted has some spelling errors). Delete the hash symbol from the front of the last two lines, then press CTRL and x together, then press y then enter to save the file.
Next, do
```
apt-get update
```
to update your sources. Finally, try to do
```
apt-get install proftpd
```
Hopefully that will install, and you can continue with the tutorial you mentioned.

There's also some more info on setting up the FTP server at [http://ubuntuguide.org/wiki/Ubuntu_dapper#FTP_Server](http://ubuntuguide.org/wiki/Ubuntu_dapper#FTP_Server)

---

