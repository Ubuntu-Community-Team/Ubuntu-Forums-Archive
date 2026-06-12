---
title: "Still trying to a working system"
date: 2007-08-18
forum: Absolute Beginner Talk
---

### Post by roylond on 2007-08-18
I'm using 6.06 LTS and a newbie. Over the past few months I've worked to get a system up and running but still a lot confounds me. 
Why cannot I get rid of Firefox as I prefer to use Opera. When I try to remove Firefox with Add/Remove I get the message saying it cannot be removed.

How do I get Flashplayer to work with Opera. I try to install it using Synaptic and get the message
md5sum mismatch install_flash_player_9_linux.tar.gz
The flashplugin is not installed.

I did try to download it from the Adobe site but if it did download I cannot find it. 

Any suggestions appreciated.

Roy

---

### Post by apjone on 2007-08-18
have a look at [http://list.opera.com/pipermail/opera-linux/2006-December/009460.html](http://list.opera.com/pipermail/opera-linux/2006-December/009460.html) . Firefox is part of the ubuntu base package and can not be removed. You can set opera as the default application.

---

### Post by taurus on 2007-08-18
If you download something, it's probably in ~/Desktop.  From a terminal, what's the output of this command?

Applications -> Accessories -> Terminal
```
ls -la ~/Desktop
```

---

### Post by roylond on 2007-08-18
> **taurus said:**
> If you download something, it's probably in ~/Desktop.  From a terminal, what's the output of this command?

Applications -> Accessories -> Terminal
```
ls -la ~/Desktop
```

This is what I get on the terminal

roy@roy-collie:~$ ls -la ~/Desktop
total 20
drwxr-xr-x  5 roy roy 4096 2007-08-14 14:58 .
drwxr-xr-x 23 roy roy 4096 2007-08-18 15:50 ..
roy@roy-collie:~$

I don't know what any of it means

R

---

### Post by taurus on 2007-08-18
Or

```
ls -la ~
```

---

### Post by roylond on 2007-08-18
> **taurus said:**
> Or

```
ls -la ~
```

roy@roy-collie:~$ ls -la ~
total 152
drwxr-xr-x 23 roy  roy   4096 2007-08-18 15:50 .
drwxr-xr-x  3 root root  4096 2007-08-13 15:49 ..
-rw-------  1 roy  roy    393 2007-08-18 17:51 .bash_history
-rw-r--r--  1 roy  roy    220 2007-08-13 15:49 .bash_logout
-rw-r--r--  1 roy  roy    414 2007-08-13 15:49 .bash_profile
-rw-r--r--  1 roy  roy   2227 2007-08-13 15:49 .bashrc
drwxr-xr-x  3 roy  roy   4096 2007-08-13 18:43 .config
drwx------  2 roy  roy   4096 2007-08-13 20:33 .cups
drwxr-xr-x  5 roy  roy   4096 2007-08-18 17:56 Desktop
-rw-------  1 roy  roy     26 2007-08-13 16:28 .dmrc
-rw-------  1 roy  roy     16 2007-08-13 16:28 .esd_auth
drwxr-xr-x  7 roy  roy   4096 2007-08-15 12:15 .evolution
lrwxrwxrwx  1 roy  roy     26 2007-08-13 15:49 Examples -> /usr/share/example-content
-rw-r--r--  1 roy  roy      0 2007-08-13 20:28 .fonts.cache-1
drwx------  5 roy  roy   4096 2007-08-18 15:50 .gconf
drwx------  2 roy  roy   4096 2007-08-18 18:13 .gconfd
-rw-r-----  1 roy  roy      0 2007-08-18 12:01 .gksu.lock
drwxr-xr-x  3 roy  roy   4096 2007-08-14 15:19 .gnome
drwx------ 10 roy  roy   4096 2007-08-18 17:52 .gnome2
drwx------  2 roy  roy   4096 2007-08-14 07:34 .gnome2_private
drwxr-xr-x  2 roy  roy   4096 2007-08-13 20:28 .gstreamer-0.10
-rw-r--r--  1 roy  roy     85 2007-08-13 16:28 .gtkrc-1.2-gnome2
-rw-------  1 roy  roy    334 2007-08-18 15:50 .ICEauthority
-rw-r--r--  1 roy  roy      0 2007-08-15 16:41 .lesshst
drwxr-xr-x  3 roy  roy   4096 2007-08-13 18:46 .local
drwx------  3 roy  roy   4096 2007-08-13 16:28 .metacity
drwx------  4 roy  roy   4096 2007-08-18 17:54 .mozilla
drwx------  3 roy  roy   4096 2007-08-14 14:50 .mozilla-thunderbird
drwxr-xr-x  3 roy  roy   4096 2007-08-13 16:28 .nautilus
drwx------  9 roy  roy   4096 2007-08-18 18:19 .opera
drwxr-xr-x  2 roy  roy   4096 2007-08-15 11:13 .qt
-rw-------  1 roy  roy    554 2007-08-18 18:09 .recently-used
-rw-r--r--  1 roy  roy      0 2007-08-13 16:29 .sudo_as_admin_successful
drwx------  4 roy  roy   4096 2007-08-18 12:30 .thumbnails
drwx------  3 roy  roy   4096 2007-08-18 17:56 .Trash
drwx------  2 roy  roy   4096 2007-08-15 10:33 .tsclient
drwx------  2 roy  roy   4096 2007-08-13 16:28 .update-notifier
-rw-------  1 roy  roy    121 2007-08-18 15:49 .Xauthority
-rw-r--r--  1 roy  roy   2139 2007-08-18 18:13 .xsession-errors
-rw-r--r--  1 roy  roy  13311 2007-08-18 12:49 .xsession-errors~
roy@roy-collie:~$

I still haven't clue what any of this means.

R

---

### Post by taurus on 2007-08-18
Are you sure you saved it to your computer?

```
sudo find / -name install_flash_player_9_linux.tar.gz -print
```

---

### Post by roylond on 2007-08-18
> **taurus said:**
> Are you sure you saved it to your computer?

```
sudo find / -name install_flash_player_9_linux.tar.gz -print
```

roy@roy-collie:~$ sudo find / -name install_flash_player_9_linux.tar.gz -print
Password:
/var/cache/flashplugin-nonfree-unpackdir/install_flash_player_9_linux.tar.gz
roy@roy-collie:~$

Is that any help ?

R

---

### Post by taurus on 2007-08-18
It is in /var/cache/flashplugin-nonfree-unpackdir.  You can move to your $HOME directory, unpack it and install it.

```
mkdir ~/temp
cp /var/cache/flashplugin-nonfree-unpackdir/install_flash_player_9_linux.tar.gz ~/temp
cd ~/temp
tar xvzf install_flash_player_9_linux.tar.gz
```
Then, look at the README/INSTALL on how to install it by hand or for system wide.

---

### Post by roylond on 2007-08-18
> **taurus said:**
> It is in /var/cache/flashplugin-nonfree-unpackdir.  You can move to your $HOME directory, unpack it and install it.

```
mkdir ~/temp
cp /var/cache/flashplugin-nonfree-unpackdir/install_flash_player_9_linux.tar.gz ~/temp
cd ~/temp
tar xvzf install_flash_player_9_linux.tar.gz
```
Then, look at the README/INSTALL on how to install it by hand or for system wide.

Did that but cannot find it ?
Where will it be ?

---

### Post by taurus on 2007-08-18
What steps have you done so far and what was the error message?

---

### Post by roylond on 2007-08-18
I have copied and pasted the code into the terminal and then hit enter.
I didn't get any error messages
I just cant seem to find anything which refers to flash player

R

---

### Post by taurus on 2007-08-18
What's the output of this command then?

```
ls -la ~/temp
```

---

### Post by roylond on 2007-08-18
> **taurus said:**
> What's the output of this command then?

```
ls -la ~/temp
```

roy@roy-collie:~$ ls -la ~/temp
total 8
drwxr-xr-x  2 roy roy 4096 2007-08-18 19:17 .
drwxr-xr-x 24 roy roy 4096 2007-08-18 19:17 ..
roy@roy-collie:~$

Still confused

---

### Post by taurus on 2007-08-18
Try this.

```
cd ~/temp
wget http://fpdownload.macromedia.com/get/flashplayer/current/install_flash_player_9_linux.tar.gz
tar xvzf install_flash_player_9_linux.tar.gz
cd install_flash_player_9_linux
```
Then, either run flashplayer-installer to install it 

```
sudo ./flashplayer-installer
```
or move those last two files, flashplayer.xpt & libflashplayer.so, to the plugins directory for opera.

---

### Post by roylond on 2007-08-18
move those last two files, flashplayer.xpt & libflashplayer.so, to the plugins directory for opera

YEAHHHHHH 
Thanks a million did that and it works 

Thanks again Taurus

Roy

---

### Post by taurus on 2007-08-18
You're welcome.

---

