---
title: "Can't install HP Photosmart C4180"
date: 2007-04-22
forum: Absolute Beginner Talk
---

### Post by Corvair on 2007-04-22
Printer HP Photosmart C4180

I try installing through regular procedure, System » Admin. »»  Print and My computer freezes on the second step before I have a chance to go down the list of drivers.

Has anyone come through a similar problem?

---

### Post by ramjet_1953 on 2007-04-22
Try doing it this way:

1. If you don't already have it, download [COLOR="Blue"]hplip[/COLOR], using Synaptic.

2. Download [COLOR="Blue"]python-qt3[/COLOR] and [COLOR="Blue"]python-qt3-gl[/COLOR] again, using Synaptic.

3. In a terminal type: [COLOR="Red"]sudo hp-setup[/COLOR]

4. There shuld now be an item in [COLOR="Blue"]System>Administration>HPLIP Toolbox[/COLOR]

5. Click on it

6. A window will open, telling you that no priners are configured, click on the button to add a printer and follow the dialog. 

7. Hopefully, your printer will now be installed and under the control of HPLIP.

Regards,
Roger :cool:

---

### Post by Corvair on 2007-04-22
Hello Roger,

Thank you for replying to my thread.

It is not working yet but I have a feeling we are getting closser

In terminal when doing hp-setup I get the reply back : command not found 
and I dont have the tool box with hplip

---

### Post by ramjet_1953 on 2007-04-22
Click on [COLOR="Blue"]System>Administration>Synaptic Package Manager
[/COLOR]
It will probably aske for your password - enter it

Click on the [COLOR="Blue"]Search[/COLOR] button

In the window that opens type in [COLOR="Red"]hplip[/COLOR]

check to see if there is a [COLOR="Lime"]green[/COLOR] square next to these files:

[COLOR="Red"]hpijs
hplip
hplip-data[/COLOR]

If any or all of these do not have a green square, right click on them and when the box opens, click on [COLOR="Red"]Mark for Installation[/COLOR].

Click OK for each one and they should install.

When this is done, refer to my previous post.

Regards,
Roger :cool:

---

### Post by Corvair on 2007-04-23
Hello Roger,

those 3 packages are installed (green)

I followed your instructions on the first message.

I dont' have a tool box in system admin by the name of hplip

In Terminal I get command not found to the request : sudo hp setup

Claude

---

### Post by ramjet_1953 on 2007-04-23
When you typed in a terminal did you put in the "-" sign?

ie sudo hp[COLOR="Red"]-[/COLOR]setup

Regards,
Roger 8-)

---

### Post by Corvair on 2007-04-23
Hello Roger,

Yes I did        sudo hp-setup

---

### Post by ramjet_1953 on 2007-04-23
In a terminal type in: [COLOR="Red"]whereis hp-setup[/COLOR]

You should get back something like this:

[COLOR="Blue"]roger@roger-laptop:~$ whereis hp-setup
hp-setup: /usr/bin/hp-setup /usr/X11R6/bin/hp-setup /usr/bin/X11/hp-setup
roger@roger-laptop:~$ [/COLOR]

That will definitely tell us that it is installed and where it is.

If you don't get this, something went horribly wrong with the install.

In a terminal type in [COLOR="Red"]cd /usr/bin[/COLOR]

Then type in: [COLOR="Red"]sudo hp-setup[/COLOR]

See how this goes.

Regards,
Roger 8)

---

### Post by Corvair on 2007-04-23
claude@ubuntuClaude:~$ sudo whereis hp-setup
Password:
hp-setup:
claude@ubuntuClaude:~$
claude@ubuntuClaude:~$ sudo cd /user/bin
sudo: cd: command not found
claude@ubuntuClaude:~$ cd /suer/bin
bash: cd: /suer/bin: No such file or directory
claude@ubuntuClaude:~$
claude@ubuntuClaude:~$ sudo hp-setup
sudo: hp-setup: command not found
claude@ubuntuClaude:~$

Like you said there is something definitely wrong.
Unfortunately I don't know enough to solve the problem by myself.
I apreciate your help and I will be waiting for your reply.

Claude

---

### Post by Sef on 2007-04-23
> I dont' have a tool box in system admin by the name of hplip

Check System > Preferences.   That is where mine is.

---

### Post by Corvair on 2007-04-23
Hello Sef,
I don't have anything like that in preferences either.

As you can see I can't get into hp set-up

Claude

---

### Post by ramjet_1953 on 2007-04-23
Ok, we're getting there!

Obviously, HPLIP is not really installed.

Go into Synaptic and search for [COLOR="Blue"]hplip[/COLOR]

As before you should see in the same screen the three programs:

[COLOR="Blue"]hpijs
hplip
hplip-data[/COLOR]

