---
title: "Toshiba Satellite sleep problems"
date: 2007-06-08
forum: Absolute Beginner Talk
---

### Post by ChrisE on 2007-06-08
I've got a toshiba satellite m35x-s114.

Periodically when I put it to sleep (but seemingly most often when I try to switch users from sleeping) the touchpad will simply stop responding.  My only way of addressing this problem is to restart the computer, which I believe has always fixed the problem.

Another problem when putting the computer to sleep is that it loses its connection to the wireless network.  This is easily fixed by going into network connections and toggling the wireless connection off and then on again.  Nevertheless, it's a pain.

So, what can I do to make my ubuntu laptop a little more convenient to use?

Thanks,
chris

---

### Post by Inxsible on 2007-06-08
Have you tried installing uswsusp?
```
sudo aptitude install uswsusp
```
 
After installing it, check this link out and see post # 19, to change your hibernate.sh and sleep.sh. You should be good to go after that (i hope).
 
[Post 19]("http://ubuntuforums.org/showthread.php?t=194426&page=2")
 
Note: This doesn't always work for everyone, so if you want to try something else then you should.

---

### Post by Inxsible on 2007-06-08
Before you try what I posted up there would be this: 
If you add the ec_intr=0 option in your menu.lst you can hibernate and sleep better on Toshiba architecture
```
gksudo gedit /boot/grub/menu.lst
```
 
Look for this line ```
defoptions ro quiet splash
```
At the end of it add ec_intr=0. So your new line would be
```
defoptions ro quiet splash ec_intr=0
```
 
Try this and see if it works ! If not try the uswsusp.

---

