---
title: "Ubuntu 10.04 LTS on Ibook G4 fixes (SEE)"
date: 2011-03-05
forum: Apple Hardware Users
---

### Post by plecebo.mc on 2011-03-05
Here i have compiled a document that contains the fixes that i have made to my iBook G4 running Ubuntu 10.04 LTS PPC i discuss how to fix the fan, battery indicator, and how to mount your CD's to your drive (manually).I have composed this because its been a pain for me to find how to fix these problems.
__________________________________________________________________
Updated: Saturday March 5th, 2011
Running Ubuntu 10.04 LTS on iBook G4:

(notes)
“i have read it is recommended that when changing to the next install of Ubuntu on the iBook G4 to start with a clean install especially if it is an LTS like the one talked about here.”

specs:
12”, Airport Extreme, CD-R,Dvd drive, Bluetooth
PPC 1.2 GHz, 512MB Ram,60GB IDE HDD
Year: 2003
Ubuntu 10.04 LTS
2.6.32-28-powerpc #55-Ubuntu Mon Jan 10 21:20:02 UTC 2011 ppc GNU/Linux

Broken Features:
Hibernate
Lid Switch
Cd Drive (works but requires manual commands see Fixed Issues)

Fixed Issues:
*-fan doesn't spin (Important)
-Cd-Rom,Dvd drive doesn't poll
-battery indicator doesn't appear

Fixes:
__________________________________________________________________
Make iBook g4 fan control change upon startup:

-First make a new file that will be the script to change the value


"sudo nano /usr/local/sbin/<scriptname>"


-the new script should be the following:
_____________
#!/bin/sh
sudo echo "-10" > /sys/devices/temperatures/limit_adjust
____________


* -10 is the number stating the temperature sensitivity the lower the number the higher the sensitivity is to the temperature

-Next make the file executable:


"sudo chmod 744 /usr/local/sbin/<scriptname>"


-Now that the file is executable we need to edit the rc2.d file


"sudo ln -s /usr/local/sbin/<scriptname> /etc/rc2.d/ss99<scriptname>"


-thats it now restart the computer and check to see if it worked by checking the file: "/sys/devices/temperature/limit_adjust"

___________________________________________________________

#mount Cd (repeat after eject):

"udisks --poll-for-media /dev/hdc"

(must be manually done every time a disk loaded or ejected)


______________________________________________________________

Fix the battery indicator (David Ron):
-edit file “/etc/modules” and add the line “pmu_battery”

“sudo nano /etc/modules”

---

### Post by plecebo.mc on 2011-03-05
also there is a battery exchange program for this and a few other ibooks and powerbooks so check into that i just got a free battery cause mine could spontaneously catch fire :p

---

### Post by rsavage on 2011-03-05
This is a good idea.  I was thinking of putting something along these lines together myself.  I recently had to reinstall 10.4 following a trial of macbuntu and I wish I'd made a note of every little step I'd made.  It would of come in handy for me in the future as well as maybe helping others!

