---
title: "Can I install Ubuntu with wubi if I am already dual booting Windows XP and PCLinuxOS"
date: 2008-04-03
forum: Absolute Beginner Talk
---

### Post by stephenj2008 on 2008-04-03
Hi,

I am quite an inexperienced Linux user, but I do have my computer dual booting Windows XP and PCLinuxOS (on a single hard drive) (Grub Bootloader).

I am interested in trying out Ubuntu by installing it onto my Windows partition via wubi.  Can anyone tell me if this is possible with my set-up?  (I have plenty of space on the Windows partition.)

Could it have any adverse effect on my current set-up - e.g. could it corrupt Grub?

Will Grub revert to its current (correct) state if I decide to uninstall wubi and Ubuntu?

Thank you for any assistance.

---

### Post by aktiwers on 2008-04-03
I think Wubi uses the Windows Bootloader so if you use grub I think this will be a little complicated.

But if you already use grub, why not do a normal install? Worst case you would have to re-setup grub.

---

### Post by angry_johnnie on 2008-04-03
No problem.  A friend of mine just downloaded Hardy and installed it with Wubi.  So, he has two bootloaders.  First, there's grub, from which he chooses either Ubuntu Feisty or Windows.  And, if he chooses windows, he's presented with Windows's bootloader, and there he must choose either Windows or ubuntu Hardy.

However, Wubi has been beta for ages.  And, like Aktiwers said, why not do a normal install?  Ubuntu is a very polite OS.  It will automatically add PCLOS and windows to its own grub menu.

But, if you really want to use wubi, then go ahead. :-)  It sure is the easier way to go.

---

### Post by stephenj2008 on 2008-04-03
Thank you angry-johnny and aktiwers for your speedy replies and help.

As I said, I'm really a novice and not too tech savvy, so I had some rather hairy moments when I installed PCLinuxOS.  Consequently, I don't really want to play around with Grub if I don't have to.  (For instance, I have read in a couple of places that PCLinuxOS Grub does not automatically recognise Ubuntu (only Windows XP).

Wubi therefore, seems a good way for me to assess Ubuntu's suitability for my system and me.  (I'm going to wait until Hardy Final is out.)  If it proves successful (which would not surprise me) I then, will 'bite the bullet' and attempt a triple boot.  Eventually, I want to bid farewell to Windows.

Thanks again.

---

### Post by Zralou on 2008-04-03
> **stephenj2008 said:**
> 
Wubi therefore, seems a good way for me to assess Ubuntu's suitability for my system and me.  (I'm going to wait until Hardy Final is out.)  If it proves successful (which would not surprise me) I then, will 'bite the bullet' and attempt a triple boot.  Eventually, I want to bid farewell to Windows.

Thanks again.

If all you need to do for now is test the system compatiblity of Ubuntu, why not just try the liveCD, that way you can see if Ubuntu is for you without touching your setup in any way.  And if you find you like Ubuntu, you can then install it from the LiveCD.

Sara Lou

---

