---
title: "Dell XPS M1530"
date: 2007-12-28
forum: Absolute Beginner Talk
---

### Post by mike_pasara on 2007-12-28
I just bought a dell XPS M1530, I'll receive it mid January so i'm quoted. Does anyone have any input on these and how well they run with ubuntu? I ran Ubuntu about 2 months ago hen gutsy was first released and i enjoyed it but switched back to windows for familiarality(sp?) reasons.



Specs:
2.2ghz Core 2 Duo
2GB of ram @ 667mhz
250GB hard drive 5400rpm
256mb Nvidia 8600
1440X900 Resolution screen
Blu Ray Disc drive(not sure if it's a rom or a burner)
9 Cell Li Ion battery
3 year Warranty


When I receive it first thing I am doing is splitting the hard drive in half... 125 gigs for windows XP(maybe vista) and 125 gigs for Ubuntu.


I'm into playing games and what not but I have my PS3 for that. But i wouldn't mind trying out Crysis like everyone is raving about or Gears of War... That will be for the windows but the the Ubuntu it's going to be mainly everything else... Can anyone confirm that all function keys work properly? Also I'll be askign question later on how to dual boot both OS.

---

### Post by Twizz on 2007-12-28
I just ordered the Same XPS 1530, with just little bit different setup, but mostly the same.  Since the M1330 is almost the same, you could probably search for that, since I could not really find anything on M1530.  There are  a few topics on these forums for M1330, also I'll give you a link I used before to dualboot my Desktop.  Hope it helps, also let me know how your new computer turns out.

[http://apcmag.com/5046/how_to_dual_boot_vista_with_linux_vista_installed_first](http://apcmag.com/5046/how_to_dual_boot_vista_with_linux_vista_installed_first)

---

### Post by svhoy on 2008-01-02
Hi,

I am considering to buy the M1530 as well.
Could you please post your installation experiences. This will help me in my buying decision.

Thanks!

BR,

Steve

---

### Post by bunnynuts on 2008-01-02
I have the xps 1710, no blu-ray and an older video card so my experience will probably be different than yours. I'm running Gutsy. However, I was pleasantly surprised at how little work I have had to do to get everything running. All the functions work fine,(changing the brightness of the screen, turning the wireless card on/off, hibernating etc...) and I did not have to do anything extra to get them to work. The media card reader works great, the touchpad works fine. The only problem I have is when I close the lid, it only comes out of stand-by or hibernate about 33% of the time. There is a bug report on launchpad about it, nothing has worked for me yet.  I disabled media direct so long ago that I forgot I had that button...not sure if it does anything...will find out shortly. I can not think of anything else that has given me problems as of yet. Dell has their own way of partitioning drives so when you get your machine look at the setup and you may want to consider doing a full reinstall of windows when you add Ubuntu. I have my windows partition, my linux partition, and a fat partition to share between the two. Ubuntu does well with NTFS, but windows doesn't play well with ext3.

---

### Post by todd_fx on 2008-01-04
I ordered an M1530 and it had a delivery date of 1/15/08.   Guess what?   It showed up today [1/4/08].

Core 2 2.4GHz, 3GB Mem, 250GB drive, 15.4 WSXGA+ TrueLife screen (1680x1050).

I've loaded Ubuntu 7.10 (i386 - I have commercial software that's not ready for 64bit).

So far everything works with minimal tweaking.   Once you enable the NVIDIA accelerated graphics driver you can enable compiz and get all the eye candy.    Wireless and bluetooth work fine.    The default for the synaptics touchpad didn't accelerate well so I had to tweak the xorg.conf file a bit. 

Once I get it home I'll see if the HDMI port works.  So far I'm pretty happy with it.

---

### Post by mattyp1 on 2008-01-05
todd_fx, thanks for the info. Please share your thoughts on the display. I was reluctant to go with 1680x1050 do to the size of the monitor. My order should ship any day now with 1440 res but I am contemplating upping it. Let us know what you think.

Peace

Matt

---

### Post by cyrustajik on 2008-01-05
hey 
Im thinking about buying XPS M1530 laptop. Im a proper heavy user and do lots of engineering and design stuff on ubuntu.
Its really important that I get the compiz running on this laptop. Ive heard that compiz doesnt work good on nVidia 8series. 
What do you think ?
Have you had any problems with it so far ?

anyways, hope you're enjoying your brand new laptop ;)

cheers
Cyrus

---

### Post by Twizz on 2008-01-06
I was able to install Ubuntu just fine.  I followed the Partition guide from the previews post I made.  I'm keeping Vista for some school stuff.  I find everything working ok, I have not been able to test everything but so far it runs better than my Desktop.  I am useing 1280x800.  My XPS has up to 1440X900, but I find that to small.  I have that Resolution mostly for when I hook up the laptop to an external monitor.  I also use 1280x800 on Vista partition.  I used Automatix to install, Fonts, Codecs, and Archiving tools.  I also used Envy to install the Nvidia video driver.  Everything else I installed by Sudo commands.  Everything is working great.  I'll post an update when I mess around with my XPS more.

---

### Post by cyrustajik on 2008-01-06
hey 
have u managed to run compiz or beryl on it ?
cheers

---

### Post by Twizz on 2008-01-06
> **cyrustajik said:**
> hey 
have u managed to run compiz or beryl on it ?
cheers
After I installed the video driver, I installed the Compizconfig setting manager.  I've messed around with it and had no problems with it.  I never really used it though, I had it turned off on my Desktop, but so far it works fine.

---

### Post by mike_pasara on 2008-01-09
> **svhoy said:**
> Hi,

I am considering to buy the M1530 as well.
Could you please post your installation experiences. This will help me in my buying decision.

Thanks!

BR,

Steve

Hey Steve, I haven't recieved my laptop yet, it's still in the building stage. Should come in sometime soon, Dell quoted me January 17 2008. Not too sure if I am going to get it a few days early or right on time.


I will let you know how everything went. I am a complete beginner at Ubuntu (well almost) but i can still let you know how everything goes as far as function keys and sleep mode wireless and so on.

---

### Post by vbabiy on 2008-01-09
Hey What wireless card do you have? And are they running fine?

---

### Post by mike_pasara on 2008-01-10
> **vbabiy said:**
> Hey What wireless card do you have? And are they running fine?

I picked the internal intel wireless A/G card... i haven't recieved the laptop yet like in my last post so when I do i'll keep you updated.

---

### Post by vbabiy on 2008-01-10
Here is my system just ordered last nigh. I am hoping to have it be the end of the month. Also I really hope that wifi card works.

-- XPS M1530 --
-- Intel® Core&#33922; 2 Duo Processor T7700 (2.4GHz/800Mhz FSB, 4MB Cache)
-----------------------
-- System Color --
-- Crimson Red
-----------------------
-- Memory --
-- 3GB Shared Dual Channel DDR2 SDRAM at 667MHz (2 Dimms)
-----------------------
-- LCD, Color and camera --
-- High Resolution glossy widescreen 15.4 inch LCD(1680x1050) &amp; 2MP Camera
-----------------------
-- Video Card --
-- 256MB NVIDIA® GeForce® 8600M GT
-----------------------
-- Hard Drives --
-- Speed: 160GB 7200rpm SATA Hard Drive Free Fall Sensor
-----------------------
-- Combo or DVD+RW Drive --
-- Slot Load DVD+/-RW (DVD/CD read/write)
-----------------------
-- Sound Card --
-- Integrated Sound Blaster Audigy HD Software Edition
-----------------------
-- Wireless Networking Cards --
-- Intel Next-Gen Wireless-N Mini-card
-----------------------
-- Primary Battery --
-- 56 WHr 6-cell Lithium Ion Primary Battery
-----------------------
-- Bluetooth Options --
-- Dell Wireless 355 Bluetooth Internal (2.0+Enhanced Data Rate)

---

### Post by mike_pasara on 2008-01-10
You had the choice of 1650X1050?? I was only allowed limited to 1440X900 then after i orderd it, i read on notebookreviews.com that Dell will be releazing LED backlit screens while the ones you order now will be CCFL. If youorder the CCFL you get a vga camera rather then the 2MP camera.


Update: status just changed from building to prepping for delivery... hoping that it comes in monday or tuesday rather then thursday.

---

### Post by vbabiy on 2008-01-10
Did you get the same wifi card as me?

---

### Post by mike_pasara on 2008-01-10
no i didn't i got the a/g not the N card. i don't have an N router yet. I shoudl have gotten the N card and bought an N router though.

seeing as everything I got on the laptop was new technology pretty much and wouldn't need to be upgraded for a while. But most of the time my laptop is ussualy plugged in because something in my house interfers with the wireless and it shuts it off. I have a feeling it's the cordless phone because i've noticed it happens more frequently when i recieve calls.

---

### Post by namatarr on 2008-01-10
I too have an M1530 running Ubuntu and its runs very well.   I am required to use the restricted drivers for Nvidia and the 1490 wireless card.  There are only two things that do not work out of box and they are the fingerprint reader and the dual mics. I haven't really spent any time trying to get them to work though.

---

### Post by mike_pasara on 2008-01-10
i jsut verified the shipping date arrival form dell and it comes in tomorrow... so excited. I am going to have my copy of Ubuntu ready for me to use tomorrow.


can someone explain to me how to enable restricted drivers for nvidia and the intel 1490 wireless card?

---

### Post by vbabiy on 2008-01-10
I am hoping my wireless card will work fine.

---

### Post by jerrylin on 2008-01-10
I just bought an XPS M1530 too, supposidly scheduled to be delivered Jan 15th. So excited!

While doing some research, I found the Intel 802.11 N card is supported in Ubuntu. If you search for Ubuntu compatibility with M1330 (alot of the same hardware) you will find alot of answers.

So far, the most major problems seem to be:
* Sleep state entrance and exit
* Fingerprint reader issues

Big plusses:
* WiFi seems to work on all models
* Function buttons work
* Webcam works

---

### Post by jerrylin on 2008-01-10
Sorry, I forgot to link where I got some of that information. Here is the wiki on ubuntu.com

[https://wiki.ubuntu.com/InstallingUbuntuOnADellXPSM1330](https://wiki.ubuntu.com/InstallingUbuntuOnADellXPSM1330)

---

### Post by mike_pasara on 2008-01-11
bummed out, it doesn't come in till tomorrow. :(

---

### Post by vbabiy on 2008-01-11
You  have Saturday delivery?

---

### Post by mike_pasara on 2008-01-11
yeah. heres the story.

at like 2pm i get a call from purolator saying it will arrive tomorrow on the 12th. then at 7pm i get a call saying it will arrive on the 14th. irritated by these date changes i call the number they gave me. I was told that my laptop is in canada in toronto. it has jsut left toronto and is on it's way north to me. so it should be here tonight, probobly sometime soon or in a few hours.

what i'll do is call the depot at lunch because it should be delivered by 9:30-10:30am. if it's not here i'll be pissed if they don't deliver on saturedays and only ship to their depots then i'll see if i can pick it up.

i am jsut wondering how the blu ray drive is going to function. ever review i hear doesn't have a blu ray drive. i don't even know yet if it's a read only or a write.

---

### Post by vbabiy on 2008-01-11
Make sure you get back here and let us know how it all worked out. I can't wait to get mine.

---

### Post by mike_pasara on 2008-01-11
ill keep you guys updated. crysis supposably runs 20fps on the same specs i have which isn't too bad considering it's a laptop.

i'll see what happens by lunch

---

### Post by vbabiy on 2008-01-11
Hey Mike how long was your laptop in production?

---

### Post by mike_pasara on 2008-01-12
I ordered my laptop on December 27. no status changes till in production which was January 4th. then on the 9th of January it was being shipped out. they originally quote me the 17th of January then the 11th then i was told by purolator it will arrive the 12th then now the 14th.


I called dell because i was mad and they told me it took a while because the xps systems ran out of chassis and dell had to order them. so on Monday i'll receive my computer. Not too impressed with the long wait because my friend ordered a mac on a Tuesday and got it Thursday

---

### Post by vbabiy on 2008-01-12
But you have to understand when its such a popular laptop it could take some time.

---

### Post by mike_pasara on 2008-01-12
if it's so popular then they should have all the parts ready. i'm not upset about that part actually because i do understand that sometimes they run short of parts and have to order. i'm upset with the fact they've given me 4 different dates the 11th, 12th, 14th, 17th

---

### Post by vbabiy on 2008-01-12
Yeah that would also drive me crazy. I hope I don't have to deal with that.

---

### Post by mike_pasara on 2008-01-12
do you know of a program that is like google maps but that can be used while not online... I'm looking for one that i can use when i go out driving long distances. Have the laptop hooked up to a power charger in the car then use it as my navigation.

---

### Post by vbabiy on 2008-01-13
No I don't but if you listen to the last 2 Linux Action Show podcast they answer that question. I can't remeber witch one

---

### Post by vbabiy on 2008-01-13
Here is one.
[http://gpsdrive.de/](http://gpsdrive.de/)

---

### Post by jerrylin on 2008-01-13
My laptop is taking a long time too =(. They claim it will be here on the 15th but I've been told randomly over the phone it'll get to me the 22nd or later... wtf mate.

Macbooks come mostly pre-configured anyway. Plus... they are way more expensive for less bang IMHO. Great computers if you don't mind that bit.

---

### Post by mike_pasara on 2008-01-13
Well jsut keep in mind the XPS chassis ran out so they had to order them. If your computer takes longer then 1 month i would cancel the order and find somewhere else to buy from. 

I find a lot of mac owners are smug about their macbooks. I just laugh now that i realize how much they are slowly becoming like microsoft (money hungry). I'm glad i went with dell, great warranty which is personalyl the most important factor of them all. You can have the nicest built machine and a year and a half later somethign will fail almost certainly.

---

### Post by vbabiy on 2008-01-13
So dell has changed my status to Shipped :) Can't wait

---

### Post by mike_pasara on 2008-01-13
> **vbabiy said:**
> So dell has changed my status to Shipped :) Can't wait


My status changed to shippe don the 9th of Jan and won't arrive till the 14th... so keep that in mind for shipping time. also they don't ship on sundays. so expect a 3-4 days shipping time.

---

### Post by jerrylin on 2008-01-13
Did they change your status today (Sunday)?

---

### Post by mike_pasara on 2008-01-13
no it was typically on mondays that they did

---

### Post by mattyp1 on 2008-01-13
I received my M1530 Tuesday and haven't gotten much sleep, partitioning, installing distros (mint, ubuntu, OSX, etc...). Finally, I think I have settled on a config. 

Dell M1530
1440x900 display w/2MP webcam
2.6 Core 2 Duo
3 GB Ram
200 GB 7200 RPM HD
Audigy
Intel Internal Wireless N
Spare battery, travel power supply (very cool!), spare AC adapter.

I kept Vista on a 60 GB partition for work (my company uses Win only VPN software :( ) and gaming. I left the quick boot stuff as first on primary and first on logical drive. I installed Ubuntu 64 Bit on 15 GB ext3 partition leaving over 100GB for home directory.

Pros:
1) Speed, man it is snappy!
2) Display is beautiful (NOTE!! Do not install nvidia driver from nvidia's site!! As of yesterday it messes up ubuntu big time, you can still boot but it is ugly and nearly impossible to get back to restricted drivers - anyway - USE RESTRICTED drivers! Looks great).
3) Wine runs well
4) Compiz is beautiful
5) Running awn, screenlets, etc... very well

