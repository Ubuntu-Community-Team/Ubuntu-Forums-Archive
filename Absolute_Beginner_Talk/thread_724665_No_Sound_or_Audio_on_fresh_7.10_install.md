---
title: "No Sound or Audio on fresh 7.10 install"
date: 2008-03-14
forum: Absolute Beginner Talk
---

### Post by mntamimi on 2008-03-14
Hey all. I just completed yesterday a fresh install of 7.10 and I can't get the sound to work.

Per this page: [https://wiki.ubuntu.com/Gutsy_Intel_HD_Audio_Controller](https://wiki.ubuntu.com/Gutsy_Intel_HD_Audio_Controller)
I tried running this line:
 lspci -n | grep `lspci | grep -i audio | awk '{print $1}'`

And got this response:
00:05.0 0403: 10de:03f0 (rev a2)

So I take that to mean that that bug doesn't apply to me, but I'm not sure.

I am using a Gigabyte GA-M61P-S3 motherboard that has an onboard audio chipset of Realtek ALC883.

I am a complete linux noob, so if you offer help, which I appreciate, it would probably be best to assume I don't much about what I am doing.

Thanks for any help!

---

### Post by MCrittenden on 2008-03-14
I'm sure you've probably already tried this, but make sure you open the volume control and turn everything up to make sure that's not the problem.  It's REALLY common that some hidden volume control that you've never heard of is muting everything.

Again, sorry if you already tried it. Had to check.

---

### Post by scragar on 2008-03-14
quick test:
```
sudo apt-get install asoundconf-gtk && asoundconf-gtk
```
make sure your soundcard is picked. once your sure your soundcard is picked you can safely uninstall it:
```
sudo apt-get --remove autoremove asoundconf-gtk
```

---

### Post by superprash2003 on 2008-03-14
hope this helps [http://prash-babu.blogspot.com/2008/02/sound-problems-in-ubuntu-gutsy-710.html](http://prash-babu.blogspot.com/2008/02/sound-problems-in-ubuntu-gutsy-710.html)

---

