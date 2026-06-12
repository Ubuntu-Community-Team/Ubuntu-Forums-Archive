---
title: "any tablet drivers available for Gateway cx2610?"
date: 2006-03-18
forum: Absolute Beginner Talk
---

### Post by LaBOOdha on 2006-03-18
am looking to find drivers or what I need to get the convertible tablet portion of my Gateway CX2610 to work. How do I solve this? wait? Pen doesn't work ...screen does not have reorientation ablility. thanks.

---

### Post by Pragmatist on 2006-03-18
Well, try as I might, I couldn't find much--even at gateway's site, about your tablet/pen situation.  The ubuntu wiki has something for wacom-type tablets and pens. However, I wouldn't do any of that unless I knew it applied to my device.

[https://wiki.ubuntu.com/WacomPenPartnerSerial?highlight=%28pen%29](https://wiki.ubuntu.com/WacomPenPartnerSerial?highlight=%28pen%29)
[http://linuxwacom.sourceforge.net/](http://linuxwacom.sourceforge.net/)

---

### Post by cx2610 on 2006-04-01
I have a cx2610 too. I haven't found much on the tablet side and I am running Breezy on it (dual boot with tabletxp). I do have to tell you that if you do a little digging, our cx2610 pen is not made by Wacom but I believe it is made by Finepoint (not completely sure because I read this quite a while ago!). Who knows what Finepoint is and I am so swamped with school work that I didn't do anymore research on it. Getting my tablet to work with linux is a designated summer task...

If you get anything to work with the tablet in linux, please do let me know. You are the only person in the world that I know that also has a cx2610 with linux on it! If I figure anything out, I will let you know.

Cheers,

Reehan

---

### Post by one_stinky_bum on 2006-08-15
hello folks,

I have an M280, and yes, the digitizer is made by Finepoint Innovations. I haven't got it to work - have you guys made any progress? So far I can get the pointer to move around erratically on the screen when I move the pen around. I have tried to calibrate it but I've been told by the guy at Linuxslate [http://www.linuxslate.org/software.html](http://www.linuxslate.org/software.html) that the new tablets may be encoding the pressure sensitivity data with the position data, that's why the old drivers don't work. 

I'm stuck, and on the verge of switching back or buying a new tablet. :(
And I've got all this compiz goodness going.

Edit:I found out from Wikipedia that it (M280, CX200/210, CX2600/2700 etc) uses the Finepoint MP-800 digitizer. Hopefully this would help if someone can be of assistance.

---

### Post by one_stinky_bum on 2006-09-20
Update: A guy from emperor linux said they could perform a "depot install" that would guarantee a fully functional tablet, but that would run you $500-$600.

---

### Post by qumak on 2006-09-30
hey it seems there hasn't been much action in this thread for a while, but if any of you are still toiling with this computer and linux i'd like to hear from you, i have the cx2610 running gentoo (though sometimes when gentoo is pissing me off, usually having to do with how it handles wireless, i'll boot up an ubuntu livecd ;)) and i too have had these problems.  However, i have gotten minimal recognition of the pen with the fpit driver in xorg-7 after much trial and error with what started as essentially random numbers that i stuck in my xorg.conf to attempt to calibrate the cursor.  Editing my xorg.conf and restarting X 5 million times was not fun, but here are my values, they should probably work for you too!


```

Section "InputDevice"
  Identifier  "Tablet"
  Driver      "fpit"
  Option      "Device"           "/dev/ttyS0"
  Option      "AlwaysCore"       "on"
  Option      "InvertY"
  Option      "MaximumXPosition" "12550"
  Option      "MaximumYPosition" "7650"
  Option      "MinimumXPosition" "400"
  Option      "MinimumYPosition" "400"
  Option      "SendCoreEvents"
EndSection
```

Now, Before you get too excited, this calibration is not perfect, i got really tired of fine tuning so the cursor is a couple millimeters off from the stylus at some points in the screen, but it's a hell of a lot better than the random flashing by everywhere on the screen uncontrollably that i was getting before.  Also, i haven't figured out how to get any sort of clicking recognition, tapping the stylus and clicking the button on the stylus do nothing, which makes moving the cursor around the screen in most applications rather useless.  the only thing i have really used it with so far is [Dasher]("http://www.inference.phy.cam.ac.uk/dasher/"), which is an awesome input method.  You could probably use it in some drawing program or something too i'd expect, but you may need to do all the clicking with the mousepad on the laptop, which defeats the purpose if you wanted to flip the screen over.

Baby steps though :)

Please if you have this laptop and are trying to get things working email me and let me know how it's coming along.  I haven't looked recently into screen orientation issues but I remember that the new version of the i810 driver was supposed to support it, and that was a while ago so maybe it's out?  hopefully i'll have the time to look into this more soon.

**EDIT:**  I posted this a few minutes ago, updated my i810 driver to version 1.6.5 (i was running 1.6.0 and it wasn't working) in the xorg-7.1 tree and screen rotation works great.  only caveat being that when i rotate the screen, the pen driver doesn't know how to rotate right, so it's like going left brings you right, up brings you down, for instance, when the screen is flipped upside down.  so there's some more good news though!!

--qumak

---

### Post by one_stinky_bum on 2006-09-30
I can confirm that "xrandr -o invert" works pretty well here in edgy with xorg-7.1. I'm just about to try your xorg.conf. I'll let you know how it pans out on my M280.

**Edit:** there's a little bug in the xrandr invert mode - type text and it doesn't appear till you hit enter. :confused: 
I still get a jumpy cursor on my M280, with the config above. Did you do any special setserial stuff?

**[SIZE="3"]Edit2:[/SIZE]** I get the following output from dmesg, hopefully it would help in solving this problem:
```
serial18250: ttyS0 at I/O 0x3f8 (irq=4) is a 16550A
ttyS0: LSR safety check engaged.
```

---

### Post by qumak on 2006-10-02
yes sorry, i forgot to mention that upon boot i have setserial invoked with the following argument:
```
/dev/ttyS0 port 0x03F8 irq 4 baud_base 38400
```

hope that can be helpful

--qumak

---

### Post by one_stinky_bum on 2006-10-02
I'm told you have to run setserial before gdm starts... how do you get that done?

---

### Post by qumak on 2006-10-02
i don't know exactly where to tell you to go in ubuntu, but you should have an init service called serial or setserial, and you just need to make sure that will start up on boot and put those arguments in the config file (/etc/serial.conf maybe).  If you have none of that, maybe you have an /etc/rc.local, which you could just append the whole setserial command with argument to.

--qumak

---

### Post by one_stinky_bum on 2006-10-02
Got it. It's working now. I had an old setserial script that I updated to the following: 
```
#!/bin/sh
/bin/setserial /dev/ttyS0 autoconfig
/bin/setserial /dev/ttyS0 port 0x03F8 irq 4 baud_base 38400

```

---

### Post by qumak on 2006-10-02
awesome.. how is the calibration of your pen with my values?  pretty good but off a millimeter or two sometimes?  that's what i have.  and i assume you can't use the pen to click or anything like that also?

--qumak

---

### Post by one_stinky_bum on 2006-10-02
Yep, the calibration is great. I would call it perfect, but maybe that's just because I was living without a tablet PC for a few weeks now. :)

I'm going to see if I can get the clicking to work. "man fpit" isn't too helpful. Do you know what tool I can use to capture click events? If we knew what keycode it sends for a click, we could probably hack something up.

---

### Post by one_stinky_bum on 2006-10-13
Any progress with the clicking?

---

### Post by iamsthitha on 2006-10-15
Hey,

This thread helped me out a lot and I was able to get the stylus working completely.

To get the clicking, you need to change some of the source code.

grab the fpit module code from [xorg]("http://ftp.x.org/pub/X11R7.0/src/driver/xf86-input-fpit-X11R7.0-1.0.0.5.tar.gz") and edit xf86Fpit.c
comment out line 285 which looks like:
if (!prox) buttons=0;

Compile it and install it and the clicking should work now.

Good luck,
Sthitha

---

### Post by one_stinky_bum on 2006-10-15
Could you please make a .deb? I believe if it compiles well for you, you can say "make checkinstall" instead of "sudo make install" and you should get a .deb file. My "./configure" is complaining about no xserver-xorg and xproto package.

I'll host the .deb if you want.

---

### Post by iamsthitha on 2006-10-15
I dont use ubuntu or any debian derivative, and I dont know how to make debs.
I just found this thread googling.
But from the looks of things, all you're missing are some devel packages.
Once you've got the right packages, it should compile instantly.

--Sthitha

---

### Post by one_stinky_bum on 2006-10-16
Yaaay! I can confirm that left click works. Make sure you have xserver-xorg-dev installed.

Sthitha, did you also get right click to work? I'm working on a .deb... I'll release it when I get rightclicking to work.

---

### Post by iamsthitha on 2006-10-18
That fix should make the side stylus button send a middle click.
To change this to a right click, I added this in my .xinitrc:
xsetpointer TOUCHSCREEN
xmodmap -e "pointer = 1 3 2"

Now, what'd be nice is if the stylus would work properly when I change orientation (xrandr -o).

--Sthitha

---

### Post by one_stinky_bum on 2006-10-18
Fantastic. If anyone here is looking for a MS Journal replacement, I recommend Xournal. The only annoying thing is that the XInput is very jittery. It would be nice if the fpit driver averaged over a few samples when the pen is relatively stable.

---

### Post by jaiwithani on 2006-10-20
Hello,

I have a Gateway CX200S, and I've been trying to get my tablet to work for months.

Following the directions on this thread I got fpit installed from source and working properly, added the appropriate lines to /etc/X11/xorg.conf, and to /etc/rc.local. Aaaand...the pen won't work. I get a lot of output from cat /dev/ttyS0, but it doesn't actually function at all. What can I doooooo?

Edit: Apparently I merely fscked something up on my own. I started over, and it works amazingly now. Hooray! Thank you!

---

### Post by one_stinky_bum on 2006-10-20
Are you using the latest X.org? It's working here on my M280 with Xorg 7.1.1

---

### Post by jambes on 2006-10-21
> **jaiwithani said:**
> Hello,

I have a Gateway CX200S, and I've been trying to get my tablet to work for months.

Following the directions on this thread I got fpit installed from source and working properly, added the appropriate lines to /etc/X11/xorg.conf, and to /etc/rc.local. Aaaand...the pen won't work. I get a lot of output from cat /dev/ttyS0, but it doesn't actually function at all. What can I doooooo?

Did you put this line in the xorg.conf, in the "ServerLayout" section?
InputDevice     "tablet"

I also have a CX200S, and was having the same problem, until I added that line. However, now the cursor just jumps around crazy like, even with the values from the other post. I tried adjusting them, but no luck.

---

### Post by jaiwithani on 2006-10-23
Just did that - still no luck.

I think I am doing something quite wrong.

---

### Post by chadraytay on 2006-11-02
I've got the cx2618, after adding the serial config and the xorg settings the pen tracking is absolutely perfect, no jitter, no jump, flawless. :cool: 

However, commenting out a line didn't get me any clicking. ](*,) 

Any ideas?

I'm using sabayon. (it's gentoo installed ready to use from a cd)
:-| Thanks I hope... :-|

---

### Post by one_stinky_bum on 2006-11-02
I have found out that I have to re-install the modified package anytime I update the xserver packages. These files worked for me, but YMMV.

The files you need are "fpit_drv.so" and "fpit_drv.la". Unzip them and place them in your "xorg/modules/input" directory, wherever that may be on your system. Example: ```
/usr/lib/xorg/modules/input/fpit_drv.so
```

This is compiled against X11 r7.0. Let me know if it works.

---

### Post by chadraytay on 2006-11-02
OMG... I fricken love you. It works... It works it works it works it works it works it works it works... I CAN CLICK AGAIN!!! YEAH!!!!
:KS :KS :KS :KS :KS :KS  

Can ya tell I'm a little more than happy? hehe

No more windows no more windows, wheeeeeeeeeeeeeeeee!


/me worships you as god. ;) 

Thank you for the files :) Time to reformat, wipe everything, and go pure linux!

---

### Post by chadraytay on 2006-11-04
Well, rotation seems simple enough... A Option "Rotate" "CCW" in both the mouse and video section of xorg makes that work just fine.  Don't suppose there's a way to link the mouse to the video rotate for the resize and rotate program in kde?

Oh well, not like restarting x is that hard :-D

---

### Post by one_stinky_bum on 2006-11-04
Yeah, that has worked for a long time, even before edgy. However, restarting X, opening up all the windows you had open, shutting down X, restarting X, re-opening the windows you had open....
you get the drift. It's not convenient.

So I'm guessing your right click is also working, right?

---

### Post by chadraytay on 2006-11-05
Yeah, everything seems to be working ok now. :)

