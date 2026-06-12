---
title: "Ubuntu Installation Questions From a Newbie"
date: 2006-09-10
forum: Absolute Beginner Talk
---

### Post by LunaticStrain on 2006-09-10
Hi, I'm relatively new to Linux. I've tried using Gentoo and while it's alright, I don't think I'm ready for it. I decided to use Ubuntu, but here's what I want to do. I have an OLD iPod. I recently got a new 30gb Video iPod, so this old thing is useless to me. So what do I want to do? Turn it into nothing more than a USB hard drive, and then install Ubuntu on it like I would any other hard drive, and use it to boot from. I am going to be using this on my Compaq Presario Laptop, x86 Arch and running Windows XP. I bought the Laptop from Best Buy and didn't get a Windows XP CD with it, so I'd prefere a way to do this that won't require the CD, but if need be I can go buy a CD (Not something I really want to do.) So I am looking for a way to install Ubuntu on my iPod, using the iPod as just an external USB hardrive and be able to choose (when the iPod is plugged in) at start up wether I want to boot windows or Ubuntu. Any help is GREATLY appreciated as I have searched all over the net and all I seem to find about installing Linux on an iPod is to have Linux on there for programs and still use the iPod for music, where as I just want to use it as a USB hard drive. Thanks

---

### Post by mbmccormick on 2006-09-10
Well first of all. Make sure in your BIOS that you can "Boot from USB" or "Boot from Removable Disk". This will determine the possibility of what you want. Then, you'll need to format you iPod into the FAT filesystem, by rightclicking on it in Windows XP's My Computer. Then, insert the Ubuntu Live CD (with ipod connected). Boot to CD, then double click install. Follow the instructions. Then, it should detect all hard drives connected to the computer, including the iPod. Select that as your install media. Wait until its done. Then it should be bootable. You'll need to hit ESC or F1 or F2 at boot to change boot order. I'd set it to the following order: USB DRIVE, CD ROM, FLOPPY (if applicable), HARD DRIVE. This should work.

---

### Post by LunaticStrain on 2006-09-10
Awesome, thanks for answering so quickly. I'll let everyone know if this works. Also, what architype should I select for Ubuntu? X86? Something else? Appreciate the help.

---

### Post by whizbaby on 2006-09-10
It's not that simple to get ubuntu on your ipod (if it's what you want), but there's ipodlinux
[http://ipodlinux.org/Main_Page](http://ipodlinux.org/Main_Page)
(the basic problem is that you need a kernel for the ipod which doesn't come with ubuntu)

---

### Post by mbmccormick on 2006-09-10
if you are using a computer that is 64 bit... use x86. it all depends on your processor. check with the download page as i am not so sure... PPC is for Apple PowerPC processor computers, 386 is for intel based processors, so maybe x86 is for AMD...

and WhizBaby, i believe LunaticStrain is trying to get ubuntu to boot from his ipod onto his computer, and not use linux on his ipod, which would replace the ipod's os.

---

### Post by bodhi.zazen on 2006-09-10
> **whizbaby said:**
> It's not that simple to get ubuntu on your ipod (if it's what you want), but there's ipodlinux
[http://ipodlinux.org/Main_Page](http://ipodlinux.org/Main_Page)
(the basic problem is that you need a kernel for the ipod which doesn't come with ubuntu)

Nice link, thank you.

LunaticStrain is using his ipod  as a hard drive and thus needs a kernel for his CPU and not the ipod.

---

### Post by whizbaby on 2006-09-10
Soo tired ...can't...hardly..read...[-(

---

### Post by LunaticStrain on 2006-09-10
Alright, thanks guys. I checked my BIOS and I changed the order so that the hardrive I named iPodLinux boots before my Laptop hardrive, so I think I'm good. All that's left is downloading and installing. Also, since I'm installing onto my iPod, I just want to make sure that this isn't going to effect my Laptop or Windows instillation right? Thanks for the help again.

---

