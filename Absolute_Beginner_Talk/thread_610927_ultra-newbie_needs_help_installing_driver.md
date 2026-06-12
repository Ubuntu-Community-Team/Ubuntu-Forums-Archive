---
title: "ultra-newbie needs help installing driver"
date: 2007-11-12
forum: Absolute Beginner Talk
---

### Post by saiorse44 on 2007-11-12
Helllo everybody. :KS

I am a Windows user that is beginning to make the migration to Linux.

I wish to install the experimental drivers for my Technotrend budget S2-3200 card, I have tried but I usually end up with a screen full of errors. 

Could somebody be so kind as to write me a short beginners guide on how to get this card up and running on a clean install of Mythbuntu 7.10.

The drivers are available from here:[http://jusst.de/hg/multiproto/]("http://jusst.de/hg/multiproto/")

I have tried going into the directory of the extracted files and typing make but to no avail.

Are there other things I need to be doing like V4L?

Many Thanks,
Rob

P.S.  I tried posting this in the mythbuntu forum but to no avail :(

---

### Post by xiombarg on 2007-11-13
Have you set up your build tools? I've not used Mythbuntu, so don't know what's installed by default. For Xubuntu, one must first intsall a package such as 'build essential' (I think that's what it's called).

Do you know how to use a package manager such as Synaptic?

For more help, you can post the text shown in your terminal window, when you try to build the source code. The specific error messages can give people on the forums more clues to help you.

Good luck.

edit- P.S. I'm only really a beginner, too.

---

### Post by saiorse44 on 2007-11-28
Hi there. many thanks for your reply. :) 

On a clean install of Mythbuntu I downloaded and unzipped the drivers and got the following when typing make into the terminal in the unzipped directory:

```

rob@MythBox:~/Desktop/multiproto$ make
make -C /home/rob/Desktop/multiproto/v4l 
make[1]: Entering directory `/home/rob/Desktop/multiproto/v4l'
scripts/make_makefile.pl
No version yet.
Updating/Creating .config
Preparing to compile for kernel version 2.6.22
File not found: /lib/modules/2.6.22-14-generic/build/.config at ./scripts/make_kconfig.pl line 31, <IN> line 4.
make[1]: Leaving directory `/home/rob/Desktop/multiproto/v4l'
make[1]: Entering directory `/home/rob/Desktop/multiproto/v4l'
Updating/Creating .config
Preparing to compile for kernel version 2.6.22
File not found: /lib/modules/2.6.22-14-generic/build/.config at ./scripts/make_kconfig.pl line 31, <IN> line 4.
make[1]: *** No rule to make target `.myconfig', needed by `config-compat.h'.  Stop.
make[1]: Leaving directory `/home/rob/Desktop/multiproto/v4l'
make: *** [all] Error 2
rob@MythBox:~/Desktop/multiproto$

```

Can you see where im going wrong?

---

### Post by pjremy on 2007-11-28
i am having the exact same problem trying to compile the isley pvr usb2 driver. the research i've done mentions installing "another" kernel source tree and compiling the driver against the kernel. now that is where i am totally lost. i have yet to find any threads that takes me through those steps. i wish you well in solving this for your good fortune is my good fortune and vice versa. i'll be sure to post any additional info i come across.

---

### Post by saiorse44 on 2008-01-09
Hi, many thanks for your replies.
Sorry for not getting back sooner on this one.

I got over my error messages by installing the kernel headers as advised by a poster on the TechSpot forums.
[http://www.techspot.com/vb/topic92558.html]("http://www.techspot.com/vb/topic92558.html")

The problem I have now is that although the /dev/dvb folder has now appeared/ it contains another folder called adapter0 in this folder there are four files called:
demux0
dvr0
fontend0
net0
however all four files are empty.

MythTV backend setup also hangs whilst tring to add a new capture card.

Any ideas?
Rob

---

