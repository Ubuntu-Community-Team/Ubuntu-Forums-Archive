---
title: "[SOLVED] VMWare with a dual-boot machine"
date: 2007-06-26
forum: Absolute Beginner Talk
---

### Post by mahasmb on 2007-06-26
Just wondering... 'cause I kinda got the impression that this is a possibility.

My laptop dual-boots with XP and Feisty. I was wondering, could I use VMWare to access my Windows XP partition? Or do I have to install a brand new Windows XP inside my VMWare?

I'm pretty new to Ubuntu, and getting all my programs set up and such is taking FOREVER.

So, I wanna experiment with Wine and VMWare until I can (hopefully) run all programs natively. That, and the rest of my family only knows Windows. Plus, I have quite a few programs that are harder if not impossible (for a noob like me) to find Linux alternatives for (i.e. my programs for my phone, PDA and the list goes on).

---

### Post by Maxtorm on 2007-06-26
> My laptop dual-boots with XP and Feisty. I was wondering, could I use VMWare to access my Windows XP partition? Or do I have to install a brand new Windows XP inside my VMWare?
You do have to install an new version inside VMWare; however, VMWare has a freely available utility available that will make the process rather painless: VMWare Converter ([http://www.vmware.com/products/converter/](http://www.vmware.com/products/converter/)).  Install it, and create a virtual image of your physical Windows XP partition.  Boot into Ubuntu and mount your Windows disc.  From VMWare, open the virtual image your created with VMWare Converter and -bingo- you're up and running (+/- any driver issues you might have under VMWare).

---

### Post by mahasmb on 2007-06-28
Thanks!

Maybe I'll use that in the future, right now I don't have a spare 23 gigs on this measly 60 GB laptop -_-. Especially with the dual-boot. And no matter what, I think it's always a good idea to have your computer set to dual-boot (even if it's the same OS'es twice!) It's saved me in the past when my computer's really messed up. And since I'm still experimenting with Ubuntu, I wouldn't be too surprised if that were to happen in the near future.

---