Cons:
1)Changing mouse settings does not impact touchpad. I REALLY want to tweak the acceleration but I've had no luck. If anyone knows how to fix this please let me know. I haven't had time to google it too much yet.
2) Installing graphics drivers from nvidia's site doesn't work 32 or 64 bit (note, if you are brave enough to try make sure kernel source is installed for 64 bit compile).
3) My buddy called me on Skype, I could hear him but he couldn't hear me, still troubleshooting.
4) Webcam doesn't seem to work (note, I haven't spent much time trying to get it to work.

Anyway, I really wanted a MacBook Pro but the Dell was a MUCH better deal. Faster, cheaper, MUCH better warranty. Plus, I may love OSX too much ;) Hopefully it wasn't a mistake.

I'll check back in as I make more progress.

Peace

Matt

---

### Post by jerrylin on 2008-01-13
* Did you have any problems with sleep/hibernate?
* Is your CPU fan or harddrive really loud? (constantly busy?)

BTW I completely agree with you about the MacBook vs M1530. The M1530 is so much more bang for the buck I couldn't resist.

---

### Post by vbabiy on 2008-01-13
Jerrylin Yeah,
Also I have overnight shipping, so I should have it the 15th

---

### Post by invictus on 2008-01-14
If I install ubuntu on my m1530, will the media thingy stop working? It kind of sucks if I am stuck with this button which do nothing at all. Or can it be programmed in ubuntu to start a media player perhaps?

And one more thing: if I decide to go back to windows again, is it possible to restore this media thingy or is it gone forever?

---

### Post by mike_pasara on 2008-01-14
> **invictus said:**
> If I install ubuntu on my m1530, will the media thingy stop working? It kind of sucks if I am stuck with this button which do nothing at all. Or can it be programmed in ubuntu to start a media player perhaps?

And one more thing: if I decide to go back to windows again, is it possible to restore this media thingy or is it gone forever?


media thing? you mean the media keys? in other reviews i've seen them work jsut fine. or do you mean the dell media thing were you can play music without booting into windows/ubuntu? that shoudl work no matter what unless the secret partition is removed.


as far as hibernate on my desktop i haven't tried that. I am at work righ tnow so I will try that as soon as i get my laptop up an runnin . It should be in this morning so hopefully no one leaves the house untill my laptop arrives. So i'll test both out tonight. 


I got gears of war ready to install on my laptop so i'm goign to see how well it will perform and i'll review that aswell



Edit: 

TRACKING DETAILS
 
Status  On vehicle for delivery 
Date/Time  JANUARY 14, 2008 AT 06:55  
 
^^so happy. if there is soemthign wrong with it, i am going to snap

---

### Post by mike_pasara on 2008-01-14
> **jerrylin said:**
> * [B]Did you have any problems with sleep/hibernate?
* Is your CPU fan or harddrive really loud? (constantly busy?)[/B]

BTW I completely agree with you about the MacBook vs M1530. The M1530 is so much more bang for the buck I couldn't resist.



from my understandings the hard drive being constantly busy was an old issue in ubuntu for only certain hard drives. back in the 6.X days a friend of mine told me 7.10 should have the problem resolved.


A question for whoever is watchign out there. Should i install 64bit or 32bit... i can't find anoything about my cpu other then it being EMT64 capable. Switchign from amd to intel... i don't even know what emt64 is other then possibly being a 64 bit chip? I have both copies of 7.10 in 32 and 64 bit ready for installation.

---

### Post by invictus on 2008-01-14
> **mike_pasara said:**
> media thing? you mean the media keys? in other reviews i've seen them work jsut fine. or do you mean the dell media thing were you can play music without booting into windows/ubuntu? that shoudl work no matter what unless the secret partition is removed.

I was thinking of the dell media thing were you can play music without booting into windows/ubuntu. Wont grub overwrite the MBR and as a result the method for booting this partition?

Another thing: what does this button do when the OS is running (windows or linux. doesnt matter) ? Would be cool if this button could be configured to launch rythmbox or something. Or what would be even more awsome would be if you could boot ubuntu with this button while the regular power button booted windows :p

---

### Post by mike_pasara on 2008-01-14
hm, i'll look into it when I get my laptop. I'll let you know. 


I just ordered a Nokia N73... i have so many new toys, just last month I bought a PS3... Next month will be a 40 inch LCD tv... so pumped.

---

### Post by jerrylin on 2008-01-14
> **mike_pasara said:**
> A question for whoever is watchign out there. Should i install 64bit or 32bit... i can't find anoything about my cpu other then it being EMT64 capable. Switchign from amd to intel... i don't even know what emt64 is other then possibly being a 64 bit chip? I have both copies of 7.10 in 32 and 64 bit ready for installation.

The chip is 64-bit and will support Ubuntu x64. Personally I am an adopter of the whole 64-bit thing... it is the future with slight performance gains (for now). Problem is you might run into some issues - such as having to manually compile Wine in 64-bit. If you want 4gb of RAM, you MUST use 64-bit.

> **invictus said:**
> I was thinking of the dell media thing were you can play music without booting into windows/ubuntu. Wont grub overwrite the MBR and as a result the method for booting this partition?

