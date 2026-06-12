---
title: "ATI driver problem : Please Help!"
date: 2008-03-14
forum: Absolute Beginner Talk
---

### Post by Tehrooni on 2008-03-14
So I was feeling advanturous and let myself convinced to try Linux.... 
Installed Unbutu by Wubi two days ago. Installation was smooth, even connecting to the Internet was a breeze... Yupie!!!! But right away I noticed the screen resolution is really bad (can only get to 1280*1024). 

So I started looking for a solution... First inside the computer, then all over the Internet. To make a long story short, I've spend over 20 hours looking all over. Have "installed" the latest ATI driver (ati-driver-installer-8-3-x86.x86_64.run), but by the amount of documentation and questions about ATI drivers under Linux, it is obvious I am not the only one having trouble... 

The only thing is that as a newbie, following some of these VERY criptic instructions has been really difficult, and when after an hour and three restarts, it is still not working, I want to just give up and go back to my Windows world where these issues have been resolved for very longtime now. 

Frankly, I feel I am back in 1996 trying to get Windows 95 to work again. Is this life under Linux??? I really hope not, especially after hearing all these great reviews from some credible sources. If I can only get this resolution problem resolved, I think I might actually enjoy learning the rest. But right now, my eyes feel like two steal balls from all the straining. 

Can someone help me to get this working please? I have really done my homework. There is something I am not doing right. If someone can guide me through this step by step, or even long-in to my computer to get it to work, Linux world might have gained a new soul!

Thanks a bunch. 
If you prefer emailing me, here it is: tehrooni101 AT yahoo com

---

### Post by joshrobinson on 2008-03-14
click system > administration > restricted drivers, you should see ati in there click the check box next to it, it should install, restart the computer.

now you should be able to go to system > preferences > screen resolution and set what you want

---

### Post by Tehrooni on 2008-03-14
That was one of the first things I tried. It adds one new resolution which is not of much use and gives me a new refresh rate (no use either). That,s why I started hunting for the full driver. 

Thanks for trying to help. Is there anything else you can think of?

---

### Post by acirilo on 2008-03-14
just edit your xorg.config  it's under /etc/X11/ 

under the video driver section your will see modes then a set of resolutions.. just add the ones you want..and logout and login again...


i'm at supper now.. i'll be back at my box to help you walk thru in a few hours...if you havent' solved it

---

### Post by joshrobinson on 2008-03-14
could you post the output of 
```
fglrxinfo
```
just to see if the driver installed fine

also the following command may automatically set it for you

```
sudo aticonfig --resolution=0,1280x800
```
change the 1280x800 to the resolution you want

---

### Post by sloggerkhan on 2008-03-14
I think the trick is to use that button to install the driver, then enter the following in the command line:
sudo dpkg-reconfigure -phigh xserver-xorg
(If you don't use -phigh it will ask you lots of questions.)

The likely  problem is that you have a new driver, but the configuration file is still for the old driver.

However, if you have a relatively old or relatively new card, the repository fglrx driver MIGHT not support your card.
What model is it?

---

### Post by Tehrooni on 2008-03-14
Thank you both!

I was REALLY happy for a few moments because after following the instructions on a page here which included adding some stuff to the xorg.conf file, I have a whole bunch of new resolution settings. 
 
But.... none of the new resolutuons, including the native 1680*1050 seems to really improve the situation. 

I think probably the driver was installed, but not correctly. 

Here's what I get from the fglrxinfo command: 

arman@ubuntu:~$ fglrxinfo
Xlib:  extension "XFree86-DRI" missing on display ":0.0".
display: :0.0  screen: 0
OpenGL vendor string: Mesa project: [www.mesa3d.org](www.mesa3d.org)
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.4 (1.5 Mesa 6.5.2)

Does it make some sense to you? 

The other one gives this: 

arman@ubuntu:~$ aticonfig --resolution=0, 1680*1050
Using /etc/X11/xorg.conf
Saved back-up to /etc/X11/xorg.conf.fglrx-1
aticonfig: Writing to '/etc/X11/xorg.conf' failed. Bad file descriptor.

But I can go to this resolution using the System/Preferences/Screen Resolution, but obviously something is very very wrong. Everything is hazy. The menus in pages like Yahoo are all displaced. 

Are we getting closer or problem is still very deep?

---

### Post by Tehrooni on 2008-03-14
Thx sloggerkhan. I have to log into Windows to get my exact model. My Video card is fairly recent. I'll be back in a few....

---

### Post by joshrobinson on 2008-03-14
fglrxinfo should put out saying ati, not mesa, so your driver seems to not installed correctly
also when you run aticonfig put sudo in front of it, see if that makes any difference

```
sudo aticonfig --resolution=0,1680x1050
```

when you installed the driver from the ati.run package, did you have any errors?

---

### Post by Tehrooni on 2008-03-14
My graphic card is a Radeon X1300 series. 

When installing it, there were a lot of errors at different stages:-)

