---
title: "Ladies and Gentlemen"
date: 2007-07-03
forum: Absolute Beginner Talk
---

### Post by netcrammer on 2007-07-03
Hi all-

Today is Day One of my Ubuntu experience. Tired of being tormented by an OS that 
consistently crashes (need I say more?). I have installed Ubuntu Linux on my laptop.
So far -great! 

Just a few needs: I am in need of the following:

-Newsgroup reader (Binary downloads) -what can I use?
-Does Linux support DIVX? 

My laptop is a DELL INSPIRON 9100.

TIA!:popcorn:

---

### Post by ukripper on 2007-07-03
Yes Linux supports DIVX. 

For more information read this guide

[http://ubuntuguide.org/wiki/Ubuntu:Feisty](http://ubuntuguide.org/wiki/Ubuntu:Feisty)

---

### Post by netcrammer on 2007-07-03
Hiya.

Ok. 

Problem 1. (bare with me---linux noobster!) 

--I cannot mute or lower my audio (sound) = In addition the master control says its "muted"
   however I can hear sound regardless.
--The volume control buttons on my laptop seem to display the balance but it actually doesn't lower or raise
  the volume.

:)

TIA.
:p

---

### Post by netcrammer on 2007-07-03
Hiya.

Problem 2. 

Within the Device manager my video drivers are incorrect????

-I have a AT RADEON 9700, however it is listed as :RADEON 9600 M10

how do I update the video drivers? and where do I find them?

TIA

---

### Post by cogadh on 2007-07-03
> **netcrammer said:**
> Hiya.

Ok. 

Problem 1. (bare with me---linux noobster!) 

--I cannot mute or lower my audio (sound) = In addition the master control says its "muted"
   however I can hear sound regardless.
--The volume control buttons on my laptop seem to display the balance but it actually doesn't lower or raise
  the volume.

:)

TIA.
:p
The default control in Ubuntu is usually "Headphones". Right-click on the volume control and select "Preferences" (I think, I'm not in front of my 'Buntu box right now). Then you will just need to select the appropriate default channel for the volume slider to control. I can't say which one it will be, it's different depending on the hardware. Just try them until you get the one that changes the volume.

---

### Post by netcrammer on 2007-07-03
awesome. Thanks. I had to change my preferences and it worked.

THANKS!

NEWSREADER ANYONE? lol---for binary downloads---need it bad! :)

---

