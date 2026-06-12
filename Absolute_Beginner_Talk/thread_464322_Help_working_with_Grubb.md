---
title: "Help working with Grubb"
date: 2007-06-04
forum: Absolute Beginner Talk
---

### Post by perrybergmann on 2007-06-04
--------------------------------------------------------------------------------

I get hit with this message everytime I try to boot up.

[10.3345301]..MP-BIOS Bug:8254 Timer not connected to IO-APIC.

I have done some research and people say to go to Grubb and append it to say no apic. I have no idea what this means. I get into the Grubb menu by pressing esc at start up and it gives me these four options.

Ubuntu, Kernel 2.6.20-16-generic
Ubuntu, kernel 2.6.20-16-generic(recovery mode)
ubuntu, kernel 2.6.20-15-generic
ubuntu, kernel 2.6.20-15-generic(recovery mode)

I have no idea which one to pick to make the changes. I have tried entering all of them but when I type no apic it says: Error 11: Unrecognized device string. I do not know what to do. I really want to remedy this situation because it seems to be making my system crash at random times. 

Does anyone have any suggestions or advice.

---

### Post by Bohlio on 2007-06-04
Well all those four different options are the different ways you can boot ubuntu. With kernel 16, kernel 16 in recovery mode. Kernel 15, and kernel 15 in recovery mode. On a default boot, your probably loading up the first entry, which is the most recent kernel. 

If people are telling you to append grub to have it say no apic which im guessing will be apic=no instead of apic=yes then I think the solution is to edit your grub.conf or menu.lst file. although I dont quite know which one or what directory they are located it :-P
Another member will probably be along shortly to help you out with the specifics :-P

---

