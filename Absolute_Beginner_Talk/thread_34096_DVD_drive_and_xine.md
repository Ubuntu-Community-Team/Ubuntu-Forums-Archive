---
title: "DVD drive and xine"
date: 2005-05-13
forum: Absolute Beginner Talk
---

### Post by odin on 2005-05-13
I just installed ubuntu and tried to play a DVD with xine.
When I try to do it I get this error message:

"error of xine's engine

there's no input plugin available to manipulate <<dvd:/>>
it may be that the sintax of MRL is wrong or the source of the file/flow doesn't exist"

This the translation of the message that I get because my ubuntu is in spanish.Anyway I dont think there are big mistakes and it is close to the real message :)

In /dev I dont have /dev/dvd only /dev/cdrom so I guess that I should recompile the kernel but I dont know how.

Can anyway help me?

Thank u very much in advance.

---

### Post by gil-galad on 2005-05-13
You probably need to install libdvdcss.  Look here [http://www.ubuntuguide.org/#dvdplayback](http://www.ubuntuguide.org/#dvdplayback)

---

### Post by odin on 2005-05-13
Thank you for your fast answer but I tried that and it doesnt work.If I run xine from a terminal when I try to play the dvd it displays a message saying:

"libdvdread: Can't stat /dev/dvd"

Could the problem be from the compilation of the kernel? Because I dont have any device in /dev called dvd.

I think I installed all posible packages (libdvdcss libdvdcss2 libdvdread3 libdvdcss2-dev libdvdread3-dev) and I can't find more.I changed the repositories in /etc/apt/sources.list and I can't find more packages related to this.

thank's :grin:

---

### Post by Stormy Eyes on 2005-05-13
There's a command you have to enter to create a link to the /dev entry for your DVD-ROM drive to /dev/dvd. Please bear with me if it seems a little complicated, as I'm going to try to cover all the possible configurations.

If you just have one hard drive and your DVD-ROM drive, then your DVD-ROM is probably **/dev/hdb**. If that's the case, do "sudo ln -sf /dev/hdb /dev/dvd".

If you have two hard drives, both of which are on your first IDE bus, and a DVD-ROM drive, then your DVD-ROM is probably **/dev/hdc**. If so, do "sudo ln -sf /dev/hdc /dev/dvd".

If you have two hard drives, a CD-ROM/CD-R/CD-RW drive, and a DVD-ROM drive, then your DVD-ROM is probably **/dev/hdd**. If so, do "sudo ln -sf /dev/hdd /dev/dvd".

When you've made your device link, don't forget to enable DMA for that drive with "sudo hdparm -d 1 $DVD_DEVICE". I'll be watching this thread for a while if you have any questions.

---

### Post by odin on 2005-05-13
I tried that and everything is working now.

Thank you very much.I was confused because I couldnt see anywhere /dev/dvd but now I understand it.

Thank's  :grin:

---

### Post by poofyhairguy on 2005-05-13
Thanks for helping out stormy.

---

### Post by garnertr on 2005-05-13
[QUOTE=odin]I just installed ubuntu and tried to play a DVD with xine.
When I try to do it I get this error message:

"error of xine's engine

there's no input plugin available to manipulate <<dvd:/>>
it may be that the sintax of MRL is wrong or the source of the file/flow doesn't exist"

In /dev I dont have /dev/dvd only /dev/cdrom so I guess that I should recompile the kernel but I dont know how.

Can anyway help me?

Thank u very much in advance.[/QUOTE]

HOWDY!  I'm running into the same problem, and I believe I can POINT you in the right direction.

What type of drive do you have?  For some reason Ubuntu is having issues w/ DVD-R/RW & CD-R/RW ROM drive (all same drive).  Its not "recognizing" it during install and you MAY have to create a symbolic link

For example I had to type:

sudo ln -sf /media /cdrom0 /dev/dvd

I believe that will get you going, however, you will have to recreate the symbolic link w/ each reboot.  My linux is lousy, so pls forgive, however, many other ppl here can probably help you more than I can.

I found this tip in the Ubuntu chat room Internet | xchatIRC

---

### Post by garnertr on 2005-05-13
[QUOTE=Stormy Eyes]There's a command you have to enter to create a link to the /dev entry for your DVD-ROM drive to /dev/dvd. Please bear with me if it seems a little complicated, as I'm going to try to cover all the possible configurations.

If you just have one hard drive and your DVD-ROM drive, then your DVD-ROM is probably **/dev/hdb**. If that's the case, do "sudo ln -sf /dev/hdb /dev/dvd".

When you've made your device link, don't forget to enable DMA for that drive with "sudo hdparm -d 1 $DVD_DEVICE". I'll be watching this thread for a while if you have any questions.[/QUOTE]

THANK YOU for your response to this ongoing issue that I'm having w/ MY LAPTOP.  My question is this:

How can I get a list of my devices?  I'd like to do this for my latop but am nervice about the commands, if I do this link and it is incorrect (for me) is there a way to undo it?  I was told that it only last until you reboot is this correct?

---

### Post by poofyhairguy on 2005-05-13
[QUOTE=garnertr]
How can I get a list of my devices?  I'd like to do this for my latop but am nervice about the commands, if I do this link and it is incorrect (for me) is there a way to undo it?  I was told that it only last until you reboot is this correct?[/QUOTE]

Linking isn't a big deal. Hmm...

hey, how can he get a list of devices?

---

### Post by NiceGuy on 2005-05-13
Hi, I've got a related problem...

I *THINK* my dvd drive is at /dev/hdc but when I try to enable the DMA using:

sudo hdparm -d1 /dev/hdc

I get the response:

/dev/hdc:
 setting using_dma to 1 (on)
 HDIO_SET_DMA failed: Operation not permitted
 using_dma    =  0 (off)

What am I doing wrong?? ](*,)   (my DVD drive is a NEC 2500A if thats any help  :-? )

