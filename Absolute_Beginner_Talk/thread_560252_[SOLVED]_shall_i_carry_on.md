---
title: "[SOLVED] shall i carry on?"
date: 2007-09-26
forum: Absolute Beginner Talk
---

### Post by maryjanua on 2007-09-26
i'm on the verge of giving up with ubuntu theres nothing but problems i cant be sure that if i switch the pc off it will come on in the same configuration and work. 3d effects are nonexistant,
the sound does what it likes, i just dont think this can be reliable enough for my needs much as i would like it to be. if anyone can convince me otherwise please feel free :(:(:(

---

### Post by BrendanM on 2007-09-26
Is your computer very new? It's possible that you have hardware that isn't well supported yet. You might want to wait until the next version of Ubuntu, 7.10, comes out next month and then give that a try. It should have support built in for a lot of newer hardware.

---

### Post by maryjanua on 2007-09-26
yeah its new to me tho im not exactly sure how new the actual compnonents are judging by how fast these things move nowadays
i have an asrock 4core dual sata2 mobo, celeron d 352+ 3.2 ghz  512 ddr400, ati x1550 agp , 160gb ide seagate ,80gb ide seagate, the soundcard is onboard and its realtek hd audio 
is that classed as new?

---

### Post by dwhitney67 on 2007-09-26
Have you attempted to run the LiveCD on your system?  Does it meet your "initial" expectations?  I mean, does X11 run, do you have network support, sound, etc?

If the answer is yes to all of the above, then you have a Linux compatible system.  If anything fails to work, then do not give up hope because there might be a solution; but you are going to have to research the web (and/or this forum) for specifics concerning the h/w on your system.

---

### Post by maryjanua on 2007-09-26
yes the sound etc works from the cd
but upon initial install 2wks agoi got no sound and had to write my own driver apparently
when i got an update yesterday i had to then reboot 
upon restart ..... no sound again 
it worked for 10 days or so also there seem to be a lot of folk having problems gettin 3d with the video card i have so thats not really bothering me its the sound ( i need tunes man!!)
 i have tried repeating what i did to fix the sound last time but its not doing it now or i am doing something wrong i dunno
i'm still pretty new at the cmd line

---

### Post by Dark Hornet on 2007-09-27
I have to say that my experience with Ubuntu has been great...sure I have had some issues, but I have learned boat loads from each "issue", and I am better for it.  Apart from seeing your system, I am not sure what to say regarding your sound issue other than to take a look in depth at what the updates where, and see if any of them would have impacted your sound.  I say stick with it, you will (with the help of the community :) ) figure things out, and hopefully you will gain something from it....Good luck!

---

### Post by dwhitney67 on 2007-09-27
> **maryjanua said:**
> yes the sound etc works from the cd
but upon initial install 2wks agoi got no sound and had to write my own driver apparently
when i got an update yesterday i had to then reboot 
upon restart ..... no sound again 
it worked for 10 days or so also there seem to be a lot of folk having problems gettin 3d with the video card i have so thats not really bothering me its the sound ( i need tunes man!!)
 i have tried repeating what i did to fix the sound last time but its not doing it now or i am doing something wrong i dunno
i'm still pretty new at the cmd line

When your system boots, see if grub will permit you to select the previous kernel version.  You stated that you updated your system (with the Ubuntu updates); I bet the new kernel is affecting your system.

Alternatively, and I am no expert on this, you can consider removing your Alsa drivers and then re-installing them.

---

### Post by maryjanua on 2007-09-27
yeah i can boot to the earlier kernel but theres no sound there either
iv also tried removing and reinstalling alsa..... no luck but thanks anyway:)

---

### Post by maryjanua on 2007-09-27
wohoo i fixed the sound with a little help
had to recompile alsa :guitar::guitar:

---

### Post by dwhitney67 on 2007-09-27
Please let me (and everyone else) how you did this.  There seems to be lots of "complaints" on the forum with others having similar problems as your system had.

Please state where you got the source code and the steps you took to compile/install it.

Thank you and congratulations.

---

### Post by maryjanua on 2007-09-27
heres what i did:

rm /home/billym/.asoundrc
sudo apt-get --purge remove linux-sound-base alsa-base alsa-utils
sudo apt-get install linux-sound-base alsa-base alsa-utils 
sudo apt-get install gdm ubuntu-desktop

reboot the pc   then; aplay -l

sudo apt-get install build-essential ncurses-dev gettext
sudo apt-get install libncurses5-dev
sudo apt-get install linux-headers-'uname -r'
sudo mkdir -p /usr/src/alsa
cd /usr/src/alsa
sudo cp /home/billym/realtek-linux-audiopack-4.06b/alsa* .
sudo tar -xvjf alsa-driver-rt20070820.tar.bz2
sudo tar -xvjf alsa-lib-1.0.14.tar.bz2
sudo tar -xvjf alsa-utils-1.0.14.tar.bz2
cd alsa-driver*
sudo ./configure --with-cards=hda-intel
sudo make
sudo make install
cd ../alsa-lib*
sudo ./configure
sudo make
sudo make install
cd ../alsa-utils*
sudo ./configure
sudo make
sudo make install

folk will have to find out their own specific audio card and drivers and replace the code accordingly     mines is a realtek hdaudio  drver is realtek alc888

hope this helps it worked for me:KS
ps. all this was really the work of mali2297 i just copy n pasted

---

### Post by maryjanua on 2007-09-27
o yeah i got the sound driver directly from realtek and downloaded it to my desktop
same with alsa

---

### Post by dwhitney67 on 2007-09-27
Thanks for the instructions.  I once had issues updating the kernel on my Fedora Core 5 system (I lost sound card and SD card support).

Someone on another forum recommended that I uninstall/reinstall Alsa, or just rebuild it like you did.  My solution was to go back to the previous kernel version.  It seemed a lot easier.  :-)

