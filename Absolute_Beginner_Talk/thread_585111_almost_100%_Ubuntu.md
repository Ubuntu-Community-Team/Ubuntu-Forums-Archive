---
title: "almost 100% Ubuntu"
date: 2007-10-21
forum: Absolute Beginner Talk
---

### Post by davidsotl on 2007-10-21
well, maybe not 100%. I do need xp for a few of my program, but I'm tired of rebooting my Machine every time I need it. so I choose VMware. it works find except one thing, well, two things: 
1. it conflict with the restricted driver I installed for ATI xpress 200M. the system will go black every time I power on. the only solution I've got is logout instead reboot, login again using fail-safe terminal. but there got be a way to solve this.

2. I choose NAT for the internet connection, but VM can't find the vmnet08 folder or something like that, so I'm aslo looking for help on that one.

---

### Post by julian67 on 2007-10-21
> **davidsotl said:**
> well, maybe not 100%. I do need xp for a few of my program, but I'm tired of rebooting my Machine every time I need it. so I choose VMware. it works find except one thing, well, two things: 
1. it conflict with the restricted driver I installed for ATI xpress 200M. the system will go black every time I power on. the only solution I've got is logout instead reboot, login again using fail-safe terminal. but there got be a way to solve this.

2. I choose NAT for the internet connection, but VM can't find the vmnet08 folder or something like that, so I'm aslo looking for help on that one.

You might want to try VirtualBox in preference to VMware. I'm not making any criticism of VMware (beyond its proprietary license) but VirtualBox can almost certainly do the same things you need VMware to do and is available with a free license from the Ubuntu repos. I can't say that it will work perfectly with the ATI driver as I have no experience of this but I have never had a problem with NAT on VirtualBox.

---

### Post by EagleRock on 2007-10-21
> **davidsotl said:**
> well, maybe not 100%. I do need xp for a few of my program, but I'm tired of rebooting my Machine every time I need it. so I choose VMware. it works find except one thing, well, two things: 
1. it conflict with the restricted driver I installed for ATI xpress 200M. the system will go black every time I power on. the only solution I've got is logout instead reboot, login again using fail-safe terminal. but there got be a way to solve this.

2. I choose NAT for the internet connection, but VM can't find the vmnet08 folder or something like that, so I'm aslo looking for help on that one.

I'd need to know how you're running VMWare to better understand the problem.  Say how you did the install exactly.  From what you said, my guess would be that you're running XP as your host OS, installed VMWare Server there, then installed Linux as the guest.  However, I'd need to know exactly how you did it to be sure.

However, if Linux is the guest, then the problem is simple.  When you use VMWare to run an OS, it doesn't recognize the hardware you are using (e.g. your ATI GPU), but rather it will recognize the "virtualized" hardware that VMWare uses.  Meaning, when VMWare starts a guest OS, it is making a virtual hardware platform for the machine to run on.  The simplest solution would be to uninstall the ATI drivers (since they're useless anyway when in VMWare), then install VMWare Tools.  VMWare tools will make the guest run a lot faster.  You won't get the best behavior out of VMWare, but then again, the solution is made for server OSes, not home gaming.

---

### Post by davidsotl on 2007-10-21
I guess I didn't make my question clear. actually Gusty is the host OS, and I'm trying to run XP on it.

---