---

### Post by Stormy Eyes on 2005-05-13
[QUOTE=garnertr]How can I get a list of my devices?  I'd like to do this for my latop but am nervice about the commands, if I do this link and it is incorrect (for me) is there a way to undo it?  I was told that it only last until you reboot is this correct?[/QUOTE]

GNOME 2.10 has, in its Administration menu, a "Device Manager" entry. By default, it shows everything, even BIOS devices. Just close branches of the device tree that you don't want until you start seeing references to IDE devices. Once you find your IDE devices, find your DVD-ROM device, select it, and switch to the "Advanced" tab. The first key at the top is called "block.device" and will show you which /dev/hdX your DVD-ROM is. 

As for removing the link, just do "sudo rm /dev/dvd" if you need to get rid of it. A symlink is only a pointer to a real file, so in this case you can remove the pointer. As far as it only lasting until you reboot, I can't say for sure. I haven't had /dev/dvd go away between reboots. Your experience may prove different.

---

### Post by Stormy Eyes on 2005-05-13
[QUOTE=NiceGuy]Hi, I've got a related problem...

I *THINK* my dvd drive is at /dev/hdc but when I try to enable the DMA using:

sudo hdparm -d1 /dev/hdc

I get the response:

/dev/hdc:
 setting using_dma to 1 (on)
 HDIO_SET_DMA failed: Operation not permitted
 using_dma    =  0 (off)

What am I doing wrong?? ](*,)   (my DVD drive is a NEC 2500A if thats any help  :-? )[/QUOTE]

Thanks for mentioning the model number; it's a good habit to get into when asking questions about hardware. I've tried googling for information on that device and turned up nothing of use, unfortunately. The only reason I can think of for not being able to enable DMA on a DVD drive like yours is either a IDE bus issue or a firmware issue. I can't help you with either of these, though. Sorry.

---

### Post by Stormy Eyes on 2005-05-13
[QUOTE=poofyhairguy]Thanks for helping out stormy.[/QUOTE]

No problem.

---

### Post by odin on 2005-05-26
to Tom Garner:

If you want to know the devices your system recogmizes try this command:

**lspci**.

I dont know much about it and I guess this command has some options so you get the answer you want about your devices.hope it helps.

---

### Post by Kphisto on 2005-06-27
When I attempt to open a DVD from Kaffiene (0.6 under Kubuntu Hoary) I get an unresponsive blank error window from xine which I need to force quit.
 
The first things I did to attempt to remedy this were to monkey about in the xine Engine Paramaters and update libdvdnav4 and libdvdread3 using Kynaptic.

Then I found this thread and opened a terminal and followed Stormy Eyes' recommendations. I still can't playback.

Any suggestions? Thanks in advance.

---

### Post by Zooropa on 2006-01-09
[QUOTE=Stormy Eyes]There's a command you have to enter to create a link to the /dev entry for your DVD-ROM drive to /dev/dvd. Please bear with me if it seems a little complicated, as I'm going to try to cover all the possible configurations.

If you just have one hard drive and your DVD-ROM drive, then your DVD-ROM is probably **/dev/hdb**. If that's the case, do "sudo ln -sf /dev/hdb /dev/dvd".

If you have two hard drives, both of which are on your first IDE bus, and a DVD-ROM drive, then your DVD-ROM is probably **/dev/hdc**. If so, do "sudo ln -sf /dev/hdc /dev/dvd".

If you have two hard drives, a CD-ROM/CD-R/CD-RW drive, and a DVD-ROM drive, then your DVD-ROM is probably **/dev/hdd**. If so, do "sudo ln -sf /dev/hdd /dev/dvd".

When you've made your device link, don't forget to enable DMA for that drive with "sudo hdparm -d 1 $DVD_DEVICE". I'll be watching this thread for a while if you have any questions.[/QUOTE]

Fantastic, that worked an absolute treat.

Now, all i need to do is get it to play smoother...it's quite jerky.

---

