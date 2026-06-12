---
title: "How to use my digital camera in xubuntu"
date: 2008-01-31
forum: Absolute Beginner Talk
---

### Post by Indy452 on 2008-01-31
I'm downloading the stable version of Xubuntu 7.10 to try out. 

Will I be able to download pictures from my Canon Powershot A630 camera onto xubuntu?  The software on the install cd has no linux info on it. This camera is half the reason I'm on the computer, so very important to be able to use this with different OS.

Also,  is limewire available in xubuntu? I use that program once and awhile also.

If so could someone link me to a place to get that info.

Thanks, Neal

---

### Post by oedha on 2008-01-31
you can have limewire through gtk-gnutella
or maybe you like azureus.....

i had the a400 and when i plug the usb cable...i can download it...just like i had an flashdisk.....

~E~

---

### Post by bodhi.zazen on 2008-01-31
With most, but not all, cameras you just plug in the USB cable, the turn on the camera, and it is recognized as a removable device (very similar to a USB device or flash card).

Generally you do not need to install any additional software at all.

---

### Post by Indy452 on 2008-02-06
Well so far I have not been able to get the OS to recognize my Canon A630 power shot.
I'm bummed.

Anybody have any other suggestions? My xubuntu7.10 is not recognizing it I guess.

Neal

---

### Post by m9ke on 2008-02-06
I have a Canon A40.  I plug it in using my USB cable, it gets recognized and gThumb downloads my pictures very nicely.  It just works.

I am running Fiesty.  If it doesn't work for you, make sure gThumb is installed.  Also does your computer recognize other USB devices when you connect them?

---

### Post by Indy452 on 2008-02-07
> **m9ke said:**
> I have a Canon A40.  I plug it in using my USB cable, it gets recognized and gThumb downloads my pictures very nicely.  It just works.

I am running Fiesty.  If it doesn't work for you, make sure gThumb is installed.  Also does your computer recognize other USB devices when you connect them?

Yes, It recognizes my mp3 player fine but I can't play the songs (I haven't crossed that bridge yet)

This camera is a very important part of mt computing and its important that I get it recognized on this os.   What is gThumb anyway? Never heard of that.

Neal

---

### Post by gn2 on 2008-02-07
Although it's a KDE application, digiKam should get you sorted.

I have a Canon A75 and Xubuntu. digiKam works a treat.
For me digiKam is for pictures what Amarok is for music, I think it's an excellent application.

Your camera is in the list of cameras that can be used with digiKam.

---

### Post by y-lee on 2008-02-07
> Also, is limewire available in xubuntu? I use that program once and awhile also.


[Frostwire]("http://www.frostwire.com/") is basically limewire for linux

---

### Post by gn2 on 2008-02-07
> **Indy452 said:**
>  but I can't play the songs (I haven't crossed that bridge yet)


In a terminal type (or copy and paste): ```
sudo apt-get install xubuntu-restricted-extras
```

Or use Synaptic Package Manager to add the xubuntu-restricted-extras package.

---

### Post by Indy452 on 2008-02-07
> **y-lee said:**
> [Frostwire]("http://www.frostwire.com/") is basically limewire for linux

Thanks for the link. I installed it but now I don't know for sure how to open it. I checked synaptic and it is installed. I can go to Applications then select network and I see it there but when I click on it nothing happens. What now?

Also where is digiKam to search my camera because I have no idea where else to look.
I really just want to get this camera going most of all.

Thanks, Neal

---

### Post by y-lee on 2008-02-07
what is the output of typing frostwire in the terminal

```
frostwire
```

frostwire uses java is java installed?

---

### Post by Indy452 on 2008-02-07
> **y-lee said:**
> what is the output of tying frostwire in the terminal

```
frostwire
```

frostwire uses java is java installed?

