---
title: "XAMPP password"
date: 2006-07-30
forum: Absolute Beginner Talk
---

### Post by helphope on 2006-07-30
Hi everybody.
I installed a few weeks ago and then ... forgot everything aout it. Also the password. Is there any way :confused:   I can retrieve it? 
Otherwise I was wondering if I could disinstall it and then install it again?
Any hint? Thanks in advance

---

### Post by rowanparker on 2006-07-30
I'm guessing you could uninstall, making sure you remove all the config files then reinstall. But there maybe an easier way if anyone knows?

---

### Post by helphope on 2006-07-31
As far as I know, disintalling inLinux is different from Windows, and everything should be disintalled. Or maybe I'm wrong?

---

### Post by adamkane on 2006-07-31
Please let us know, if you are able to uninstall XAMPP.

---

### Post by timka1 on 2006-07-31
I installed XAMPP on Windows XP and the blurb made quite a lot of the fact that all you needed to do was delete the top folder and everything was gone. I.e. it didn't leave things lurking around to foul you up if you reinstalled.

I suspect this would be the case on Linux too...

---

### Post by rowanparker on 2006-08-03
You can give it a go.

---

### Post by helphope on 2006-08-07
:) :) Thanks everybody for answering and sorry for replying back so late.

Eventually I managed to cope with the problem just by reinstalling xampp:
- download the files
- sudo tar xvfz xampp-linux-1.5.3a.tar.gz -C /opt

Have a look at [http://www.apachefriends.org/en/xampp-linux.html](http://www.apachefriends.org/en/xampp-linux.html)

---

### Post by colo on 2006-08-07
"Uninstallting" lampp solely consists of executing `rm -rf /opt/lamp*`.

You might just want to run `/opt/lamp*/lamp* security` once more, though - this should let you re-set all needed passwords.

---

### Post by rowanparker on 2006-08-07
Glad you got it sorted.

---

