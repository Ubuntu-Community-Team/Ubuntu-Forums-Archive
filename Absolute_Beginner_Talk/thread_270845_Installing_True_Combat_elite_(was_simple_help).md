---
title: "Installing True Combat elite (was: simple help)"
date: 2006-10-03
forum: Absolute Beginner Talk
---

### Post by dmichaels on 2006-10-03
trying to install true combat elite from desktop but get a unicode error. also whats the command to install stuff from the desktop?

---

### Post by llamakc on 2006-10-03
Always post the error: it helps people who want to help you.

---

### Post by Fully216 on 2006-10-03
This site might be helpful:

[http://katanoon.nl/Ubu-e/install.php](http://katanoon.nl/Ubu-e/install.php)

---

### Post by dmichaels on 2006-10-03
i saved the game to my desktop. when i run it i get this message 


Could not open the file /home/drew/Desktop/true.…at.elite_0.49-english.run

gedit has not been able to detect the character coding.
Please check that you are not trying to open a binary file.
Select a character coding from the menu and try again

what the *&%^%:confused:

---

### Post by Brunellus on 2006-10-03
Topic changed better to reflect the nature of the help request.  In the future, use the thread title to express, generally, the TYPE of problem you are having.  This lets users who know how to help you...help you.

that .run file is probably a binary executable.  You'd have to execute it in the terminal.

```

cd /Desktop
./long-***-filename.run

```

yes, that's dot-slash.

---

### Post by dmichaels on 2006-10-04
the code wont work for me.  

cd /desktop

bash: cd: /desktop: No such file or directory

---

### Post by Madpilot on 2006-10-04
It's Desktop, not desktop.

Linux is case-sensitive - capitalization counts.

---

### Post by incubus on 2006-11-10
Also there's no slash before Desktop.  This should do the trick:

Make sure you're in your home directory:
```

cd

```

Finally:
```

cd Desktop

```

incubus

By the way, I'm also interested in trying out this game.  I'll try it here and post my results.

---

### Post by javierfh on 2006-11-11
Hello...

i followed the steps in the link above but when getting to step 2:install RTCW:ET in the last step where it says sudo ./et-linux-2.60.x86.run i get the  following error.
> 
javi@javi-desktop:~$ sudo ./et-linux-2.60.x86.run
Verifying archive integrity...Error in MD5 checksums: be740ed31074ac1385c9d4b79b091182 is different from b8b59bc515d86cc845fb52f5d2c14423


Any idea how to continue?
I add here the output from console hopping someone can give me some tip or hint how to solve that.

> 
javi@javi-desktop:~$ wget [http://ftp.games.skynet.be/pub/wolfenstein/et-linux-2.60.x86.run](http://ftp.games.skynet.be/pub/wolfenstein/et-linux-2.60.x86.run)
--17:16:33--  [http://ftp.games.skynet.be/pub/wolfenstein/et-linux-2.60.x86.run](http://ftp.games.skynet.be/pub/wolfenstein/et-linux-2.60.x86.run)
           => `et-linux-2.60.x86.run'
Resolving ftp.games.skynet.be... 195.238.1.6
Connecting to ftp.games.skynet.be|195.238.1.6|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 270,965,248 (258M) [text/plain]

100%[====================================>] 270,965,248  132.33K/s    ETA 00:00

17:51:31 (126.15 KB/s) - `et-linux-2.60.x86.run' saved [270965248/270965248]

javi@javi-desktop:~$ sudo apt-get install libgtk1.2
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  libgtk1.2-common
The following NEW packages will be installed:
  libgtk1.2 libgtk1.2-common
0 upgraded, 2 newly installed, 0 to remove and 0 not upgraded.
Need to get 995kB of archives.
After unpacking 2777kB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 [http://fi.archive.ubuntu.com](http://fi.archive.ubuntu.com) edgy/main libgtk1.2-common 1.2.10-18 [158kB]
Get:2 [http://fi.archive.ubuntu.com](http://fi.archive.ubuntu.com) edgy/main libgtk1.2 1.2.10-18 [837kB]
Fetched 995kB in 1s (826kB/s)     
Selecting previously deselected package libgtk1.2-common.
(Reading database ... 101375 files and directories currently installed.)
Unpacking libgtk1.2-common (from .../libgtk1.2-common_1.2.10-18_all.deb) ...
Selecting previously deselected package libgtk1.2.
Unpacking libgtk1.2 (from .../libgtk1.2_1.2.10-18_i386.deb) ...
Setting up libgtk1.2-common (1.2.10-18) ...

Setting up libgtk1.2 (1.2.10-18) ...

javi@javi-desktop:~$ chmod +x et-linux-2.60.x86.run
javi@javi-desktop:~$ sudo ./et-linux-2.60.x86.run
Verifying archive integrity...Error in MD5 checksums: be740ed31074ac1385c9d4b79b091182 is different from b8b59bc515d86cc845fb52f5d2c14423
javi@javi-desktop:~$ et
bash: et: command not found



---

### Post by Fully216 on 2006-11-20
a MD5 checksum error means the file was downloaded incorrectly/corrupt and needs to be redownloaded.

---

