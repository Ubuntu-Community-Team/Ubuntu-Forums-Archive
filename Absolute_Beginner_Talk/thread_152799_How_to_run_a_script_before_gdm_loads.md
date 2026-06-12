---
title: "How to run a script before gdm loads?"
date: 2006-03-30
forum: Absolute Beginner Talk
---

### Post by aerials on 2006-03-30
I own a thinkpad with a fingerprint scanner and it works quite nice with sudo and gdm. Problem is, that I use the notebook as often on the road as at home in the docking station, where it is closed and I can't access the fingerprint scanner.

The key to activate/deactivate the whole fingerprint thing are two lines in the file /etc/pam.d/common-auth. My wish is to have a script that detects if the notebooks lid is closed at boot and changes/copies the file common-auth so that I have the full fingerprint experience with an open notebook and no hassling with clicking away fingerprint windows when I'm at home.

So, where do I have to hook in such a script that it gets executed early enough that gdm uses the changed common-auth file? And how do I get this script to run with root privileges without having to enter a password all the time?

---

### Post by dcstar on 2006-03-30
[QUOTE=aerials]I own a thinkpad with a fingerprint scanner and it works quite nice with sudo and gdm. Problem is, that I use the notebook as often on the road as at home in the docking station, where it is closed and I can't access the fingerprint scanner.

The key to activate/deactivate the whole fingerprint thing are two lines in the file /etc/pam.d/common-auth. My wish is to have a script that detects if the notebooks lid is closed at boot and changes/copies the file common-auth so that I have the full fingerprint experience with an open notebook and no hassling with clicking away fingerprint windows when I'm at home.

So, where do I have to hook in such a script that it gets executed early enough that gdm uses the changed common-auth file? And how do I get this script to run with root privileges without having to enter a password all the time?[/QUOTE]
You probably need something in /etc/init.d (linked to /etc/rcS.d with a low number, so it starts before /etc/rcS.d/S70xorg-common).

That way the job would run before the X server stuff kicks in.

Have a look at the existing scripts in that directory for how you should structure it to run correctly.

---

