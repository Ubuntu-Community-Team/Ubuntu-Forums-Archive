---
title: "installing audacious 1.3.2"
date: 2007-06-06
forum: Absolute Beginner Talk
---

### Post by metaverse on 2007-06-06
Howdy guys - 2nd day on Ubuntu and I've got some questions.  As user friendly as Ubuntu is I'm finding that installing thing manually through the terminal is dominating me (imagine that!).

So anyway, I'm trying to install audacious 1.3.2 manually because the newest version isn't listed in Synaptic.  I've read quite a few posts and even read through the "How to Install Anything" guide @ [http://monkeyblog.org/ubuntu/installing/#source](http://monkeyblog.org/ubuntu/installing/#source)

I've gotten some of the basics of the terminal down (just moving/browsing directories) but I'm struggling to pull this install off.  I've got the audacious file folder extracted to my home directory, I cd into that directory then try ./configure make etc and I'm getting roughly this for each

> checking build system type... i686-pc-linux-gnulibc1
checking host system type... i686-pc-linux-gnulibc1
checking target system type... i686-pc-linux-gnulibc1
checking whether make sets $(MAKE)... yes
checking for a BSD-compatible install... /usr/bin/install -c
checking whether NLS is requested... yes
checking for msgfmt... no
checking for gmsgfmt... :
checking for xgettext... no
checking for msgmerge... no
checking for gcc... gcc
checking for C compiler default output file name... 
configure: error: C compiler cannot create executables
See `config.log' for more details.


So without turning this into an essay - am I on the right track?  Do I need to download a compiler that doesn't come stock with ubuntu?  Thanks for your help in advance, and sorry if this same thing has been posted before (but I hopefully have read through most of the audacious stuff without retaining anything hah)

---

### Post by metaverse on 2007-06-06
*bump* in hopes of a quick explanation.  Ubuntu rocks, btw ;)

---

### Post by saygin on 2007-06-09
are you sure that you have gcc installed? if not try writing "sudo apt-get build essential" in the terminal.

---

### Post by mahiyar on 2007-06-09
Do you mean audacity (like the one shown in image)? Well I managed to install it through this post, [http://ubuntuforums.org/showthread.php?t=419358](http://ubuntuforums.org/showthread.php?t=419358) , please read the post and the link to it carefully, as there are errors even in the original link.

---

### Post by Monteleone on 2007-06-17
Metaverse,pls,where did you download audacious 1.3.2? I have found just a .tgz version but i don't  think i can install it on Ubuntu.

---

### Post by meborc on 2007-06-17
> **saygin said:**
> are you sure that you have gcc installed? if not try writing "sudo apt-get build essential" in the terminal.

it is "build-essential" package with a "-" :) but i'm sure you already have it installed if youread through the how to install stuff how-to... if not, install it!

---

