---
title: "Whoops...(Idiot to Linux)"
date: 2006-02-19
forum: Absolute Beginner Talk
---

### Post by jsdewey on 2006-02-19
Sorry if I have this in the wrong forum, but I'd consider myself as a complete beginner to Linux and Ubuntu.....

Alright, so I have two HDs, a 200 Gig and a 30 Gig. I installed Windows 2000 on the 200 gig and Ubuntu on my 30 gig. Thing is, I can no longer access Windows. It wants to load something called GRUB and gives an error "21" (i'm guessing GRUB is what allows me to dual boot?). My buddy says I screwed up my MBR (I really don't know what that is). I would like to access Windows again, because I forgot to make recent back ups because of a lack of CDs to burn, and there are files I would like to recover. It gives me the option to boot Ubuntu on the 200 gig in several different oprtions, like recovery mode and such. Any way to recover my files, or do I have to install Windows on my 30 gig? Is it also possible for my just to unplug the drive I don't want running (Like if I wanted Windows, I would unplug the drive with Ubuntu, and vice-versa) without any problems? I use Ubuntu 5.10.

---

### Post by gnutux on 2006-02-19
try to reinstall Ubuntu/Kubuntu but if you really want to try another Linux distribution with better noobie tools, then use SuSE.

gnutux

---

### Post by Coelocanth on 2006-02-19
MBR is you Master Boot Record, which is what controls if you'll boot at all and what OSes you have the choice of booting. If you can't access your Windows partition, you can try restoring your MBR. I'm not sure if this method works for 2000, but it will for XP:

boot from your Windows install CD
choose "fix an existing install using recovery mode"
choose your WIN installation, type fix mbr.

Like I say, this works for XP - not sure about 2000. You may want to try a Google search. If it does work, it will restore your MBR so you can boot Windows. You'll probably have to create a boot floppy to get into Ubuntu after doing this, so I advise you to make that with Ubuntu before trying to fix your MBR.

Perhaps others with more knowledge than I (I'm a complete noob to Linux) can offer a better solution, so keep checking the thread.

---

### Post by Netisan on 2006-02-19
[QUOTE=gnutux]try to reinstall Ubuntu/Kubuntu but if you really want to try another Linux distribution with better noobie tools, then use SuSE.

gnutux[/QUOTE]
Reinstallation and reboot are Bill Gates know-hows ;)
Probably physical disconnection of Ubuntu HDD will be better temporary action. Something goes wrong with GRUB but this is fixable.

---

### Post by jsdewey on 2006-02-19
Thanks everyone! I will try everthing so far (except reformatting). Just another noob question. How do I make a boot disk in ubuntu? :lol:

---

### Post by suziequzie on 2006-02-19
I'm using a boot disk in Kubuntu to simplify things for my boyfriend (he doesn't get the concept of a boot menu).

The Trick Is This: Watch the install process. Don't pick up a book, or answer the phone, or do dishes or anything else: You'll want to watch for 2 screens: 

When it comes to installing Grub, it will scan your drives for other OS's. It will then ask if you wish Grub to be installed to MBR.
Say no. Here's where you'll see it: 

[http://d-i.alioth.debian.org/svn/debian-installer/installer/doc/talks/d-i_internals/096-grub-install-mbr.png]("http://d-i.alioth.debian.org/svn/debian-installer/installer/doc/talks/d-i_internals/096-grub-install-mbr.png")
 
(but yours may say It has found windows or some other OS's... it will include them in the boot menu it writes for you) 

It will then give you this screen where you can choose where to install it ... look at the last line of text showing (not the input line, but their instructions line).

[http://lists.debian.org/debian-boot/2004/12/png00000.png]("http://lists.debian.org/debian-boot/2004/12/png00000.png")  

(Look at the blue and grey screen: ignore the VMWare stuff around the blue screen).

Put your blank floppy in the drive, then type in "/dev/fd0" (no quotes).  

When it's done, it will pop the CD tray open so you can remove the install disk. Leave the floppy in and let it reboot. 
 
Let me know if it works for you. 

[QUOTE=jsdewey]Thanks everyone! I will try everthing so far (except reformatting). Just another noob question. How do I make a boot disk in ubuntu? :lol:[/QUOTE]

---

### Post by Plank117 on 2006-02-20
If you just gotta get those files off your hard drive, I have a simple solution for you that requires no knowledge of GRUB/Ubuntu whatsoever. Take the hard drive out, stick it in another computer, boot off of it, and make your backups. Then you can mess around with GRUB. It doesn't really solve the problem you're trying to address, but at least you don't have to wait until you've got GRUB fixed to get your stuff off that drive.

---

