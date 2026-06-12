---
title: "Help with MacBook Pro 5,5"
date: 2010-06-15
forum: Apple Hardware Users
---

### Post by yhan2000 on 2010-06-15
Hi,

I had just installed a fresh version of Ubuntu on my 13' MacBook Pro 5,5. and after the installation, I did a full upgrade to the latest version of ubuntu 10.04.32.22.

And then I realised that the sound is not working, isight is not working, nor the wireless connection are not there either.

So I did some search through google, and followed the full instruction from: [https://help.ubuntu.com/community/MacBookPro5-5/Lucid](https://help.ubuntu.com/community/MacBookPro5-5/Lucid)

After all, the wireless works now, but the sound and isight are still cannot be found. I can't even start the music player, and I believe that the drivers are missing for those.

By the way, I didn't use bootcamp for partition, could that be the problem? 


Thanks for any comments.

---

### Post by Ravernomina on 2010-06-16
> **yhan2000 said:**
> Hi,

I had just installed a fresh version of Ubuntu on my 13' MacBook Pro 5,5. and after the installation, I did a full upgrade to the latest version of ubuntu 10.04.32.22.

And then I realised that the sound is not working, isight is not working, nor the wireless connection are not there either.

So I did some search through google, and followed the full instruction from: [https://help.ubuntu.com/community/MacBookPro5-5/Lucid](https://help.ubuntu.com/community/MacBookPro5-5/Lucid)

After all, the wireless works now, but the sound and isight are still cannot be found. I can't even start the music player, and I believe that the drivers are missing for those.

By the way, I didn't use bootcamp for partition, could that be the problem? 


Thanks for any comments.

Do this

1. Open terminal then type ```
gnome-alsamixer
```
2. Once it if open Make sure you unmute Front Speaker and turn it all the way up
3. Close ALSA mixer
4.Test Sound Post results

---

### Post by yhan2000 on 2010-06-16
Hi,

I tried that, either type through the terminal "gnome-alsamixer", or open through the UI (applications -> sound and video -> Gonme Alsa mixer), they both went to a new window, but blank inside. 

This is really strange?

Plus, I just realized that the wifi is working, but the icon on the notification are (top right) was never correct, either a block of white, or some other icons.



Thanks.

---

### Post by Ravernomina on 2010-06-16
> **yhan2000 said:**
> Hi,

I tried that, either type through the terminal "gnome-alsamixer", or open through the UI (applications -> sound and video -> Gonme Alsa mixer), they both went to a new window, but blank inside. 

This is really strange?

Plus, I just realized that the wifi is working, but the icon on the notification are (top right) was never correct, either a block of white, or some other icons.



Thanks.

What Version of Ubuntu are you Using my Friend?

---

### Post by yhan2000 on 2010-06-16
10.04.32.22

I believe the latest one.

---

### Post by Ravernomina on 2010-06-16
> **yhan2000 said:**
> 10.04.32.22

I believe the latest one.

hmm you might have a glitch.... try a reinstall??

---

### Post by yhan2000 on 2010-06-16
Obviously, that would be my last option, but want to give a try for few more solutions.

---

### Post by linuxopjemac on 2010-06-16
Sound:
Did you try altering /etc/modprobe.d/alsa-base.conf ?

```
gksudo gedit /etc/modprobe.d/alsa-base.conf
```

and add 
```

options snd-hda-intel model=mbp55
```

at the end

---

### Post by yhan2000 on 2010-06-16
Yes, that's there already.

---

### Post by yhan2000 on 2010-06-16
Ok, I had just tried to re-insatll ubuntu.

and everything works well, until it complete installation and restart the computer.

after the CD was automatically ejected, heaps of error showing up

[ 1590.978332] end_request: I/O error, dev sr0, sector 507136

and there are about 100 error lines like this, and they the computer just stay there forever, I had to press the power button to restart the computer.

would that be the reason of my problem?

Thanks

---

### Post by yhan2000 on 2010-06-16
By the way, after reboot and back into ubuntu first time, still no sound, no isight working

---

### Post by alexmurray on 2010-06-16
You'll need to re-add the model=mbp55 line to your alsa-base.conf for sound to work. Also the errors you got after finishing the install are normal - see the release notes for more info [https://wiki.ubuntu.com/LucidLynx/ReleaseNotes#I/O](https://wiki.ubuntu.com/LucidLynx/ReleaseNotes#I/O) error after CD is ejected at end of install

---

### Post by yhan2000 on 2010-06-16
So what i suppose to do now after the refresh installation? update ubuntu?

---

### Post by yhan2000 on 2010-06-18
All working now after re-installation :)

---

### Post by alexmurray on 2010-06-18
Great to hear, well done for persevering.

---

### Post by DCGStudios on 2010-06-18
> **yhan2000 said:**
> All working now after re-installation :)

Iv been running different linux distro's on my macbook for a long time now, and honestly ALL upgrades cause nothing but hours of debugging and headaches. For anyone else reading this I STRONGLY recommend creating a seperate /home partition and doing a fresh install of the OS rather then system upgrades. 

This is a very comprehensive tutorial on how to set it up..

[http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome)

---

