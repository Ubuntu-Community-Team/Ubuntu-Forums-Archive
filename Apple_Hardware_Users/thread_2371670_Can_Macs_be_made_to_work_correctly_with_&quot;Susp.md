---
title: "Can Macs be made to work correctly with &quot;Suspend&quot; and &quot;Hibernate?&quot;"
date: 2017-09-17
forum: Apple Hardware Users
---

### Post by sterator on 2017-09-17
My 2009 Mac Pro and 2012 Mac BOOK Pro will Suspend just fine. They won't awaken from Suspend. I'm forced to to a hard power-down and reboot.

Can Mac Hardware be made to behave correctly with Suspend and Hibernate such that the computer will revive or wake from those states?

If so, how's this achieved? Thank you for any clues!

---

### Post by &amp;KyT$0P# on 2017-09-17
What are the exact model numbers of your Macs?

---

### Post by pteryges on 2017-09-18
My 2010 Mac Pro does it with no problems. What version of Ubuntu are you running?

---

### Post by donwakefield on 2017-09-22
My MacBook Pro 9,2 (mid 2012) comes back from Suspend without a problem. I am running Elementary OS Loki and did not need to tweak anything to accomplish it. I have not tried Hibernation though.

---

### Post by sterator on 2017-09-24
The Mac pro is a 2009 "Nehalem" 2.26ghz machine and the Mac BOOK Pro is a 2012 i5..model is 9,2

For both machines, it is Ubuntu 17.04 (Zesty Zapus?)


Thank you!

---

### Post by &amp;KyT$0P# on 2017-09-24
> **sterator said:**
>  the Mac BOOK Pro is a 2012 i5..model is 9,2
Please post here the output from running these commands in a Terminal on your MacBook Pro -
```
glxinfo
inxi -Gxxz
```

If you don't have inxi, install it first -
```
sudo apt-get install inxi
```

---

### Post by sterator on 2017-09-24
halogen2;

Thank you...I ran the command, but this forum software chokes when I try to post the results. Is there a specific bit I can post, to help lighten the load on the forum?

Thank you!

---

### Post by &amp;KyT$0P# on 2017-09-25
You could put it on [pastebin]("https://paste.ubuntu.com/") and post the link here.

---

### Post by sterator on 2017-09-25
Darn good idea..thank you!

[https://pastebin.com/VEqnYWed](https://pastebin.com/VEqnYWed)

---

### Post by &amp;KyT$0P# on 2017-09-25
Err, I meant run those commands in Ubuntu, not Mac OS.  But we may have enough to work with anyway.

Your MacBook Pro is using the integrated Intel graphics.  When you set up your Ubuntu to use the Intel graphics, did you do **all** of the things mentioned [here]("https://ubuntuforums.org/showthread.php?t=2335586&p=13539492&viewfull=1#post13539492")?

---

### Post by kevin160 on 2017-09-27
As for hibernation working, my mini 6,2 running 17.04 desktop happily resumes from suspend, hibernate and hybrid-sleep.

I understand that it is possible to hibernate to a swap file, but I'm old fashioned and created a proper swap partition a bit bigger than my RAM on the internal HD rather than wasting space on the internal SSD.  

I put the UUID of the swap in my /etc/default/grub with

GRUB_CMDLINE_LINUX_DEFAULT="resume=UUID=9a731b79-5521-476a-bf8a-afdbde7fb1aa"

and I need to use the "grub" option in rEFInd when the machine boots back up.  Otherwise it's just a reboot rather than a resume.

---

### Post by sterator on 2017-09-27
Thank you, halogen2

No, I didn't do all or any of the things at the link you provided..are you saying that I ought to do them now?

---

### Post by &amp;KyT$0P# on 2017-09-28
> **sterator said:**
> No, I didn't do all or any of the things at the link you provided..are you saying that I ought to do them now?
It fixed a similar suspend problem on my MacBook Pro 9,1.  I would say it's worth a shot on your MacBook Pro 9,2.

**Back up your system**, then do **_all_** the steps mentioned there on your MacBook Pro.  Does it now wake from suspend?

---

### Post by sterator on 2017-10-12
Thank you, halogen2. I will follow your advice. May be a few days until I get to it, but I will follow up with my results...hopefully it will help others with the same issue.

---

