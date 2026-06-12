---
title: "Google Earth Hangs"
date: 2006-12-18
forum: Absolute Beginner Talk
---

### Post by loyaleagle on 2006-12-18
Hello everyone,

Still as happy as ever with Ubuntu. I installed Google Earth a while ago. Work great for a week. Now when I start it, I seems to hang (CPU is at 100% for a long time, but app refuses to initialize). I un-installed it and re-installed to no avail. Any ideas why it is doing this?

Thanks, Loyaleagle:-D

---

### Post by loyaleagle on 2006-12-18
Oh... Forgot to state that I did install Firestarter.... could this be the problem?

---

### Post by taurus on 2006-12-18
Try to run it from a terminal to see exactly what the error message is.

---

### Post by loyaleagle on 2006-12-18
I need a little help with terminal commands?

---

### Post by gunksta on 2006-12-18
Where did you install it to?

For example, I installed it to /opt/google-earth

This is where I usually put programs that, like Google Earth aren't managed by apt-get.

If you put it into /opt/google-eart, then you need to go to the commandline (gnome-terminal) and run:

```
/opt/google-earth/googleearth
```

Of course, you will have to modify my example because I have no idea where you put Google Earth.

Once you figure out how to run Google Earth from the command line, post the output from that command here. I think it will help me confirm my suspicions.

I think your computer is going to say something like:

```
Xlib:  extension "XFree86-DRI" missing on display ":0.0".
```


Google Earth requires an accelerated video card to work. What kind of video card do you have and are you using the accelerated (hardware) drivers for this card? My theory, you are using a generic driver and this is the problem. I bet you upgraded your kernel since last time you used Google Earth and apt-get goofed up and didn't reconfigure everything correctly.

One way to help us figure out if it's the video card or not is to open up the file (use gedit) /etc/X11/xorg.conf

Scroll past the input devices and look for something that reads:

```
Section "Device"
```

Post the contents of this part of the file to this discussion. I think this last idea may explain why your processor spikes, and the program hangs. I just tried disabling the hardware driver on my card, and my copy of Google Earth did exactly as you described.

--andy

---

### Post by loserboy on 2006-12-18
if it worked for a while and then stopeed working it wouldnt make sense to be a video card issue would it?
did you try disabling firestarter and see if it works then?  
so far ive seen ubuntu acts strange compared to windows whith its network connections, it likes to freeze up when theres a problem rather then give up after a number of tries and throw an error.

---

### Post by loyaleagle on 2006-12-18
Here is what you asked for......
Section "Device"
	Identifier	"ATI Technologies, Inc. Radeon Mobility M7 LW [Radeon Mobility 9000]"
	Driver		"ati"
	BusID		"PCI:1:0:0"
EndSection

---

### Post by loyaleagle on 2006-12-18
I tried stoppin the firewall (firestarter) and still a problem with GoogleEarth
I even uninstalled Firestarter to make sure and still a problem.

I appreciate the help and posted what Gunksta requested.

---

### Post by taurus on 2006-12-18
What kind of error message do you get when you run it from a terminal?

---

### Post by loyaleagle on 2006-12-18
Can't even get it going through the terminal. The system now freezes completely when Googleearth is started (Terminal). All else is great. No other issues, just google earth. How can I update my video drive to take advantage of the hardware acceleration?

---

### Post by gunksta on 2006-12-18
I think I guessed correctly. You are using the ATI driver for your graphics card. I thought this would be the problem. I have an ATI card too, and unless I am using the fglrx driver, I can forget about using Google Earth.

I really don't think your firewall is the problem. I can't think of any reason why a firewall would max your CPU, and not let you into the program at all. If we get the Graphics driver going, then we'll see if your firewall is a problem or not.

In contrast, it makes perfectly good sense for a heavy graphics program like Google Earth to max the processor if it's trying to make MESA do what the graphics card is supposed to be doing.

Pop open Synaptic (System -> Administration -> Synaptic Package Manager) and look up fglrx.

You must have xorg-driver-fglrx installed. If you do, make sure it is the newest version. It's your call if you want the fglrx-control panel or not. It' not necessary but it is a nice way to quickly check your configuration. Otherwise, it's useless.

Once you have these verified as installed, or installed... let's go play on the commandline. (Sorry, I usually avoid telling people to do this, but there's no other good way to do this.)

