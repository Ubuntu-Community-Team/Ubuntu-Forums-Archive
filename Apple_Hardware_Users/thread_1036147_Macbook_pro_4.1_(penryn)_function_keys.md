---
title: "Macbook pro 4.1 (penryn) function keys"
date: 2009-01-10
forum: Apple Hardware Users
---

### Post by daleha on 2009-01-10
I am using ubuntu 8.10 on my 4.1 macbook pro.

I have followed the guide on this forum, and it has gotten sound and other features working, but unfortunately I can't get the screen brightness (F1/F2) to work, or the keyboard brightniess (F5/F6).

The screen brightness is supposed to work out of box on this model, so I don't know what I am doing wrong. I have re-installed ubuntu a few times, and I know that it was working with one of my installations before off of the same disc. I have tried burning different discs, but it doesn't seem to fix anything.

As for the keyboard brightness, installing applesmc didn't seem to work. Is there any sort of special configuaration that I need to do to get these working that anyone knows about? Has anyone had this problem, where the display brightness keys didn't work OOB?

Thanks!

---

### Post by hajk on 2009-01-10
The screen brightness keys F1/F2 will not work out-of-the-box, but need the "pommed" package installed and then configured a bit in /etc/pommed.conf. The F5/F6 keyboard backlighting keys require a bit more configuration and the "applesmc" kernel module. Unfortunately, "applesmc" as presently constituted in the 2.6.27 kernel in Intrepid (and the earlier 2.6.24 kernel in Hardy) cause the logs to fill up with an unending stream of debugging messages, so loading this module may not be what you want. There is a thread here describing some patches to the applesmc sources that will fix this, you could google for it; apparently, the patches will be included as of 2.6.28 kernel.

---

### Post by hyperboloid on 2009-01-11
Have you looked at the Wiki?
[https://help.ubuntu.com/community/MacBookPro4-1/Intrepid]("https://help.ubuntu.com/community/MacBookPro4-1/Intrepid")

You don't need pommed for 8.10, for example.

---

### Post by cyberdork33 on 2009-01-11
> **hajk said:**
> The screen brightness keys F1/F2 will not work out-of-the-box, but need the "pommed" package installed and then configured a bit in /etc/pommed.conf. The F5/F6 keyboard backlighting keys require a bit more configuration and the "applesmc" kernel module. Unfortunately, "applesmc" as presently constituted in the 2.6.27 kernel in Intrepid (and the earlier 2.6.24 kernel in Hardy) cause the logs to fill up with an unending stream of debugging messages, so loading this module may not be what you want. There is a thread here describing some patches to the applesmc sources that will fix this, you could google for it; apparently, the patches will be included as of 2.6.28 kernel.
pommed is depreciated, you should not use it.

The latest versions of applesmc are in the mactel-support PPA repo

[https://wiki.ubuntu.com/MactelSupportTeam/PPA](https://wiki.ubuntu.com/MactelSupportTeam/PPA)

---

