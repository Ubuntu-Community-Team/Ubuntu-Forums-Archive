---
title: "Ubuntu on Xserve?"
date: 2007-05-30
forum: Apple Intel Users
---

### Post by mikie75 on 2007-05-30
Hi all

Has anyone had any success with installing either Ubuntu 6.06.1 or 7.04 server and desktop on an Intel Xserve? I am running a 2 x 2.66 GHz Dual Core Intel Xeon.

I can't even boot off any of the install cd's that I have downloaded. Anyone else having this trouble?

Mike

---

### Post by blazercist on 2007-05-30
this is a server box?  why use the live cd?  use the server install instead or perhaps the alternate CD(text based installer)  If you NEED a GUI then you can always install the server CD and then download and install the GUI its as easy as "sudo apt-get install ubuntu-desktop"

---

### Post by mikie75 on 2007-05-31
Hi

Yes this is a server box, and I wanted to boot from a Live CD as I don't want to blitz the OS that is installed just yet, as it will take time to reinstall it, compile and install all the source code, and configure the various applications as a result. 

I would like to see if there are drivers for the NIC's and also for the HBA's (but I am not sure as to whether these will work or are loaded as part of a Live CD).

Certainly I don't need a GUI; all my administration is over a CLI. The department here has a support contract with the peeps from Ubuntu so I think that it is necessary that I do install from the Live CD in order to have that contract honoured. However, I am not 100% sure.

The main problem, that I will reiterate, is that I am unable to boot from _any_ of the cd's that I have downloaded from the Ubuntu site. I have tried the same cd's on other Intel Macs (desktops , not servers), and they have booted with no issues. I was wondering if anyone else had encountered a similar issue with the Intel servers. As I am unable to access the EFI I am a bit stuck.

Mike

---

### Post by blazercist on 2007-05-31
well can you try to remove the "quiet splash" boot options from the boot line and telling us where exactly it is that the live cd fails?  do you even get the option to "start or install ubuntu"?

also if you have a spare HD, i would suggest replacing the current one with the spare and installing the server CD for testing... if the live cd doesn't work there are very few options as far as getting a fix.

---

### Post by magicfab on 2007-08-29
> **mikie75 said:**
> Hi
[...]
Certainly I don't need a GUI; all my administration is over a CLI. The department here has a support contract with the peeps from Ubuntu so I think that it is necessary that I do install from the Live CD in order to have that contract honoured. However, I am not 100% sure.

Hi there,

I can assure you you don't need to install from any specific CD to get support from Canonical.

If you need assistance for this install, call us and we'll gladly assist. G4s and G5s have official support until Ubuntu 6.10, but the community also provides ISO images for latest releases. Intel-based Xserves have regular support by using either 32bit ort 64bit machines.

Cheers,

---

### Post by drewsta on 2008-05-08
Hi!

That sounds great, although I'm surprised we haven't seen more people talking about running apple intel xserve's on linux platforms. The 3d world is hurting for 64 bit performance, and I have several people interested in using apple hardware if we can use 64bit for rendering...

I've submitted a contact request with you, look forward to hearing from you soon.

Thanks!

---

