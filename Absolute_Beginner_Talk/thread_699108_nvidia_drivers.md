---
title: "nvidia drivers"
date: 2008-02-17
forum: Absolute Beginner Talk
---

### Post by DonDodge on 2008-02-17
I was able to get my desktop effects working just fine on an old x86 Gutsy install after I hooked it into a new computer. I just let it download the restricted driver and boom, there it was. Unfortunately, that install has been doomed for quite some time because of instability problems that persisted even when I put the new computer under it.

Since the new computer is an AMD64 X2 5000+ Black Edition with a MSI 7300LE nvidia GeForce, 256 mb PCI-E card on a MSI SLI motherboard, I decided to go with the AMD64 version of Gutsy. I tried to get a good install but it didn't work out. The restricted drivers would kill the system. I'd get about two boots out of it and it was finished. After a few tries, I gave up and went back to x86.

Now, Ubuntu x86 install insists on using a vesa 800x600 low res driver. Desktop effects wants nvidia-glx-new_100.14.19+2.6.22.4-14.9_i386.deb, which it has. The restricted drivers manager says this NVIDIA accelerated graphics driver is enabled and in use but "Screen and Graphics" doesn't even show it as an option. All I get is drivers that allow me lousy resolutions and no desktop effects. When I choose the Nvidia proprietary driver it restarts with a silly low graphics mode warning box with choices that only take me back to the simple vesa compliant 800x600 driver when it gets back to the desktop after the logoff/login exercise eventually completes.

If I select somethig else like the Nvidia Riva 128, I can get a decent resolution of 1152 x 768 but at alousy 55 MHz and, of course, no desktop effects and no acceleration.

If I run the nvidia-glx-new_100.14.19+2.6.22.4-14.9_i386.deb again, the package installer gives me Error: Conflicts with the installed package 'nvidia-glx'. Not hardly true since that package isn't even installed. Synaptics agrees. So all I'm able to do with this thing is go around in circles. How can I break the cycle?

I did notice that Synaptics has some suggestions to mark for download to go with the nvidia driver but every time I look, it offers new suggestions. I guess it doesn't matter right now because Ubuntu forgot how to make my modem dial. Had to come back to old reliable XP to get some actual work done.

---

### Post by Kilz on 2008-02-17
> **DonDodge said:**
> I was able to get my desktop effects working just fine on an old x86 Gutsy install after I hooked it into a new computer. I just let it download the restricted driver and boom, there it was. Unfortunately, that install has been doomed for quite some time because of instability problems that persisted even when I put the new computer under it.

Since the new computer is an AMD64 X2 5000+ Black Edition with a MSI 7300LE nvidia GeForce, 256 mb PCI-E card on a MSI SLI motherboard, I decided to go with the AMD64 version of Gutsy. I tried to get a good install but it didn't work out. The restricted drivers would kill the system. I'd get about two boots out of it and it was finished. After a few tries, I gave up and went back to x86.

Now, Ubuntu x86 install insists on using a vesa 800x600 low res driver. Desktop effects wants nvidia-glx-new_100.14.19+2.6.22.4-14.9_i386.deb, which it has. The restricted drivers manager says this NVIDIA accelerated graphics driver is enabled and in use but "Screen and Graphics" doesn't even show it as an option. All I get is drivers that allow me lousy resolutions and no desktop effects. When I choose the Nvidia proprietary driver it restarts with a silly low graphics mode warning box with choices that only take me back to the simple vesa compliant 800x600 driver when it gets back to the desktop after the logoff/login exercise eventually completes.

If I select somethig else like the Nvidia Riva 128, I can get a decent resolution of 1152 x 768 but at alousy 55 MHz and, of course, no desktop effects and no acceleration.

If I run the nvidia-glx-new_100.14.19+2.6.22.4-14.9_i386.deb again, the package installer gives me Error: Conflicts with the installed package 'nvidia-glx'. Not hardly true since that package isn't even installed. Synaptics agrees. So all I'm able to do with this thing is go around in circles. How can I break the cycle?

I did notice that Synaptics has some suggestions to mark for download to go with the nvidia driver but every time I look, it offers new suggestions. I guess it doesn't matter right now because Ubuntu forgot how to make my modem dial. Had to come back to old reliable XP to get some actual work done.

Looks like going to 32bit didnt help, did you post a question to the [64bit section]("http://ubuntuforums.org/forumdisplay.php?f=134") when you were having problems? It was probably a video driver issue that [envy]("http://albertomilone.com/nvidia_scripts1.html") could have solved.

---

### Post by DonDodge on 2008-02-17
The original flaky install from year was x86 32bit but as I said, it was doomed. I pretty much gave up on it but had hopes it would do better on the new computer. My video with all the effects worked great but it was still crap. 

I didn't spend all that much time and effort on the 64bit and posted no questions.

 l'll download the envy and see if that can negoiotiate with Ubuntu. Thanks for the tip

---

### Post by DonDodge on 2008-02-17
Envy is just a monumental waste of time. After doing a fresh format and install of Gutsy x86, Envy tried and tried to accomplish whatever it is it's supposed to do. It spent 8 hours downloading different combinations of programs and libraries, etc. with the same result. That being nothing but failures. I should have taken note beforehand so I'd know but I think that silly program downloaded over 100 mb of files.

---

### Post by spiderbatdad on 2008-02-17
[https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia](https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia)

---