Another thing: what does this button do when the OS is running (windows or linux. doesnt matter) ? Would be cool if this button could be configured to launch rythmbox or something. Or what would be even more awsome would be if you could boot ubuntu with this button while the regular power button booted windows 

From what I understand, once GRUB takes over this button does not work. I have seen ALOT of discussion regarding this since pressing this button actually kills the partition table for some people (reversable). I think you might be able to program the buttons, but I would suspect it required you unlock the BIOS and hack around with it, however I havn't looked into that.

---

### Post by invictus on 2008-01-14
> **jerrylin said:**
> 

From what I understand, once GRUB takes over this button does not work. I have seen ALOT of discussion regarding this since pressing this button actually kills the partition table for some people (reversable). I think you might be able to program the buttons, but I would suspect it required you unlock the BIOS and hack around with it, however I havn't looked into that.

Wow...that is kind of serious. perhaps I should get another laptop instead then if I want to use ubuntu.

---

### Post by jerrylin on 2008-01-14
From what I understand there are alot of work-arounds. You should read into it more, there are alot of threads regarding this.

Also for those looking to buy a M1530 soon: My order has been delayed a week (yes a whole f#&$ing week) because they ran out of Intel Wireless N cards. They don't expect to get a shipment until end of the week.

---

### Post by mike_pasara on 2008-01-14
> **jerrylin said:**
> 
Also for those looking to buy a M1530 soon: My order has been delayed a week (yes a whole f#&$ing week) because they ran out of Intel Wireless N cards. They don't expect to get a shipment until end of the week.

That's a huge bummer, they ran out of the chassis and now the N cards... you would think with a popular laptop liek this they would atleast have a bunch of everything because most of the stuff like wireless cards can be used in multiple systems.

---

### Post by mattyp1 on 2008-01-14
> **jerrylin said:**
> * Did you have any problems with sleep/hibernate?
* Is your CPU fan or harddrive really loud? (constantly busy?)

BTW I completely agree with you about the MacBook vs M1530. The M1530 is so much more bang for the buck I couldn't resist.

I haven't had problems with hibernate/sleep yet but I've only tried it once. I'll try a few more times.
I use a cooling pad which is rather loud but my HD/fan is not loud a all. Note: there are bios setting for the hard drive noise...

Peace

Matt

---

### Post by mike_pasara on 2008-01-14
[http://ubuntuforums.org/showthread.php?t=628229&highlight=dell+media+button+ubuntu](http://ubuntuforums.org/showthread.php?t=628229&highlight=dell+media+button+ubuntu)
> **nealron said:**
> **[SIZE="3"]I found a fix for the Dell Self-destruct-direct (MediaDirect) button problem.[/SIZE]** 

A little background info might be in order though. What the Dell MediaDirect button (next to the power button and has a house icon on it similar to an internet browsers "Home" button) does when the hard drive is partitioned in a way that it does not expect (aka, linux installed) it rewrites the partition table that it thinks it should have. Your partition table is essentially like the table of contents pages in a book with 100 billion pages, without it your screwed. 

What we're going to do here is offer a way to disable the button if you don't care about the data on the drive (like right after a fresh install) OR a way to recover your partition table with a nifty program called [testdisk]("http://www.cgsecurity.org/wiki/TestDisk").

**[SIZE="3"]Plan A - Disable Destruct Button[/SIZE]**
You can low-level format your hard drive to permanently remove the danger the button poses to your future data, because you _will_ loose ALL data currently on your drive. Issue the following command from a live CD/DVD booted system.

[B][SIZE="2"]****WARNING USE ONLY FROM LIVE CD/DVD******
****WARNING WILL DESTORY ALL DATA ON DISK*******[/SIZE][/B]
```
sudo dd if=/dev/zero of=/dev/sda
```

The above command writes zeros in every sector of your hard drive, aka "Zeroing the drive". Zeroing the drive has been known to overwrite the HPA (Host Protected Area) of the hard drive where the MediaDirect partition is hidden on the drive. Afterwards, pressing the self-destruct button will harmlessly show the MediaDirect splash screen and then boot GRUB.

[_The above came from Skuzniak here_]("http://ubuntuforums.org/showpost.php?p=3870754&postcount=2")

**[SIZE="3"]Plan B - RECOVER YOUR DATA[/SIZE]**.
If you have pressed the dreaded MediaDirect button and now have a very expensive paper weight for a laptop, FEAR NOT! testdisk to the rescue!

1) Boot up your live CD/DVD (like the one you used to install from).

2) Copy the additional repositories to your /etc/apt/sources.list file on your live CD/DVD session. The live CD isn't mean to install packages/programs to since it is erased when your reboot, however, if needed you can install a small amount of extra data. Like repair utilities. You can find instructions on how to do this [HERE]("http://kubuntuguide.org/Gutsy#Add_Extra_Kubuntu_Repositories").

3) Issue the following command to update your repository list after you changed your sources.list file and also install the precious data recovery utility "testdisk", as well as run testdisk after it's installed creating a testdisk.log file of all it's actions in the directory you issue the following command from.
```
sudo apt-get update && sudo apt-get install testdisk && sudo testdisk /log
```

4) Use the arrow keys to select your laptop hard drive. If you are using the live CD/DVD you should see two hard drives. 

**/dev/hda** (the live CD virtual drive) and **/dev/sda** (your laptop hard drive)

To "Proceed", tap the "Enter/Return" key when you've selected the appropriate hard drive.

5) Tap the "Enter/Return" key again on the next screen to select "Intel/PC" partition type.

6) Tap the "Enter/Return" key again on the next screen to "Analyse" (spelled the way it is in the program) your hard disk and search for your lost partitions.

7) This screen shows the screwed up partition table.. just tap the "Enter/Return" key again to "Proceed"

8) If you're lucky you'll see two or three partitions (If you let Ubuntu install configure your disk for you). Something like what you see below:
```
* Linux 0 1 1 18752 254 63 301266882
L Linux Swap 18753 0 1 19456 254 63 11309760
```
Tap the "Enter/Return" key again to "Proceed"

9) Now tap the right arrow key twice and tap the "Enter/Return" key to write the recovered partition table. Confirm it by taping the "Y" key and then the "Enter/Return" key.

10) Reboot your computer and take the live CD/DVD out. :)

NOTE: I had to do this twice for it to work for some reason, but after that, my precious Kubuntu booted up normal just like it used to without one file missing!

THANK YOU [_NICOLAE_]("http://ubuntuforums.org/showpost.php?p=3878125&postcount=7") and [_PSEUDOMANCER_]("http://ubuntuforums.org/showpost.php?p=3885747&postcount=8")!

---

### Post by mattyp1 on 2008-01-14
> **invictus said:**
> Wow...that is kind of serious. perhaps I should get another laptop instead then if I want to use ubuntu.

I've tested this and while it doesn't mess up my partitions it does fail. To be honest, the software is crap, it is windows based. On my old HP dv1000 (Quickplay) it was linux based and much faster. This worked fine. I haven't played too much with it on my Dell...

Peace,

Matt

---

### Post by mattyp1 on 2008-01-14
> **invictus said:**
> If I install ubuntu on my m1530, will the media thingy stop working? It kind of sucks if I am stuck with this button which do nothing at all. Or can it be programmed in ubuntu to start a media player perhaps?

And one more thing: if I decide to go back to windows again, is it possible to restore this media thingy or is it gone forever?

FYI, by default it launches Rythmbox in Ubuntu. You can change the key to do anything using the keyboard shortcut utility which is either in the System Admin or preferences menu. Mine launches the amarok.

Peace,

Matt

---

