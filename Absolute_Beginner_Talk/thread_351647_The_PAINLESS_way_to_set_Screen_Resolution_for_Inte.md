---
title: "The PAINLESS way to set Screen Resolution for Intel Chipsets"
date: 2007-02-02
forum: Absolute Beginner Talk
---

### Post by ramjet_1953 on 2007-02-02
[CENTER][B]The Painless Way to Set-Up  Widescreen Laptops
 that have the Intel® 845-945 Graphics Chipets,
 Using 915resolution.[/B][/CENTER]

A major complaint from many Ubuntu &#8220;virgins&#8221; is that they have a great deal of difficulty in changing both the screen resolution and colour depth of their widescreen laptops.

My own experience was one of frustration and despair, which took several days to resolve, even with the excellent and willing help of several people on the forums.

Unfortunately, some of the advice was not as accurate as it could have been and on two occasions, after fiddling with the /etc/X11/xorg.conf file, my system was broken to the extent that I had to use  software in my Windows partition to recover the backed-up file, as I couldn't even get in to recover it from a console.

As is often the case, the solution was so simple, that I was gob smacked, when I finally worked it out!

Here is what you need to do:

1.Enable the extra repositories in Synaptic.
2.Using Synaptic, download 915resolution
3.In a console, type in    [COLOR="Blue"] sudo 915resolution -l[/COLOR]
4.You should get something like this:

roger@roger-laptop:~$ sudo 915resolution -l
Password:
Intel 800/900 Series VBIOS Hack : version 0.5.2

Chipset: 915GM
BIOS: TYPE 1
Mode Table Offset: $C0000 + $269
Mode Table Entries: 36

Mode 30 : 640x480, 8 bits/pixel
Mode 32 : 800x600, 8 bits/pixel
Mode 34 : 1024x768, 8 bits/pixel
Mode 38 : 1280x1024, 8 bits/pixel
Mode 3a : 1600x1200, 8 bits/pixel
Mode 3c : 1920x1440, 8 bits/pixel
Mode 41 : 1280x800, 16 bits/pixel
Mode 43 : 800x600, 16 bits/pixel
Mode 45 : 1024x768, 16 bits/pixel
Mode 49 : 1280x1024, 16 bits/pixel
Mode 4b : 1600x1200, 16 bits/pixel
Mode 4d : 1920x1440, 16 bits/pixel
Mode 50 : 1280x800, 32 bits/pixel
Mode 52 : 800x600, 32 bits/pixel
Mode 54 : 1024x768, 32 bits/pixel
Mode 58 : 1280x1024, 32 bits/pixel
Mode 5a : 1600x1200, 32 bits/pixel
Mode 5c : 1920x1440, 32 bits/pixel
Mode 60 : 512x771, 8 bits/pixel
Mode 61 : 512x771, 16 bits/pixel
Mode 62 : 512x771, 32 bits/pixel
roger@roger-laptop:~$ 

The ideal resolution and colour depth for my Acer TravelMate 4101 laptop is 1280X800 with a colour depth of 32 bits.

As you can see from the above, it is already listed as Mode 50. However in my case, if that mode is chosen in 915resolution, the system breaks badly. I'm not sure if this is universal, or not.

5.What you need to do is choose a mode which is further up the list and a resolution/depth that you'll never use (Mode 30 is ideal)
6.Type in a terminal  the resolution and colour depth that you want.  In my case I wanted 1280X800 at 32 bits/pixel. So I typed:
7.  [COLOR="Blue"]sudo 915resolution 30 1280 800 32[/COLOR]
8.The program comes back with confirmation that the new resolution has been patched to Mode 30, in this case.
9.Now all you have to do is to modify your /etc/default/915resolution file to correspond to the above patch.
10.In a terminal type: [COLOR="Blue"]sudo gedit /etc/default/915resolution[/COLOR]. You should get a screen like the one below:
#
# 915resolution default
#
# find free modes by  /usr/sbin/915resolution -l
# and set it to MODE or set to 'MODE=auto'
#
# With 'auto' detection, the panel-size will be fetched from the VBE
# BIOS if possible and the highest-numbered mode in each bit-depth
# will be overwritten with the detected panel-size.
[COLOR="Blue"]MODE[/COLOR]=AUTO
#
# and set resolutions for the mode.
# e.g. use XRESO=1024 and YRESO=768
[COLOR="Blue"]XRESO=
YRESO=[/COLOR]
#
# We can also set the pixel mode.
# e.g. use BIT=32
# Please note that this is optional,
# you can also leave this value blank.
[COLOR="Blue"]BIT=[/COLOR]

11.Now simply edit this file by changing MODE to the MODE that you selected. In this case it was MODE 30
12.Set [COLOR="Red"]XRESO=1280[/COLOR] (Or the Horizontal resolution that you selected)
13.Set [COLOR="Red"]YRESO=800[/COLOR] (Again set to whatever you selected earlier)
14.Set [COLOR="Red"]BIT=32[/COLOR] (Again to the colour depth you chose previously.)
15.Save the file and re-start.
16.The system should boot-up in the new mode and it should also appear as an option in the System>Preferences>Screen Resolution menu.

Enjoy! :D

---

### Post by i_dan on 2007-02-06
Thanks for a great post!

As a quick update, I installed 915resolution via
"sudo apt-get install 915resolution"
and it ran straight away,  replacing some of the modes.
Then I killed X "<CTL><ALT><BKSP>".
When gdm started, it was in 1280x800 (much clearer) but the desktop
was still at 1024x768 (blury).
I then went to "system->preferences->screen resolution"
and now 1280x800 was an option.  Chose it and all was well.

Just might be worth trying this first since it's abit cleaner.

Laptop: Amilo Pro v3205
intel 945GM chipset

---

### Post by emarkay on 2007-02-06
"This includes the 845G, 855G, and 865G chipsets, as well as 915G, 915GM, and 945G chipsets."

FYI, It apparently does not support the older I810 versions, like the I82810E DC-133 CGC.

---

### Post by dorcssa on 2007-02-06
Does it configure the frequency? A friend of my have this kind of laptop, and have this resolution problem (it will solved with this 915 resolution I hope), and there's only 60 Hz for frequency, no other options.

---