---

### Post by gsagers on 2006-11-07
Thanks from a Gentoo user for a great thread, and a completely working pen on an M285E!  Just a couple of notes, if you want to have both mouse and touchscreen working, so that you can work in laptop mode, then swivel the screen for tablet w/o having to restart X, use "xsetpointer TouchPad" in addition to the "xsetpointer TOUCHSCREEN".  (Of course, you can always use xsetpointer within your X session, too).  If you want to source the xsetpointer an xmodmap lines via a KDM login, use ~/.xprofile rather than ~/.xinitrc.

Quick question, my pen seems very sensitive, and thanks to my heavy-handed approach, I get extra clicks when moving the pen around, and it's tough to hold it still enough for a right-click.  Is there some sort of "debouncer" like a keyboard repeat rate that can be set with xmodmap or another program?

---

### Post by nosbig on 2006-12-14
Hey gang - I just got meself a fancy new Gateway CX210X.  So far, love it - but have not yet gotten the Tablet/Pen working with my Linux Distro (okay, I'm sorry, but I'm running FC6 on it right now...).  However, I did want to point out, that I found the following LinuxQuestions post on getting FinePoint tablets working on Linux.  The Gateway's seem to use the Finepoint OEM tablet panel. 

[http://www.linuxquestions.org/questions/showthread.php?t=497879](http://www.linuxquestions.org/questions/showthread.php?t=497879) 

I think this is essentially a rehash of most of the information found in this thread already.   But, I thought I'd link to it from here, if it has any other tips or pointers that may have been missed, and also just FWIW.

I'll post back here, after going through this, and let you all know if it worked.  I believe that the tablet/pen portion is relatively variant agnostic, so what I do on FC6 should mostly apply with Ubuntu as well... 

If anyone else reading this thread had gotten their Gateway tablet/pen working ... your thoughts and experiences would be greatly appreciated.  Thanks!

++nosbig

---

### Post by chadraytay on 2006-12-14
Um, yeah, that's just a copy of this condensed for the rest of the world. I dropped it onto linuxquestions so people could find it. Not many look on ubuntuforums for that kind of information.

---

### Post by kfhughes on 2006-12-19
> **gsagers said:**
> Thanks from a Gentoo user for a great thread, and a completely working pen on an M285E! 

Can you give a summary of what you has to do on the M285E?  I'm trying to get it working on my M285E but on boot-up /dev/ttyS0 isn't detected (nothing in dmesg).

---

### Post by cabose on 2006-12-24
hey, iamstitha, if you haven't figured out how to rotate the stylus plane, i have a script that works for the wacom driver. I found it online, and edited it a little.  If you are using a different driver, I am sure you can figure it out.  I hope the commenting is okay.

---

### Post by DNeoMatrix on 2006-12-26
Hello all, been trying to switch over to linux on my CX210X for a while. Finally got the nerve to do it between semesters. I have the pointer working well, but i'm missing out on the clicks. Any help would be appreciated. I'm running SUSE 10.1 -> Gnome. Downloading 10.2 at the moment. Apparantly I can't recompile the code for xf86Fpit.c because i'm missing some stuff....  xserver (and can't install that because i'm missing pkg-config) ... and it's all messy. Anything simple? or should i just go with a reinstall at 10.2 and hope that's a little easier? (10.1 has X.org 6.9, but 10.2 has 7 something)

--okay - installed 10.2, now i got clicking and pointing working. Everything works but i gotta couple ... irritations. Screen Buttons, and rotation. I wouldn't mind writing some programs/scripts to do some listening and stuff... but i'm having a hard time finding the info to do this with. Any help?

---

### Post by chadraytay on 2006-12-28
Well, screen buttons may be a problem. At least on my 2618, when I run programs to monitor all keypresses, it shows no key events for the screen buttons. However, oddly enough, the brightness and volume on the 4 way pad still work, they even display a tiny blob in the corner when I use them...](*,)

