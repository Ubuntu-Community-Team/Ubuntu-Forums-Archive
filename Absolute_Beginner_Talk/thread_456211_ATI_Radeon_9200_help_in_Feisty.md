---
title: "ATI Radeon 9200 help in Feisty"
date: 2007-05-27
forum: Absolute Beginner Talk
---

### Post by dean_brfc on 2007-05-27
I've had Ubuntu for about a week now and I still can't get my Radeon 9200 to display anything more than 1024x768 or do things like play Chess in 3D. I've tried virtually every online guide etc. and everything comes to a dead end, usually resulting in a blue screen and me having to restore xorg.conf. As much as I really want to ditch Windows for this (dual-booting at present), I think I'll have to remove it from my system if I can't sort it in the next couple of days.

A few of the methods I've tried are:

-[This link on fixing resolution problems](http://help.ubuntu.com/community/FixVideoResolutionHowto). It didn't corrupt xorg.conf if I remember rightly, but it didn't give me more display options.

-Envy. I tried the 'autmomatic install' which told me that it wasn't compatible with my operative system, so I tried manual install (which wasn't actually manual at all, it seemed to install everything simply by choosing that option). However, when Ubuntu restarted I had the blue screen saying X wasn't configured. I read through the Envy website some more and it seems it no longer supports cards below the Radeon 9500.

