---
title: "DVD players not working"
date: 2008-03-30
forum: Absolute Beginner Talk
---

### Post by hozo on 2008-03-30
I have recently bought for my daughter Acer4315 with Ubuntu7.10.
This is our first contact with linux.

I have followed the guide supplied with the product and downloaded all additional bits, updated it, but the DVD players were still not working.
From desperation I have then followed various advices on number of forums / sites in order to make it work - nothing solved the problem.
 In addition to Totem and Mplayer I have have tried the VLC media player.
At this stage after spending most of yesterday on it, I am frustrated.

Totem starts but it does not get to read the dvd or play it, and gets stuckon this / no controls work. At one stage it played the first "entry" part of the DVD without sound and then got stuck.

Mplayer does not even respond to DVD inserted and its controls do not work.
.
VLC player works til I open the DVD with it. Then it starts playing  the DVD without sound and control buttons cease to respond to anything (as in case with Totem). 
The players can only be stoped / disengaged by "forced quiting" function.

The sound is working ok in other application and I have managed to get Banshee and ipod going fine.

Can anybody offer some suggestions?
Alternatively, iIs there any Ubuntu center in Melbourne where I could get this fixed for a fee?

Thanks for any advice

---

### Post by smurphy_it on 2008-03-30
Did you install the libraries needed to decode a DvD in order to watch it ?

In a terminal one would type

**gksudo apt-get install libdvdcss2**

---

### Post by mgmiller on 2008-03-30
> gksudo apt-get install libdvdcss2

I don't think that will work unless he has the medibuntu repositories installed.