I installed (or attempted to install) it several times.... even once many apps in Linux stopped functioning so I reinstalled the whole OS again.....

The last time things were more smooth. I do have the ATI config Manager application now, but when I click on it it generates an error. 

Do you think I should start out clean. Reinstall Ubuntu again and follow your directions?

---

### Post by joshrobinson on 2008-03-14
if you want to get a fresh start you can do that, and try to install your driver through the "restricted drivers" application, then if you have to, you can add your resolution with the aticonfig command

but your video card is supported, so im not sure what happened

---

### Post by Tehrooni on 2008-03-14
I am glad my card is supported. I should be able to get it to work with all the help from you guys! Thanks, I really appreciate it. 

Can I sort of undo what I have done so far? I remember seeing an article that said delete all the files containing fglrx, and maybe some other action(?). I can try finding it again, or if you know how just tell me please. A fresh install is going to take me an hour, so it is certainly doable as well.

---

### Post by joshrobinson on 2008-03-14
you can always open synaptic, search for fglrx, and reinstall the xorg-driver-fglrx package
restart, and see what happens

---

### Post by Tehrooni on 2008-03-14
It didn't like it (LOL) - now I can't get the OS up again..... 
Si I am going to start fresh. Hope you'll be around to give me a hand. 
A quick question. When the OS installation is finished, it asks me if I want to update some files. So far, I've always said yes. Then it updates some 192 apps and files... Is this the right way to go, or should resolve this issue first before updating the OS?

---

### Post by joshrobinson on 2008-03-14
it shouldnt matter either way but go for the updates, then try to get your video settings correct

---

### Post by Tehrooni on 2008-03-14
Ok I am back buddy! A brand new OS. I haven't been prompted to do the updates yet, so I'll just wait. 

Now back to this problem. Obviously the resolution settings are back to what they were before. 

I havemt touched anything yet. I only rn the fglrxinfo command and this what I get:

arman@ubuntu:~$ fglrxinfo
The program 'fglrxinfo' is currently not installed.  You can install it by typing:
sudo apt-get install xorg-driver-fglrx
Make sure you have the 'restricted' component enabled
bash: fglrxinfo: command not found

So start by System/Administration/Restricted Driver Manager ?

---

### Post by joshrobinson on 2008-03-14
yeah, install it from the restricted drivers menu, then restart your computer
then do a fglrxinfo and post your output

sorry late getting back to this thread, had to get some food

---

### Post by Tehrooni on 2008-03-14
No problem, even a Linux guy has to eat I guess

here's the fglrxinfo

arman@ubuntu:~$ fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: Radeon X1300/X1550 Series
OpenGL version string: 2.0.6334 (8.34.8)

Looks like it is seeing the card! But the highest resolution I have is 1280*1024. 

Is it just a matter of config? Maybe try?

sudo aticonfig --resolution=0,1680x1050

Thx for all your help. I feel we're getting close.....

---

### Post by Tehrooni on 2008-03-14
btw the smily is 8 ) 
(no space)

