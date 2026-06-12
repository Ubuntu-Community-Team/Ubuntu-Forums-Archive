---
title: "thunderbird"
date: 2006-10-12
forum: Absolute Beginner Talk
---

### Post by tchoklat on 2006-10-12
Hello all,

I have downloaded thunderbird email client as I used it in XP. It is now resident on my desktop. I have two questions.

1.  How do I move the folder containing the files off the desktop as I do not want to 'see' them on my desktop?

2. Can I, and how do I, move my thunderbird email addresses and emails from the XP thunderbird to Ubuntu thunderbird email client?

:-D

---

### Post by Kateikyoushi on 2006-10-12
Click Places >> Desktop, now right click on the folder you want to move select cut, click the up arrow and paste it there. Now you won't see it on your desktop.

[Moving email from windows to linux.]("http://www.softwareinreview.com/cms/content/view/29/1/")

---

### Post by dmizer on 2006-10-12
first of all ... last i checked, ubuntu came with thunderbird installed by default.  so downloading and installing it was probably not necessary, and will likely cause you problems in the future.

you'll need to find where thunderbird is storing it's profile information.  the default install is ~/.thunderbird/profiles

thunderbird's profile setup in linux is identical to that in windows.  all you have to do is copy the profiles folder from windows and replace the one in linux.

but ...

since you indicate that your thunderbird resides on your desktop, you've done something funky with your install, and i have no idea where your profiles folder in linux would be.

---

### Post by hyper_ch on 2006-10-12
The default install is ~/.mozilla-tunderbird/profiles/... I think :)

You just can copy your profile folder from windows into the one in ubuntu and then you may have to chmod/chown files :)

---

### Post by puppy on 2006-10-12
Note that the profiles folder is probably in your home directory but "hidden", so you will have to enable "view hidden files" in Nautilus to see it etc ;)

---

### Post by timetunnel on 2006-10-12
Here's a thread that explains how to move your Thunderbird profile from Windows to Linux:

[http://ubuntuforums.org/showthread.php?t=100797](http://ubuntuforums.org/showthread.php?t=100797)

Especially this post:
[http://ubuntuforums.org/showpost.php?p=572675&postcount=6](http://ubuntuforums.org/showpost.php?p=572675&postcount=6)

---

### Post by tchoklat on 2006-10-24
done - now up and running thanks team!

---

