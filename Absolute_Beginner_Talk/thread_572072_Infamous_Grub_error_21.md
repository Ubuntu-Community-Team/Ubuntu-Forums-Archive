---
title: "Infamous Grub error 21"
date: 2007-10-10
forum: Absolute Beginner Talk
---

### Post by HackCoders on 2007-10-10
Well, some of you might have read through my other thread just below, or above this one..I've been trying to install linux all day.

I had installed it once and I got the grub error, so I emptied the partition via the Live CD, I must of did something wrong, because there were absolutely no grub files on the drive, I did a whole search, everywhere.. none at all. I even downloaded that "Easy grub" little application and burnt it to a CD, it could not repair any of it because "Error 15: File does not exist"

So; I will start all over, try to get it installed..What mounting option should I choose?

You know how it has /boot, /home etc, which one do I do?

And, when I re-install it and it comes with GRUB error again, what must I do to the config file? (Is it conf.1st?)

Some more information, I have one HDD, 160GB IDE drive..I create partition of about 50GB for the linux thing, and a 2GB linuxswap partition (I don't know what that is, but partition magic says its recommended)

Thanks for reading.

---

### Post by Bliepo32 on 2007-10-10
Grub usually is placed in /boot (other distributions might differ). I would as you said try to install it again. I also had error 15 after installation, but running it again fixed it. If I were you, I would make a small partition for /boot (around 50MB), one for /home so you don't lose personal data when you have to install once again, and one of course for / (this one will be the largest).

---

### Post by HackCoders on 2007-10-10
Another user has suggested to me that I should select the option "Use largest continous space", or something like that, instead of making all the partitions myself.

I will do that, and if that doesn't work I'll do what you said, I must go away for a while now, to install ubuntu..

Thanks :)

---

### Post by sayuki288 on 2007-10-10
manual partition your drive and install ubuntu in an ext2 or 3 filesystem and choose the / option / - means root

---

### Post by sayuki288 on 2007-10-10
no need to make a new partition foor /-boot grub

---

### Post by HackCoders on 2007-10-10
umm, I'm on the installation now

There's no option called "use the larges continuous free space"

There's only; Resize Partition #1, use freed space

And use entire disk.

Also, for the slider bar asking how much %, is it asking how much GB's to make free, or how much to resize my XP partition to or what? I'm confused..

---

### Post by HackCoders on 2007-10-10
Well I tried selecting the first option to resize, it stayed on 0% for like 30 minutes so I just clicked close..then came back to XP..

Hmmm

---

### Post by gn2 on 2007-10-10
Easiest way I know is to use a Windows based partitioning utility to create some blank unallocated space then install Ubuntu into that space.
I've found the Ubuntu partitioner is unable to shrink an NTFS partition if there's data in the way.

For all the info you'll ever need on setting up a dual-boot system, check the Hermanzone link in my sig.

---

### Post by HackCoders on 2007-10-10
OK I'll read through

Thanks for that.

---

### Post by HackCoders on 2007-10-10
OK well, now I get errors when creating a partition :(

Using partition magic, I get error 1529, I'm considering doing a format and ditching windows all up.

Is it possible in any way to emulate exe's in linux?, I can't go by without a few programs, can I use them by emulating or anything like that?

---

### Post by HackCoders on 2007-10-10
Not sure if I should keep double posting but hmm...

I've made a backup of everything that I have on my computer, that's software, music, movies, anime, everything that I use :)

I have decided to ditch microsoft all up, switching to linux as of tonight

I'm sick of having to deal with viruses on a daily basis, even with AVG and nod32, I still have to waste countless hours removing viruses and whatnot, then come the crashes and the incompatibility, and the formatting every 2 month's due to a system crash..

You know what would annoy me, if I format the drive fully then I still get Grub error 21..

---

### Post by gn2 on 2007-10-10
> **HackCoders said:**
> OK well, now I get errors when creating a partition :(

Using partition magic, I get error 1529, I'm considering doing a format and ditching windows all up.

Is it possible in any way to emulate exe's in linux?, I can't go by without a few programs, can I use them by emulating or anything like that?

Partition Magic is best used for deleting or shrinking NTFS partitions so that you can use the native paertitioning tool in Ubuntu's installer to create the required Linux partitions in unallocated space.

Better to seek native Linux apps than use Windows ones, which is possible in many cases using the Wine compatibility layer.
Which I've never used as the native apps do everything I need, and in most cases are better than their Windows counterparts.

---

### Post by HackCoders on 2007-10-10
Yeah but I need things like photoshop, that's the only thing I can think of right now that I would need.

Also, can anyone recommend an FTP program for linux?

I'm installing it right now, I did a full clean format, backed up all my media first, so hopefully all will go well...If I get the grub error for whatever reason :(

Thanks for the help guys

---

### Post by HackCoders on 2007-10-10
I did a full format and I still get error 21..

---

### Post by HackCoders on 2007-10-10
I give up.

I think after I did a format it should be able to boot fine, It's probably a hardware issue.

Weird thing is that I can't launch the x86 edition on my computer but the 64bit one works..(Only the Live CD)..I read somewhere just now that my motherboard (The Asus P5B-E) is not really supported, there's an error with the jmicron or w/e it is.. I don't know if thats true

Well anyhow, I give up...Been trying all day, perhaps I'll give the new ubuntu a go when it's officially released :)

---

### Post by Orbital75 on 2007-10-10
I have gotten this before after a fresh installation.  What I did was go into the Bios
and looked to see what it said about my Hard Drive.  It ended up that some setting
was changed ( how I don't know ) but that was the case. It wasn't labeling my drive correctly,
I pointed it to my drive and error 21 went away and it booted right into the OS.

Give that a try, Couldn't hurt.....  :KS

---

### Post by e_james on 2007-10-10
I currently have 4 PCs running ubuntu in dual boot with Windows XP, 3 of them 7.04. With one of them (7.04), no matter how many times I install ubuntu, it puts the boot files where I say and then sets the grub menu to the wrong place (for ubuntu). I have to manually edit the menu lines before booting and then edit the menu.lst file. If I get a kernel update it goes back to the wrong settings again. I suspect a bug in the grub installer.

By the way, the Gparted live CD seems to have much the same problem in the latest versions - grub can't find the correct boot files.

---

### Post by HackCoders on 2007-10-10
lol now vista will reboot the PC each time I get to the end of the BIOS loading thing /sigh

I can't edit menu.1st, it's read only, I'll format and install ubuntu again though..and try going through the BIOS.

I'll go format and try ubuntu.....again

---

### Post by HackCoders on 2007-10-10
I'm gonna get Gutsy Gibbon and try installing that one :)

---

### Post by HackCoders on 2007-10-11
Update, My bios version was from last year....when the mobo was released

I have updated to the latest BIOS version, I'm downloading Gutsy 64bit edition and I will give that a go..

---

### Post by e_james on 2007-10-11
In order to edit menu.lst you need to use sudo. Open a terminal window. Applications - Accessories - Terminal. Then type > sudo gedit /boot/grub/menu.lst

I believe I have found the solution to my own problem but it will take a bit of studying.

[https://help.ubuntu.com/community/GrubHowto?highlight=%28howto%29](https://help.ubuntu.com/community/GrubHowto?highlight=%28howto%29)

---

