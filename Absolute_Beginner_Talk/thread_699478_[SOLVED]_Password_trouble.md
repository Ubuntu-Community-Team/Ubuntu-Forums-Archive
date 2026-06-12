---
title: "[SOLVED] Password trouble"
date: 2008-02-17
forum: Absolute Beginner Talk
---

### Post by Ekemet on 2008-02-17
Hi all. FIrst of all Im a n00b in Linux. In fact this is the first distro I try (Ubuntu). 

My problem is with the password for "administrative tasks". I am 100% sure that I am typing the correct password, but the system tells me it is incorrect all the time.

I only used 2 passwords during the installation and none of them work; I use one to log on when you boot the system. In fact, the very first time I logged on Ubunutu, the Update Manager asked me to install 240 MB of updates... it asked me for password to "perform administrative tasks", and IT DID WORK that time. (the updates were downloaded and installed, and it was with the same password I log on...).

But now, it does not work anymore. Iv tried with the terminal, typing **su**, **sudo**, and **sudo passwd root**, and its always the same: wrong password. I cant run the update manager, nor get into Synaptic Package Manager nor User and Groups, etc...

I did search for help in the forums but basically all refer to use the **su** command in the terminal, which isnt viable for me... also, some have suggested to edit the **sudoers** file using **visudo**, but it ask me for password when I try to do so...

 Im completely frustrated. Any help will be greatly appreciated. Thanks in advance.

Edit: BTW, I am using Gnome in case that matters, and Ubuntu version is 7.10

---

### Post by Zeroangel on 2008-02-17
Well the password of your main user should work with sudo/gksudo, etc but if its not theres definitely a problem there.

First of all, make sure CAPS LOCK is off, as passwords are case sensitive. 

If that doesnt work. You could always try and reboot into recovery mode. You should get terminal access and it will let you run the passwd command. Run the passwd command as the regular user, and reboot. If that fails, then reboot into Recovery Mode and run "sudo passwd" to try and edit your root password.

---

### Post by Ekemet on 2008-02-17
Thanks for replying.

Lets call my older passwords "oldest" and "alpha" (Made both when installing. "oldest" has proven to be useless since all the time I write it I get an incorrect password message, while alpha at least lets me log in when booting)

I am sure it is not a CAPS LOCK issue. I think I tried writing the password like 50 times, making all kind of combinations... my password is quite short (only 6 characters), and I am certain I have been typing it correctly.

As you suggested, I booted in safe mode and used **passwd** and was asked for a new UNIX password. I typed a new one and got a "updated succesfully" message. Lets call this new password "beta". Then rebooted in standard mode, and when I tried to update, I was asked for password for administrative tasks,.. it did not work again (neither with the new password "beta" nor the old one "alpha").

Then, rebooted in safe again... this time I was asked for the root password... I typed the old password "alpha", and it gave me access (this is just so screwed up IMO).... then used **sudo passwd**. Just as the case before, got a "updated succesfully" (lets call this gamma) message. I even did a **sudo passwd root** (lets call this delta), and go the same result (updated succesfully). I wrote down all the changes I made, with the proper passwords.

Again in standard more... tried to update, and got same error message regardless of the password I wrote (alpha, beta, gamma, delta... even with oldest). In the terminal I get same results. o_O

This is just sooo bizarre.

---

### Post by Ekemet on 2008-02-18
OK, I found the solution to my problem...

When I first installed Ubuntu I used the US keyboard layout by default. I made my password using that layout. Using the updater, I downloaded all the files available at such moment.

However, since I am mexican, I need to write signs and symbols not found on the US layout. So I switched to the latin american keyboard layout, and got everything working fine. And a that time the nightmare began... 

In my password I have a under **slash symbol** ( **_** ). My wild guess is that such symbol generates conflict when switching from a US layout to a latin american one. 

The weird thing is that both my user password and password for administrative tasks are the SAME... and still, only ONE WORK (when logging in) and not when performing administrative tasks... oO (all of this under the US layout).

When using the latin american layout, the same password WORK FOR BOTH logging and administrative tasks... oO

 So messed up, IMO. Anyway, I guess I will change my password without under slash symbol, to prevent any further problems. Thanks for the help, and if anyone can mark this thread as solved, it would be good, so other people with this problem can find a solution.

Thanks again, and see ya! >D

---

### Post by bodhi.zazen on 2008-02-18
Please mark this thread as solved (you can do it), it saves the time of many volunteers looking to help ...

[https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)

---

### Post by Zeroangel on 2008-02-18
Ahh man. Burn!
Well glad ya got it working, my mexican fellow ubuntu'er. :popcorn:

---

### Post by Ekemet on 2008-02-21
:lolflag:

Thanks for the help, anyway.

:D

---

