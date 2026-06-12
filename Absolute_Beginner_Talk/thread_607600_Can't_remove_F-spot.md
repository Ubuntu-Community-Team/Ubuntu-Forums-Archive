---
title: "Can't remove F-spot"
date: 2007-11-09
forum: Absolute Beginner Talk
---

### Post by JJNova on 2007-11-09
So I don't want F-Spot. 

No big deal, I just open up terminal and type

```
sudo apt-get remove f-spot
```

F-Spot has been removed. Awesome! Except when I click APPLICATIONS>GRAPHICS, F-Spot is right there. Ok, maybe it didn't remove the launcher. So I click on it, and sure enough, F-Spot launches. 

I'm still not too worried about it, as being a previous windows user, I'm accustomed to "reboot" before anything takes affect. I reboot, and sure enough, F-Spot will still launch. So I open up Add/Remove, and F-Spot is unchecked (implying that it's not installed). Now I am getting confused. The program isn't being recognised as installed, yet it will launch without any hindrance. I close add/remove and launch Synaptic. Maybe there's a dependency that didn't get removed that's keeping the whole package around (Hey, it was worth checking out!).

Nope, I do a search in Synaptic for F-Spot and everything is unchecked (all two results). Ok, back to terminal.

```
$ sudo apt-get remove f-spot
$ Package f-spot is not installed, so not removed
$ f-spot

```
AND F-SPOT LAUNCHES! Is there a way to remove programs that I am unaware of? 

By the way, I installed xubuntu-desktop and tried removing it form that terminal with no results. So then I logged out completely, hit CTR+ALT+F1 and then went through the commands again, and had no results.

---

### Post by felicity on 2007-11-09
I'm not sure what's going on with your f-spot installation. Did you happen to install a version of f-spot outside of the apt system? I can tell you that I used synaptic to remove f-spot with Mark for Complete Removal and it worked fine for me.

---

### Post by JJNova on 2007-11-09
No, it's just the F-Spot that's installed by default. I went through Thunar and deleted the folder as well as other instances I could find. Which means I probably still have parts of F-Spot on my computer, but at least the binary is gone and it's no longer in my Applications bar.


The bad news is, the same thing happens with Totem. Removed Totem, terminal informs me that Totem is not installed, but if I type "Totem", sure enough, it launches.

edit: Totem Movie Player

edit again: Totem has been successfully removed. I removed it from Terminal in XFCE, and it would still launch. I restarted into gnome, used add/remove, and then it removed it completely. I don't understand it, but it worked.

---

### Post by beanco on 2007-11-10
I am having the same kind of problems with open office.

removed it in terminal but it is still there in applications/office

if I try to remove it again in terminal it says it is not installed.

I am on feisty if that matters.

any ideas how i can actually remove it?

robi

---

### Post by JJNova on 2008-01-03
Just thought i would pop back in with an update. All of my problems have been fixed by re-installing Gutsy from a disc instead of using the upgrade feature. This has made everything work smoothly. As for the person having the same issue in Feisty.... sorry :confused:

---

