---
title: "Replacing WinXP with MythTV on 2nd drive"
date: 2007-04-14
forum: Absolute Beginner Talk
---

### Post by flyingsolo on 2007-04-14
My old Dell started with XP & I tried live Breezy CD, then dual-booted with XP & Breezy on one drive, then bought a new drive to put Dapper on it with XP on other but now I'm finally done with XP because Dapper does all I want/need and I want to try MythTV.

So now I want to remove WinXP from its drive and replace it with Myth (specifically,  Knoppmyth) but I sure don't want to mess up my Dapper.  Basically, I'm trying out Myth but in a dual boot arrangement with Dapper on the other drive.  Any suggestions how to proceed and problems to avoid or be aware of?

Thanks for any suggestions.

---

### Post by majoridiot on 2007-04-14
> **flyingsolo said:**
> So now I want to remove WinXP from its drive and replace it with Myth (specifically,  Knoppmyth)...

maybe you should check some knoppmyth forums, if you do not plan to use our ubuntu packages?

why you aren't is beyond me...

---

### Post by flyingsolo on 2007-04-14
Well, my understanding is that the Knoppmyth install is a light weight version of Knoppix with only packages required for the MythTV.  This seemed more sensible than a full 2nd install of Ubuntu with Myth also.
So, yes, you're right I could double up Ubuntu--but still my question really was how to [COLOR="Blue"]_safely_[/COLOR] remove XP from my 1st hard drive & replace it with Knoppmyth _or_ Ubuntu with Myth so as not to disturb Dapper install on 2nd drive.

Maybe changing tacks would be easier and just go with Ubuntu Myth install where it is already on drive 2 since it is mainly a trial of Myth but I'd prefer to have the "TV linux" separate from my workhorse linux.

---

### Post by majoridiot on 2007-04-14
[https://help.ubuntu.com/community/MythTV](https://help.ubuntu.com/community/MythTV)

is a good place to start.  it covers mythtv from dapper to the new feisty packages.  there are "light" 
(server only) installs that pretty much put in only the bare minumum.

if you installed dapper after XP, you should just be able to wipe your XP drive and then fix your grub 
menu.lst to remove the entry.  if it is booting from the xp drive, you can boot a live cd and fix grub after
XP is out.

---

### Post by click4851 on 2007-04-14
fair warning....I could not get what you are doing to work. I had the exact same setup, and attempted to do exactly what you are doing, my recollection was that Knoppmyth wants to load to hda and no other. If I remember the lead developer was asked about this and his response was to the effect of "it was designed to be a standalone device, not dualbooted with an additional desktop", I tried to find a way to dual boot with Edgy and was unsuccessful, others though claim to have been luckier than I. Definetly check out their forum, and the associated wiki.

P.S. I just went ahead and built a seperate tower and built my Knoppmyth in that, I love it.  Its running R5E50 I think, with an AMD 2600 and dual Hauppaguage tuners.

---

### Post by flyingsolo on 2007-04-14
Thanks for the advice/warning click4851.  The XP drive currently is hda because I recall Windows needed to be loaded first and then Dapper.  I'll keep banging away but maybe your fresh build idea is best.

---

### Post by click4851 on 2007-04-15
Well I would try to do what your doing, suuposedly if your good at editing grub and all the stars align it can be done, I just got to a point where I was done futzing with it, and I had this old case and motherboard that happens to work pretty well with mythtv....and you know how it goes. :) heck if you come up with a grub setting thats easy I bet they would love it.

---

### Post by majoridiot on 2007-04-15
if you installed dapper after windows and decide to try an ubuntu installation, it should be as simple as following the
guide for the mythtv server installs and installing on top of (formatting) the XP drive.  grub will sort out your menu
options to include dapper.

other than a small edit to grub menu.lst to possibly sort out the default grub choice and/or the logon timer, etc. it
should install fine.

i did this literally dozens of times testing the feisty mythtv packages, installing to a second hd with an existing edgy
install and had difficulties only once, due to a mistake.  it was easily sorted by booting the live cd and fixing grub
as usual.

---

### Post by flyingsolo on 2007-04-18
Thanks for advice guys.  For now, I've decided to go the 'easiest' way and just trial Myth on my existing Ubuntu 6.06 installation.  I've got a Hauppauge 150 and satellite service via BellExpressvu and I've got Myth via Synaptic.  The graphics card is weak--GeForce4 MX 440.

Following the Ubuntu guide, I hit a roadblock at configuring channel frequency table...satellite isn't an option--what to use?  I guess I use one of us-cable, us-cable-irc, or us-cable-hrc (no options for Canada & us-bcast doesn't seem right) but what are us-cable-irc & -hrc anyway?

