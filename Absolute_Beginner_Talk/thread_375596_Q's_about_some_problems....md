---
title: "Q's about some problems..."
date: 2007-03-03
forum: Absolute Beginner Talk
---

### Post by PsycoGeek on 2007-03-03
Greetings everyone!  Let me start off saying that this is my first foray into Linux Land, and so far I'm liking what I am seeing.  I've been watching Linux since about '97 and have been waiting for it to mature to the point that it could really compete with M$.

I've been toying around with the 6.10 live CD and was wowed by the fact that the whole system seems to work pretty well.  Sound, video, network/internet, and even my Xerox/Tektronix 860DP worked with the 850 built in driver with little difficulty.  But I do have a few questions regarding some problems...

1.  I can access my Win2K server just fine, but I can't play any audio files that are stored there.  They are FLAC format, but what really confuses me is that the same files on my DAP (Digital Audio Player, iAudio/Cowon U3) play just fine when connected via USB.  Why play from the DAP but not from the network?

2.  My Logitech LX7 mouse does not have full functionality.  The "Back" and "Forward"  buttons are selecting whatever the pointer is over when pushed instead of moving backwards or forwards in Firefox.  Anyway to get them working?  Didn't ever try the "Wheel Click" or "Tilt Wheel" functions, but how about them anyway?

3.  On the same note of functionality, I also have a Logitech Medis Keyboard Elite (PS2 connected).  The volume control works.  Any chance of getting the other special keys working, like the media and internet keys, or the dual mode function keys?

4.  The desktop in Ubuntu is fuzzy on my Radeon X1900XT.  Without installing it to a hard drive I have no way of testing if the problem is driver related, or if I should put an nVidia card back in.  The scrolling is also very jerky (which I attribute to the system being booted from a CD and not a hard drive).  The Live CD is just fine on my son's PC with an nVidia 6800GT... nice and crisp text and images.  Only difference in monitors is his is 1280x1024, and mine is 1600x1200.  Any suggestions?

Thank you in advance for any advice, suggestions, or answers you can provide.

---

### Post by mrmonday on 2007-03-04
I can half answer two questions... I am not sure if they work on the live CD... I just went straight for the install:) Very pleased - Maybe if you are hovering over windows you wait for Feisty? from what I have heard/seen it is very good so far, it may also solve a couple of your problems:)

For Q3 try System> Preferences> Keyboard Shortcuts - Find the function you want click it and press your key- some of my keys don't work:( hopefully they will for you

For Q4 under System> Preferences> Screen Resolution - Is you resolution right? Try that. If not what does:
```
glxinfo | grep rendering
``` 
give in the terminal (Applications> Accessories> Terminal) - I know a solution for if it is installed... I don't think it will work on the live CD though:(

Hope it works for you:D

---

### Post by PsycoGeek on 2007-03-04
Q4... resolution is set at 1600x1200.  I tried glxinfo | grep rendering and it isn't installed.

I will try the function setting for the keyboard too.  Thank you.

---

### Post by PsycoGeek on 2007-03-06
Q4 SOLVED...  I installed the driver from ATI (ati-driver-installer-8.34.8-x86.x86_64.run).  The desktop is crystal clear now.  

Still working on other problems....

---

### Post by PsycoGeek on 2007-03-06
Ran into another problem with Q4...  the ATI driver is working @ 1600x1200/60hz, but I get corruption on the desktop in the lower right corner.  I have the clock turned on.  The corruption is a black block with coloured pixels randomly distributed in it.  I also get a block of pixels to the lower right of the cursor that move with it.  There is also a "shadow" of any application that I open in the lower left of the sereen, above the "Hide Windows" button and lower bar (task bar?).

When I change resolution to 1280x1024 everything seems to display OK.  Any ideas on the problem?

Almost forgot...  Thanks mrmonday.  I got most of the buttons working for multimedia and internet, now I have to work on the application function buttons.

---

### Post by PsycoGeek on 2007-03-06
Q4 screen corruption issues...  Looks like it is a problem @ 1600x1200 only.  :(

---

