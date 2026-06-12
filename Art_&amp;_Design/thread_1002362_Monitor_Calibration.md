---
title: "Monitor Calibration"
date: 2008-12-04
forum: Art &amp; Design
---

### Post by Gerhardus on 2008-12-04
Today I got my new huey from newegg. 
I am a photographer and use a spyder coupled with ps elements in windows.  I decided to try out ubuntu with the hopes of being able to make a complete conversion. In order to do this I need to be able to calibrate and profile my monitor. Now I got lprof and got nowhere on a bullet train when trying to use it with my spyder. So I decided to try argyll though I've heard that it's more complicated, I need my monitor profiled. After hunting and fighting and trying for several days I realized that getting a spyder1 to work with it would be more difficult that just upgrading. In my research I found that colorvision is particularly hostile towards open source. I decided to go with a huey, because of the price and the fact that it's said to be supported. In lprof I haven't been able to figure out in the slightest how to get the huey to work. Searching on line, I've found no helpful tutorials or blogs that explain how to use them just a few saying that it is supposed to work and a couple saying that it does. I'm not opposed to using argyll, but I've heard about lprof working with colorimeters and since it's available in the repositories and it's graphical, I would much prefer figuring it out there. Nothing against using command lines but it'll be a lot easier to convince other photogs to convert if I can show them something they can do as well. If anybody has any idea please let me know

---

### Post by kayosiii on 2008-12-06
from what I can gather from wikipedia [http://en.wikipedia.org/wiki/Linux_color_management](http://en.wikipedia.org/wiki/Linux_color_management) the version of lprof that supports hardware calibration is not yet released... that information could easily be out of date. I would march on over to lprof website and offer to help test for them.

---

### Post by rockin_goliath on 2008-12-07
[http://linux.softpedia.com/get/Utilities/GAMMApage-4628.shtml]("http://linux.softpedia.com/get/Utilities/GAMMApage-4628.shtml")

GAMMApage is great. I do a little photography myself, and also just like having the colors on my monitor look even and nice. You don't have to install anything, it's just a little script file that you click on, and any changes you make are reversible. Try it out!

---

### Post by glantucan on 2008-12-07
Hi folks,

GAMMApage, Monica, Kgamma, just correct the luminance curve of your graphics-card/monitor to make it as linear as possible. They DON'T produce any monitor profile, which is a must for good printing.

For that you would use lprof or Argyll. For now I'm testing lprof, but the important thing, if you don't want to invest time in tests, is that you can use a profile created on windows. See [http://ubuntuforums.org/showpost.php?p=3347611&postcount=5]("http://ubuntuforums.org/showpost.php?p=3347611&postcount=5")
> I do photography under linux (see my site down there) and I managed a satisfying workflow.

1) create a monitor profile (under winXP, but some hardware is also supported by Linux, AFAIK).
2) load it with xcalib (I have a script which I run if needed so I can check that the data is indeed loaded; there is a command to remove any LUT information, check xcalib --help).
3) load the same profile in your application, (gimp 2.4rc should work, I use cinepaint); chose your editing profile (sRGB or AdobeRGB).

You have a working color managed display.

To load the profile when you log in you can add:
```
xcalib <profile(with complete path)>
```
to ~/.xinitrc

I'm having my own problems getting all this to work, but the experts say it is all possible (I guess I made so many changes in my configuration that I messed all up) so I keep trying.