Now when I get updates for my FC5 system, I specifically exclude kernel updates.  I would recommend the same for those who are running Ubuntu.  There generally is no need to update the kernel if your system already has one that works.

"glibc" (the GNU C Library) is coupled to the kernel source header files, thus if one updates the kernel and the kernel source, then glibc must also be updated.  Fortunately it is easy to exclude these items using Ubuntu graphical interface.

---

### Post by maryjanua on 2007-09-27
i'll remember nxt time"[COLOR="Red"]DONT UPGRADE THE KERNEL!![/COLOR]"

---

### Post by hyper_ch on 2007-09-27
Generally I tend to say if you have to ask others if you should stick to Linux then the answer is more likely to be "No, you shouldn't"

---

### Post by maryjanua on 2007-09-27
i'm gonna stick with it as i'm learning loads of stuff that i just didnt know was going on in windos
i'v heard it said that "if its not hard its not worth doing" that kind of applies to me
hopefully folk in the forum will continue to help when i get stuck:):):) (bcos i probably will)

---

### Post by hyper_ch on 2007-09-27
if you are willing to learn then it is for good for you... but if you ask yourself whether you should stick to it that indicates for me you don't want to learn and hence my recommendation was to not stick to it.

---

### Post by sahra on 2007-09-27
> **dwhitney67 said:**
> Please let me (and everyone else) how you did this.  There seems to be lots of "complaints" on the forum with others having similar problems as your system had.

It doesn't seem to matter (although the instructions are available on a variety of threads on this forum).  After having a number of initial problems with sound not working, I have reinstalled Alsa *three times* now -- and every time I do an update, it breaks again.  Even if that's a basic security update that I should do to ensure my system is, y'know, secure.

No Linux should fail to work like that.


-S

---

### Post by maryjanua on 2007-09-27
sorry its not workin4 u sahra it fixed mine im no xpert so i wouldnt know whats up with yours needin redone every time

---