### Post by grim1234 on 2007-07-03
You can use a prgram called pan for binary news. [http://pan.rebelbase.com/screenshots/screenshot.png](http://pan.rebelbase.com/screenshots/screenshot.png)

There is also klibido which works well, but it's KDE so there will be a fair bit of downloading before it is installed (still not to bad though). Here's a screenshot :[http://klibido.sourceforge.net/group.html](http://klibido.sourceforge.net/group.html)

To install it open a terminal (Applications > Accessories > terminal )

and type

> 
sudo apt-get update
sudo apt-get install klibido


---

### Post by netcrammer on 2007-07-03
ATI drivers:

Currently I see the following:

Section "Screen"
	Identifier	"Default Screen"
	Device		"ATI Technologies Inc RV350 [Mobility Radeon 9600 M10]"
	Monitor		"Generic Monitor"


---however my video card is a 9700? how and where do i find these specific drivers.

TIA.

---

### Post by Nythain on 2007-07-03
xorg has a habit of guessing the wrong card... at least it does for me... it told me my 9550 was a 9600, it tells me my gforce fx 5200 is a 5500, etc.

as long as everythign is working just fine, i would leave the identifier alone... my guess would be that since all the r series cards (yours is actually an R300 and not an rv350) probably use the same drives, x just picks a generic card and says you have it

---

### Post by netcrammer on 2007-07-03
My concern is the following:

when I play a DVD and minimize or resize the screen (currently using default player Totem)
the screen dissappears and flickers.

Perhaps another player is better? any suggs?

TIA.

---

### Post by Antonio44 on 2007-07-03
I don't know if it does DVD, I think it probably does. But try VLC media player it plays just about anything that you throw at it. 



A.

---

### Post by sailor2001 on 2007-07-03
vlc is my choice of viewers. it's in the repositories (System / administration /synaptics)

---

### Post by netcrammer on 2007-07-03
great thanks all.

VLC works great----except when I try to resize the window it goes blank (black screen).

What can I use to create ISO images?

TIA.

---

### Post by netcrammer on 2007-07-03
Where can I find a basic outline of the contents of the folders found in the root?

what does lib contain?
what does sys contain?

etc....

TIA

---

### Post by cogadh on 2007-07-03
I highly recommend you spend some time reading some Linux newbie info websites. When I first started with Linux, I found the info on [www.justlinux.com](www.justlinux.com) to be very helpful. In fact they have a very basic description of the file system [here]("http://www.justlinux.com/nhf/Filesystems/Filesystems_Directories_and_Devices.html").

Also, you may want to hit a bookstore or library for some Linux books. There is actually an "Official Ubuntu Book" released by Canonical that is supposed to be very good.

---

### Post by Damanther on 2007-07-03
Creating an iso image will depend on what type of iso image you want to make, DVD? CD? etc.
DeVeDe will let you create DVD iso images for example.

MPlayer has been working the best for me. VLC works well too, but I get some garbage when trying to play some .mov and .avi files with it. MPlayer is the only one I've found to play all the codecs I use appropriately.

K3b for burning imo

Damanther

---

### Post by netcrammer on 2007-07-03
awesome guys....thanks for all the help! I haven't been this excited since
the release of DOS! LMAO!

---

### Post by Jimmyfj on 2007-07-03
Welcome to Ubuntu world :) Hope you'll get as much fun from using Linux as have I.

Just wondering, could all them unhappy Winblows-users have know about this:

[http://news.softpedia.com/news/Forget-about-the-WGA-20-Windows-Vista-Features-and-Services-Harvest-User-Data-for-Microsoft-58752.shtml](http://news.softpedia.com/news/Forget-about-the-WGA-20-Windows-Vista-Features-and-Services-Harvest-User-Data-for-Microsoft-58752.shtml)

---

### Post by cogadh on 2007-07-03
Wow... I don't have words...

---

### Post by moredhel on 2007-07-03
Gnomebaker for ubuntu, K3B for kubuntu for burning applications. ;)

---

### Post by netcrammer on 2007-07-04
wow- i have to say I am impressed with you guys. 
Thank you all for the replies and great posts. 

I have a new one for you: 

I use WPA-Preshared Key for my wireless at home and have not been able to get it to work.
Is this security type supported?

TIA
:p

---

### Post by blastus on 2007-07-04
[quote=netcrammer]What can I use to create ISO images?[/QUOTE]

mkisofs -dvd-video -volid VOLUME_LABEL -o output.iso foldername/

---

### Post by netcrammer on 2007-07-04
After numerous attempts to configure my wireless device----read through some documentation 
on how to view your device to make sure it was enabled. 
I put in my WPA password and nothing....says network 0%????
It is listed as Wireless Ethernet (eth1)
Speed: Unknown
Driver bcm43xx

nothing else--no ip..etc.

Within the Nteowk Settings:
I see: Wireless Connection, roaming mode enabled.

bit loss at this point...

TIA.

---

### Post by guitodd on 2007-07-04
You mentioned Totem... I had similar issues.  VLC seems to be the way to go IMHO.  Here is a link to a great tutorial to get VLC configured to play and rip DVD's.  

[http://www.stchman.com/dvd_rip.html](http://www.stchman.com/dvd_rip.html)

---

### Post by netcrammer on 2007-07-05
my avi playbacks look like this

---

### Post by jamesey on 2007-07-05
> **netcrammer said:**
> Where can I find a basic outline of the contents of the folders found in the root?

what does lib contain?
what does sys contain?

etc....

TIA

I found a good answer to that question
[http://www.ibm.com/developerworks/aix/library/au-speakingunix11/](http://www.ibm.com/developerworks/aix/library/au-speakingunix11/)

---

### Post by netcrammer on 2007-07-05
My RAR problem: basically I don't know how to extract (into a single file) my rar files.
When I try to extract it creates a folder for each file vs. creating the single data file.

any suggs?

TIA.

---

### Post by cogadh on 2007-07-05
Are you extracting them through File Roller or through a terminal command?

---

### Post by netcrammer on 2007-07-05
not sure what file roller is----but I installed unrar and used a terminal to get it to work..
Thanks!

---

### Post by cogadh on 2007-07-05
File Roller is a GUI frontend for several of the archive packages, including unrar (see attached pic). If you double-click on the .rar file, it should automatically open in File Roller and you can extract the files in any way you need. The interface is very basic, but it does the job and extracts the files perfectly.

---

### Post by WiseOdd on 2007-07-08
Well, there allways is you everlasting greatest kick-some-*** VLC player :)

The greatest of em all!

Ihve tried quite a few players; VLC Player beats em all imho!

---

### Post by ukripper on 2007-07-11
Mplayer with swiftfox and Firefox plugins plays all windows media files within browser and also works flawlessly in standalone mode.

---

