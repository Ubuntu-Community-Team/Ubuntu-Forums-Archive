---
title: "Linux Noob needs help installing FireFox and other programs"
date: 2006-09-04
forum: Absolute Beginner Talk
---

### Post by TheMatt on 2006-09-04
I am relatively new to Linux. I need help installing programs like Firefox and Thunderbird. They are all in .tar.gz archives except for goggle earth, which is in a .bin format. I have tried the instructions on Mozilla's site and Google's site but cannot figgure it out. I get errors when I follow their instructions. Help with this would be much appreciated.

---

### Post by aysiu on 2006-09-04
[http://www.monkeyblog.org/ubuntu/installing](http://www.monkeyblog.org/ubuntu/installing) is a good place to start.

---

### Post by meng on 2006-09-04
Also, Firefox and Thunderbird can be installed from Ubuntu repositories.

---

### Post by aysiu on 2006-09-04
Oops! Just saw that you were a Kubuntu user--in that case that link I gave is slightly less helpful.

Try this:
[http://www.psychocats.net/ubuntu/installingsoftware](http://www.psychocats.net/ubuntu/installingsoftware)

---

### Post by TheMatt on 2006-09-04
> **aysiu said:**
> Oops! Just saw that you were a Kubuntu user--in that case that link I gave is slightly less helpful.
 
 Try this:
 [http://www.psychocats.net/ubuntu/installingsoftware](http://www.psychocats.net/ubuntu/installingsoftware)
 That seemed to work. I followed the instructions to enable extra repositories. I got everything installed but google earth. It says its installed in adept, but I can't seem to find it or any of its program files. These are the programs I downloaded:
 Audacity
 Gaim
 GIMP
 Firefox
 Thunderbird
 Google Earth
 I can successfully run all of these except for google earth.
 
 The other thing I would like to do is put shortcuts to all these new programs in the applications menu.

---

### Post by aysiu on 2006-09-04
If you've enabled extra repositories, you can install those programs by pasting this command in the terminal: ```
sudo aptitude update && sudo aptitude install audacity gaim gimp firefox mozilla-thunderbird
``` They should show up in your KMenu later.

Google Earth is a special case. For Google Earth, try [this script](http://www.ubuntuforums.org/showthread.php?p=1138374#post1138374).

---

### Post by TheMatt on 2006-09-04
OK, I got it working. Goggle earth started working when its shortcut along with that of firefox and all the other programs I installed appeared on the applications menu.
 
Thank you so much for all the help!

---

