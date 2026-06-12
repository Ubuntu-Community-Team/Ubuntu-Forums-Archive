---
title: "[SOLVED] Howto extract update packages to use it on other PC"
date: 2007-05-30
forum: Absolute Beginner Talk
---

### Post by guhpraset on 2007-05-30
I have installed ubuntu 6.06. And spent two full days to download the update using synaptic.

Now i want to install this Ubuntu to another PC but i dont want to spent other two days to download the packages, Can i extract the downloaded package and use it to update other PC? How?

Thankyou

---

### Post by yabbadabbadont on 2007-05-30
All of the deb archives that you downloaded and installed are (usually) stored in /var/cache/apt/archives.  You should be able to copy them into that same directory on the new machine so that it won't try to download them after you update apt on that machine and then upgrade.

---

### Post by guhpraset on 2007-05-30
Done! Thank you very much Yabbadabbadont :)

Now, how to apply it in the next PC?

---

### Post by yabbadabbadont on 2007-05-30
Run the normal "sudo apt-get update" and let it update it's package database from the repositories.  Then when you go to do the "sudo apt-get upgrade"  (or dist-upgrade), it will only download the deb files that you haven't already copied to that machine from the other.

---

### Post by guhpraset on 2007-05-30
Thank you, your tips really save a lot of my time.

---

### Post by guhpraset on 2007-06-07
Emmh, i want to have the same installed packages from both PC. I copied all the deb inside /var/cache/apt/archives from the first PC to /var/cache/apt/archives of the second PC (is this the right way?). 

But it is not easy to click them one by one in the synaptic (i forgot), and it hurts to click the deb one by one. 

Is there any easier way to install ALL the deb i copied from /var/cache/apt/archives from the PC?

---

### Post by Ek0nomik on 2007-06-07
> **guhpraset said:**
> Emmh, i want to have the same installed packages from both PC. I copied all the deb inside /var/cache/apt/archives from the first PC to /var/cache/apt/archives of the second PC (is this the right way?). 

But it is not easy to click them one by one in the synaptic (i forgot), and it hurts to click the deb one by one. 

Is there any easier way to install ALL the deb i copied from /var/cache/apt/archives from the PC?

I thought "sudo apt-get dist-upgrade" would have automatically installed the files you do have and downloaded the ones you don't.  Have you ran that command?  I could be mistaken though...

---

### Post by yabbadabbadont on 2007-06-07
> **Ek0nomik said:**
> I thought "sudo apt-get dist-upgrade" would have automatically installed the files you do have and downloaded the ones you don't.  Have you ran that command?  I could be mistaken though...

That's what I told them to do a week ago.  It should work.

---

### Post by AAM on 2007-06-07
The software you seek is available and is called APTonCD and it is in the repositories. The process is very very easy and you only need a blank CD.

Install APTonCD on your primary machine. Perform the update as previously described. Now that you have finished, reboot (probably will be advised to do this anyway). Have a blank CD available. APTonCD sits on the **System | Administration** menu. It is really easy to use. 

Start it, choose "**Create APTonCD**", then enter a file name then "**OK**". Put the blank CD in and when it says "**Do you want it burn it now?**" say "**yes**" and you are done! If you repeat that procedure every time you want new software or to update, you will be OK. 

To set the APTonCD CD up for use, put the disk in the caddy, and when it has mounted select **System | Administration | Software Sources**. Go to the tab called "**Third-Party Software**" and the CD you have sitting in the caddy should be listed there. Tick the box to select it and then "**Add CD-ROM...**". It should then load. Close **Software Sources** and then open Synaptic Package Manager (you can do both of these actions using the repositories menu item inside SPM!). Click on the **Mark all upgrades** button and then **Apply. **

It's that easy! I tried it last night and that's what I did!

---

### Post by guhpraset on 2007-06-09
Waw, if only i know that sooner, i wouldnt have to face [this problem]("http://ubuntuforums.org/showthread.php?t=468624").
I am downloading it now.
Thankyou

---

