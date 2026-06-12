---
title: "Setting up a new server"
date: 2007-03-25
forum: Absolute Beginner Talk
---

### Post by pjmckeown on 2007-03-25
Well, let's start by saying, I am pretty new to Linux, I can get around okay and do the basics from the command line. I used to work in a unix environment 10 years or so ago. 

Now the questions:

I am building a new server next weekend to use as a file server and have the following needs/questions:

1. I want to be able to run MythTV and record programs to watch on other devices (how)
2. I want to use this as a file server so my mac's and windows devices can attach and read/write to it
3. I would like to hang my printer off of this so that I don't have to have my printer in my main office. Can I use it as a print server and how?
4. There will be no monitor on this, what is the recommended remote software? VNC?
5. I want to run Apache, perl, PHP and MySQL

Server specs:
2ghz amd
1 gb ram
4TB HDDs
100meg wired network
Hauppage 150 tv tuner
on board video

What are your recommendations and such for how I should set this up?

Any help is greatly appreciated!

Regards,
Patrick

---

### Post by sailingboarder on 2007-03-25
#5 will happen automatically if u install a ubuntu lamp server (**L**inux**A**pache**M**ysql**P**hp)
then u could build on functionality from there for all your other needs

---

### Post by thornomad on 2007-03-25
> 
1. I want to be able to run MythTV and record programs to watch on other devices (how)
2. I want to use this as a file server so my mac's and windows devices can attach and read/write to it
3. I would like to hang my printer off of this so that I don't have to have my printer in my main office. Can I use it as a print server and how?
4. There will be no monitor on this, what is the recommended remote software? VNC?
5. I want to run Apache, perl, PHP and MySQL

Here are some quick answers to help you in googl-ing some detailed answers.

1. I don't konw about MythTv, sorry
2. You could use SAMBA, NFS (native for Mac and Linux, but a pain to setup in Mac, though it works) or SSH (try MacFUSE with SSHFS).
3. CUPS should work.
4. Use SSH to access it via the command line.  Install openssh-server on the server.  From the mac can access it in the Terminal ... ssh is included on the mac already.
5. As suggested, do a LAMP install.

D

---

### Post by chymo on 2007-03-28
You can install MythTV to ubuntu.  However I investigated the different variations of a MythTV install, and there are many.  I tried KnoppMyth but had no luck and eventually had success with MythDora.  It's based on Fedora and I have a seperate box dedicated to Myth.  

I highly recommend having a seperate box for Myth because the hardware is constantly working doing recordings or other jobs such as commercial flagging which  works flawlessly for me.  

You really don't want all of this work to interfere with your normal activities, like file serving, parsing web pages, etc...

---

### Post by h0ax on 2007-03-28
There are some great Ubuntu tutorials on setting up servers over at 
[www.howtoforge.com](www.howtoforge.com)

I prefer [http://howtoforge.com/perfect_setup_ubuntu_6.10](http://howtoforge.com/perfect_setup_ubuntu_6.10)
but click Ubuntu and look at all the tutorials

Hope this helps!

---

### Post by pjmckeown on 2007-03-28
Thanks everyone for all the info. Does Myth really tax the machine that much that I would not want to put it on the same box as my main box. This box will pretty much just be a file server and a test web/php development box, as well as a box for me to learn more about Linux on?

Regards,

Patrick

---

### Post by h0ax on 2007-03-30
Generally, when people set up MythTV they have a dedicated box for this purpose.

Personally, I would recommend staying with that.  If you want to have anything on your webserver being accessed good and well I would stick to a standalone webserver / development server.

Unless you think your comp can handle both things running, then do it by all means.
But I would get a cheap dink comp, and put mythTV on it as its sole purpose.

Glad to help

---

### Post by majoridiot on 2007-03-30
your system's specs should be more than sufficient to do what you are wanting.  mythbackend 
requires surprisingly few system resources (for non-HD applications)- so  recordiing, commercial
flagging, file and print sharing should not be a problem.  the *only* possible bottleneck is see
might be the need for a little more RAM.

as a suggestion, follow the ubuntu mythtv guides, which are specifically developed for use with
the ubuntu mythv packages: [https://help.ubuntu.com/community/MythTV](https://help.ubuntu.com/community/MythTV)

from experience, i would approach it one step at a time, with the *first* step being setting
up mythtv and then attacking each additional function one at a time once you have myth up and
running.

i suggest you go with the "backend server" setup or the "backend with desktop" setup, if you are
more comfortable with a full gui.  interface-wise, ssh with a forwarded X connection works well, as
does vnc.  SAMBA should also work well for your file sharing needs. setup for ssh, VNC and SAMBA
are included in the mythtv guides.

since this is a new install for you, i also suggest waiting a couple of weeks for the feisty release (or
the release candidate), as the new mythtv packages and guides are much improved from an 
install standpoint and support for your pvr-150 is built into the kernel (no need for additional
drivers).

i **DO NOT** recommend a LAMP install, as it will complicate mythv installation unless you know
exactly what you are doing.  starting with an "alternate install" cd and building upon that is
your best bet for complication-free setup.  LAMP is great for setting up everything at install,
but could prove troublesome when installing myth, as myth uses mysql and can cause password
issues when setting up the mythconverg database.

good luck!

---

