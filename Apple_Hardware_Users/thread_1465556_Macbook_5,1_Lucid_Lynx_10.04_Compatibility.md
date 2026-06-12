---
title: "Macbook 5,1 Lucid Lynx 10.04 Compatibility"
date: 2010-04-29
forum: Apple Hardware Users
---

### Post by undoIT on 2010-04-29
I have been using Lucid on my Macbook 5,1 since beta 1. Everything appears to be updated to stable now. A recurring problem has been that after rebooting, I often get an error message and I have to run Ubuntu in low-graphics mode. The Nvidia proprietary blob driver is not loaded. I must run sudo nvidia-xconfig and reboot to get it working again. It doesn't happen all the times,  but most reboots it does. Any idea how to fix this?

Also, after installing the Nvidia proprietary driver, plymouth looks like crap while Ubuntu is booting. It seems to be running at 640x480 with 16 colors. Plymouth looks fine if the Nvidia driver is not installed and Nouveau drive is running. Any fix for this?

Other than that, everything seems to be running quite well.

---

### Post by einstais on 2010-04-29
i just upgrade it from 9.10
i had a problem with grub and i needed to force a reinstall but its ok now 


touchpad is a little more sensitive by default but it can be easily fixed 
the screen light sensor for the brightness still doesnt work really well. (i ve made a script for that)

reboot works,
also when you insert earphones the sound from the laptop's speaker stops normally (in 9.10 it didnt in mine)

---

### Post by rantom on 2010-05-07
I can confirm, that I have this bug as well. It's quite annoying, since I'm using so called Clamshell-mode (external display on my MBP and my lid is closed). I also can't adjust my screens brightness, thus I'm on 100 % brightness all the time.

I also think that the touchpad is too sensitive and misses some features, as in four finger-actions. But anyways how should I fix the Nvidia-error?

---

### Post by undoIT on 2010-05-07
> **rantom said:**
> I can confirm, that I have this bug as well. It's quite annoying, since I'm using so called Clamshell-mode (external display on my MBP and my lid is closed). I also can't adjust my screens brightness, thus I'm on 100 % brightness all the time.

I also think that the touchpad is too sensitive and misses some features, as in four finger-actions. But anyways how should I fix the Nvidia-error?

Try installing nvidia-bl-dkms and pommed for brightness adjustment after adding Mactel ppa:

[https://launchpad.net/~mactel-support/+archive/ppa?field.series_filter=lucid](https://launchpad.net/~mactel-support/+archive/ppa?field.series_filter=lucid)

Also, see this section for fine-tuning pommed configuration:

[https://help.ubuntu.com/community/MacBookPro5-5/Karmic#Keyboard%20Functions](https://help.ubuntu.com/community/MacBookPro5-5/Karmic#Keyboard%20Functions)

I don't know if there is a way to permanently fix the low-graphics mode bug yet. Does your splash screen during boot look okay, or is it running at low resolution and colors?

---

### Post by zAfi on 2010-05-20
> **einstais said:**
> touchpad is a little more sensitive by default but it can be easily fixed
And how if I may ask?

I played around a little bit and even installed gsynaptics, but it's still way too sensitive. I'm used to tap-to-click and while scrolling with two fingers too often text gets marked.

---

### Post by nataraj88 on 2010-05-20
> **zAfi said:**
> And how if I may ask?

I played around a little bit and even installed gsynaptics, but it's still way too sensitive. I'm used to tap-to-click and while scrolling with two fingers too often text gets marked.

Someone posted this in another thread.  If you search you can probably find more details.  I haven't tried it yet.

sudo apt-get install xserver-xorg-input-synaptics

Nataraj

---

### Post by hadi2 on 2010-05-27
@undoIT 
After installing nvidia drivers add these lines to the end of your  /etc/modprobe.d/blacklist.conf file :

blacklist amd76x_edac
blacklist vga16fb
blacklist nouveau
blacklist rivafb
blacklist nvidiafb
blacklist rivatv

---

### Post by undoIT on 2010-05-31
> **hadi2 said:**
> @undoIT 
After installing nvidia drivers add these lines to the end of your  /etc/modprobe.d/blacklist.conf file :

blacklist amd76x_edac
blacklist vga16fb
blacklist nouveau
blacklist rivafb
blacklist nvidiafb
blacklist rivatv

"blacklist amd76x_edac" is already in the blacklist.conf file. i added the rest of the lines listed above, rebooted and i still get the low graphics mode warning after reboot. to fix this i have:

1. press Ctrl Alt F2 for tty after selecting run once
2. login with username and password
3. run sudo service gdm start
4. enter password again
5. run sudo service gdm stop

obviously this is a pain in the butt. any other ideas?

---

