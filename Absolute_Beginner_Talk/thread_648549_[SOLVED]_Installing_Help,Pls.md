---
title: "[SOLVED] Installing Help,Pls"
date: 2007-12-23
forum: Absolute Beginner Talk
---

### Post by bluebrew on 2007-12-23
OK I know you guys see these help threads alot so I apologize in advance
I've been on here reading awhile,defragged my windows 5 times and decided I'm ready to install Gutsy,running the live cd as I type here but cannot get it installed.
I'm sure its a easy fix but I cannot find it
So my problem is during the install window I just can't see or get access to the bottom of the installation window to hit next,the first page was ok,selected English then hit enter and it went through but cannot get past the country/area selection due to this thou
please help

Thnx

---

### Post by overdrank on 2007-12-23
> **bluebrew said:**
> OK I know you guys see these help threads alot so I apologize in advance
I've been on here reading awhile,defragged my windows 5 times and decided I'm ready to install Gutsy,running the live cd as I type here but cannot get it installed.
I'm sure its a easy fix but I cannot find it
So my problem is during the install window I just can't see or get access to the bottom of the installation window to hit next,the first page was ok,selected English then hit enter and it went through but cannot get past the country/area selection due to this thou
please help

Thnx

HI and welcome, try and use the alt, key and single click with the mouse and you should be able to move the window. goos luck :KS

---

### Post by bluebrew on 2007-12-23
Thank you for the quick reply
That let me move the window however not the way that is necessary,it won't let me move the window past the task bar so I can see the next button still.It will move past the bottom one so I can move the screen down but not up,stops at the taskbar
and here I thought this was gonna be the easy part ha ha

---

### Post by bluebrew on 2007-12-24
no takers on this yet ???
took all this time to prepare myself to install the infamous ubuntu and feel as if I got stalled by something that should be simple 
neways the inlaws are comming for the holidays today,hopefully I can get it installed right after xmas

happy holidays every1

---

### Post by overdrank on 2007-12-24
> **bluebrew said:**
> no takers on this yet ???
took all this time to prepare myself to install the infamous ubuntu and feel as if I got stalled by something that should be simple 
neways the inlaws are comming for the holidays today,hopefully I can get it installed right after xmas

happy holidays every1

HI and if you are just installing you can use the alternate cd. It is a text based installation.
[http://releases.ubuntu.com/releases/7.10/](http://releases.ubuntu.com/releases/7.10/)

---

### Post by ed-koala on 2007-12-24
Does the installation screen have the Minimize/Maximize/Quit buttons?  Or, if it has a title bar, right click and resize. 

If you only need just a little more room, right click your task bar, select properties, and hide the taskbar, that'll give you a bit more room to maneuver.

Hope it helps  :)

---

### Post by bluebrew on 2007-12-24
All I had for options is to hit the red X to close it,which I had to do cause I was unable to go further
I remember clicking on the title bar pretty sure I never had the resize option or I would tried that
I'm gonna try to see if I can move or hide the top taskbar,not sure if I can since I'm in the live cd environment

what is it like using the alternate cd?

---

### Post by bluebrew on 2007-12-27
ok so I got it all installed and working great...thanks to all who replied
now just getting used to Linux after using Windows for years

I love the features of Ubuntu,the graphics,everything is so much faster then Windows


I'm gonna try and just use thread if I need further advice which I'm sure I will

---

### Post by bluebrew on 2007-12-27
Ok I'm looking for advice already

I have a ati video card and I see theres alot discussion regarding there drivers
so how do I know if I already have the proper drivers installed already,I haven't actually watched any video yet(that will be another task,getting my torrents) but seems to be ok according to the screen saver graphics

