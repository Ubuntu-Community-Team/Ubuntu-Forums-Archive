---
title: "Can Someone Recommend"
date: 2007-04-29
forum: Absolute Beginner Talk
---

### Post by Angelbeast on 2007-04-29
I've been trying Ubuntu Feisty Fawn for the past several days and i really love it. The only issue however is the wireless issues. I have tried every recommendation i could find on here and elsewhere with no luck. I have one of those evil Broadcom cards. So i really want to keep using Ubuntu but i simply NEED to have wireless access. So can someone recommend a distro that is similar to Ubuntu, but that wireless actually works in, until the wireless issue is resolved in a future release?

---

### Post by earobinson on 2007-04-29
Broadcom afaik is a global linux problem (since distros shair source) Your best bet is to get a new card :(

Sorry

---

### Post by Angelbeast on 2007-04-29
I was afraid of that. Which one seems to work best with Linux?

---

### Post by Angelbeast on 2007-04-29
I forgot to mention also that i'm on a laptop.

---

### Post by nonewmsgs on 2007-04-29
netgear tend to use atheros.  it's a restricted driver but ive already bought 3 of those cards and they just work.  they're pretty reasonable on ebay.  

edit: add: well all the netgear ones i bought were all pcmcia laptop ones :P
i think i have 2 rangemax and one other one...i had absolutly no trouble.  i think im going to sell the prism cards i have -- windows garbage.

---

### Post by Angelbeast on 2007-04-29
> **nonewmsgs said:**
> netgear tend to use atheros.  it's a restricted driver but ive already bought 3 of those cards and they just work.  they're pretty reasonable on ebay.  

edit: add: well all the netgear ones i bought were all pcmcia laptop ones :P
i think i have 2 rangemax and one other one...i had absolutly no trouble.  i think im going to sell the prism cards i have -- windows garbage.

pcmcia...

are those theexternal ones? isee different models of netgear on ebay...which specific one do you use?

---

### Post by Angelbeast on 2007-04-29
Okay...i've been wondering how SOME people with broadcom get it to work...does it make much difference which brodcom driver it is? i have bmcwl5.sys ... 

this is just craziness...well as James T. Kirk says..."There's gotta be a way" ... *LOL*

---

### Post by MrKlean on 2007-04-29
The wireless card in my satellite worked with FF..and my new laptop...Acer///works with it..no problems/  I just clicked Network.. added my ascii phrase and connected.  I think laptops are easier than desktops LOL

---

### Post by Angelbeast on 2007-04-29
you have  broadcom card?

---

### Post by Angelbeast on 2007-04-29
i was thinking also...i had installed he 64 bit version...is there more success with the 32 bit one?

---

### Post by Straywolf on 2007-04-30
hey I found this, hope it helps

If you're running Ubuntu on a laptop and your Wi-Fi card is not detected or supported, try installing the Ndisgtk package (listed as such in Synaptic, but as 'Wireless Windows Drivers' in Add/Remove Applications). Then select the new System, Administration, Windows Wireless Drivers entry in Ubuntu's menu bar. The ensuing dialog box asks for the location of an INF file that represents the Windows driver for your wireless adapter. Have a driver disc? Find the INF file on there and see if Ndisgtk can get you up and running.

---

### Post by Angelbeast on 2007-04-30
> **Straywolf said:**
> hey I found this, hope it helps

If you're running Ubuntu on a laptop and your Wi-Fi card is not detected or supported, try installing the Ndisgtk package (listed as such in Synaptic, but as 'Wireless Windows Drivers' in Add/Remove Applications). Then select the new System, Administration, Windows Wireless Drivers entry in Ubuntu's menu bar. The ensuing dialog box asks for the location of an INF file that represents the Windows driver for your wireless adapter. Have a driver disc? Find the INF file on there and see if Ndisgtk can get you up and running.


ooooo...where did you find that? It sound promising...I'll try it tuesday or wed...I had to put windows bck on so i can download Heroes tomorrow night coz i'm in school when it comes on *LOL* ...

---

### Post by Angelbeast on 2007-05-02
> **Straywolf said:**
> hey I found this, hope it helps

If you're running Ubuntu on a laptop and your Wi-Fi card is not detected or supported, try installing the Ndisgtk package (listed as such in Synaptic, but as 'Wireless Windows Drivers' in Add/Remove Applications). Then select the new System, Administration, Windows Wireless Drivers entry in Ubuntu's menu bar. The ensuing dialog box asks for the location of an INF file that represents the Windows driver for your wireless adapter. Have a driver disc? Find the INF file on there and see if Ndisgtk can get you up and running.

Okay i tried this and i think it may work...however...my hardware is not detected...how do i fix THAT? I've included a screenshot...

---

### Post by Fitzy_oz on 2007-05-02
> **Angelbeast said:**
> i was thinking also...i had installed he 64 bit version...is there more success with the 32 bit one?

I would go with the 32bit one personally, also you'll need to blacklist the module that drives the wireless card.  Drop to a terminal and type sudo nano /etc/modprobe.d/blacklist

add a line like so:
**blacklist [wireless module name]**

Then reboot and the wrapper should do the rest for you.

---

### Post by Angelbeast on 2007-05-02
> **Fitzy_oz said:**
> I feel you're pain.  Have you tried the ndiswrapper yet?  This method will use the Windows NDIS driver instead of you're evil broadcom piece of poop. You will have to blacklist the module that runs you're broadcom driver though.

oh fun...is there a tutorial on that bit of joy?

---

### Post by MilosDusan on 2007-05-02
I hate to sound cruel, but curse these Broadcom cards..

I seriously recommend the 'easy' way out.. Go pickup a supported WiFi card to replace the one you have existing.. You'll find that the 'plug and play' ones will make life with Ubuntu so much easier!!

[http://linux-wless.passys.nl/"]]http://linux-wless.passys.nl/](")

Any card listed in 'green' is pure gold.. I dropped $40 on a new Linksys WMP54G, and nearly cried when I installed it in the system, and Ubuntu not only picked it up, but I was online as soon as I booted in....

---

### Post by Fitzy_oz on 2007-05-02
> **Angelbeast said:**
> oh fun...is there a tutorial on that bit of joy?

Sorry mate my computer crashed while I was editing the last post - It's actually pretty straight forward - 

drop to a terminal and type sudo nano /etc/modprobe.d/blacklist and add the like **blacklist [wireless module name goes here]**

Reboot and you should be good to go.

I had these same issues with my belkin wireless card as well as my netgear usb dongle, the ndiswrapper runs them both flawlessly now.

---

### Post by Angelbeast on 2007-05-02
> **MilosDusan said:**
> I hate to sound cruel, but curse these Broadcom cards..

I seriously recommend the 'easy' way out.. Go pickup a supported WiFi card to replace the one you have existing.. You'll find that the 'plug and play' ones will make life with Ubuntu so much easier!!

[http://linux-wless.passys.nl/"]]http://linux-wless.passys.nl/](")

Any card listed in 'green' is pure gold.. I dropped $40 on a new Linksys WMP54G, and nearly cried when I installed it in the system, and Ubuntu not only picked it up, but I was online as soon as I booted in....

i would love to do that...but at the moment it's not an option *LOL* ... i'm so poor right now that i don't see having the funds for that anytime soon...

---

### Post by Angelbeast on 2007-05-02
> **Fitzy_oz said:**
> Sorry mate my computer crashed while I was editing the last post - It's actually pretty straight forward - 

drop to a terminal and type sudo nano /etc/modprobe.d/blacklist and add the like **blacklist [wireless module name goes here]**

Reboot and you should be good to go.

I had these same issues with my belkin wireless card as well as my netgear usb dongle, the ndiswrapper runs them both flawlessly now.

okay sorry to sound ignorant but what is  the wireless module name? and will this make my card show up? did you see the screenshot of what i was talking about?

---

### Post by Fitzy_oz on 2007-05-02
> **Angelbeast said:**
> okay sorry to sound ignorant but what is  the wireless module name? and will this make my card show up? did you see the screenshot of what i was talking about?

No need to be sorry, what type of wireless card is it - model name for exmaple, If you can get that for me I can tell you which module to blacklist...

---

### Post by Angelbeast on 2007-05-02
> **Fitzy_oz said:**
> No need to be sorry, what type of wireless card is it - model name for exmaple, If you can get that for me I can tell you which module to blacklist...

does this have what you need?

ron@ron-laptop:~$  lspci | grep Broadcom\ Corporation
06:02.0 Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)

---

### Post by Fitzy_oz on 2007-05-02
> **Angelbeast said:**
> does this have what you need?

ron@ron-laptop:~$  lspci | grep Broadcom\ Corporation
06:02.0 Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)

Ok, this is the line you need to add to the blacklist file I talked about earlier.

**blacklist bcm43xx**
save it and reboot, you should be right after that...

---

### Post by Angelbeast on 2007-05-02
okay i think i may have made some sort of progress with this:  [http://ubuntuguide.org/wiki/Ubuntu:Feisty#Ndiswrapper_for_Broadcom_43xx_wireless_chipset](http://ubuntuguide.org/wiki/Ubuntu:Feisty#Ndiswrapper_for_Broadcom_43xx_wireless_chipset)

now it will detect wireless networks but will not connect and still says my hardware is not detected...

---

### Post by Angelbeast on 2007-05-02
> **Fitzy_oz said:**
> Ok, this is the line you need to add to the blacklist file I talked about earlier.

**blacklist bcm43xx**
save it and reboot, you should be right after that...

okay i'm trying it now...it's gonna take a few min though coz to get a wireless network here i have to go upstairs and across the house *LOL*

---

### Post by Fitzy_oz on 2007-05-02
> **Angelbeast said:**
> okay i think i may have made some sort of progress with this:  [http://ubuntuguide.org/wiki/Ubuntu:Feisty#Ndiswrapper_for_Broadcom_43xx_wireless_chipset](http://ubuntuguide.org/wiki/Ubuntu:Feisty#Ndiswrapper_for_Broadcom_43xx_wireless_chipset)

now it will detect wireless networks but will not connect and still says my hardware is not detected...

You should really have to go though all of that - Feisty has a nice Graphical interface for it called windows drivers which is already there - All you should need to to is blacklist the module. Let me know how you go.

---

### Post by Angelbeast on 2007-05-02
> **Fitzy_oz said:**
> You should really have to go though all of that - Feisty has a nice Graphical interface for it called windows drivers which is already there - All you should need to to is blacklist the module. Let me know how you go.

well i blacklisted the module and it does show a network and tries to connect toit...or at least appears as ifit is...but then it never connects to anything...

---

### Post by Fitzy_oz on 2007-05-02
> **Angelbeast said:**
> well i blacklisted the module and it does show a network and tries to connect toit...or at least appears as ifit is...but then it never connects to anything...

are you running any wep or wpa keys for encryption?  Is it listing you're wireless network router's ID (Im assuming it's an ADSL router) correctly? If this fails we may be able to set it up statically...

---

### Post by Angelbeast on 2007-05-02
> **Fitzy_oz said:**
> are you running any wep or wpa keys for encryption?  Is it listing you're wireless network router's ID (Im assuming it's an ADSL router) correctly? If this fails we may be able to set it up statically...

i need it so that t will detect and connect to various networks. for the time being i have to go to friends house or to public places to connect unless i come over here to my moms house and sit in the basement on the wire *LOL*

---

### Post by Fitzy_oz on 2007-05-02
> **Angelbeast said:**
> i need it so that t will detect and connect to various networks. for the time being i have to go to friends house or to public places to connect unless i come over here to my moms house and sit in the basement on the wire *LOL*

Ahhh, now it makes sense.... Which driver did you end up using for the NDISWRAPPER - you can use the XP/98/2000 driver all of them should work, it might even be worth trialling them and seeing which one works the best.  It sounds to me like you're right on the edge of it working....  If you can, drop to a terminal and type iwlist wlan0 scanning and post the output... (You'll need to be in the vicinity of the wireless network of courese lol)

---

### Post by Angelbeast on 2007-05-02
> **Fitzy_oz said:**
> Ahhh, now it makes sense.... Which driver did you end up using for the NDISWRAPPER - you can use the XP/98/2000 driver all of them should work, it might even be worth trialling them and seeing which one works the best.  It sounds to me like you're right on the edge of it working....  If you can, drop to a terminal and type iwlist wlan0 scanning and post the output... (You'll need to be in the vicinity of the wireless network of courese lol)

okay give me just a few min to finish up an email and i'll make another trip and let you know what it say *LOL* ... thanks by the way for all of your help...

---

### Post by Angelbeast on 2007-05-02
> **Fitzy_oz said:**
> Ahhh, now it makes sense.... Which driver did you end up using for the NDISWRAPPER - you can use the XP/98/2000 driver all of them should work, it might even be worth trialling them and seeing which one works the best.  It sounds to me like you're right on the edge of it working....  If you can, drop to a terminal and type iwlist wlan0 scanning and post the output... (You'll need to be in the vicinity of the wireless network of courese lol)

i used the driver that came on my xp disc...okay so when i did the scan thing i reembered that last time i tried to get thi to work (this is my second time installing it) it was using 'eth1' so that's what i used...

ron@ron-laptop:~$ iwlist wlan0 scanning
wlan0     Interface doesn't support scanning.

ron@ron-laptop:~$ iwlist eth1 scanning
eth1      Scan completed :
          Cell 01 - Address: 00:0F:66:37:FB:5D
                    ESSID:"Home"
                    Protocol:IEEE 802.11g
                    Mode:Managed
                    Frequency:2.437 GHz (Channel 6)
                    Quality:9/100  Signal level:-90 dBm  Noise level:-96 dBm
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
                              12 Mb/s; 48 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0

---

### Post by Angelbeast on 2007-05-02
hey would it matter that i installed the 64 bit version? i can't seem to install flash player either...says it doesn't work with 64 bit ...

---

### Post by Fitzy_oz on 2007-05-02
> **Angelbeast said:**
> hey would it matter that i installed the 64 bit version? i can't seem to install flash player either...says it doesn't work with 64 bit ...

Are you using the the 64bit version of Feisty or 32bit - Pretty sure you have to use 64 if you're using 64bit but I could be mistaken

---

### Post by Angelbeast on 2007-05-02
> **Fitzy_oz said:**
> Are you using the the 64bit version of Feisty or 32bit - Pretty sure you have to use 64 if you're using 64bit but I could be mistaken

i have the 64 bit one...my cpu is a AMD Turion64

doe that mean i can't use adobe flash for firefox? *LOL* .. i could live without that once the wireless works

---

### Post by Fitzy_oz on 2007-05-02
> **Angelbeast said:**
> i have the 64 bit one...my cpu is a AMD Turion64

doe that mean i can't use adobe flash for firefox? *LOL* .. i could live without that once the wireless works

On that - The signal strength for you're network doesn't look great - 9/100.

---

### Post by Angelbeast on 2007-05-02
> **Fitzy_oz said:**
> On that - The signal strength for you're network doesn't look great - 9/100.

ah...i think i used to be able to connect to that one in windows...there's a it stronger one by my house though...i'll give that one a try...it's about time for me to go anywayi suppose...if it works i'll let you know and if not i'll be back on from my moms to try some more ideas *LOL*

---

### Post by Fitzy_oz on 2007-05-02
> **Angelbeast said:**
> ah...i think i used to be able to connect to that one in windows...there's a it stronger one by my house though...i'll give that one a try...it's about time for me to go anywayi suppose...if it works i'll let you know and if not i'll be back on from my moms to try some more ideas *LOL*

No Problem.  Good Luck

---

### Post by Angelbeast on 2007-05-02
okay it looks like the operation was a success...now i've discovered another matter...i had movie and music files on a seperate storage drive on windows...now linux is telling me i'm not the owner and won't let me add anything to the drive or edit files or delete anything...is there any way to fix that?

---

### Post by Fitzy_oz on 2007-05-02
> **Angelbeast said:**
> okay it looks like the operation was a success...now i've discovered another matter...i had movie and music files on a seperate storage drive on windows...now linux is telling me i'm not the owner and won't let me add anything to the drive or edit files or delete anything...is there any way to fix that?

NTFS - You'll need to install read write support for NTFS which is still a work in progress, it is considered beta and not to be trusted with mission critical data (which for me is all of my music and videos LOL), I have used it and it works fine but you're probably better off copying it off that drive and reformatting it to EXT3 that way you can maintain better control and it's a bit safer than using a well but incomplete implementation of another OS's filesystem. 

Should be able to just do a search for ntfs-3g in the forums and it should yield a lovely tutorial for you to install the necessary packages and get it going.

---

### Post by Angelbeast on 2007-05-02
> **Fitzy_oz said:**
> NTFS - You'll need to install read write support for NTFS which is still a work in progress, it is considered beta and not to be trusted with mission critical data (which for me is all of my music and videos LOL), I have used it and it works fine but you're probably better off copying it off that drive and reformatting it to EXT3 that way you can maintain better control and it's a bit safer than using a well but incomplete implementation of another OS's filesystem. 

Should be able to just do a search for ntfs-3g in the forums and it should yield a lovely tutorial for you to install the necessary packages and get it going.

eh i think i'd rather just do the reformat if it's safer and better ince i don't need my windows backups anymore it' just gonna be movies, music and 15 year of family pics *LOL*

---

### Post by Angelbeast on 2007-05-03
okay i have the files copied...now another newbie question...how do i format the drive? *LOL*

---

### Post by Fitzy_oz on 2007-05-03
> **Angelbeast said:**
> okay i have the files copied...now another newbie question...how do i format the drive? *LOL*

Goto add remove applications and add a program called gparted, it has an intuitive interface much like that of Partition Magic or Disk Manager for windows.  Simply unmount the drive, format it to EXT3.

Goto the places menu and select computer - It should show the volume there but it won't be mounted.  Double click it and the computer should mount it for you.  Now this is where the irritating part for me is as I have yet to find a normal way of doing this (but to be fair I haven't looked...), drop to the terminal and type sudo nautilus and you will be greeted with a nautilus file browser window but it will be for the root user - BE CAREFUL, the root user is the super user and you can do damage with this account if you delete things that you shouldn't (same as the windows admin account).  Navigate to the media folder and oyu should see the folder in which you're volume has been mounted, open it and and right click and select properties - Change all of the permissions to you're user name and presto - Read write is yours.

---

### Post by Angelbeast on 2007-05-03
> **Fitzy_oz said:**
> Goto add remove applications and add a program called gparted, it has an intuitive interface much like that of Partition Magic or Disk Manager for windows.  Simply unmount the drive, format it to EXT3.

Goto the places menu and select computer - It should show the volume there but it won't be mounted.  Double click it and the computer should mount it for you.  Now this is where the irritating part for me is as I have yet to find a normal way of doing this (but to be fair I haven't looked...), drop to the terminal and type sudo nautilus and you will be greeted with a nautilus file browser window but it will be for the root user - BE CAREFUL, the root user is the super user and you can do damage with this account if you delete things that you shouldn't (same as the windows admin account).  Navigate to the media folder and oyu should see the folder in which you're volume has been mounted, open it and and right click and select properties - Change all of the permissions to you're user name and presto - Read write is yours.

