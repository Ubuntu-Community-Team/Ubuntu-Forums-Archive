---
title: "Password when laptop lid opens"
date: 2006-04-12
forum: Absolute Beginner Talk
---

### Post by Papa-san on 2006-04-12
I thought I had this hammered out, but don't seem to be able to get this setting back where it needs to be:

When I open the lid of my laptop,, and when I use a sudo command in terminal, I have to use a password that I find to be too confusing, and easy to forget. (I have it written down, so at least I was thinking at the right time!) I tried to go into System > Administration > Users and Groups, opened the properties for the only user listed, and the password is not the same as the one for these other functions. Where do I go to find the right place to change it for sudo and the other?

EDIT: I guess my problem is linked to my lack of understanding with the root vs. user accounts. (Azz... this is another usability concern that a little text with install would clarify for many ex-xp-ers) Is my 'root' the 'john' I entered, or the 'johnstone' I entered?!?

---

### Post by mandrakethepenguin on 2006-04-12
Well, when your laptop lid shuts, ubuntu locks the screen (I think, I have never used ubuntu on anything but a desktop).  To unlock the screen, the password should be the same as your username password, unless you were running the X server as root, but I highly doubt that.  To change the sudo password enter 'sudo passwd' in a terminal.  It will then ask you for your confusing password, then it will ask you for a new password.

---

