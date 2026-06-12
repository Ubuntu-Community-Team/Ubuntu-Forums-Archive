---
title: "beryl not working"
date: 2007-07-06
forum: Absolute Beginner Talk
---

### Post by Korea91 on 2007-07-06
* Beryl system compatiblity check                            *
**************************************************************

Detected xserver                                : AIGLX

Checking Display :0.0 ...

Checking for XComposite extension               : failed

No composite extension
beryl: No composite extension

---

### Post by Rocket2DMn on 2007-07-06
What video card do you have (it looks like some sort of ATI)?  What have you tried?  How did you initially set it up?
I used this tutorial when I set up Beryl on my Radeon Mobility 9000.
[http://www.howtoforge.com/ubuntu_feisty_beryl_ati_radeon](http://www.howtoforge.com/ubuntu_feisty_beryl_ati_radeon)
Please check the list of supported cards if you choose to use this.

---

### Post by KIAaze on 2007-07-06
Is libxcomposite1 installed on your system?
If not install it.
> sudo aptitude install libxcomposite1

---

