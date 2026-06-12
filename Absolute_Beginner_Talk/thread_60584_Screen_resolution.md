---
title: "Screen resolution"
date: 2005-08-28
forum: Absolute Beginner Talk
---

### Post by pawnUz on 2005-08-28
Hi

I just installed Ubunto 5.04 but during the installation when it aks you to choose which screen resolutions xserver is going to use i accidently only choosed the 3 default ones (1024x768, 800x600, 640x480). I dont know if this mathers or not but these are the only screen resolutions i can choose from and i really want to run it on 1280x1024, how do i fix this?

I tried adding 1280x1024 in the xorg.conf file and i have installed nvidia-gfx and nvidia-settings without any luck.

This is my first time using Linux ever so please try and respond in a way i can understand.

Thanks in advance :)

---

### Post by aysiu on 2005-08-28
I think you'll find the solution you're looking for in several threads in [this Google search](http://www.google.com/search?hl=en&q=site%3Aubuntuforums.org+screen+resolution&btnG=Google+Search). Poke around in a few of those. If you have further questions, let us know.

---

### Post by frodon on 2005-08-28
It's a well known problem, all you have to do, i think, is to add the good (USE THE CONSTRUCTOR PARAMETERS OF YOUR SCREEN ... really important) refreshrate lines in the device section like that : ```
Section "Monitor"
	Identifier	"Écran générique"
	Option		"DPMS"
	HorizSync	28-70
	VertRefresh	43-160
EndSection
```Use the search field of the forum with resolution or refresh rate as keywords and you will find a lot of threads about that, all the answers are in this forum, just take the time to search  ;-) .
But if you still have problems just ask.

---

### Post by tseliot on 2005-08-28
ctl-alt-f1 (so as to get to the command line)

login with your username and password (if required)

sudo /etc/init.d/gdm stop (or "kdm stop" if you use KDE)

sudo nano /etc/X11/xorg.conf

Make sure the only resolution is the one you want to use (look at the example below)

Section "Screen"
Identifier"Default Screen"
Device"NVIDIA Corporation NV17 [GeForce4 MX 420]"
Monitor"IBM E74"
DefaultDepth24
SubSection "Display"
Depth1
Modes"[COLOR=Red]1280x1024[/COLOR]" 
EndSubSection
SubSection "Display"
Depth4
Modes"[COLOR=Red]1280x1024[/COLOR]" 
EndSubSection
SubSection "Display"
Depth8
Modes"[COLOR=Red]1280x1024[/COLOR]"
EndSubSection
SubSection "Display"
Depth15
Modes"[COLOR=Red]1280x1024[/COLOR]"
EndSubSection
SubSection "Display"
Depth16
Modes"[COLOR=Red]1280x1024[/COLOR]"
EndSubSection
SubSection "Display"
Depth24
Modes"[COLOR=Red]1280x1024[/COLOR]"
EndSubSection
EndSection

CTRL+O to save (yes, use the same name and overwrite the file)
CTRL+X to exit

/etc/init.d/gdm start (or "kdm start" if you use KDE)

Tell me if it works

---

### Post by pawnUz on 2005-08-28
[QUOTE=frodon]It's a well known problem, all you have to do, i think, is to add the good (USE THE CONSTRUCTOR PARAMETERS OF YOUR SCREEN ... really important) refreshrate lines in the device section like that : ```
Section "Monitor"
	Identifier	"Écran générique"
	Option		"DPMS"
	HorizSync	28-70
	VertRefresh	43-160
EndSection
```Use the search field of the forum with resolution or refresh rate as keywords and you will find a lot of threads about that, all the answers are in this forum, just take the time to search  ;-) .
But if you still have problems just ask.[/QUOTE]

I tried putting in higher values on HorizSync and VertRefresh and it worked, but what do these values mean and how do i found out which values are right for my monitor?

Thanks

---

### Post by frodon on 2005-08-28
Be careful wrong hsync and vertsync parameters could destroy your screen, so open a google page and type the name of your screen and you will find the specification of your screen. This specification define the horizontal and vertical refresh rate that you MUST use. Also if you kept the box of your screen you should have inside a manual which contain the specification of the screen.

---

### Post by pawnUz on 2005-08-28
[QUOTE=frodon]Be careful wrong hsync and vertsync parameters could destroy your screen, so open a google page and type the name of your screen and you will find the specification of your screen. This specification define the horizontal and vertical refresh rate that you MUST use. Also if you kept the box of your screen you should have inside a manual which contain the specification of the screen.[/QUOTE]

The thing is in the manual it says: Horizontal Sync: 31 ~ 60 Hz and Vertical Sync 56 ~ 75 Hz but when i put these values in the xorg file the 1280x1024 option disappears and i know my monitur supports 1280x1024.

So what do i do?

---

### Post by frodon on 2005-08-28
Hum, it's quite strange. Could you give me the name of your screen ?

---

### Post by pawnUz on 2005-08-28
[QUOTE=frodon]Hum, it's quite strange. Could you give me the name of your screen ?[/QUOTE]

It's Samsung SyncMaster 172x.

Thanks for helping me :)

---

### Post by aysiu on 2005-08-28
[QUOTE=pawnUz]It's Samsung SyncMaster 172x.

Thanks for helping me :)[/QUOTE] I looked it up at the Samsung website, and your HorizSync and VertRefresh ranges are correct, but according to the documentation, it doesn't support more than 1024 x 768 resolution. Check out the PDF yourself:

[http://product.samsung.com/cgi-bin/nabc/support/b2c_downloadcenter_detail.jsp?eUser=&mobile=N&oid=1073809617&cntType=UM&cntId=41955&lang=EN](http://product.samsung.com/cgi-bin/nabc/support/b2c_downloadcenter_detail.jsp?eUser=&mobile=N&oid=1073809617&cntType=UM&cntId=41955&lang=EN)

---

### Post by frodon on 2005-08-29
[QUOTE=aysiu]I looked it up at the Samsung website, and your HorizSync and VertRefresh ranges are correct, but according to the documentation, it doesn't support more than 1024 x 768 resolution. Check out the PDF yourself:

[http://product.samsung.com/cgi-bin/nabc/support/b2c_downloadcenter_detail.jsp?eUser=&mobile=N&oid=1073809617&cntType=UM&cntId=41955&lang=EN](http://product.samsung.com/cgi-bin/nabc/support/b2c_downloadcenter_detail.jsp?eUser=&mobile=N&oid=1073809617&cntType=UM&cntId=41955&lang=EN)[/QUOTE]
Strange I found a [specification](http://www.overclockersclub.com/reviews/samsung_syncmaster_172x_lcd.php)  which define other hsync and vertsync parameters and 1280 * 1024 as maximum resolution. Is it the good screen ?
If you don't use the hsync and vertsync constructor's parameters ... it's at your own risks. But check if the specification above correspond to your screen and if it's the case use the defined hsync and vertsync parameters and it will solve your problem. Also it's possible that your screen can't support 1280* 1024.

---

### Post by xmastree on 2005-08-29
[QUOTE=pawnUz]It's Samsung SyncMaster 172x.[/QUOTE]I hate myself for suggesting this but...

What resolution can you achieve with that monitor in Windows?

---

### Post by arnoct on 2005-08-29
First of all, you don't have to go manually editing your horizontal and vertical refresh rates. First of all, run this in a console:

sudo dpkg-reconfigure xserver-xorg

This will bring up the configuration for X.Org which you saw when you installed Ubuntu.

Now, if you have an nVidia card and you're *sure* your monitor will support that resolution, run the following in the terminal:

sudo gedit /etc/X11/xorg.conf

Scroll down to the "Device" section, and add this:

Option "IgnoreEDID" "True"

This will make the drivers ignore what the monitor says its maximum resolution is. BE CAREFUL, this could damage your monitor (but in my experience, it never did anything to me :p)

Hope it works!

---

### Post by frodon on 2005-08-29
I think write in xorg.conf file constructors's refresh rate parameters is a more secure way to enable higher resolutions, indeed the way you gave will work but i don't recommend that way for noobs because you have to know what you do.

---

### Post by arnoct on 2005-08-29
IMHO it's a *lot* scarier inputting custom refresh rates. That, and some people (like me) don't have the original documentation from their monitor. Ignoring the EDID is somewhat safer than potentially sending your monitor a refresh rate it can't handle.

---

### Post by frodon on 2005-08-29
of course that why i always recommend to to do a google search to get the good parameters before adding these lines.
So in both case you need to check the specification of the screen, it's the most important point for me.
But both way are goods ... it's not the question but i don't want to destroy pawnUz's screen  ;-)  
So pawnUz all you have to do is to follow one of these 2 ways and respect the resolution that your screen can manage.

---

### Post by pawnUz on 2005-08-29
[QUOTE=aysiu]I looked it up at the Samsung website, and your HorizSync and VertRefresh ranges are correct, but according to the documentation, it doesn't support more than 1024 x 768 resolution. Check out the PDF yourself:

[http://product.samsung.com/cgi-bin/nabc/support/b2c_downloadcenter_detail.jsp?eUser=&mobile=N&oid=1073809617&cntType=UM&cntId=41955&lang=EN](http://product.samsung.com/cgi-bin/nabc/support/b2c_downloadcenter_detail.jsp?eUser=&mobile=N&oid=1073809617&cntType=UM&cntId=41955&lang=EN)[/QUOTE]

Ok, im gonna redo my post :P

The specs that i looked at yesterday and that aysiu found was for the 152x, the 152x and 172x shares the same manual and thats why we got the wrong specs. If you look further down in that pdf you'll find the specs for the 172x which are the specs that frodo found (hsync 30-81, max res 1280x1024). So now im using the hsync rage 30-81 and its working.

The only thing that still has me thinking is that in frodos link is says that the hsync range for DIGITAL (which i am using) is 30-63. But since it doesnt say anything about this in the official manual i am gonna ignore this and use 30-81 (if you thinks this is a bad idea let me know).

I would like to thank you all for helping me and finish this post with one question :P
In the boot menu at pc startup ubunto is the default os to boot, i would like to change this to win2k, how do i do this?

---

### Post by ubuntme on 2005-08-30
/boot/grub/menu.lst contains the boot options.

There may be a nice way to do this, but if you move the windows lines to the top it will work.  Back up the file before hand though.

---

### Post by microbe on 2005-08-30
I found this thread as I am having a similar fight with a Samsung 700TFT. 

As regards the refresh rates and supported resolutions, the Windows driver for my screen (SM700TFT.INF) says:
```
......[700tft.AddReg]
HKR,"MODES\640,480",Mode1,,"30.5-45.0,58.0-85.0,+,+"
HKR,"MODES\800,600",Mode1,,"35.0-56.0,56.0-85.0,+,+"
HKR,"MODES\1024,768",Mode1,,"45.0-72.0,59.0-85.0,+,+"
HKR,"MODES\1152,864",Mode1,,"67.5-70.0,74.0-76.0,+,+"
HKR,"MODES\1280,1024",Mode1,,"61.5-80.0,59.0-76.0,+,+"
HKR,,ICMProfile,0,"sm700tft.icm".....
```

So I reckon this might be a good (best?) place to look for the details if you are migrating form Windows since you will probably have the right file for your screen stored on your Win system already.

---

### Post by pawnUz on 2005-08-30
[QUOTE=microbe]I found this thread as I am having a similar fight with a Samsung 700TFT. 

As regards the refresh rates and supported resolutions, the Windows driver for my screen (SM700TFT.INF) says:
```
......[700tft.AddReg]
HKR,"MODES\640,480",Mode1,,"30.5-45.0,58.0-85.0,+,+"
HKR,"MODES\800,600",Mode1,,"35.0-56.0,56.0-85.0,+,+"
HKR,"MODES\1024,768",Mode1,,"45.0-72.0,59.0-85.0,+,+"
HKR,"MODES\1152,864",Mode1,,"67.5-70.0,74.0-76.0,+,+"
HKR,"MODES\1280,1024",Mode1,,"61.5-80.0,59.0-76.0,+,+"
HKR,,ICMProfile,0,"sm700tft.icm".....
```

So I reckon this might be a good (best?) place to look for the details if you are migrating form Windows since you will probably have the right file for your screen stored on your Win system already.[/QUOTE]

Could you tell me exactly where and how you found this? Thanks :)

And thanks for the answer ubuntme.

---

### Post by Darigaaz on 2005-08-31
I've been having a similar problem, and just adding the HorizSync and VertRefresh lines (with the appropriate specs, in my case 31-80 and 60-75) fixed it. Thanks for the help. (I did a search a few days ago, but I must have missed the threads where that particular hint came up, and the rest of them sounded a bit more complicated than I wanted to deal with - I'm running Kubuntu Live right now, and I wasn't sure if there was a way to monkey with the driver and save it somewhere where Kubuntu would find it on boot.)

I think I'll just save my new xorg.conf file to a USB stick, copy it after booting, and <Ctrl><Alt><Backspace>. Won't have to bother with that once I set this up as a dual boot, but that's not a project I'm ready to try out yet - need to get a spare hard drive to make a backup first. (Yeah, I know, I should have been doing that all along. Hasn't come back to bite me yet [knock on wood], fortunately - and I at least have hardcopy of the most important stuff.)

---

### Post by STINGRAY on 2005-09-02
[QUOTE=frodon]It's a well known problem, all you have to do, i think, is to add the good (USE THE CONSTRUCTOR PARAMETERS OF YOUR SCREEN ... really important) refreshrate lines in the device section like that : ```
Section "Monitor"
	Identifier	"Écran générique"
	Option		"DPMS"
	HorizSync	28-70
	VertRefresh	43-160
EndSection
```Use the search field of the forum with resolution or refresh rate as keywords and you will find a lot of threads about that, all the answers are in this forum, just take the time to search  ;-) .
But if you still have problems just ask.[/QUOTE]

When I type"Section "Monitor" "it only says "bash:  section: command not found"!?

I need to set my screen resolution to sxga as well but knowing nothing about how to use the terminal and commands I tried following the above advice, but I can seem to get anywhere with it... :? Any suggestions, what I am doing wrong?

---

### Post by STINGRAY on 2005-09-03
^^^^^^Anyone please?

---

### Post by frodon on 2005-09-03
[QUOTE=STINGRAY]When I type"Section "Monitor" "it only says "bash:  section: command not found"!?

I need to set my screen resolution to sxga as well but knowing nothing about how to use the terminal and commands I tried following the above advice, but I can seem to get anywhere with it... :? Any suggestions, what I am doing wrong?[/QUOTE]The refresh rates lines (HorizSync and VertRefresh parameters) have to be added in your xorg.conf file in the monitor section, to open it use this command : ```
sudo gedit /etc/X11/xorg.conf
```When you have edited your xorg.conf file restart Xserver (Ctrl + Alt + Backspace).
Use the search field of the forum and you will find a lot a thread about that.

---

### Post by wolfchri on 2005-09-09
Folks, 

what exactly is the reason that Ubuntu installation does not offer the well known Monitor selection known from Yast, Mandriva, Anaconda etc.?

Why cant you choose your monitor from this list? It is very unfriendly to the user and driving beginners nuts when you tell them that they need to open the console and have to edit a strange looking config file.....

It are little things like that that keep deterring people from Linux  ](*,)

---

### Post by frodon on 2005-09-09
It's just a liitle "bug" of hoary, of course it's unfriendly to not have you screen well configured after a fresh install but i think the problem will be solved in the next release of ubuntu.

---

### Post by Freddie.Ruddick on 2005-10-01
[newbie alert]
Hi,

I, at present have a Windoze PC, and a second machine (Dell Optiplex GX270) onto which I have just installed Hoary Hedgehog. I had previously tried a Knoppix Live CD on the Dell, which worked, although only at 640*480. It wouldn't let me choose anything higher. The HH Live CD worked at 1024*768 on the Windoze PC, so I blamed the low resolution on the Knoppix disc and went ahead and installed HH on the dell. 

However, it still only displays at 640*480. I tried the procedure suggested by tseliot, deleting all resolutions except 1024*768and that worked upto the "/etc/init.d/gdm start" bit. This returns
```
Starting GNOME Display Manager                  [[COLOR="Red"]fail[/COLOR]].
```

Any insight? Xorg.conf correctly identified the graphics card/display.

Thanks

EDIT: Boy, do I feel stupid now?! 1 reboot later: lovely 1024*768 resolution! Thanks people.

---

### Post by ubuntujedi on 2005-10-07
hi .. I am having a similar resolution issue

my GUI is displaying in 1600x600 res for some resason.

I tried doing sudo nano /etc/X11/xorg.conf
to change res.. but when the file opened, it is blank! There is nothing to edit.

So how else can i change the resolution? :confused: 

I even reinstalled ubuntu from scratch, but to no avail!

Please help.

---

### Post by Abd-al-Karim on 2005-10-08
[QUOTE=ubuntujedi]hi .. I am having a similar resolution issue

my GUI is displaying in 1600x600 res for some resason.

I tried doing sudo nano /etc/X11/xorg.conf
to change res.. but when the file opened, it is blank! There is nothing to edit.

So how else can i change the resolution? :confused: 

I even reinstalled ubuntu from scratch, but to no avail!

Please help.[/QUOTE]
^^^ You can go to: System > Preferences > Screen Resolution. Its in the main menu  (at the top when you first install).

I had a similar problem not for my main resolution but for my graphical login screen resolution instead, so I edited my xorg.conf file as described in the beginning of this thread and now it works in my resoltuion (1024 x 768 instead of a higher one) :) thanks. But :rolleyes: now my font for typing in usernames and passwords is really small, its like the text is a higher resolution than the screen, this is not the case for the text at the bottom of the screen though like "Actions" etc. is all normal. Does any one know how to fix that? Thanks for any input.

---