ahhhh...okay do i need to reboot for it to take effect? and if i get rid ofthe lost and found folder will that cause problems?

---

### Post by Fitzy_oz on 2007-05-03
> **Angelbeast said:**
> ahhhh...okay do i need to reboot for it to take effect? and if i get rid ofthe lost and found folder will that cause problems?

Shouldn't and you shoudn't need to reboot.

---

### Post by Angelbeast on 2007-05-03
> **Fitzy_oz said:**
> Shouldn't and you shoudn't need to reboot.

well...dammit...it's still saying i don't hv permission

---

### Post by Fitzy_oz on 2007-05-05
> **Angelbeast said:**
> well...dammit...it's still saying i don't hv permission

Try the following,
In the terminal type gksudo /etc/fstab

This will bring up you're startup drive mounts - This is what mine looks like

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hdb1
UUID=07cf3efd-df84-41fe-aa21-eb1b5056153d /               ext3    defaults,errors=remount-ro 0       1
# /dev/hdb5
UUID=a3c7e2b3-ec1f-4580-942e-00efaf79332a none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hda1	/home		ext3		defaults
[COLOR="Red"]/dev/hdd1	/media/disk	ext3		defaults[/COLOR]

The line in red is the line I added for my reformatted drive - You just need to know which drive it is on the controller - ie: hdd1 is second HDD controller slave drive partition 1.

