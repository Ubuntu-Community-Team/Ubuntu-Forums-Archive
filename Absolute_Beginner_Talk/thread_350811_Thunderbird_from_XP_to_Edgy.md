---
title: "Thunderbird from XP to Edgy"
date: 2007-02-01
forum: Absolute Beginner Talk
---

### Post by Devilled on 2007-02-01
Well, after a week or two of playing around and finding my feet, I've decided to ditch Mr. Gates and run my system purely on Ubuntu.

I do have one potential problem, however...

Is there a simple way to transfer my stored email from Thunderbird on XP to Thunderbird on Ubuntu (over 2,000 items) without having to forward them all?  I have it all backed up via an extension I used in Windows called MozBackup, but I can't find the same extension for Ubuntu to simply restore the back-up file.

Any suggestions would be very gratefully received.

Devilled

---

### Post by muguwmp67 on 2007-02-01
You're most of the way there.  Check the email portion of this faq:

[https://help.ubuntu.com/community/MigratingFromWindows#head-b661aab3dac739fa47c0c49d9b348a1ec2c04b0a]("https://help.ubuntu.com/community/MigratingFromWindows#head-b661aab3dac739fa47c0c49d9b348a1ec2c04b0a")

---

### Post by Devilled on 2007-02-01
That looks like the boy!  Thanks so much!

Devilled

---

### Post by frolle on 2007-02-01
I will say thanks too!

---

### Post by Devilled on 2007-02-01
Ah...  Guess I didn't read down far enough.  The instructions aren't complete.

Any idea how to import the email into Ubuntu's Thunderbird anyone?  Where is my profile folder in Edgy?

Many thanks in advance (again!)

Devilled

---

### Post by hyper_ch on 2007-02-01
it's in

/home/YOURUSERNAME/.mozilla-thunderbird

You can basically copy the profile folder plus the profile.ini file over from winxp to ubuntu and then make sure you have the right user:

```

sudo chown -R YOURUSERNAME:YOURUSERNAME /home/YOURUSERNAME/.mozilla-thunderbird/*

```

---

### Post by Devilled on 2007-02-01
Thanks Sjau - but I'm still on the training wheels version of Terminal commands.  Could you describe the process step-by-step for me?

I copied the contents of my XP Thunderbird mail folder over to the Ubuntu one - but it hasn't worked.  Guess I'll have to try the entire profile folder.

Any further advice would be welcome!

Devilled

---

### Post by hyper_ch on 2007-02-01
I said copy the whole profile folder and the profile.ini from xp to ubuntu..

and regarding the terminal... you can issue the exact command except that you ahve to replace YOURUSERNAME with your actual one...

---

### Post by Devilled on 2007-02-01
Many thanks

---

### Post by hyper_ch on 2007-02-01
so it worked?

---

### Post by Devilled on 2007-02-01
Yes, thank you.

---

