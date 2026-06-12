---
title: "Softwares and updates"
date: 2008-03-04
forum: Absolute Beginner Talk
---

### Post by mmarif4u on 2008-03-04
Hi to all.
My system is up to date.
Now the next step is to install the programmes.
So i need some guidence about installing some important softwares.
Actullay i am a programmer(PHP,Mysql,Apache).
So which softwares i install for these above programming modules.
i-FTP
ii-PHP syntax highlighter editor
iii-Software like My Query broswer for Mysql to resotre and backup databases.

Now in general softwares:
1-Best movie player
2-Best MP3 playes
3-Best archive software
4-Best PDF viewer and creator
5-Best browser

If the recommanded software is not available in the repositry then how can i update and install that software.
Also any new theme for desktop look.

Thanks in advance.

---

### Post by hyper_ch on 2008-03-04
i- FTP --> do you need an ftp server? Can it be done with SSH?

ii-PHP --> Have a look at Quanta, it's quite nice... simpler would be KATE... you can also use eclipse or vi(m) or or or... there are tons...

iii- --> I like phpMyAdmin, it's webbased and works well


(1) VLC

(2) Amarok

(3) Command line ("tar")

(4) Creator is integrated into OOo, viewer comes also with default install

(5) FF 3, Opera 9.5x, Kazehakaze, Dillo, Konqueror, Epiphany, ......

It's all in the repos, maybe you need to enable universe and multiverse

---

### Post by kpkeerthi on 2008-03-04
PHP,Apache, MySQL: [https://help.ubuntu.com/community/ApacheMySQLPHP](https://help.ubuntu.com/community/ApacheMySQLPHP)

In my opinion:
1-Best movie player : VLC

2-Best MP3 playes: I have iPod. I found banshee the best iPod manager/music library manager/player for GNOME

3-Best archive software: You mean with a GUI? I use the one that comes bundled with gnome + unrar

4-Best PDF viewer - Acrobat Reader, creator - No Idea

5-Best browser - Firefox + plugins (java/acrobat/mplayer-plugins/flash)

---

### Post by mmarif4u on 2008-03-04
Tq to all...
one last question Which software for writing to cds and DVDs.Best one.

---

### Post by taurus on 2008-03-04
K3b.

---

### Post by mmarif4u on 2008-03-04
Tq to all...
one last question Which software for writing to cds and DVDs.Best one.

---

### Post by mmarif4u on 2008-03-04
Sori for double post.
Tq for the reply.
Where can i find this software and then install.

---

### Post by taurus on 2008-03-04
Applications -> Accessories -> Terminal
```
sudo apt-get update
sudo apt-get install k3b
```
Applications -> Sound & Video

[http://monkeyblog.org/ubuntu/installing/](http://monkeyblog.org/ubuntu/installing/)

---

### Post by hyper_ch on 2008-03-04
K3B

it's all in the repos.

---

### Post by mmarif4u on 2008-03-04
Yup i got it.
In my 1st post i ask about ftp software.any body have any idea.
from where can i install phpmyadmin.

---

### Post by Teber on 2008-03-04
in the repos you may find ftp stuff. i found one that looks promising. additionally you may install putty for text oriented operations on the server, which could be in the repos. just check under add/remove.

---

### Post by taurus on 2008-03-04
Use either vsftpd or proftpd (& gproftpd).

---

### Post by ImAnOgre on 2008-03-04
1-Best movie player - VLC
2-Best MP3 playes - Exaile (amarok clone for Gnome)
3-Best archive software - archive manager
4-Best PDF viewer and creator - To create pdfs I use the CUPS virtual printer
5-Best browser - **Swiftweasel**

---

### Post by Oldsoldier2003 on 2008-03-04
> **mmarif4u said:**
> Yup i got it.
In my 1st post i ask about ftp software.any body have any idea.
from where can i install phpmyadmin.
Try filezilla if you like gui clients (plus its open source and also available in windows), it supports sftp as well.  For server... unless you just want an anonymous ftp server I'd say don't install one at all, use ssh.  For anonymous FTP only I agree with Taurus:  Use either vsftpd or proftpd (& gproftpd).

The reason I say no ftp is passwords are sent in the clear, same with telnet. you get the functionality and security  by using ssh, but for anonymous ftp it doesn't matter...

---

### Post by hyper_ch on 2008-03-05
ftp client or ftp server?

phpmyadmin is also in the repos...

---

