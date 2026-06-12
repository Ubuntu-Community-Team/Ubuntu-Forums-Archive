---
title: "Xubntu on old machine"
date: 2008-02-13
forum: Absolute Beginner Talk
---

### Post by bvd06 on 2008-02-13
Hi Folks, 
I am trying to put Xubuntu on an old P120 with 640MB RAM and 1.5 GB HD. I am just looking for a server CLI implementation, pretty bare bones.

The bios does not support CD booting, so I have worked through creating a smartboot diskette and this works fine. I am now booting off of an alternate 7.10 ISO image that I burnt onto CD. The CD checks out and does not have any media errors. I am essentiall sitting at the Xubunto install menu, trying to do a CD based install.

I have used fdisk to wipe the partitions off the disk, and not created any new ones.

When I get to the Xubunto install menu, and select one of the install options I get the kernel load message, followed by load messages from a script and eventulally things freeze. The most meaningful scenario I think is when I select the "Install a command-line interface" option. Lots of text messages stream by, and then some intersting things happen. When it is loading keyboard stuff, the led on my keyboard goes out, it hangs a while later when messages about scssi drives come up ( I have vanilla IDE drives). I am wondering whether incomapatible drivers are being loaded, as it looks like the keyboard is getting knocked out?

So here is the big question. Where are these install scripts located? I am having a heck of a time finding this. Is there a way that I can get some control over these so that I can take a more proactive position in debugging this as opposed to just blindly changing things and looking up messages that are likely just  symptoms of a problem.  I have been reading through masses of documentation, but there is so much stuff layered onto these systems to protect the users, that its not particulary intuitive of where to go to trouble shoot this stuff. So any advice on how to troubleshoot this is appreciated. Any good SUCCINCT documetation on the boot process and install process that covers off what is really going on and not just another tour of what you will see flashing by on the screens would be very much appreciated.

Thanks in advance bvd.

---

### Post by stevejesus on 2008-02-13
I had a similar issue on a PII Lappy.  Honestly, I didn't bother troubleshooting anything.  I just tossed the disk into my desktop machine and installed from there.  In the long run it saved alot of time.
I would just put the disk into another machine, install, and then put the disk back in the P120.

By the way, I am ASTONISHED that you have crammed 640 megs of ram into that relic...  So, I am assuming that it was a typo and you meant 64 megs.

---

### Post by bvd06 on 2008-02-13
65536k Ram :)

---

### Post by .nedberg on 2008-02-13
Use alternate disk! Not the LiveCD.

---

### Post by bvd06 on 2008-02-13
Hi ned, as stated I am using the alternate.

---

### Post by .nedberg on 2008-02-13
Sorry, didn't notice that... :(

---

### Post by dstew on 2008-02-13
> I am trying to put Xubuntu on an old P120 with 640MB RAM and 1.5 GB HD. I am just looking for a server CLI implementation, pretty bare bones.
Xubuntu is a graphical desktop distribution. If you only want a CLI server, install Ubuntu Server. It only takes up about 500 Mb of disk space. I think Xubuntu takes up quite a bit more space. Maybe your drive is getting too full, and that's why the installation stalls.

---

### Post by bvd06 on 2008-02-13
Hi dstew, I might have this wrong, but I picked Xbuntu over Ubuntu as it was supposed to give me a samller server footprint. At any rate the install is not at the point anything is being written to disk. I believe its at the point where its is working out of RAM Disk. No partitioning has been done.

thanks for your response.

---

### Post by tgalati4 on 2008-02-13
You probably need a swap partition.  I think the installer needs a minimum of 128 MB of RAM.  Xubuntu will run, but it will be painful.  You will get more mileage out of Damn Small Linux for that vintage of hardware.

In addition, DSL has a CD-ROM and USB boot floppy that boots from the floppy and looks for the CDROM or USB to boot from.  This can get around old BIOS problems.

---

### Post by bvd06 on 2008-02-13
Thanks for the pointers guys. 

Steve, I did get it onto a hd on a different machine, but am having trouble running it up when back in the relic. Basically hangs quietly very early on... 

tg, thx for the DSL tip. I had time to burn a CD, its hanging, but this may be because I am using a different boot floppy then the one reccomended. Next step is to try that. I am out of time and on the road for a week and a half so will be delayed in moving this along.

---

### Post by jw5801 on 2008-02-13
> **bvd06 said:**
> Hi dstew, I might have this wrong, but I picked Xbuntu over Ubuntu as it was supposed to give me a samller server footprint. At any rate the install is not at the point anything is being written to disk. I believe its at the point where its is working out of RAM Disk. No partitioning has been done.

thanks for your response.

The difference between Xubuntu and regular Ubuntu is that Xubuntu uses the Xfce4 desktop environment, whilst Ubuntu uses the Gnome desktop environment. Since you don't want a graphical environment at all, there is effectively no difference between the two. However the Ubuntu Server Edition provides only a commandline interface, therefore it would be what you're after. Not sure how to get past the booting issues though.

On a different note, if you're looking for an extremely light-weight server system that gives you complete control over absolutely every inch of installation, I would be inclined to recommend [Linux From Scratch](http://www.linuxfromscratch.org/lfs/). However given the distinct lack of RAM, I'm not sure where you'd get a host environment to compile the initial bits and pieces, I'm sure there is a way to do it though.

---

### Post by Origin415 on 2008-02-13
Gentoo is simpler to install than LFS, and should be easier on the computer without bootstrapping and such, and can be made extremely lightweight as well, just add minimal to your use flags and -Os to your CFLAGS :D

I cant imagine using LFS over Gentoo other than for the educational experience.

---

