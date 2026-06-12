---
title: "Resizing my Windows Partition"
date: 2007-01-13
forum: Absolute Beginner Talk
---

### Post by sean_ on 2007-01-13
Hey, I recently uninstalled Ubuntu by deleting the partition and GRUB **** itself. My question is, am I able to resize my Windows Partition and make it 110 GB, instead of 120? I don't think the computer I'm on at the moment can burn CD's for the latest ubuntu, and a Live CD won't work because it has tons of errors when it tries to load the GUI. Anyways, when I try to resize my Windows partition from 120 GB to 110 GB on a previous version, it doesn't do anything to it, it just keeps the same space. Somehow I need to fix that so I can uninstall Ubuntu properly and move it to another machine without deleting the partition and messing up GRUB.

---

### Post by sean_ on 2007-01-13
I'd like to add that I did search the forums/google.

---

### Post by deanlinkous on 2007-01-13
Could you clarify?
You uninstalled ubuntu, now you want to make a 110GB partition instead of a 120 so you can uninstall ubuntu and move it to another parition without deleting it and messing up grub???

All that flew right by me....

---

### Post by sean_ on 2007-01-13
> **deanlinkous said:**
> Could you clarify?
You uninstalled ubuntu, now you want to make a 110GB partition instead of a 120 so you can uninstall ubuntu and move it to another parition without deleting it and messing up grub???

All that flew right by me.... Now you just confused me.. I guess I misstyped something, I meant uninstall as in deleted the ubuntu partition.

---

### Post by sean_ on 2007-01-13
So, does anybody know why Ubuntu refuses to resize my Windows partition?

---

### Post by puneit on 2007-01-13
With my limited knowledge I know that, resizing can be done on same file formats. Someone correct me if I am wrong.
So, you have deleted the partition on which Ubuntu was previously installed. But then have you formated it to the same file system as Windows? If not, do it then try resizing.

---

### Post by sean_ on 2007-01-13
> **puneit said:**
> With my limited knowledge I know that, resizing can be done on same file formats. Someone correct me if I am wrong.
So, you have deleted the partition on which Ubuntu was previously installed. But then have you formated it to the same file system as Windows? If not, do it then try resizing.I don't plan to do that, I just want to resize my windows partition so I can install Ubuntu and get my computer working again.

---

### Post by deanlinkous on 2007-01-13
> **sean_ said:**
> I don't plan to do that, I just want to resize my windows partition so I can install Ubuntu and get my computer working again.

Thank you, why didn't you state that in your original post. So right now you have just one partition and it has windows on it and now you want to install linux again? 
Could you clarify this part then...
> so I can uninstall Ubuntu properly and move it to another machine without deleting the partition and messing up GRUB.

What exactly are you trying to accomplish, and what is the current state?

Yes if all you are trying to accomplish is to resize and reinstall then ubuntu should resize it when you go to install. If not then you can try a Gparted liveCD or any other live cd for a GUI to resize the partition. If you are comfortable without a GUI then a debian install CD or any other SHOULD be able to resize the partition.What do you mean when you say it doesn't do anything?  Any errors? Did you click APPLY or whatever?

---

### Post by sean_ on 2007-01-13
> **deanlinkous said:**
> Thank you, why didn't you state that in your original post. So right now you have just one partition and it has windows on it and now you want to install linux again? 
Could you clarify this part then...


What exactly are you trying to accomplish, and what is the current state?

Yes if all you are trying to accomplish is to resize and reinstall then ubuntu should resize it when you go to install. If not then you can try a Gparted liveCD or any other live cd for a GUI to resize the partition. If you are comfortable without a GUI then a debian install CD or any other SHOULD be able to resize the partition.What do you mean when you say it doesn't do anything?  Any errors? Did you click APPLY or whatever? I told you this already, I'm not sure if the computer I'm on right know has a burner. And when I try to resize it, I change 120.0 GB to 110.0 GB... I hit Enter when I highlight Apply and it still says 120.0 GB for HDA1.

---

### Post by deanlinkous on 2007-01-13
Dude that first post is so confusing I am not sure WHAT you have said or not.

Am I correct in assuming that you simply are trying to install Ubuntu and are having trouble partitioning?  Is that the whole situation?

If you cannot run a liveCD then how are you trying to install? Is this a older Ubuntu CD? What liveCD do you have that has tons of errors? What version are you trying to install?

Please realize you are explaining this to someone who is not there with you, cannot see what you see, and to provide any help needs every single thing explained in detail.

---

### Post by sean_ on 2007-01-13
[QUOTE=deanlinkous]Am I correct in assuming that you simply are trying to install Ubuntu and are having trouble partitioning? Is that the whole situation?[/QUOTE]Yes.

[QUOTE=deanlinkous]If you cannot run a liveCD then how are you trying to install? Is this a older Ubuntu CD? What liveCD do you have that has tons of errors? What version are you trying to install?[/QUOTE]
I'm using an older CD, I do happen to have a Live CD, but I have some Buffer I/O Error that I won't go into.

Like I said in my last post in this thread, I went into "Resize this Partition" Changed 120.0 GB to 110.0 GB, hit OK, and it still said HDA1 120.0 GB ect..

---

### Post by sean_ on 2007-01-13
Nobody knows why the installer won't let me resize my windows partition....?

---

### Post by sean_ on 2007-01-14
Finaly fixed it. I took Dean's suggestion with using a Windows 98 Disc to delete GRUB.

---

