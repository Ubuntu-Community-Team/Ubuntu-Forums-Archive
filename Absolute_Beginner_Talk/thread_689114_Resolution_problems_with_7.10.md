---
title: "Resolution problems with 7.10"
date: 2008-02-06
forum: Absolute Beginner Talk
---

### Post by Northstorm1x on 2008-02-06
Hello everyone this is my first post. 
I have been running a triple boot system now for six months using Ubuntu, Windows XP pro and Vista Home Premium.
I decided to upgrade Ubuntu  to version 7.10 from 7.4 now it wont run at all its telling me my monitor    resolution  is set to low at a weird number like 774x? No matter what I set it at with the F4 command. 
Has anyone got an Idea  how to fix this or is this a common bug with 7.10. The Live-cd doesn't work it said the same thing. 

Here are my system specs 

Athlon64 3800+
Nforce motherboard
320HDD with XP, Ubuntu and Vista  
3GB DDR2 5300 memory 
Radeon HD 2400 PRO with 256MB DDR2  
and A flat tube CRT 17&#8221; monitor (someday I,ll get a LCD)

I would like to start using Linux more, up till now I was just using Ubuntu on line and windows for my games. I was thinking of switching to Ultimate Ubuntu gamer edition but I am afraid it wont run ether.

Thank you for any help.  :frown:

---

### Post by Trail on 2008-02-06
> **Northstorm1x said:**
> Ultimate Ubuntu gamer edition

... the what?! :confused:

I only know of one possible way that might help, but don't use it unless you have no better ideas. Wait for someone more knowledgeable to help :) This might work if you used modules for a graphics card before the update, and they don't match the current kernel version.

After ubuntu stop loading, press ctrl-alt-f2 to switch to a terminal screen. Login. Run the command
```
sudo /etc/init.d/gdm stop
```
to stop the graphics screen. Then run 
```
sudo dpkg-reconfigure xserver-xorg
```
This will start a guide of (sort of) reconfiguring among other things your graphics card support. It should be safe to take most defaults (make a not of two things: if you use an nvidia card and if there is both an "nv" and "nvidia" at the first selection, pick "nv", and don't select a resolution your monitor does not support).
Then, the easiest way is too reboot (sudo reboot) and see if it worked.

---

### Post by Bush_Roo on 2008-02-06
No need to worry about ultimate gamer edition of Ubuntu (I think that it is of out of date anyway??). When you set up the repositories, you can download all the games that any other (Linux) distro could eva have!

---

### Post by Northstorm1x on 2008-02-06
(sudo reboot) 

I Did USE SUDO REBOOT STILL SAME PROB  :confused:

---

### Post by Northstorm1x on 2008-02-06
RE:No need to worry about ultimate gamer edition of Ubuntu (I think that it is of out of date anyway??). When you set up the repositories, you can download all the games that any other (Linux) distro could eva have!


THANK THATS GOOD TO KNOW:guitar:

---

### Post by forestpixie on 2008-02-06
so reconfiguring x has made no difference - or did you not do it

if you did and you still have no luck try running it again and using vesa as the driver

hopefully that will get you into your system and you can then either use the restrictyed driver manager or get [envy]("http://albertomilone.com/nvidia_scripts1.html")

if you get a kernel updtae be aware that you might need to reinstall the driver if you use envy (or at least that's my understanding)

---

### Post by GSF1200S on 2008-02-06
> **Northstorm1x said:**
> (sudo reboot) 

I Did USE SUDO REBOOT STILL SAME PROB  :confused:

Get to the command line. Im assuming the desktop environment, or X, fails to load. When you get an error message, you should be able to login at the command line (black screen with text). After logging in and putting in your password, type:

```
sudo dpkg-reconfigure -phigh xserver-xorg
```

select the vesa driver, and select whatever resolution you want for your monitor. Then, restart X:

```
sudo /etc/init.d/gdm restart
```

This should get you in a GUI where you can then proceed to install the actual 3d drivers if you want. You can do this 1 of 4 ways:

1) Restricted Drivers Manager- click the check box next to your video card...
2) Synaptic (search for ati or nvidia drivers, and run config to update the xorg.conf)
3) Manual- download from the ati or nvidia website and install them from the command line (easy)
4) Envy- a great app that works wonders for many people.

Good Luck!

---

