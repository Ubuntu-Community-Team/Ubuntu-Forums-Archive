---
title: "Unbuntu 6.06 install on Parallels, stalls..."
date: 2006-06-13
forum: Absolute Beginner Talk
---

### Post by syrcle on 2006-06-13
Hi all,

I'm not sure why I'm running into this problem, but let me describe what's happening.  I have a MacBook running Parallels, and I'm trying to install Ubuntu 6.0.6, but when I get to the installation setup when booting from an image file or CD, the installation stops at about 15%, and just sits there.  This is my first time using Ubuntu, so any help would be greatly appreciated.

---

### Post by kaje on 2006-07-08
> **syrcle said:**
> Hi all,

I'm not sure why I'm running into this problem, but let me describe what's happening.  I have a MacBook running Parallels, and I'm trying to install Ubuntu 6.0.6, but when I get to the installation setup when booting from an image file or CD, the installation stops at about 15%, and just sits there.  This is my first time using Ubuntu, so any help would be greatly appreciated.

I'm having a similar problem on Windows XP (Parallels Workstation) except my installation is stopping around the 53-80% mark. I've tried installation four times now, each time deleting the virtual machine and creating a new one, and I keep running into the problem.

---

### Post by garrettmurray on 2006-07-11
I am having the same problem on my MacBook Pro in Parallels. Sits at 15%.

Also, I get an error when first loading the live CD that the power manager "cannot start until you start the dbus system service"

...?

---

### Post by petxurag on 2006-07-11
Hi,

My install completes but then stalls after rebooting right here, see attachment.

Any help on how to reconfigure Parallels to make it work is appreciated.

Thanks guys
~P

---

### Post by Tu13erhead on 2006-07-11
15%++.

Anyone have a solution?  It appears this is the only way to install Ubuntu with the live CD...

---

### Post by ubuntu-geek on 2006-07-11
> **Tu13erhead said:**
> 15%++.

Anyone have a solution?  It appears this is the only way to install Ubuntu with the live CD...
On my macbook pro this is the only way I could get it to install as well. Also, I had to initially set the ram at 512mg anything higher caused issues. IMO, this is more a parallels issue then an ubuntu issue.

---

### Post by kaje on 2006-07-11
Guys, I found out a way to install it. When in parallels, if you change the CD-ROM device to "Use an Image," you can use the unbutu live cd ISO file. I was able to install no problems from this.

Great tip for in the future saving CDs as well ;)

Hope this helps.

---

