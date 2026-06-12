---
title: "[SOLVED] printer setup in Gutsy"
date: 2007-11-01
forum: Absolute Beginner Talk
---

### Post by Boaslad on 2007-11-01
I have an HP 2110 all in one scanner / printer / copier. It works... o.k... under Gutsy. (it worked a lot better under Feisty) I want to try changing the driver or configure a few settings to see if i can get it working better. But, when ever I make a change and click "Apply" I get a prompt for "password for *username* on localhost". My main password doesn't work here, nor does any password that I have created in the system. so... um... how do I figure out what this password is? Is there a way to bypass this "security" feature?

---

### Post by fivesmellydragons on 2007-11-01
Have you downloaded and installed the HPLIP Toolbox? I have an HP as well and I installed that program and it set it up perfectly. 

If your having a separate issue with the password, stupid question here but what about the caps lock on? Just a guess! I think there's a way to change the root password, but I don't know how to go about that.

---

### Post by jkounis on 2007-11-08
**This post could be related to an Ubuntu bug filed at**: [https://answers.launchpad.net/ubuntu/+question/4306](https://answers.launchpad.net/ubuntu/+question/4306)  [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				This seems to be a known bug described in [https://answers.launchpad.net/ubuntu/+question/4306](https://answers.launchpad.net/ubuntu/+question/4306) . 

If you right-click on the "System" Menu and click "Edit Menus", and then scroll down to System -> Administration on the left window. On the right window, right-click on "Printing" and click "Properties". You'll see that the "Command" that the menu item invokes is /usr/bin/system-config-printer.

Change the command to the following, and click "Close" twice:
> gksudo /usr/bin/system-config-printer

If that doesn't work, try the typing the following command at the command line:
>  sudo /usr/share/system-config-printer/system-config-printer.py

---

### Post by Boaslad on 2007-11-10
Thank You very much.This solved my problem.

---

