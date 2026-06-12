---
title: "Intrepid on MacBook - impressions"
date: 2008-11-05
forum: Apple Hardware Users
---

### Post by rickbsgu on 2008-11-05
Just upgraded on my White MacBook Core 2 Duo.

8.10 appears to be very solid, I'm impressed.  After a little tweaking with the trackpad settings, I was able to get two finger scroll and two finger right mouse click working (the most important items to me.)  For sound, I had to take the 'PCM' sliders from bottom to top, and they worked fine.  Function key assignments from my 8.04 install transferred completely transparently.

I use eclipse for jdk development - on 8.04, it would crash, frequently.  So, far, I haven't seen that on 8.10.  Also, the OpenGL would just 'blink out' under 8.04.  That doesn't seem to be happening on 8.10.

All in all, I'd say 8.10 really brings Ubuntu to the fore, at least on the MacBook.  It definitely appears ready for PrimeTime.

rickb

---

### Post by rickbsgu on 2008-11-05
Oops - found an issue:

I can't get multiple selection in lists to work.

In 8.04 multiple selections worked with shift-mousebtn, and sparse multiple selections worked with shift-ctl-mousebtn.

In 8.10, none of the above work.

Anyone have any ideas?

rickb

Followup - I figured out the multiple selection problem: syndaemon is blocking out the mouse button when any key is pressed.  The '-k' option allows the modifier keys to come through.

So now multiple selections are working fine.

rickb

---

### Post by aldeayeah6 on 2008-11-05
I have a MacBook 3.1 (first Santa Rosa model), with the international (Spanish) keyboard. I made a clean 8.10 install from the LiveCD. I had the following out-of-the-box issues:

1) ALSA freezing on shutdown.

This is a known bug. See [http://ubuntuforums.org/showthread.php?t=966436](http://ubuntuforums.org/showthread.php?t=966436)

2) Bad default touchpad settings

Two fingers are set to middle button and three fingers are set right button, no two-finger scrolling, and the touchpad is way too sensitive).

Unlike everyone, I can't get the XML hal policy configuration file thing to work (following the instructions over at [https://wiki.ubuntu.com/MacBook/SantaRosa](https://wiki.ubuntu.com/MacBook/SantaRosa)). Does anyone else have this problem?

3) Swapped keyboard keys (<> and ºª)

This is another typical issue on the international MacBook models.

I fixed it using System->Preferences->Keyboard->Layouts->Options->Miscellaneous->Swap keycodes...
That did the trick, but only in the graphic environment. Isn't there a better way?

4) Eject button doesn't work.

I installed pommed and it works. Looks like a HAL bug.

---

### Post by mattgaunt on 2008-11-05
I was fairly happy with it, had the odd problem as you do with any install of ubuntu on any computer.

My only problem at the moment is compiz has stopped working and I can't see any reason why :-S

Oooo and WPA Enterprise doesn't work which is the worst bit because I need it for uni, but I still got OS X :-(

---

### Post by cyberdork33 on 2008-11-05
> **aldeayeah6 said:**
> 2) Bad default touchpad settings

Two fingers are set to middle button and three fingers are set right button, no two-finger scrolling, and the touchpad is way too sensitive).

Unlike everyone, I can't get the XML hal policy configuration file thing to work (following the instructions over at [https://wiki.ubuntu.com/MacBook/SantaRosa](https://wiki.ubuntu.com/MacBook/SantaRosa)). Does anyone else have this problem?
make sure there are no touchpad options defined in your xorg.conf as it conflicts.

---

### Post by emptiness on 2008-11-06
Honestly I'm really impressed...

Everything seems to be working better:
power consumption and less heat
water effects working in compiz
interface seems to be improved 
cpu usage is down 
sound working with no tweaking
mac buttons working without having to install pommed

haven't tried dvd playback yet...

They even included a nice dark theme so I don't have to configure my desktop colors much :)