Try going to the medibuntu website for instructions, it's really easy, just copy and paste a few lines into terminal and you are set:
[http://www.medibuntu.org/]("http://www.medibuntu.org/")

---

### Post by hozo on 2008-03-30
I have repeated it already few times - it tels me that i have there the latest and then it comes with the following (don't know if something more should be done).

The following packages were automatically installed and are no longer required:
  libmozjs0d
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
julia@ACER:~$

---

### Post by mgmiller on 2008-03-30
Have you also installed the restricted extras package?

For Ubuntu:
```
sudo apt-get install ubuntu-restricted-extras

```


For Kubuntu:
```
sudo apt-get install kubuntu-restricted-extras

```

For Xubuntu:
```
sudo apt-get install xubuntu-restricted-extras
```

The only other thing I can think of is if the region isn't set correctly on the DVD drive, it may not play a commercial movie correctly, if at all.

"Regionset is a small utility which displays and sets
the region/zone setting of a DVD drive, allowing it to decrypt
the DVD's sold in this geographical zone. Hardware vendors
often limit the number of such modifications, but it is
necessary to set it at least once with a brand new drive."

```
sudo apt-get install regionset
```

it is then run from terminal by typing the command:
```
regionset
```

It needs to have a disc in the drive to work.

I think you can only change this setting 5 times or some such and then it gets permanently set to the 5th region you entered.  Usually, you only have to enter you home region once, though.

---

### Post by smurphy_it on 2008-03-30
To get started with the codecs, we are going to install all the GStreamer library packages available on the repository:

$ sudo apt-get install gstreamer0.10-ffmpeg gstreamer0.10-plugins-ugly gstreamer0.10-plugins-ugly-multiverse gstreamer0.10-plugins-bad gstreamer0.10-plugins-bad-multiverse

From now on, you should be able to play any divx, non encrypted DVD and music.

In order to be able to play encrypted DVDs, we need to install libdvdcss2 package. As I said earlier, this package is not provided by Ubuntu for legal reasons. However, a script is supplied in order to easily install this package. This script is provided by libdvdread3 package.

Let's go back to the command line and, for people using Ubuntu Gutsy 7.10, Ubuntu Feisty 7.04 or Ubuntu Edgy 6.10, type:

$ sudo /usr/share/doc/libdvdread3/install-css.sh

People using releases prior to Edgy Eft, such as Ubuntu Dapper 6.04 will type:

$ sudo /usr/share/doc/libdvdread3/examples/install-css.sh

Give that a go.

Info found [here]("http://www.debuntu.org/how-to-play-dvd-under-ubuntu-linux").

---

### Post by hozo on 2008-03-30
Medibutu repositories installed and it came with this -

Reading package lists... Done
W: Duplicate sources.list entry [http://archive.canonical.com](http://archive.canonical.com) gutsy/partner Packages (/var/lib/apt/lists/archive.canonical.com_ubuntu_dists_gutsy_partner_binary-i386_Packages)
W: You may want to run apt-get update to correct these problems
julia@ACER:~$ 

so I have updated it 

regrettably, no improvement resulted from it - all DVD players problems remain as before.

---

### Post by hozo on 2008-03-30
restricted extras and regions done; no change

---

### Post by perixx on 2008-03-30
Hello!


I've been encountering some trouble as well with DVD playback; this is not so trivial a topic:

At first, you've got to distinguish between playing back DVD's and playing back MPG's and WMV's with Firefox/Internet. For the latter, you'll need some plugin, respective to the browser you're using. For playing back DVD's, you need the decryption libraries, as stated above (libdvdcss2). 
Best open your Synaptic packet manager and check, if it's installed. If not, you'll have to go to the Medibuntu homepage and see how to set up their repositories. Then, you can update the repos and simply install it via Synaptic; of course, the Terminal commands might be easier (and quicker) to use. 

For playing back restricted formats like 'wmv', there's a package you need to install: 'w32codecs'. This requires that you allow to use the 'restricted' repositories in your repo manager.
From what I can tell, every media player has its advantages and drawbacks. For home DVD watching, VLC is not bad a choice - it should have everything you need (except the libdvdcss2 package). But the integration into Firefow is not that good. 

Regarding the best format-compatibility, Totem / Xine, along with the plentyful availible media libraries is maybe the best, though not in terms of video quality (so I have experienced). You'll find some exotic and not-so-common media support here, like some weird types of streaming formats or AVI playback. Integration into Firefox appeared to be a bit weird to me, though. 

I had the best experiences with Mplayer / SMPlayer / Mplayer-plugin. Mplayer is the actual backend app, SMPlayer is merely a (rather good and feature-rich) frontend for home video watching. Mplayer comes with its own, very complete pack of codecs (downloadable on their homepage), and the video quality is pretty good. The integration into Firefox is not that good, though it works; you can't save streamed videos, which is annoying at times (but then again, most other player cannot either). 

When playing back internet vids, a different frontend pops up, regarding which media format you use (varies even along different wmv formats). But I've seen happening this as well with Totem-Mozilla, and I liked Mplayer better. This is due to the fact that Firefox handles the mime-types for itself, in a separate config file (but so far, I couldn't find out where exactly - didn't try that hard, though). Sadly, you can't simply choose 'mplayer-plugin' in the FF options for some media types - you'd have to edit the mentioned config file by hand (but that might also apply to other players. 

Btw.: there's some 'Mozilla Connectivity Plugin' out there - from many reports I've read, it's badly programmed and probably messes up your Firefox configuration or worse. Sou you'll maybe not like to use that one.

Another thing to keep in mind: some DVD drives are 'more compatible' to a wider range of CD/DVD media (depending mostly on the firmware) and some are prone to fail on copy protected discs. This also refers to playback in Windows(!) Say thanks to the content industry and return those media to the store. Also, consider to buy a different DVD player's brand next time - if playing back in a 'consumer electronics' player works, there's no seeying why playing back on a PC  doesn't.


perixx

Hope that helped you a little ;]

perixx

---

### Post by mgmiller on 2008-03-30
Just wondering, we should rule out a hardware problem with the optical drive.  

Will the drive mount and display the contents of a DVD or CD that just contains data instead of a movie?  Will it play a music CD?

If you have access to another machine with a burner, try making a DVD or CD that you just burn a video file to, like an .avi or similar.
See if the drive will read and play this kind of non encrypted media.

---

### Post by yesterday on 2008-03-30
Ok sorry to ask some obvious questions, but :

Firstly, are you trying just one or many DVDs?
Secondly, do you still have a Windows partition on the same computer that you can test DVD drives with?
Have you tested the drive with data DVDs?
Can you access data DVDs on the computer?
Can you play audio CDs?


Also, alot of advice has been given in the thread.  Just to confirm, did you install libdvdcss from the medibuntu repos or did you use the install script in /usr/share/doc/libdvdread/.  And can you confirm that in synaptic under the section, Installed (local or obsolete), libdvdcss2 is listed?

---

### Post by hozo on 2008-03-30
It plays sound  Cd's fine

I havenow  tried DVD with clips of various formats. They automatically open in a directory as thumbs.
But when trying to play them:
Mplayer - nothing happens and " failed to open"
Totem - gets stuck while trying to open it; when I try to close it "failed to respond"  and I have to "force quit"
VLC palyer- opens and plays the clip, but without a sound and the controls do not function (stuck in playinig it). On completion  of the clip or if try to close it  while playing "failed to respond"  and I have to "force quit".

So it does not seem to be a hardware problem.

---

### Post by mgmiller on 2008-03-30
Try going to System > Preferences > Appearance and select the Visual effects tab.  
Try clicking next to "None".  
This will turn off the compiz effects if they are running.  

See if you can play videos now.

---

### Post by hozo on 2008-03-30
I have tried various DVD's all playing fine on other PC and DVD home  players except on this notebobok.
I have just tested data DVD and apears to be fine. All directories open and visible. various files opened without problem (pictures, text,...)

---

### Post by hozo on 2008-03-30
I dont have windows on this Acer;  only Ubuntu

---

### Post by hozo on 2008-03-30
The visual effects were already set on NON.
so I have not changed it.

---

### Post by mgmiller on 2008-03-30
Lets try changing some of the settings for the major players you have installed.

First, Totem (gstreamer)
Open a terminal and type 
```
gstreamer-properties
```
Press Enter.
 Click the Video tab.
 Under Default Video Plugin select "X Window System (No Xv)".
 Click Test to verify that video playback is working (you should be able to see the standard TV testing colour stripes).
 Click Close

Next, VLC
Start VLC and click on Settings, then Preferences.
 Expand Video by clicking the + and then expand Output modules. 
You will notice several options for output device.

 Select the item Output modules, and notice the checkbox at the bottom right that says Advanced options. 
Check the box, and now you have the option to select a different output device.
 Pick X11 video output
 Click on Save and you are set.

Finally, Mplayer:
Start Mplayer
 Right-click on the screen and select Preferences
 Select the Video tab and under Available Drivers select "X11 (XImage/Shm)"
 Click Save and restart the program for the setting to take effect.

See if any of the above now work for you.

---

### Post by hozo on 2008-03-30
I have done all described on settings of all three players. It has not improved any one of them - problem remains unchanged.

Regrettably, I will soon have to leave for work.

Thank to all of you for trying to help me !!!!!!

I will be back in 9 hrs to continue trying.
Please don't give up on me.

---

### Post by perixx on 2008-03-31
> First, Totem (gstreamer)
Open a terminal and type:
gstreamer-properties
Press Enter.
 Excuse me, I don't know Totem very well, but I thought 'gstreamer' plugins only apply to gstreamer-library compatible apps like 'Xine'? From what I know, Mplayer uses it's own set of codecs? Maybe I'm wrong...

> Click the Video tab.
Under Default Video Plugin select "X Window System (No Xv)" For me, 'XV' and 'X11' video plugins were the only one's that worked on my system (until I installed the proprietary graphics drivers)...

Btw.: there's a little weirdness about Mplayer/SMPlayer: it will only playback Audio and DVD media, if the 'play CD/DVD' button from within the app is being used... this also requires, that your drive is mounted to where the player is looking for it (check it in the options and /etc/fstab file). In fact, I was only able to play back Audio CD's, by linking the 'autoplay' feature for the optical drive of Ubuntu to SMPlayer (might apply to Mplayer, too). This isn't necessarily the case with DVD's, though.  


perixx

---

### Post by mgmiller on 2008-03-31
> Excuse me, I don't know Totem very well, but I thought 'gstreamer' plugins only apply to gstreamer-library compatible apps like 'Xine'? From what I know, Mplayer uses it's own set of codecs? Maybe I'm wrong...


Totem can use either the gstreamer or xine back ends.  The default install in Ubuntu is with the gstreamer backend, hence the command "gstreamer-properties".  

Mplayer does use its own codecs.

> For me, 'XV' and 'X11' video plugins were the only one's that worked on my system (until I installed the proprietary graphics drivers)...

What kind of video card do you have?  For me, Nvidia has always worked with the suggestion I gave.  ATI on the other hand, may behave differently.  Or for that matter, different Nvidia drivers may behave differently.  In any case, it's easy to change the settings and try.

---

### Post by perixx on 2008-03-31
Ah, ok. I didn't notice he also used totem. Or it's me being to Mplayer-focused :)

In fact, I do have an Ati card - XV is probably the most reliable video plugin on my side, along with X11, but the first seems to have a tad bit better video quality...

perixx

---

### Post by hozo on 2008-03-31
Hi everybody, I am back and ready to try anything more you can suggest.
I do not have a  preference for any of these  players. I would be glad if any one would play DVDs. The quality is at this stage unimportant.

Question I have is - is it possible that the Ubuntu wasn't initially installed correctly, and would it be of any benefit to uninstall everything and download + install Ubuntu again (this has once solved my problems with MS windows on another PC). ????

---

### Post by mgmiller on 2008-03-31
You could try making a live CD and booting off that and try playing an unencrypted avi.  If it needs a codec for that it should download it and install it for you.  You could try either the current Gutsy 7.10 or try the beta of the new 8.04 hardy Heron.  If they work, then you may want to try reinstalling.

---

### Post by hozo on 2008-03-31
I do no know much about computer stuff and will need some more help with this advice.
How do I make "live CD" and how do I boot off that.
Likewise the unencrypted AVI - I only know that some video comes with the AVI at theback of the file name.

---

### Post by mgmiller on 2008-04-01
To make a live CD, go to ubuntu.com and download the Ubuntu 7.10 desktop edition.  It should be selected by default.

[http://www.ubuntu.com/getubuntu/download]("http://www.ubuntu.com/getubuntu/download")

Once you have the file, it should have a file name ending in .iso

Just right click the file and select Write to Disc from the choices that pop up.

Obviously, you will need a blank CD in your burner.

Once it's done, just boot off that disc.  Select the first option at the top to give you a desktop and you can try to play things again.

Files ending in .avi or .mpg or even possibly .wmv should play without too much fuss.  For those types of files, if it needs a codec, the codec wizard should walk you through installing them.

---

### Post by perixx on 2008-04-01
Hey, if you don't like bothering about how to set up codecs and stuff, you could try out 'Mint' Linux...

It's coming in 3 different flavours, as Ubuntu, and in fact is just an Ubuntu derivate, so to say (uses the same repositories). The special thing about it: you can downoad two different versions - one 'clean' version and one that contains many of the most important proprietary codecs and software, that are kept out of the vanilla installation of Ubuntu ('restricted' content, such as codecs, flashplayer and so on). So, you might give it a shot - unlike Ubuntu, the 'full' Mint version should handle DVD playing out-of-the-box.

perixx

---

### Post by hozo on 2008-04-01
I have looked into the Mint Linux and became worried that could cause other problems (not recognizing wifi card,...) So I have made CD of the 7.10 Ubuntu.

One more question before I try the booting from CD.
When trying to play a DVD (avi)  I have to first remove the CD. Would that not interfere with the process?

Thanks

---

### Post by Harisz750 on 2008-04-01
Hi... i must say i have exactly the same problem here... Nvidia grafic card and ubuntu 7.10 gutsy,  dvd's are playing out of the box in my xp partition but when in totem.. it stucks.. also tried vlc.. but the same problems.. also tried everything above..also tried reinstallation....  please help us!!!!!!

---

### Post by yesterday on 2008-04-05
ok so it seems the problem has more to do with video playback than DVDs.  I take it you cannot get ANY video files to playback?  Run vlc {filename} from the command line and post the output

---

