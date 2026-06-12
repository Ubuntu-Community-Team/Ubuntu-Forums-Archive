---
title: "[SOLVED] Error when updateing Skype"
date: 2008-03-14
forum: Absolute Beginner Talk
---

### Post by avanrens on 2008-03-14
I get the following error when I try to update Skype.
E: /var/cache/apt/archives/skype_2.0.0.63-1_i386.deb: trying to overwrite `/usr/share/icons/skype.png', which is also in package skype-common

---

### Post by MidEvilHungarian on 2008-03-14
Here is a little help, go to skype.com , download the package ubuntu7.04+, then start synaptic, search for skype and make a complete removal for all packages affiliated, from there on just install the package you downloaded. have fun.

---

### Post by mikewhatever on 2008-03-15
I did not even have to completely remove it, just uninstall with <sudo dpkg -r skype>.

---

### Post by avanrens on 2008-03-15
I tried all the above but still got the same error. I used terminal and used the "locate skype" command and then manually deleted all the skype files. Then used Synaptic Package Manager to remove the rest of Skype and then used the same to re-install Skype. It all works fine again. Thanks for the Help.
:lolflag:

---

### Post by MidEvilHungarian on 2008-03-16
Yeah.... did you checked the version you reinstalled with synaptic? Let me know if you have the latest 2.0.0.63 If you got something else then you only reinstalled the (beta)

---

### Post by avanrens on 2008-03-16
Yes I only have the beta ver. but I know that it works. Trying to update to the next ver was when I had the problem.
Thanks again for your help. I might leave Skype as it is until I update to the next ver of Ubuntu in April.

---

