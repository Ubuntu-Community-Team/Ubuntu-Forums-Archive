---
title: "remove prompting of nm-applet Xubuntu"
date: 2007-11-22
forum: Absolute Beginner Talk
---

### Post by MockY on 2007-11-22
I really dislike when nm-applet prompts for your password everytime you reboot your laptop.
I disabled this in Ubuntu by doing this:

```

rm ~/.gnome2/keyrings/default.keyring
sudo aptitude install libpam-keyring

Edit the /etc/pam.d/gdm file and append the following line to the end of the file:
@include common-pamkeyring
```

But how do I go about to do so in Xubuntu?

---

### Post by t0n1 on 2007-12-30
Good question.
Is there any elegant way to do this on xubuntu?
Been looking for a while how to do this for my laptop.

---

### Post by sgfaulkner on 2007-12-31
I am also having this same issue and have not found a solution for Xubuntu.

---

### Post by jacksonz123z on 2008-01-04
I have wasted hours playing with NM, it has been causing trouble for years!  I just installed WICD to fix the keyring xubuntu login problem.  So far, just using WEP it is perfect!  With NM I had to give my password three times to have wireless access.
I will test  WPA at work soon.   Maybe it is time to get rid of NM?

---

### Post by Paqman on 2008-04-04
I've got this issue too. I've just installed Xubuntu on my girlfriend's laptop, and it's something which I know will bug her.

---

### Post by taavikko on 2008-04-04
Just an info on issue, Hardy is supposedly fixed this problem.
At least on gnome enviroment.

---

### Post by Paqman on 2008-04-05
Well, i'm running Xubuntu Hardy, and it's definitely still broke in XFCE.

---

### Post by Tom Mann on 2008-05-01
Mocky, you have solved your own question. I tried your instructions in Hardy Xubuntu, then connected to my wireless. It asked me for a password (which I left blank and clicked OK) then it asked if I would like to use unsafe storage. Sorted! Thanks!

---

### Post by MockY on 2008-05-01
Fantastic. Thanks for the info. I will try this out on a later date to confirm.

---

### Post by Tom Mann on 2008-05-02
Errr. Actually since doing that my login prompt has gone all awry - It keeps giving me authentication errors. Nevermind... I tried it on a clean install, just hope you get this before you try it yourself...

---