### Post by invictus on 2008-01-14
> **mike_pasara said:**
> [http://ubuntuforums.org/showthread.php?t=628229&highlight=dell+media+button+ubuntu](http://ubuntuforums.org/showthread.php?t=628229&highlight=dell+media+button+ubuntu)

Great stuff. But let me ask you this: If I follow that guide and zero the disk, will the button still work when running windows or ubuntu? Not for booting into mediadirect, but as a shortcut for some desktop environment feature?

---

### Post by mike_pasara on 2008-01-14
if you zero your disk... you will have absolutely nothing... no partitions of anyt kind. that means dells partition they use for your recovery will be lost. so if you dual boot vista with ubuntu then when you use the media keys with vista ... theoretically they shouldn't work because there is nothing installed unless you install medi direct.

but since your asking can you use that button for other programs yes you could most likely. I have a acer laptop and i can configure my email and internet and e management keys to do whatever i want. So it is possibly you can program it to open up say... gears of war for vista or the terminal for ubuntu as an example.

---

### Post by Omnios on 2008-01-14
Hi I got my XPS 1530 on Jan 10th and am pretty impressed so far thought I have not installed K/Ubuntu on it yet. 

 I kind of did some value shopping so I kind of based my purchase on best bang for the buck. My specs are as follows. 

 PROCESSOR Intel® Core™ 2 Duo Processor T7500 (2.2GHz/800Mhz FSB, 4MB Cache)

MEMORY 2GB Shared Dual Channel DDR2 SDRAM at 667MHz (2 Dimms)


SYSTEM COLOURCrimson Red
(very impressed with the look wanted it to be different)

LCD AND CAMERAGlossy, widescreen 15.4 inch LCD &  2.0 MP Camera (1280x800)
(res is very good with vista, have to test with Ubuntu and Kubuntu to see how it works)

HARD DRIVE160GB 5400RPM SATA Hard Drive
(think this is the weekest part of my buy but can always upgrade when the 7200's get cheaper)

GRAPHICS CARD256MB NVIDIA® GeForce™ 8600M GT
(got the GT after reading this [geforce_8600Ml]("http://www.nvidia.com/object/geforce_8600M.html") )

OPTICAL DRIVE8X CD/DVD burner (DVD+/-RW) with double-layer DVD+R write capability
(If I dish out money for a blue ray it will be for an external also standards not set you might end up with a bata/vhs like lemon product)

WIRELESS CARDIntel® 3945 802.11a/g Mini-card
(hooked up to a old SMC 102.1x network and getting really good speeds)

BLUETOOTHDell Wireless 355 Bluetooth Internal (2.0+Enhanced Data Rate), for XPSM1530
(havent tryed it yet)

HARDWARE SERVICES3 Year Return to Depot Service and Technical Support
(Did a lot of local shopping and every shop owner stated get the extended support, Sort of lemon and die after one year protection)

BATTERY OPTIONS85 WHr 9-cell Lithium Ion Primary Battery
(k the nine cell sticks out a bit but gives the lappy a nice angle avd longer running times)

SOUND OPTIONSIntegrated Sound Blaster Audigy HD Software Edition
(The ear phones that come with this probably cost a hell of a lot more than adding this option)

K I did a lot of value shopping here and only added upgrades that where under $100 except for the Vid card.

 I am still not certain about the LCD display yet but from what I have seen so far the 1400 res in vista would be uncomfortable to read. Also you can always play with icon and font settings to get what you want but would like other users input on this.

 Also I was thinking of upgrading this laptop in the future when the [FONT=arial] Intel® Core™ 2 Duo Processor T7800 (2.6GHz/800Mhz FSB, 4MB drops in price as it is a $550 upgrade right now.

 As for the 2Gigs of ram I have not used 100% or it yet.

The built in camera seems pretty good thought the build in speakers seem weak for media. Though the the CREATIVE EP-650 noise-Isolating Earphones are totally amazing and are worth a lot more than the sound upgrade costs.
Amazing sound quality from them.

The [/FONT]5400RPM SATA Hard Drive seems a bit week but was going over my budget already though probably should have looked at the 7200RPM.

 I never liked slid in cd/dvd set ups because of fears of the cd jamming but kind of getting used to it. 

 I am finding that the build in wireless card more than meets my needs so far. 

 I did not buy a laptop bag or pack pack from dell as I know someone who bought one and said I can get better locally for the same amount of money.

Impressions so far.

 The laptop handles heat well even under load and so far has only got warm to the touch. The T7500 does an amazing job of manging the heat. The cooling system and fan in the system is incredibly quite with just a whisper when running. 

 The keyboard keys are huge and its going to take a while to get used to them compared to my old Logitech keyboard on my PC but I find using but using the lappy is a lot more comfortable witch I noticed after using it for a few days.

 The finger print reader takes a while to get used to but really like it so far.

 I have not timed the battery life as of yet but found charge times to be incredibly quick.

 Other than the three year service I kind of value shopped with the intention of upgrading my system over a period of time and intend on upgrading the cpu, ram and hard drive. 

 Also my XPS 1530 was bough as a replacement PC as My old tower is over  six years old though I do not buy top of the line systems and tend to get stuff that is about a year old already. 

 I will install K/Ubuntu on it as soon as I finish researching the install and what I need. Main point is how to make the partitions for K/Ubuntu, Vista, a  documents partition, and also a swap partition on it. Currently my PC has way to much XP space lol.

 


---

### Post by mike_pasara on 2008-01-14
Omnios, You shoudl have gotten the blu ray if you really wanted it. I am almost certain blu ray is here to stay. Disney and a few other movie makers are going with blu ray only. Not to mention blockbuster is supporting blu ray by only offering blu ray movies to customers. It's not a forsure thign yet but i am almost cetain blu ray will win versus hd-dvd.

if anyone is interested in upgrading their ram you can get 2gb sticks for 51.50 canadian and 50$ even for american currency.

[http://www.memorydepot.com/details.asp?id=KVR667D2S5%2F2G](http://www.memorydepot.com/details.asp?id=KVR667D2S5%2F2G)

it's kingston ram. so if your looking to upgrade your ram i would say this is the way to go. 4gigs of ram for 100$+ shipping... who would pass on that?

---

### Post by vbabiy on 2008-01-14
Wow thats a nice deal.

---

### Post by invictus on 2008-01-14
> **Omnios said:**
> 

 I am still not certain about the LCD display yet but from what I have seen so far the 1400 res in vista would be uncomfortable to read. Also you can always play with icon and font settings to get what you want but would like other users input on this.


What do you mean that the 1400 res is uncomfortable to read? is that a problem with vista, the display, or just that it gets so small that its uncomfortable with such a high resolution on such a small display?

---

### Post by Omnios on 2008-01-14
> **invictus said:**
> What do you mean that the 1400 res is uncomfortable to read? is that a problem with vista, the display, or just that it gets so small that its uncomfortable with such a high resolution on such a small display?

 I find the 1280x800 just right for vista. Not sure how it will be with Ubuntu. As for the 1400 res I really cant say as I do not have the 1400 display just wondering if the stuff is to small on the screen. 

 Anyone have any input on this?

---

### Post by jerrylin on 2008-01-14
> **Omnios said:**
> I find the 1280x800 just right for vista. Not sure how it will be with Ubuntu. As for the 1400 res I really cant say as I do not have the 1400 display just wondering if the stuff is to small on the screen. 

 Anyone have any input on this?

My girlfriend has a 15.4" screen with the 1680x1050 resolution and it looks fine for her. Fonts are indeed sometimes too small to read, so she uses the cleartype and large font option. Overall this is just personal preference. 

The seeming advantage of the higher resolution is bigger workspace for photo editing and the like.

---

### Post by lewindha on 2008-01-15
Hello all,

I got my m1530 last week.  Sat down tonight to install linux.  No dice.  I tried Ubuntu 7.10, Mint 4.0, and Mint 3.1.  Insert CD, press F12 and select boot from CD, get install screen, press install.  It does nothing.  Then I select install in graphics safe mode, same thing.  It does nothing.

Anybody having this problem?  Fixes?

---

### Post by mike_pasara on 2008-01-15
I got my XPS yesterday and my god it's nice... everythign is so new it's "sticky" i'm so used to worn out it feels nice to have a new laptop.

I got a few extras like headphones which are amazing (Creative Labs EP-630). A case even though i didn't ask for one. A dustfree cloth to wash the the screen with.

The charger pack thing is ridiculously dumb design, I guess I am just used to my old one.

The 9cell battery gives a great angle for typing on the lap and on the desk. Also i can see this helping cool down the laptop much better.

Biometrics works good, gets some used to, you have to start where your finger bends then roll it acros makign sure the tip of your finger is on the scanner then go down... it's weird.. akward with the thumb and pinky fingers.


The optical drive is not as loud as i thought it would be and neither is the fan and hard drive. It's not silent but it's not loud.

1440X900 resolution is just perfect for the 15.4inch screen.

Permission to... is so annoying i had to press yes 3 times at a few points before i can install a program. Still need to work that out.


VLC, winamp, firefox are all easy to install with no issues... I installed gears of war and so far no lag in the menu but once i start playing the game it shuts down on me


Volume buttons aren't sensitive enough... maybe i'm used to my ps3 but i wish they were more sensitive.  the blue glow and fade is a really nice touch that dell put on the system.


keyboard is great, i make less spelling mistakes on it then any other keyboard, i am most comfortable with it, as for the touchpad the scroll down and up isn't the greatest but i'll find a way to change that setting. the left click and right click are too deep to click in i would preferably want something with a less depth in click... sounds weird but ohwell.


Video drivers... when i go to install gear of war and play it i get a message saying i need 163.XX drivers so i update to 169.9(the latest from nvidia) and says my hardware is not compatible so i went to 3dguru.com installed drivers from there and still get the message, i then later realized it's only telling you it needs the 163 drivers even if you have higher drivers... kind pointless to put a message you need a certain thing when you have better.


Speakers are too high of a sound, not good for music at all unless your a drummer and need to listen to which cymbals are being hit. good for tv shows though voice is really heard well.


i'll think of some other things. I am not done installing everything yet once i do then i'll work with ubuntu

---

### Post by lonelocust on 2008-01-15
I got my M1530 about a week and a half ago.  So for things are going pretty well.  I left vista about 30 gigs (keeping it because there is no really good mp3 DJ software for linux yet), gave ubuntu (Gutsy) 30 gigs and made the rest FAT32 to share files (almost entirely music).
  The only real problemm I have had with ubuntu on this laptop so far is that if I close the lid and then open it again the touchpad freaks out.  The cursor jumps all over the screen when I try to move it.  A USB mouse works fine.  I'm working on fixing this right now (although any suggestions would be welcome).  I mapped the media direct key so that when ubuntu is running it opens Amarok.   I haven't tried bluetooth or the webcam yet.
  On the subject of the media direct key, I have read the thread linked to earlier in here and it seems to me that some of it might not apply to this laptop.  The discussion about zeroing the drive assumes that media direct is in a partition that is completely hidden from the operating system.  Dell recently switched to putting media direct on a logical partition which it is possible to see.  Under places>computer there is an entry MEDIADIRECT.  It seems to me that it should be possible to erase this partition to disable the self-destructing key.  Or am I missing something here?  I should probably post this thought over in that thread as well.  Of course somewhere in there is a discussion of redicting the keys so that the power button boots vista and the media direct boot ubuntu.  That would be quite useful.

---

### Post by vbabiy on 2008-01-15
Well I got my m1530 and i must also say its a beatiful machine. The only prolbem that i seem to have is the IR Remote is not working and I can't seem to get the webcam to work either. If any one has had better luck let me know please. I also had to hack the xorg.conf to get the mouse to be more senstive because i could not work with it being so slow. Here is the link [http://ubuntuforums.org/showpost.php?p=673394&postcount=2]("http://ubuntuforums.org/showpost.php?p=673394&postcount=2")

---

### Post by lonelocust on 2008-01-15
I think I got the touchpad working.  I was having trouble, including not being able to disable tapping, until I tried:

```
cat /proc/bus/input/devices
```

and got:

```
I: Bus=0011 Vendor=0002 Product=0008 Version=7321
N: Name="AlpsPS/2 ALPS GlidePoint"
P: Phys=isa0060/serio2/input0
S: Sysfs=/class/input/input7
U: Uniq=
H: Handlers=mouse4 event7 
B: EV=f
B: KEY=420 0 70000 0 0 0 0 0 0 0 0
B: REL=3
B: ABS=1000003
```

as one of the entries.  So it's at Alps touchpad, not synaptics.  So now my xorg.conf has the following entries (sorry it's kind of messy at the moment):

```
Section "InputDevice"
Identifier "ALPS"
Driver "synaptics"
Option "AlwaysCore"
Option "Device" "/dev/input/event7"
Option "Protocol" "event"
Option "MaxTapTime" "0"
Option "SHMConfig" "on"
    Option "VertScrollDelta" "20"
    Option "HorizScrollDelta" "20"
    Option "MinSpeed" "0.60"
    Option "MaxSpeed" "1.10"
    Option "AccelFactor" "0.030"
    Option "EdgeMotionMinSpeed" "200"
    Option "EdgeMotionMaxSpeed" "200"
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
        screen "Default Screen"
	Inputdevice	"Generic Keyboard"
	Inputdevice	"Configured Mouse"
	InputDevice     "ALPS"
	# Uncomment if you have a wacom tablet
	#	InputDevice     "stylus"	"SendCoreEvents"
	#	InputDevice     "cursor"	"SendCoreEvents"
	#	InputDevice     "eraser"	"SendCoreEvents"
EndSection
```

---

### Post by lonelocust on 2008-01-15
After using the computer for a while longer it appears that my touchpad problem is not fixed.  Is anyone else having problems after closing the lid?
  Also, vbabiy mentioned that the webcam didn't seem to work.  It works with kdetv for me, but not with anything else.

---

### Post by mike_pasara on 2008-01-16
i think the touch pad is a big issue with the m1530's i haven't tried ubuntu on it yet because i've been playing gears of war :p but tonight i will try it out.

i've noticed on vista that the touch pad becomes all squirrely after the screen saver comes on. it jsut won't move like it should, i click the left mouse two - three times and finally it comes back to normal... kinda weird.

---

### Post by lewindha on 2008-01-16
> **lewindha said:**
> Hello all,

I got my m1530 last week.  Sat down tonight to install linux.  No dice.  I tried Ubuntu 7.10, Mint 4.0, and Mint 3.1.  Insert CD, press F12 and select boot from CD, get install screen, press install.  It does nothing.  Then I select install in graphics safe mode, same thing.  It does nothing.

Anybody having this problem?  Fixes?

OK, I still don't know what the problem is. 

For more info,  I've got the GeForce 8600 GT, 3gigs of Ram, and the 1650x1020 screen.  I used disc management tool to shrink the vista partition, downloaded and burned Gutsy to disc and rebooted.  Once I get the opening screen from the disc I select install, press enter.  Nothing happens.  

Any ideas?

---

### Post by vbabiy on 2008-01-16
lewindha I have Ubuntu running fine on mine. But the only difference that i can see is that i wipe off all the partition on the drive. And install only installed Ubuntu.

On an other note, has any one had any luck fixing the Mouse issues?

---

### Post by mattyp1 on 2008-01-16
> **lewindha said:**
> OK, I still don't know what the problem is. 

For more info,  I've got the GeForce 8600 GT, 3gigs of Ram, and the 1650x1020 screen.  I used disc management tool to shrink the vista partition, downloaded and burned Gutsy to disc and rebooted.  Once I get the opening screen from the disc I select install, press enter.  Nothing happens.  

Any ideas?

lewina,

Have you tried installing the 64 bit version using graphics safe mode option? This should work. Our configs are similar except I have 1440 res. If this doesn't work you can try alternative install...

---

### Post by mattyp1 on 2008-01-16
> **mattyp1 said:**
> lewina,

Have you tried installing the 64 bit version using graphics safe mode option? This should work. Our configs are similar except I have 1440 res. If this doesn't work you can try alternative install...

sorry, I wasn't clear, try using the alternative install cd if the 64 bit graphics install doesn't work.

---

### Post by lonelocust on 2008-01-16
Lewindha, I have no idea if this will help at all, but I had a slightly strange experience trying to install.  After burning the live CD I could not get it to boot.  I tried several times.  But then in Vista I noticed that on the CD there was an installer that runs from windows.  It worked just fine for me.  I know this is different from the problem you're having, but if you still have vista installed it probably won't hurt to give it a try.

---

### Post by jerrylin on 2008-01-17
Anyone know if the remote control works? Can we use it for Open Office presentations?

---

### Post by vbabiy on 2008-01-18
Hey Jerrylin I have tried the remote and I can't get it to work. I would also like to know if some one has had better luck.

---

### Post by Omnios on 2008-01-18
As for the remote I think you have to config lirc.

```

From synaptic package manager

Linux Infra-red Remote Control support
This package provides the daemons and some utilities to support infra-red
remote controls under Linux.

```

 Also searching lirc in synaptic will show other stuff for lirc like a XMMS demon to control the program.

 Also you might want to Google "lirc + "dell remote"

---

### Post by vbabiy on 2008-01-19
So I got the remote working by fixing the position of the battery. And it worked fine.
I didn't need any software, it just worked out of the box.

I still am hacking the xorg to get the mouse to work right.

---

### Post by jerrylin on 2008-01-19
What do you mean fixing the position of the battery?

---

### Post by riskable on 2008-01-20
I've had my XPS M1530 for a few weeks now and I have a few things to share plus I believe I can answer a few people's questions.  First, to answer some questions people have had:

1) Does the remote control work?  Yes.  The remote control/IR receiver is hard-wired to act like a keyboard.  So when you press the "up" button on the remote it will *literally* emulate the up arrow key on your keyboard (Ubuntu doesn't even have to know there's an IR receiver or remote for this to work).  If your remote isn't working it is either a broken remote or your battery wasn't seated properly.  For reference, the remote battery is a CR1016 and it goes into the remote with the text (and + sign) on top.

So to summarize the remote functionality:  Nothing to configure.  It should just "work"--even off of a boot CD or on the command line (I can even use it to select Ubuntu/Vista in grub).

2) The Dell MediaDirect button didn't work after I installed Ubuntu but I was able to boot it from the grub menu anyway (though, it won't start--it complains that it can't find my Vista partition but I'm going to delete it and replace it with Mythbuntu since MediaDirect sucks so bad).  Merely using the button to boot doesn't break anything (it just gives you an error).  No lost partitions or data.