-The driver from ATI's website. This came in .run format but doesn't seem to do much when I run it (I've changed the permissions thing to allow running). If I run in a terminal it says it's extracting or something, loads for a few seconds, then displays a message...but the window closes too quickly for me to see what it says, then that's it. Is this normal or do .run files need something else to make them work?

Any help would be greatly appreciated. I've tried to refrain from posting as I can usually get over problems by using Google, plus this problem seems to be one that has been asked countless times before...but I really have run out of ideas so this is a last attempt really.

As I've messed about with xorg.conf quite a bit, I think it may be best for me to start with a default one to follow any advice that follows, is there a way I can do this?

---

### Post by johnny4north on 2007-05-27
link - [http://lists.netisland.net/archives/plug/plug-2003-07/msg00462.html](http://lists.netisland.net/archives/plug/plug-2003-07/msg00462.html)
the link above has really detailed info on how to get this card to work.  i m sorry i cant be of more help.  i cheated.  i upgraded my aiw radeon to a Nvidia 4000MX 128mb, to get ubuntu 7.04 to work well for me.  good luck....

---

### Post by riven0 on 2007-05-27
Hmmm, well I've got a Radeon 9200 card. Right now I'm displaying in 1280x1024, but I could go up to 1600x1200 if I wanted. All I did was **sudo dpkg-reconfigure xserver-xorg**, choose all the defaults until I got to the resolution screen. Then I hit the space bar to choose my resolutions and restarted the xserver with ctrl+alt+backspace.

---

### Post by dean_brfc on 2007-05-28
> **riven0 said:**
> Hmmm, well I've got a Radeon 9200 card. Right now I'm displaying in 1280x1024, but I could go up to 1600x1200 if I wanted. All I did was **sudo dpkg-reconfigure xserver-xorg**, choose all the defaults until I got to the resolution screen. Then I hit the space bar to choose my resolutions and restarted the xserver with ctrl+alt+backspace.
Oooh, this has actually worked! (I think the first time I did this I didn't put the "ATI RADEON 9200" thing and just left it has generic something or other).

But...

...despite my nice 1280x1024 resolution, I can't do anything. If I click menus from the top, they don't open. If I click Firefox, it doesn't open. If I click the 'shut down' button...well, you get the idea. In fact, the only thing I can do is press ctrl+alt+backspace. 

Is this a common problem? I hope it's something minor as I got very excited about the resolution being sorted.

Edit: I was going to post my xorg.conf but I'm not sure how I can do it whilst the aforementioned problem exists.

---

### Post by wdetmar on 2007-08-05
Riven0,

The command: sudo dpkg-reconfigure xserver-xorg worked for me. I ran it, choose the defaults and then the proper screen resolution screen for my monitor. However I tried the ctrl+alt+backspace to restart the xserver but when I went to choose resolutions from the Screen Resolutions settings the 1440 x 900 was not available, only what I had before I started. Once I rebooted I was able to change my resolution to the 1440 x 900.

Thanks for your help.

---

### Post by Joje on 2007-08-10
Well, I have the same problem as you guys, but sudo dpkg-reconfigure xserver-xorg with defaults plus adding wanted resolutions doesn't work for me. Every time i try X won't load and i have to reset xorg.conf. I tried editing xorg.conf manually and adding "1280x1024" to all modes but that didn't work either, though X didn't crash this time, I just can't choose the setting. And yes, I tried both restarting X by ctrl-alt-backspaceing and rebooting the whole comp. I'm starting to get desperate here 'cause by tuesday next week we need 20 computers with Feisty and working 1280x1024 resolution at my workplace, and I can't get it to work :S

/Stressed out intern

---

### Post by AR_Kozz on 2007-08-14
I had trouble with my radeon 9200 right off the bat too, as soon as I did the Feisty upgrade. I used to 
use ATI's fglrx, but when I tried to reinstall it with Envy I got the same "not compatible" message. Unwilling to believe
it, I went to the blog of Envy's author, Alberto Milone, and asked if that meant fglrx was incompatible with 
Feisty. He said "yes." 

And I've tried directly using ATI's download. Dean I bet the message you couldn't see was "substitution error, deleting tmp/blahblahblah/fglrx" cause that's exactly what it did to me. That is, the package never even successfully self-extracts.

Which should be a moot point, because if you search the Ubuntu repo's for "fglrx" you'll find that it is already
installed. Some people have mentioned simply going to "system/restricted drivers" and checking a box next to the ati proprietary driver. However when I do that I am smugly told by Feisty that I "don't need any restricted drivers," with an "OK" box the only option.

I shouldn't even need fglrx. I need direct rendering, without which any OS is useless to me. With Dapper the open-source driver rendered just fine. But not now.

The Radeon 9200 is old but is far from obsolete, and Ubuntu should not be abandoning it.

---

### Post by Vaan on 2007-08-15
This is just crazy. I have the same GPU on my notebook (ATi Radeon 9200) based on the 9100 IGP.

I've been using the default "ati" driver from xserver and I had desktop effects working and everything seemed to be working fine. Then about 2 days ago I installed fglrx-control or something like that and totally screwed me up. I can no longer enable desktop effects and it's driving me nuts.

I'll try and figure this out and post my findings.

---

### Post by dougfractal on 2007-08-15
> I installed fglrx-control
I guess apt also installed fglrx*

sudo apt-get remove fglrx*
sudo apt-get install libgl1-mesa-glx libgl1-mesa-dri   # as fglrx over wrote these.

---

### Post by Vaan on 2007-08-15
Many thanks [dougfractal]("http://ubuntuforums.org/member.php?u=230202")! I now have direct rendering working again. Everything is back like it used to be, desktop effects and everything.

This makes me wonder if your solution will help out the others in this thread.


Okay if you have an ATi card below the 9500 series (such as the 9200) then try and follow these steps and let us know your results.

Open up a terminal window and type these commands:
```

sudo apt-get remove fglrx*
sudo apt-get install libgl1-mesa-glx libgl1-mesa-dri

```After you've finished running the previous commands type this in your console/terminal window:
```

sudo dpkg-reconfigure xserver-xorg

```The blue xerver configuration should show up. For the x server driver select **ati**. Next just continue to follow the directions (when you get to the screen resolution area make sure to select your resolution(s) using the spacebar, when done press enter) and after it's all done press **ctrl alt backspace** to restart the X11 display.

After you login back to the desktop open up a terminal window again. Type in:
```

glxinfo

```Near the top you should see something that says:
```

direct rendering: YES/NO

```It should say Yes. If it says No that means either something went wrong, or this solution did not work for you.

If it is Yes, then your display driver should be configured properly and you can enable Desktop Effects and play your games and such.

---

