---
title: "School Ubuntu"
date: 2008-03-12
forum: Apple PPC Users
---

### Post by AdHavoc on 2008-03-12
I am starting a project at my school and I plan on converting around 70 iBook G3's running Mac OS9 to some variant of Linux.  I am looking at Edubuntu right now but not sure if there will be any issues with connecting to the school network / etc.  I will post the technical specs a little later when I get a hold of them, but for now, I think it's safe to assume it's the standard iBook G3.  If anyone has any suggestions for these aging Macs, feel free to comment.

---

### Post by stream303 on 2008-03-13
Sounds great!

To help with inventory, have you taken a look at the G3 ibook specs here:

[http://www.everymac.com/systems/apple/ibook/index-ibook.html](http://www.everymac.com/systems/apple/ibook/index-ibook.html)

Aside from online references, one of the best descriptions of how to install, run and administer Edubuntu I've seen has come from Chapter 10 "Using Edubuntu" of

"The Official Ubuntu Book  - Second Edition"
Prentice Hall publishers
ISBN 13: 978-0-13-235413-4
ISBN 10: 0-13-235413-6

Will the course be about computing or other subjects?  If the material is web-based and relies on flash, you may want to consider that ppc doesn't have perfect flash support yet.

---

### Post by AdHavoc on 2008-03-13
After examining the hardware, the iBooks are of Family M2453, which I believe is a NewWorldMac (at least I hope so lol).  It's the blue clamshell version with 128mb memory, so I'm not sure if that's enough to run Edubuntu.  Xubunutu is certainly an option, but I'd rather have the advantages of an education-oriented distro rather than something simply lightweight and somewhat feature lacking.  I suppose I'll try to put the PPC port of Edubuntu Gutsy/Feisty (I also heard that maybe Feisty is better in terms of PPC computers?) on them and see if it runs.  

Also, to answer your question, they are going to be used as general purpose laptops for younger students (writing papers, surfing the internet, etc.).  The older students get newer (circa 2006) HP laptops running Windows XP.  Convincing the administration to convert THEM to Linux is a whole other story ;p

---

### Post by oswaldkelso on 2008-03-13
You may want to take a look at skolelinux the project has been going a few years and ppc wll be supported for a good while yet as it debian based. If they're run as thin clients those machines are well with in spec. 

[http://www.skolelinux.org/en/node/1](http://www.skolelinux.org/en/node/1)

[http://wiki.debian.org/DebianEdu/Documentation/Etch/Requirements](http://wiki.debian.org/DebianEdu/Documentation/Etch/Requirements)

---

### Post by stream303 on 2008-03-13
With only 128mb on board, I think you'd be happier with Xubuntu.

I took a look at the Edubuntu downloads, and it appears that you need 192 mb to install the ppc version, which is mostly likely the live-cd desktop.  I don't see an option for an "alternate" install which uses less resources during installation:

[http://cdimage.ubuntu.com/edubuntu/ports/releases/7.04/release/](http://cdimage.ubuntu.com/edubuntu/ports/releases/7.04/release/)

Perhaps OswaldKelso's suggestion to look into Skolelinux might save the day.  I'd definitely contact the Edubuntu people to see about reducing the ram requirements with an alternate image if one could be made available.

---

### Post by AdHavoc on 2008-03-13
> **oswaldkelso said:**
> You may want to take a look at skolelinux the project has been going a few years and ppc wll be supported for a good while yet as it debian based. If they're run as thin clients those machines are well with in spec. 

[http://www.skolelinux.org/en/node/1](http://www.skolelinux.org/en/node/1)

[http://wiki.debian.org/DebianEdu/Documentation/Etch/Requirements](http://wiki.debian.org/DebianEdu/Documentation/Etch/Requirements)

I might have to check it out.  But can laptops be run as thin clients?  I thought you needed an ethernet connection for PXE boot?  I'm not too sure about that though, so I'm probably misinformed.

> **stream303 said:**
> With only 128mb on board, I think you'd be happier with Xubuntu.

I took a look at the Edubuntu downloads, and it appears that you need 192 mb to install the ppc version, which is mostly likely the live-cd desktop.  I don't see an option for an "alternate" install which uses less resources during installation:

[http://cdimage.ubuntu.com/edubuntu/ports/releases/7.04/release/](http://cdimage.ubuntu.com/edubuntu/ports/releases/7.04/release/)

Perhaps OswaldKelso's suggestion to look into Skolelinux might save the day.  I'd definitely contact the Edubuntu people to see about reducing the ram requirements with an alternate image if one could be made available.

Edubuntu has a LiveCD version, a regular install version (analogous to the Alternate Install for other Ubuntu distros), and an addon CD with extra programs and repositories.  Yet even so, I think you might be right that Edubuntu would push it.

---

### Post by doorknob60 on 2008-03-14
Yeah, with only 128 MB of RAM, I would NOT recomend using Gnome (Edubuntu or ubuntu), but Xfce (Xubuntu), which I use on my brother's computer and it's pretty nice IMO. Also, if you wanted, you could try Debain, which is very similar to Ubuntu, but I've heard it works better on PowerPC, and it's still supported. Here's a direct link to Debian with Xfce if you want to give it a shot: [http://cdimage.debian.org/debian-cd/4.0_r3/powerpc/iso-cd/debian-40r3-powerpc-xfce-CD-1.iso](http://cdimage.debian.org/debian-cd/4.0_r3/powerpc/iso-cd/debian-40r3-powerpc-xfce-CD-1.iso)

---

### Post by oswaldkelso on 2008-03-14
> **AdHavoc said:**
> I might have to check it out.  But can laptops be run as thin clients?  I thought you needed an ethernet connection for PXE boot?  I'm not too sure about that though, so I'm probably misinformed.



Edubuntu has a LiveCD version, a regular install version (analogous to the Alternate Install for other Ubuntu distros), and an addon CD with extra programs and repositories.  Yet even so, I think you might be right that Edubuntu would push it.

The laptops all have ethernet ports. The main reason I suggested skolelinux was that edubuntu for power pc will be stuck at 6.06 lts where as skolelinux has just added ppc and debian will support it for a long while yet. 

Also I had edubuntu on my daughters imac 333 ppc with 256mb of ram. It was good but slow so I did a custom debian install to improve performance (link at bottom) running it as a thin client would would have  made a big difference but not really applicable I my case.

---