Also, in the capture card setup menu, I chose the 'MPEG encoder card" selection but what goes in the 'video device' window (no default or entries in dropdown menu) and 'Default input' is also blank.  These don't accept manual input.

Sorry for so many questions!

---

### Post by majoridiot on 2007-04-18
you want us-cable for your frequency table.

if it doesn't find your 150, then the driver is not loaded correctly.  did you install ivtv?

[https://help.ubuntu.com/community/Install_IVTV_Dapper](https://help.ubuntu.com/community/Install_IVTV_Dapper)

[EDIT] i just caught the subtle reference to you being canadian... i would try us-cable first, as it seems the
logical choice for modulation on that box.  it won't hurt anything if it's wrong and you need to adjust it.

---

### Post by flyingsolo on 2007-04-18
Thanks majoridiot--between my last post & yours I realized the ivtv hadn't been addressed & was following the same link you gave.  It seemed to be going well but at the end, this happened:

~$ sudo modprobe ivtv
FATAL: Module ivtv not found.

Not sure what went wrong.

---

### Post by majoridiot on 2007-04-18
what sort of errors did you get along the way?

---

### Post by flyingsolo on 2007-04-18
I had one error reported after sudo apt-get update related to Automatix:

Err [http://www.getautomatix.com](http://www.getautomatix.com) dapper Release

W: GPG error: [http://www.getautomatix.com](http://www.getautomatix.com) dapper Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY CC919A31E23C5FC3
W: You may want to run apt-get update to correct these problems

Otherwise, I don't see any other errors.  Is the Automatix somehow interfering with the ivtv install? (I don't think it should)
Again, thanks for assistance--it's getting quite late at night where I am so I'll have to check back at this thread tomorrow after work.

---

### Post by majoridiot on 2007-04-18
i'm bringing this to superm1's attention to see if he has any thoughts...

---

### Post by superm1 on 2007-04-19
Flyingsolo,

Let see, you followed through all the ivtv guide (for dapper) steps.  Any errors along the way?  

Modules built fine and all?

---

### Post by flyingsolo on 2007-04-22
OK, me again...I sorted out the ivtv problem; when I cut/pasted one of the commands from the ivtv tutorial, a few letters got dropped...silly me.
So now I have ivtv setup and a zap2it account, downloaded our tv schedule so things are going well.  Haupaugge 150 is recognized but in Myth frontend, I get:
"Could not connect to the master backend server--is it running?  Is the IP address set for it in the setup program correct?"
Well, I have it set to the localhost 127.0.0.1.  For input connections, there are choices of tuner, composite0, composite1, S-video0, S-video1.  Since I have coaxial output of satellite box to the Haupaugge card, I assume 'tuner' is correct(?). I've tried composite connection also but Input connections list doesn't list any as recognized/active.
Suggestions please & thanks as always.

---

### Post by superm1 on 2007-04-22
> **flyingsolo said:**
> OK, me again...I sorted out the ivtv problem; when I cut/pasted one of the commands from the ivtv tutorial, a few letters got dropped...silly me.
So now I have ivtv setup and a zap2it account, downloaded our tv schedule so things are going well.  Haupaugge 150 is recognized but in Myth frontend, I get:
"Could not connect to the master backend server--is it running?  Is the IP address set for it in the setup program correct?"
Well, I have it set to the localhost 127.0.0.1.  For input connections, there are choices of tuner, composite0, composite1, S-video0, S-video1.  Since I have coaxial output of satellite box to the Haupaugge card, I assume 'tuner' is correct(?). I've tried composite connection also but Input connections list doesn't list any as recognized/active.
Suggestions please & thanks as always.
You have made sure to restart the backend correct?  Is the backend running?  See /var/log/mythtv/mythbackend.log for more information.  The most common cause of it not running ends up being permissions problems on the directory that recordings would be written to.

---

### Post by flyingsolo on 2007-04-22
I think permissions are set correctly.  As for the backend log, well there are 8 mythbackend.log files listed whose modification dates span the past week of me fixing/adjusting Myth.  The contents of the most recently created (today) is:
```
2007-04-22 12:48:09.535 MainServer::HandleAnnounce Monitor
2007-04-22 12:48:10.541 adding: ubuntu-desktop as a client (events: 0)
2007-04-22 12:48:10.559 MainServer::HandleAnnounce Monitor
2007-04-22 12:48:10.564 adding: ubuntu-desktop as a client (events: 1)
2007-04-22 13:27:04.948 MainServer::HandleAnnounce Monitor
2007-04-22 13:27:04.980 adding: ubuntu-desktop as a client (events: 0)
2007-04-22 13:27:04.985 MainServer::HandleAnnounce Monitor
2007-04-22 13:27:04.988 adding: ubuntu-desktop as a client (events: 1)
2007-04-22 13:27:29.927 MainServer: HandleRemoteEncoder(cmd GET_STATE) Unknown encoder: 2, exiting
2007-04-22 13:44:39.388 Using runtime prefix = /usr
QSettings: error creating /.qt
QSettings::sync: filename is null/empty
2007-04-22 13:44:39.680 New DB connection, total: 1
2007-04-22 13:44:39.716 Connected to database 'mythconverg' at host: localhost
2007-04-22 13:44:40.244 Current Schema Version: 1160
Starting up as the master server.
QSettings: error creating /.qt
QSettings::sync: filename is null/empty
2007-04-22 13:44:41.235 New DB connection, total: 2
2007-04-22 13:44:41.272 Connected to database 'mythconverg' at host: localhost
2007-04-22 13:44:41.323 EITHelper: localtime offset -3:00:00 
2007-04-22 13:44:41.364 TVRec(2) Error: Start channel invalid, setting to '615' on input Could not open '' to probe its i instead.
2007-04-22 13:44:41.376 Channel()::Open(): Can't open video device, error "No such file or directory"
ERROR: no valid capture cards are defined in the database.
Perhaps you should read the installation instructions?
2007-04-22 13:44:41.417 Main::Starting HttpServer
2007-04-22 13:44:41.441 Main::Registering HttpStatus Extension
2007-04-22 13:44:41.488 mythbackend version: 0.20.20060828-3 www.mythtv.org
2007-04-22 13:44:41.491 Enabled verbose msgs:  important general
2007-04-22 13:44:41.516 AutoExpire: Found 0 recorders w/max rate of 0 MiB/min
2007-04-22 13:44:41.521 AutoExpire: Required Free Space: 1.0 GB w/freq: 10 min
2007-04-22 14:52:29.638 MainServer::HandleAnnounce Monitor
2007-04-22 14:52:29.643 adding: ubuntu-desktop as a client (events: 0)
2007-04-22 14:52:29.652 MainServer::HandleAnnounce Monitor
2007-04-22 14:52:29.659 adding: ubuntu-desktop as a client (events: 1)
2007-04-22 15:05:39.043 MainServer: HandleRemoteEncoder(cmd GET_STATE) Unknown encoder: 2, exiting
2007-04-22 23:24:29.585 Using runtime prefix = /usr
2007-04-22 23:24:29.884 New DB connection, total: 1
2007-04-22 23:24:30.052 Connected to database 'mythconverg' at host: localhost
2007-04-22 23:24:30.066 Current Schema Version: 1160
Starting up as the master server.
2007-04-22 23:24:30.222 New DB connection, total: 2
2007-04-22 23:24:30.228 Connected to database 'mythconverg' at host: localhost
2007-04-22 23:24:30.238 EITHelper: localtime offset -3:00:00 
2007-04-22 23:24:30.290 TVRec(2) Error: Start channel invalid, setting to '615' on input Could not open '' to probe its i instead.
2007-04-22 23:24:30.322 New DB connection, total: 3
2007-04-22 23:24:30.350 Connected to database 'mythconverg' at host: localhost
ERROR: no valid capture cards are defined in the database.
Perhaps you should read the installation instructions?
2007-04-22 23:24:37.322 Main::Starting HttpServer
2007-04-22 23:24:37.346 Main::Registering HttpStatus Extension
2007-04-22 23:24:37.374 mythbackend version: 0.20.20060828-3 www.mythtv.org
2007-04-22 23:24:37.379 Enabled verbose msgs:  important general
2007-04-22 23:24:37.410 AutoExpire: Found 0 recorders w/max rate of 0 MiB/min
2007-04-22 23:24:37.418 AutoExpire: Required Free Space: 1.0 GB w/freq: 10 min
2007-04-22 23:26:05.722 MainServer::HandleAnnounce Monitor
2007-04-22 23:26:05.729 adding: ubuntu-desktop as a client (events: 0)
2007-04-22 23:26:05.734 MainServer::HandleAnnounce Monitor
2007-04-22 23:26:05.742 adding: ubuntu-desktop as a client (events: 1)

```

Unfortunately, it is again late & so will try again tomorrow

---

### Post by majoridiot on 2007-04-23
it looks like you don't have your capture card correctly configured in mythtv-setup.  you need to configure it in section 2, set up
your guide data source in step 3 and then bind that tuner to the channel source in step 4.

if you have partial entries for 2 and 3, i suggest deleting what is there, exiting mythtv-setup and then running it again to configure these
three steps.

(you will not need to run mythfilldatabase after deleting your entries the first time, but you do need to run it after making the
changes).

if you run into trouble, there are usually folks around to help in the #ubuntu-mythtv irc channel

---

