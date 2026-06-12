---
title: "Still about LTSP problem"
date: 2007-11-15
forum: Absolute Beginner Talk
---

### Post by farifk on 2007-11-15
everything was great until...
there are several computers that do not have the PXE boot roms, so I need to build a boot floppy for all of them. I started with one of the computer, but before i go any further, let me remind you my server and client configuration:

server: amd64 athlon 1GB of RAM, i have built 2 client images: amd64.img (by mistake), and i386.img.

client: p3 computers, via cyrix III/ nehemiah computers, P4 computers with at leat 64MB of RAM on all of them.

my questions are:
1. I tried to boot one of the p4, with boot floppy with no luck. i used rom o matic 5.4.3, with pxeloader_keep_all turned on. But the thing does not get very far. it got to boot until usb port set up, an then nothing, no more progress. I look at the syslog in the server and found out that it is assigned to the wrong image file (to /opt/ltsp/images/amd64.img). The thing is, I have one other p4 machine that has PXE boot rom, and that one boot flawlessly. Any setting that I miss? or maybe i should just delete the amd64.img? 
2. how do you delete the whole amd64 built client? it was built by mistake, I will never boot an amd64 machine.

thanks
frank

---

### Post by Lem on 2007-11-15
Look in /opt/ltsp/ . i386 will be your 32bit build. Not sure what the 64bit version is called, but you'll need to

```
sudo rm -rf /opt/ltsp/x64
``` Replace x64 with whatever the directory is called.

---

### Post by farifk on 2007-11-18
do i need to delete amd64.img in /opt/ltsp/images too?

---

### Post by farifk on 2007-11-20
one more thing, how about /var/lib/tftpboot/ltsp/amd64
delete that one too?

---

