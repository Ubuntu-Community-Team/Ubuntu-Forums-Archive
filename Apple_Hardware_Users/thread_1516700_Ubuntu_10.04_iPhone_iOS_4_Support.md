---
title: "Ubuntu 10.04 iPhone iOS 4 Support?"
date: 2010-06-24
forum: Apple Hardware Users
---

### Post by randomsearch on 2010-06-24
Hi,

Does anyone know if Ubuntu 10.04 will work with the iPhone's iOS 4?  

Currently, I am able to transfer photos and music to my phone out-of-the-box with Ubuntu.  I need to upgrade my iPhone's OS but don't want to break compatibility with Ubuntu.

Thanks,

RS

---

### Post by eatmytag on 2010-06-24
I have never tried to connect my iPhone 3GS to my Lucid, but I just did and it worked - iPhone 3GS running iOS 4.0 GM.

---

### Post by randomsearch on 2010-06-24
Thanks!  

Please could you confirm exactly which features are ok, i.e. whether it works in Rhythmbox for transferring music and also browsing/transferring photos.

RS

---

### Post by BishopPell on 2010-06-24
> **eatmytag said:**
> I have never tried to connect my iPhone 3GS to my Lucid, but I just did and it worked - iPhone 3GS running iOS 4.0 GM.

I was using ipheth USB internet tethering on OS 3.1.3 on 10.04.  I was worried I would break iphone internet tethering but really wanted to upgrade to IOS 4.  Imagine my joy when I discovered iphone internet tethering DOES WORK perfectly in IOS 4.

I can access my photos too.

However when I tried to use Rhythmbox it does NOT work.  In Rhythmbox I could view the music on my iphone, but when I tried to transfer music over to the iphone I received a bus error.

Its possible the iphone library used to connect the iphone needs some updates to get music working again.

