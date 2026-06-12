---
title: "Minimum system requirements?"
date: 2006-08-19
forum: Absolute Beginner Talk
---

### Post by ExploreMN on 2006-08-19
Hi,
I've been looking around and I can't seem to find the minimum system requirements for installing and running Ubuntu 6.06.  I tried installing it on a PIII 450Mhz system with 192mb of RAM and it can't even get past the loading screens.  So what does it take to run this?  Even WinblowsXP can run on the above described system...  :(

---

### Post by foolsh on 2006-08-19
I run it on 400Mhz 64mb as a server/firewall/router and it doesn't give me anyproblems is there some other issue with your PIII

I have also installed it on a 33Mhz 486 with 16mb although unpleasent in GUI mode it still loaded but i had to use breezy then apt-get dist-upgrade to get to dapper

maybe the graphical installer is hanging somehow

---

### Post by kepos on 2006-08-19
256MB of RAM
2GB of disk space.

Procesor . i don't know. it's not written heare, but it is working fine on 650Mhz.


You don't have enough memory. Try with alternate CD. But i'm not shure it will work.
But xubuntu should work.

---

### Post by kepos on 2006-08-19
> I have also installed it on a 33Mhz 486 with 16mb although unpleasent in GUI mode it still loaded

33Mhz, 16MB and it works??? Ha :)
I should try that. I have one in my backyard.

---

### Post by gn2 on 2006-08-19
Ubuntu 6.06 
should be OK on that system, mines a p3 500 laptop with 192 ram, and works perfectly.

Have you explored the "Options" in the install menu?

There are different install options for different machines.

When I first expiremented with Ubuntu on a desktop, it worked with the "noapic nolapic" option...

---

### Post by ExploreMN on 2006-08-20
Its strange, but it hangs on the part where you pick the timezone.  The CD drive just keeps spinning.  The CD worked fine on another computer for a complete install.  So I changed to a brand new CD drive.  Same problem.  It seems like it just can't handle it past that.  Also, I never get prompted for different loading options.  I'm using whatever the image is that you download here.  Its a "live" CD or something that loads the desktop and then has an "install" icon on the desktop.

Any help would be greatly appreciated.

---

### Post by IYY on 2006-08-20
Your machine is not nearly good enough for the LiveCD installer. Download the  alternate CD for a text-based installer and you'll be fine. I'd suggest using Xubuntu instead, though. It's even faster.

---

### Post by houseisland on 2006-08-20
> **ExploreMN said:**
> Its strange, but it hangs on the part where you pick the timezone.  The CD drive just keeps spinning.  The CD worked fine on another computer for a complete install.  So I changed to a brand new CD drive.  Same problem.  It seems like it just can't handle it past that.  Also, I never get prompted for different loading options.  I'm using whatever the image is that you download here.  Its a "live" CD or something that loads the desktop and then has an "install" icon on the desktop.

Any help would be greatly appreciated.

As kepos and Ivy say above, try the alternate/OEM iso file.  It doesn't start in GUI mode and will install more easily on older machines.

---

### Post by ExploreMN on 2006-08-21
Thanks, that did the trick.  However you guys are right...its dog slow.  So I downloaded Xubuntu last night and will give that a shot later today.

Thanks for the help!

---