Provided you've set the permissions correctly on the drive as I mentioned above this drive will mount on it's own at boot with the correct permissions.

I had at the screenshot in you're other post - It looks like you're permissions are correct.  I didn't realize you were a Megadeth Fan, whats the new album like?

---

### Post by Angelbeast on 2007-05-05
> **Fitzy_oz said:**
> Try the following,
In the terminal type gksudo /etc/fstab

This will bring up you're startup drive mounts - This is what mine looks like

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hdb1
UUID=07cf3efd-df84-41fe-aa21-eb1b5056153d /               ext3    defaults,errors=remount-ro 0       1
# /dev/hdb5
UUID=a3c7e2b3-ec1f-4580-942e-00efaf79332a none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hda1	/home		ext3		defaults
[COLOR="Red"]/dev/hdd1	/media/disk	ext3		defaults[/COLOR]

The line in red is the line I added for my reformatted drive - You just need to know which drive it is on the controller - ie: hdd1 is second HDD controller slave drive partition 1.

Provided you've set the permissions correctly on the drive as I mentioned above this drive will mount on it's own at boot with the correct permissions.

I had at the screenshot in you're other post - It looks like you're permissions are correct.  I didn't realize you were a Megadeth Fan, whats the new album like?

i got the permissions worked out too...i just need to know how to make the drive mount on it's own when i reboot...

