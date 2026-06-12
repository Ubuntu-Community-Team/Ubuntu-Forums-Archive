---
title: "Problems after install"
date: 2005-12-30
forum: Apple PPC Users
---

### Post by jmdennis on 2005-12-30
I have tried installing Kubuntu 5.10 a few times and I get to the same place each time.  It installs fully even doing the restart and installing the other packages.  It tries to go to the desktop for me to login but the screen flashes for a second and then it has me login with out a graphical login.  I just get a $ sign after this to do what I need to do.  I do not know what I need to edit before hand to get this to work right so I can use the system.  Otherwise it is a waste for me.  I have not tried Ubuntu 5.10 yet but probably should since I read that Kubuntu had problems with certain machines.  If any one could offer some advice it would be greatly appreciated.  I am using a blue and white on this and just yolur generic pc monitor that was given to me.

---

### Post by jmdennis on 2005-12-30
I have even used the live disc of Ubuntu 5.10 and get the same thing that it does not give me a graphical login.  So far I have found out some information but nothing that has really helped.  All I want to do is get to the desktop so I can install updates and make sure that I can get the graphical login all the time.  I bypassed the network set up because I use DSL and do not use dhcp.  If some one can help it would be greatly appreciated as I have spent way to much time on this already.

---

### Post by fordfan753 on 2005-12-30
Your problem is almost certainly your graphics card, and it is almost certainly fixable without too much work. What type of graphics card do you have make/model ?

---

### Post by jmdennis on 2005-12-30
I believe that you are right.  I changed the settings for the live cd to 800X600 and below and it got the graphical mode going but then it crapped out saying that I had an xserver problem and once I fixed it I should be able to start gdm again.  My video card is an ATI Rage 128 video card.  My monitor is a generic pc monitor that was given to me.  I believe it is older and thus can not handle the refresh rates that are probably set for it.

---

### Post by jmdennis on 2005-12-31
It seems to be working.  I found this command sudo ddcprobe | grep monitorrange on the link below.  I found out the information for my monitor was 30-70 and 50-130.  I entered this but it still brought me to a non-graphical login.  I logged in as myself and did a startx and it started up kde.  Now I will either have to wipe the hard drive and install version 5.10 or just upgrade from version 5.04.  I will have to see if I can get connected using my dsl account which I did have working when I had YDL so that should not be an issue.

[https://wiki.ubuntu.com/FixVideoResolutionHowto](https://wiki.ubuntu.com/FixVideoResolutionHowto)

---

