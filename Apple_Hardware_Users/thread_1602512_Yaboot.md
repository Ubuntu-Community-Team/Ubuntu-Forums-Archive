---
title: "Yaboot"
date: 2010-10-21
forum: Apple Hardware Users
---

### Post by Hakimjo on 2010-10-21
Wicked problem:

on my mac mini ppc, 10.10 xfce and Gnome are installed correctly and it worked nicely until I also installed my preferred KDE.

After I did this, it switched to the typical KDE log screen and it seems that it has forgotten my username/password.

other problem: the internal CD drive hasn't work properly since I had installed 9.04 from that very drive and btw a disc now is stuck in it.

So, how do I get the machine to boot ?

One solution would be to start in recovery mode and make a password change.
Another solution would be to boot from an external CD that has a live 10.10 ppc disc

BUT how can I do this under YABOOT, since this is already installed (and not the mac boot loader or the intel grub)

I tried help in the boot screen but didn't find the answer there (it only proposes "c" for the internal drive)

YABOOT experts, please HELP !

Jo

---

### Post by zeroti on 2010-10-21
I don't think you'll be able to do that with yaboot alone. it's just for booting a kernel image, if i understand correctly. could you possibly boot from a usb drive? there may be an Open Firmware command that you can use to do that. (although your computer may or may not support it, i don't know.)

check this out:
[http://penguinppc.org/bootloaders/yaboot/doc/yaboot-howto.shtml/ch9.en.shtml#s9.2](http://penguinppc.org/bootloaders/yaboot/doc/yaboot-howto.shtml/ch9.en.shtml#s9.2)

you should try the "devalias" command in OF and see if there's any option to boot from usb. then enter the right command, and hopefully that will work for you. :)

otherwise, an external cd drive could work, as you said yourself.

good luck!!

---

### Post by Hakimjo on 2010-10-21
thanks for giving hope

the external CD is attached through usb - I didn't mean to refer to a stick.

I understand that I can tell yaboot where to look for a kernel which it should mount.  Very flexible for somebody who knows how to talk to yaboot and I am trying to figure this out.

The only opportunity I have to talk to the machine is when yaboot gives me a boot: prompt.  Is this when I can use the OF command ?

(I can also do a text only login later, in ubuntu itself)

I would also consider getting that stuck CD out physically and then reinstall OSX Tiger from there, hoping that then the kubuntu 10.10 install disc will be recognised again.  Is this a good plan ?  Is it possible that after installing 9.10 and upgrading to 10.10, the mac mini doesn't recognise linux install CD (it DOES see the CD as an empty CD, while it is perfectly ok on a different ubuntu machine), but would still recognise the mac install CD ?

Thanks

---

### Post by Hakimjo on 2010-10-21
ok - I see that o> for OF should appear if I start the computer with control+option+o+f pressed.  It doesn't.  Also the firmware reset command (...+p+r) doesn't seem to be heard and the startup process goes straight to boot:

---

### Post by linuxopjemac on 2010-10-23
You can boot from a USB stick. Just dd a Debian Lenny mini.iso onto a stick and let the installer have yaboot sorted out.


Just follow the first steps as here:
1. USB base system installation

Download the minimal iso [here]("http://ftp.nl.debian.org/debian/dists/lenny/main/installer-powerpc/current/images/powerpc/netboot/mini.iso"). In Gparted make the USB stick empty. Find also out here what the device name is for your stick (in my case /dev/sda but it could be different). Then copy the content of the iso to the stick:

	sudo dd if=/path/to/mini.iso of=/dev/sda

Then boot from the USB if your Mac is capable of doing this. One of my Pismo is, the other not, don't ask me why. They are both the same.
Boot in open firmware by holding option+command+o+f. Then find out which is the device:

	dev / ls

You should see somewhere usb with an extra entry disk, write that number down usb19 or something in my case. Then have a look at the devalias:

	devalias

Now it's either usb0 or usb1 which is associated with usb19. This is your boot device, in my case usb1. Then boot:
 

	boot usb1/disk@1:2,\\yaboot      (or)
	boot usb0/disk@1:2,\\yaboot

---

### Post by Hakimjo on 2010-10-23
Thanks again for the FO hints - I might need it another time.  This time, the problem was solved by opening the mac mini and extracting the cd manually from the drive and change the keyboard.  KDE then remembered the same password as I everything works just fine.  (once booted, some utilities eject even unrecognized discs).

Ubuntu really gives a new life to my ppc mac mini, for which OSX Tiger was a drag much too heavy.

But I shall be looking for more solutions to these (common) problems:

- non-recognition of normal ISO cd/dvd
- which Flash and Skype versions can I install ?

---