---

### Post by kingofearth on 2007-01-03
@DNeoMatrix.

I've also got a Gateway cx210x, but I can't get my touch screen to work at all. Catting the serial ports gives me an I/O error, and dmesg | grep tty displays:
```
ttyS0: LSR safety check engaged!
```

Any tips on how I might get it working?

Edit: Nevermind this question I got it working using 0x6a8 for the serial port. Now when ever I touch the screen with the pen the mouse starts moving erraticly around the screen. I used the xorg.conf touch screen InputDevice section from earlier, but it's not working quite right.

---

### Post by Macinkross on 2007-01-14
I managed to get input from the CX210 but, like kingofearth, the cursor just jumps randomly around the screen.  Also, it seems to be generating a mouse click at every jump (very annoying).  Anyone make any progress here?

---

### Post by kingofearth on 2007-01-21
> **Macinkross said:**
> I managed to get input from the CX210 but, like kingofearth, the cursor just jumps randomly around the screen.  Also, it seems to be generating a mouse click at every jump (very annoying).  Anyone make any progress here?

I got help from Meekles over at Linux Questions and I found out the problem was that I didn't have the baud_base set to 38400 in /etc/serial.conf

So to anyone who has the random cursor movement problem on a CX210X, make sure that your serial.conf is this:
```

/dev/ttyS0 uart 16450 port 0x06a8 irq 4 baud_base 38400

```