---

### Post by joshrobinson on 2008-03-14
nice, thats the correct output of fglrxinfo, it doesnt mention mesa now, so you are on the right track.. do the aticonfig command as you stated and see if you can get it to go up to your resolution

---

### Post by forrestcupp on 2008-03-14
It looks like you are getting it worked out.  But for future reference, if the Restricted Drivers Manager doesn't work for you, the easiest way to get the latest drivers installed and set up is to use a program called [Envy](http://www.albertomilone.com/nvidia_scripts1.html).  It does it all for you.  It downloads the driver from ATI's website, installs it, and configures it.  You don't have to do anything.

---

### Post by joshrobinson on 2008-03-14
> **forrestcupp said:**
> It looks like you are getting it worked out.  But for future reference, if the Restricted Drivers Manager doesn't work for you, the easiest way to get the latest drivers installed and set up is to use a program called [Envy](http://www.albertomilone.com/nvidia_scripts1.html).  It does it all for you.  It downloads the driver from ATI's website, installs it, and configures it.  You don't have to do anything.

i thought of suggesting that, but ive heard alot of horror stories about that application on the forums, and ive never had to use it personally

---

### Post by Tehrooni on 2008-03-14
no, it gives:

arman@ubuntu:~$ sudo aticonfig --resolution=0,1680x1050
error at set screen resolution : screen0 does not exist
aticonfig: parsing the command-line failed.


To be sure I also tried 

sudo aticonfig --resolution=0,1680*1050
and 
sudo aticonfig --resolution=1,1680x1050

No go in all cases

---

### Post by Tehrooni on 2008-03-14
I actually tried Envy this morning but got an error message about dependencies and Python so didn't want to get more confused than I already was. Thx for the suggestion though...

---

### Post by joshrobinson on 2008-03-14
ok run this command

```
 sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.backup
```
this will backup your xorg.conf file

now do

```
sudo gedit /etc/X11/xorg.conf
```
scroll down to this section
```

Section "Screen"
	Identifier	"Default Screen"
	Device		"ATI Technologies Inc Radeon XPRESS 200M 5955 (PCIE)"
	Monitor		"Generic Monitor"
	Defaultdepth	24
	SubSection "Display"
		Modes		"1280x800"
	EndSubSection
EndSection
```

note yours will look different, and add your resolution in the quotes over your highest one or add it in front of the highest one with quotes around it
then restart, if you run into trouble boot into recovery mode and change it back, or rename your backup

```
sudo mv /etc/X11/xorg.conf.backup /etc/X11/xorg.conf
```
to restore your backup

---

### Post by Tehrooni on 2008-03-14
Yes, it looks different. I seem to have several depths. Do I add 1680x1050 to each one?



Section "Screen"
	Identifier	"Default Screen"
	Device		"Generic Video Card"
	Monitor		"DELL 2007WFP"
	Defaultdepth	24
	SubSection "Display"
		Depth	1
		Modes		"1280x1024"	"1152x864"	"1024x768"	"800x600"	"720x400"	"640x480"
	EndSubSection
	SubSection "Display"
		Depth	4
		Modes		"1280x1024"	"1152x864"	"1024x768"	"800x600"	"720x400"	"640x480"
	EndSubSection
	SubSection "Display"
		Depth	8
		Modes		"1280x1024"	"1152x864"	"1024x768"	"800x600"	"720x400"	"640x480"
	EndSubSection
	SubSection "Display"
		Depth	15
		Modes		"1280x1024"	"1152x864"	"1024x768"	"800x600"	"720x400"	"640x480"
	EndSubSection
	SubSection "Display"
		Depth	16
		Modes		"1280x1024"	"1152x864"	"1024x768"	"800x600"	"720x400"	"640x480"
	EndSubSection
	SubSection "Display"
		Depth	24
		Modes		"1280x1024"	"1152x864"	"1024x768"	"800x600"	"720x400"	"640x480"
	EndSubSection
EndSection