### Post by forrestgump on 2007-02-08
[http://ubuntuforums.org/showthread.php?p=2113867](http://ubuntuforums.org/showthread.php?p=2113867)

worked a charm for me

---

### Post by fi_ on 2007-02-11
Thank-you so much for this thread!

My first ubuntu (and first linux) installation was only a couple of days ago and I've been using the book 'Beginning Ubuntu Linux' by Keir Thomas. Although otherwise very good, it encourages running the x.org config program without first suggesting a backup and as I tried rerunning the util and then editing the file itself my errors increased until I gave up & reinstalled ubuntu again to restart with a clean slate.

Using I_Dan's suggestion of "sudo apt-get install 915resolution" seemed a less daunting first option and did the trick right away on my machine. The (restarted) laptop resolution had automatically corrected to 1280x800. My only refresh option was 60 but I'm unsure the inbuilt screen can use any higher. (PB's website has no info on this).

Laptop:  Packard Bell EASYNOTE GN45-032
Video Component:  Intel® Graphics Media Accelerator 950 (Chipset GMA950)

---

### Post by treesurf on 2007-02-21
Thanks for the heads up on 915resolution.  I installed it on my new Gateway laptop using aptitude, and it ran automatically.  I restarted and my resolution was set correctly for me.  Sweet!

Intel 950, by the way.

---

### Post by j0sh0 on 2007-02-21
Hi,
I've using a HiGrade MB02 notebook with 855gm graphics. When using 915resolution, it wont change the bpp when I select a different mode. For example, I've typed in "sudo 915resolution 3a 1024 768 32". As you can see from "915resolution -l", it changes the selected mode's resolution but not the bpp. 

Intel 800/900 Series VBIOS Hack : version 0.5.2

Chipset: 855GM
BIOS: TYPE 2
Mode Table Offset: $C0000 + $3c3
Mode Table Entries: 21

Mode 30 : 640x480, 8 bits/pixel
Mode 32 : 800x600, 8 bits/pixel
Mode 34 : 1024x768, 8 bits/pixel
Mode 36 : 1024x600, 8 bits/pixel
Mode 38 : 1280x1024, 8 bits/pixel
**Mode 3a : 1024x768, 8 bits/pixel**
Mode 3c : 1024x768, 8 bits/pixel
Mode 41 : 640x480, 16 bits/pixel
Mode 43 : 800x600, 16 bits/pixel
Mode 45 : 1024x768, 16 bits/pixel
Mode 47 : 1024x600, 16 bits/pixel
Mode 49 : 1280x1024, 16 bits/pixel
Mode 4b : 1024x768, 16 bits/pixel
Mode 4d : 1024x768, 16 bits/pixel
Mode 50 : 640x480, 32 bits/pixel
Mode 52 : 800x600, 32 bits/pixel
Mode 54 : 1024x768, 32 bits/pixel
Mode 56 : 1024x600, 32 bits/pixel
Mode 58 : 1280x1024, 32 bits/pixel
Mode 5a : 1024x768, 32 bits/pixel
Mode 5c : 1024x768, 32 bits/pixel

Even editing /etc/default/915resolution makes no difference!

Please can someone help me, this resolution problem is the only thing keeping me from being completely satisfied with ubuntu!

Cheers,

j0sh0

---

### Post by ramjet_1953 on 2007-02-21
Try re-mapping it to mode 30.

Regards

Roger

---

### Post by wat3r on 2007-02-22
This worked really well for me! Thank you so much for this howto :)

---

### Post by Ben Sprinkle on 2007-02-22
Should go in the howto section, thanks fir the info. I got an Intel 900 chipset. :)

---

### Post by Troubled on 2007-02-22
Well, after using this in combination with a reconfigure of xorg, I managed to get my resolution, but upon changing it, my system crashes rather badly, and besides, my refresh rate is stuck at 60 Hz. Anyone else having these problems?

---

### Post by jis on 2007-02-23
I have Mobile Intel 910GML Express chipset in my laptop and it works fine in the laptop's native resolution 1280x800 without 915resolution in Xubuntu 6.10, if no external monitor is connected. However, I installed the package because I thought it would help to set resolution, if I use an external monitor. Well, it didn't. And 915resolution recognizes the chipset as 915GM, not 910GML Express. The external CRT monitor I tried it with is MAG DJ707, that has specifications HorizSync 30-70 kHz, VertRefresh  50-120 Hz. For Windows XP it works in many resolutions such as 1152x864 32 bit 75Hz, but such a mode is not in the list of modes displayed by 915resolution -l. The upsplash is fine, login screen displays, but not in optimal mode, and after login there is only a blank screen..

---

### Post by jis on 2007-02-23
Well I can put the resolution mentioned in the previous message to the list like ramjet_1953 suggests in step 7, and I can change that resolution to /etc/default/915resolution, but that does not change the fact that my external screen becomes blank after gaphical login. It used to work with another CRT without 915resolution.

---

### Post by stuntant on 2007-02-23
I have done this and I can get the resolution I want 1440x900 to show but it does not display properly on the monitor, the top 1/4 is unusable? Has anyone run into this?, and fixed it.

---

### Post by jis on 2007-02-23
If you edit /etc/deafult/915resolution do you set e.g. 'MODE 30' or '30' instad of 'AUTO'?

P.S. In /usr/share/doc/915resolution/README.Debian it is told to use just the number of the mode in the file. Anyway, it didn't work with my external monitor.

---

### Post by stuntant on 2007-02-23
I changed it to the mode i set. That is how I got it to show up. It wasn't showing before that. I tried with 30, 38 and 58. 

What's wierd is that ubuntu says it is set to 1440x900 but the monitor information says it is 1280x1024. I am thinking maybe I should just get a video card...

---

### Post by DaveT on 2007-02-23
Hi.

Im running a Sony Vaio VGN-FS115E (intel 915GM Express) with a native resolution of 1280 x 800.

currently im running in 1024 x 768, and 'Display Settings' just states 'Default' as the only option.

i seem to be having a problem in that no matter what changes I make in xorg.conf/915resolution, im still left with Default as the only option.

