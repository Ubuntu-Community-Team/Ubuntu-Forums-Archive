---
title: "[SOLVED] Ubuntu won't boot from hard drive or live CD"
date: 2008-01-14
forum: Absolute Beginner Talk
---

### Post by ubername on 2008-01-14
Hi

I have a strange situation.

Last time I used my dual boot Ubuntu / XP box all worked.

I haven't used it for a couple of days, but my kids probably have. Last time I used it was to install Visual Studio C# (in XP obviously)

I have just resatrted it, and from the GRUB menu selected ubuntu. I get  a 'starting up ...'message, then the machine reboots again (back to the bios load, (i.e. Dell and BIOS revision message, with a white bar tracking along the screen.)). The grub menu is then displayed again. Memory test works, but not the ubuntu option, nor safe graphics mode. (Both cause reboot again) The XP option does work.

When I put the live cd in, and select 'start or install', same thing happens, computer reboots.

Any Clues?

TIA

---

### Post by Het Irv on 2008-01-14
If you have a XP CD try popping it in.  Also Can you test your CD for Defects?

---

### Post by ubername on 2008-01-14
> **Het Irv said:**
> If you have a XP CD try popping it in.  Also Can you test your CD for Defects?
Thanks

I have discovered that the 'OEM' installation option seems to work (I get to the live CD environment) so it looks like the CD and CD drive are OK. I don't really want to do a reinstall if there is a simple work around

TIA.

---

### Post by Het Irv on 2008-01-14
try reloading Grub or redoing the lines for Ubuntu.  I don't know the exact procedure to do this but I know there are other threads.

---

### Post by ubername on 2008-01-15
Hmm.

It all seems a bit FUBARed at the moment. If I do a cold boot it (sometimes) goes into ubuntu. If I do a 'logoff' or 'restart'  from ubuntu it exhibits the problem I explained above. Thanks for your help, I think I need to do a better diagnosis first, before anyone should feel like replying.

---

### Post by ubername on 2008-01-20
I think I have found the problem. I had a USB IRDA dongle attached to a fourport USB hub which had been reattached to my system. I don't think Ubuntu likes it at all, and windows not much.

I'm a bit surprised that this causes such a fundamental problem however.

Cheers

---

