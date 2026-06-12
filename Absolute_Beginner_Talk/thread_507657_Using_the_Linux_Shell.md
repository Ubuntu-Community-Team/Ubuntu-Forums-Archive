---
title: "Using the Linux Shell"
date: 2007-07-23
forum: Absolute Beginner Talk
---

### Post by rkeslar on 2007-07-23
I'm very new to Ubuntu, but I've used other distributions of Linux in the past. In college I had a Unix Systems course, where we mainly learned how to use the Unix Shell. Is there a way to use the shell with Ubuntu or can you only use the gui now?

Thanks,
Rich

---

### Post by LaRoza on 2007-07-23
You can use it, if you are like me, you have it in the panel so you can get to it faster.

(It is under "accessories", called "Terminal")

The terminal is frequently used.

---

### Post by zanglang on 2007-07-23
Yep, go to Applications -> Accessories -> Terminal to open up one.

---

### Post by RomeReactor on 2007-07-23
Hi. Yes you can still use it: go to "Applications->Accessories->Terminal".

Or you can install the server version which is command line only.

---

### Post by rkeslar on 2007-07-23
Oh ok that's interesting. Thanks

---

### Post by jvc26 on 2007-07-23
The shell is hugely useful for loads of things, despite many would suggest that it no longer serves a purpose outside the server world I'm a major fan, and still do a lot of my commands via CLI as I prefer its direct and speedy nature to that of GUIs. (I was a windows user who had never used CLI before I came to Linux, but wouldn't look back now)
Il

---

### Post by Anzan on 2007-07-23
> **Illuvator said:**
> The shell is hugely useful for loads of things, despite many would suggest that it no longer serves a purpose outside the server world I'm a major fan, and still do a lot of my commands via CLI as I prefer its direct and speedy nature to that of GUIs. (I was a windows user who had never used CLI before I came to Linux, but wouldn't look back now)
Il

Hi Illuvator,

I'm interested in using the CLI more but am not certain of what kinds of tasks I could do with it (other than installing apps and backing up). Can you give a few examples?

---

### Post by asmoore82 on 2007-07-23
yea, winders can give you a command prompt but linux gives your the whole
Command Line **Environment** ...

use it, love it, live it.

---

### Post by asmoore82 on 2007-07-23
> **Anzan said:**
> Hi Illuvator,

I'm interested in using the CLI more but am not certain of what kinds of tasks I could do with it (other than installing apps and backing up). Can you give a few examples?

Do you have a CD you burned and would like to do a quick checksum of it?

place the CD in your drive but don't close it and ...

```
~$ dd if=/dev/cdrom | md5sum > cdtest_md5.txt; eject /dev/cdrom
```

the text file 'cdtest_md5.txt' now holds that checksum

Are you feeling lonely during the checksum with no output on the term...
install one of the greatest comline apps ever ... 'pipemeter ~ why wasn't this written sooner'
and run the checksum with some user friendly output ...

```
~$ sudo apt-get install pipemeter
~$ dd if=/dev/cdrom | pipemeter | md5sum > cdtest_md5.txt; eject /dev/cdrom
```

now that's better than a cd verifying GUI ever could be. :guitar:

As long as you've got the power of the pipemeter installed now, Why not do an informal benchmark test on your machine
```
~$ pipemeter </dev/zero >/dev/null
```
press [ctrl]+c to stop the flow of fun and post your Gigs per Second.

---

### Post by RomeReactor on 2007-07-23
Hi **Anzan**. This is just a sample of tasks you can do in the command line:

* Copy/Paste files from one place to another (using **cp**)
* Move files or rename them (using **mv**)
* Print to screen the contents of a text file without opening it (using **cat**)
* Install programs (using **apt-get, aptitude, dpkg**)
* Browse the internet in text mode (by installing **links, links2, lynx**, or using **w3m**)
* View pictures and other images (by installing **zgv**)
* Listen to mp3 music (by installing **mpg321, cplay, mp3blaster**)
* Download files through ftp/http (using **wget**)
* Compress/extract files (by installing **zip/unzip, rar/unrar**, or by using **tar**)
* Chat in IRC (by installing **irssi**)
* Chat in ICQ, IRC, MSN, YAHOO, AIM, JABBER (by installing **centericq**)
* Manage your files with a fully featured file manager (by installing **mc**)
* View and manage your system processes with a system monitor (by using **top** or installing **htop**)
* Download BitTorrent files (single file using **btdownloadcurses**, multiple simultaneous files using **btlaunchmanycurses** or by installing **rtorrent**
* Edit text files (using **nano, vim**)
* Use an antivirus to scan email attachments or other files (by installing **clamav**, [f-prot]("http://www.f-prot.com/download/home_user/download_fplinux.html"))
* Manage your firewall (using **iptables**)
* Burn CDs or DVDs (using **cdrecord** and **growisofs**, respectively)

And much more. The command line is a complete computing environment that is reliable, fast, and extremely light on system resources. For more information about each command's usage, try **man COMMAND_HERE** to get a detailed manual.

*Note* The antivirus is not really needed for your system; rather, it's commonly used to vaccinate files for transfer to windows machines where the viruses can do actual damage.

---