At the command line (gnome-terminal)  there are a couple of things you can try. First

```
cd /etc/X11/
sudo cp xorg.conf xorg.conf.backup
```And enter your password. This will back up your existing configuration. So, if we blow everything up you aren't completely screwed! :-D

ATI provides a way to configure their cards, and it's always a good place to start. 

```
sudo aticonfig --initial --input=/etc/X11/xorg.conf
```Now reset your X-Server by hitting Control-Alt-Backspace (this is going to log you out and bring you back to log in screen)

IF THIS &^%$#@#^ THINGS UP MAKe SURE YOU WRITE THE NEXT PART DOWN!!!!! You can get to a command line by CTRL-Alt-F2 (or any other F-Key)
```
cd /etc/X11/
sudo rm xorg.conf
sudo cp xorg.conf.backup xorg.conf

```This will help if things get REALLY whack by resetting your machine to it's original configuration



Once you log back in, open a terminal and try

fglrxinfo

and see what it says. If you see anything about MESA, it didn't work. I am sure there are some better directions on getting ATI video cards to work on these forums, and I would suggest you read those too (just search for "ATI", trust me, they're there)


--andy

---

### Post by gunksta on 2006-12-18
> **loserboy said:**
> if it worked for a while and then stopeed working it wouldnt make sense to be a video card issue would it? 

Actually, sometimes kernel updates screw this up. It shouldn't happen, but it does. Especially if you are unfortunate and use an ATI card like the OP does. (I have one too....I won't make that mistake again!)

--andy

---

### Post by Metallinut on 2007-01-13
Hey I found this thread when having similar issues with googleearth. I went through a big huge rigoramarole with getting XGL and Beryl to work on my system.  Now Beryl's working great, and I'm afraid to change anything, cause it might break it.  But here's the output of fglrxinfo:
```

Xlib:  extension "XFree86-DRI" missing on display ":1.0".
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: ATI Mobility Radeon X1400 Generic
OpenGL version string: 2.0.6011 (8.28.8)

```

And coincedentally that's the error that I get when trying to run googleearth.  Is there simply a line about XFree86-DRI that I can add to xorg.conf?  If so, what's the format, and where does it go?

Thanks!

---

### Post by niekko on 2007-01-21
Same problem here except that only starting googleearth gives me the error ```
Xlib:  extension "XFree86-DRI" missing on display ":1.0"
``` fglrxinfo outputs ```
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: ATI Mobility Radeon X1300 Generic
OpenGL version string: 2.0.6234 (8.32.5)
```

---

