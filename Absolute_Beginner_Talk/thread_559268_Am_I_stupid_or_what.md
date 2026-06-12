---
title: "Am I stupid or what?"
date: 2007-09-24
forum: Absolute Beginner Talk
---

### Post by guymclaren on 2007-09-24
Having worked in command line on DOS many years ago, I figured linux can't be that difficult. Thus fae I have managed a LAMP install on 6.06.  I Installed Firefox but don't know how to open it. When I type firefox on the command line I get

(firefox-bin:6460): Gtk-WARNING **: cannot open display

1. So what exactly does this mean?

2. My objective is a file server used on my network as well as via the net allowing individual accounts (password protected) for data storage. We want to allow web signups using apache I guess. For now testing phase I will need to use the IP adress and IP forwarding for my clients to access the box from outside.  Is this at all feasible? 

3. I would prefer this to not need ftp software on the outside. Do I need to install SAMBA? The appearance needs to be like an added harddrive or network connection?

4. My objective for today is to manually set up an account and allow someone to access it from an external source. They will be on a windows machine, Where do I start?

5. Is there some kind of software I can use to configure the server from my windows machine? 

6. Is there some kind of idiots guide (step by step) to doing some of this stuff?

---

### Post by bobplano on 2007-09-24
wow a lot of questions i don't know they answers to. if you're running a server then most likely you don't have the gui firefox requires. try lynx if you need a web browser.

---

### Post by guymclaren on 2007-09-25
Thank you sir, I shall try that

anyone that can help with any of the other questions? I would really appreciate the help

---

### Post by Rabidmonkey1 on 2007-09-25
[http://ubuntuguide.org/wiki/Ubuntu:Feisty](http://ubuntuguide.org/wiki/Ubuntu:Feisty)

That guide might help you as there is a Remote Access section available there.

Be careful though, as most of this is "unoffical" advice and some of the things they recommend aren't exactly good protocol (such as installing automatix or easyubuntu - which shouldn't interfere with anything you want to do however)

---

### Post by guymclaren on 2007-09-25
Thank you sir, I shall read the material

---

### Post by Adramelech on 2007-09-25
4) My objective for today is to manually set up an account and allow someone to access it from an external source. They will be on a windows machine, Where do I start?

Maybe ssh can help, its on the guide Rabidmonkey1 gave you and on the wiki:
[Wiki]("https://help.ubuntu.com/community/AdvancedOpenSSH")

Theres a really useful tip at the end of the howto.

---

### Post by Wim Sturkenboom on 2007-09-25
One of the ways for data storage is a simple ftp server. This is not installed in the default Ubuntu LAMP setup. You can get one using the package manager. If you want to use vsftp as a server, you can read Miles Brennan's [Linux Home Server HOWTO - FTP](http://www.brennan.id.au/14-FTP_Server.html) as a guideline for the setup (written for Fedora but the same priciples apply).
Pay attention to the part about chroot as you don't want users to get outside their home directory and pay attension to the secure FTP part (to protect users credentials).

Signup can be by a simple email (no need for apache) although a website with signup functionality can be more user friendly.

For remote access, you can use the telnet server (not secure) or the ssh server (secure). The latter is the preferred way. Again, Ubuntu LAMP does not come with sshd pre-installed, so again use the package manager.
On the windows side you can use putty to gain access to your server (both for telnet and ssh).

---

### Post by bukwirm on 2007-09-25
2. Sounds complicated but feasible. Give yourself lots of time and be prepared to do lots of research.

3. If you want to be able to mount shares from your server in Windows, you will need Samba. If you want to mount shares from your server in Unix, you can use NFS.

4. adduser is the command to add a user to the system. Start with it's man page. If you just want to access files from the server, try to get Samba working.

5. ssh - install "openssh-server" package on the server and use putty to connect to it.

---

### Post by guymclaren on 2007-09-25
Thank you all

I am busy working on the samba install, problem I have right now is how do I change a read only file to rw?

---

### Post by justleen on 2007-09-25
use chmod
you can use the numerical way to change fil permissions, or text. text is  perry straight forward.
-rw------- 1 root root  4987 2007-09-03 09:57 mbox

the first bit consists of 4 sections.
bit 1:  dir or not  , values:  - or d
the other places are for Owner, Groep, and Other.
they van have X, R or W
tho change these values (in my mbox file):
chmod a+rw  mobx  -> give All R/W right
-rw-rw-rw  mbox

chmod g+rw mbox
-rw--rw--- mbox


to remove right, use a - instead of a +

---

### Post by hyper_ch on 2007-09-25
Ahem, I don't quite understand what you want to achieve.

You want to setup a file server to which you can sign-up from a webinterface?
And when you sign-up, do you want only to give the people only access to their own files or shall there be shared files?

---

### Post by alienexplorers on 2007-09-25
Try running firefox as root and see if you get the GTK error.

---

### Post by 3rdalbum on 2007-09-25
I'm assuming you installed from the Server ISO, and only have a command-line. This explains why Firefox won't start, because you need the X server installed.

You can use apt-get to install the ubuntu-desktop package, which includes everything you need (including some programs you might not). Or, you could install these packages:

xserver-xorg
gdm
openbox
xterm

I believe this will be enough to start a simple X session, so that you can use Firefox.

---

### Post by guymclaren on 2007-09-25
Thank you all, hyperch no shared files at all.

---

