---
title: "Boot process: rEFInder -&gt; GRUB - then starts"
date: 2017-04-25
forum: Apple Hardware Users
---

### Post by themusicman on 2017-04-25
Hi All

In my Xubuntu/Linux learning quest, I'd like to get my head around the basic boot process and sequence.  From what I have read, it seems I have a strange issue that I need to understand and am after some expert advice please.

I am using a Mac, and installed on this is OSx10.6 and Xubuntu16.04 - selectable at boot.  Now, here's what i don't understand - the process my machine goes through is this...

Power on
rEFInder presents boot options in gui (Xubuntu avatar | OSX Avatar | another Xubuntu avatar )
GRUB presents boot options in a text based manner (Xubuntu | Advanced Xubuntu Options | Mac OSx)
All seems to work OK: if I select Xubuntu in the gui rEFInder window, then Xubuntu as option 1 in the GRUB text based interface, Xubunut then loads and boots fine.

What I don't understand is why there are two apparent boot processes/applications, when I really only need one to be used? How do I make it such that there is only one selection to be made?

Ta

---

### Post by howefield on 2017-04-25
Thread moved to the "*Apple Hardware Users*" forum.

---

### Post by themusicman on 2017-04-25
> **howefield said:**
> Thread moved to the "*Apple Hardware Users*" forum.

Apologies... never sure if it's an Apple Hardware issue, or a startup/installation issue. :D

---

### Post by oldfred on 2017-04-25
I do not know Mac.

But you have 3 not 2 boot managers or menus.
UEFI is a boot manager.
rEFInd is a boot manager
Grub is both a boot manager & a boot loader.

I assume you can hide menu in any or all of them.

You can turn os-prober off in Ubuntu/grub and then if grub menu only has one entry it will not show by default.
And you can set menu delay from 10 sec to 3 which I do, just so I have time to press a key to get into menu in case I need recovery mode. If set to 0, just cannot get menu even if needed.

       sudo nano /etc/default/grub
#change from 10
GRUB_TIMEOUT=3
# add new entry/line
GRUB_DISABLE_OS_PROBER=true 

 sudo update-grub

---

### Post by LastDino on 2017-04-25
And reason as to why there are multiple of these boot managers is the process that was used to install Xubuntu alongside your existing MAC OSx. It was easiest one with use of rEFInd, so it is there because of that.

And Grub is there because it is Ubuntu's (and many others) default boot manager, you can choose not to install or turn off like how Oldfred has showed.

---

