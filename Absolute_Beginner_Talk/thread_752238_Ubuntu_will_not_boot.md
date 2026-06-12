---
title: "Ubuntu will not boot"
date: 2008-04-11
forum: Absolute Beginner Talk
---

### Post by tinylittlesteps on 2008-04-11
Apologies in advance for a slightly longwinded post. 

I have 2 drives, and older (slave) drive win2K installed and a newer (master) drive with Ubuntu installed. At some stage I fixed the drives to allow Dual booting, so that as I switch the machine on/reboot I go grub first and then get to choose if I want to go to Ubuntu or to the other drive and win2K. I did this so long ago I can't recall how I did it, and it's been working fine until now. 

Recently, I had the windows drive freeze on me a couple times and I had to pull the plug. Since then, Ubuntu will not boot. I have had all the following erros: 

grub loading stage1.5 read error
error 16
error 18

and and error loading the kernel - I think kernel not found. 

Perhaps foolishly, I tried using a set of commands that should reinstall grub. I used the install CD I made when I first installed ubuntu to do: 

sudo grub
find /boot/grub/stage1
root (hd ?,?)
setup (hd 0)
quit

Since doing this, boot now fails completely: I can't get past stage1.5 reading error, the thing just hangs. I'm not sure I can even get into my BIOS, and when by some miracle I got the chance to start the windows partition I jumped at it and am posting from there right now. 

Is there any way I can save my linux drive? what's gone wrong here?

---

### Post by sancho panza on 2008-04-11
I'd advise try [Super Grub Disk]("http://users.bigpond.net.au/hermanzone/supergrubdiskpage.html") first. Its a powerful tool and lets you fix a lot of bootup related issues on both windows and/or linux.

---

### Post by Lazy-buntu on 2008-04-11
I dual boot vista and ubuntu (on the same drive), what I did though is I installed GRUB just to my ubuntu partition (/dev/sda4), then I booted up vista, installed EasyBCD.

I ran EasyBCD and went to Add/Remove entries, there's a linux tab and I think I chose the partition from there too.

When I boot my computer up now it gives me the options : Windows Vista or Neosmart Linux

If I want to load ubuntu I pick neosmart Linux, then GRUB loads like it would normally and I'm all set.

Dual boot no problem this way, but I'm having wireless issues =/  [http://ubuntuforums.org/showthread.php?p=4692890#post4692890](http://ubuntuforums.org/showthread.php?p=4692890#post4692890)

---

### Post by chrisdugdale on 2008-04-15
I think I'd just do a complete reinstall of Ubuntu if you haven't got it all worked out by now, Maybe wait 9 days and do the new Ubuntu 8.04 LTS edition when it's released? The beta seems quite stable. Either way, why not install Ubuntu and then use Wine and/or VMware to run your Windows stuff if you need to. I don't need to use Wine, but I gotta say the VMware runs Windows stuff real good. Make sure you backup data first!

---

