---
title: "FTP help"
date: 2006-12-01
forum: Absolute Beginner Talk
---

### Post by Halfling Rogue on 2006-12-01
I am completely unfamiliar with using a terminal-based ftp; up until now, I've been using winscp, so I have no idea what the text commands are, and 'man ftp', while somewhat helpful, is still leaving me confused in a lot of places. Could someone show me how to upload an image from my computer to my website?

---

### Post by faraazs on 2006-12-01
It should just be ```
ftp <hostname>
``` and then to put a file onto the server ```
put <local filename>
```. If you want, you can just install gftp and it will take care of all of that for you in a nice GUI system. It's all up to you.

---

### Post by stupidkid on 2006-12-01
ftp user@server allows you to get in.

put <file name> - uploads file
get <file name> - downloads file to the current directory you're in
cd <dir> - changes directory 

If you don't want to use cmd line why not install gftp? I've heard it's pretty good.

Edit: faraazs beat me :)

---

### Post by mushroom on 2006-12-01
You can use Nautilus (the file manager) to connect to FTP servers. Just put "ftp://<url>" (where <url> is the url of the server you want to connect to) into the location bar.

---

### Post by Halfling Rogue on 2006-12-01
I'll download gftp, but I'd like to know how to work the terminal commands as a backup if I need it. :)

The problem I keep getting is this:

<snip>

---

### Post by tchoklat on 2006-12-01
gFTP is a breeze to use and does a great job. I use it to update my web site.
 
sudo aptitude install gftp
 
tony

---

### Post by Halfling Rogue on 2006-12-01
I'm getting problems with gFTP, too.

<snip>

---

### Post by stupidkid on 2006-12-02
Does your server have ssh installed? If so, sftp works too. Just sftp user@server. By the way, ssh/sftp uses port 22 by default and ftp uses port 21 by default.

Judging from SSH-2.0-OpenSSH_3.8.1p1, it seems like you're using the wrong port. Use port 21 for ftp or sftp with port 22.

---

