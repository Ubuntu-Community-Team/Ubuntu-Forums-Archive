---
title: "auto logon to wireless"
date: 2008-01-30
forum: Absolute Beginner Talk
---

### Post by garyed on 2008-01-30
Is there a way to automatically log on to my wireless connection without entering my encripted password & whatever other password it asks for ?
My desktop logs on automatically since its a wired ethernet connection.  
I  loaded Feisty on my laptop & I assume I could log on automatically but I'm a little lost. 
Any help appreciated.

---

### Post by dstew on 2008-01-30
You will need to enter the WEP or other encryption password or code at least once. Later, it should connect automatically.

---

### Post by (((X))) on 2008-01-30
Just enter your login password, when you get prompt, keyring will save it and apply on next reboot

---

### Post by emarkd on 2008-01-30
That's the Gnome keyring asking for your password.  When you save your WEP/WPA key in Ubuntu, it's saved in the keyring which needs your account password to unlock.  You can have it unlock automatically by installing the pam-keyring module.  It's in Synaptic.

---

### Post by (((X))) on 2008-01-30
first remove your old password, if you entered one before..
code:
$ rm ~/.gnome2/keyrings/default.keyring

---

### Post by garyed on 2008-01-30
I installed the keyring manager but I'm using Nautilus & not Gnome.
Does that make a difference?
It still asks me for a password everytime I boot up to connect to the wireless, but it only asks for one password now.
It doesn't ask for my WEP/.... pssword but for the keyring???
I'm still confused.
Thanks for the replies, I'll eventually get it <g>

---

### Post by garyed on 2008-01-30
Sorry for sounding so stupid but I was confused & didn't realize that Nautilus was the file manager for the Gnome Desktop. I thought Nautilus was a separate Desktop.

---

### Post by fatality_uk on 2008-01-30
> **garyed said:**
> Sorry for sounding so stupid but I was confused & didn't realize that Nautilus was the file manager for the Gnome Desktop. I thought Nautilus was a separate Desktop.

If it doesn't prompt you after you logon, 

Click **System->Administration->Keyring Manager**

You should get a prompt then and click **Always Allow** to sort the password.

---

### Post by garyed on 2008-01-31
I've tried everything but every time I log on it still asks for the keyring password.
It remembers the WEP password but not the keyring password.
Any more ideas?

---

### Post by (((X))) on 2008-02-01
It can be, that you ve change your loginpasswd, but keyring uses your old one.

---

### Post by garyed on 2008-02-03
I finally got it.
Great thread here  [http://ubuntuforums.org/showthread.php?t=463639&highlight=keyring](http://ubuntuforums.org/showthread.php?t=463639&highlight=keyring)

---

