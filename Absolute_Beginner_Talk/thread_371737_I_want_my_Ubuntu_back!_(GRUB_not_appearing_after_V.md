---
title: "I want my Ubuntu back! (GRUB not appearing after Vista installation)"
date: 2007-02-27
forum: Absolute Beginner Talk
---

### Post by satchelpig on 2007-02-27
I upgraded my windows XP partition to Vista last night, and all of that is basically fine.  However, I no longer get my GRUB screen at bootup, and thus I can't get to my Ubuntu installation, with which I had become very happy after hours of tweaking it to be just so.  I have, however, confirmed by using the Live CD that it's all still in there.

I have gone to [this guide]("https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows") to try to correct the problem, and I have tried both the SuperGrub disk method and the version that preserves the Windows Bootloader, but neither has worked.  My computer boots right into Vista (which, I admit, is pretty to look at, but it's still not my Ubuntu!).

My next step is to try the instructions that overwrite the Windows Bootloader, but before doing that I wanted to get some confirmation from a wiser head than mine that: (a) this is reasonably likely to work in my case; and (b) if it does not work, it is not going to render my computer totally unusable absent a complete re-installation of all operating systems.

I know there are never any guarantees, but can I at least get the educated guess of someone that this is worth pursuing?  Other ideas are also welcome.

Thanks!

---

### Post by Aurora Borealis on 2007-02-27
I think it's because you have to install the windows before the linux.

---

### Post by satchelpig on 2007-02-27
> **Aurora Borealis said:**
> I think it's because you have to install the windows before the linux.

OK, but having not done that, what do I do now?

---

### Post by K.Mandla on 2007-02-27
If you boot the alternate CD, you can use the rescue option to reinstall Grub. You just have to know how your partitions are set. I've never used it in conjunction with Vista though, so be careful.

---

### Post by Darkula on 2007-02-27
reinstall ubuntu and choose "upgrade", it should detect your windows installation and reinstall the grub loader.

(but really, who needs windows???)

---

### Post by TheWizzard on 2007-02-27
> **satchelpig said:**
> I upgraded my windows XP partition to Vista last night, and all of that is basically fine.  However, I no longer get my GRUB screen at bootup, and thus I can't get to my Ubuntu installation, with which I had become very happy after hours of tweaking it to be just so.  

sue them! :twisted:

---

### Post by satchelpig on 2007-02-27
OK . . . I swallowed hard and tried the instructions that overwrite the Windows bootloader and it appears that I have my Ubuntu back now.  

One minor complaint that I suspect is easily fixed:

GRUB still refers to Windows as being Windows XP instead of Windows Vista.  How to I change that?  A minor quibble, I know, but I'm the type of guy who that'll drive nuts.

---

### Post by proalan on 2007-02-27
> OK . . . I swallowed hard and tried the instructions that overwrite the Windows bootloader and it appears that I have my Ubuntu back now.

One minor complaint that I suspect is easily fixed:

GRUB still refers to Windows as being Windows XP instead of Windows Vista. How to I change that? A minor quibble, I know, but I'm the type of guy who that'll drive nuts.

open up a terminal via 

Applications -> Accessories -> Terminal

type in

```
sudo gedit /boot/grub/menu.lst
```

locate the windows xp entry (usually towards the end of the document) and change it to whatever you wish

:)

---

### Post by satchelpig on 2007-02-27
> **proalan said:**
> open up a terminal via 

Applications -> Accessories -> Terminal

type in

```
sudo gedit /boot/grub/menu.lst
```

locate the windows xp entry (usually towards the end of the document) and change it to whatever you wish

:)

Worked perfectly. 

Thank you.

---

### Post by mikewhatever on 2007-02-27
That should be just the matter of editing the title in GRUB menu.
Back up the menu first:
cp /boot/grub/menu.lst /boot/grub/menu.lst_backup

now open the menu file:
gksudo gedit /boot/grub/menu.lst

go to the very end to find the Windows entry and rewrite the title. Save and exit.

Lots of fast typers here :)

---

