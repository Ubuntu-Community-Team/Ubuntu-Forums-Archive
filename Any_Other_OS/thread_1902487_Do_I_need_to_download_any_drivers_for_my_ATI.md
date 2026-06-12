---
title: "Do I need to download any drivers for my ATI?"
date: 2011-12-30
forum: Any Other OS
---

### Post by cokabear on 2011-12-30
im running fedora16 with my ati radeon hd 5770
do i need any other drivers? or does the system already have them included?

if i run this in the terminal:[FONT=monospace]
[/FONT]glxinfo | grep rendering

if get an answer of:
direct rendering: Yes

does this mean i already have drivers for my ati?

---

### Post by 2F4U on 2011-12-31
Every Linux distribution I know includes at least the open source driver versions for ATI/nVidia cards. These usually work fine for 2D effects, but not so much for 3D effects. No Linux distribution has control over the proprietary drivers and therefore doesn't include them by default. They may also cause problems when new kernel versions get pushed out.

---

### Post by Mark Phelps on 2011-12-31
> **cokabear said:**
> does this mean i already have drivers for my ati?

IF you didn't have drivers already, you wouldn't be seeing a graphical desktop; instead, you would be stuck in a command line interface.

To see if you have the restricted drivers installed, open a terminal and enter "fglrxinfo".

---

### Post by MoreOrLess on 2011-12-31
> These usually work fine for 2D effects, but not so much for 3D effects
The open-source driver works fine for 3D desktop effects and light gaming, as they're not too demanding on 3D power. The proprietary driver (fglrx/Catalyst) has better 3D performance, but I wouldn't install it unless I was having bad performance with the open-source drivers. Catalyst has its own drawbacks (slower 2D and other assorted bugs depending on version).

---

### Post by 3Miro on 2011-12-31
As MoreOrLess said, in the case of ATI I would keep using the default drivers and install the proprietary ones only if I run into trouble. For example, you may run into issues on some heavy games or you may suffer from low battery life on a laptop.

If you decide to install the proprietary drivers, from the Unity menu, look for "Additional Drivers" and enable the ATI drivers from there. This is the correct way to install the drivers on Ubuntu. Do not download anything from AMD unless you know what you are doing.

---

### Post by oldos2er on 2011-12-31
Moved to Other OS/Distro Talk

---