Only problem was that from a fresh install grub wouldn't install properly, reinstalling grub from a live cd wouldn't work.I don't understand why since hardy installed and booted no problem...
This may be 'cause I have an ubuntu only box.
I remedied this by using the alternate install cd to upgrade a hardy install.

My desktop is now sweeeet!
Water effects now working, not to mention I finally got electricsheep running as my desktop background(not really related,but I'm stoked I finally got it to work)

I don't even miss os x in the least now...

forgot to mention I have a white 3,1 macbook

---

### Post by vegetali on 2008-11-07
good for you, people. Intrepid seems to deliver better perfomance on my macbook, but multitouch tricks do not work anymore. any intrepid specific tip for this (the hardy tweaks do not work)? 

Also, I have minor problems with the net, but this is related to some custom settings that used to work with hardy, and give some troubles now.

thanks

---

### Post by cyberdork33 on 2008-11-07
> **emptiness said:**
> Only problem was that from a fresh install grub wouldn't install properly, reinstalling grub from a live cd wouldn't work.I don't understand why since hardy installed and booted no problem...
This may be 'cause I have an ubuntu only box.
I remedied this by using the alternate install cd to upgrade a hardy install. There is a bug int he grub installer that seems to break the MBR of Macs (sometimes). If you install grub to the root partition of you linux system, you should not get this problem.

---

### Post by cyberdork33 on 2008-11-07
> **vegetali said:**
> good for you, people. Intrepid seems to deliver better perfomance on my macbook, but multitouch tricks do not work anymore. any intrepid specific tip for this (the hardy tweaks do not work)? 
Please check the "Before you Post" link in my signature to properly identify your mac hardware and version and find information regarding setting up your MacBook properly. You might also want to check here:
[https://wiki.ubuntu.com/MactelSupportTeam/PPA](https://wiki.ubuntu.com/MactelSupportTeam/PPA)

---

### Post by emptiness on 2008-11-07
Thanks for that info cyberdork33 :)
I have just noticed a couple of problems,namely the eject button doesn't work(not a big deal) and no dvd playback yet.I'll look around though to make sure I'm installing things properly for dvd playback...

Still it is beautiful thing!

---

### Post by dark_harmonics on 2008-11-08
> **emptiness said:**
> Honestly I'm really impressed...

Everything seems to be working better:
power consumption and less heat
water effects working in compiz
interface seems to be improved 
cpu usage is down 
sound working with no tweaking
mac buttons working without having to install pommed

haven't tried dvd playback yet...

They even included a nice dark theme so I don't have to configure my desktop colors much :)


Only problem was that from a fresh install grub wouldn't install properly, reinstalling grub from a live cd wouldn't work.I don't understand why since hardy installed and booted no problem...
This may be 'cause I have an ubuntu only box.
I remedied this by using the alternate install cd to upgrade a hardy install.

My desktop is now sweeeet!
Water effects now working, not to mention I finally got electricsheep running as my desktop background(not really related,but I'm stoked I finally got it to work)

I don't even miss os x in the least now...

forgot to mention I have a white 3,1 macbook

You should try out cairo-dock for a cool mac-like dock. For DVD playback you will need medibuntu (google will pull it up) and probably regionset. I had to use regionset (sudo apt-get install regionset) to get DVD playback on my 3rd gen macbook pro to work. 

I do have a problem that i cant figure out: When i connect to a wireless network at my work that has WPA security, my computer instantly freezes up! No keystrokes work no mouse nothing!

ARGH!

---

### Post by rickbsgu on 2008-11-08
OP, here.

Interesting such varied experiences.  I figured out my multiple-selection problem (updated in original post) - essentially syndaemon was the problem.

Now, everything is working just fine.

I'm not missing OS X on this machine, at all (but it is my second machine...)

rickb

---

### Post by milk~tea on 2008-11-08
I installed Intrepid a few days ago (my first experience with linux) and am loving it!  (maybe even more than OSX)

i had to make a few tweaks though like: 

re-enable the caps lock light
change the touchpad config
change isight firmware
etc

---