xorg.0.log refers to pipe A and pipe B, im assuming that these are the outputs (1 being the LFP the other being the external connecter (unused). Im wondering if my settings are being applied to the wrong pipe.

is there anyway to set up such things as i xorg doesnt seem to cover it (that i can find anyway).

Great post BTW.

DaveT

---

### Post by stuntant on 2007-02-23
so i did buy a cheap nvidia graphics card and the difference is amazing. it was definitely worth the $40, and the nv driver seems to work great.

oh a tip for people messing with graphics. If you screw your settings up and get the xorg error window and don't get the command prompt, restart and hit escape. You will get some options on how to start and can start it in a mode (I forgot the exact terminology, it was the second one down)  that will allow you to log in and fix your mistakes. You should just be able to use the up arrow to recall commands you've already used. If you don't the followiung command will give you options to reset your xorg configuration.

 sudo dpkg-reconfigure -phigh xserver-xorg

for intel graphics select i810.

Now I am on to installing Java :)

---

### Post by jis on 2007-02-24
stuntant, can't you use e.g. Ctrl-Alt-F1 to get to console, Ctrl-Alt-Backspace to restart X, Ctrl-Alt-F7 to get back to X?

---

### Post by gurgle on 2007-02-28
cant get this to output 1680x1050. Monitor is working fine in Win XP. 

Intel 800/900 Series VBIOS Hack : version 0.5.2

Chipset: 915G
BIOS: TYPE 1
Mode Table Offset: $C0000 + $269
Mode Table Entries: 27

Mode 30 : 1680x1050, 8 bits/pixel
Mode 32 : 800x600, 8 bits/pixel
Mode 34 : 1024x768, 8 bits/pixel
Mode 38 : 1280x1024, 8 bits/pixel
Mode 3a : 1600x1200, 8 bits/pixel
Mode 3c : 1920x1440, 8 bits/pixel
Mode 41 : 1680x1050, 16 bits/pixel
Mode 43 : 800x600, 16 bits/pixel
Mode 45 : 1024x768, 16 bits/pixel
Mode 49 : 1280x1024, 16 bits/pixel
Mode 4b : 1600x1200, 16 bits/pixel
Mode 4d : 1920x1440, 16 bits/pixel
Mode 50 : 1680x1050, 32 bits/pixel
Mode 52 : 800x600, 32 bits/pixel
Mode 54 : 1024x768, 32 bits/pixel
Mode 58 : 1280x1024, 32 bits/pixel
Mode 5a : 1600x1200, 32 bits/pixel
Mode 5c : 1920x1440, 32 bits/pixel


#
# 915resolution default
#
# find free modes by  /usr/sbin/915resolution -l
# and set it to MODE or set to 'MODE=auto'
#
# With 'auto' detection, the panel-size will be fetched from the VBE
# BIOS if possible and the highest-numbered mode in each bit-depth
# will be overwritten with the detected panel-size.
MODE=30
#
# and set resolutions for the mode.
# e.g. use XRESO=1024 and YRESO=768
XRESO=1680
YRESO=1050
#
# We can also set the pixel mode.
# e.g. use BIT=32
# Please note that this is optional,
# you can also leave this value blank.
BIT=24

---

### Post by themysteriouscharacter on 2007-03-01
You have saved my life. Thank you!

---

### Post by Soglad on 2007-03-04
Hey guys, I'm a COMPLETE noob to Ubuntu and I've just installed it and I've this problem. I cannot seem to find "915resolution" in the Synaptic program. I've downloaded the 915resolution from a website but have NO idea how to install or use.

PLEASE HELP!! :P

---

### Post by ramjet_1953 on 2007-03-04
Hi, Solgad!

You need to enable the extra repositories in Synaptic.

To do this follow there directions:

1. Click on System>Administration>Synaptic Package Manager

2. If prompted to enter your password, do so (Your Admin Password)

3.Click on Settings>Repositories

4. A window will open and offer you the opportunity to click on the boxes to make the other repositaries available. Do so.

5. While you are there, click on the drop-down menu for "Download From" and see if there is a server close to your home location. If so, choose it.

6. Close the window.

7. You should now be able to do a search for 915resolution and use Synaptic to install it.

Enjoy!

Regards,
Roger :cool:

---

### Post by Soglad on 2007-03-05
> **ramjet_1953 said:**
> Hi, Solgad!

You need to enable the extra repositories in Synaptic.

To do this follow there directions:

1. Click on System>Administration>Synaptic Package Manager

2. If prompted to enter your password, do so (Your Admin Password)

3.Click on Settings>Repositories

4. A window will open and offer you the opportunity to click on the boxes to make the other repositaries available. Do so.

5. While you are there, click on the drop-down menu for "Download From" and see if there is a server close to your home location. If so, choose it.

6. Close the window.

7. You should now be able to do a search for 915resolution and use Synaptic to install it.

Enjoy!

Regards,
Roger :cool:

I LOVE YOU!

Thanks, haha

Dav

---

### Post by gurgle on 2007-03-06
any ideas as to why I cant get 1680x1050 on my config?

---

### Post by tralfmordian on 2007-03-06
Hello! Complete noob here. I have followed the instructions precisely on my laptop, and here's where I stand:
I am using a gateway 3520gz laptop, with a intel 855gm chipset. (I know nothing about hardware), but the "video chipset" is "Intel Extreme 2 Integrated Graphics," if that matters. 

My computer has a maximum resolution of 1280 X 768, 32 bit, 60hz.

I was successful in downloading and installing 915resolution, and I was able to get all the way to changing the default to "mode=30", with the resolutions set to what they should be as well. Here is what it looks like as I have pulled it up now (after multiple restarts.):

#
# 915resolution default
#
# find free modes by  /usr/sbin/915resolution -l
# and set it to MODE or set to 'MODE=auto'
#
# With 'auto' detection, the panel-size will be fetched from the VBE
# BIOS if possible and the highest-numbered mode in each bit-depth
# will be overwritten with the detected panel-size.
MODE=30
#
# and set resolutions for the mode.
# e.g. use XRESO=1024 and YRESO=768
XRESO=1280
YRESO=768
#
# We can also set the pixel mode.
# e.g. use BIT=32
# Please note that this is optional,
# you can also leave this value blank.
BIT=32


As you can see, I'm pretty sure I've set everything correctly, and when I perform the command "sudo 915resolution -l" in a terminal, it does show that Mode 30 is set to 1280X768, with 32 bits.

