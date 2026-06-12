---
title: "Any way to remove all kubuntu-related apps?"
date: 2006-06-15
forum: Absolute Beginner Talk
---

### Post by Henrythewound on 2006-06-15
Hey there, a while back I wanted to check out kubuntu and xubuntu so I installed them as optional choices at the login screen. I believe I used a command similar to 

sudo aptitude install kubuntu-desktop

or something similar (I can paste the exact command from my home PC when I get home tonight). I did not care for the KDE feel so I removed it from my system (so I thought) via the following command

sudo aptitude remove kubuntu-desktop

I may have used "purge" instead of remove (not sure). I am not positive of the differences in purge and remove, but kubuntu is no longer a choice at the login screen although I still see what I think are KDE-related apps (most start with the letter "K") in my applications menu. I do have xubuntu still installed so I suppose its possible that these apps are from that install. I suppose I could go through manually and remove each program that I do not want to use, but I was wondering if there was a blanket means of removing these as I want to have the bare minimum apps installed and only the ones I use most frequently. Sorry if this is vague, I can do a better description later at home if anyone needs it.

Thanks for any help!

Joe aka Wound

---

### Post by aysiu on 2006-06-15
You have a couple of options:
[http://www.psychocats.net/ubuntu/puregnome](http://www.psychocats.net/ubuntu/puregnome)

```
sudo aptitude update
sudo aptitude install gtkorphan gksu
gksudo gtkorphan
```

---

### Post by bruce89 on 2006-06-15
[http://psychocats.net/ubuntu/puregnome.php](http://psychocats.net/ubuntu/puregnome.php) to get back to GNOME only.

EDIT: Too late, I knew aysiu would beat me to it!

---

### Post by Henrythewound on 2006-06-15
Sounds exactly like what i was looking for.

Talk about speedy answers, thanks to both of you!
Joe:razz:

---

### Post by bruce89 on 2006-06-15
[QUOTE=Henrythewound]Talk about speedy answers[/QUOTE]
Sometimes not speedy enough though!

---

