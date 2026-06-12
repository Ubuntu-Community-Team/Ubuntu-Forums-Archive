---
title: "I'm getting annoyed with typing my password three times (logon, NetworkManager, NTFS)"
date: 2007-05-05
forum: Absolute Beginner Talk
---

### Post by Amablue on 2007-05-05
Is there a way to skip the two extra instances where it asks for passwords? I don't want to have to type in my pass word every time I log on to my computer for Network Manager and my NTFS partition. 

Speaking of NTFS partitions, how do I get write permissions for it?

---

### Post by aysiu on 2007-05-05
I don't see why you'd need your password for NTFS. Try this:
[http://www.ubuntugeek.com/widows-ntfs-partitions-readwrite-support-made-easy-in-ubuntu-feisty.html](http://www.ubuntugeek.com/widows-ntfs-partitions-readwrite-support-made-easy-in-ubuntu-feisty.html)

As for the Network Manager thing, try this:
[http://ubuntuforums.org/showthread.php?p=2586057](http://ubuntuforums.org/showthread.php?p=2586057)

After that, you should have only one password--to log in.

---

### Post by DSn0wMan on 2007-05-05
You can use this to have network manager automagically log in with your keyring.

1. sudo apt-get install libpam-keyring
2. add the following line to the end of /etc/pam.d/gdm:

@include common-pamkeyring

---

### Post by Billy McCann on 2007-05-05
You can automatically login too.  

System > Admin' > Login Window > Security > Enable Automatic Login

---

### Post by asbesto on 2007-05-05
Also, in this way you don't need any password anymore when logged into GDM. Automatic login, et voila'! no more annoying password for synaptic, network manager, or anything else...

and this is GREAT on your personal laptop, where no one have an account apart of you. :)

---

### Post by OffHand on 2007-05-05
> **asbesto said:**
> Also, in this way you don't need any password anymore when logged into GDM. Automatic login, et voila'! no more annoying password for synaptic, network manager, or anything else...

and this is GREAT on your personal laptop, where no one have an account apart of you. :)

All it is is superbad security practice. You might as well use Windows then.

---

### Post by AaronMT on 2007-05-05
> **OffHand said:**
> All it is is superbad security practice. You might as well use Windows then.

No need to be living in a super paranoid world. This is his laptop not a public terminal.

---

### Post by OffHand on 2007-05-06
> **AaronMT said:**
> No need to be living in a super paranoid world. This is his laptop not a public terminal.


You have no idea about security. But do whatever floats your boat.

---

### Post by aysiu on 2007-05-06
If it's connected to the internet, you have to worry about security.

---

### Post by asbesto on 2007-05-07
> **OffHand said:**
> You have no idea about security. But do whatever floats your boat.

g333Z, wh4t a k-r4d 3l33tZ H4xx0r h3r3!!!!!!

bRRRBrRRRRRRrrRRRR!!!

:lolflag:

---

### Post by asbesto on 2007-05-07
> **asbesto said:**
> Also, in this way you don't need any password anymore when logged into GDM. Automatic login, et voila'! no more annoying password for synaptic, network manager, or anything else...

and this is GREAT on your personal laptop, where no one have an account apart of you. :)



Ehm, 

I talked too fast. it doesn't work - anyone knows why ?!? :(

Synaptic package manager ask me a password again :(

---