---

### Post by Fitzy_oz on 2007-05-05
> **Angelbeast said:**
> i got the permissions worked out too...i just need to know how to make the drive mount on it's own when i reboot...

Sweet, then just add the line in red to the fstab file, of course you'll need to add you're hard drive details in there, not mine but thats pretty much it, the auto-mounting is controlled by that file.

---

### Post by Angelbeast on 2007-05-05
okay so this is the part that's confusing for me... if this i my fstab file

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda1
UUID=de70cf45-29aa-436e-8e8a-31ae633c3a14 /               ext3    defaults,errors=remount-ro 0       1
# /dev/hda5
UUID=ab7ac934-f156-4c18-b8a1-f525c7a09578 none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0


then directly under the last line i would add:

/dev/hdb1 /media/hdb1 ext3 defaults

ia that right?

---

### Post by Fitzy_oz on 2007-05-06
> **Angelbeast said:**
> okay so this is the part that's confusing for me... if this i my fstab file

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda1
UUID=de70cf45-29aa-436e-8e8a-31ae633c3a14 /               ext3    defaults,errors=remount-ro 0       1
# /dev/hda5
UUID=ab7ac934-f156-4c18-b8a1-f525c7a09578 none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0


then directly under the last line i would add:

/dev/hdb1 /media/hdb1 ext3 defaults

