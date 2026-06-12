---
title: "Problem with dual boot- can no longer boot into OSx"
date: 2008-10-11
forum: Apple Hardware Users
---

### Post by stealth17 on 2008-10-11
I have a Macbook Santa Rosa with Ubuntu 8.04 dual booted with OSx. I followed the wiki and installed rEFIt. Everything worked fine for a few months, it would startup to the rEFIt menu and I could select OSx or Ubuntu. Then one day I booted and it went straight into the OSx loading screen and didn't go any further. The screen looks like this:

[attach]88024[/attach]

It just sits at that screen and never loads any futher. The only way I can get on now is if I hold Alt when I boot and get the other boot menu. I select Windows (even though it goes to Ubuntu). I suspect this is the bootcamp boot menu?

How do I get it to boot into OSx again? What exactly is going on here?

---

### Post by DonnieP on 2008-10-11
> **stealth17 said:**
> ... The only way I can get on now is if I hold Alt when I boot and get the other boot menu. I select Windows (even though it goes to Ubuntu). I suspect this is the bootcamp boot menu?

How do I get it to boot into OSx again? What exactly is going on here?
Are you saying that 'the other boot menu' does not have a selection for OSX?

---

### Post by mfox on 2008-10-11
If you boot with the option key down, you should get all the bootable drives showing, and then you can pick Mac OSX.

---

### Post by stealth17 on 2008-10-12
I figured out the problem but now I cannot boot Ubuntu. It turns out the first 200MB Fat32 drive created for EFI had a bootable tag set in gparted. It's exactly the situation described [here]("http://www.macosxhints.com/article.php?story=20080130022147512").

So now when I boot it will go directly to OSx and it will boot it correctly. When I hold Alt/Option during boot it brings up EFI and the only option is rEFIt. If I choose rEFIt it will load it up and it shows OSx on the left and "legacy OS" on the right. If I choose legacy OS it will goto a black screen with the error "non-system disk error" and I can't go any further.

In rEFIt I used the partition tool to update the MBR as well. I still have the first partition marked as msftres, but I cannot get it to unflag it. I tried to mount it in OSx under disk utility as the article says but it won't mount for me.

How do I get Ubuntu back?

---

### Post by xiaoqiangwj on 2008-10-12
> **stealth17 said:**
> I figured out the problem but now I cannot boot Ubuntu. It turns out the first 200MB Fat32 drive created for EFI had a bootable tag set in gparted. It's exactly the situation described [here]("http://www.macosxhints.com/article.php?story=20080130022147512").

So now when I boot it will go directly to OSx and it will boot it correctly. When I hold Alt/Option during boot it brings up EFI and the only option is rEFIt. If I choose rEFIt it will load it up and it shows OSx on the left and "legacy OS" on the right. If I choose legacy OS it will goto a black screen with the error "non-system disk error" and I can't go any further.

In rEFIt I used the partition tool to update the MBR as well. I still have the first partition marked as msftres, but I cannot get it to unflag it. I tried to mount it in OSx under disk utility as the article says but it won't mount for me.

How do I get Ubuntu back?

try to update your partition information, and see what will happen. If it doesn't work, try to rebuild grub through the live cd.

---

### Post by stealth17 on 2008-10-12
> **xiaoqiangwj said:**
> try to update your partition information, and see what will happen. If it doesn't work, try to rebuild grub through the live cd.

How do I update the partition information, you mean through rEFIt? I did once and it asked if I wanted to update so I said yes and now when I go back it just gives me an error that it could not read the scheme or something.

---

### Post by cyberdork33 on 2008-10-12
sync the partitions in refit using the partition tool, and you may need to reinstall grub. See this thread:
[http://ubuntuforums.org/showthread.php?t=767677](http://ubuntuforums.org/showthread.php?t=767677)

---