3) I have the 802.11N wireless and it worked out of the box on Gutsy without any problems.  I did not have to download any drivers.

4) The fingerprint reader works fine if you use Thinkfinger.  Just follow the directions on the website (note:  it doesn't work in kdm or KDE).

5) All the media buttons work as expected without any configuration in both Gnome and KDE.  I'm very impressed with the Ubuntu team in this regards =).

6) The webcam works WONDERFULLY.  It did not require any configuration at all either.  I installed Skype and was immediately able to use it with the webcam.  I repeat:  I never had to configure anything.

7) The built-in bluetooth works with headsets (already got it working with Skype and for listening to music in stereo).  I've had major problems with this on other laptops so I'm glad Dell included a decent Bluetooth chip.

Now for my notes and observations:

A) I have the 1680x1050 LCD (so nice--especially with fonts--more on this below) and the default settings for the touchpad were horrid (too slow, too "tappy", too easy to accidentally hit it while typing, etc).  Here's what I've got in my xorg.conf for people to use as a reference:

```
Section "InputDevice"
        Identifier      "Synaptics Touchpad"
        Driver          "synaptics"
        Option          "SendCoreEvents"        "true"
        Option          "Device"        "/dev/psaux"
        Option          "Protocol"      "auto-dev"
        Option          "HorizEdgeScroll"       "0"
        Option          "SHMConfig"     "on"
        Option          "MaxTapTime"    "180"
        Option          "MaxTapMove"    "220"
        Option          "MinSpeed"      "0.70"
        Option          "MaxSpeed"      "1.10"
        Option          "AccelFactor"   "0.0520"
        Option          "HorizScrollDelta"      "17"
        Option          "VertScrollDelta"       "17"
EndSection
```

Also, to prevent the touchpad from messing with my typing I wrote a little script to startup the syndaemon and put it in my ~/.kde/Autostart folder.  Here's the script:

```
#!/bin/bash
syndaemon -k -i 0.5 &
```

B) After resuming from sleep or hibernate the screen does not come back on for me.  It may just be an Nvidia driver issue (I'm using the latest from their website--I'm going to try using the ones that came with Gutsy).

C) People who are saying that fonts are too small haven't set their DPI properly (yet).  In your xorg.conf under the "Monitor" section you need to tell X.org how large your display is so it can scale fonts properly.  I measured the LCD (it should be the same no matter which one you got)...  It's 332 X 208 mm.  So make sure your "Monitor" section in /etc/X11/xorg.conf looks like this:

```
Section "Monitor"
        Identifier      "Generic Monitor"
        DisplaySize     332     208
        Horizsync       28.0    -       84.0
        Vertrefresh     43.0    -       60.0
        Option          "DPMS"
EndSection
```

That's about 129x126 dots per inch on my 1680x1050 resolution.  It will be lower if you've got a 1440x900 or 1280x800 display.