### Post by bwtranch on 2008-02-06
The best place to get NVIDIA drvers is at their website [www.nvidia.com](www.nvidia.com) In my opinion Envy is garbage and has screwed up more of my systems than I can count. I know the flaw in the code, but I'm not telling, until I'm sure. But, I feel safe in saying, it's a bad hack. Go to the OEM website, they have a shell program that works. Nuf said.

---

### Post by overdrank on 2008-02-06
> **bwtranch said:**
> The best place to get NVIDIA drvers is at their website [www.nvidia.com](www.nvidia.com) In my opinion Envy is garbage and has screwed up more of my systems than I can count. I know the flaw in the code, but I'm not telling, until I'm sure. But, I feel safe in saying, it's a bad hack. Go to the OEM website, they have a shell program that works. Nuf said.

Hi and I believe the op is speaking of ATI graphics 
Radeon HD 2400 PRO with 256MB DDR2 
 I am sorry that Envy did not work for you but it has helped many including me. If you have issues I am sure  tseliot would be glad to hear.
[http://ubuntuforums.org/member.php?u=19388](http://ubuntuforums.org/member.php?u=19388)

---

### Post by marufaberlin on 2008-02-06
By the way: did you know that writing with CapsLock on means your're SHOUTING?

---

### Post by Northstorm1x on 2008-02-08
Sorry about yelling (with the caps on).

---

### Post by overdrank on 2008-02-08
> **Northstorm1x said:**
> re :Hi and I believe the op is speaking of ATI graphics 
Radeon HD 2400 PRO with 256MB DDR2 
I am sorry that Envy did not work for you but it has helped many including me. If you have issues I am sure tseliot would be glad to hear.
[http://ubuntuforums.org/member.php?u=19388](http://ubuntuforums.org/member.php?u=19388)

yes My GPU is from ATI.

thank you
I have tried all your suggestions,  so far nothings working  :(

Hi and if I may ask, How did you upgrade. Through the update manager or a clean install of 7.10?

---

### Post by Northstorm1x on 2008-02-08
Thank you all I have tried what you  all have said to do,  but so far no luck.
Yes the video card is a ATI card, is their a known problem with Ubuntu and the  ATI 2000 series cards?

I really love Linux and rather use it than Windows Vista  on my system.

---

### Post by Northstorm1x on 2008-02-08
RE: 
Hi and if I may ask, How did you upgrade. Through the update manager or a clean install of 7.10?

I had to do a clean install because I only have a 56k dial-up connection.

---

### Post by overdrank on 2008-02-08
> **Northstorm1x said:**
> RE: 
Hi and if I may ask, How did you upgrade. Through the update manager or a clean install of 7.10?

I had to do a clean install because I only have a 56k dial-up connection.

Hi and you have tried Envy
[http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)

---

### Post by Northstorm1x on 2008-02-08
Yes it didn't work I think its cuz I have a ATI card.

---

### Post by Northstorm1x on 2008-02-08
> **overdrank said:**
> Hi and you have tried Envy
[http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)

is their one for ATI video cards?

---

### Post by overdrank on 2008-02-08
> **Northstorm1x said:**
> is their one for ATI video cards?

Yes Envy works for ati and nvidia. You may want to look at the link I posted earlier.

---

### Post by Northstorm1x on 2008-02-08
Here is more information I hope it helps .


This  is what I keep getting:

the display sever has been shut down 6 times in the last 90 seconds   it is likely something bad is going on, waiting 2 minutes before trying again on display 0

my resolution gets set to
720x400
31.khz
32.v 70 hz

no matter what I set it to.

Hope this helps.

---

### Post by Northstorm1x on 2008-02-08
getting Envy now, will try 
thanks

---

### Post by jeyaganesh on 2008-02-08
GSF, thanks for your brilliant post. It worked for me.

---

### Post by Northstorm1x on 2008-02-09
I am going to reinstall 7.10 tonight and retry Envy, something happened when I tried it and I can't start  Ubuntu at all,
 I already backed everything up  so I'll do a fresh install tonight when I get back.

Thank you once again for all the help I am receiving and I will not give up If it takes me to the release of Ubuntu 8 to get it right.

---

### Post by Northstorm1x on 2008-02-18
Tried everything and still no luck, I'll keep using 7.4 for now

---

### Post by Northstorm1x on 2008-02-18
Thank you everyone for your help.


Ubuntu still rocks!

---

