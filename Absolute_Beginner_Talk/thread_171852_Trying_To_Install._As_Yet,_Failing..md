---
title: "Trying To Install. As Yet, Failing."
date: 2006-05-07
forum: Absolute Beginner Talk
---

### Post by Omicron Machine on 2006-05-07
So my tale of woe basically starts when my younger sister's computer crashes beyond all reson. As in, no one had seen the desktop in ages. It had stopped working and there was nothing to be done. She got a new one, and my Mum gave me that one to "play with". I checked it out, hardware's old but in working order. So I plunged in and convinced it to format C:. Eventually. I still have the Windows98 (yuck) cd and floppy bootdisk that it had before, but I decided I wanted to have something different, a new learning curve, more experience, etc. I wanted to experiment with Linux, and Ubuntu looked like a good choice. It was one I had some notion of the general idea of. 

So, now I've burned myself my CD with the .ISO. But the computer I'm installing to will only accept booting from the floppydrive. I turn it on, and since C: is empty, it says "invalid system disk". It won't look at the CD-ROM untill it's heard from the floppy drive. I've tried various different .img files I've found around, with no measurable results. The best results I've had have been a result of it detecting a bootable disk in the floppy drive. It goes through it's little thing. It says to remove the floppy disk and press any key to reboot. I do so. It reboots and wants the system disk again. Won't do anything else. So I give it the system disk. It does the exact same thing, tells me to do the same thing, and then repeats again when I do.

What I'm going for is a machine running only Linux. Ideally, Windows is entirly absent. I have to start the whole process with something on a floppy disk. So...what do I do now?

---

### Post by Resurrection on 2006-05-07
Two questions:

1)  Did you burn the .iso properly (i.e. a disc image) instead of as a data disc?

2)  Have you tried going into BIOS and setting the system to boot from CD-Rom prior to the hard drive?  As long as you burn the disc properly (and slowly enough) you should be able to boot from it.  I can't imagine that that your machine is so old you can't boot from CD.  Just need to change the BIOS.

---

### Post by craigmac on 2006-05-07
My only suggestion is for you to download a BIOS update for your particular motherboard. There is usually an upgrade that allows for advances in technology like bootable CDs - LOL.

It won't be very difficult to install the upgrade. Most likely it will be installable on to a floppy and then you'll be able to flash your BIOS and then you can work from the bootable CD.

Let us know if you manage to find the BIOS upgrade. If you need help, let us know what sort of MB you have and then we can try and find the right files from the Web.

---

### Post by uzi09 on 2006-05-07
if i understand correctly, ur porbably sitting at a "caldera" a:\ prompt. (i think that's what it's called).

this is usually caused by imporperly burning the cd image.


basically, there are lots of .img (image) files out there. when u burn them, u have 2 ways of doing them:
1) burn as a BOOTABLE DATA DISC
2) burn as an IMAGE

some images are preconfigured (the more recent ones tend to do this) to be burnt as an IMAGE and they'll automatically make the cd bootable. so all you have to do is go to ur cd burning program (if u specifiy which one, someone could probably give u a step-by-step) and burn an image cd.
if u burn one of those preconfigured images as a "bootable" cd, u'll end up with the a:\ prompt.

other images aren't preconfigured to be burnt using the plain ol' "burn image to cd" way. these need to be burnt as a BOOTABLE DATA DISC.

give the burning a retry, and let us know what u come up with.


goodluck,
uzi


EDIT: okay, so i decided to re-read and looks like i completely misunderstood what u were saying :S. lol, but i believe i may have a solution to your actual problem too :D. just gimme a minute to find the exact procedure. bascially i'm googling (and also checking ubuntu's site) about how to burn an image to a cd (regular img i think) and then using a floppy to boot from cd. i'll post up what i come up with soon.

EDIT(2): here are a couple of links -- careful, the second one is for red hat, but i think it should be the same procedure for ubuntu.
- [http://www.linuxiso.org/viewdoc.php/isofaq.html#boot](http://www.linuxiso.org/viewdoc.php/isofaq.html#boot)
- [http://www.linuxmigration.com/quickref/install/media.html#createfloppy](http://www.linuxmigration.com/quickref/install/media.html#createfloppy)

---

### Post by confused57 on 2006-05-07
Make sure you burn the iso file as an "image", your cd burning software should have an option to do this.  Forgot to mention burn the cd as an "image" as slow as your software allows you(4x-8x).  

To boot from CD on an older machine, you'll need "Smart Boot Manager":

[https://wiki.ubuntu.com/SmartBootManagerHowto](https://wiki.ubuntu.com/SmartBootManagerHowto)

The instructions say to do it with DOS commands, but you can do it in Windows.
Download the smartbootmanager and the rawrite into the same folder.  Been awhile for me, but I think you extract the rawrite zip file then double-click on the .exe file.  The program will open in a window, which should be pretty self explanatory to copy smartbootmanager as an image to the floppy.  Boot your computer with the bootfloppy and your Ubuntu installation cd both inserted.
Smartbootmanager will open with a menu to select to boot from the cd drive.
I think you press "F2" to save, then enter;  you may have to do it a couple of times(I usually have to, I get an error message at first), but it'll eventually boot from your cd.   I have an old computer that cannot boot from the cd drive and that's how I did it.  With an older computer, you'd be lucky to find a bios upgrade.

Your win98 boot floppy may have an option to boot from CD, try that first.

---

### Post by n3tfury on 2006-05-07
Exactly how old is this hardware?  I had a IBM desktop w/ P166 that absolutely would not boot from CD (duh).

*edit* looking at confused's post, that would have saved me from scrapping that machine!  it was my first ever box :(

---

### Post by jkbritt on 2006-05-07
I had the same problem. I fixed it by going into the BIOS, and changing the order of the Boot drives.  Tell it to Boot from your CD first, and your disk second (just in case you have to boot using that at some point).  Look up your motherboard's specs to find the key combination to access your BIOS. For my notebook, I had to hold the Del key.

---

### Post by Omicron Machine on 2006-05-07
Thanks, I went into the BIOS and now I have it checking for CDs first. Everything was going fine, and then it said something along the lines of my CPU not supporting it and I need the 32-bit distribution (I think that's the right word, there, that last). I get the general idea of what this means, but I'm not sure what I should do about it precisly (the computer, you remember, is kinda old. I was planning on updating the rest of it once I had a working operating system on it)....

---

### Post by Resurrection on 2006-05-07
[QUOTE=Omicron Machine]Thanks, I went into the BIOS and now I have it checking for CDs first. Everything was going fine, and then it said something along the lines of my CPU not supporting it and I need the 32-bit distribution (I think that's the right word, there, that last). I get the general idea of what this means, but I'm not sure what I should do about it precisly (the computer, you remember, is kinda old. I was planning on updating the rest of it once I had a working operating system on it)....[/QUOTE]
Sounds like you downloaded the 64bit version, which obviously won't work on your 32 bit processor.  

You need the regular 32 bit version, and then burn that.

---

### Post by Omicron Machine on 2006-05-07
Yeah, that's what I thought. Where can I find it? I don't see it on the directory tree where I found the 64 bit version, ubuntu-5.10-install-amd64.iso . Or does it this one? ubuntu-5.10-install-i386.iso

---

### Post by Resurrection on 2006-05-07
[http://mirror.mcs.anl.gov/pub/ubuntu-iso/CDs/5.10/]("http://mirror.mcs.anl.gov/pub/ubuntu-iso/CDs/5.10/")

Yes you are looking for the ubuntu-5.10-install-i386.iso

You can always just click on "PC (Intel x86) install CD" on the link above.

---

