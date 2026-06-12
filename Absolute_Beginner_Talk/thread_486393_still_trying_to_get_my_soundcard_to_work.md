---
title: "still trying to get my soundcard to work"
date: 2007-06-28
forum: Absolute Beginner Talk
---

### Post by Anarchy965 on 2007-06-28
Ok, I installed the newest version of alsa using the code 
```
wget ftp://ftp.alsa-project.org/pub/driver/alsa-driver-1.0.14.tar.bz2
tar -xjf alsa-driver-1.0.14.tar.bz2
cd alsa-driver-1.0.14
./configure
sudo make
sudo make install 
```

but now alsa is working with my onboard sound, not my actual soundcard. How do I change what soundcard alsa is set to? I looked in alsamixer but couldn't find anything.

---

### Post by Anarchy965 on 2007-06-28
also, should I have also done 
```
wget ftp://ftp.alsa-project.org/pub/lib/alsa-lib-1.0.14a.tar.bz2
tar -xjf alsa-lib-1.0.14a.tar.bz2
cd alsa-lib-1.0.14a
./configure
sudo make
sudo make install
```

and
```
wget ftp://ftp.alsa-project.org/pub/driver/alsa-utils-1.0.14.tar.bz2
tar -xjf alsa-utils-1.0.14.tar.bz2
cd alsa-utils-1.0.14
./configure
sudo make
sudo make install
```

because it didn't say to in the thread I looked at, but I think I should.

---

### Post by Anarchy965 on 2007-06-28
Bump

---

### Post by Anarchy965 on 2007-06-28
Ok, I think I know what to do. Now I'm trying ```
wget ftp://ftp.alsa-project.org/pub/driver/alsa-driver-1.0.14.tar.bz2
tar -xjf alsa-driver-1.0.14.tar.bz2
cd alsa-driver-1.0.14
sudo ./configure --with-kernel=/usr/src/linux-headers-$(uname -r) --with-cards=emu10k1 --with-oss=yes
sudo make
sudo make install 
```

I think this shouild get alsa working with my soundcard(emu 1212m).

---

### Post by techno-mole on 2007-06-28
do you have both your onboard sound and a pci card enabled, because things will get confused as the system wont know which one to use.
if you want to use a pci sound card i would advice disabling the onboard sound, you will need to go into your bios to do this.
generally ive found that using a pci sound card gives a little better performance than the onboard sound.
cheers.

---

### Post by Anarchy965 on 2007-06-28
I tried that, but now when I press the test button in the sounds settings window it says: 
```
audiotestsrc wave=sine freq=512 ! 
audioconvert ! audioresample ! gconfaudiosink: 
Could not open resource for writing.
```

Can someone help?

---

### Post by Anarchy965 on 2007-06-28
Also when I try to open alsamixer terminal replies:
```
alsamixer: function snd_ctl_open failed for default: No such device

```

---

### Post by Anarchy965 on 2007-06-28
Bump

---

### Post by cybermaster on 2007-12-19
hi i am new here and new tu ubuntu linux can any one tell me to where to type this code pls help me i also want to make my sound card work on ubuntu 

thanks

---

### Post by kpkeerthi on 2007-12-19
We need to know what sound card you have. Can you post the output of 
```

lspci | grep -i audio

```

---

### Post by Demosthenesaus on 2008-01-08
anyone have any idea how to install emu-tools in Ubuntu?

---

