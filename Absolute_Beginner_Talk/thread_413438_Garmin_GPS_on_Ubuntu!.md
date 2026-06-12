---
title: "Garmin GPS on Ubuntu?!"
date: 2007-04-19
forum: Absolute Beginner Talk
---

### Post by bodzasfanta on 2007-04-19
I have a [Garmin eTrex GPS]("https://buy.garmin.com/shop/shop.do?pID=6403&locale=en_US"). On XP I use MapSource to bring datas, make routes... etc.

My question is that is it available to use my GPS on Ubuntu? And open MapSource files?

---

### Post by Nik_Doof on 2007-04-19
Reading the specs it seems that it has a Serial interface, and from what (limited) knowledge I have about GPS apps is that they usually require a serial interface to the device, So it doesn't look like you'll need any funky drivers to get it to work.

---

### Post by traxtar3 on 2007-08-16
I have a Garmin Vista Cx (USB) and have had no problem using it in ubuntu via VMware-server reading my windows partition. see guide on venturecake.com

I was not impressed with GpsDrive, so i just used windows xp inside of ubuntu.

Mapsource installs beautifully and connects to my handheld with no problems.

---

### Post by ryaner on 2007-09-11
I just installed Mapsource with Wine. Installs fine but wont run. Jeeeees!!!!!!!

---

### Post by linuksamiko on 2007-09-28
I have an etrax too and there are different ways how you can use your garmin. But first of all, from my experienc it won't be that comfortable like mapsource. I could install mapsource with wine too but I never figured out how to get Serial running under wine (but I never spent much time trying to do so). Maybe you should try a little more on this one.

The best source for gps-software is this one right here:
[TuxMobile]("http://tuxmobil.org/linux_gps_navigation_applications.html")

I could get many things out of my Garmin using OSS-Software in Linux:
Waypoint, Tracks, the actual coordinats. So the most basic stuff worked ok (even if most of the programs are only commandline and hard to use).

The fare most sophisticated program for Linux I found was GPSDrive. This was actually fun to use. Even though I could only connect it to my Desktop-PC and the program is mostly made for mobile use.
[GPSDrive]("http://www.gpsdrive.de/index.shtml")

Well, it is possible to get some things out of your GPS using Linux but it is sometimes not quite easy.
One thing I never got to work was up/downloading maps to my Garmin. On TuxMobile is a new project wich seams to be able to extract maps from your Garmin but I can't test it anymore since I have a Laptop and no Serial Port.

I hope you will finde some interesting programs for your purposes.

---

### Post by ramadhian on 2007-10-05
My Nokia 6165i has built in GPS function

is there any possiblity for me to use it with GPSDrive ?

---

### Post by gewitty on 2007-10-07
I hooked up my Garmin Extrex to a serial port ( /dev/tty/S0 and /dev/tty/S1 ) but cannot get anything working. I have tried using gspsbabel from the command line, but this just returns an error message (MAGPROTO read error) and also tried using Mapsource running under Win XP using VirtualBox, which also fails to connect (I did remember to enable the COM ports).

Can anyone suggest why the port(s) are not accessible and how I can get the Garmin talking to either gpsbabel or Mapsource?

---

### Post by linuksamiko on 2007-10-13
you maybe have to change the Data mode on your Garmin. It is somewhere in the settings. I can't remember how it's called but Garmin can send data in different data formats. I think it was in Main menu --> Settings --> Datatransfer

I'm just a little surprised that Mapsource can't handle your Garmin. If you hadn't change anything the default settings should be recognized by Mapsource.
Well but maybe you should play a littlebit around with the transfer. Or check that you have chosen the right Serial Port

---

### Post by gewitty on 2007-10-13
Thanks for the ideas, but the Garmin is set up OK, as it used to work fine with a WIN XP machine. The problem seems to definitely be with Ubuntu not seeing the serial ports for some reason, but I'm not sure how to test these.

---

### Post by Sisophon2001 on 2007-10-13
I recommend you check out Qlandkarte for a linux replacement for the Garmin download program (MapSource?). I have this installed in SUSE 10.2.