Here's the problem: I've rebooted a couple times, and my resolution is still where it started, which is 1024 X 768. I've gone to the screen resolution settings under "system," and it only gives me the option of 1024 X 768, or 800 X 600.

I'm new to forums, and Linux, so I hope this is in the right place, and that I haven't missed anything in the forums - I've searched extensively. Any and all help would be greatly appreciated. Thanks!

---

### Post by higgylm on 2007-03-06
Thank you very much, solved my problem, very usefull info, cheers

---

### Post by tralfmordian on 2007-03-07
Okay, this is sick. While hoping for help, I have realized that I have probably devoted around 20 hours to trying to get my display to go from 1024 X 768 --> 1280 X 768. When do I decide that I've done enough searching, and that there is no solution to my problem? I've gone to more forums than I can count searching threads, and looked all over the internet, and have not been able to find any reasonable solution to this...and I haven't even begun to figure out why my speakers don't work yet. 
I know, I'm whining, but seriously, do any of you experienced users say "enough's enough" and move on? I'm about ready to just accept my funky looking screen and just start doing something more productive with my newly installed Ubuntu.  With that, if anyone out there has any other suggestions of how to even *search* for an answer to my woes, please advise, it would be greatly appreciated.

---

### Post by ramjet_1953 on 2007-03-07
OH, try this.

Go back to tors and and run 915resolution again, going through all of the steps and this time specify 24 bit depth.

Regards,
Roger :cool:

---

### Post by dotman on 2007-03-07
I came across this on the forums and it worked for me:

[http://www.ubuntuforums.org/showpost.php?p=2058945&postcount=14](http://www.ubuntuforums.org/showpost.php?p=2058945&postcount=14)

---

### Post by tralfmordian on 2007-03-07
Ok, so that was interesting. When I set the bit depth to 24, something at least changed, albeit not for the better...it changed to a (kinda) higher resolution, but was still messed up - the page carried over in a way that made the left side of the screen part of the right side of the desktop. Oh yeah, it was also black and white mostly.

So then I tried out what dotman suggested with the link he provided, and saw that the suggested package (xserver-xorg-video-intel) was already installed, So I uninstalled 915resolution, reinstalled the above new package, and tried to find a place to change in the "xorg.conf to intel (from i810)" as the post suggested. In looking at my xorg.conf file, I found no place showing i810 to be changed...

Thank you so much for your suggestions so far. Sadly, I was happy even when one of them just changed something, even if it didn't do what it was supposed to.

Here's one other thing. I noticed I have an xorg.conf file, but I also have an xorg.conf_easyubuntu file, so just out of curiosity, I took a look at that. What I found is that in the xorg.conf file, all of the stuff (that I'm ignorant about) is generic, but in the xorg.conf_easyubuntu file it specifies my graphics card, and shows the driver under "device" as i810 - which is what I was looking for to change to "intel" from the other suggestion.

So what the difference between these two files? ( I found that one is read only (easyubuntu) and the other one I'm assuming is the only one that actually controls this stuff? 

Sorry for the long post, if anyone wants me to post these .conf files, let me know. Thanks a ton again.

---

### Post by tralfmordian on 2007-03-07
I did something good! In my last post I mentioned how there were correct (looking) settings in the xorg.conf_easyubuntu file? I decided to copy most of those into the actual xorg.conf file, and that seemed to do the trick. My screen looks SOOOOO much better now. Crisp and Clear. I am very happy, now that I have overcome my first big Linux hurdle. Still don't know what the difference was between those 2 files though? 

Thank you to everyone for all their help with this. Now to get my sound working!

---

### Post by cbutters on 2007-03-07
Thanks Ramjet, this worked for me after hours of trouble.

---

### Post by dotman on 2007-03-07
tralfmordian,

EasyUbuntu is a program similar to automatix that automates package installation and configuration for some of the more challenging, but necessary programs/utilities/drivers. Since it does support the nvidia and ati drivers, perhaps one of those was accidentally installed and it created a custom xorg.conf or replaced the existing one or maybe it just puts it in /etc/X11 for future use. Either way, its good to hear that everything is working well for you.

---

### Post by mekkah on 2007-03-07
This is so funny! I did EXACTLY like you described and it work somewhat. One problem left for me to tackle:

When i applied the patch (sudo 915resolution 30 1280 800 32) & editet 915resolution to match it, i pressed "ctrl+alt+backspace" and got back to the login screen. It was i perfect resolution. I logged in, still perfect resolution. But if i restart the entire computer, everything dissapears & i have to start over again.

As long as i just run the patch for a terminal & restart gnome, everything works fine but how do i keep it so i don't have to do the entire thing over again each time i restart my laptop?

---

### Post by ramjet_1953 on 2007-03-08
Hi, Mekkah!

Did you edit the edit the /etc/default/915resoltion file, as I mentioned at the end of the how-to?

code:

[COLOR="Red"]sudo gedit /etc/default/915resolution[/COLOR]

Regards,
Roger :cool:

---

### Post by tm0054 on 2007-03-08
Thanks for the great info! It's exactly what I was looking for... I simply installed the file and rebooted. All is fixed! 1024x768 is UGLY on a widescreen!

---

### Post by tralfmordian on 2007-03-08
> **dotman said:**
> tralfmordian,

EasyUbuntu is a program similar to automatix that automates package installation and configuration for some of the more challenging, but necessary programs/utilities/drivers. Since it does support the nvidia and ati drivers, perhaps one of those was accidentally installed and it created a custom xorg.conf or replaced the existing one or maybe it just puts it in /etc/X11 for future use. Either way, its good to hear that everything is working well for you.

Thanks dotman. I'm very happy too that it's working better. I think I got a little over-zealous and started to fool around with getting beryl installed after, and I completely lost my ability to load the gui. Good for me, that as a complete noob, I had to learn enough about the command line to know how to go back to my xorg file and fix it again...I was very proud of myself! :) I guess people really mean it when they suggest backing files like that up, seems to make sense!

---

### Post by richwales on 2007-04-02
I've tried 915resolution on a Dell Optiplex GX280, with a builtin Intel 915G-based video adaptor and a Dell monitor capable of 1680x1050.

I can get Ubuntu (Feisty) to select 1680x1050, but the monitor continues to show only 1280x1024; material that should be on either the left or right of the screen is not shown.

