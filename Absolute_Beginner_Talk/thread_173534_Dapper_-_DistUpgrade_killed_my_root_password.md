---
title: "Dapper - DistUpgrade killed my root password"
date: 2006-05-10
forum: Absolute Beginner Talk
---

### Post by amsgwp on 2006-05-10
I installed dapper about a day ago(ubuntu newbie), and after a few days I was getting some sort of error that said I should probably try the apt-get dist-upgrade.  So I did it, and all seemed fine until I just tried to launch synaptics and it keeps saying my root password is wrong.  The password screen has changed since I did the distupgrade, it now has the option to "save for this session" or add to keyring, these are both new options since before.  I'm paranoid about restarting now because my root password is the same as my username password(can someone tell me how to fix this too?).  During the isntallation you setup a username and password and it seems that the same password is also root password.

---

### Post by amsgwp on 2006-05-10
well its not just synaptic, I tried to do some other things in the control panel that ask for root and I get "Wrong Password."  This is so weird, could it have defaulted my root password to something else?

ok this is getting even weirder

I clicked on the software update icon and it asked for my password and it worked.  But my password still doesn't work in anything else that uses my root password.  This is really strange

---

### Post by keshav0001 on 2006-05-10
i hope u must have restarted ur computer after this cause this is really weird!

replied cause i saw this post to be just 3 mins old..just try after restarting

---

### Post by Mustard on 2006-05-10
Normally those dialogs are asking for your user password.  By default the root password in Ubuntu is disabled, so I'm not sure why you would even be entering a root password to start Synaptic.

If it's really a problem with it not recongnising a password then perhaps changing that password with the **passwd** command would help.

---

### Post by capt_cope on 2006-05-10
try this in console:
sudo passwd root

if all is well it'll as you for your new unix password, then ask you to confirm.

---

