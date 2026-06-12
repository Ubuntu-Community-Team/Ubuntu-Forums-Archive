---
title: "Monitor refresh rate: how many more years does it take to fix it?"
date: 2006-09-27
forum: Absolute Beginner Talk
---

### Post by sc0undrel on 2006-09-27
Ok, here's my sad story with Linux:

Back in the year 2003 I tried out Knoppix as my first Linux distro. I didn't continue to use it, because there was no way to get my montitor's refresh rate to go higher than 60, which was KILLING my eyes, though I tried really really hard to fix it. So I had to back to WinXP.

A year went by. Then in 2004 I tried out Slackware as my second Linux distro. I didn't continue to use it, because there was no way to get my montitor's refresh rate to go higher than 60, which was KILLING my eyes, though I tried really really hard to fix it. So I had to back to WinXP.

Another year went by. Then in 2005 I tried out Mandriva as my third Linux distro. I didn't continue to use it, because there was no way to get my montitors refresh rate to go higher than 60, which was KILLING my eyes, though I tried really really hard to fix it. So I had to back to WinXP.

Yet another year went by. Now in 2006 I tried out Ubuntu as my fourth Linux distro. I don't know if I should continue to use it, because there seems to be no way to get my montitor's refresh rate to go higher than 60, which is KILLING my eyes, though I have tried really really hard to fix. Must I go  to WinXP again? :(


Here's my current monitor: [http://ccm.senecadata.com/specsheets/f700b.htm]("http://ccm.senecadata.com/specsheets/f700b.htm")

The resolution I'd like to get is **1024x768 @ 85Hz** (which works perfectly in Wind0ze).


Using my limited knowledge about linux, here's what I have tried in Ubuntu:
1. From the "System" menu in the top toolbar I chose "Perferences" and then "Screen resolution". There was an option for 1024x768 @ 85, but after selecting it and then pressing the "Apply" button, the screen went blank for a second, but there were no changes. Monitor was still using 1280x1024 @ 60Hz.
2. Using the command "sudo dpkg-reconfigure xserver-xorg", then answering all questions and saving the xorg.conf file. X didn't even start after it, so I had to reformat and install Ubuntu again, because I didn't know how to get back to X. ](*,) 
3. Editing the /etc/X11/xorg.conf file directly.  X didn't even start after it, so I had to reformat and install Ubuntu again, because I didn't know how to get back to X. ](*,)
4. Something else that I don't remember, but it also had no effect.