---

### Post by will_tk on 2007-06-04
Hey Guys

I'm new on the forum...
had ubuntu 7.04 for fe weeks now on my CX210X and messed up my system by trying 
several tips to get my stylus to work .. but NO LUCK
if any one was able to get their stylus to work on their system... please drop me a link
((( absolut beginer)))

thanks

---

### Post by jrcoder on 2007-06-09
Same problem here with my cx210x.  Anybody know where the setserial.conf file is?  Absolute newbie.

Edit: Oops I guess it helps to have the setserial pkg installed!

---

### Post by chadraytay on 2007-06-09
Ok, i'm actually trying to use ubuntu this time.

Got the latest dvd edition installed. Installed the packing building packages and got the fpit source from apt-get. Patched it with the 3 patches that are available to enable rotation and clicking. And compiled.

Now when I "sudo insmod fpit_drv"
 
I only get error inserting, -1 invalid module format.

Eh?

---

### Post by siraf on 2007-06-15
> **iamsthitha said:**
> Hey,

This thread helped me out a lot and I was able to get the stylus working completely.

To get the clicking, you need to change some of the source code.

grab the fpit module code from [xorg]("http://ftp.x.org/pub/X11R7.0/src/driver/xf86-input-fpit-X11R7.0-1.0.0.5.tar.gz") and edit xf86Fpit.c
comment out line 285 which looks like:
if (!prox) buttons=0;

