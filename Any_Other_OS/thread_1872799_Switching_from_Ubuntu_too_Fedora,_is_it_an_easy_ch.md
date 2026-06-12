---
title: "Switching from Ubuntu too Fedora, is it an easy change?"
date: 2011-10-31
forum: Any Other OS
---

### Post by GumpTron on 2011-10-31
I would like to try out Fedora 15 but I am concerned I will cause myself major problems. I currently duel boot Ubuntu and Windows 7 and when I boot my PC I get a purple screen and I choose the OS I want. I am afraid that when I install Fedora I will lose this boot screen and be locked out of booting any OS.

Is there a safe way to install Fedora over Ubuntu and have it duel boot with Windows 7? :D

Maybe I need to set up another boot screen and then install Fedora over Ubuntu?

Currently, my pc default boots to Windows after 7 seconds with Ubuntu being the other option. I would love to have the same set up with Fedora replacing Ubuntu.

---

### Post by 11jmb on 2011-10-31
When you say you want to "install Fedora over Ubuntu" do you mean that you want to install Fedora and get rid of Ubuntu?

If that is the case, you should be fine. Grub should detect your Win7 OS as long as you don't do anything screwy to its partition while installing.

---

### Post by nothingspecial on 2011-10-31
Moved to Other OS/Distro talk.

---

### Post by raja.genupula on 2011-10-31
Hi man
   could please tell us what makes you to move fedora , i mean have you faced any difficulty in Ubuntu or any specific problem? 
we are here to help you ...

---

### Post by collisionystm on 2011-10-31
If you have a desktop. I encourage you to spend 40 dollars and get a second hard drive from newegg.com to install your Linux OS's on.

---

### Post by GumpTron on 2011-10-31
> **raja.genupula said:**
> Hi man
   could please tell us what makes you to move fedora , i mean have you faced any difficulty in Ubuntu or any specific problem? 
we are here to help you ...

Fedora desktop is more appealing to me and i like the way it's menus slide in and out and how i can drag a window to the side.

---

### Post by GumpTron on 2011-10-31
> **11jmb said:**
> When you say you want to "install Fedora over Ubuntu" do you mean that you want to install Fedora and get rid of Ubuntu?

If that is the case, you should be fine. Grub should detect your Win7 OS as long as you don't do anything screwy to its partition while installing.

When I installed Ubuntu I created a partition for it then installed it into that partition. What I would like to do is simply overwrite the partition with Ubuntu and put Fedora on it. I am just worried that I will install Fedora but won't even be able to boot into it because after I restart the boot menu will be futzed. That's why I'm posting here, to just be sure.

---

### Post by fantab on 2011-10-31
> **GumpTron said:**
> Fedora desktop is more appealing to me and i like the way it's menus slide in and out and how i can drag a window to the side.

Fedora 15-16beta uses **Gnome-Shell**. You can use Gnome-shell in Ubuntu too. If you are interested to know more, ask for help in Ubuntu Forums- Desktop Environments, we'd love to help you.

EDIT:
> When I installed Ubuntu I created a partition for it then installed it  into that partition. What I would like to do is simply overwrite the  partition with Ubuntu and put Fedora on it. I am just worried that I  will install Fedora but won't even be able to boot into it because after  I restart the boot menu will be futzed. That's why I'm posting here, to  just be sure.Yes, you can overwrite. Fedora will recognize Windows.

---

### Post by raja.genupula on 2011-10-31
> **fantab said:**
> Fedora 15-16beta uses **Gnome-Shell**. You can use Gnome-shell in Ubuntu too. If you are interested to know more, ask for help in Ubuntu Forums- Desktop Environments, we'd love to help you.

EDIT:
Yes, you can overwrite. Fedora will recognize Windows.


+1

you can install gnome-shell

```
sudo apt-get install gnome-shell
``` just taste a bit of it.I am sure you gonna like it.

---

### Post by GumpTron on 2011-10-31
thanks for the help everyone. I am trying out Fedora for now :popcorn:


one problem is right after the install I am not able to update Fedora cause of some rawhide error. Working it out now on Fedora forum which is not as good as this forum haha.

---

### Post by aykoola on 2011-11-01
the above stated reason is one of the main reason i'm not on fedora in the long term. ubuntu and opensuse forums are much friendlier :)

---

### Post by GumpTron on 2011-11-01
i have to be honest and say that it may have taken a little while to get help on the Fedora forums but when I did the fixes were simple and in some ways I really prefer Fedora so far.

Let me explain..

When Using Ubuntu, if i wanted to change the boot order of my duel boot I had to edit a config file. With Fedora, after I got the updates to work, I simply used an easy to understand GUI and it set it all up.

---

### Post by cbowman57 on 2011-11-01
When I want to change the look or behavior of grub2 on Ubuntu I use [grub customizer.]("http://ubuntuforums.org/showthread.php?t=1664134")

---

### Post by Linux_junkie on 2011-11-01
> **GumpTron said:**
> thanks for the help everyone. I am trying out Fedora for now :popcorn:


one problem is right after the install I am not able to update Fedora cause of some rawhide error. Working it out now on Fedora forum which is not as good as this forum haha.

I had the same problem when I installed F15.  If you go in to terminal and type the following command you can get it to update without the rawhide problem.

sudo yum update

---

### Post by Suroh66 on 2011-11-02
> **Linux_junkie said:**
> I had the same problem when I installed F15.  If you go in to terminal and type the following command you can get it to update without the rawhide problem.

sudo yum update

su - "enter" then enter your pass word then yum update... Or update through the software update system their is atleast one package you will have to remove if you're using fedora 15 ( It was rawhide noarch but don't remember the version) I love ubuntu it's my favorite Os for many reasons but fedora is awesome as well I keep multiple coppies of different linux os's around just so I  how I can have them and see their differences I think it's a good thing to know and it's fun to learn more right :).

---

