---
title: "Unreadable log on"
date: 2008-01-27
forum: Absolute Beginner Talk
---

### Post by lift_test on 2008-01-27
When I log in the date and time are readable size but the prompts for name etc are so small as to be unreadable.  Doesn't matter now but will do when I have more than 1 user.  Any ideas please?

---

### Post by Jimmey on 2008-01-28
This might happen when you have a bigger resolution available in your xorg.conf than you're actually using. I've noticed (although I might be wrong), that the login screen (GDM) will use the largest possible resolution, where your normal X sessions will use whatever resolution you've set for it to use.

This can be a problem if you have a massive resolution in your xorg.conf.

Although this might not be the reason for the small fonts, it's worth trying the following instructions:

First make a backup of your xorg.conf file by entering the command ```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.BACKUP
```

Leaving a backup file that you can "re-instate" should the changes you make later break anything.

Then enter the command ```
sudo dpkg-reconfigure xserver-xorg
``` into a terminal. This will bring up a little wizard that will help you reconfigure the Xserver.

You can navigate through this wizard using a combination of the tab and enter keys, and the arrow keys.

At some point during the course of this wizard it will ask you if you would like for it to attempt to autodetect your monitor. Select "No".

It will also, at some point, ask which sort of configuration you would like to run for your monitor. Select advanced. 

At some point during this entire process, it will ask you to provide a range of monitor resolutions that the Xserver can run at. **It is important at this stage that you only leave highlighted the resolutions that you will actually use.** For example, if the largest resolution you actually use for your monitor is 1024x768, make sure that no resolutions greater than this are selected.

The majority of the questions asked by the wizard can simply be answered "yes".

Once the wizard has completed, you can then restart the xserver by hitting the key combination CTRL + ALT + BACKSPACE.

Please, let me know if this solves your problem.

---

### Post by lift_test on 2008-01-28
Thanks, tried it but it's still the same.  Date and time are perfectly legible but all other text is so small as to be unreadable.

---

### Post by golovan on 2008-01-28
Have you got a Nvidia card?
I fixed my problem following this thread: [http://ubuntuforums.org/showthread.php?t=586681&highlight=nvidia+text+small](http://ubuntuforums.org/showthread.php?t=586681&highlight=nvidia+text+small)

---

### Post by lift_test on 2008-01-29
No NVidia, using motherboard display.  However tonight when I fired it up the prompts were legible, three reboots after I tried suggestion above!
Thanks for the help.

---

