---
title: "FTP client for Ubuntu"
date: 2008-03-12
forum: Absolute Beginner Talk
---

### Post by Pat Brown on 2008-03-12
I really need a graphical user interface to manage my web page. I tried using Synaptic Package Manager but though I installed what seemed to be a couple of FTP clients, I can't find how to access them. How do I run these things if they are installed? I tried going to the ftp site with my browser but get a login error - 425 Can't get connection. My web hosting site isn't helping much, saying I should use CuteFTP or something like that, but of course I'm not on Windows. I really need help in this.

Pat
[email]pat.mysterywriter@gmail.com[/email]

---

### Post by Teber on 2008-03-12
they should be under applications/internet

alternatively they should run in terminal too. or from a string gadget evoked by pressing Alt+F2

---

### Post by owbizi on 2008-03-12
You can try gftp. Install that with:
$ sudo apt-get install gftp

Also, FileZilla is very good, but is not avalaible via apt-get, I think. Anyways, this is the site:
[http://filezilla-project.org/download.php](http://filezilla-project.org/download.php).

And, to run some program you install, only do alt+f2 and type the name of the program. In the majority of cases, this will work (*edit: damn!, Teber was faster!*). :)

---

### Post by PinkFloyd102489 on 2008-03-12
GFTP is the most commonly used for Gnome. There's also Filezilla for Firefox.


If you want to do a bit of configuring, use Connect To Server in the Places menu. Provides a drag and drop interface through Nautilus instead of having items in a list.

---

### Post by Oldsoldier2003 on 2008-03-12
> **owbizi said:**
> You can try gftp. Install that with:
$ sudo apt-get install gftp

Also, FileZilla is very good, but is not avalaible via apt-get, I think. Anyways, this is the site:
[http://filezilla-project.org/download.php](http://filezilla-project.org/download.php).

And, to run some program you install, only do alt+f2 and type the name of the program. In the majority of cases, this will work (*edit: damn!, Teber was faster!*). :)

Gftp is good but i like to recommend filezilla because its cross platform, making it a lt easier to do walkthroughs with windows users.

---

### Post by Pat Brown on 2008-03-13
> **owbizi said:**
> You can try gftp. Install that with:
$ sudo apt-get install gftp

Also, FileZilla is very good, but is not avalaible via apt-get, I think. Anyways, this is the site:
[http://filezilla-project.org/download.php](http://filezilla-project.org/download.php).

And, to run some program you install, only do alt+f2 and type the name of the program. In the majority of cases, this will work (*edit: damn!, Teber was faster!*). :)

Filezilla works. Thanks!

Pat

---

### Post by Teber on 2008-03-13
> **Pat Brown said:**
> Filezilla works. Thanks!

Pat

and that has been the point all the time. 

what a forum! pat brown posts a question and two replies get posted within 10 minutes! the ubuntu community truly shines!

---

### Post by Dr Small on 2008-03-13
I use gFTP for all my needs as it supports sftp also.

---

### Post by oldos2er on 2008-03-13
Just FYI, Nautilus has built-in FTP support. Open Nautilus, and under the File menu, choose 'connect to server....'

---

### Post by Oldsoldier2003 on 2008-03-13
> **Dr Small said:**
> I use gFTP for all my needs as it supports sftp also.

gFTP works great, I usually recommend filezilla for folks that support a mixed environment because they can walk through a windows user without having to boot up a VM. Unfortunately the Linux client is acually LESS capable then the windows one, but still works for most purposes. For instance you cant edit a file on the linux version, but then again why would you use a FTP client to edit foles if you use linux???? :)

---