I use gpsbable to download all my data, I created a script to run it, so I don't have to remember all the settings) and have some conversion scripts to convert the data into the formats I use with different programs.

To convert my display maps to Garmin format I had to use windows (free) programs, mapedit and GPSmapper, but for me this was a once off conversion.

For creating maps in Linux I use openJump.

Garvan

---

### Post by gewitty on 2007-10-13
Thanks Garvan. Sounds as if you are well ahead of me in using Open Source software for mapping. I haven't used any of the apps you mentioned but I'll check them all out and see if they help with my difficulties.

I have got Mapsource running successfully under WIN XP, using VirtualBox, but the main problem remains the fact that I cannot get a connection to the serial port.

If anyone has any ideas about this, or can give me help with testing the port for faults, I would be most grateful.

---

### Post by catnap on 2007-10-14
gewitty,

I also have a Garmin etrex and am having a similar problem.

To test the serial port my solution was to switch the etrex interface to NMEA. The interface settings can be found under setup. The etrex then outputs position plus other info in text form every second.

I had some trouble finding the right port, but found [http://ubuntuforums.org/showthread.php?t=422672&highlight=serial+port+problem+7.04]("http://ubuntuforums.org/showthread.php?t=422672&highlight=serial+port+problem+7.04") useful.

I then downloaded and used cutecom to select the right port (in my case it turned out to be /dev/ttyS1) at 4800 baud, and confirmed the NMEA text messages.

So I now know which port the etrex is on, and that it works.

My next step will be to use gpsabel to download the waypoints I need ([http://www.gpsbabel.org/htmldoc-1.3.4/fmt_garmin.html]("http://www.gpsbabel.org/htmldoc-1.3.4/fmt_garmin.html"))

hope this helps
catnap

---

### Post by Sisophon2001 on 2007-10-14
My Garmin is a serial port model and I can use this command syntax for gpsbable in ubuntu:

gpsbabel -w -i garmin -f /dev/ttyS0 -o gpx -F test_wpt.gpx

The GPS is set to GARMIN/GARMIN interface.

QLandkarte loads and displays the gpx file as produced. I have two other utilities I wrote myself, one converts the gpx file to a mif (Mapinfo Exchange Format - easy to import into many windows mapping programs) and the other to jml format for OpenJunp.

Garvan

---

### Post by gewitty on 2007-10-14
Thanks for those ideas. I'll give them a go and hopefully that will sort out the problem.

---

### Post by gerkin on 2007-12-21
Hi all

I use a Garmin eTrex (the basic yellow) model on Ubuntu 7.10 and have used it on Linux for some time. 

I have done a fair bit of reading on the subject and there doesn't yet appear to be a good pure linux alternative to most of the non-free GPS/mapping products.

I use a locally produced (N.Z) mapping software product called Freshmap and have tried several other products for my area & have found that they generally work poorly with "wine".  I have had reasonable success with VirtualBox running an XP environment.  

So far the best results have been with VMWare and an XP virtual Machine, running the Freshmap software & EasyGPS for upload/download waypoints, tracks or routes but  your mileage my vary.

Of all the Linux solutions GPSBabel seems to be the best in my opinion (command line only).  The other products generally have none or very poor map coverage in my part of the world anyway.  

GPSBabel can be used to upload/convert/download waypoints, tracks or routes, it works well with Geocaching.loc files & the eTrex.

I am currently working on a bash script to automate converting and uploading Geocaching.loc files.  If anyone is interested I would happy to post it here.

One other thing, I understand it can be very tricky to get USB GPS to hot-plug I am using the Garmin eTrex serial cable and it works very well and is also very reliable.

Hope this helps someone

cheers

---

### Post by kolinab on 2007-12-22
Thanks for that info gerkin.

I had given up on using my Garmin eTrex with Ubuntu, but I learned in another thread how to get it working. I don't have a serial port on my laptop and have been trying to get a USB to serial adapter working. Not sure what I actually did that makes the difference, but I learned to specify the port as /ttyUSB0.

Also, I set write permissions to the port:

```
sudo chmod 666 /dev/ttyUSB0
```

Maybe that's what did the trick?

I know you have these problems far behind you but I thought they might help those trying it out for the first time. 

I really don't need to DO much with the data from my GPS, mostly I want to back up my waypoints. So I'll take your recommendation of gpsbabel and see if it does what I want! I tried GPSman for a bit but I didn't take the time to see all its features.

K

---

### Post by gerkin on 2007-12-23
kolinab

you could also check out: [http://www.marengo-ltd.com/gps/](http://www.marengo-ltd.com/gps/)

I didn't have any luck with the "gps_upload.sh script" but it did give me some ideas for my own

hope this helps 

cheers ...........dave

---

### Post by gerkin on 2008-01-14
Hi all

I have been working on a few simple bash scripts to upload [http://www.geocaching.com/](http://www.geocaching.com/) .loc files & download waypoints,routes & track from Garmin eTrex yellow

I would be happy to share them and would invite any comments or suggestions (as I'm a bit of a novice coder)

The scripts are based around GPSBabel, and if you want me to post the 0.1 versions just let me know.

Also check out this GPS  site, which has all sorts of fantastic web based tools  :  [http://gpsvisualizer.com/](http://gpsvisualizer.com/) 

cheers ........gerkin

---

### Post by gerkin on 2008-01-15
Here is another site with heaps of links to GPS tools (some are open source):

[http://www.maps-gps-info.com/fgpfw.html](http://www.maps-gps-info.com/fgpfw.html)

---

### Post by catnap on 2008-02-17
QGis uses gpstools and worked well for me

---

### Post by catnap on 2008-02-17
Sorry Qgis uses a _gpsbabel _gui

---

### Post by carlao2005 on 2008-02-21
Hello,

I have a HP notebook dv6120, running ubuntu 7.10. This notebook does not have a serial port.

I have a Garmin Venture, with a serial cable.

I have bought a serial to usb adapter from Trendnet, named tu-69.

I linked the gps to the notebook with both cables, and running dmesg I have received:

[ 2232.584000] usbcore: registered new interface driver usbserial
[ 2232.588000] /build/buildd/linux-source-2.6.22-2.6.22/drivers/usb/serial/usb-serial.c: USB Serial support registered for generic
[ 2232.588000] usbcore: registered new interface driver usbserial_generic
[ 2232.588000] /build/buildd/linux-source-2.6.22-2.6.22/drivers/usb/serial/usb-serial.c: USB Serial Driver core
[ 2232.596000] /build/buildd/linux-source-2.6.22-2.6.22/drivers/usb/serial/usb-serial.c: USB Serial support registered for pl2303
[ 2232.600000] pl2303 1-2:1.0: pl2303 converter detected
[ 2232.600000] usb 1-2: pl2303 converter now attached to ttyUSB0
[ 2232.600000] usbcore: registered new interface driver pl2303
[ 2232.600000] /build/buildd/linux-source-2.6.22-2.6.22/drivers/usb/serial/pl2303.c: Prolific PL2303 USB to serial adaptor driver


It can be seen, on the third line from bottom to up, that the port is ttyUSB0.

I have tested gpstrans and gpsman, both were able to retrieve data from the unit, when I configured the port to ttyUSB0.

I will make some more tests with some gps programs, to handle the data downloaded from the gps unit, and post here the results.

Best regards,

Carlos
Ilheus - Bahia - Brasil

---

### Post by carlao2005 on 2008-02-21
just something more...

I used gpstrans with this command line:

 gpstrans -p /dev/ttyUSB0 -dt

-p sets the port to be used (/dev/ttyUSB0)

-dt is the command to -D-ownload the -T-rack on the gps unit.


On gpsman, I used the gui interface, setting the port to /dev/ttyUSB0.

Best regards,

Carlos

---

### Post by macogw on 2008-02-22
Er I'm kinda confused.  My mom has a Garmin GPS, but she didn't have to attach it to the computer to make it work.  All she did was take it out of the box and plug it into the car.  Why do you need a computer to make your GPS work?  Shouldn't it work on its own?

---

### Post by gewitty on 2008-02-22
> **macogw said:**
> Er I'm kinda confused.  My mom has a Garmin GPS, but she didn't have to attach it to the computer to make it work.  All she did was take it out of the box and plug it into the car.  Why do you need a computer to make your GPS work?  Shouldn't it work on its own?

You don't need a computer to make a GPS work. But if you have a handheld GPS (such as a Garmin Etrex) which you use for walking or geocaching, then it's very useful to be able to upload and download route information to a PC, where it can be displayed and manipulated using detailed terrain maps.

What your mom has is a straightforward car route-planner, which, as you say, works straight out of the box.

---

### Post by carlao2005 on 2008-03-04
Hello all,

After a time of lots of work, I had the time to complete my tests, as I have started to show some posts ago (they are in this page).

To my surprise, the hole thing was very very easy and fast! I have installed Qgis. In qgis, I went to menu "plugin", and then "plugin manager". Marked the box in "gps tools" and OK.

After that, and after linked my gps venture to the notebook usb port (via serial to usb adapter, as I have already said), I clicked on the gps icon on the right of the toolbar. Clicked on "download from gps", "garmin serial" (although it is on a usb!!) and in the port, /dev/ttyUSB0.

In "feature type", I have tried both waypoints and track. All worked OK! 

I wish this information is usefull to somebody.

Best regards to you all,

Carlos
Ilheus/Brasil

PS: sorry the poor english

---

### Post by themorningflight on 2008-03-10
Getting my Garmin Etrex Venture cx to work on Ubuntu has been an adventure it itself. See my [blog]("http://themorningflight.com/index.php/2008/03/07/garmin-etrex-gps-on-ubuntu/") for some info on how I got around it.

The short answer is that it will not be simple but worth the effort

---

### Post by s.merlin on 2008-04-14
Hi all 

Since 2 weeks, i try to connect my GPS Garmin Etrex Vanture (with serial port) to Qlandkarte. And it isn't successfull. :(
If i use another software like gpsman os Qisg it works fine.
Is there anybody with experience of this issues?? 


Hardware:

Dell inspiron 6400n with Ubuntu 7.10
Qlandkarte new version
Garmin etrex venture (old version grey scale) connected via USB to serial cable


s.merlin

---

### Post by kiwi-pete on 2008-04-28
Hello all, I am wondering if any Kiwi's here have tried to run/use NZMapped GPS with WINE.
I am running Ubuntu Hardy Heron, only been using it for just short of 2 weeks now, and tried to install it via WINE.
It keeps telling me this software must be installed under W95 or NT etc.

Do I have to set WINE for this as the software installs perfectly under my XP OS on the other PC's im using.

I really want this to work as I use NZMapped for my off roading in my 4x4. It will be running on my Mini ITX PC in the truck.

---

### Post by kxmas on 2008-05-16
I wasted some time figuring out how to get MapSource working with Wine on Hardy.

I am using Wine 1.0RC1

to get MapSource to install I used [winetricks]("http://www.kegel.com/wine/winetricks")...
```
$ winetricks corefonts
$ winetricks gecko 
```

To get MapSource to see the GPS, do this, then restart MapSource
```
$ sudo modprobe garmin_gps
$ ln -s /dev/ttyUSB0 ~/.wine/dosdevices/com1 
```

Use dmesg to figure out the exact tty device the garmin was attached to.

---

### Post by worlestone on 2008-05-27
Confirmed, works for me too.  Running Wine 0.9.59

I ran through the commands as suggested by kxmas and can now import/export to Garmin Quest from Mapsource under Ubuntu 8.04.  The device is recognised as COM1 by Mapsoure for some reason.  I have not tried to upload new mas yet, but will report back on speed when I do!

Thank you all for help

Adrian

---

### Post by rob09 on 2008-05-30
i've been trying to use the wine tricks but not sure the proper way to read the wine wine tricks for input any suggestions i have garmin nuvi 350 and the latest wine and the latest ubuntu and all i want to do is update my garmin maps and create maps any suggestions? let me know please I'm new to linuix

---

### Post by gewitty on 2008-06-03
I also got Mapsource running with Wine 0.9.59. I have successfully uploaded maps to both a Garmin C510 and an Etrex Vista HCx, using a USB connection.

The only curious thing I have noticed is that when doing a transfer, Mapsource begins by compiling an index list. This starts out fairly fast and quickly reaches the 68% complete mark, then it slows right down and takes anything up to 45 minutes to finish the transfer (or even longer, depending upon how many maps I'm uploading). During this period, my processor is working at 80% to 100% capacity. Can't figure out what's causing this slow-down though.

I also used Garmin's POI Loader and this works fine, with no delays at all.

Has anyone else experienced the same problem with Mapsource?

---

### Post by teich on 2008-06-07
Hm.  Install for me worked fine (even without using the suggested winetricks script), but I was only able to get the program to run correctly twice.  Now I am getting the following error on startup:

```
There is a problem with MapSource.
Please provide the following information to [GARMIN blah blah].
APPLICATION.CPP-399-2.00
```

I don't see an uninstall option anywhere, and reinstalling does not seem to change anything, nor does winetricks.  Frustrating.  I am using wine 0.9.47.

Thoughts?

---

### Post by teich on 2008-06-07
To add to the confusion, it occasionally (non-deterministically) works now, for no apparent reason.  However, after running 

```

modprobe garmin_gps
ln -s /dev/ttyUSB0 ~/.wine/dosdevices/com1
```

and attempting to send maps to the Garmin 60Csx, I get an error:

```

An error occurred while receiving data.
Broken pipe

Please ensure that the GPS's Interface option is set to GARMIN or host mode and try again.

```

This is a different error than if com1 does not exist, so it seems like the connection is being made but they just aren't talking to each other.

---

### Post by Alpinist on 2008-06-14
Thanks kxmas, I got Mapsource working in wine with your simple directions.  Haven't tried all the features but it seems pretty stable.  (wine platinum?)

Noticed that I need to do the modprobe garmin_gps to get mapsource to see the unit in wine but I need to remove it (sudo modprobe -r garmin_gps) in order for gpsbabel to work.

---

### Post by Alpinist on 2008-06-14
> **teich said:**
> However, after running 

```

modprobe garmin_gps
ln -s /dev/ttyUSB0 ~/.wine/dosdevices/com1
```

and attempting to send maps to the Garmin 60Csx, I get an error:

```

An error occurred while receiving data.
Broken pipe

Please ensure that the GPS's Interface option is set to GARMIN or host mode and try again.

```


I was getting a similar error just trying to connect to my GPS to receive data.  Just seemed to indicate the software wasn't seeing the unit at all.  In my case I noticed the unit was using /dev/ttyUSB1 so I ran the command
ln -s /dev/ttyUSB1 ~/.wine/dosdevices/com2 
and mapsource was able to see my unit on com2

---

### Post by halfhaggis on 2008-06-26
I got Mapsource installed without using winetricks, but make certain that the Mapsource version is the latest one provided on the Garmin website -- older versions don't work too well.

---

### Post by gewitty on 2008-06-26
Got MapSource talking to my Etrex HCx now, so loading maps is not a problem.

I've also been trying several other GPS apps, but far and away the best is Viking - [http://sourceforge.net/projects/viking/](http://sourceforge.net/projects/viking/). This is a really well-designed package that allows you to upload/download tracks and waypoints; create new tracks, etc. But the clever bit is that it uses Google Maps and satellite images, onto which you can overlay your data. The manual is a bit brief so far, but after playing around with it for a bit, the interface is fairly intuitive. Highly recommended.

---

### Post by jwcjr1 on 2008-07-01
When Mapsource launches I get this screen....any suggestions?

---

### Post by teich on 2008-07-02
Thanks for the heads-up on Viking, gewitty.  That's something I've been wanting for a while..

---

### Post by alek66 on 2008-07-13
> **jwcjr1 said:**
> When Mapsource launches I get this screen....any suggestions?

I have the same problem. Any luck whit that???:KS

---

