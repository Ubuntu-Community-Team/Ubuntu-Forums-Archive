---
title: "First time Ubuntu install!"
date: 2005-06-27
forum: Absolute Beginner Talk
---

### Post by Markp.com on 2005-06-27
Hello all,

Just got Ubuntu installed... its amazing, already customised it to look damn sexy! :D

Now I need a little help.

How do I install programs? I've heard of a "package manager" but I'm not sure where this is or how to use it.

I've been reading through the software comparisons thread here and it all seems nice, but where do I go to download and install these programs?

I also have a TwinHan DVB-T tv pci card, are there any linux apps available so I can start watching (and even recording TV) again?

If this is posted in the wrong place, please move it, or let me know where I should post.

Thanks everyone!

---

### Post by rachii on 2005-06-27
[http://www.debian.org/doc/manuals/apt-howto/index.en.html](http://www.debian.org/doc/manuals/apt-howto/index.en.html)

apt is the greatest thing ever.   you can read ALL about it at the above link
(or for more of a crash course on apt, type 'man apt-get' into a console)

but if your warry of the command line.  under System - Administration - Synaptic
is a gui to manage packages, you search and check off the ones you want to install or remove etc...

---

### Post by Leif on 2005-06-27
[http://ubuntuguide.org/](http://ubuntuguide.org/)

---

### Post by frodon on 2005-06-27
In the first time this guide will be really useful for you : [http://www.frankandjacq.com/ubuntuguide/5.04/index.html](http://www.frankandjacq.com/ubuntuguide/5.04/index.html) get information here and if it's not enough, ask some questions here or post a specific thread.
You make the good choice installing ubuntu !  ;-)

---

### Post by Kvark on 2005-06-27
In the menues on top, go to System -> Administration -> Synaptic Package Manger. Look around in the cathegories or use the search function to find programs,
Put checkboxes for the programs you want, and hit apply.

But first, follow these steps to configure synaptic to find most of the programs:
[http://ubuntuguide.org/#extrarepositories](http://ubuntuguide.org/#extrarepositories)

---

### Post by Markp.com on 2005-06-27
Thanks chaps, having a play with this Synaptic thing now...

So whats cool in linux? What should I install? And does anyone have experience with getting TV cards to run in Ubuntu?

---

### Post by Mr. Electric Wizard on 2005-06-27
Best thing is that its free, and not M$.
Different is _better_.

MPlayer - for playing any video imaginable
XMMS - for playing mp3's
Samba - for sharing files to other PC's on your network

---

### Post by poofyhairguy on 2005-06-27
[QUOTE=Markp.com]Thanks chaps, having a play with this Synaptic thing now...

So whats cool in linux? What should I install? [/QUOTE]

My favs are Gxine, bittornado and openoffice.org2

> And does anyone have experience with getting TV cards to run in Ubuntu?

xawtv

Install that program and see if your card works.

Here is a great site with info for that:

[http://www.linuxtv.org/](http://www.linuxtv.org/)

---

### Post by monchichi on 2005-06-27
the best tv program is tvtime, imho

---

### Post by Markp.com on 2005-06-28
[QUOTE=poofyhairguy]My favs are Gxine, bittornado and openoffice.org2



xawtv

Install that program and see if your card works.

Here is a great site with info for that:

[http://www.linuxtv.org/](http://www.linuxtv.org/)[/QUOTE]
 Hello there... I've been to the  xawtv website and downloaded xawtv-3.94.tar.gz to my desktop.

How do I install it? Sorry for being such a n00b! :(

---

### Post by Gustav on 2005-06-28
[QUOTE=Markp.com]Hello there... I've been to the  xawtv website and downloaded xawtv-3.94.tar.gz to my desktop.

How do I install it? Sorry for being such a n00b! :([/QUOTE]
 You don't have to download any files. Just type this command:

sudo apt-get install xawtv

or use synaptic to install it (see previous posts)

---

### Post by Markp.com on 2005-06-28
Hello all, I'm having a bit of bother getting this xawtv thing running...

I opened a terminal window and typed in the commands as you suggested.

It ran through an "installation" process and dropped me back out at the command prompt.

I looked round the Gnome start menu, but there were no programs listed there, so I went back to the terminal window.

I then typed xawtv and got this error...

> ubuntu:~$ xawtv
This is xawtv-3.94, running on Linux/i686 (2.6.10-5-386)
WARNING: v4l-conf is compiled without DGA support.
can't open /dev/video0: No such file or directory
v4l-conf had some trouble, trying to continue anyway
v4l2: open /dev/video0: No such file or directory
v4l2: open /dev/video0: No such file or directory
v4l: open /dev/video0: No such file or directory
no video grabber device available


Any idea what it means or how to fix it? Am I doing this correctly?

Thanks for all your help so far! :)

M

---

### Post by poofyhairguy on 2005-06-28
> 
sudo apt-get install tvtime


Try Tvtime then. It might work.

---

### Post by Markp.com on 2005-06-28
[QUOTE=poofyhairguy]Try Tvtime then. It might work.[/QUOTE]
 TVtime installs fine, but when I run it, it just gives me a no signal error...

There are no options to tune in channels or anything?!

Strange... is there a TVTime help forum, as I think I've used up my helpful requests here! :D

Thanks for all your help by the way! :)

---

### Post by bassMonkey on 2005-06-29
[QUOTE=Markp.com]TVtime installs fine, but when I run it, it just gives me a no signal error...

There are no options to tune in channels or anything?!

Strange... is there a TVTime help forum, as I think I've used up my helpful requests here! :D

Thanks for all your help by the way! :)[/QUOTE]

Hi, you might not have the correct drivers (modules) loaded, what tv-card are you using?

---

