---
title: "File Permissions Denied in my Home directory?"
date: 2007-01-09
forum: Absolute Beginner Talk
---

### Post by Saterus on 2007-01-09
I installed Ubuntu a couple of days ago and have been slowing becoming used to it. I've been slowly following some of the many terminal tutorial guides and using it to message people on gaim while I got used to everything. Now I wanted to start learning a little more and installing programs. I went to the newbie forum and followed a sticky to the [Dapper Start Guide]("http://doc.gwos.org/index.php/DapperGuide"). I tried to start installing some of the programs by following the directions and haven't had any success with any of it. I've had no problems as far as Ubuntu has gone. It installed wonderfully on my laptop and detected everything better than I had ever hoped for.

I decided to start simple and follow the guide on how to install the [Clipboard Daemon for GNOME]("http://doc.gwos.org/index.php/DapperGuide#How_to_install_Clipboard_Daemon_for_GNOME"). I followed the first set of directions to download the program from the website with 'wget' and it failed citing a lack of permissions (or at least thats how I read it).

Here is my error message based on what I did:
```
anb19@anb19-laptop:/$ wget -c http://easylinux.info/uploads/gnome-clipboard-daemon-1.0.bin.tar.bz2
--01:47:49--  http://easylinux.info/uploads/gnome-clipboard-daemon-1.0.bin.tar.bz2
           => `gnome-clipboard-daemon-1.0.bin.tar.bz2'
Resolving easylinux.info... 195.13.158.141
Connecting to easylinux.info|195.13.158.141|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 8,784 (8.6K) [application/octet-stream]
gnome-clipboard-daemon-1.0.bin.tar.bz2: Permission denied

Cannot write to `gnome-clipboard-daemon-1.0.bin.tar.bz2' (Permission denied).

```

I'm just trying to download the file to my Home directory. I'm not sure what the problem could be. The folder permissions settings are set up correctly so it shouldn't really be a problem. I even tested it by making new directories in the terminal with 'mkdir' (probably unnecessary to check, but I felt like using something I'd learned from the guides). 

I'm guessing this is going to be a really simple problem since I'm following the guide posted in the newbie forum.

If you guys need any more information about what I've done, I'll be happy to give it to you. 

Thanks,
Alex

---

### Post by deadgobby on 2007-01-09
sudo chown (user name) and then file name

---

### Post by Saterus on 2007-01-09
But what file am I supposed to change the owner of? The file wont save itself (as I understand the problem at least..).

---

### Post by deadgobby on 2007-01-09
Try not to save the file to the clip board, Try to save save the tar to desktop. And see if you get the same.
GObby

---

### Post by Saterus on 2007-01-09
As you requested:

```
anb19@anb19-laptop:/$ wget http://easylinux.info/uploads/gnome-clipboard-daemon-1.0.bin.tar.bz2 > /home/anb19/gnome-clipboard-daemon-1.0.bin.tar.bz2
--01:52:23--  http://easylinux.info/uploads/gnome-clipboard-daemon-1.0.bin.tar.bz2
           => `gnome-clipboard-daemon-1.0.bin.tar.bz2'
Resolving easylinux.info... 195.13.158.141
Connecting to easylinux.info|195.13.158.141|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 8,784 (8.6K) [application/octet-stream]
gnome-clipboard-daemon-1.0.bin.tar.bz2: Permission denied

Cannot write to `gnome-clipboard-daemon-1.0.bin.tar.bz2' (Permission denied).

```

Same result. I'm not sure what's happening, but it does it even if I try downloading other programs too. (That was supposed to go in the first post, but I forgot to put that)

Thanks,
Alex

---