### Post by niekko on 2007-01-21
I found a solution at [[COLOR="Blue"]http://wiki.beryl-project.org/wiki/Troubleshooting_Xgl#Error_on_running_hardware_accerlated_3d-applications[/COLOR]]("http://wiki.beryl-project.org/wiki/Troubleshooting_Xgl#Error_on_running_hardware_accerlated_3d-applications").

Try starting Google Earth like this: ```
DISPLAY=:0 googleearth
```

---

### Post by Dr. Nick on 2007-02-27
Old Topic but here is what worked for me

[http://n01getsout.com/blog/2006/11/26/google-earth-for-linux-freezing-with-ati/](http://n01getsout.com/blog/2006/11/26/google-earth-for-linux-freezing-with-ati/)

still using ati not fglrx drivers

---

### Post by borobudur on 2007-03-11
I have the problem with this message:
```
Xlib:  extension "XFree86-DRI" missing on display ":1.0".
```My xorg.conf file device part looks like that: 
```
Section "Device"
    Identifier  "ATI Technologies, Inc. Radeon Xpress 200M (RS482)"
    Driver      "fglrx"
    Option        "VideoOverlay" "on"
    Option        "OpenGLOverlay" "off"
    Option "DRI" "true"
    Option "ColorTiling" "on"
    Option "EnablePageFlip" "true"
    Option "AccelMethod" "EXA"
    Option "XAANoOffscreenPixmaps"
    Option "RenderAccel" "true"
    #Option "AGPMode" "x" <- x may be 2 or 4 depending on your system
    Option "AGPFastWrite" "on" 
    BusID       "PCI:1:5:0"
EndSection

```Your help would be great!
borobudur

---

### Post by borobudur on 2007-03-12
I have done that with the copy of *[[I]libGL.so.1.2*]("http://www.ground-impact.com/libGL.so.1.2") to [/I]/usr/local/google-earth *and rename it to **[[I]libGL.so.1 but still no sucess :-(*]("http://www.ground-impact.com/libGL.so.1.2")


[/I]

---

### Post by Dr. Nick on 2007-03-12
I could never get the fglrx drivers working, so not exactly sure how to troubleshoot your problem.  I had to use that link to get google earth to run with the standard non accelerated "ati" drivers

You could try switching to "ati" instead of fglrx but you would loose 3d acceleration.

---

### Post by borobudur on 2007-03-14
I changed the driver to 'ati' but also here it doesn't work. It stays forever initialising. To bad...

---

### Post by DougieFresh4U on 2007-03-14
Although this may not help, but my machine kept freezing with google earth  and after many post on the forum i decided to add another stick of RAM to my machine and I'll be dammed if that didn't solve my problem!!!  :) :)  All replies to my post were telling me my graphics card(an old Intel card) Just my two cents worth.

---

### Post by rnewman38 on 2007-03-23
Found The FIX!

To disable Composite extensions, add the following lines to the end of /etc/X11/xorg.conf file:

Section "Extensions"
        Option "Composite" "false"
EndSection

This will bring back support for DRI, 3D acceleration and, thus, OpenGL support.

Reference:

[http://felipe-alfaro.org/blog/2006/09/06/ubuntu-edgy-ati-fglrx-dri-3d-acceleration-and-xorg-composite-extension/](http://felipe-alfaro.org/blog/2006/09/06/ubuntu-edgy-ati-fglrx-dri-3d-acceleration-and-xorg-composite-extension/)

Cheers:)

---

### Post by whistlerspa on 2007-03-31
Same here  - i wasted my time installing ATI propriety drivers as well with the same result.

---

### Post by whistlerspa on 2007-03-31
Really confused  - got about five different versions of xorg.conf in my /etc/X11 folder. one of them has the words about extensions, the others don't  - how do I know which one is being used.  I'm afraid that this whole Google earth thing is about to hit the too hard basket.  

FTR  I have the same problem with Piccaso2 as well.

---

### Post by STREETURCHINE on 2007-03-31
if i am not mistacken you should be able to run google earth from terminal by typing 


```
google earth
```

and that will then produce an error message if it fails

not on my ubuntu computer so i cant check ,but do it it cant hurt

---

### Post by Dr. Nick on 2007-03-31
google earth and every program will use xorg.conf

the ones with other numbers in the filename are backups.

I never goy fglrx working at all, here is my xorg that works with google earth and beryl. Only change to get google earth working was using the link i posted earlier about changing a file
[http://n01getsout.com/blog/2006/11/26/google-earth-for-linux-freezing-with-ati/](http://n01getsout.com/blog/2006/11/26/google-earth-for-linux-freezing-with-ati/)
```

Section "Device"
        Identifier      "ATI Technologies Inc RV280 [Radeon 9200]"
        Driver          "radeon"
        BusID           "PCI:1:0:0"
        Option "ColorTiling" "on"
        Option "EnablePageFlip" "true"
        Option "XAANoOffscreenPixmaps"
        Option "RenderAccel" "true"
EndSection
```

---

### Post by PuffServe on 2007-04-04
Friends,

I found discussions in other forums which suggested that the ATI proprietary graphics drivers did not work well with GoogleEarth (sorry, can't find the actual links from my browser history).   I recall one discussion thread that suggested putting the non-ATI version of libGL.so.2 into the directory where GoogleEarth binary resides.

In my case, I had an aborted installation of ATI's proprietary driver package.  Essentially the solution is to undo that by updating the libGL.so

[INDENT]# yum update mesa-libGL.i386[/INDENT]

which updated 

[INDENT]mesa-libGL.i386 6.5.1-9.fc6
mesa-libGL-devel.i386 6.5.1-9.fc6[/INDENT]

After that, Google Earth executed fine.

Hope this helps...

---

### Post by mwacky on 2007-05-19
Sorry to jump in here, but if anybody is still around, my Google earth is hanging and I am not getting any messaging from the command line.  Google Earth would hang when my graphics card was not setup properly, but it would suck down 100% of the CPU, now that i think my graphics card is working, it just hangs with the splash screen and does use any CPU.  Any ideas?

---

### Post by mwacky on 2007-05-19
Okay more evidence here, if I reboot the machine Google Earth fires up and works fine.  I think the problem is happening if I put the computer to sleep by closing the laptop lid and come back to it later, then I have the problem mentioned in the post above.  It hangs with just the splash screen and does not use cpu.

---

### Post by firmwire on 2007-07-10
Decided to post this in more than one forum section:

I have been all over the forums and have found some very good info for possibly solving my issue. I am not sure if it will work or not since I am not at home at the moment. I wanted to run some things by you all to make it easier when I do get home.

Issue: 
Running Compiz Fusion ( perfectly) in xgl w/ gnome. I have fglrx as the driver I am using. I have Composite set to "0" and have even changed it to "false".
When I run glxinfo I get direct rendering is NO. 
glxgears works fine in any session I do.
From what I can find, in order for compiz fusion to run it has to be in xgl mode. But google earth NEEDS direct rendering ( I think).
I think if I just go into a non xgl session the same glxinfo gives me YES for direct rendering. I don't remember though at the moment.
Even so...when I run google earth in any session I get 100% CPU usage from it. It just hangs at the initialization splash screen. I can still kill the process, so it doesn't lock my system up completely. 
I have read that people have been able to get it to work with Beryl and ATI cards running together. I am just trying to figure out how to get it to run with my setup.

In case the question comes up, I have installed it two different ways. I had installed it through Automatix. Then uninstalled it. Then I installed it from the download from the google earth linux download site. Both installs went fine. Both hang and produce 100% cpu usage when activated and hangs on the splash screen.

I found this post [http://ubuntuforums.org/showthread.php?t=176636](http://ubuntuforums.org/showthread.php?t=176636). Do you think this will solve my problem?

Also I have seen posts about libGL.so.1.bz2 and libGL.so.1.tar.bz2, and I do you think this may fix my issue?

Oh yeah... and I even tried this earlier today: DISPLAY=:0 /usr/local/google-earth/googleearth. It just loads the splash screen and hangs.

I know people have had the issue with 100% cpu usage, but I couldn't find anything saying what they did to fix it or if they were even able to.
I have seen in one place that one person actually installed an extra stick of RAM and that helped. But I don't think I should have to. Everything else works great. I only have 1GB on this system currently.

I am running Feisty 64 and it runs completely stable. I love it!

Any suggestions/solutions are greatly appreciated. Thanks in advance.

---

### Post by firmwire on 2007-07-11
/bump

---

### Post by gunksta on 2007-07-12
Firmwire, 

I have Google Earth running just fine on Kubuntu Feisty and my friend uses it on Ubuntu too. We both have ATI cards and use the evil proprietary drivers.

My suggestion: Disable Compiz-Fusion and then try to run Google Earth. Compiz-Fusion is, to the best of my knowledge beta-ware. If it runs correctly on Metacity or whatever XFCE is using for a window manager these days, you will probably be able to redirect your efforts . .  or wait for the compiz stuff to settle down.

I also know that XGL causes many problems with some programs. I don't think the problem is Google Earth. 

--andy

---

### Post by Icarosaurus on 2007-07-20
Hi all,
my computer freezes when I start googleearth with metacity, but doesn't freeze when I start it with compiz. When I switch to metacity while googleearth is open all works fine.
I use an ati 9600 with mesa drivers. Anyone experiencing the same behaviour?

---

### Post by angryfirelord on 2007-07-23
Hmm, no success for me. I'm using the fglrx drivers and google earth still gets stuck.

---

### Post by gunksta on 2007-07-24
> **Icarosaurus said:**
> Hi all,
my computer freezes when I start googleearth with metacity, but doesn't freeze when I start it with compiz. When I switch to metacity while googleearth is open all works fine.
I use an ati 9600 with mesa drivers. Anyone experiencing the same behaviour?


I am surprised you are able to get compiz to work (in a useful manner) with the mesa drivers.

I'm sorry I can't be more help. I run Kubuntu, not compiz, fusion, beryl, or metacity.

My understanding is that Google Earth uses OpenGL. Programs that use OpenGL sometimes cause problems with compiz/et al. I am surprised to hear someone say they can't get it to work under metacity, but they can under compiz. Are you sure you're using MESA drivers?

--andy

---

