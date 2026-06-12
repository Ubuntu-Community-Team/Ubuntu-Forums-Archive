---
title: "Freezing free Desktop environment"
date: 2014-06-27
forum: Any Other OS
---

### Post by akkb100 on 2014-06-27
Hello All, 

Let me start with my Laptops specs.
I have a HP laptop with 2nd Gen i3 Core, 6 GB RAM with inbuilt Intel Graphics, and 500 GB HDD

Right now I have installed Linux Mint 17 cinnamon desktop, its one of the best distro around, but it hangs a lot. With simple actions like switching between tabs in FF or opening up media files. It freezes in most of the cases. I have same issue with Unity so I switched to this. But I am not getting a proper solution for this issue. 

Can anyone suggest me a decent looking Desktop environment, which do not freeze or freezes less?

---

### Post by ajgreeny on 2014-06-27
Perhaps try running the memtest86+ from grub for as long as possible; even overnight if you are able to, and see if there are any errors showing.

If any error at all is shown, you may have found your problem and may need to replace your memory module(s), however it could also be almost any piece of your hardware.  I think Mint with cinnamon DE should run fine on that spec laptop, but it could also be worth looking at XFCE4 when it is released, if you want to stay with Mint 17.

---

### Post by akkb100 on 2014-06-27
> **ajgreeny said:**
> Perhaps try running the memtest86+ from grub for as long as possible; even overnight if you are able to, and see if there are any errors showing.

If any error at all is shown, you may have found your problem and may need to replace your memory module(s), however it could also be almost any piece of your hardware.  I think Mint with cinnamon DE should run fine on that spec laptop, but it could also be worth looking at XFCE4 when it is released, if you want to stay with Mint 17.


Thanks for your Valuable feedback, will try this tonight. I have never used XFCE desktop, so don't know about it. I will try as per your recommendation (Linux Mint XFCE 17 is launched). Hope things go well.

---

### Post by buzzingrobot on 2014-06-27
Cinnamon relies on 3D effects and compositing.  The Intel video in your laptop may not be up to that task.

An interface that does not rely on 3D and compositing might work better, if the video is the issue.  XFCE is one. Mate is another.  If a distro enables compositing in XFCE or Mate by default, it's easily disabled via the settings tool.

You'll also find many suggestions to use Lubuntu here.

---

### Post by tgalati4 on 2014-06-27
What is your definition of "freezing"?  Does the desktop lock up so that you have to reboot?  Or does the desktop stutter for a few seconds causing you to wait to use your computer?

Look in /var/log/Xorg.0.log to see if there are errors.

```
cat /var/log/Xorg.0.log
grep EE /var/log/Xorg.0.log
```

---

### Post by Phateless on 2014-07-20
I had a similar experience with Cinnamon on my old Dell laptop with Core 2 Duo.

Switched to Xubuntu and all is well. Xubuntu is very pretty, lighter than full Ubuntu, but not as sparse as Lubuntu.

Give it a shot.

---