[http://www.libimobiledevice.org/](http://www.libimobiledevice.org/)

[http://blog.sukimashita.com/2010/06/23/ios-4-0-released-libimobiledevice-and-music-sync-with-linux/](http://blog.sukimashita.com/2010/06/23/ios-4-0-released-libimobiledevice-and-music-sync-with-linux/)

It says that music syncing is broken right now but will be fixed soon.

Not sure.

---

### Post by randomsearch on 2010-06-24
Thanks very much.

Those interested can read more at the Blog post:

[http://blog.sukimashita.com/2010/06/23/ios-4-0-released-libimobiledevice-and-music-sync-with-linux/](http://blog.sukimashita.com/2010/06/23/ios-4-0-released-libimobiledevice-and-music-sync-with-linux/)

If you want music sync. with iOS 4 then you're best to wait until a fix is released.

RS

---

### Post by LoutUK on 2010-06-25
I had the same bus error with iOS4 and needed to install GTKPOD and LIBGPOD4 from the package manager to get audio syncing to work with Rhythmbox again. It now works flawlessly for me at least.

---

### Post by tnt533 on 2010-06-25
try plugging in your iPhone, wait for it to fully mount and appear in Rhythmbox and then close and restart Rhythmbox. That worked for me. Make sure to completely close the application not just click close and have it minimize to your tray. Right click on the tray icon and select <Quit> and then reopen it from the gnome panel or how ever you like to start applications.

I have a 3G running iOS 4.0 and it is syncing "ok" with Rhythmbox. It will sync an album or two just fine but when I tried to sync a 9 gig play-list to it, not only did it take 5 hours to transfer but the iPhone also refused to see the music.

So I would say sync is working with 4.0 but there seems to be some issues. 


> **BishopPell said:**
> I was using ipheth USB internet tethering on OS 3.1.3 on 10.04.  I was worried I would break iphone internet tethering but really wanted to upgrade to IOS 4.  Imagine my joy when I discovered iphone internet tethering DOES WORK perfectly in IOS 4.

I can access my photos too.

However when I tried to use Rhythmbox it does NOT work.  In Rhythmbox I could view the music on my iphone, but when I tried to transfer music over to the iphone I received a bus error.

Its possible the iphone library used to connect the iphone needs some updates to get music working again.

[http://www.libimobiledevice.org/](http://www.libimobiledevice.org/)

[http://blog.sukimashita.com/2010/06/23/ios-4-0-released-libimobiledevice-and-music-sync-with-linux/](http://blog.sukimashita.com/2010/06/23/ios-4-0-released-libimobiledevice-and-music-sync-with-linux/)

It says that music syncing is broken right now but will be fixed soon.

Not sure.

---

### Post by VinoFuriaRoja on 2010-06-26
I bought an iPhone 3GS today with the iOS4 already installed.  I clicked on rhythmbox to start adding music, but it asks if I want to initialize my iPod?  I click on initialize after naming it, but nothing happens.  The drop down menu for me to click on the model is greyed out...help!

---

### Post by VinoFuriaRoja on 2010-06-27
any other help?

---

### Post by VinoFuriaRoja on 2010-06-29
I don't know if this will be help to anyone, but I went in to iTunes via Windows and did a back up of my phone, and then a full restore to original factory settings.  Then I upgraded to the iOS4 firmware and then re-installed the phone from the backup I made, all within iTunes.  Finally, I re-registered my phone, complete with name for the phone and everything.  

I then went in to Ubuntu and connected my iPhone with iOS4 and it recognized it immediately.  I went in to Rhythmbox and again, it recognized my phone immediately.  Now I have full access to my music on my phone and can happily transfer music in to and out of my iPhone!  It works like a dream now!  

So, hopefully this will help out those of you still having problems....

---

### Post by Der_Kommissar on 2010-06-29
I hope this is related enough so that I can lob it in this thread.  Plugged my new iPhone (4) in via USB to my work machine (iPhone is synch'd at home).  I can play music from the phone, but it keeps flashing the "Sync in progress" on the phone.  Any idea why it's doing this - haven't hit on the computer to ask it to sync.

---

### Post by VinoFuriaRoja on 2010-06-30
I believe that is just one of the quirks of Rhythmbox.  It sync's the phone automatically.  I notice that it does that whenever I play a song from my Iphone within Rhythmbox.  Obviously if you add any media to your phone from Rhythmbox, its going to sync it automatically.  Hope this helps.

---

### Post by Der_Kommissar on 2010-07-01
> **VinoFuriaRoja said:**
> I believe that is just one of the quirks of Rhythmbox.  It sync's the phone automatically.  I notice that it does that whenever I play a song from my Iphone within Rhythmbox.  Obviously if you add any media to your phone from Rhythmbox, its going to sync it automatically.  Hope this helps.

Thank you for the reply.  It's not a huge issue, just an annoyance.  I was happy that Ubuntu was able to recognize the music on my phone and play it. :)

---

### Post by natrixgli on 2010-07-03
In my experience with a 3GS and iPhone 4 both running iOS4, Rhythmbox puts the music on the device, but it must not be writing the iTunesDB correctly because none of it shows up in the iPod app on the phone.

Additionally, music added via iTunes does not show up in Rhythmbox.

-n8

---

### Post by blahbommer on 2010-07-03
i updated about a week ago.
back then ryhtmbox saw my ipod but didnt sync it.

but now it doesnt even see it. its jailbroken i dont know if that makes a difference.
Thanks

---

### Post by blahbommer on 2010-07-03
i got mine working now full support.
it turns out i just didnt have my rhytmbox plugins installed.
but it works great now

---

### Post by couzin2000 on 2010-07-04
I too am having difficulty with my iPhone 3G. I checked the version of the software, for now it seems I'm still setup with iOS 3.1.2. I had jailbroken this phone before, but I am in the process of restoring it to factory defaults, then upgrading the software to iOS4.0. 

My issue is with Rhythmbox... I can definitely see the icon popup on my desktop, which means Ubuntu can establish communication with the iPhone. But I think there are some info missing, and the lib cannot see the software proprely. Rhythmbox does see the phone, but not entirely... here's what I get when I run [FONT="Courier New"]Properties[/FONT] on the iPhone in Rhythmbox:
```
**Sébastien's iPhone Properties:**
**Advanced**
  **System**
    Mount point: /home/sebastien/.gvfs/Sébastien's iPhone
    Device node:
    Model: xA712
    Serial number:
    Firmware version:
    Database version: 46
    Audio formats: MP3 audio
                   AAC sound
```

So I think there's stuff it doesn't see because of the old age of the software in my phone. I'll update and see what it does. I'll post back as well.

---

### Post by tom|es on 2010-07-06
Yes it does :D

---

### Post by natrixgli on 2010-07-08
I filed [bug #623899]("https://bugzilla.gnome.org/show_bug.cgi?id=623899") on Gnome's bugzilla.

-n8

---

### Post by BishopPell on 2010-07-13
> **LoutUK said:**
> I had the same bus error with iOS4 and needed to install GTKPOD and LIBGPOD4 from the package manager to get audio syncing to work with Rhythmbox again. It now works flawlessly for me at least.

Tried - that, but still get the bus error.  When I upgraded to 10.04 I had to create a new user to get iphone syncing working, wondering if the same might work this time.  Will try and see.

---

### Post by BishopPell on 2010-07-13
> **BishopPell said:**
> Tried - that, but still get the bus error.  When I upgraded to 10.04 I had to create a new user to get iphone syncing working, wondering if the same might work this time.  Will try and see.

Ok - so creating a new user on my ubuntu 10.04 allows me to 'successfully' transfer an MP3 to the iPhone, but no matter what I do this song does not appear on the iphone ipod app.  My experience now seems to correspond to what some others are reporting which is that the itunesDb format has changed and rhythymbox is not writing the correct format to the iphone.

In the mean time it would be fantastic to know what I need to change about my user account to enable the iphone to actually work without a bus error.  As once music syncing is fixed in the libmobiledevice or libgpod libraries I am still stuck unless I create a new account.

---

### Post by esaloch on 2010-07-18
> **tnt533 said:**
> try plugging in your iPhone, wait for it to fully mount and appear in Rhythmbox and then close and restart Rhythmbox. That worked for me. Make sure to completely close the application not just click close and have it minimize to your tray. Right click on the tray icon and select <Quit> and then reopen it from the gnome panel or how ever you like to start applications.


Worked for me. Thanks.

---

### Post by esaloch on 2010-07-18
I noticed that after you transfer the files do not show up in the iPod app. However, if you delete something else from your iPhone through rhythmbox the phone will update its database and the new file will then show up. Annoying but works (until you're out of things you want to delete).

---

### Post by B0rat on 2010-08-08
I was googling for this problem.... couldn't get music to sync. Turns out that I was trying to move .ogg files to my iPhone on ios 4. Just a word of advice to anyone with this issue - make sure you're moving compatible files :oops:

---

### Post by PatrickVogeli on 2010-08-14
I've been trying, but it's not working... sad :(

According to the libimobile device, syncing is working with iOS 4.0.1 but NOT with iphone 4 or ipad. I guess we'll have to wait..

---

### Post by Joan A. on 2010-08-15
I think that the problem is related to the **libgpod4** and not to the **libimobiledevice**. I have readt in some blogs it is working perfectly. As *PatrickVogeli* said, we will have to wait for an update, even though I hope that its arrive before the Ubuntu 10.10 release.

---

### Post by jsampaio57 on 2010-09-01
> **esaloch said:**
> I noticed that after you transfer the files do not show up in the iPod app. However, if you delete something else from your iPhone through rhythmbox the phone will update its database and the new file will then show up. Annoying but works (until you're out of things you want to delete).

Can you be more specific? Delete what? If you say that it works, it is because you know what it is. Do you want to share of keep it secret?
Cheers...

---

### Post by gast0r on 2010-09-01
> **jsampaio57 said:**
> Can you be more specific? Delete what? If you say that it works, it is because you know what it is. Do you want to share of keep it secret?
Cheers...
He obviously means delete something like a song, or album. I too can confirm that this works. It would be nice though if this wasn't needed to be done though. It's just small problems like this that put off people from coming over to Linux.

---

### Post by girard on 2010-10-04
I have the same problem with one other post up in the thread. I followed the instructions to install the libimobiledevice1 through synaptic and include the debug thing, did the dist upgrade and installed upgrades. Prior to this, rhythmbox would not recognize the iphone.. it would launch (and the annoying fspot) but the phone icon would not be there... that works now after the installation of libimobiledevice1. i was able to transfer a file to the phone and it sync'd as i closed rhythmbox, but when i checked the ipod app on the phone to see if i could play, the song was not there...

i'm on 10.04 LTS with the actual iphone 4...

so to summarize, 10.04 will only work with the IOS 4.xx on the 3rd gen phone... not the new iphone 4 hardware?

EDIT:

hmmm... the deleting of songs didn't work for me... i transfered some files from rhythmbox to the iphone, then i deleted a song on the iphone via the controls on rhythmbox (remove - the move to trash was grayed out), but nothing showed up on the iphone after it sync'd and i disconnected it from the usb connection. i connected it to windows and checked itunes, and there weren't any files there as well...

---

### Post by Big_Dee on 2010-10-05
Same thing here ..."No content" in iTunes app on iPhone 4 after an apparent sync'

---

### Post by girard on 2010-10-09
i wonder if anyone knows of any development on this issue?

---

### Post by n3rxs on 2010-10-11
Do we have an update on the iPad? My iPhone4 and iPod work fine with Ubuntu 10.04 and 10.10 with iOS4.1 but for some reason the iPad is not recognized with any version of iOS.

---

### Post by girard on 2010-11-06
> **n3rxs said:**
> Do we have an update on the iPad? My iPhone4 and iPod work fine with Ubuntu 10.04 and 10.10 with iOS4.1 but for some reason the iPad is not recognized with any version of iOS.

your iphone 4 works fine with ubuntu 10.xx? would you mind sharing how you got this to work please...

---

### Post by gurt on 2010-11-10
Upgraded to libimobiledevice1 per [link]("http://www.ubuntugeek.com/how-to-get-ios-4-iphone-os-to-sync-with-rhythmbox-in-ubuntu-10-04-lucid.html"). 
Where on the iphone are you suppose to put your mp3 files? What directory? Do you just use the file browser or can you do it with rhythmbox? When I plug in my iphone4 (IOS4.1) I can see it under devices and a file browser opens.

TIA

---

### Post by SwingTime on 2010-11-16
Hi everyone. I have been trying to get my iphone 4 to mount in Lucid. 

When I first plugged it in it opened Fspot and I got a message from Rhythmbox asking me to initialize my iphone (when I followed those instructions nothing happened)

After I installed libimobiledevice1.0.3 my computer just doesn't see the iphone at all. I unistalled and reinstalled it a couple of times, and tried going back to libimobiledevice0, but nothing helped. 

Now, when I go to synaptic libimobiledevice1 doesn't even show up anymore.


Any suggestions? I am pretty lost as to how to even get the iphone4 to mount. Thanks!

---

### Post by thered on 2010-11-17
I've just got my iphone4. Not happy you can't transfer mobile to mobile, but that's another story!

I have loads of images and vids I want to transfer from 'puter to said iphone.  I tested with one image and it transferred it ok.  I casn see it in Nautilus, it is there, but it doesn't show when I click on the photo app.

I also transferred some music using rhythmbox and it showed the files transferring but they won't show in ipod app and I can't find them with nautilus either!. I haven't tried the above fix yet though.

---

### Post by DShad on 2011-01-05
Are there any development on iPhone 4 (iOs 4.2.1) or iPod Touch 4g (iOs 4.1)?

I have those 2 devices and they are recognized but after transferring some mp3, they don't show up after disconnecting...

Anything new about that?

Thanks

P.S. I'm on Ubuntu 10.10 and libimobiledevice 1.0.4-1 and usbmuxd 1.0.6-1 are installed.

---

### Post by kupo365 on 2011-02-05
I'm having the same problem as some of you.

I have the iPhone 4, and I got Rhythm Box to transfer the files to the phone (which took a long time, about an hour) and when I checked on the phone in the iPod app, there was 'No Content', but when I check the iPhone in Rhythm Box, I can see and play all of the music.

Is there no known solution for this issue yet?

---

### Post by typhoon_tip on 2011-03-24
**_Attention guys_**:

Just been trough a surgical downgrade of GVFS modules and all the things installed trough the suggested PPA to make the IOS 4 connect to Ubuntu 10.04, only to discover that it totally destroy Obex and Bluetooth with any other mobile phone that you have. I plan to submit a bug report asap.

Cheers,
S.

---

### Post by rich52x on 2011-03-26
iPod Touch 2nd Generation iOS4.0 works with my Ubuntu 10.04 and 10.10 installs, transfers music with Rhythmbox, but can't delete music that is on iPod from Rhythmbox, don't know if that's a widespread issue or just me though

---

### Post by lew_redd on 2011-08-12
Same here. Can't believe there's still no fix to this. iphone 4 appears to sync with Rhythm-box but can't find files on the handset

---

### Post by rosegqgraham on 2011-08-13
I want to get rid of my go phone but than I heard that you can put the  sim card into an unlocked iphone. I want to do this, but I don't know  what website I should order an unlocked iphone.

---

### Post by alexstrand7 on 2012-03-27
Hi!
Just update to 10.04.4 from the Ubuntu repositories
The upgrade contains the new iPod/iPod/iPad driver.
Now its working. :-)

---

