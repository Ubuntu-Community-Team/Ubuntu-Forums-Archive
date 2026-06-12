---
title: "Upgrade to dapper while in 5.10 breezy??"
date: 2006-10-17
forum: Absolute Beginner Talk
---

### Post by crimesaucer on 2006-10-17
Hello, I just had a version of xubuntu 6.0.6 running on my notebook and I loved it. Then I tried to add my Windows Xp in a dual boot, and I messed up so I went ahead and did a fresh install of Windows Xp, and then tried to add the xubuntu 6.06 Dapper LTS, and the CD that I had used, started to error. It had worked fine on the last install, but it froze part way through the install process and I was unable to finish it.

So I went back to windows and downloaded another ISO image and checked it with md5 (passed everytime) and from going through this process for about 10 different times from both Softpedia and the ubuntu/xubuntu download page, I was unable to install.

Each time except once, failed the disk check, and the one time that it actually passed, it froze at 87% finished, and then failed the disk check when I tried to see what the problem was.

So, I didn't know if it was my CD, which had a few install ISO's burnt on to it and then erased, or a problem with the ISO images. And I tried both the Alternate and Desktop for both 6.06 LTS and 6.10 Beta.

Well, I had an install cd of Breezy, and I figure I could hopefully install it and upgrade to xubuntu 6.06 LTS by adding dapper repositories and using terminal to install xubuntu-desktop.

Is this possible and could someone give me simple directions if that is possible?

Thanks,
-c.

---

### Post by Kateikyoushi on 2006-10-17
One of my rewriteables died this week and I wondered what's wrong with the iso. Might be the disc in your case as well.

You can also upgrade from breezy. [GUIDE]("http://ubuntuguide.org/wiki/Dapper#How_to_upgrade_from_Hoary_Hedgehog_-.3E_Breezy_Badger_-.3E_Dapper_Drake")

---

### Post by crimesaucer on 2006-10-17
it worked, thanks, now all I have to do is change to the xubuntu desktop, will all the packages of ubuntu 6.06 disapear?

I'm also thinking about upgrading to the edgy eft, is it almost finished?

---

### Post by Kateikyoushi on 2006-10-17
Edgy eft isn't finished yet but, it is getting close final release is scheduled for the 26th of october.

This will install xubuntu
```
sudo aptitude update
sudo aptitude install xubuntu-desktop
```

Log out and select xfce in session.

If works try this to remove ubuntu-desktop, it is not removed by default you can choose which one to use at login.

```
sudo aptitude remove ubuntu-desktop
```

---

### Post by crimesaucer on 2006-10-17
thank you for the help.

---

### Post by euphro on 2006-11-03
Kateikyoushi thanks very much for the link.  That has helped me a lot, thanks :)

---

