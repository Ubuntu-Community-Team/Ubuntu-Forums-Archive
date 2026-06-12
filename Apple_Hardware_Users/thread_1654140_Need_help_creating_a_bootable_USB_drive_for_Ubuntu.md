---
title: "Need help creating a bootable USB drive for Ubuntu from a Mac, for a PC netbook"
date: 2010-12-27
forum: Apple Hardware Users
---

### Post by Ripp_Steakface on 2010-12-27
Hey all. I'm in a predicament. I stupidly deleted the partitions on my netbook's hard drive that contained Ubuntu, and now I'm stuck with the GRUB loader with the Error 22 message.

I've downloaded Ubuntu 10.10 Netbook edition, and I tried using the instructions to create a bootable USB drive, but my PC won't boot off it. I've already checked the netbook's BIOS to make sure "Removable dev." is the first boot option, and I had Ubuntu on the netbook previously and had used a similar method, but I had done it all using Windows XP.

Is the problem that I'm creating a bootable USB drive in OS X, for a Windows PC? When I use Terminal to create the Ubuntu USB drive, is it writing it in a way that only a Mac can read? If so, where do I go from here? My netbook is completely unusable right now, as it goes through the BIOS and directly to Error 22.

Thank you for any help you can provide! Also, I'm sort of a Ubuntu / Linux / OSX Terminal noob, so if I need to type some commands, go easy on me :)

---

### Post by amsterdamharu on 2010-12-27
Did you try [unetbootin]("http://unetbootin.sourceforge.net/"), it always worked for me but I am not sure if a mac can boot off a syslinux USB stick.

---

### Post by Ripp_Steakface on 2010-12-27
It doesn't look like UNetbootin runs on a Mac. My main computer is a Mac, which is what I have to use to create this USB drive. The computer I'm trying to fix currently has Windows on it (the netbook).

---

### Post by amsterdamharu on 2010-12-27
I thought you had Ubuntu running on the MAC, and it's available for ubuntu (out of the repositories). so the command "sudo apt-get install unetbootin" would install it.

---

### Post by Ripp_Steakface on 2010-12-28
Is anyone else able to help?

---

### Post by amsterdamharu on 2010-12-28
Does your MAC boot off it?

---

### Post by mikcarroll on 2010-12-29
Is downloading and burning a live or desktop cd an option? Vmware.

---

