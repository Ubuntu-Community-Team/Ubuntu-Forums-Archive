---
title: "Trying to install xubuntu and it just gets to a black screen after the..."
date: 2007-04-07
forum: Apple PPC Users
---

### Post by thegreenblob on 2007-04-07
xubuntu loading screen?

I just boot it up, then I press enter like it tells me to. Then it shows the xubuntu loading screen like everything is working, then after that it just goes to a black screen and nothing works?

Any help here?

Specs are imac g3 333mhz with 128mb of ram.

Thanks for any help. :)

---

### Post by 3rdalbum on 2007-04-07
iMac Blank Screens: [http://www.ubuntuforums.org/showthread.php?t=75604]("http://www.ubuntuforums.org/showthread.php?t=75604")

Guaranteed to work, or your money back :-)

---

### Post by thegreenblob on 2007-04-07
It didn't work :(

I edited the file then tried to restart x and it said stopping it was [ok] but when it tried to start it again it said it failed cause it was already running...

Any more help?

---

### Post by ZoiaGuyver on 2007-04-07
Here's the steps i normally use on the iMac's

ctrl-option-F1

at prompt type

sudo nano /etc/X11/xorg.conf

Look in the file for the "Modules" Section in there you should have one that says

Load "dri"

change that to 

#Load "dri"

Then look towards the bottom of the file for

HorizSync  

and

VertRefresh

change the values of these to

HorizSync 58-62 

VertRefresh 75-117

Then do ctrl + o  then enter

Then do ctrl + x

Then type

sudo killall -HUP gdm

That works on every iMac ive tried it on without fail as yet (these include G3 600 Graphite, G3 400 Bondi and a G3 450 Berry)

Hope this helps

---

### Post by thegreenblob on 2007-04-09
Thank you!!!

That got the live cd working. But... another problem :(

The installer crashes when I try to run it :(

So... any more help..?

---

### Post by ZoiaGuyver on 2007-04-09
Does the installer give an error message when it crashs??

If it doesnt you could try doing a command line install (think thats still on the Xubuntu CD).

At the "boot" prompt hit the "tab" key to list accepted installs (should say *live and a few others), If its in the list for boot type.

cli-install 

This will give you a very basic install with command line only but it should go through without probs and allow you to apt-get the stuff after the install.

If it is successfull and you then want Xubuntu to be installed at the prompt after logging in to your new ubuntu system type

sudo apt-get update 

Then

sudo apt-get upgrade (these commands will make sure the system is upto date)

Then

sudo apt-get install xorg 

Then

sudo apt-get install xubuntu-desktop

After this it should give you a working Xubuntu.

Hope this helps

---

### Post by thegreenblob on 2007-04-09
The "cli-install" isn't in the list :(

And yeah it gives me an error message. I'm booting it up now to see what it is so I'll edit that in here in like ~5 mins.

EDIT: erm... maybe a little longer cause this is a long error message, lol.

--EDIT2 (error)--

Traceback (most recent call last):
 File "/usr/bin/ubiquity", line 166, in ?
  Main()
 File "/usr/bin/ubiquity", line 161, in main
  install(sys.argv[1])
 File "/usr/bin/ubiquity", line 56, in install
  wizard = ui.Wizard(distro)
 File "/usr/lib/ubiquity/ubiquity/frontend/gtkui.py", line 177, in __init__
  self.customize_installer()
 File "/usr/lib/ubiquity/ubiquity/frontend/gtkui.py", line 339, in customize_installer
  self.tzmap = TimezoneMap(self)
 File "/usr/lib/ubiquity/ubiquity/frontend/gtkui.py", line 1827, in __init__
  self.tzdb = ubiquity.tz.Database()
 File "/usr/lib/ubiquity/tz.py", line 182, in __init__
  self.locations.append(Location(line, iso3166))
 File "/usr/lib/ubiquity/tz.py", line 168, in __init__
  today = datetime.datetime.today()
ValueError: microsend must be in 0..999999

---

### Post by ZoiaGuyver on 2007-04-10
That looks like the date bug for OF.

As the mac boots try hlding ctrl + option + p + r, you should hear a second boot sound if all has gone correctly and it will try and pull the correct date and time from the NTP servers.

To see if it is the bug when its booted do ctrl-alt-F1 and at the prompt type "date" if its the time bug the date will be something like 01/01/1970 (may not be that exactly).

Its a known prob with the older macs as the pram batterys have a tendency of dying. The only solution is to try and reset the pram and get it to lock down a new date and time. You could also try holding "n" when it boots this makes it try to boot off a network but has worked for me a couple of times. The Mac wont actually boot up (as there isnt a network to boot from) but it should reset the date.

Hope this helps

---

### Post by thegreenblob on 2007-04-10
Thanks you!!

The installer is running and I'm installing it!!

Although its lagging a bit but I'm pretty sure I'll be able to get it to work. Just take awhile, lol.

But, thanks for your help :)

---

### Post by ZoiaGuyver on 2007-04-10
hehe np the installer may lag a bit as its recommended to have atleast 196mb of ram where yours has 128mb :D

Hope you enjoy having a mess with Ubuntu it can be fun on Mac's

---

### Post by 3rdalbum on 2007-04-11
Actually, I'm having the same sort of trouble on Copland. I've tried reinstalling Ubiquity in the chroot, and it doesn't help.

My iMac's PRAM battery is fine, and I don't even get any error messages in the terminal. Either nothing appears (the disk thrashes for a while and then gives up) or the window appears briefly, but before it is populated with widgets it disappears. No messages in the terminal; very frustrating.

Are there any log files for Ubiquity that I can look in?

---