but neways when I attempted to follow this guide
[https://help.ubuntu.com/community/BinaryDriverHowto/ATI](https://help.ubuntu.com/community/BinaryDriverHowto/ATI)

I typed "sudo apt-get update"  in the terminal and I get this error message
"E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem"

any takers on this?

---

### Post by overdrank on 2007-12-27
> **bluebrew said:**
> Ok I'm looking for advice already

I have a ati video card and I see theres alot discussion regarding there drivers
so how do I know if I already have the proper drivers installed already,I haven't actually watched any video yet(that will be another task,getting my torrents) but seems to be ok according to the screen saver graphics

but neways when I attempted to follow this guide
[https://help.ubuntu.com/community/BinaryDriverHowto/ATI](https://help.ubuntu.com/community/BinaryDriverHowto/ATI)

I typed "sudo apt-get update"  in the terminal and I get this error message
"E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem"

any takers on this?

HI and if you go to the terminal located under applications, accessories and use this command
```
sudo dpkg --configure -a
``` hopefully that will correct the issue

---

### Post by bluebrew on 2007-12-27
ok thank you
I will try that once I'm home and post the results

---

### Post by bluebrew on 2007-12-31
Well well...been using Ubuntu Gutsy for 5-6 days now and still going strong
not really catching onto the commands but thankfully we don't have to be fully Dependant on them,I usually google what I want to do then copy and paste the commands that I find(most of the results comes from here neways) 
once I was able to get past my original installation problem(see first post haha),I got it installed flawelessly,I got dual boot set up with this and XP.

The biggest challenge has been trying to lure the wife away from windows and use this more haha(atleast shes not restarting as often as she was to go back to windows)


So what I'm wondering is can I enlarge my partition that has Ubuntu to make it bigger by reducing my xp partition in size?
I started this with just 15gigs(I wanted it to be 25 but slid the slider the wrong way when making the partition during the installation I guess)

---

### Post by overdrank on 2007-12-31
> **bluebrew said:**
> Well well...been using Ubuntu Gutsy for 5-6 days now and still going strong
not really catching onto the commands but thankfully we don't have to be fully Dependant on them,I usually google what I want to do then copy and paste the commands that I find(most of the results comes from here neways) 
once I was able to get past my original installation problem(see first post haha),I got it installed flawelessly,I got dual boot set up with this and XP.

The biggest challenge has been trying to lure the wife away from windows and use this more haha(atleast shes not restarting as often as she was to go back to windows)


So what I'm wondering is can I enlarge my partition that has Ubuntu to make it bigger by reducing my xp partition in size?
I started this with just 15gigs(I wanted it to be 25 but slid the slider the wrong way when making the partition during the installation I guess)

HI and you can use gparted on the live cd or use the stand alone version. This will allow you to resize your partitions. Good luck! :KS

---

### Post by bluebrew on 2007-12-31
So it's just that easy...
I'd like to have some insight of what to expect pls?
Will I lose what I currently have on Gutsy by enlarging that partition?(I assume not as you don't lose xp data when making that smaller)

---

### Post by overdrank on 2007-12-31
> **bluebrew said:**
> So it's just that easy...
I'd like to have some insight of what to expect pls?
Will I lose what I currently have on Gutsy by enlarging that partition?(I assume not as you don't lose xp data when making that smaller)

HI and there is always a chance. It is always good to back up your data and the live cd is a good way to resize the windows partition just as you did when you installed. Good luck! :popcorn:

[http://gparted.sourceforge.net/screenshots.php](http://gparted.sourceforge.net/screenshots.php)

---

### Post by bluebrew on 2007-12-31
ok seem to have another issue
system is freezing when playing games,yesterday when playing "bzflag",and just now playing "alien arena",note these are games installed and not online/through browser as all flash games seems just fine
didn't really think nothing of it yesterday as it was once and nothing runs perfect but now twice during game play within the first couple mins so I'm seeing a trend here
any known issues with this? hopefully theres something we can do

any input is and will be appreciated

---

### Post by overdrank on 2007-12-31
> **bluebrew said:**
> ok seem to have another issue
system is freezing when playing games,yesterday when playing "bzflag",and just now playing "alien arena",note these are games installed and not online/through browser as all flash games seems just fine
didn't really think nothing of it yesterday as it was once and nothing runs perfect but now twice during game play within the first couple mins so I'm seeing a trend here
any known issues with this? hopefully theres something we can do

any input is and will be appreciated

Ok I see in this thread you have attempted to install your graphics drivers, what is the model of the card and some specs on the system.

---

### Post by bluebrew on 2007-12-31
and another thing...when I go to System-Administration-Restricted Drivers Manager it tells me "Your hardware does not need any restricted drivers.

Does that mean that I can't edit/manage that or that everything is fine???


Like I previously said I will use this thread to post ne concerns rather then making a new thread for every question,is that ok or acceptable here?
I'm still getting used to all this Linux lingo,used and was very familiar with windows

---

### Post by Don1500 on 2007-12-31
Which ATI card do you have? If you go to System=preferences=appearance=visual effects can you select the custom preferences?

If you can not, reinstall your ATI driver from ENVY, Follow this link, you will be surprized how much more Ubuntu can do with the correct drivers.

 Check here:
[http://ubuntuforums.org/showpost.php?p=4047910&postcount=6](http://ubuntuforums.org/showpost.php?p=4047910&postcount=6)

---

### Post by overdrank on 2007-12-31
> **bluebrew said:**
> and another thing...when I go to System-Administration-Restricted Drivers Manager it tells me "Your hardware does not need any restricted drivers.

Does that mean that I can't edit/manage that or that everything is fine???


Like I previously said I will use this thread to post ne concerns rather then making a new thread for every question,is that ok or acceptable here?
I'm still getting used to all this Linux lingo,used and was very familiar with windows

HI and I believe since you have marked this thread as solved and the issue is installation, that you should maybe start a new thread for graphics issue. For the simple fact that when other user are searching for help that they might find that particular thread and it will help them.:KS

---

### Post by bluebrew on 2007-12-31
Thnx for ur interest (again) overdrank,seems you've been here posting after me everytime lol

My system is:
3.2 ghz Intel Prescott
MSI 865 PE Mobo 800mhz
120 gig HDD Seagate
*9250 ATI Radeon (can't remember if its 9200 or 9250 but pretty sure 9250)
1.5 gig ram pc3200 400mhz DDR Ultra

---

### Post by bluebrew on 2007-12-31
> **Don1500 said:**
> Which ATI card do you have? If you go to System=preferences=appearance=visual effects can you select the custom preferences?

If you can not, reinstall your ATI driver from ENVY, Follow this link, you will be surprized how much more Ubuntu can do with the correct drivers.

 Check here:
[http://ubuntuforums.org/showpost.php?p=4047910&postcount=6](http://ubuntuforums.org/showpost.php?p=4047910&postcount=6)


OK done that and it said graphic card could not be enabled when I selected the bottom option for extra
will check that link in a few
miswell wait n see what over drank says about my specs as well

---

### Post by bluebrew on 2007-12-31
> **overdrank said:**
> HI and I believe since you have marked this thread as solved and the issue is installation, that you should maybe start a new thread for graphics issue. For the simple fact that when other user are searching for help that they might find that particular thread and it will help them.:KS

Thank you for the advice and will make new thread
but will place a link to this as well as it originated here

---