Right ckick on each entry individually  and when a small window opens, click on [COLOR="Blue"]re-install[/COLOR].

When you have done this for the three entries, click on [COLOR="Blue"]Apply[/COLOR] in the toolbar.

Make sure that your printer is plugged into your computer and turned on.

After this has been done, open a terminal and type in: [COLOR="Red"]sudo hp-setup[/COLOR]

Hopefully it will work this time.

Regards,
Roger :cool:

---

### Post by Corvair on 2007-04-24
claude@ubuntuClaude:~$ whereis hplip
hplip: /usr/lib/hplip /usr/share/hplip
claude@ubuntuClaude:~$ whereis hp-setup
hp-setup:
claude@ubuntuClaude:~$ cd /usr/bin
claude@ubuntuClaude:/usr/bin$ sudo hp-setup
Password:
sudo: hp-setup: command not found
claude@ubuntuClaude:/usr/bin$

I completely removed hpijs, hplip and hplip-data
I restarted the computer
I reinstalled the 3 files
Still can't find hp set-up.
Maybe the first two lines from the terminal will mean something to you.

Claude

---

### Post by Corvair on 2007-04-24
more info that may help you

claude@ubuntuClaude:~$ whereis hpijs
hpijs: /usr/bin/hpijs /usr/bin/X11/hpijs /usr/share/man/man1/hpijs.1.gz
claude@ubuntuClaude:~$ whereis hplip-data
hplip-data:
claude@ubuntuClaude:~$ whereis hplip
hplip: /usr/lib/hplip /usr/share/hplip
claude@ubuntuClaude:~$


Claude

---

### Post by ramjet_1953 on 2007-04-24
Now that HPLIP is definitely installed, we can try this:

In a terminal type in: [COLOR="Red"]hp-toolbox[/COLOR]

If no printer is set-up it should pop-up a notice, asking if want to do so.

Hopefully, this will work.

Regards,
Roger 8)

---

### Post by Corvair on 2007-04-25
this is what I got, but I dont' have time to work on it right now as I have to go to work

See you later.

Claude


claude@ubuntuClaude:~$ hp-toolbox

 HP Linux Imaging and Printing System (ver. 0.9.7)
 HP Device Manager ver. 6.0

 Copyright (c) 2003-5 Hewlett-Packard Development Company, LP
 This software comes with ABSOLUTELY NO WARRANTY.
 This is free software, and you are welcome to distribute it
 under certain conditions. See COPYING file for more details.

X Error: BadDevice, invalid or uninitialized input device 166
  Major opcode:  144
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 166
  Major opcode:  144
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
claude@ubuntuClaude:~$

---

### Post by Corvair on 2007-04-25
Hello again

I am no further than before.
Still can't get tool box.

As soon as I plug the printer to the computer it starts to search for data base and ends up freezing the computer.

What's next?

Claude

---

### Post by ramjet_1953 on 2007-04-26
Try :

[COLOR="Red"]gksu hp-toolbox[/COLOR]

Regards,
Roger 8)

---

### Post by Corvair on 2007-04-26
I get the same thing as before

claude@ubuntuClaude:~$ gksu hp-toolbox

 HP Linux Imaging and Printing System (ver. 0.9.7)
 HP Device Manager ver. 6.0

 Copyright (c) 2003-5 Hewlett-Packard Development Company, LP
 This software comes with ABSOLUTELY NO WARRANTY.
 This is free software, and you are welcome to distribute it
 under certain conditions. See COPYING file for more details.

  Major opcode:  144
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 166
  Major opcode:  144
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
Session management error: Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed
claude@ubuntuClaude:~$

The system hangs up again when I plug the printer to the computer.
I get the same thing as I did before I removed and reinstalled hpijs, hplip and hplip-data

After typing in gksu hp-toolbox I get a window HP DEVICE MANAGER
On top of it I get another window HP DEVICE MANAGER - NO INSTALLED HP DEVICES
To install a device, use CUPS web interface (host 631)  or the printer installation utility that came with your system. After setting up a printer youo must.......

On add a printer, step 2 of 3, printer driver, hte system hangs up and I have to restart the computer.

I am completely  lost.

---

### Post by ramjet_1953 on 2007-04-28
Sorry, I'm out of ideas!

HP stuff is usually painless.

Anyone else have any ideas to help out?

Regards,
Roger :cool:

---

### Post by Corvair on 2007-04-28
Hello Roger,

I want to thank you for trying to help.

Maybe I mislead you from the start.
In System » Admin. I have » Printer  which is probably the [COLOR="Red"]toolbox [COLOR="Red"][COLOR="Red"][COLOR="Red"][COLOR="Black"]you were talking about. With this I was able to install a printer box called Color StyleWriter-4100 but my printer is Photosmart C4180 so I think this is not the proper driver.

