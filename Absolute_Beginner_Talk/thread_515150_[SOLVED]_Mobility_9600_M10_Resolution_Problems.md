---
title: "[SOLVED] Mobility 9600 M10 Resolution Problems"
date: 2007-08-01
forum: Absolute Beginner Talk
---

### Post by MacMonster on 2007-08-01
Hi All,

Just a quick introduction to myself and my skill levels. I am an ex Windows user in the middle of a switch to Mac (Collecting Funds :) ) and have opted to try out Ubuntu during my transitional period. I have removed all trace of XP from my laptop and am learning about Ubuntu as I go here. I know Little>Nothing about Linux and/or Terminal Commands etc so go easy.

I have installed the latest version of Ubuntu today and have a few issues with some of my hardware. The one I want to concentrate on 1st is my screen resolution. My laptop has a Mobility 9600 (M10) graphics card that should run at 1400x1050. However after installing I was only able to choose 800x600 or 640x480. I have done some reading through these forums and had a bash at [https://help.ubuntu.com/community/BinaryDriverHowto/ATI]("https://help.ubuntu.com/community/BinaryDriverHowto/ATI") using the "Install from Ubuntu repositories (easier)" guidelines. However I am only able to choose 1024x768 or 800x600 or 640x480 and cannot enable System>Preferences>Desktop Effects getting the message "The Composite extension is not available". My final goal is to run at 1400x1050 and use Desktop Effects.

All help and/or tutoring is greatly appreciated.

---

### Post by Rocket2DMn on 2007-08-01
Screen resolution problems are quite common, have you run the following command (in terminal):
```
sudo dpkg-reconfigure xserver-xorg
```
You use TAB to move around and SPACEBAR to select/enable when appropriate.  When you get to the resolution page, you should select your monitor's max resolution and everything less.
I tried out fglrx on my Radeon Mobility 9000, but when I installed Beryl, it had me use the open source driver.  If you want to use the open source driver now that you have the restricted one installed, you can follow the guide on the first page of the Beryl setup guide I used which shows you how to switch back to the open source driver.  I also use 1400x1050 resolution.
[http://www.howtoforge.com/ubuntu_feisty_beryl_ati_radeon](http://www.howtoforge.com/ubuntu_feisty_beryl_ati_radeon)
PS: Beryl has now been replaced by Compiz Fusion.

After you run that configuration, restart the X-server with CTRL+ALT+BACKSPACE.  You should now be able to select the correct resolution from going to System->Administration->Screen Resolution

---

### Post by MacMonster on 2007-08-01
Worked a treat! You Legend :)

I must admit a lot of that "sudo dpkg-reconfigure xserver-xorg" process was quite baffling to me and i'm not sure if I did it right though. When i typed it in to Terminal I got a message saying that the window was not big enough and so all the questions showed up as text within terminal. I'm not sure if I entered the right thing in some of the questions especially about the KB & Mouse etc...

Could I have done damage in other areas by not understanding some of that?

---

### Post by Rocket2DMn on 2007-08-01
If everything works, you're probably fine.  Most of it you *can* ENTER your way through, but it's always best to know what's going on and play it safe.
The questions ARE supposed to be text based.  Doesn't make much sense to provide a CLI (command line interface) method to reconfigure the X server when X doesn't work - sometimes people can't get to the GUI at all.
Glad it worked.

---

### Post by MacMonster on 2007-08-01
Thanks Again,

Any advice on whether I should try Beryl or Compiz Fusion? Do you use either of these to good effect at the correct resolution?

---

### Post by Rocket2DMn on 2007-08-01
I use Beryl and everything works fine.  Your card falls under "Experimental 3D Acceleration" with the guide I gave above.  You might as well try Compiz Fusion since it has replaced Beryl and will be receiving regular updates.  I don't have any guides for you based on personal experience because I haven't used CF, but if you ran a google search for something like "ubuntu compiz fusion ati" you might come up with some results.  CF is pretty new, so there is likely less out there for it, but it should be remarkably similar to setting up Beryl.

---

### Post by MacMonster on 2007-08-01
Cheers, I think I will look into getting my Intel Wireless 2200BG working 1st.

Post marked as SOLVED.

---

### Post by Rocket2DMn on 2007-08-01
I had no problems getting my 2200BG to work, though you might have to enable Roaming even when you input information for your wireless network.  Good luck.

---

### Post by MacMonster on 2007-08-01
It may be working then it that case, it's just that when I click the little network icon in the top right there are no networks listed under wireless networks? I am using a netgear DG834G router but can't remember what kind of protection I have set up on there (e.g. WEP, WPA etc...)

---

### Post by Rocket2DMn on 2007-08-01
Home wireless routers have a web based interface for changing settings - you can look there from a computer wired in or already connected to the wireless.  I suggest using WEP encryption, WPA can be a little more difficult to setup and isn't really necessary.

---