Compile it and install it and the clicking should work now.

Good luck,
Sthitha

Here's a deb for later viewers, though i still can't get clicking to work :(

---

### Post by Ryoojin83 on 2007-06-25
Alright.
I followed the guide and the pen tracks perfectly and the left click is great.
My only problem is my side button is still a 'middle click' instead of the 'right click'
I have the 

xsetpointer TOUCHSCREEN
xmodmap -e "pointer = 1 3 2"

addition in my ~/.xinitrc file.

Do you know another way to make the right click work?

I was also confused on how to get the screen to rotate.  
Just add

option "Rotate" "CCW" 

to two sections?  what do I type to make it rotate? 
Also, was anyone able to get the table buttons working for rotate?  
Thanks

EDIT:  Forgot to mention I have the ATi x1400... do the fglrx drivers even support rotation?  Can't find info.. :-(

---

### Post by silverballer47 on 2007-07-08
I too have issues getting the .xinitrc file working. Ubuntu does not seem to use it to change the right click settings on the pen. Would anyone be able to post their entire .xinitrc?

Thanks!

---

### Post by Joe_L_Detroit on 2007-07-08
Hello all--

I got the setserial package installed and tried to add the following line to /etc/modutils/setserial to get the pen working correctly:
/dev/ttyS0 port 0x03F8 irq 4 baud_base 38400

Before I added that the pen was erratic but worked.  Now it's not doing anything...

thoughts?

I have the fpit drivers and the DEB file done, and I've made the changes to xorg.conf from the first page

Thanks,
Joe

---

### Post by Noirangel on 2007-07-11
Heyu guys, maybe I'm missing the guide or something. 

But I need a step by step walk through from the install of Unbuntu too compleatly working tablet + Pen. 

I have pretty much no practical knowledge of Unbuntu or Linux, can you guys walk me through this? 

It'd be much appreciated, PM me if you want, thanks.

---

### Post by Joe_L_Detroit on 2007-07-11
Okay, so I've made some progress...

The pen tracks and left-clicks correctly (not the right-click yet, but I'm working on it)

Here's what I did:
changed the setserial package from auto to manual by running dpkg-reconfigure setserial and following the prompts.

added /dev/ttyS0 uart 16450 port 0x3f8 irq 4 baud_base 38400 to /var/lib/setserial/autoserial.conf

created a serial.conf file in /etc (sudo gedit /etc/serial.conf) with the line /dev/ttyS0 uart 16450 port 0x3f8 irq 4 baud_base 38400 in it

rebooted and it works!

Now for the right-click part...

---

### Post by bigoriginal on 2007-08-16
Hello all

I have a cx2608 and am running ubuntu 7.04. I have only gotten so far as the pen flickering around on the screen and what seems to be random clicking. (somewhat hard to tell since its flickering so much) I have followed several forum threads to install the drivers. I have used preconfiged fpit drivers, and compiled them myself (Which certainly was an ordeal). I have edited my xorg.conf as well and installed setserial and entered to necessary commands. Please help, I am an absolute noob. I am a computer enginneering student so I know a bit, but I am completely new to being a linux admin. Thanks again.

---

### Post by stuart.grant on 2007-08-23
Hey everyone thanks for the info. I've quickly managed to get my pen tracking. I'm a bit confused about click and rotation though. Could someone who's gotten it working summarize things for me?

I'm new to Linux so I'm not sure how to recompile/reinstall an input driver. I've got the source code and make the aforementioned change but don't know how to use the make files or install the compiled driver. I did try with the compiles files someone posted but the click was happening constantly.

As for rotation, I can get the screen to rotate but the pen doesn't rotate. I've seen the post about changing the xorg.conf but that would require restarting xserver every time. I've seen something about changing the driver to support this as well but it wasn't clear what needed changing and whether it worked correctly. I've seen a few comments on the screen rotate button as well but nothing that suggested that anyone's got it working

Oh, I'm running Ubuntu 7.04 on a Gateway CX2610.

Thanks in advance for any help,
-Stuart

---

### Post by mtecknology on 2007-09-02
That seems to work excellent. The only thing not working is right click. It doesn't matter much to me if that works or not.

Also... this is on a Gateway M285-E model.

Also2...I don't suggest buying one.

---

### Post by JibberFisch on 2007-09-03
This thread has been a tremendous help getting my pen to work (I'm working on a CX2610).  I did get it working, though the tracking isn't perfect.  I'm not sure if it's a hardware issue or not, because when I ran windows on the computer, the tracking wasn't perfect there either.  I always assumed it was because windows is flawed at a basic level.

However, now that I have it tracking as it had before I installed Feisty, it still has some issues.  When I hold the pen just above the screen, the pen flicks around within about 1 cm of the point directly under the pen, and randomly right clicks.  When I bring the pen into contact with the screen, it stops clicking and tracks.  Sometimes when I'm using Xournal, it draws stray marks from the top left corner of the screen as I begin a stroke.

 I can't quite figure out why it's doing it.  Is there some sort of battery I need to change or a new pen I need to buy, or is this some issue with the configuration I've followed thus far?

Thanks,
Will

p.s. Dumb answers are good; I'm relatively new to Ubuntu.

---

### Post by neil78b on 2007-10-08
It would really be cool if someone showed how to do step #3 in detail, because I did compile it but I didnt do it right because it doesnt show up as changed in my files or something.  I have the fpit_drv.so, but not the fpit_drv.la, but it was there before until I thought I compiled and installed the new.  Anyway this thread has been a great help and I know its old, but I just need a detail explaination of STEP 3.  Thanks

1. Exact file I need to download.
2. Steps to compile it.
3. How to install.
4. How to verify.

THANKS!!!!!

---

### Post by mrnitro on 2007-10-25
> **neil78b said:**
> It would really be cool if someone showed how to do step #3 in detail, because I did compile it but I didnt do it right because it doesnt show up as changed in my files or something.  I have the fpit_drv.so, but not the fpit_drv.la, but it was there before until I thought I compiled and installed the new.  Anyway this thread has been a great help and I know its old, but I just need a detail explaination of STEP 3.  Thanks

1. Exact file I need to download.
2. Steps to compile it.
3. How to install.
4. How to verify.

THANKS!!!!!

I agree with Neil.  If someone could post the exact steps they took to get this working on a CX2610, or equivalent with the finepoint driver, it would be much appreciated!  It is the main thing keeping me from completely converting from windows.  Please help my conversion process.... ;)

---

### Post by Saylient_Dreams on 2007-11-06
> **JibberFisch said:**
> This thread has been a tremendous help getting my pen to work (I'm working on a CX2610).  I did get it working, though the tracking isn't perfect.  I'm not sure if it's a hardware issue or not, because when I ran windows on the computer, the tracking wasn't perfect there either.  I always assumed it was because windows is flawed at a basic level.

However, now that I have it tracking as it had before I installed Feisty, it still has some issues.  When I hold the pen just above the screen, the pen flicks around within about 1 cm of the point directly under the pen, and randomly right clicks.  When I bring the pen into contact with the screen, it stops clicking and tracks.  Sometimes when I'm using Xournal, it draws stray marks from the top left corner of the screen as I begin a stroke.

 I can't quite figure out why it's doing it.  Is there some sort of battery I need to change or a new pen I need to buy, or is this some issue with the configuration I've followed thus far?

Thanks,
Will

p.s. Dumb answers are good; I'm relatively new to Ubuntu.

The clicking is a problem that still hasn't been fixed. It doesn't seem like anyone is working on fixing it either since Gateway recent (couple months ago) changes from finepoint to wacom. I wish I knew how these things work, I'd put more effort into it if I knew.

---

### Post by onemsad on 2007-11-09
Thanks to all for the information in this thread.  It seems that (at least for the M285-e) the best one can hope for is a pen that tracks OK but right-clicks and jitters around the edges of the tablet screen...most notably on the top left.

Hope is eternal so I will keep checking!  Again, thanks for the information.  Haven't looked at Linux in YEARS and am super pleased at the progress.  

All the best!

---

### Post by rampage_1973 on 2007-11-11
I am still having trouble getting the pen to work , I have downloaded the xprg-fpit package and the drivers (.so and .la ) and copied them to the correct places.
And I have tried various baud rate settings but my cursor jumps all over the place when I set the pen on the screen (clicks also without me touching the button) .
I have a GATEWAY cx2619 tablet .

any ideas or can someone point me in the right direction?

Thanks 
](*,)

---

### Post by ace214 on 2007-11-29
EDIT: For some reason my compiling doesnt work either. Had to use the posted files. Weird....

---

### Post by short3000y on 2007-12-04
i have a gateway m285E and i am a total nuub. but i would be greatful if someone just posted the total instructions on how to get the tablet working. THANKS!!!!!:)

---

### Post by ace214 on 2007-12-05
Did you read the whole topic cus they're all there....... Try something for yourself first and then tell us what went wrong and we'll help you fix it.

---

### Post by stanz on 2007-12-16
Hi All,
This thread has gone multiple! Many posts aren't identifying Tablet type or K/Ubuntu version for tweaks!
These are important tricky files we're tweaking...clarity in ALL areas of info is important as well as being most helpful {to me too!}.
I found a thread JUST FOR the [B][Gateway M285-E Finepoint Driver]("http://ubuntuforums.org/showthread.php?p=3962061#post3962061").

[/B][FONT=Book Antiqua][SIZE=3] Sad to say, no...nothing I've done here has got my stuff working, so I'll search on and edit this if something positive happens.[/SIZE][/FONT]

---

### Post by ace214 on 2008-04-25
Hate to revive an old thread, but has anyone gotten their finepoint pen to work on Hardy? I did a fresh install of Hardy so I repeated the process but compiled the driver from GIT. When I use the compiled driver or the one posted on page 3 of this topic, nothing happens when I put the pen to the screen (I am getting data from "cat /dev/ttyS0"). When I use the driver from the repositories with the same serial and xorg configuration, X turns to a gray screen and crashes when I put the pen near the screen.

I'll attach my compiled driver to see if it works for anyone else....

---

### Post by br@ssmule on 2008-06-08
I've got a friend's cx2618 that I'm attempting to fully convert over to Ubuntu 8.04.  I have everything else working (including her one Windows-holdout application working great via Wine), but the Tablet features of the lappy have thus far eluded me.  I've also tried the techniques listed previously in this thread, but apparently their compatibility is broken with Hardy Heron.

I'd be interested in teaming up with whoever in order to write and build a definitive user guide to make this easy for new Linux users to get done.  It's a lot more in-depth work that most Windows users are used to, and of course, with a fresh install of Ubuntu so easy to accomplish nowadays, it's not something new users are prepared for at all.

Any and all help would be appreciated on this.

---

### Post by ace214 on 2008-06-08
br@ssmule:
Please see [this thread.]("http://ubuntuforums.org/showthread.php?t=763380")

---

### Post by tkrause22 on 2008-07-03
ok total nub here I need a step by step to get my cx2618 to a fully working hardy ubuntu tablet PC.

---