Any ideas?

---

### Post by bekirserifoglu on 2007-04-05
i have the same probelm with mekkah. after the restart everything goes. i think i have to put it somewhere in x start but i dono how. but i am sure i have done everything you said. plz help!!!

---

### Post by STREETURCHINE on 2007-04-05
> 10.In a terminal type: sudo gedit /etc/default/915resolution. 

for all graphical application you should use gksudo

```
gksudo gedit /etc/default/915resolution
```

---

### Post by qbnronin on 2007-04-06
> **bekirserifoglu said:**
> i have the same probelm with mekkah. after the restart everything goes. i think i have to put it somewhere in x start but i dono how. but i am sure i have done everything you said. plz help!!!
bekirserifoglu I also had your and same problem. I was able to solve it after many hours of trying. My solution might be complex. I would first back up my xorg.conf file then use "sudo gedit /etc/X11/xorg.conf" and change the monitor and screen resolutions. In my case I used the following:

Section "Monitor"
  identifier "Generic Monitor"
  vendorname "Plug 'n' Play"
  modelname "Plug 'n' Play"
  modeline "1440x900@60.00" 106.47 1440 1520 1672 1904 900 901 904 932 -HSync +Vsync
  gamma 1.0
EndSection

Section "Screen"
  Identifier "Default Screen"
  Device "Generic Video Card"
  Monitor "Generic Monitor"
  DefaultDepth 24
  SubSection "Display"
    depth 24
    modes "1440x900@60"
  EndSubSection
EndSection

Hope the above helps.

Hope the following doesn't confuse most.
Now, I confess that I also used "dburnett77" solution for problems with the Intel 945 chipset. :
     "I saw somewhere to download the newer driver "xserver-xorg-video-intel" via Synaptic. I then changed the entry in xorg.conf in the Driver section from "i810" to "intel", and I got all the resolutions I needed, plus the correct refresh rates. "

---

### Post by qbnronin on 2007-04-06
> **stuntant said:**
> I have done this and I can get the resolution I want 1440x900 to show but it does not display properly on the monitor, the top 1/4 is unusable? Has anyone run into this?, and fixed it.

Addendum to my last reply.
I also forgot to mention, being that I am a total newbie, that I had to wrong hardware configured. To check this, I went through System Settings/Monitor & Display/Hardware (tab) then change to Administrator Mode to make modifications to hardware selected.

Over and out! :-)

---

### Post by Markp.com on 2007-04-08
Hello there! First, thank you for getting me half way there! :)

I have an acer travelmate 4020 laptop. It has the intel graphics chip set. The screen died a while ago, so I am trying to set it up as a mini media centre for the living room.

It is connecting to a Dell LCD TV 26", which has the strange resolution of 1280x768.

When I enable this via the steps above, it works for the Y, but for the X, the screen has two thick black borders and half the screen is missing.

See the attached screen shots:
1024x768
[[IMG]http://img180.imageshack.us/img180/2368/dscf0002qb6.th.jpg[/IMG]](http://img180.imageshack.us/my.php?image=dscf0002qb6.jpg)

1280x768
[[IMG]http://img443.imageshack.us/img443/2042/dscf0004uz0.th.jpg[/IMG]](http://img443.imageshack.us/my.php?image=dscf0004uz0.jpg)

(Ignore the picture in picture, I was watching some tv!)

I'm new to Linux (aren't most posters here!) :) So any help would be great! 

Thanks,
Mark

---

### Post by kornhead127 on 2007-04-12
> **jis said:**
> I have Mobile Intel 910GML Express chipset in my laptop and it works fine in the laptop's native resolution 1280x800 without 915resolution in Xubuntu 6.10, if no external monitor is connected. However, I installed the package because I thought it would help to set resolution, if I use an external monitor. Well, it didn't. And 915resolution recognizes the chipset as 915GM, not 910GML Express. The external CRT monitor I tried it with is MAG DJ707, that has specifications HorizSync 30-70 kHz, VertRefresh  50-120 Hz. For Windows XP it works in many resolutions such as 1152x864 32 bit 75Hz, but such a mode is not in the list of modes displayed by 915resolution -l. The upsplash is fine, login screen displays, but not in optimal mode, and after login there is only a blank screen..

I'm having this same problem.

I log in, it splashes, the three little icons do their thing and then it turns all white. Also when I change the bpp it stays at 8 bpp. I've tried patching to different modes but to no avail. My next step is to install the latest xserver-xorg-video-intel

-=]Rob Swift[=-

p.s. I'm running a 82865G or 865G

---

### Post by badduck on 2007-04-19
Nice guide to set up the resolution.

My problem is that I am having a 845G graphic chipset, thus at install I got the lowest resolution (640*480) and I cant change it.

I did follow your step to step installation guide, but it didnt help me.

One strange this was that when I wrote "915resolution" in the terminal, I didnt get all the different mode attributes. But I followed the one from your instructions and did change the text file in the end.

But I still have the lowest resolution. By the way, I am using a Dell optiplex SX260.

Does anyone know what I need to do to fix it?

---

### Post by wladston on 2007-04-23
Thanks for the post. It was the resource that saved me!

One queston : what has been done to ensure that future users won't have this problem ?

I have just sent an email to Intel asking for support on this case. Let's hope they'll release a new Video Bios that will get the cards back to a working state.

---

### Post by ramjet_1953 on 2007-04-23
Badduck, when you typed in the screen what exactly did you type?

It should be : sudo 915resolution -l

Exactly as above, no quotations and yes, the"-l" is VERY NESESSARY.

Regards,
Roger 8-)

---

### Post by wieman01 on 2007-04-23
Is this the same approach for Feisty? I have got a Sony Vaio with Dapper and plan on upgrading to Feisty. Just not sure about the (widescreen) resolution issue. Advice would be appreciated.

---

### Post by ramjet_1953 on 2007-05-08
For Feisty 7.04 users, try the new Intel driver instead of 915resolution.

[COLOR="Red"]sudo apt-get install xserver-xorg-video-intel[/COLOR]

After install, re-boot and all should be great.

I can't confim this, but I believe this driver supports the newer Intel graphics chips that 915resolution didn't.