Starting FrostWire...
Java exec not found in PATH, starting auto-search...
ls: /usr/lib/j*: No such file or directory
OOPS, unable to locate java exec in  /usr/lib/  hierarchy
You need to upgrade to JRE 1.5.x or newer from [http://www.java.com](http://www.java.com)
ls: /usr/java/j*: No such file or directory
OOPS, unable to locate java exec in  /usr/java/  hierarchy
You need to upgrade to JRE 1.5.x or newer from [http://www.java.com](http://www.java.com)
ls: /opt/j*: No such file or directory
OOPS, unable to locate java exec in  /opt/  hierarchy
You need to upgrade to JRE 1.5.x or newer from [http://www.java.com](http://www.java.com)

Right there is what she says. I guess this would mean I need to get some java? I need flash player 9 as well to view youtube videos.

I don't understand the whole extract thing. I wish I did and I will,  I just need the help the first time you know.

---

### Post by BandD on 2008-02-07
I have a Canon 30D SLR and I use gtkam (which is the GUI to gPhoto) to download my photos.  I checked on the site:  [http://www.gphoto.org/proj/libgphoto2/support.php]("http://www.gphoto.org/proj/libgphoto2/support.php")

and it shows support for your camera.  

You can get gtkam via Synaptic.  I think that's the easiest way.  Just open it up and type in gtkam, it'll make sure it installs everything you need.  You should be good to go.  If this doesn't work, then you computer may not be recognizing that your camera is plugged in.  There is probably some way to mount it manually, but that's a little over my head.  Also, make sure the camera is turned on to Transfer mode, it is has one.

Let us know!

---

### Post by Indy452 on 2008-02-07
No gtkam in my synaptic package.  Theres gotta be something I'm missing.

I'm finding out that I need loads of applications downloaded onto my OS to make this thing hum.

Is there a guide on using the synaptic package manager? I need to install java and flash as well and don't know how.

Thanks, Neal

---

### Post by BandD on 2008-02-07
Ok, try this, In Synaptic go:

Setting--> Reopsitories 

Then inthe dialog box that pops us, under the UBUNTU SOFTWARE tab, make sure everything is checked except for "Source Code".  Then Click Close, and Synaptic should tell you it needs to refresh the list (if not, click the refresh button in the Synaptic window).  Then see if gtkam is there.

Hope that helps.

---

### Post by Indy452 on 2008-02-07
> **BandD said:**
> Ok, try this, In Synaptic go:

Setting--> Reopsitories 

Then inthe dialog box that pops us, under the UBUNTU SOFTWARE tab, make sure everything is checked except for "Source Code".  Then Click Close, and Synaptic should tell you it needs to refresh the list (if not, click the refresh button in the Synaptic window).  Then see if gtkam is there.

Hope that helps.

That helped thanks. Its in there now what should I do? Theres a gtkam and a gtkam gimp.

Neal

---

### Post by BandD on 2008-02-07
If all you want to do is get the pictures from your camera to your computer use the gtkam.  gtkam Gimp allows you to import your photos directly into Gimp (the photoshop of Linux).  

Simply click the box next to gtkam, and select 'Mark of Installation' and a swirling arrow should appear next to it.  Next, toward the top of the Synaptic window, click the Apply button, and then a box will appear, click apply again and it should download and install the package. 

 When it's finished, go to the Applications menu in the top toolbar/menu and it should have installed gtkam in the GRAPHICS section.  Click the icon, and gtkam should open.  Plug in the camera and turn it on.  Click IGNORE if a box pops us that isn't gtkam.  Then, in the gtkam window, got to: Camera--> Add Camera.  In the box that pops up, scroll through the cameras until you see your model and select it (or try the detect button).  And then you should be good to go.  Play around with it a little.  But it should work for you!

EDIT: I didn't realize that you were on Xubuntu, so the directions for HOW TO GET TO gtkam through the desktop will be slightly different.  I've never used Xubuntu, so I'm not sure of the exact path you would take.  But it'll be installed somewhere in your applications menu I'm sure.

---

### Post by gn2 on 2008-02-08
In digiKam, click Camera> Add Camera> Add> and select your camera from the list.

---

### Post by y-lee on 2008-02-08
> **Indy452 said:**
> Right there is what she says. I guess this would mean I need to get some java? I need flash player 9 as well to view youtube videos.

I don't understand the whole extract thing. I wish I did and I will,  I just need the help the first time you know.

Yep you need Java, you have several options here and several ways to go about it. Linux is all about choice. lol. the easiest thing to do is to just get java from the repos.

System > Administration > Synaptic Package Manager

Make sure you have all the repositories enabled under Settings > Repositories, do a 'Reload' and search for sun-java6-bin sun-java6-jre sun-java6-plugin sun-java6-fonts and install them all.

Once it downloads the packages and begins the installation, you’ll get a screen that contains the Sun Operating System Distributor License for Java and hit Enter to continue. You’ll see a dialog that asks you if you agree with the DLJ license terms. Select Yes, and hit Enter; the JRE will finish installing.

If at this point you don't see a dialog post back you are missing something.

You’ll want to confirm that your system is configured properly for Sun’s JRE. This is a two-step process.

First, check that the JRE is properly installed by running the following command from a terminal.

```
java -version
```

You should get similar output

```
java version “1.6.0&#8243;
Java(TM) SE Runtime Environment (build 1.6.0-b105)
Java HotSpot(TM) Client VM (build 1.6.0-b105, mixed mode, sharing)
Testing Java Plugin for Firefox
```

open Firefox and typing```
about:plugins
``` in the address bar and check for java plugin

If you wish to use some java other than Suns, see [Java]("https://help.ubuntu.com/community/Java")

(NOTE: I always use Suns it seems to work better, some don't because of copyright issues. )

Monkey blog has a really nice introduction to install things in Ubuntu, see [How to install ANYTHING in Ubuntu]("http://monkeyblog.org/ubuntu/installing/"). Be  aware tho it is not always as easy as he makes it seem, dependency issue can be hard to figure out when you are compiling source code.

If all this works now try frostwire :popcorn:

---

### Post by y-lee on 2008-02-08
> **Indy452 said:**
> I need flash player 9 as well to view youtube videos.


From what I've saw on the forums the flash plugin in the repos is not working well in Gusty right now. I use dapper and have had no problems but I got the below from [Complete Streaming, Multimedia & Video How-to]("http://ubuntuforums.org/showthread.php?t=661833") here on the forums. It should work.


**The flash plugin (for YouTube) in the repo is currently broken.** If you are fairly new to Ubuntu and your flash plugin doesn't seem to work, do the following:

Download it [here]("http://ubuntuforums.org/attachment.php?attachmentid=53648&stc=1&d=1198033466") and then save or move it to your home folder, then open the Terminal (Applications>Accessories>Terminal) and paste this command into it;

```
sudo dpkg -i flashplugin-nonfree_9.0.115.0ubuntu0.7.10_i386.deb
```

Now do the about plugin thing in firefox and see if it is there :)

---

### Post by Indy452 on 2008-02-09
> **BandD said:**
> If all you want to do is get the pictures from your camera to your computer use the gtkam.  gtkam Gimp allows you to import your photos directly into Gimp (the photoshop of Linux).  

Simply click the box next to gtkam, and select 'Mark of Installation' and a swirling arrow should appear next to it.  Next, toward the top of the Synaptic window, click the Apply button, and then a box will appear, click apply again and it should download and install the package. 

 When it's finished, go to the Applications menu in the top toolbar/menu and it should have installed gtkam in the GRAPHICS section.  Click the icon, and gtkam should open.  Plug in the camera and turn it on.  Click IGNORE if a box pops us that isn't gtkam.  Then, in the gtkam window, got to: Camera--> Add Camera.  In the box that pops up, scroll through the cameras until you see your model and select it (or try the detect button).  And then you should be good to go.  Play around with it a little.  But it should work for you!

EDIT: I didn't realize that you were on Xubuntu, so the directions for HOW TO GET TO gtkam through the desktop will be slightly different.  I've never used Xubuntu, so I'm not sure of the exact path you would take.  But it'll be installed somewhere in your applications menu I'm sure.

I have installed the gtkam, I opened it selected my Canon psA630 and I still can't get the pictures from it. Whats going on here? When I retrieved the camera info I know that my computer was communicating with gtkam because the lights flashed on the cam like they did on xp when I WAS running that OS.

BTW, BandD the directions were exactlly the same in X as they are in UB2. Thanks.

One issue at a time here. I've almost got everything just the way I want it. I just need to get this camera working in Xubuntu. 

Neal

---

### Post by gn2 on 2008-02-09
> **Indy452 said:**
>  I just need to get this camera working in Xubuntu. 

digiKam..... digiKam...... digiKam........   :D

---

### Post by BandD on 2008-02-09
When gtkam is open, and you tell it to look for your camera, does the camera show up on the left-hand side?  If so, then have you tried clicking on the little arrow next to the name of the camera until you get to the folder inside your camera where the photos are actually stored?  I have to click through a few directories before I'm at the actual storage folder.  Once I'm there and I click on that folder, all my pictures show up on the right-hand side and I'm able to tranfer them over through File--> Save Photos.

If your camera (name) doesn't show up on the left side, does gtkam give you any errors?

You're also welcome to try digiKam as gn2 suggests (one of the most beautiful things about the Linux community...so many options!!!).  I haven't tried it, but I do hear good things about it.  But you've also made it this far with gtkam already...

Anyway, keep us posted on your progress.  We'll try to get you there!

EDIT:  Also, I noticed that within gtkam it notes that you camera will only work if PTP (Print Transfer Protocol) is enabled.  I did a quick google search, and most likely the way you accomplish this with this camera (though check your user's manual if you have it) is to press the button on the back with a little printer next to it, though I'm not certain.  You'll want to have the camera ready to go in this mode, and then tell gtkam to scan for your camera. Check this site for more info:

[http://www.usa.canon.com/consumer/controller?act=ModelInfoAct&fcategoryid=183&modelid=14108#SupportDetailAct]("http://www.usa.canon.com/consumer/controller?act=ModelInfoAct&fcategoryid=183&modelid=14108#SupportDetailAct")

And out check the "Drivers and Downloads" tab and the Camera User Guide Advanced guide for more info.

---

### Post by Indy452 on 2008-02-09
> **BandD said:**
> When gtkam is open, and you tell it to look for your camera, does the camera show up on the left-hand side?  If so, then have you tried clicking on the little arrow next to the name of the camera until you get to the folder inside your camera where the photos are actually stored?  I have to click through a few directories before I'm at the actual storage folder.  Once I'm there and I click on that folder, all my pictures show up on the right-hand side and I'm able to tranfer them over through File--> Save Photos.

If your camera (name) doesn't show up on the left side, does gtkam give you any errors?

You're also welcome to try digiKam as gn2 suggests (one of the most beautiful things about the Linux community...so many options!!!).  I haven't tried it, but I do hear good things about it.  But you've also made it this far with gtkam already...

Anyway, keep us posted on your progress.  We'll try to get you there!

EDIT:  Also, I noticed that within gtkam it notes that you camera will only work if PTP (Print Transfer Protocol) is enabled.  I did a quick google search, and most likely the way you accomplish this with this camera (though check your user's manual if you have it) is to press the button on the back with a little printer next to it, though I'm not certain.  You'll want to have the camera ready to go in this mode, and then tell gtkam to scan for your camera. Check this site for more info:

[http://www.usa.canon.com/consumer/controller?act=ModelInfoAct&fcategoryid=183&modelid=14108#SupportDetailAct]("http://www.usa.canon.com/consumer/controller?act=ModelInfoAct&fcategoryid=183&modelid=14108#SupportDetailAct")

And out check the "Drivers and Downloads" tab and the Camera User Guide Advanced guide for more info.



Hi BandD!  I got the gtkam to work (sort of) I'll explain the best I can here.

I hook up my camera to the usb port then I select Applications-graphics-gtcam.

In gtkam the lower panel of the box shows its loading camera/loading drivers then initializing camera. My camera screen goes blank after this happens (which I find unusual)

I have the camera listed on the left and I click the arrow you mentioned. It then says store 0010001 I then click the arrow next to store and it says DCIM and MISC below it. When I click the arrow next to DCIM 100 Canon appears. If I click on 100 Canon I am able to view the pics in my camera but when I select a picture and right click it and select View with-built in viewer I get a black empt screen where the picture should be. So basically I'm unable to view the enlarged picture. 

If all else fails I can try the Digikam program that gn2 suggests. I have no opinion of either now I just need something that works and is reliable if possible.

I sure do appreciate all the help I've been recieving here on the forum. I know for a fact that if it were not for this forum I would not have even considered Ubuntu.

Regards, Neal

---

### Post by BandD on 2008-02-09
Are you able to save the pictures to your computer?  Flie-->Save Photos (and then choose either all, or selected), and save them where you so desire.

I haven't actally tried to use the built-in viewer in gtkam.  I just get all the pictures off my camera and then delete the ones I don't want.  I'll try and look into it later today, though.

Dustin

---