I had an HP  LaserJet IIIP printer installed before on a paralel port and it worked fine but now it is dead so I took it off the Printers window.

Now I am trying to install the HP Photosmart C4180 printer on a USB port because it does not have a paralel port.

When I turn the Printer on and plug it into the computer a window opens : GNOME -  CUPS - ADD  

The sytem goes to step 2 and freezes my computer and I have to restart.

This may make it clearer for you or anybody else who can HELP.

The printer works fine on Windows XP but I want to get rid of Windows so I would appreciate a solution for this problem.
Claude[/COLOR][/COLOR][/COLOR][/COLOR][/COLOR]

---

### Post by Corvair on 2007-04-29
I have finely been able to load the right driver, I think, for the HP photosmart C4180. 
It uses the same as the C3180. I loaded a print job but it is not going to the printer.
In CUPS I try to print a test copy but I am requested USER NAME  and PASS WORD 
 but of course this does not work.  I had this problem before with the LaserJet IIIP
 but I don't remember how I got over this.

Can anyone tell me how I can get the printer to respond?

Claude

---

### Post by Corvair on 2007-04-29
This is what I have in CUPS

[http://localhost:631/printers/](http://localhost:631/printers/)
  	

Search in Printers: Clear

Showing 1 of 1 printer.
  	Sort Descending 	 
PhotoSmart-3100 "/usr/lib/cups/backend/lpd failed"
	Description: hp photosmart C4180
Location:
Make and Model: HP PhotoSmart 3100 Foomatic/hpijs (recommended) - HPLIP 0.9.7
Printer State: stopped, accepting jobs, published.
Device URI: lpd://http://localhost:631/

---

### Post by Corvair on 2007-04-30
Here is an error list in CUPS  that may have some meaning for some initiates and help
find a solution to why my system freezes when I connect the USB cable.

:confused: 

E [30/Apr/2007:11:55:52 -0400] Bad request line "DEBUG: show_all_printers(http=0x8089860, user="(null)")" from localhost!
E [30/Apr/2007:11:55:53 -0400] Bad request line "DEBUG2: cgiSetIPPObjectVars(obj=0x808d3a0, prefix="(null)", element=0)" from localhost!
E [30/Apr/2007:11:57:06 -0400] Bad request line "DEBUG: show_all_printers(http=0x80898c0, user="(null)")" from localhost!
E [30/Apr/2007:11:58:03 -0400] Bad URI "http=0x80762a8" in request!
E [30/Apr/2007:11:58:08 -0400] Bad request line "/usr/share/cups/drivers/pscript5.dll: No such file or directory" from localhost!
E [30/Apr/2007:11:58:28 -0400] Bad request line "DEBUG: show_all_printers(http=0x8089860, user="(null)")" from localhost!
E [30/Apr/2007:11:58:40 -0400] Bad URI "http=0x80762a8" in request!
E [30/Apr/2007:12:02:06 -0400] Creating missing directory "/var/run/cups/certs"
E [30/Apr/2007:16:00:09 -0400] Creating missing directory "/var/run/cups/certs"
E [30/Apr/2007:16:33:38 -0400] Unknown directive debug on line 10.
E [30/Apr/2007:17:00:53 -0400] Unknown directive debug on line 10.
E [30/Apr/2007:17:00:53 -0400] Creating missing directory "/var/run/cups/certs"
E [30/Apr/2007:17:10:43 -0400] Creating missing directory "/var/run/cups/certs"

---

### Post by Corvair on 2007-05-02
Hello everyone,

I am still hoping to get some help on my problem.

I am able to load a printer in my printer window but it seems that the computer does not recognise the printer.
Could be a port problem but I don't know how to check this out. 

When installing the printer I am asked for a device, but there is no listing for USB so I enter :
Internet Printing Protocol (ipp)

Device URI :  [http://hostname:631/ipp/](http://hostname:631/ipp/)

Next step I enter PPD file : hppsc4100.ppd
Then I get: hp printer added succesfully.

Followed by : error: not found.

In System » Admin. » Printers I have hpphotosmartc4180  Reader.

In properties I go to Connection and click on Local Printer and Use a detected printer.

In General I request a Test Page Which is waiting to be printed.

Then when I plug the printer in the USB port a CUPS window opens up requesting to set-up a printer
and the computer hangs up and I have to restart it.

I want to use the printer as a local printer only.

If you see anything wrong in my procedure please corect me and straighten me up.

Any help would be appreciated.

hpphotosmartc4180 "open device failed; will retry in 30 seconds..."
	Description: HP Photosmart C4180
Location: Office
Make and Model: Local Raw Printer
Printer State: processing, accepting jobs, published.
Device URI: hp:/no_device_found


Claude

---