For good step by step tutorials go to [http://jcornuz.wordpress.com/]("http://jcornuz.wordpress.com/")

For a very good (and easy to understand) technical explanation about what color management is all about go to [http://regex.info/blog/photo-tech/color-spaces-page0/]("http://regex.info/blog/photo-tech/color-spaces-page0/")

**EDIT:**
Putting xcalib call in ~/.xinitrc does not work if you use automatic graphical session start.
As said here [https://wiki.ubuntu.com/CustomXSession]("https://wiki.ubuntu.com/CustomXSession") it should work crating ~/.xsession as a symbolic link to ~/.xinitrc:
```
ln -s ~/.xinitrc ~/.xsession
```
I tried and didn't work either, my profile is not loaded on session start.

**SOLUTION:**
Create a script named xCALIB.sh (or other name you like) with the following contents:
```
#!/bin/bash
killall gnome-screensaver
xcalib /media/datos/__MisDocs/settings/PROFILES/LiteOnAdobeGamma_sinFlexo080704.icc
gnome-screensaver
```
and add it to your start applications. In gnome, go to system/preferences/sessions and click Add in the Start programs tab. Add the script click OK, close and you are done.

*NOTE*: 
Gnome-screensaver is killed before and restarted when the profile is loaded to workaround a bug of gnome-screensaver, which causes the loaded profile to unload. 
It seems that if you call xcalib before gnome-screensaver daemon is started this is solved. 
I read somewhere this was fixed for the last versions of gnome-screensaver, but it doesn't hurt much to be cautious.

Hope this help
Cheers

---

### Post by glantucan on 2008-12-07
Hi again

I've been trying to create as a first step a rough monitor profile with lprof using my eyes as measurements devices :P (eyes are not good ones,  I know)
Just to clarify, I open lprof, get to the monitor tab, press *enter monitor values* choose D65 white point, leave default option for monitor primaries and press the *set gamma and black point* button. Follow the on-screen instructions, and accept the changes. Finally I save it. If I use the profile checker in lprof I get these values:
```
Profile: rgb built-in - (lcms internal)

lcms RGB virtual profile



White point near  D65 (daylight)

Media white (XYZ): 95.02, 100.00, 108.84
Primaries: R:0.64, 0.33  G:0.3, 0.6  B:0.15, 0.06
Estimated gamma: R:2.31, G:2.33  B:2.31
```
 
The problem is that when I try to load it with xcalib from the command line nothing happens. 

I can load windows generated profiles with xcalib with no problem.

I even tried to create a really messed up profile using really high gamma value for the reds. Still no change when I try to load it with xcalib.

Any ideas?

Thanks

---

### Post by glantucan on 2008-12-07
I found someone who ran into the same problem:
> Lprof and xcalib didn’t work for me. Either Lprof didn’t write a profile that xcalib understood, or xcalib wasn’t able to properly communicate to the video card. I suspect the later, as on xcalibs site it is noted that xcalib has trouble setting a couple variables on older ATI cards.
[http://linuxtidbits.wordpress.com/2008/03/10/linux-design-calibrate-the-display/]("http://linuxtidbits.wordpress.com/2008/03/10/linux-design-calibrate-the-display/")

I have a nvidia Geforce 8600 GTS, though

No solution yet

---

### Post by mariosnc on 2008-12-08
I recently had this problem myself. I managed to get my screen colour profiled using argyllcms and Pantone Huey color meter. I got a .deb package of argyllcms at this blog:

[http://blog.pcode.nl/2008/08/argyllcms-for-ubuntu-hardy](http://blog.pcode.nl/2008/08/argyllcms-for-ubuntu-hardy)

Here is a little tutorial to simplify things for you.

If you do not have a color meter or your color meter isn't supported by argyllcms you can copy your icc profile created in windows and proceed to step 3.

_Step 1_

Add this line to your repositories and then install argyllcsm through synaptics. 

deb [http://ubuntu.pcode.nl/ubuntu](http://ubuntu.pcode.nl/ubuntu) hardy argyll

_Step 2_

Then give at the console

dispcal -yl -v -o toshiba

targen -v  -d3 -f500 toshibaA

dispread -yl -v -k toshiba.cal toshibaA

colprof -yl -v -D"toshiba A" -qm -as toshibaA

Give one command at a time and follow the screen instructions. First and third command could take some time to complete so be patient (almost 20 minutes). Change toshiba with your screen name or whatever you like. Also change -yl with -yc if you have a crt monitor. -yl is for lcd monitor.

After all the tests finish, in your home folder an icc profile will be created and some other files. The one you need is the one with the final name. I this case it will be toshibaA.icc Copy the file if you want into a different folder. If you move the icc profile to a new folder make sure the folder name is a single word not two words. This is because if you auto load the profile on startup it won't start if the folder is named with 2 words (step 4)

_Step 3_

Then give to the console again 

sudo apt-get install xcalib

This will install xcalib which is needed for loading the icc profile at your system.

_Step 4_

You can make a simple script to load the icc profile you just created with xcalib instead of giving the command every time at the console. This can be done with this script.

(open a text editor and type the following and then save as whateveryoulike.sh)

#!/bin/bash
xcalib /home/mariosnc/iccprofile/toshibaA.icc

Right click on the script (after you saved and closed the editor) and go to Properties->Permissions and put a tick on the box where it says Allow executing file as a program.Close and your ok.

As you can see my icc profile resides in a folder named iccprofile in my home folder.

_Step 5_

The final step is to make the script to load automatically every time you boot. This can be done by going to System->Preferences->Sessions and adding an new event. Press add and give the new event a name and at the command browse to the folder you saved the script you made in step 4 and select the script.

All Done!!

_Final words_

You can load the icc profile if you double click on the script and then press run. You can unload the icc profile and use the system default by giving at the console (or use Alt+F2) 

xcalib -c

You can take an look at ArgyllCms website to find out what each command we used in step 2 means.

[http://www.argyllcms.com/doc/Scenarios.html#PM1](http://www.argyllcms.com/doc/Scenarios.html#PM1)

Good Luck!

P.S.: Sorry if my English is poor. I hope you understand.

---

### Post by glantucan on 2008-12-08
Nice post mariosnc :D

Today I was wondering... If I load a monitor profile with xcalib, that doesn't mean that any application makes a conversion from the embedded profile in the image to the monitor color space, right? It's just that every color in the screen is corrected (in gamma terms), assuming it was created as sRGB. Is it so?

I read about xicc ([http://burtonini.com/blog/computers/xicc]("http://burtonini.com/blog/computers/xicc")), wich seems to do something different: set an icc aware profile globally, so icc applications (like gimp or eog) can convert on the flay to the monitor color space. But, what if I use them both, xcalib for gamma correction and xicc for profile conversion. Are they going to conflict in any way?

This color management stuff is an infinite source of anxiety and misunderstandings, (sigh)

What I am actually looking for is to get a color managed workflow, and for that I want/need:
[LIST=1]
[*]A color managed lightweight wiewer (like gthumb or eye of gnome. Not done) There is noway to configure that through preferences so I guess they are not "color aware" yet.
[*]A color managed picture editor like GIMP (done). Configurable through preferences.
[*]A color managed RAW converter (for now I'm happy and done  with ufraw)
[*]A color managed printing software (next step when I'm satisfied with he previous ones)
[/LIST]
  
Not far away from there, I think, but still I have a lot of questions.

Cheers!

---

### Post by glantucan on 2008-12-08
Ok, I found something
The development version of gqview (2.1.5) supports color profiles
It even displays the .pef raw files from my pentax. It's nice.
:guitar:
I found a deb package here:[ http://linuxappfinder.com/package/gqview]("http://linuxappfinder.com/package/gqview")

But my previous questions still bothering my curiosity :)

---

### Post by mariosnc on 2008-12-08
> **glantucan said:**
> 
If I load a monitor profile with xcalib, that doesn't mean that any application makes a conversion from the embedded profile in the image to the monitor color space, right? It's just that every color in the screen is corrected (in gamma terms), assuming it was created as sRGB. Is it so?

I read about xicc ([http://burtonini.com/blog/computers/xicc]("http://burtonini.com/blog/computers/xicc")), wich seems to do something different: set an icc aware profile globally, so icc applications (like gimp or eog) can convert on the flay to the monitor color space. But, what if I use them both, xcalib for gamma correction and xicc for profile conversion. Are they going to conflict in any way?

What I am actually looking for is to get a color managed workflow, and for that I want/need:
[LIST=1]
[*]A color managed lightweight wiewer (like gthumb or eye of gnome. Not done) There is noway to configure that through preferences so I guess they are not "color aware" yet.
[*]A color managed picture editor like GIMP (done). Configurable through preferences.
[*]A color managed RAW converter (for now I'm happy and done  with ufraw)
[*]A color managed printing software (next step when I'm satisfied with he previous ones)
[/LIST]


Yes, xcalib does not load the icc profile in every application. Unfortunately it only corrects system colours and firefox web pages. We have to manually enable colour management in The GIMP and UFRaw. 

I have never managed to use xicc. I load the profile from the console but i can not see any colour change in any program.

My workflow is about the same as yours. Eog, unfortunately, does not support icc profiles. F-spot does but it is not as lightweight as eog.

You can use icc profiles in f-spot if you copy your icc in 

/usr/share/color/icc   or   /usr/local/share./color/icc

Then go to Edit-> Preferences and select under display the colour profile you have. Check both, enable and try to use system display profiles and you are ready to go.

I would like to learn more about xicc and how it works. If you have any other info please share. 

About the colour managed printing which printer do you own? HP printers with gutenprint drivers allow to print with several options in almost any program. Among the options you can find an option for colour correction. I think if you set it to uncorrected your printer prints exactly what your screen shows although i haven't tested yet all the options due to a big problem i am trying to solve.

When i print a picture the printer instead of printing a single image prints two compressed images side by side (on A4 paper). Please help if you know anything.

---

### Post by glantucan on 2008-12-08
I searched, but no more info on xicc.
  
> You can use icc profiles in f-spot if you copy your icc in

/usr/share/color/icc or /usr/local/share./color/icc

Then go to Edit-> Preferences and select under display the colour profile you have. Check both, enable and try to use system display profiles and you are ready to go.

I did that but there isn't such an option in my f-spot preferences (version 0.4.3.1) I guess you have a newer version. Can you also select the camera profile?
> About the colour managed printing which printer do you own? 
I own a HP Photosmart D7160. I tested photo printing some months ago, but I didn't try it with a color managed system. I will post my findings when I try again. Soon I hope, but for now I'm trying to get the same visual approximated results with ufraw than those I was capable of with my old windows system.
> When i print a picture the printer instead of printing a single image prints two compressed images side by side (on A4 paper). Please help if you know anything.
Don't know if I understand your problem, but check if you have 2 pages per sheet selected in the page configuration tab. (Assuming you got the same printer configuration dialogs I have)

Cheers, and thanks

---

### Post by mariosnc on 2008-12-09
> **glantucan said:**
> 
I did that but there isn't such an option in my f-spot preferences (version 0.4.3.1) I guess you have a newer version. Can you also select the camera profile?

Don't know if I understand your problem, but check if you have 2 pages per sheet selected in the page configuration tab. (Assuming you got the same printer configuration dialogues I have)



Yes i have a newer version of f-spot. My version is 0.5.0.3. There is no option to select camera profile, only the display profile.

No, i do not think there is a problem with any of the options in the config dialogues. I checked all the settings not once. And i tried different settings but i always get the same result. Very strange... With windows there is no problem at all but ubuntu is driving me crazy.

---

### Post by glantucan on 2008-12-09
Yes, welcome to club :p
But the good thing is that after all that effort and crazyness, at the very end, when you solve the problem... and with enough patience I always found the solution (or a workaround, je) ... You feel that you did learn something useful, and that didn't happen to me when I worked with windows.

Anyway, do you have the same printer I have? 

This week I'm pretty busy (correcting exams, sigh!), but i will be back to testing things next week. I'll try to see how my printer works then. If you are around check this thread.

Heave fun in the meantime!

Cheers!

---

### Post by lt_gustavsen on 2008-12-10
> **glantucan said:**
> Nice post mariosnc :D

Today I was wondering... If I load a monitor profile with xcalib, that doesn't mean that any application makes a conversion from the embedded profile in the image to the monitor color space, right? It's just that every color in the screen is corrected (in gamma terms), assuming it was created as sRGB. Is it so?

Hello. I just signed up.
xcalib just loads the correct gamma curve to the monitor. After that you have a calibrated display. Every application is affected. But you should also load the xicc atom with dispwin. Dispwin can also load the lut so xcalib is not needed anymore.
> 
I read about xicc ([http://burtonini.com/blog/computers/xicc]("http://burtonini.com/blog/computers/xicc")), wich seems to do something different: set an icc aware profile globally, so icc applications (like gimp or eog) can convert on the flay to the monitor color space. But, what if I use them both, xcalib for gamma correction and xicc for profile conversion. Are they going to conflict in any way?


No they do not conflict. The lut loading brings the display to a known state and it is also responsible for white point. The xicc atoms are used by applications to correct colours that are send to the display.

Normaly you create the profile and install it with
#dispwin -I myprofile.icc

After a restart the calibartion is lost so you have to loadt it again. This can be done with xcalib or dispwin.
# dispwin -L
 
As you have seen in other posts here the calibration is alos reseted by the gnomescreensaver to the state before it was started the first time. A script in seassion that stop gnome-screensaver and issue dispwin takes care of that. 

Another note: Some systems are not xrandr compatible and needs an enviroment variable to be set like this:
export ARGYLL_IGNORE_XRANDR1_2=yes 
before you run dispwin.

> 
This color management stuff is an infinite source of anxiety and misunderstandings, (sigh)

Yes it is. I have used many years myself to try to learn this. I have still a long way to go.
The documenation over at argyllcms is recomended:
[http://argyllcms.com/doc/Scenarios.html#PM1](http://argyllcms.com/doc/Scenarios.html#PM1)
> 
What I am actually looking for is to get a color managed workflow, and for that I want/need:

[*]A color managed lightweight wiewer (like gthumb or eye of gnome. Not done) There is noway to configure that through preferences so I guess they are not "color aware" yet.

Eye of gnome (eog) reads the xicc atom by default on ubuntu.  That is very nice. 
> 
[*]A color managed picture editor like GIMP (done). Configurable through preferences.

Yes, and you can also use the "use system default" to read the xicc atom.
> 
[*]A color managed RAW converter (for now I'm happy and done  with ufraw)
[*]A color managed printing software (next step when I'm satisfied with he previous ones)


Ufraw can also read the xicc atom. Photoprint is a nice application with color managment support. The same author have now started to work with a linearizing tool for gutenprint.

>   
Not far away from there, I think, but still I have a lot of questions.

Cheers!


Cheers from me to and I whis you good luck.

---

### Post by glantucan on 2008-12-12
Today Im going to buy a colorimeter to calibrate my monitor. Has anybody a suggestion of something which works on linux?

Thanks

---

### Post by glantucan on 2008-12-13
I did buy a calibrator already.
I bought X-Rite ColorMunki... Don't ask me why. I knew it's not supported, yet, by argyll. But the point of being able to calibrate the monitor and the printer with the same device convinced me to spend 500 euros on this (Being able to calibrate a projector was also a plus). The seller was very convincing

The bad news?... Though there is no sign of it in the packaging neither the printed quick start instructions, it only calibrates LCD or laptop monitors. I got upset when I discovered this, after installing the software on windows.

Eventually I found a post in the support forum with a technician climing that it was possible to calibrate CRT monitors just using the LCD option, so I did try it. Nothing to loose once the package was already open.

The profiling procedure is really fast and easy. But the profile  I got produce a orange cast on the highlights and oversaturated colors everywere.

Oh! I'm not asking for support in this forum about this issue, by the way. Just advicing not to buy this product. There are lots of issues reported, specially regarding the software, as it seems the hardware is pretty good. Maybe when argyll support it, will be a top quality calibrator.

All that last is the hope to get my money back, or at least to be able to exchage it for another calibrator.

---

### Post by glantucan on 2008-12-16
I did some further tests with this calibrator. I think I made a mistake criticizing it so soon.

It seems my monitor is so bright that the spectrophotometer was saturating, and that could be the reason I got highlights clipped to orange when calibrating.

I decreased the brightness of the monitor and this problem didn't show again.

I still have to do some experimentation.

---

### Post by AJB2K3 on 2008-12-16
Um probably missing the post but.

The spider is supposed to have official linux software made by its makers.

---

### Post by pvalley1967 on 2009-01-25
just my two cents but I feel that Ubuntu needs to work more on monitor profiles and setting them right instead of using Generics its funny because suse10.3 did this why cant ubuntu?

---

