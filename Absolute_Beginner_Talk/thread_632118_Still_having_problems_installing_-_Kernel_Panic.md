---
title: "Still having problems installing - Kernel Panic"
date: 2007-12-05
forum: Absolute Beginner Talk
---

### Post by Stolengoat on 2007-12-05
Hi everyone,

As I mentioned in earlier posts, I have just installed a new motherboard because my BIOS crashed (but the same HDD and memory), and I was innocent enough to think that this would be straightforward!

When I try to install Ubuntu for the first time, I get Kernel Panic, and it comes up with:

[ 66.295907] PCI: Cannot allocate resource region 8 of bridge 0000:00:03.0
[ 66.295970] PCI: Cannot allocate resource region 0 of device 0000:00:00.0
[ 66.806245] Invalid compressed format (err=2)
[ 66.806977] Kernel panic - not syncing: VFS: Unable to mount root fs on unknown block (8,1)

I suddenly thought that perhaps I should run the board as naked as possible.  I have fitted my previous graphix card and firewire card, and I have a usb mouse connected.  Do you think it would make any difference if I removed these (I'm at work at the moment - won't be able to try it 'till I go home tonight), and then attempt to install them later.  Could it be a memory problem?

I would love a relatively simple solution!  I'm a complete Newbie.

Thanks

---

### Post by overdrank on 2007-12-05
> **Stolengoat said:**
> Hi everyone,

As I mentioned in earlier posts, I have just installed a new motherboard because my BIOS crashed (but the same HDD and memory), and I was innocent enough to think that this would be straightforward!

When I try to install Ubuntu for the first time, I get Kernel Panic, and it comes up with:

[ 66.295907] PCI: Cannot allocate resource region 8 of bridge 0000:00:03.0
[ 66.295970] PCI: Cannot allocate resource region 0 of device 0000:00:00.0
[ 66.806245] Invalid compressed format (err=2)
[ 66.806977] Kernel panic - not syncing: VFS: Unable to mount root fs on unknown block (8,1)

I suddenly thought that perhaps I should run the board as naked as possible.  I have fitted my previous graphix card and firewire card, and I have a usb mouse connected.  Do you think it would make any difference if I removed these (I'm at work at the moment - won't be able to try it 'till I go home tonight), and then attempt to install them later.  Could it be a memory problem?

I would love a relatively simple solution!  I'm a complete Newbie.

Thanks
Ok sorry you are having issues and creating a new thread every day will not help. If you could give us some system specs and tell us  did you check the cd for errors and [https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)
Check the memory, I have seen this error with conflicts between onboard graphics and a pci slot graphics card. It could be a conflict between any of the additions slots so strip the board to the bare minimum and try that.

---

### Post by Stolengoat on 2007-12-05
Hi Overdrank

Sorry to cause offence - I'm just desperate.  Thanks for the response.

Many thanks.

---

### Post by overdrank on 2007-12-05
> **Stolengoat said:**
> Hi Overdrank

Sorry to cause offence - I'm just desperate.  Thanks for the response.

Many thanks.

I understand your frustration, but I am sure if someone has encounter this error they would help. Like myself I have seen that type of error but I was not able to resolve it. Just bump the thread and search and try new things and hopefully it will get resolved and I will help with what I can. :)
Edit. If you make more threads it is like chasing your own tail because the user's trying to help have no idea what you have tried unless they search your previous post like I did.

---