HELP needed!!!11!111!!oneoneeleven. :( :(

---

### Post by bulldog on 2006-09-27
Did you try to install the driver for your graphic card?

It's pretty essential to do so.:D

And if you experiement with your xorg.conf make a backup first and replace it if your altering went wrong.

The reconfigure etc. makes a copy automaticly and you only had to put the original back,without a new install.

Especially option four has my interrest.:D

---

### Post by xpod on 2006-09-27
WOW...Thats a while to wait to sort your drivers and your xorg.config out.
Bit sore on the eyes just reading it;)

---

### Post by sc0undrel on 2006-09-27
> **bulldog said:**
> Did you try to install the driver for your graphic card?

It's pretty essential to do so.:D

Uh, no, I haven't done that in Ubuntu. I'm afraid I even don't know how to do it. :(

I remember I tried installing the graphic card drivers for both Slackware and Mandriva several years ago when I still had Ati Radeon 9600Pro, but in spite my efforts, I could not get them installed properly. It ended up with a lot and lot of reformating and reinstalling, but I had no luck. =\

Now I have Ati Radeon X1900XTX. Where could I get drivers for it and how do I install them? :-?


> **bulldog said:**
> And if you experiement with your xorg.conf make a backup first and replace it if your altering went wrong.

The reconfigure etc. makes a copy automaticly and you only had to put the original back,without a new install.

Yep, I tried it, but instead of renaming the backup file, the command shell deleted it instead. I inserted the following command before messing with the xorg.conf file:

```
cp /etc/X11/xorg.conf /etc/X11/xorg.conf_backup
```

... and then when the xorg.conf file was fscked up and the X didn't start, I inserted this:

```
rm /etc/X11/xorg.conf
mv /etc/X11/xorg.conf_backup xorg.conf
```

... then when I did "ls" to that directory, there was no xorg.conf file anymore. :S

... so I had to reformat and install everything all over again. :(

---

### Post by bulldog on 2006-09-27
> **sc0undrel said:**
> Uh, no, I haven't done that in Ubuntu. I'm afraid I even don't know how to do it. :(

I remember I tried installing the graphic card drivers for both Slackware and Mandriva several years ago when I still had Ati Radeon 9600Pro, but in spite my efforts, I could not get them installed properly. It ended up with a lot and lot of reformating and reinstalling, but I had no luck. =\

Now I have Ati Radeon X1900XTX. Where could I get drivers for it and how do I install them? :-?


Well [http://www.ATI.com](http://www.ATI.com) should do I suppose?

But there's an alternative and it's called Easy Ubuntu.
It can install your video drivers and help you with java and some more things you gonna need.

[http://ubuntuforums.org/showthread.php?t=84742](http://ubuntuforums.org/showthread.php?t=84742)

Did you really tried **that** hard?

Offtopic,

Good eveneing to you xpod

---

### Post by bulldog on 2006-09-27
rm /etc/X11/xorg.conf
mv /etc/X11/xorg.conf_backup xorg.conf

Wasn't very good to do.

You should have done

```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf_backup 
```
to make the backup file.
And to place it back you should have done
```
 sudo cp /etc/X11/xorg.conf_backup /etc/X11/xorg.conf 
```

To do things like this you need to have root rights in Ubuntu.

This is accomplised by using the sudo command without sudo it will not be possible to make a backup file.

---

### Post by xpod on 2006-09-27
I just did the same m8 as i end up messing things up in the xorg thingy too.
I wanted to re-install though so i could do all the home partition thing.

I backed the xorg.config up and put the refresh rates in along with the extra resoloution but when i restarted i got my monitor lights flashing like it was`nt amused and a black screen for my troubles..:confused: and thats with my monitors settings from google;) 

Done all the reconfigure thing and startx and even used the backup again but still made a mess of it somewhere.....

All installed again and ready to break again:twisted:
Messed it up last night too but a backup seemed to work then.

ALL in 24 hours....lol

EDIT:sorry mate...to you too

---

### Post by sc0undrel on 2006-09-27
> **bulldog said:**
> rm /etc/X11/xorg.conf
mv /etc/X11/xorg.conf_backup xorg.conf

Wasn't very good to do.

You should have done

```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf_backup 
```
to make the backup file.
And to place it back you should have done
```
 sudo cp /etc/X11/xorg.conf_backup /etc/X11/xorg.conf 
```

Hmm... I'll try those commands next time, thanks. :)

> **bulldog said:**
> Well [http://www.ATI.com](http://www.ATI.com) should do I suppose?

But there's an alternative and it's called Easy Ubuntu.

No thanks, Easy Ubuntu sounds too noobish, I prefer the Ubuntu 6.06 AMD64 edition for my AMD64 Athlon X2 3800+ processor.

Alright, I'll try to install the graphic card drivers that I just leeched from ATI site, I can install them right while using Live-CD, right?
If not, I hate to reformat+reinstall everything again, if anything should go wrong and I can't get to X. :\

---

### Post by gn2 on 2006-09-27
Or treat yourself and buy a TFT?

Uses less power, emits less nasty radiation and much easier on the eyes.

My LG Flatron runs at 60 hz on DVI, and it's fine...

---

### Post by xpod on 2006-09-27
"Easy ubunto" and its counterpart "automatix" are not separate OS`s m8 there handy little apps that make the installation of all the usual requirements like flash,java and codecs and all the other sort of stuff your probably going to be wanting to start outa lot easier.
Of course installing it all seprately will give you much more experience but that`ll come with time anyway..
still aint got much of a clue myself but i scrape by for now;) 

Personanlly i use automatix but i hear easy ubunto is quite similar.

---

### Post by jd65pl on 2006-09-27
You should look into easy ubuntu or if you don't like its name try automatix you can download them from the repos and it aids in setting up your system. It is not a distro in itself if I have understood you correctly

Try searching the forums for them before you pass judgement on what is "too noobish"!!!

Edit:
[URL="https://wiki.ubuntu.com/EasyUbuntu?highlight=%28easy%29%7C%28ubuntu%29"]
Click here for easy ubuntu I tried really hard and found this![/URL]

---

### Post by Mimsy on 2006-09-27
> **sc0undrel said:**
> No thanks, Easy Ubuntu sounds too noobish, I prefer the Ubuntu 6.06 AMD64 edition for my AMD64 Athlon X2 3800+ processor.

Excuse what may be a stupid question but as long as it works, what does it matter how it sounds?

/Mimsy

---

### Post by xpod on 2006-09-27
Better get used of the silly sounding app names cause your gonna come across a few :D ...

---

### Post by jd65pl on 2006-09-27
Xpod's point is highly valid as developers for linux think of extremely creative names, it keeps it interesting!

---

### Post by xpod on 2006-09-27
LOL...Everytime i mention my gimp or my B.U.M i get a worried look from the wife....she`s still convinced im on some sleazy chatroom...

Yup..so much better then.."paint" or "start up manger".....

---

### Post by sc0undrel on 2006-09-27
> **gn2 said:**
> Or treat yourself and buy a TFT

Thanks for the suggestion, but I hate LCDs. Thanks to the afterglow, locked refresh rates and very limited resolutions,
they make a very bad choice when I wanna play some games. Unless of course I get some über-expensive LCD that costs 10 times more than my X1900XTX.

And I already ordered myself [a new monitor](http://www.viewsoniceurope.com/UK/Products/CRTProf/P227fB.htm), which should arrive tomorrow. ^^
Now that's what I call a monitor. Pwns all weak LCDs.

===================================================

Anyway, I failed to install the graphic card drivers, and my eyes hurt like hell. =\
So I guess once again I have to go back to WinXP and try again in about after a year or two... or maybe sooner, if my eyes can stand the pain.

---

### Post by sc0undrel on 2006-09-27
Alright, I used Easy Ubuntu to install the ATI drivers, but they don't seem to be working, there's absolutely no difference and the "glxgears" command gives the same error message as before (can't tell what error messager exactly, as I'm typing this from WinXP).

Then I used the xorg wizard again, answered all the questions and rebooted. Grub loaded Ubuntu like usual, but then BAM! The screen goes all black, completely blank with nothing on it. I had no idea what to do from there, so I put on the Ubuntu CD again, rebooted and then reformated+reinstalled everything again. So, I'm right back where I started. =\

Help! :-|

---

### Post by xpod on 2006-09-27
Sorry to hear your still at it too.
I too started messing again today only to balls it all up again.
Once i put the extras res and the refresh rates into the file and reboot i just kept getting a black screen with my monitor lights all flashing.

It all works prior to that though so it `s only me messing mine up.
I got the correct rates of my monitors site though and done it all the right way..
I wanted to make the extra"home" space on here anyway so i did`nt mind the install again anyway...

Hope someone can help you

---

### Post by lapsey on 2006-09-27
> **sc0undrel said:**
> Grub loaded Ubuntu like usual, but then BAM! The screen goes all black, completely blank with nothing on it. I had no idea what to do from there, so I put on the Ubuntu CD again, rebooted and then reformated+reinstalled everything again. So, I'm right back where I started.

just fyi, next time press Ctrl+Alt+F1. That will take you to a non-x console screen from which you can run xorg-reconfigure (or w/e the x configure wizard is called) to fix it. if that doesnt work you can go into rescue mode from the CD

---

### Post by gn2 on 2006-09-27
> **sc0undrel said:**
> Thanks for the suggestion, but I hate LCDs. Thanks to the afterglow, locked refresh rates and very limited resolutions,
they make a very bad choice when I wanna play some games. Unless of course I get some über-expensive LCD that costs 10 times more than my X1900XTX.

And I already ordered myself [a new monitor](http://www.viewsoniceurope.com/UK/Products/CRTProf/P227fB.htm), which should arrive tomorrow. ^^
Now that's what I call a monitor. Pwns all weak LCDs.

===================================================

Anyway, I failed to install the graphic card drivers, and my eyes hurt like hell. =\
So I guess once again I have to go back to WinXP and try again in about after a year or two... or maybe sooner, if my eyes can stand the pain.


Read up on your monitors, you might find out that your sore eyes are a direct result of the way that CRT monitors operate.

I used to get sore eyes until I got a TFT.

You'll get a better frame rate at the resolution a TFT runs at anyway.

And by afterglow, do you mean ghosting?
This has been all but eliminated with newer TFT's having much better response times.

Also, a 20" TFT costs the same as the fishtank you're looking at.
[http://www.ebuyer.com/customer/products/index.html?rb=22050006171&action=c2hvd19wcm9kdWN0X3NwZWNpZmljYXRpb25z&product_uid=112517](http://www.ebuyer.com/customer/products/index.html?rb=22050006171&action=c2hvd19wcm9kdWN0X3NwZWNpZmljYXRpb25z&product_uid=112517)

Each to their own I suppose, but mind how you go.

---

### Post by wpshooter on 2006-09-27
> **sc0undrel said:**
> Alright, I used Easy Ubuntu to install the ATI drivers, but they don't seem to be working, there's absolutely no difference and the "glxgears" command gives the same error message as before (can't tell what error messager exactly, as I'm typing this from WinXP).

Then I used the xorg wizard again, answered all the questions and rebooted. Grub loaded Ubuntu like usual, but then BAM! The screen goes all black, completely blank with nothing on it. I had no idea what to do from there, so I put on the Ubuntu CD again, rebooted and then reformated+reinstalled everything again. So, I'm right back where I started. =\

Help! :-|

Scoundrel:

I know I might possibly risk having the wraith of God coming down upon me or even worse the Ubuntu forum flames, but I don't think that you should have to reinvent the wheel to get the video on your computer to work correctly.  

This, at most, should be a matter of running one simple GUI program or running an executable from the desktop and this would be fixed.  

I can hardly envision some of the computer users in the office I work in who just until fairly recently could not even comprehend having to reset the shutdown choice on their workstation from restart to shutdown in order to get the machine to actually stay off, having to attempt to try to follow something like all the afore posted instructions for getting this video problem fixed.

But good luck to you, hang in there, in my opinion in about 2 to 3 years Ubuntu is going to be a better desktop O/S than M/S.

---

### Post by sc0undrel on 2006-09-28
Thanks to everyone who has replied so far. Sorry for
some of the immature things I said yesterday... it's just that I was way too pissed off then. #-o

Anyway, I'm too stubborn to quit just yet. This time I'm gonna get this
problem solved even if I have to spend every single evening on it. 
All my leet friends use Linux and they say that Ubuntu is one of the best.

Damn, if I could only get my resolution+refreshrate problem fixed,
I could move on to actually learning a bit, without this tremendous eyestrain. :mrgreen:

Well, unfortunately I had no luck with Easy Ubuntu, so I guess I give Automatix a go!

---

### Post by xpod on 2006-09-28
Good day to you my freind and to all...:D 
Sorry to see your still at it but this is getting worse than one of my recent xp re-installs that took 3 days to get right.......I was using a burnt and dodgy i386 to install from though:D 

> [http://www.getautomatix.com/wiki/index.php?title=Installation](http://www.getautomatix.com/wiki/index.php?title=Installation)

This is the how to i follow for automatix and it`s usually up and running in 5 minutes or so....
I like the "stubborn" attitude by the way.........THAT in itself should be enough o carry you through....:D 

Good luck......today;)

---

### Post by sc0undrel on 2006-09-29
Ok, my new monitor arrived today. In WinXP everything works perfect -- every single resolution and refresh rate are where they should be, no problems at all.

So I booted into Ubuntu (Live-CD this time), and I was like ZOMG WTF, it auto-selected the resolution to something like 1920x1200, even though I don't have a wide-screen monitor, how strange is that. :-?

Anyway, the screen was flickering like hell and as I opened my monitor's control panel by pressing the button on the monitor, it STILL fscking showed that it was using 60Hz refresh rate!

**WHY OH WHY** does it have to use a resolution SOOOOOOOOO high, and a refresh-rate so low that kills my eyes?! :(

Of course changing the resolution/refreshrate from the System - Perferences menu had no effect at all, like usual. Then I installed Automatix, and guess what. There is NO ATI driver to install! Oh god, how much more frustrating can it get? =\

---

### Post by ringmaster on 2006-09-29
I think that your graphic card is not correctly supported by xorg or the kernel; I don't know.
Please try sudo dpkg-reconfigure xserver-xorg and when selecting default resolution, select "medium" and then the desired resolution.
Hope it helps.

---

### Post by petri on 2006-09-29
You should not start a another thread like this [http://ubuntuforums.org/showthread.php?p=1558340&posted=1#post1558340](http://ubuntuforums.org/showthread.php?p=1558340&posted=1#post1558340)

You have to learn to use **Search** option above. Chances are really good you will find an answer directly to your problem but if you don't feel free to start a thread. Many questions have been answered so many times that people just get tired to answer again and again and again... that's why you have to use the **Search**. ;)

---

### Post by tommcd on 2006-09-29
The 64 bit OS can be more problematic than the 32 bit OS, especially with drivers for hardware. Since you are having so much trouble, why not try the 32 bit OS? You may have better luck. At least it won't cost anything to try it.

---

### Post by sc0undrel on 2006-10-03
> **tommcd said:**
> The 64 bit OS can be more problematic than the 32 bit OS, especially with drivers for hardware. Since you are having so much trouble, why not try the 32 bit OS? You may have better luck. At least it won't cost anything to try it.

Yes, that was the problem. :D

I tried out the 32-bit version of Ubuntu, and finally managed to get the refresh rate problem solved. Here's how I did it.
First I installed the 32-bit version of Ubuntu, then after it had auto-updated some of the packages, I used EasyUbuntu to install the ATi drivers.

Then I inserted this commmand into the terminal:
sudo dpkg-reconfigure xserver-xorg

After answering all the questions and rebooting, I could finally select the resolutions and refresh rates, that were satisfactory. :)

I've settled at 1600x1200 @ 100Hz, although I originally wanted to use 1280x960 @ 120Hz, but somehow it just doesn't seem to appear in the list of the resolutions to choose from. Even if I manually edit the xorg.conf file. :-?

---

### Post by gn2 on 2006-10-03
> **sc0undrel said:**
> 
I've settled at 1600x1200 @ 100Hz, although I originally wanted to use 1280x960 @ 120Hz, but somehow it just doesn't seem to appear in the list of the resolutions to choose from. Even if I manually edit the xorg.conf file. :-?

Have you checked the product documentation?

Sadly your monitor doesn't support your desired resolution, it's a 4:3 screen, 1280x960 is a widescreen setting.

[http://www.viewsoniceurope.com/UK/Products/CRTProf/P227fB.htm#specs](http://www.viewsoniceurope.com/UK/Products/CRTProf/P227fB.htm#specs)

---

### Post by wpshooter on 2006-10-03
> **sc0undrel said:**
> Ok, here's my sad story with Linux:

Back in the year 2003 I tried out Knoppix as my first Linux distro. I didn't continue to use it, because there was no way to get my montitor's refresh rate to go higher than 60, which was KILLING my eyes, though I tried really really hard to fix it. So I had to back to WinXP.

A year went by. Then in 2004 I tried out Slackware as my second Linux distro. I didn't continue to use it, because there was no way to get my montitor's refresh rate to go higher than 60, which was KILLING my eyes, though I tried really really hard to fix it. So I had to back to WinXP.

Another year went by. Then in 2005 I tried out Mandriva as my third Linux distro. I didn't continue to use it, because there was no way to get my montitors refresh rate to go higher than 60, which was KILLING my eyes, though I tried really really hard to fix it. So I had to back to WinXP.

Yet another year went by. Now in 2006 I tried out Ubuntu as my fourth Linux distro. I don't know if I should continue to use it, because there seems to be no way to get my montitor's refresh rate to go higher than 60, which is KILLING my eyes, though I have tried really really hard to fix. Must I go  to WinXP again? :(


Here's my current monitor: [http://ccm.senecadata.com/specsheets/f700b.htm]("http://ccm.senecadata.com/specsheets/f700b.htm")

The resolution I'd like to get is **1024x768 @ 85Hz** (which works perfectly in Wind0ze).


Using my limited knowledge about linux, here's what I have tried in Ubuntu:
1. From the "System" menu in the top toolbar I chose "Perferences" and then "Screen resolution". There was an option for 1024x768 @ 85, but after selecting it and then pressing the "Apply" button, the screen went blank for a second, but there were no changes. Monitor was still using 1280x1024 @ 60Hz.
2. Using the command "sudo dpkg-reconfigure xserver-xorg", then answering all questions and saving the xorg.conf file. X didn't even start after it, so I had to reformat and install Ubuntu again, because I didn't know how to get back to X. ](*,) 
3. Editing the /etc/X11/xorg.conf file directly.  X didn't even start after it, so I had to reformat and install Ubuntu again, because I didn't know how to get back to X. ](*,)
4. Something else that I don't remember, but it also had no effect.

HELP needed!!!11!111!!oneoneeleven. :( :(

As I have said before, IMO, it will take about 2 to 3 years before Ubuntu becomes as user friendly as M/S windows.  If you just love spending your time fixing this kind of stuff instead of doing actual work with your computer, I have heard it before.

Thanks.

---

### Post by sc0undrel on 2006-10-03
> **gn2 said:**
> Have you checked the product documentation?

Sadly your monitor doesn't support your desired resolution, it's a 4:3 screen, 1280x960 is a widescreen setting.

[http://www.viewsoniceurope.com/UK/Products/CRTProf/P227fB.htm#specs](http://www.viewsoniceurope.com/UK/Products/CRTProf/P227fB.htm#specs)

Hmm, I'm afraid you are mistaken.
As far as I know 1280x960 is not a widescreen resolution. I can use it just fine under WinXP @ 120Hz with this monitor. :)

[http://www.latenighthacking.com/projects/monitorResolutions.html](http://www.latenighthacking.com/projects/monitorResolutions.html)

1280x960  = 4:3 = fullscreen?


> **wpshooter said:**
> As I have said before, IMO, it will take about 2 to 3 years before Ubuntu becomes as user friendly as M/S windows.  If you just love spending your time fixing this kind of stuff instead of doing actual work with your computer, I have heard it before.

Thanks.

Heh, I just wanna learn more about Linux and am way too impatient to wait another 2-3 years. :mrgreen:

/Edit: I searched the forums for my problem and found out that some people were able to fix it with some weird modelines or something.
Hmm, does anyone know which modelines I should use in order to get a resolution of 1280x960 @ 120Hz? :-?

---

### Post by gn2 on 2006-10-03
1280x1024 is a standard setting, [http://www.webopedia.com/TERM/S/SXGA.html](http://www.webopedia.com/TERM/S/SXGA.html)

If you want to jump through hoops to lose 64x1280=81920 pixels, you're mad.

If XP is better for you, then stick with it.

Linux works for me, but if it's not working for you, move on.

---

### Post by sc0undrel on 2006-10-03
> **gn2 said:**
> 1280x1024 is a standard setting, [http://www.webopedia.com/TERM/S/SXGA.html](http://www.webopedia.com/TERM/S/SXGA.html)

If you want to jump through hoops to lose 64x1280=81920 pixels, you're mad.

If XP is better for you, then stick with it.

Linux works for me, but if it's not working for you, move on.


1280x1024 is 5:4, not 4:3. 5:4 is standard on most LCDs. CRT standard is 4:3.

And no, I'm not going to stick with WinXP. I've been using WinXP since it first came out in 2001.
During that time I've installed it hundreds of times on dozens of boxes and have learned to tweak
it pretty much inside out. To say the least I find it just too limiting and wanna try out something different. :)

Hmm, I found some good modelines generators with Google, gonna check how they work.

---