ia that right?

Correct - But Make sure the directory you're mounting to exists, it doesn't have to be hdb1, you could create a directory like /media/disk2 and then the line would be:

/dev/hdb1 /media/disk2 ext3 defaults

---

### Post by Angelbeast on 2007-05-06
> **Fitzy_oz said:**
> Correct - But Make sure the directory you're mounting to exists, it doesn't have to be hdb1, you could create a directory like /media/disk2 and then the line would be:

/dev/hdb1 /media/disk2 ext3 defaults

it shows up in places ad 'disc' but in partition editor the partition is named hdb1

so if i can call it dic does that mean i could name it anything that way? say like 


/dev/hdb1 /media/storage ext3 defaults

??

---

### Post by Fitzy_oz on 2007-05-06
yep, thats what it means

---

### Post by Angelbeast on 2007-05-07
> **Fitzy_oz said:**
> yep, thats what it means

well cool...this is becoming less confusing now...another question...i noticed that when i putin a cd that it mounts the drive when i putin a cd and unmounts it whe ni take itout...the hard drive mountswhen i click on it...can i just leave them like that? long as i can get to what's on them i don't need to mess with it even if they mount nd unmount each time...

---

### Post by jargoman on 2007-05-07
I have a broadcom card sabayon works out the box. 

ubuntu will work though I'm using it right now with ndiswrapper.

I recommend ndiswrapper for greater range (a little finicky sometimes though)

if you want an easy fix

$ sudo apt-get update
$ sudo apt-get install bcm43xx-fwcutter

once installed a screen will pop up asking "do you want to download firmware"
click yes and that's it.

or if you want I'll tell you how to get ndiswrapper working. I'm using this second

---

