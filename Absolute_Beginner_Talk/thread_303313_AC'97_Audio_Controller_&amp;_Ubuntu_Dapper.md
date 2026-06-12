---
title: "AC'97 Audio Controller &amp; Ubuntu Dapper"
date: 2006-11-20
forum: Absolute Beginner Talk
---

### Post by derekguy on 2006-11-20
Hi there everyone. I have a Compaq BT1800 which I have recently installed Ubuntu Dapper Drake on (go Shipit!) Nearly everything is workimg fine. I have Wireless and everything which makes me happy. Only one issue though, I cannot get the sound up and running. I am using a laptop and do not know how to find out whether the onboard speakers have been detected but the sound does not work when I plug in external speakers either. I have been into alsamixer and turned all my volume bars up. The soundcard has been detected with lspci giving

[INDENT]0000:00:1e.2 Multimedia audio controller: Intel Corporation 82801FB/FBM/FR/FW/FR W (ICH6 Family) AC'97 Audio Controller (rev 04)[/INDENT]

I don't know where to go next and have ben distracted by xgl (:D  it is cool) has anyone else had an issue like this? What would you suggest I do?

Cheers in advance everyone, and congratulations on a wicked OS!

---

### Post by ReaderRat on 2006-11-20
[**AC'97 ICH6 Audio**](http://ubuntuforums.org/showpost.php?p=1733758&postcount=3)
Sound Solutions - Comprehensive Guide
       **[http://doc.gwos.org/index.php/Comprehensive_Sound_Problems_Solutions_Guide](http://doc.gwos.org/index.php/Comprehensive_Sound_Problems_Solutions_Guide)**

---

### Post by dolphinholmer on 2006-11-20
The first link you provide readerrat is written wrong. The text it displays is from /etc/modprobe.d/alsa-base not /etc/apt/sources.list as it says.

---

### Post by ReaderRat on 2006-11-20
Curses! I saved the wrong post. Sorry.
Go to "Tags" (at the top of the page), click on it and enter "ICH6" (without the quotes) in the search box. You shoule get several posts on this. (Or try "AC'97")

---

### Post by derekguy on 2006-11-23
Cheers guys, you all rock some good reading here. I will report with my results soon. Thanks for the tips.:KS

---

### Post by rlozano on 2006-11-24
[QUOTE=derekguy

[INDENT]0000:00:1e.2 Multimedia audio controller: Intel Corporation 82801FB/FBM/FR/FW/FR W (ICH6 Family) AC'97 Audio Controller (rev 04)[/INDENT]

[/QUOTE]

i believe this AC'97 rev 04 is a not supported yet even in edgy. but hopefully you'll be lucky to make it work. ](*,)

---

### Post by derekguy on 2006-11-24
Oh it does now haha! I am on dapper still and the problem was that I had the external amplifier checkbox checked in alsamixer (seems I checked everything without thinking) Well for anyone searching, this soundcard does work under dapper and I am assuming edgy (will start dist. upgrade now) Thanks for the great links everyone The exhaustive guide was my answer :D

---

### Post by derekguy on 2006-11-24
ReaderRat you are a legend!

---

