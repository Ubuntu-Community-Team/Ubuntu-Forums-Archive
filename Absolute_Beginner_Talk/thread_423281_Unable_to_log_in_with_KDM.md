---
title: "Unable to log in with KDM"
date: 2007-04-25
forum: Absolute Beginner Talk
---

### Post by cpetzol2 on 2007-04-25
I just installed Kubuntu Feisty last night. Things were going wonderful, used my computer for 1 hour and had zero problems.

This morning, I decided to customize "Kooldock" (MacOS like dock) and after I made the proper changes, none of the icons were showing up right.
Another thing, was when I started up Kmail for the first time, it says that it was unable to make any changes in my home directory. Using sudo fixed it, but I shouldnt have to do that for access to the home directory should I?

 I thought a quick reboot might make something better. When I restarted, everything went wonderfully, and I was left at the KDM login screen. I log in.....the screen goes black.....flashes one time.....and I am back at the KDM log in screen again, like nothing had happened. No error messages, no anything. 
I try again, this time setting the session type as 'failsafe'. Exact same thing.

I restarted the computer again, and booted in recovery mode, things went well, and I was left at the prompt as root. I typed "/etc/init.d/kdm", got to the KDM login screen, and everything started happening all over again.

I really dont want to reinstall everything again, but I dont know what else to do at this point. Does anybody have any ideas as to what might be causing this. Thanks.

---

### Post by Austin_KW on 2007-04-25
You have probably messed up someting in your own account settings. 
Rather than reinstalling try cleaning out all the flies under your account. I am assuming that if it is a new install you dont have anything you need saving

boot in revovery mode, and change to you own home directory

cd /home/yourUserName

the remove everything (make sure you are in your home directory with pwd)
pwd
rm -rfv * 

Now reboot and try loging into your account

---

