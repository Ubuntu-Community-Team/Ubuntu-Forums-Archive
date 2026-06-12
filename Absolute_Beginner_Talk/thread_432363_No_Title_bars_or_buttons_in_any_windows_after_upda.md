---
title: "No Title bars or buttons in any windows after update"
date: 2007-05-03
forum: Absolute Beginner Talk
---

### Post by dannemil on 2007-05-03
Help. Since the gnome update today I have completely lost all of the title bars on windows. None of the windows have any buttons (min, max, etc) either. Running Feisty. :(

---

### Post by Tux Aubrey on 2007-05-03
If you are running Beryl or "Desktop Effects", try turning them off.  

I have had this problem with Feisty on my desktop machine with nVidia drivers.  Worked on Edgy, but not now.  Seems to be a common problem.

---

### Post by AncientPC on 2007-05-03
I have this same exact problem.  I did turn on desktop effects with the nVidia driver to test them out, but they didn't work so I turned them back off.

My title bars are still missing though.

---

### Post by dannemil on 2007-05-03
Thanks, but I'm not running Beryl. I tried turning off desktop effects, but still no title bars or buttons. I am using nvidia, but all was working fine yesterday with Feisty until the update today.

---

### Post by dannemil on 2007-05-03
Update: I did what was suggested in this thread as far as editing your /etc/X11/xorg.conf file, and it fixed the problems with the missing title bars. Still cannot use the desktop effects though.

[http://ubuntuforums.org/showthread.php?t=417146&highlight=title+bars]("http://ubuntuforums.org/showthread.php?t=417146&highlight=title+bars")

To edit your xorg.conf:

cd /etc/X11
sudo cp xorg.conf xorg.conf.backup
sudo nano xorg.conf

---

### Post by AncientPC on 2007-05-04
I visited the link and followed the instructions but it didn't fix my missng title bar problem.

However I did fix it by going back to Desktop Effects, trying out the new settings, and then selecting "Keep Settings".

---