The other advantage is that it's a no-brainer.

Regards,
Roger 8)

---

### Post by Markp.com on 2007-05-08
> **ramjet_1953 said:**
> For Feisty 7.40 users, try the new Intel driver instead of 915resolution.

[COLOR="Red"]sudo apt-get install xserver-xorg-video-intel[/COLOR]

After install, re-boot and all shoul be great.

I can't confim this, but I believe this driver supports the newer Intel graphics chips that 915resolution didn't.

The other advantage is that it's a no-brainer.

Regards,
Roger 8)


Thanks for this Roger! I'll try it this evening!

---

### Post by Go2doug on 2007-05-08
> **ramjet_1953 said:**
> For Feisty 7.04 users, try the new Intel driver instead of 915resolution.

[COLOR="Red"]sudo apt-get install xserver-xorg-video-intel[/COLOR]

After install, re-boot and all should be great.

I can't confim this, but I believe this driver supports the newer Intel graphics chips that 915resolution didn't.

The other advantage is that it's a no-brainer.

Regards,
Roger 8)

I am experiencing the "Ubuntu Noobie Intel945 Blues"; it seems to be a rite of passage for many here.

I tried the 915resolution instructions in the first post of this thread; I was unsuccessful.

When I ran the command you recommended, the output is:

```
Reading state information... Done
You might want to run `apt-get -f install' to correct these:
The following packages have unmet dependencies:
  j2re1.4-mozilla-plugin: Depends: j2re1.4 but it is not going to be installed
  xserver-xorg-video-intel: Conflicts: xserver-xorg-video-i810 (< 2:1.9.91-1) but 2:1.7.4-0ubuntu1 is to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).
