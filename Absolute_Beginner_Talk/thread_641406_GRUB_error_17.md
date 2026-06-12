---
title: "GRUB error 17"
date: 2007-12-15
forum: Absolute Beginner Talk
---

### Post by czepluch on 2007-12-15
Hi.

I've been using Ubutu for half a year now, and I've been very happy with it, but now I'm going to sell my laptop to one of my friends. I've been dual-booting on my laptop. my friend and I agreed that I would get rid of the Ubuntu partition without formating the computer because he would like to have all the software pre-installed (some of it pretty expensive).

So here is my problem: I've deleted the Ubuntu partition just fine and I've made a new NTFS partiotion for storage instead. But what I didn't think of was GRUB, and now when I try to rebbot my labtop it says GRUB error 17. What do I do?

Thanks
Jacob

---

### Post by zcal on 2007-12-15
Sounds like GRUB still wants to boot Ubuntu even though its partition has been wiped.  You might want to dig around in [this]("http://ubuntuforums.org/showthread.php?t=442945") thread.

Still, I would recommend wiping the drive and reinstalling Windows (I assume that's what you're dual booting with) so that it uses its own bootloader, especially if your friend does not intend to dual boot with a Linux distro.  It's also important to get rid of all traces of your own private data.
[read this]("http://www.webopedia.com/DidYouKnow/Computer_Science/2007/completely_erase_harddrive.asp")

---

### Post by logos34 on 2007-12-15
> **zcal said:**
> It's also important to get rid of all traces of your own private data.

i.e. the porn downloads. ;-)

 
Seriously, he has a point about personal data and stuff, but if you trust your friend and there's expensive sw you don't want to dump, then just reinstall the NTLDR with [Super Grub disk]("http://supergrub.forjamari.linex.org/").

---

### Post by ashikahamed on 2007-12-15
There is a boot disk called super grub disk.This will help you restore your windows partition if you have deleted the ubuntu partition. Please visit the following links for further instructions.
[http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html](http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html)
[http://supergrub.forjamari.linex.org/?section=home](http://supergrub.forjamari.linex.org/?section=home)

---

### Post by czepluch on 2007-12-15
> **logos34 said:**
> 
 
 then just reinstall the NTLDR with [Super Grub disk]("http://supergrub.forjamari.linex.org/").

How do I install the NTLDR. ??

---

### Post by logos34 on 2007-12-15
> **czepluch said:**
> How do I install the NTLDR. ??

Select 'Windows' option on the SGD menu

Windows -> Fix Boot offers the equivalent of fdisk /mbr to restore a system for booting Windows.

---

### Post by czepluch on 2007-12-15
> **logos34 said:**
> Select 'Windows' option on the SGD menu

Windows -> Fix Boot offers the equivalent of fdisk /mbr to restore a system for booting Windows.

thanks. But its now booting. some other program boots that doesnt do what SGD is supposed to do.

---

### Post by czepluch on 2007-12-15
The program that boots is called Caldere DR- or DS-DOS ? Why is that happening? The file I downloaded is downloaded from this site: [http://forjamari.linex.org/frs/?group_id=61&release_id=499]("http://forjamari.linex.org/frs/?group_id=61&release_id=499")

---

### Post by czepluch on 2007-12-15
bump

---

### Post by logos34 on 2007-12-15
that the right site...it's been a while since I used sgd to restore win boot (usually use the xp disc)...lemme try it and see what happens...although it may use parts of caldera linux boot program, dunno.

---

### Post by czepluch on 2007-12-15
> **logos34 said:**
> that the right site...it's been a while since I used sgd to restore win boot (usually use the xp disc)...lemme try it and see what happens...although it may use parts of caldera linux boot program, dunno.

Okay, but I still don't get why it doesn't work, but it would be nice if you would try to see if it works for you :)

---

### Post by psusi on 2007-12-15
You just need to restore the windows MBR.  Boot the windows install cd into recovery console and run the FIXMBR command.

---

### Post by logos34 on 2007-12-15
I just tried it and it boots into windows normally, nothing indicated before the Microsoft splash screen.
  
SGD writes a  new IPL code to the MBR (pointing to the windows partition with NTLDR):
> 
dd (cd)/boot/sgd/brs/winnt.bin (hd0) 0 0...

So I'm not sure what happened in your case.

You might read through Herman's [page]("http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html").

---

