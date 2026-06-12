---
title: "Bleached video with totem.  Black screen with VLC and few other anomalies."
date: 2007-09-25
forum: Absolute Beginner Talk
---

### Post by curiousnoob on 2007-09-25
I have just installed Ubuntu Fiesty Fawn and for some reason I am unable to get the video to work correctly.
Originally, when I tried to open up a video file, format did not matter, I would see a quick flicker of video and then it went black. The audio continues as normal and the really weird part is that if I resize the window I can see the video playing as long as the size is being adjusted but as soon as I stop it goes to black again.
I have tried both Totem and VLC with the same results.

Just to see what would happen I tried switching to totem with the xine backend. The files now play with totem and gxine but are all washed out. 
VLC still has the original problem. For the split second I see video everything looks correct.  No bleaching at all.  And if I resize the window I see the video during the resize.  
I'm baffled and cannot find anyone who has had this problem in the past.

---

### Post by alienexplorers on 2007-09-25
Did you load all the codec's and plugins for your video viewers?  
> [https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)
> [https://wiki.ubuntu.com/EasyCodecInstallation?highlight=%28codec%29](https://wiki.ubuntu.com/EasyCodecInstallation?highlight=%28codec%29)

---

### Post by curiousnoob on 2007-09-26
> **alienexplorers said:**
> Did you load all the codec's and plugins for your video viewers?
Yes, I have followed all of those instructions but the problem persists.  I have noticed that if I restart the computer and load a movie into VLC and don't touch any controls it will play just fine.  As soon as I click on the window it goes to black.
For good measure I even installed every gstreamer package I could find but no luck.:(

---

### Post by curiousnoob on 2007-09-28
Is there any way to find out exactly what codec a file uses and where to locate that codec in the repositories?  
I can't figure this thing out.

---

### Post by curiousnoob on 2007-09-28
Bump?

---

### Post by CaptainStabbin on 2007-09-30
Hey buddy, I just registered to answer your question since I had the same problem and maybe the solution that worked for me might work for you too. 

Download "mplayer" and "mplayer skins" from the Synaptic Package Manager and it seems those codecs are more compatible with our type of video cards. 

Hope this helps!

---

### Post by curiousnoob on 2007-10-02
> **CaptainStabbin said:**
> Hey buddy, I just registered to answer your question since I had the same problem and maybe the solution that worked for me might work for you too. 

Download "mplayer" and "mplayer skins" from the Synaptic Package Manager and it seems those codecs are more compatible with our type of video cards. 

Hope this helps!

I already had both installed.  Thanks for trying though.  At this point I'm thinking I should just do a reinstall.  I don't know what the problem is.

---

### Post by anewguy on 2007-10-02
You may be having a problem with overlay - I had it and couldn't get mine to work, but there is link that mentions some things to try:


  #41   Report Post  
Old July 7th, 2007
anewguy anewguy is online now
Quad Shot of Ubuntu
	  	
Join Date: Jun 2007
Location: Sterling, IL
Beans: 461
Ubuntu 7.04 Feisty Fawn User
Unhappy Re: Help with wmv, etc?
To all reading this thread with a similar problem: I upgraded to 7.04, which of course messed up my "via" driver for xorg.conf, so I went back to the default "vesa" driver until I get time to go through building the driver again. The end result, is that in 7.04, using the default "vesa" driver in xorg.conf, movies, .wmv, etc., play fine. I believe this indeed points to the openchrome driver as the root of my problem.

If you have an integrated graphics processor using the k8m800(?) chipset, you will by default get lower resolution but be able to play movies, etc., if you use the default "vesa" driver.

If someone has a way around this please post back to this thread.
__________________
Edit/Delete Message Reply With Quote Multi-Quote This Message Quick reply to this message
anewguy
View Public Profile
Send a private message to anewguy
Find all posts by anewguy
Add anewguy to Your Buddy List
  #42   Report Post  
Old July 8th, 2007
anewguy anewguy is online now
Quad Shot of Ubuntu
	  	
Join Date: Jun 2007
Location: Sterling, IL
Beans: 461
Ubuntu 7.04 Feisty Fawn User
Re: Help with wmv, etc?
tarek - I found this in a post about using compiz - perhaps it can help you (I don't have the drivers installed so I can't do it now anyway).


#26 Report Post
Old 2 Weeks Ago
crimesaucer's Avatar
crimesaucer crimesaucer is online now
Has an Ubuntu Drip

Join Date: Jan 2006
Location: Traveler
Beans: 709
Xubuntu 7.04 Feisty Fawn User
Re: Compiz Fusion: A guide with a warning for new users.
I fixed my Xine movie palyer like this: The Settings-->--Set Up-->--Video-->--I changed the driver from "auto" to "xshm" and it worked for playback.

I also fixed the transparent video like this: ccsm-->--General-->--Opacity Settings-->--Window Opacities-->-- then edit the string and take "Unkown" off of the list.
__________________
We are the music-makers, and we are the dreamers of dreams- Willy Wonka.
Reply With Quote
__________________
Edit/Delete Message Reply With Quote Multi-Quote This Message Quick reply to this message
anewguy
View Public Profile
Send a private message to anewguy
Find all posts by anewguy
Add anewguy to Your Buddy List
  #43   Report Post  
Old July 10th, 2007
tarek's Avatar 	
tarek tarek is offline
Way Too Much Ubuntu
	  	
Join Date: May 2006
Location: Canada
Beans: 222
Ubuntu 7.04 Feisty Fawn User
Re: Help with wmv, etc?
Quote:
Originally Posted by anewguy View Post
tarek - I found this in a post about using compiz - perhaps it can help you (I don't have the drivers installed so I can't do it now anyway).


#26 Report Post
Old 2 Weeks Ago
crimesaucer's Avatar
crimesaucer crimesaucer is online now
Has an Ubuntu Drip

Join Date: Jan 2006
Location: Traveler
Beans: 709
Xubuntu 7.04 Feisty Fawn User
Re: Compiz Fusion: A guide with a warning for new users.
I fixed my Xine movie palyer like this: The Settings-->--Set Up-->--Video-->--I changed the driver from "auto" to "xshm" and it worked for playback.

I also fixed the transparent video like this: ccsm-->--General-->--Opacity Settings-->--Window Opacities-->-- then edit the string and take "Unkown" off of the list.
__________________
We are the music-makers, and we are the dreamers of dreams- Willy Wonka.
Reply With Quote

I tried it using mplayer and it worked! Thanks a lot

tarek
__________________
CSMonkey Blog
CSMonkey TV Remote: desktop TV remote for IVTV supported cards
Registered Linux user number 448653
Reply With Quote

---

### Post by mysticmatrix on 2007-10-02
> **curiousnoob said:**
> I already had both installed.  Thanks for trying though.  At this point I'm thinking I should just do a reinstall.  I don't know what the problem is.

Are desktop effects turned on? If yes, try to turn them off and see if problem persists.

---

### Post by Kynan on 2007-10-06
This worked for me i was having the same problem till i turned off beryl Thanks. any ideas on how to fix it so i can have beryl running?
EDIT: found a solution here [http://ubuntuforums.org/showthread.php?t=314813](http://ubuntuforums.org/showthread.php?t=314813)

---

### Post by Linux_Man on 2007-10-06
Beryl messes up lots of graphic-intensive work such as VMs and some games, so I would just have the beryl manager sit in your tray and change the Window manager to metacity or your desktop environment's defaults whenever you want to watch a move, I have to do that to get Battle For Wesnoth to run correctly

---

### Post by anewguy on 2007-10-08
A suspicion of using one of the "eye-candies" for Linux was why I made my previous post.  The solution listed there does work so you can leave the eye candy running.

---

### Post by Kynan on 2007-10-08
amen to that :D whats the use of all those cool effects if you cant play a simple video.

---

### Post by curiousnoob on 2007-10-09
Turning off Compiz Fusion solved the issue with VLC and Gxine showing only a black screen.  I have no idea why it would only effect those two programs though.

The only problem now is that all of my videos are still "bleached".  I can manually turn the contrast and brightness down in the preferences but this introduces pretty severe artifacts and banding.  None of this happens with videos I view through firefox.  Any ideas?

---