You may want to check out this thread [http://art.ubuntuforums.org/showthread.php?t=1498559](http://art.ubuntuforums.org/showthread.php?t=1498559) which has been a great help to me.  It does some good things, but others I'd change.  The method for getting fans to work is different to your method.  Where did you get yours from?  Things I'd change are I'd install powernowd instead of cpudyn.  I wouldn't bother compiling a new kernel because using the described method will take hours and hours to compile and is sure to give you an error anyway.  In my experience there are more steps to follow to get wireless to work.  The Xorg.conf files are way too complicated and don't highlight what actually has to be put in.  Your method of getting the battery status is better.

I'm still working on getting the perfect setup, but am so impressed with my ubuntu/ibook combination!

Incidentally, what is the problem with your lid switch?

---

### Post by plecebo.mc on 2011-03-05
when you close the lid ubuntu doesnt know its closed

yeah this is a compilation of things i have found using google

im glad you like it

---

### Post by rsavage on 2011-03-06
I have the same model (but without the bluetooth).  When I close the lid the computer goes into suspend.  I have the flashing light at the front.  When i open the lid it wakes up and asks me to log in.  Working perfect?

Is there something mechanically wrong with your switch?  Actually, I think it is triggered by a magnet on the side of the computer which can move about if you've taken the iBook apart.  If not aligned correctly it won't suspend.  You should be able to trigger suspend by passing a magnet along the right side of the LCD screen if I remember correctly (but best to do a google first to check I'm right).

---

### Post by plecebo.mc on 2011-03-06
OMG thanks man your a life saver cause i had to take it apart to resolder my power jack on the board and i wondered what that thing was for thanks. i will fix this right now :)

---

### Post by aquilainferna on 2011-03-08
Hi placebo i have a found a stone in my way and i don't know if is one great or a litle problem, well when i wwere writing the fan fix the Terminal shots me a message, it says that the directory /sys/devices/temperatures/limit_adjust doesn't exist, so i went to seek that directory and i realize that it really isn't there.
It's normal which is explain in the last text. I have to install some app or some is wrong with my ubuntu instalation?. 



Great job making alternatives to the use of Mac os. Congratulations

Ah of course my machine is a ibook g4 12" 1.2Ghz and sorry if my english looks freaky that is because i'm not a native speaker.

bye bye

Using Ubuntu since 2 days ago

---

### Post by rsavage on 2011-03-10
[aquilainferna]("http://ubuntuforums.org/member.php?u=1258451"), are you still having problems?  I can try and help you until plecebo.mc is available.  But, I should say it is their method and I don't know much about it.  I use another method that is described in the link I gave earlier.

I think you should have /sys/devices/temperatures/limit_adjust, but I am not an expert!  I remember when I first started using linux I couldn't find anything!

At a terminal type "cat /sys/devices/temperatures/limit_adjust".  This will print the contents of the file.  For me it just prints a "0", but under plecebo.mc's method I think it should print a "-10".

---

### Post by plecebo.mc on 2011-03-25
did you figure out the problem because i was on vacation sorry :(

rsavage: the problem with the fan is that it is set to "0" setting the limit to "-10" is the best fix but in order for it to stay at "-10" you need to follow the method i found otherwise you will have to manually change that limit every time you restart.

also i find that using nano is the best way to edit the file if you need help using it just ask.

---

### Post by plecebo.mc on 2011-03-25
this is the original post i found for the method im using for fixing the fan
[http://ubuntuforums.org/showthread.php?t=132164]("http://ubuntuforums.org/showthread.php?t=132164")

---

### Post by gabrielgj on 2011-04-01
Help! plecebo.mc, I followed all your directions but it didn't work for me. 

I typed in  
"sudo echo "-10" > /sys/devices/temperatures/limit_adjust" but all  I get this error:
"bash: /sys/devices/temperatures/limit_adjust: Permission denied"
and when I type "cat /sys/devices/temperatures/limit_adjust" I get "0" 

I'm new to Linux and Mac so I know nothing about all this. Oy!

I'm also having troubling enabling desktop effect on this Ibook g4[-o<

---

### Post by gabrielgj on 2011-04-02
I have another problem. My battery doesn't charge and I don't know why.

Power Statistics:
Device                                    battery_PMU_battery_0
Type                                       Laptop battery
Supply                                    Yes
Refreshed                              0 seconds
Present                                  No
Rechargeable                        Yes
State                                      discharging
Energy                                   0.0 Wh
Energy when empty              0.0 Wh
Energy (design)                     0.0 Wh
Rate                                        0.0 W  
Voltage                                    16.7 V
Time to full                               0 seconds
Time to empty                         0 seconds
Percentage                             0.0%
Capacity                                 0.0%
Technology                            Unknown technology

I tried resetting the pmu by pressing "Shift-Control-Option-Power" but it didn't work. oy!

---