---

### Post by joshrobinson on 2008-03-14
na, in your 24 depth section at yours in front
```
Depth 24
Modes "1680x1050" "1280x1024" "1152x864" "1024x768" "800x600" "720x400" "640x480"
```
so it looks like that

---

### Post by Tehrooni on 2008-03-14
That works! 

But I am back to the problem of a bit earlier. At this resolution, as with the previous one, everything is hazy (just a bit smaller). It looks like a laptop with screen resolution that is not optimal, plus some menu items that are displaced (example, "more" in yahoo.com is under the "web" but in reality it should be beside shopping (see top of their page). 

So I wonder if this is the right resolution? Or is that is the issue here. 1680x1050 is what I have under Windows and it is very crisp. In fact, most resolutions under windows look fine. How can I get this driver to get the most out of the graphic card?

---

### Post by joshrobinson on 2008-03-15
do you mind taking a screenshot? just do a printscreen and it should appear on your desktop, then post a reply, scroll down to additional options and you should see "manage attachments" attach the image so i can look at it.. your driver is set up correctly, unless this is a fault of the driver im not sure

also do you have a model number for your monitor so i can look at the specs?

---

### Post by Helios1276 on 2008-03-15
Hey man , I'm new to ubuntu too and am currently wrestling with my ATI x1400 card. I got everything bar 3d going. Have a look here, it might help and good luck!
[http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide)

---

### Post by Tehrooni on 2008-03-15
This is a cool forum! Didn't think you could attach stuff to your messages. 

My monitor is a DELL 2007WFP

I just noticed that in the xorg.conf file, the Device is "Generic Video Card"
Is this correct? I had a flash back from a few years ago when I struggled with a Win2000 that would not see a graphic card. It would always see it as a Generic Video Card and we couldn't get the functionalities until that was changed. 

Let me know if you see the attachment!

---

### Post by joshrobinson on 2008-03-15
as far as the image quality on that screenshot, everything looks fine to me, doesnt look blurry or anything.. but i do see how the "more" isnt where it should be

i also looked up your monitor, and 1680x1050 is the correct resolution that you should be running

now things may be blurry on your end, but i think it comes down to the monitor displaying the signal, because it looks sharp and crisp in the image

i honestly dont know what to tell you in this situation, im actually quite puzzled.. maybe mess with your monitors settings to try to clear it up some?

---

### Post by acirilo on 2008-03-15
is it everything on the desktop? or just the web browser? it could be the rendering engine on the browser.....

---

### Post by joshrobinson on 2008-03-15
> **acirilo said:**
> is it everything on the desktop? or just the web browser? it could be the rendering engine on the browser.....

thanks for poping in, does that screenshot look ok to you quality wise? be good to get a second opinion

---

### Post by piousp on 2008-03-15
The image quality its fine. Let me get something to eat and read the hole thread.

---

### Post by Tehrooni on 2008-03-15
It's the same thing in other applications. When I look at the image, it looks very fuzzy. I looked at it in the browser and F-spot. Also opend Open Office, and charcters are all hazy, so whatever it is, it is related to the screen/or the card. I am going pop in the windows and to take a look at image. I guess if the rendering by the Graphic card is good, then it's the Monitor. But I never had to adjust my monitor before.... 

Once again, I really appreciate all of your help. It's great to get feedback and not feel I am working in the dark all alone.

---

### Post by acirilo on 2008-03-15
> **joshrobinson said:**
> thanks for poping in, does that screenshot look ok to you quality wise? be good to get a second opinion

yea the shot looks great..

---

### Post by acirilo on 2008-03-15
> **Tehrooni said:**
> It's the same thing in other applications. When I look at the image, it looks very fuzzy. I looked at it in the browser and F-spot. Also opend Open Office, and charcters are all hazy, so whatever it is, it is related to the screen/or the card. I am going pop in the windows and to take a look at image. I guess if the rendering by the Graphic card is good, then it's the Monitor. But I never had to adjust my monitor before.... 

Once again, I really appreciate all of your help. It's great to get feedback and not feel I am working in the dark all alone.

i think its your pc.. because the capture doesn't reveal the area as blurry

---

### Post by Tehrooni on 2008-03-15
That image looks a bit better when I look at in Windows, but I see a notable difference between it and what I have under Windows. Here's another screen shot under Win. It is noticeably sharper, at least when I look at it. 

Is it possible that Windows Vista has better rendering capabilities than Linux - or at least this compared to this version of Linux? 

I must say, there is another noticeable difference between the two OS, and that is noise. It's all so quite when I am in Linux. I don't know why Windows writes so much to the HD and when it does it is SO loud!!

---

### Post by joshrobinson on 2008-03-15
the only difference i notice is the fonts, but when you run a lower resolution you dont notice any of the blurryness?

---

### Post by acirilo on 2008-03-15
> **Tehrooni said:**
> That image looks a bit better when I look at in Windows, but I see a notable difference between it and what I have under Windows. Here's another screen shot under Win. It is noticeably sharper, at least when I look at it. 

Is it possible that Windows Vista has better rendering capabilities than Linux - or at least this compared to this version of Linux? 

I must say, there is another noticeable difference between the two OS, and that is noise. It's all so quite when I am in Linux. I don't know why Windows writes so much to the HD and when it does it is SO loud!!

i can't see anything...

yes the Video cards seemed to be designed to run on windows.. so it might cause "less" problems by default in windows... 
i have an ATI card intergated in my motherboard.. i bought a Nvida GeForce FX 5500 .. ii'm just debating if i want to open it or take it back to wal-mart...

the ATI seems so buggy.. i can't get my "special effects:" to work at all.. but i get clear and high resolutions with the fglrx driver...

yea.. with windows.. it's always doing something weird in the background.. maybe calling home to MS, ..or who knows... it's not knowable..

---

### Post by Tehrooni on 2008-03-15
> **joshrobinson said:**
> the only difference i notice is the fonts, but when you run a lower resolution you dont notice any of the blurryness?

More blurry in other resolutions.
 
The fonts should be the same no? When I look at this screen in Ubuntu, it's as if I am looking at my monitor through a sheet of plastic. It's most noticeable when I look at the characters. 

I am going to install this package on my laptop and see how it looks there. Thanks everyone for all the help. I will update you if I come across something else!

---

### Post by Tehrooni on 2008-03-15
> **acirilo said:**
> 

yea.. with windows.. it's always doing something weird in the background.. maybe calling home to MS, ..or who knows... it's not knowable..

I dont even want to think about that one.....

I know Vista does a LOT of system backups and they have a new thingy that is checking for "threats" all the time. I guess it's to keep up with the times.... What is really strange is the way it writes to the HD. I can hear it going from another room..... With Linux, I noticed the writing is very quite and smooth. It's as if it writes its data in a sequencial and orderly manner. Where as Windows is writing one bit on this side of the HD and the next bit on the opposite side.... 

Anyway, I think I am stuck with Windows for a while yet. I can always wear headphones when I work.

---

### Post by acirilo on 2008-03-15
> **Tehrooni said:**
> I dont even want to think about that one.....

I know Vista does a LOT of system backups and they have a new thingy that is checking for "threats" all the time. I guess it's to keep up with the times.... What is really strange is the way it writes to the HD. I can hear it going from another room..... With Linux, I noticed the writing is very quite and smooth. It's as if it writes its data in a sequencial and orderly manner. Where as Windows is writing one bit on this side of the HD and the next bit on the opposite side.... 

Anyway, I think I am stuck with Windows for a while yet. I can always wear headphones when I work.

yea.. don't give up.. it took me a long time to finally kick the windows habit..and i still have a laptop that my wife uses with XP on it. i took off Vista and put XP on it because Vista made me to mad to often. 

one day Windows will have a decent defrag program.. maybe that will help with the noise.. i don't know why it's so noisy to be honest.

---