```


Any suggestions? I am using Kubuntu 7.04. Thanks.

---

### Post by Go2doug on 2007-05-08
I ran "sudo apt-get -f install" and apparently it finished installing some apps that had not completed. I was then successfully able to run "sudo apt-get install xserver-xorg-video-intel". After a reboot I could adjust the resolution to 1280x800...cool.

---

### Post by jrodri on 2007-05-11
I have a Acer Travelmate 4002WLCi that came with the intel chip. This tutorial work very fine for me. the resolution problem was killing me... Thanks a lot

---

### Post by Korrontean on 2007-05-16
Thank you VERY much, Ramjet.

I was installing Ubuntu on a friend's Dell laptop and it worked perfectly. I wish I had had your post when I installed Ubuntu on my laptop. Setting the resolution was SUCH a big pain. It -almost- discouraged me from switching to Linux.

THANKS AGAIN! great post :)  :)  :)  :)  :)  :)  :)

---

### Post by Korrontean on 2007-05-16
Ah, my computer is an Acer 3500. My friend's is a Dell Inspiron 1300.

So if you have any of these, go ahead and install 915resolution, following the steps mentioned by Ramjet.

Your Ubuntu will finally look perfect.

---

### Post by Simran on 2007-05-20
Great guide. It solved my problem in no time :)

thanks

   Simran

---

### Post by Wolftastic on 2007-05-24
i'm brand new to ubuntu and i followed these directions for my dell xps m140 and it works great now. thanks ramjet, for making my hours of searching worth it!

---

### Post by wowshailen on 2007-05-25
Hi,

I am new to Ubuntu Feisty. I have a Dell Optiplex 170L with an Intel 865g graphics card. The 915resolution seemed to be right for me, but when i tried what it says, i cant get any new resolution i choose.  

When i first loaded Ubuntu via the Live CD, it was a 1280*768 which didnt display correctly.

800*600 display well, but the fonts are too big and wiedly.  I actually want 1280 * 1024 (mode 58). I edited the text file required but still, the resolution does not appear in the screen resolution list in synaptics.

Any suggestions, or an alternate method to solve this problem.

Regards, 

Shailen.

---

### Post by howardroark on 2007-05-27
Hey, I did exactly as you said. It worked fine. But when i restart it's just like the old one. i went to System>Preferences>Screen Resolution and the resolution i had installed isn't even there. mine intel 855g.

---

### Post by phil_71204 on 2007-06-05
Please please help, I am trying to get the resolution right since days now! ](*,)](*,)](*,)

I've tried tons of stuff, apart from the 915resolution I gave xserver-xorg-video-intel and xserver-xorg-video-i810 several tries without any success. then again, I'm not exactly the linux-man...maybe I missed out on something?


my machine: dell optiplex sx280 with 'Intel 915G Express' graphics adapter running ubuntu 7.04 with all updates done
screen: philips 220ws8 with default resolution 1680x1050

I installed the 915resolution pkg and set the new resolution according to ramjet-1953's guide:
sudo 915resolution 30 1680 1050 32

so that when I type:
sudo 915resolution -l
the following is output:

-------------------------------------

Intel 800/900 Series VBIOS Hack : version 0.5.2

Chipset: 915G
BIOS: TYPE 1
Mode Table Offset: $C0000 + $269
Mode Table Entries: 27

Mode 30 : 1680x1050, 32 bits/pixel
Mode 32 : 800x600, 8 bits/pixel
Mode 34 : 1024x768, 8 bits/pixel
Mode 38 : 1280x1024, 8 bits/pixel
Mode 3a : 1600x1200, 8 bits/pixel
Mode 3c : 1920x1440, 8 bits/pixel
Mode 41 : 1680x1050, 16 bits/pixel
Mode 43 : 800x600, 16 bits/pixel
Mode 45 : 1024x768, 16 bits/pixel
Mode 49 : 1280x1024, 16 bits/pixel
Mode 4b : 1600x1200, 16 bits/pixel
Mode 4d : 1920x1440, 16 bits/pixel
Mode 50 : 1680x1050, 32 bits/pixel
Mode 52 : 800x600, 32 bits/pixel
Mode 54 : 1024x768, 32 bits/pixel
Mode 58 : 1280x1024, 32 bits/pixel
Mode 5a : 1600x1200, 32 bits/pixel
Mode 5c : 1920x1440, 32 bits/pixel

----------------------------------

I then edited /etc/default/915resolution:

#
# 915resolution default
#
# find free modes by  /usr/sbin/915resolution -l
# and set it to MODE or set to 'MODE=auto'
#
# With 'auto' detection, the panel-size will be fetched from the VBE
# BIOS if possible and the highest-numbered mode in each bit-depth
# will be overwritten with the detected panel-size.
MODE=30
#
# and set resolutions for the mode.
# e.g. use XRESO=1024 and YRESO=768
XRESO=1680
YRESO=1050
#
# We can also set the pixel mode.
# e.g. use BIT=32
# Please note that this is optional,
# you can also leave this value blank.
BIT=32

----------------------------------------

I restart and some three or so times the screen went black saying it cannot support the resolution or something. the last time I tried just nothing happens, no change, screen res. stays 1024x768...:cry:

do I need to change the xorg.conf, if yes, then how exactly? my attempts always resulted in the same black screen complaining about a wrong res...

thank you for any attempt to help!!

---

### Post by brimedd on 2007-07-05
This was very hard for me as I did NOT use the i815 driver I tried to use Intel i8xx i9xx. Once I went into synaptic and changed it to i815 rebooted and BOOM it worked. Of course I had done all of the settings in the first post of this thread.

Also, I did have to use 1280x1024 because 1600x1200 would not display properly even adjusting the monitor settings manually. 

Thanks SO MUCH for all the help everyone! :D

---

### Post by thecure on 2007-07-19
On my wifes laptop, Dell E1705, with Intel 945GM chipset, never could get 1440 x 900 resolution by following any of the threads and the countless reconfiguring of xorg. That is to say until just a few seconds ago I decided to check synaptic for anything with intel and xorg. I noticed that the xserver-xorg-video-intel was a later version than the i810 driver that was installed. I clicked on it and it of course said it was going to uninstall the i810 driver and I figured what the heck I've reconfigured xorg a few hundred times from command line. I installed the driver and rebooted. Boom... my screen went straight to 1440x900 without any reconfiguring! Now that was the easiest fix ever.

---

### Post by bme on 2007-07-19
915resolution is a HACK...I installed "xserver-xorg-video intel" instead using synaptic.
Upon reboot there was no need for me to set the resolution,It was set at 1280x800 by default...

---

### Post by thecure on 2007-07-19
> **bme said:**
> 915resolution is a HACK...I installed "xserver-xorg-video intel" instead using synaptic.
Upon reboot there was no need for me to set the resolution,It was set at 1280x800 by default...

Perhaps I wasn't clear. (That's what I did... installed xserver-xorg-video-intel) On reboot my resolution was fixed.

---

### Post by bme on 2007-07-19
thecure,
yes I understood your post.....
I am responding to the thread in general as the suggestion of 915res is indicated in the title....not in particular to any post....
cheers....

---

### Post by tblehr on 2007-07-20
I have an Envision H193Wk 19" widescreen 1440x900 i'm trying to get working.  I use an old MS-6215 barebones system I picked up.  It has a i815E chipset, i'm not positive what the video chip is, but I know it's an Intel.  I've tryed using the 915resolution method, but this is the error I get when I type *915resolution -l*.

[I]Intel 800/900 Series VBIOS Hack : version 0.5.2

Intel chipset detected.  However, 915resolution was unable to determine the chipset type.
Chipset Id: 11308086
Please report this problem to [email]stomljen@yahoo.com[/email][/I]

Has anyone ever seen this?  I've tryed searching the forum and even googled it and couldn't find anything.

Any help would be great!

---

### Post by wmecity2729 on 2007-07-21
:) Hi, I try your method. However, when restart back, the screen become blank at user name and password.
    It is still running, not hanging or anything, but cannot see the screen.
   
    I try to run under recovery to undo the resolution setting but do not know the proper sudo command.
    I try sudo gedit /etc/default/915resolution under recovery screen, but the instruction not supported.

    Could you inform the proper sudo command for the recovery screen.

    Thanks.

---

### Post by rahul_bhise on 2007-07-21
i also have a same problem.
the system is still running (as i can hear the startup jingle) but the screen went blank.
i want to undo what i did in915resolution.

---

### Post by xubu_caapn on 2007-07-23
I followed directions.

First I tried the "1920x1440" setting, then I tried the "1600x1200" setting, both 32. It did nothing, both showed "1024x768" resolution still. When I go to change settings, "1024x768" is no longer there, replaced by "Default". I then replaced i810 drivers with the xserver-xorg-video intel, and still no difference (however, more "1024x768" is an option now, but it is same as "Default"). I have a intel 945gm video card. What is the problem? Why will it not budge from 1024x768?

---

### Post by dustrho on 2007-07-24
> **ramjet_1953 said:**
> For Feisty 7.04 users, try the new Intel driver instead of 915resolution.

[COLOR="Red"]sudo apt-get install xserver-xorg-video-intel[/COLOR]

After install, re-boot and all should be great.

I can't confim this, but I believe this driver supports the newer Intel graphics chips that 915resolution didn't.

The other advantage is that it's a no-brainer.

I tried the original suggestion you made with the 915resolution, and after making all the manual changes that didn't work for me. Then I came across this post of yours regarding the xserver-xorg-video-intel, and that worked like a champ! With the default Ubuntu installation I had 1280x1024, which is what the Intel 82865G Integrated Graphics Controller, but the refresh rate was at 75mhz which is too high for me. I wanted it to be 60mhz if possible, and after installing this new video driver I can get it set to that. SWEET!

Thank you SO much for the suggestion! This is why I love Ubuntu, people helping people.

---

### Post by Nudgeworth on 2007-07-31
THANk YOU, THANK YOU TAHNK YOU>

 Your instrustions were easy to understand to Console NOOB like me. 
 I was following another set of instructions, and it left out information that was important. Sudo is needed before "every" command. 

 Once again THANK YOU :)

---

### Post by Nudgeworth on 2007-07-31
feck, it only worked until i restarted ubuntu. now the 915resolution instructions don't work..
 time to do some reading

---

### Post by Nudgeworth on 2007-07-31
Yay a new driver!

---

### Post by mordani on 2007-08-16
Here is something interesting that I did. I downloaded 915resolution and my laptop (Dell Inspiron 1420)  had the correct resolution of 1440x900 (Exactly what I wanted). However, the desktop effects were not working no matter what I did. 

Eventually I figured that the driver entry was not updated in /etc/X11/xorg.conf and the device entry was still ¨vesa¨. I changed this to ¨i810" and then the enabled desktop effects - now it works perfectly !!

~Rohit

---

### Post by tyggna1 on 2007-08-16
Anyone know if this will work on a  Intel 830MP chipset?  Nevermind- I'm using an old ATI card for Video, on an intel motherboard--no wonder I have graphics card issues--my motherboard and video card don't get along.

---

### Post by zachalekos on 2007-09-26
[QUOTE=i_dan;2113737]Thanks for a great post!

As a quick update, I installed 915resolution via
"sudo apt-get install 915resolution"
and it ran straight away,  replacing some of the modes.
Then I killed X "<CTL><ALT><BKSP>".
When gdm started, it was in 1280x800 (much clearer) but the desktop
was still at 1024x768 (blury).
I then went to "system->preferences->screen resolution"
and now 1280x800 was an option.  Chose it and all was well.

Just might be worth trying this first since it's abit cleaner.

Laptop: Amilo Pro v3205
intel 945GM chipset[/QUOTE/]

Worked a charm

---

### Post by elastigirl on 2007-09-30
Such a useful post! Worked like a charm for me. I am using the ACER Aspire 1640.

THANK YOU for the perfect insrtuctions :-)

---

### Post by CaptainStabbin on 2007-10-02
Here is a little shortcut I found on [http://roland-lopez.blogspot.com/2007/03/auto915resolution-ubuntu-resolution-fix.html](http://roland-lopez.blogspot.com/2007/03/auto915resolution-ubuntu-resolution-fix.html)

This will do all the work of 915Resolution without the pain! 

I am copying the relevant instructions below

[INDENT] **auto915Resolution** - Ubuntu Resolution fix for Intel chipset 8x-945

If you have an Intel Chipset 8x - 945 series you will have some trouble setting your resolution in Ubuntu.
Theres is a tool, made by Steve Tomljenovic, called 915Resolution that will fix this problem. However you will have to run this tool every time you restart or logoff from Ubuntu because these changes are only temporary. To avoid this you need to create a startup script that will run before the X server starts. So I have written a small script that will automate this process for you that I called auto915resolution.

The script will automatically install 915resolution and will create the startup script for you.

Below is a sample run of the script that will serve as a guide on how to use it and will give you an idea of how it works.

   1. Download auto915Resolution **you can download from the link above**
   2. Extract the file to your home folder (i.e. /home/[your user name]/
   3. Run terminal.
   4. Login as root (you must be logged in as root to create the startup script)
   5. Navigate to that folder. In my case my home folder is "rolando", replace it with your folder name.

      # cd /home/rolando/auto915Resolution/
   6. Run the script. (notice the dot before the forward slash)

      # ./auto915resolution.sh **make sure you are logged in as root** 
   7. When you get the prompt to install 915resolution fix enter 'Y'. If you have 915resolution already installed you can choose not to install it.
   8. A list of all available resolutions ( Modes ) will be displayed followed by a prompt to enter the "Mode" you want to replace with you desired screen resolution. (You might have to maximize the terminal window to see the entire list)
      At the top of the list you will see your chipset info. In my case I have a 915GM.

      Example:
      Chipset: 915GM
      BIOS: TYPE 1
      Mode Table Offset: $C0000 + $269
      Mode Table Entries: 36

   9. Enter the "Mode" number you want to replace. You should replace your default resolution. In my case my default resolution was 1024x768 in mode 34.

      # 34
  10. A prompt to enter your desired resolution will be displayed. Enter your horizontal resolution followed by a space and then your vertical resolution. For example for a resolution of "1280x800" enter "1280 800".

      # 1280 800

  11. A prompt for your maximum color depth (in bits) will be displayed. Options are 8, 16, 24 and 32. Most monitors should be able to handle 24, so if you're not sure enter:

      # 24

  12. The resolution (Mode) list is refreshed and the Mode you chose should now be replaced with the new resolution and color depth.
      A prompt to create the startup script will be displayed. You should enter 'y' in here if you see that your changes were applied correctly in the list.
  13. If you entered 'y', then you should see this output:

      Creating startup script...
      The startup script has been created! Please restart for changes to take effect.

  14. Restart your computer.[/INDENT]




Hope this helps!

---

### Post by BlueFusionX on 2007-10-08
Thanks a bunch for the information!  This information really should be more available.  It really saved me some time.

---

### Post by otdave on 2007-10-13
I am not sure if this is the right place to put this question.  I have been searching for a way to get a native res of 1440 x 900 on my gateway m8708 and have crashed my system 4x trying to get there.  

I have installed ver 7.10 ubuntu and was pleased to find the resolution i was looking for in the system preferences, however....  I am not getting true 1440 x 900 resolution, instead I'm getting a virtual res, so everything looks like 1028 x 764 and I can pan around the 1440 x900 desktop.  Anyone else have this problem and know how to fix it?  I really like Linux in general but I'm killing myself trying to get it to bend to my will.

Oh, I have an Intel Graphics Media Accelerator 950 and a 17" wide screen wxga tft

---

### Post by lavinia on 2007-10-15
My Motherboard Chipset :Intel Crestline GL960/GM965 ?

---

### Post by Royal_Pwner on 2007-11-16
> **badduck said:**
> Nice guide to set up the resolution.

My problem is that I am having a 845G graphic chipset, thus at install I got the lowest resolution (640*480) and I cant change it.

I did follow your step to step installation guide, but it didnt help me.

One strange this was that when I wrote "915resolution" in the terminal, I didnt get all the different mode attributes. But I followed the one from your instructions and did change the text file in the end.

But I still have the lowest resolution. By the way, I am using a Dell optiplex SX260.

Does anyone know what I need to do to fix it?

I have the exact same problem, but i'm running a dell inspiron 1100. And I did everything followed the guide, everything. The resolution just won't change.

---

### Post by Royal_Pwner on 2007-11-16
bump

---

### Post by jhford on 2007-12-10
Maybe I'm in the wrong thread. If so, I apologize. 

I have a Samsung Q1 Ultra UMPC 1024 X 600. I'm a Linux virgin, so I have followed the terrific instructions. I have tried modes 52. 30 and 3c but 1024 X 600 doesn't appear in Preference - Screen Resolution.

Any suggestions would be appreciated.

---