That "DisplaySize" line will make it so that all KDE applications scale fonts properly (and automatically).  However, you'll still need to set your DPI manually in Gnome's Appearance control panel (if you're a Gnome) guy and Firefox will also need tweaking (since it is fixed at 96dpi by default).

Remember:  72 points is ONE INCH.  Always.  Period.  The "point" scale is an absolute measurement just like inches or a centimeters.  So no matter what resolution your screen is your fonts should always be the same size.

---

### Post by bnastic on 2008-01-20
Has anyone tried using external monitor with m1530?
Will it work in "lid closed" mode? (sorry if this sounds a bit dumb, m1530 will be my first linux/pc laptop, was running Macs up until now where this stuff just worked without any manual setup).

Is HDMI (+DVI converter) viable option for external monitor (I have 22", 1680x1050) on m1530? I don't feel like using VGA output.

TIA

---

### Post by vbabiy on 2008-01-21
Hey riskable were you able to fix the mouse? So when you close the lid and reopen it wouldn't go crazy?

---

### Post by lonelocust on 2008-01-22
I tried the xorg.conf configuration posted by riskable and it didn't change anything for me.  The touchpad works mostly okay until I close the lid, and then after opening it is nearly useless about 2/3 of the time because it jumps all over the place.
  Riskable also mentioned that the media keys work as expected.  I'm having problems with them myself.  The mute and volume keys work fine, but the others do nothing when I have any mp3 player or movie player app open (I've tried several).  Any suggestions?

---

### Post by Omnios on 2008-01-22
As for the jumping pad this is not a fix but ctrl-alt backspace will restart X which also should reset the pad.

---

### Post by jerrylin on 2008-01-23
I've been playing around on my M1530 with Ubuntu 7.10 x64 and so far so good.

**One thing I've found that no one else has mentioned:**
Intel Hardware Virtualization Technology is disabled by default?
Has anyone tried to install a 64-bit guest VM and got the message that you need to enable VT in the BIOS?
Unfortunately it doesn't look like the A05 bios allows you to turn it on.

Anyone have a solution or NOT have this issue?

---

### Post by pxleak on 2008-01-23
Hello! everyone I just purchased M1530 to be shipped on Feb 5 if not sooner. I'm new to Ubuntu myself and I gotta admit, I was impressed and it would make heads turn. I've been reading the post from day 1 and I wanna say hi to Mike and everyone enjoying this laptop and Ubuntu. 

Specs: 2.4 Ghz, 4 GB ram, 256 8600gt, 2x bluray (read/write), 250 HDD, WSXGA+ resolution, and all that regular installed components. 

I have a few questions though.

1. As I said I'm new to Ubuntu and even vista lol! Though I know I'm an average tech person. Is there a live cd available before I install it? If there is Ubuntu live cd has install too? Does anyone have a step by step guide in installation.

2. I don't want to mess up my Vista. I'll test the whole unit and vista making sure everything is working fine. Then I'll install Ubuntu. The question is will Vista and the unit itself (components, keys etc...) work normal even if Ubuntu is installed as partition drive, separate OS. I'm saying normal Vista and XPS routine with Ubuntu just installed but not running. I'm planning on dual boot and Vista will be needed to play games and school as well etc...

I've seen this link and I think this applies to 1530 to as well. 

[https://wiki.ubuntu.com/InstallingUbuntuOnADellXPSM1330]("https://wiki.ubuntu.com/InstallingUbuntuOnADellXPSM1330")

3. If Ubuntu messes up everything how can I uninstall it?

**I'm a graphics designer and doing some freelance, majoring in Animation.

---

### Post by Omnios on 2008-01-23
> **jerrylin said:**
> I've been playing around on my M1530 with Ubuntu 7.10 x64 and so far so good.

**One thing I've found that no one else has mentioned:**
Intel Hardware Virtualization Technology is disabled by default?
Has anyone tried to install a 64-bit guest VM and got the message that you need to enable VT in the BIOS?
Unfortunately it doesn't look like the A05 bios allows you to turn it on.

Anyone have a solution or NOT have this issue?

 I ready over the book that comes with it at it states the bus as 32bit can anyone clear up this. Is it possible to run 64bit?

---

### Post by Omnios on 2008-01-23
> **mike_pasara said:**
> Omnios, You shoudl have gotten the blu ray if you really wanted it. I am almost certain blu ray is here to stay. Disney and a few other movie makers are going with blu ray only. Not to mention blockbuster is supporting blu ray by only offering blu ray movies to customers. It's not a forsure thign yet but i am almost cetain blu ray will win versus hd-dvd.

if anyone is interested in upgrading their ram you can get 2gb sticks for 51.50 canadian and 50$ even for american currency.

[http://www.memorydepot.com/details.asp?id=KVR667D2S5%2F2G](http://www.memorydepot.com/details.asp?id=KVR667D2S5%2F2G)

it's kingston ram. so if your looking to upgrade your ram i would say this is the way to go. 4gigs of ram for 100$+ shipping... who would pass on that?

 Forgot to mention this before. I have no need for Blue Ray as of yet. Being on a disability I really can not want to dish out all that money for something I can do without. Maybe i the future but not right now as dishing out an extra $200 item and tax for the three service was more important. If something is going to go wrong it usually happens just after a year lol. I was advised by about three computer store owners to get extended service. I would have got the accidental  but that would have totally blown my budget.

---

### Post by Omnios on 2008-01-23
> **vbabiy said:**
> Hey riskable were you able to fix the mouse? So when you close the lid and reopen it wouldn't go crazy?

 Read somewhere that someone made a desktop script to fix this problem.

---

### Post by mike_pasara on 2008-01-23
I know what you mean, if you can't afford it you can't afford it. But my strong beliefs are that blu ray will come out a winner. maybe grab one when you can afford it.


Another note... is there a 100% working touchpad thing. because it's truly annoying when it jumps around. I am havin the same issue in vista but i can fix the  issue by clicking where the touchpad is "touching" so it's it in the right hand top corner i touch there once and and it goes away. With ubuntu it doesn't give you a touch pad sensor screen in the task bar or anything.

---

### Post by Omnios on 2008-01-23
> **mike_pasara said:**
> 

Another note... is there a 100% working touchpad thing. because it's truly annoying when it jumps around. I am havin the same issue in vista but i can fix the  issue by clicking where the touchpad is "touching" so it's it in the right hand top corner i touch there once and and it goes away. With ubuntu it doesn't give you a touch pad sensor screen in the task bar or anything.

 I remember reading a post, I think its in the dell forum area. Someone came up with a script that is located on the desktop. He stated you ran the script to fix the touchpad problem after hibrination..

---

### Post by pelle.k on 2008-01-24
Hey all XPS m1530 owners. I just ordered one myself, with a 1440x900 CCFL screen.
This will be my third (!) laptop within 6 months. I had to replace my first because of crappy viewing angles, light leakage, plus 1440x900 on a 14" lcd was too small really. The second one had good viewing angles, but 1680x1050 is too small on a 15" lcd (some of you might disagree).

So, i wanted to ask you how the 1440x900 lcd is treating you? (i.e viewing angles, light leakage, is it nice to your eyes, is it the LG screen?).

Also, i took 3 years "accidental". Does that mean i get a new one if mine dies, or do i have to physically break (accidentally, of course) it to get a replacement. Should i've opted for the extended "hardware support" instead?

---

### Post by jin psu on 2008-01-25
> **bnastic said:**
> Has anyone tried using external monitor with m1530?
Will it work in "lid closed" mode? (sorry if this sounds a bit dumb, m1530 will be my first linux/pc laptop, was running Macs up until now where this stuff just worked without any manual setup).

Is HDMI (+DVI converter) viable option for external monitor (I have 22", 1680x1050) on m1530? I don't feel like using VGA output.

TIA

I'm using an external 22" (1680x1050) with my M1530 (1280x800).  I use both displays in TwinView and it works great.  Font sizes are about the same on both displays at these resolutions.  I've been using VGA but just got an HDMI cable yesterday.  Unfortunately, I haven't got it working yet, the colors are all washed out and the screen is mostly greenish with HDMI.  Haven't spent any time looking into it though.

justin.

---

### Post by mike_pasara on 2008-01-25
> **Omnios said:**
> I remember reading a post, I think its in the dell forum area. Someone came up with a script that is located on the desktop. He stated you ran the script to fix the touchpad problem after hibrination..

Can you provide a link please, i have been searching and can't find what you are talking about.

---

### Post by Omnios on 2008-01-26
Hi guys I started a Dell XPS hardware thread to talk about the hardware in the XPS series laptops and also to hammer out how upgradeable they are,

 [http://ubuntuforums.org/showthread.php?t=677954](http://ubuntuforums.org/showthread.php?t=677954)

 Got hardware questions post them.

---

### Post by KoMpLoT on 2008-02-07
Just for everyone looking around some Dell supported Ubuntu, here you go:
[http://linux.dell.com/wiki/index.php/Ubuntu_7.10#Dell_OS_Reinstallation_7.10_DVD_ISO](http://linux.dell.com/wiki/index.php/Ubuntu_7.10#Dell_OS_Reinstallation_7.10_DVD_ISO)
There are versions of Gutsy for  some Inspiron models and for XPS M1330.
Anyway I have a XPS M1530 and I've installed the M1330 and works like a charm.

I also suggest installing ThinkFinger (to make the finger thing work) (more info at: [https://wiki.ubuntu.com/ThinkFinger](https://wiki.ubuntu.com/ThinkFinger)).
Also there is a great, yet simple, piece of software for the Webcam, called cheese. It's great!! :)

I also have hibernating issues, if someone knows how to solve them :) great!!

Oh, and maybe this page could help someone... I've just found it..
[http://www.wains.be/index.php/2008/01/21/ubuntu-on-dell-xps-m1330/](http://www.wains.be/index.php/2008/01/21/ubuntu-on-dell-xps-m1330/)

---

### Post by pelle.k on 2008-02-07
> I also have hibernating issues, if someone knows how to solve them  great!!
Do you mean hibernate, as in "suspend to disk" specifically, or does that include "suspend to ram" as well? To me, "suspend to ram" is the most important feature.
Also, you could try installing pm-utils, and if that doesn't work, try installing powersave(d?). You shouldn't really have to do something special, just reboot your computer once, then try to suspend/hibernate.

Please report back and tell us how it went.

---

### Post by namatarr on 2008-02-07
For anyone having touchpad problems take a look at the following post: [http://ubuntuforums.org/showthread.php?t=78904](http://ubuntuforums.org/showthread.php?t=78904)


For all m1530 owner's we have the ALPS touchpad which needs some additional settings to get things working properly with the synaptics driver.  

Be sure to cat /proc/bus/input/devices in order to obtain the correct event# from the touchpad.  If you use the event# from the guide above it will most likely not fix anything.

---

### Post by Aybara on 2008-02-13
I got this laptop yesterday. Gutsy is installed, and most of it works out-of-the-box. I'm having some wireless problems though. 

I have the "Intel® Next-Gen Wireless-N Mini-PCI Card". I can see networks, select mine, type in a WEP-key and connect, but once I try to use the connection I'm disconnected. Should I get a restricted driver or something?

---

### Post by pelle.k on 2008-02-19
I got my XPS m1530 (with the 3945 network card) a few days ago.
The first thing i did was to install the newest nvidia driver with envy, because it supposedly has better suspend/hibernate support. I also applied this piece of code i found in the dell wiki;
```
#!/bin/bash
# http://linux.dell.com/wiki/index.php/Ubuntu_7.10/Issues/8400M_Suspend_Hibernate-Failure
# Workaround for Suspend and Hibernate with nVidia video cards
perl -p -i -e "s|MODULES=\"\"|MODULES=\"uvcvideo\"|g;" /etc/default/acpi-support
perl -p -i -e "s|SAVE_VBE_STATE=true|SAVE_VBE_STATE=false|g;" /etc/default/acpi-support
perl -p -i -e "s|POST_VIDEO=true|POST_VIDEO=false|g;" /etc/default/acpi-support
perl -p -i -e "s|# DISABLE_DMA=true|DISABLE_DMA=true|g;" /etc/default/acpi-support
```
If you want to do the same thing, save it to a file, then do "sudo sh file_in_question". Reboot once, then try suspending.
I also noticed the second core seemed to "hang", that is, it doesn't speedstep correctly after suspending, so i uninstalled "powernowd", installed "cpufrequtils" (that may, or may not be relevant, either way i like cpufrequtils better), and then wrote a resume hook.
```
#! /bin/sh

## add to /etc/acpi/resume.d/99-cpufreq.sh
## remember to make it executable; "sudo chmod +x /etc/acpi/resume.d/99-cpufreq.sh"

modprobe -r acpi-cpufreq
modprobe -r cpufreq-ondemand
modprobe acpi-cpufreq
modprobe cpufreq-ondemand
invoke-rc.d cpufrequtils restart
```

I am also using the iwl3945 module, so i blacklisted the ipw3945 in /etc/modprobe.d/blacklist-ipw3945
```
blacklist ipw3945
```
and added "iwl3945" to /etc/modules.
It seems to work well, if you add it to MODULES="" in /etc/default/acpi-support, so that it correctly unloads before suspending.

---

### Post by Aybara on 2008-02-19
Do you have all audio jacks working on Gutsy? With Alsa 1.0.14 internal speakers and headphone jacks worked, but not the mic. With alsa 1.0.16 the mic and the right hp-jack works, while the rest is silent for me...

---

### Post by pelle.k on 2008-02-19
Unfortunately, no. That's a tough nut to crack.
I tried the linux-modules-backport from dell, and even the model=5stack option in alsa-base. No go.

---

### Post by Aybara on 2008-02-20
I compiled and installed alsa 1.0.16, and now it works for me :-)

---

### Post by Omnios on 2008-02-21
> **mike_pasara said:**
> Omnios, You shoudl have gotten the blu ray if you really wanted it. I am almost certain blu ray is here to stay. Disney and a few other movie makers are going with blu ray only. Not to mention blockbuster is supporting blu ray by only offering blu ray movies to customers. It's not a forsure thign yet but i am almost cetain blu ray will win versus hd-dvd.

if anyone is interested in upgrading their ram you can get 2gb sticks for 51.50 canadian and 50$ even for american currency.

[http://www.memorydepot.com/details.asp?id=KVR667D2S5%2F2G](http://www.memorydepot.com/details.asp?id=KVR667D2S5%2F2G)

it's kingston ram. so if your looking to upgrade your ram i would say this is the way to go. 4gigs of ram for 100$+ shipping... who would pass on that?


[SIZE="4"] "Blue Ray just won "There next major competitor through in the towel stating that the needed investment was to high for the expected returns. Herd it on G4-tech-TV[/SIZE]

---

### Post by GordonFreeman on 2008-03-24
On my system the special keys (fn+arrow up/down for light, fn+f1 for sleep, etc.) do not work out of the box.
What do I have to do to enable them?

I'm running Xubuntu 7.10

---

### Post by mattz on 2008-03-26
Hi I am also interested in purchasing this laptop. I am looking at getting the Penryn T9300 (2.5ghz) CPU and Nvidia 8600M GT.

I am wondering if there are any people who have tried yet with similar specs to play a 1080p video file. I am aware that it will be downsized on the smaller resolution laptop screen but I am just thinking ahead if I purchase a HD screen in the future and play it back on there.

I talked to a Dell rep today and he thinks it will be able to play it no problem but he would probably be referring to a video played in Windows, which supports Nvidia's Purevideo.

---

### Post by vbabiy on 2008-03-26
Hey has any one been able to get the Mic to work with 7.10. Or does any one know if it will work on 8.04?

---

### Post by Lacrimstein on 2008-04-02
I ordered mine yesterday, with the following specs:

-2.4 GHz Intel Core 2 Duo Processor
-1680x1050 HD Screen
-256MB nVidia GeForce 8600GT
-200GB 7200rpm hard drive
-DVD/CD-RW Drive
-Intel 3945 a/g wireless card
-4GB RAM 667MHz

Are there any issues other than hibernate i should know about?
Anyway, can't wait to play with it :)

---

### Post by Crafty Kisses on 2008-04-02
> **Lacrimstein said:**
> I ordered mine yesterday, with the following specs:

-2.4 GHz Intel Core 2 Duo Processor
-1680x1050 HD Screen
-256MB nVidia GeForce 8600GT
-200GB 7200rpm hard drive
-DVD/CD-RW Drive
-Intel 3945 a/g wireless card
-4GB RAM (Don't remember speed)

Can't wait to play with it :)

Lucky. Enjoy!

---

### Post by Twizz on 2008-04-04
The only other problem I have had so far, is the touchpad acting up sometimes after I close the lid, and open it.  Also I've noticed in ubuntu 8.04, my laptop comes out of sleep OK now more than before.

---

### Post by blierp on 2008-04-11
I'm currently using Hardy on my m1530 and everything is running peachy apart from the laptop getting very hot. Idle temperatures are 55~ and when i'm stressing the cpu it can reach 70. This is almost 20 degrees higher then in windows. I'm not sure why the temperature is getting so high though, cpu scaling is working properly as far as i can tell. Does anyone have a solution for this overheating issue?
lm-sensors can't detect my fans, maybe that has something to do with it?

---

### Post by kai ekael on 2008-04-16
I'm running Gutsy 7.10 64-bit on a m1530, most things work fine except for:

1. Wireless: I got the Intel 3945 card. I switched to the iwl3945 driver, sometimes it works fine, sometimes it's a reboot to get it to work.

2. Touchpad: Close the lid and the touchpad is hosed, just jumps around the screen. A USB mouse still works though, weird.

3. Webcam: No worky, though it seems like it should!

4. Screen dim on battery: THIS IS MADDENING! On battery, the screen dims. The function keys work to bring the brightness back up, BUT it dims back in 2 minutes no matter if I'm typing or whatever. I changed the power prefs, changed the BIOS setting, nothing changes that DIM. REALLY annoying (can you tell?).

[Things I haven't tried: mics, fingerprint reader, multi-reader]

This is the model with the 1680x1050 display (nice!), which appears to have issues.
It's nice the extra media buttons work just fine.


Anyone have any ideas on the screen dimming thing?

---

### Post by Twizz on 2008-04-17
I used Cheese program for the webcam.  Works ok.  I had the same problem with the screen diming, but I was able to solve it by changing the settings in power managers not to dim the display by any percent.  In 8.04 the only problem I have from 7 is the touch pad going crazy when you close the lid.  Standby works 90% of the time now it seems.  Now I can finally take off Vista!

---

### Post by mTuran on 2008-04-19
Hi guys,
i will buy XPS m1530 notebook i have 2 questions..

- i want to install ubuntu on m1530, there is any compability problems ? like wi-fi...
- What m1530 configuration is the best for ubuntu ?

---

### Post by lonelocust on 2008-04-27
I've made a couple changes to my system since I last posted and the touchpad doesn't work at all now.  I updated to the latest BIOS, A08 and did a clean install of 8.04.  If I try to use the touchpad it doesn't respond at all until I take my finger off of it.  Then random, and usually bad, things start to happen, like a bunch of windows with messages about changing to a different browsing mode opening, which I have to force quit to close.
  Another odd thing about this is that before these changes the command cat /proc/bus/input/devices showed me the alps touchpad, now I don't see it at all.  Is it possible that Ubuntu can't detect it with the new firmware?  Any ideas about what to do about all this?

---

### Post by lonelocust on 2008-04-27
I just found a solution to my own question.  If anyone else is having the same problem read this thread:
[http://ubuntuforums.org/showthread.php?t=737060](http://ubuntuforums.org/showthread.php?t=737060)

---

### Post by madiyaan on 2008-04-30
> **pelle.k said:**
> I got my XPS m1530 (with the 3945 network card) a few days ago.
The first thing i did was to install the newest nvidia driver with envy, because it supposedly has better suspend/hibernate support. I also applied this piece of code i found in the dell wiki;
```
#!/bin/bash
# http://linux.dell.com/wiki/index.php/Ubuntu_7.10/Issues/8400M_Suspend_Hibernate-Failure
# Workaround for Suspend and Hibernate with nVidia video cards
perl -p -i -e "s|MODULES=\"\"|MODULES=\"uvcvideo\"|g;" /etc/default/acpi-support
perl -p -i -e "s|SAVE_VBE_STATE=true|SAVE_VBE_STATE=false|g;" /etc/default/acpi-support
perl -p -i -e "s|POST_VIDEO=true|POST_VIDEO=false|g;" /etc/default/acpi-support
perl -p -i -e "s|# DISABLE_DMA=true|DISABLE_DMA=true|g;" /etc/default/acpi-support
```
If you want to do the same thing, save it to a file, then do "sudo sh file_in_question". Reboot once, then try suspending.
I also noticed the second core seemed to "hang", that is, it doesn't speedstep correctly after suspending, so i uninstalled "powernowd", installed "cpufrequtils" (that may, or may not be relevant, either way i like cpufrequtils better), and then wrote a resume hook.
```
#! /bin/sh

## add to /etc/acpi/resume.d/99-cpufreq.sh
## remember to make it executable; "sudo chmod +x /etc/acpi/resume.d/99-cpufreq.sh"

modprobe -r acpi-cpufreq
modprobe -r cpufreq-ondemand
modprobe acpi-cpufreq
modprobe cpufreq-ondemand
invoke-rc.d cpufrequtils restart
```

I am also using the iwl3945 module, so i blacklisted the ipw3945 in /etc/modprobe.d/blacklist-ipw3945
```
blacklist ipw3945
```
and added "iwl3945" to /etc/modules.
It seems to work well, if you add it to MODULES="" in /etc/default/acpi-support, so that it correctly unloads before suspending.

Hello. I used your method to write the script file and executed it. The changes were made to the file /etc/default/acpi-support. I also used envy to get the latest nvidia binary drivers and am using 8.04. I did apt-get install hibernate to install the hibernate binary. 

When I do hibernate, even with the changes above, I get this message:

```

Some modules failed to unload: nvidia
hibernate: Aborting suspend due to errors in ModulesUnloadBlacklist (use --force to override).

```

And when I use the --force option, it does some disk activity and turns off. However, when I turn it back on, it goes through the boot process (which is what I want to avoid basically).

Has anyone got hibernate to work for Ubuntu 8.04 for Dell XPS M1530?

Regards,

---

### Post by pelle.k on 2008-04-30
I would actually prefer "pm-utils" to "hibernate", as is now the standard in hardy (8.04). Btw, is the dual core speed stepping bug left in hardy? (If so i can whip up a pm-hook in no time...)
I don't think you need a newer nvidia driver than the one in hardy (in gutsy it did help, though).

I'm afraid i didn't keep my XPS, so i can't help you any more than this.

---

### Post by madiyaan on 2008-04-30
Hello pelle.k. 

Even closing the lid (not using the hibernate binary) does not work as intended. When I open the lid again, it goes through the boot process again (however, it does restore the applications that were running before the lid was closed). But this is "fake hibernate" as opening the lid should not go through the boot process: it should just load the data from disk and resume. 

The boot process is as slow as a regular cold boot and is annoying. Any help would be appreciated to fix this. I can post all my config if so desired. My hw is the following:

Core2Duo T9300
Nvidia 8600 GT (I don't know the exact driver version as I used envy to install it. If you can tell me the command to dump the version number I can post it)
4 GB RAM
Built-in Webcam

When I execute the hibernate application, it says that nvidia module could not be unloaded. When I do --force, it says something about uvdisplay (I believe this is the webcam), does some disk activity and turns off HDD. However, when I start the computer again, it takes just as long as a warm-boot.

Regards,

---

### Post by pelle.k on 2008-04-30
Well, i can only give you a few tips.
Uninstall "hibernate", install "pm-utils", *and* "uswsusp" and then try hibernating.
Also try "sudo nano /etc/pm/config.d/modules" and put;
```
SUSPEND_MODULES="uvcvideo"
```
in there (ctrl+x to save in nano...)

---

### Post by madiyaan on 2008-04-30
Hello pelle.k.

Thank you for your quick messages. I really appreciate that.

I removed hibernate and installed pm-utils (it was already there) and created a file /etc/pm/config.d/modules and put the line in there.

Unfortunately, upon opening the lid again I find that it goes through the boot process.

Any idea how to resolve this?

---

### Post by steenbras on 2008-05-01
Very happy with my XPS M1530 but I've got 2 niggles that are fairly annoying at the moment.

Has anyone managed to get audio working on the HDMI out? I get video but sound still comes from the laptop speakers. I upgraded to Hardy last week but can't be sure if this is the cause as I hadn't attempted HDMI out until after the upgrade. 

Also since the upgrade the volume control buttons on the laptop, and the slider on the panel both control the surround volume, not the master, and so have no effect on the actual volume being output.

Anyone have any ideas on either of these 2 issues?

---

### Post by pelle.k on 2008-05-01
Well, if i'm not mistaken that is how it is done, actually;
grub boots an OS entry, if pm-utils is installed it checks for a resume image in the swap partition and boots that instead.
It isn't super fast, but i don't think that is the primary objective either.
Still, for me it's faster than a cold/warm bootup.

[edit]s2ram, aka "suspend" is by design the fastest way though[/edit]

---

### Post by smacattack on 2008-05-03
I'm thinking of purchasing this laptop as well I just have a quick question...

I intend to dual-boot Vista and Ubuntu (Hardy) as I see many on this board are doing I'm just wondering what the best way to do that is?

I've been using Ubuntu for over a year now so I know my way around but would it be best to format the drive and do a clean install of Vista and then Ubuntu or what do you suggest?

[I know there is that new option to install Ubuntu with wubi inside windows but I'd rather have it on a dedicated partition]

---

### Post by rossmoore on 2008-05-06
Smacattack:
I should be getting mine in the next few days. I plan to boot it up to make sure the hardware all works, and check out vista for the first time (I haven't actually seen it yet!). Check the disk is appropriately defragged - I would hope so since this should be its second boot up after being checked at Dell.

Then boot down, stick in a Live CD and use the partitioner in the installer to split the drive into 4 - 1 small one (30Gb?) for Vista, 1 small one (30Gb?) for Hardy, 1 small one (15Gb?) for swap, and the rest for home.

I'm told Hardy 32 bit mostly works out of the box on this laptop, with a few ifs and buts to make sure wireless uses the best driver, and perhaps a tweak to menu.lst to get the trackpad working properly.

I'll let you know how it goes - especially if you remind me by posting to this thread in a few days!

---

### Post by seanhvw on 2008-05-06
I got my m1530 last week and installed Hardy. I used the Vista drive manager to shrink the Vista partition and then ran the Hardy install. It picked up the other OS (XP Media and Vista) and installed itself to the space I made, it also brought over my user accounts. Fingerprint, Video, and Sound all work after making a few changes. Waiting to get a larger drive and then installing Hardy as my Primary and Vista (or XP) as secondary for gaming. Very happy with how well it works on this machine.

Sean :)

---

### Post by FeG on 2008-05-07
Hi guys..

I'm thinking about buying a M1530 with a 9-cell-battery .. what is your experience, how much is the battery lifetime for this notebook under ubuntu?

Greetings
FeG

---

### Post by jerrylin on 2008-05-07
> **FeG said:**
> Hi guys..

I'm thinking about buying a M1530 with a 9-cell-battery .. what is your experience, how much is the battery lifetime for this notebook under ubuntu?

Greetings
FeG

I've had amazing performance with the 9-cell battery. I usually turn the monitor's brightness up all the way and use wifi and the laptop can run a good 3 hours straight. I sometimes get more or less depending on what exactly I am doing I guess.

---

### Post by FeG on 2008-05-07
Hi...

this sounds good.. has anyone tested how long the M1530 can run at most i.e. with the disply dimmed down?

Greetings
FeG

---

### Post by rossmoore on 2008-05-07
FeG: did you have MediaDirect on your laptop? I've read it can cause problems when it's installed as a hidden partition. I've also read that Dell laptops often come with 4 partitions already - i.e. no space to create another one. Did you find this, and how did you overcome it if you did - which one can I safely nuke?

---

### Post by FeG on 2008-05-07
> **rossmoore said:**
> FeG: did you have MediaDirect on your laptop? I've read it can cause problems when it's installed as a hidden partition. I've also read that Dell laptops often come with 4 partitions already - i.e. no space to create another one. Did you find this, and how did you overcome it if you did - which one can I safely nuke?

Hi rossmore,

I'm sorry but I don't have this laptop ;-) .. I was only thinking about buying one and so I wanted to know how long it runs on battery..

.. so I can't answer your question, sorry ..

Greetings
FeG

---

### Post by Omnios on 2008-05-07
> **smacattack said:**
> I'm thinking of purchasing this laptop as well I just have a quick question...
 
I intend to dual-boot Vista and Ubuntu (Hardy) as I see many on this board are doing I'm just wondering what the best way to do that is?
 
I've been using Ubuntu for over a year now so I know my way around but would it be best to format the drive and do a clean install of Vista and then Ubuntu or what do you suggest?
 
[I know there is that new option to install Ubuntu with wubi inside windows but I'd rather have it on a dedicated partition]
 
 If you havent used Vista yet its  hard drive hog, I made the mistake of buying the 160Gig hard drive so now have to wait till get something bigger -320 but the one I got quoted is still cheaper than there purchase upgrade so cant complain.

---

### Post by Omnios on 2008-05-07
> **rossmoore said:**
> Smacattack:
I should be getting mine in the next few days. I plan to boot it up to make sure the hardware all works, and check out vista for the first time (I haven't actually seen it yet!). Check the disk is appropriately defragged - I would hope so since this should be its second boot up after being checked at Dell.
 
Then boot down, stick in a Live CD and use the partitioner in the installer to split the drive into 4 - 1 small one (30Gb?) for Vista, 1 small one (30Gb?) for Hardy, 1 small one (15Gb?) for swap, and the rest for home.
 
I'm told Hardy 32 bit mostly works out of the box on this laptop, with a few ifs and buts to make sure wireless uses the best driver, and perhaps a tweak to menu.lst to get the trackpad working properly.
 
I'll let you know how it goes - especially if you remind me by posting to this thread in a few days!
 
 Not shure but read that the vista install disks do not like anything smaller than 40 to 60Gigs. Vista's a hard drive pig 20g for xp loaded up but vista is like 30gig almost bare.

---

### Post by madiyaan on 2008-05-20
> **pelle.k said:**
> Well, if i'm not mistaken that is how it is done, actually;
grub boots an OS entry, if pm-utils is installed it checks for a resume image in the swap partition and boots that instead.
It isn't super fast, but i don't think that is the primary objective either.
Still, for me it's faster than a cold/warm bootup.

[edit]s2ram, aka "suspend" is by design the fastest way though[/edit]

Hello:

Thank you for your message above. I don't think hibernate is done that way. For example, when Windows Vista hibernates (not suspends), it never shows the boot menu. It directly loads up Vista from disk and immediately shows login screen.

In my M1530 with Nvidia drivers, even suspend doesn't work properly. Any suggestions on getting it to work?

Regards,

---

### Post by pelle.k on 2008-05-20
> I don't think hibernate is done that way. For example, when Windows Vista hibernates (not suspends), it never shows the boot menu. It directly loads up Vista from disk and immediately shows login screen.

The graphics magic and whatnot is just the "friendly face" of the process wich in vista hides the vista bootloader and goes straight for the "hibernate" image. So it's no different there either.

No, i'm sorry to say i haven't got any good advice for you other than whats already been said. Sadly, hardware vendors are doing a real crappy job at following ACPI specifications so the linux developers have nothing to go on. Naturally they supply microsoft with the necessary info/drivers to make it work (for the most part) on windows machines only, and that is a shame.

Try a diffrent distro? "Mandriva 2008.1 gnome" is a nice distro with good hardware support, and it might just be that it'll work better with that hardware configuration you have there?

---

### Post by gOLdenHaWK3D on 2008-05-31
I bought a Dell XPS 1530 3 days back. Installed Ubuntu 8.04... Everything worked fine, except the NVidia 8600. So, I installed the restricted drivers. 

Everything working fine now :)

---

