---
title: "Newbie, Need help...."
date: 2006-08-02
forum: Absolute Beginner Talk
---

### Post by zhenyu21 on 2006-08-02
I'm currently trying out the 6.06 release with the LiveCD, can't install it as of yet cause i'm waiting for my harddrive to arrive.
Have a couple of questions
1) It is unable to give me the native resolution on my widescreen laptop (1280x800) will it be solved if i installed it?
2) When 6.10(the release due in october) comes out, do i have to reinstall the whole thing? Or can i do a System Upgrade( like windows?)

Thanks in advance.

---

### Post by nalmeth on 2006-08-02
> **zhenyu21 said:**
> I'm currently trying out the 6.06 release with the LiveCD, can't install it as of yet cause i'm waiting for my harddrive to arrive.
Have a couple of questions
1) It is unable to give me the native resolution on my widescreen laptop (1280x800) will it be solved if i installed it?
2) When 6.10(the release due in october) comes out, do i have to reinstall the whole thing? Or can i do a System Upgrade( like windows?)

Thanks in advance.
1. Yes, likely so. What kind of video card do you have anyway? Should be a relatively easy fix. 
2. System Upgrade

---

### Post by zhenyu21 on 2006-08-02
> **nalmeth said:**
> 1. Yes, likely so. What kind of video card do you have anyway? Should be a relatively easy fix. 
2. System Upgrade

Err... I have an intel gfx, does that mean i have to edit some stuff?

---

### Post by Tomosaur on 2006-08-02
You should be fine, I had an integrated intel gfx board on my laptop and it ran Ubuntu fine.

---

### Post by darrenm on 2006-08-02
> **zhenyu21 said:**
> Err... I have an intel gfx, does that mean i have to edit some stuff?

Likely have to edit the xorg.conf file but its very easy.

Also when has Windows ever been able to do a system upgrade? ;)

When Edgy (6.10) comes out you can just change your repositories and watch as it tells you lots of updates are waiting :)

---

### Post by zhenyu21 on 2006-08-02
can i edit that for my LiveCD session?
can you outline what i have to change in the xorg.conf file?

---

### Post by darrenm on 2006-08-02
> **zhenyu21 said:**
> can i edit that for my LiveCD session?
can you outline what i have to change in the xorg.conf file?

Yes once inside the operating system, just edit /etc/X11/xorg.conf and change the part where you have the resolutions listed e.g:
```
Section "Screen"
        Identifier      "Default Screen"
        Device          "ATI Technologies, Inc. RV350 AR [Radeon 9600 XT]"
        Monitor         "C1770NSL/NST"
        DefaultDepth    24
        SubSection "Display"
                Depth           1
                Modes           "1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           4
                Modes           "1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           8
                Modes           "1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           15
                Modes           "1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           16
                Modes           "1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           24
                Modes           "1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
        EndSubSection
EndSection

```
Change the first resolution for the default depth (normally 24) to what you want and as long as the driver will support it then X will run it.

---

### Post by zhenyu21 on 2006-08-02
Cool. Thanks.
I have some more questions though, after reading through the forums. 
I have gotten a bit scared of installing ubuntu on top of my windows. 
If i want to dual boot, do i want to manually set up my partition table (in the install wizard)(I think its option 3) or let ubuntu do it by its own(option 1)?
Although i know this question can't be answered correctly, but do I need a swap partition? (is it just for swapping ordinary files?, and in that case, is it FAT32?)

Then again, is it simply easier to create partitions before even my windows installation?

---

### Post by nalmeth on 2006-08-02
> **zhenyu21 said:**
> Cool. Thanks.
I have some more questions though, after reading through the forums. 
I have gotten a bit scared of installing ubuntu on top of my windows. 
If i want to dual boot, do i want to manually set up my partition table (in the install wizard)(I think its option 3) or let ubuntu do it by its own(option 1)?
Although i know this question can't be answered correctly, but do I need a swap partition? (is it just for swapping ordinary files?, and in that case, is it FAT32?)

Then again, is it simply easier to create partitions before even my windows installation?
If you don't really know what you're doing, you should let it do it on its own. Make sure it knows it's shrinking your windows. Alternatively you can use your own partitioning tool to shink windows, then let ubuntu install in the largest continuous unused space.

But first, BACKUP your data. Just in case something goes wrong.

You really should have a swap file. If you have a gig or more of RAM it won't really be that important, but you should always have at least 512 meg swap file.

---

### Post by zhenyu21 on 2006-08-03
very werid... i just looked at my xorg.conf file and all my modes are listed as 1280x800(which is the correct resolution for my laptop) but i can only select 1024x768, 800x600, and smaller resolution. I can't get the internet working (wireless) though, so i can't post my .conf file here

---

### Post by rck_hitokiri on 2006-08-03
do it like this and see if its much easier for you....

sudo dpkg-reconfigure xserver-zorg
(on the screen you can pretty much accept until you arrive to your monitor and its resolution, i assume your on a lower resolution)

now use the space bar to remove the option 640x480 and put it to your desired resolution. try it.

___________________________________________________________________

---

### Post by raspberryh on 2006-08-03
I'm having the same problem. I did that and I got this:
> heather@alien-lifeform:~$ sudo dpkg-reconfigure xserver-zorg
Package `xserver-zorg' is not installed and no info is available.
Use dpkg --info (= dpkg-deb --info) to examine archive files,
and dpkg --contents (= dpkg-deb --contents) to list their contents.
/usr/sbin/dpkg-reconfigure: xserver-zorg is not installed

](*,)

---

### Post by darrenm on 2006-08-03
means the driver for onboard VGA wont support that resolution (i think!)

If you set your xorg.conf to only 640x480 then will it only select 640x480?

Also are you sure you're looking at the correct colour depth? Change the first one to 1280x800 for all of them.

---

### Post by raspberryh on 2006-08-03
For me, in the xorg.conf file, they are already all set to 1280x800.

---

### Post by zhenyu21 on 2006-08-04
oh ok thanks people, will try it out

---

### Post by darrenm on 2006-08-04
> **raspberryh said:**
> I'm having the same problem. I did that and I got this:

](*,)

(Its sudo dpkg-reconfigure xserver-xorg not xserver-zorg ;) )

---

### Post by raspberryh on 2006-08-04
Okay did that, didn't work. :-x

---

### Post by darrenm on 2006-08-05
> **raspberryh said:**
> Okay did that, didn't work. :-x

What driver are you using and which chipset do you have?

check in /etc/X11/xorg.conf for the line Driver inside section Device

---

### Post by raspberryh on 2006-08-05
> **darrenm said:**
> What driver are you using and which chipset do you have?

check in /etc/X11/xorg.conf for the line Driver inside section Device

This:

Section "Device"
        Identifier      "Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller"
        Driver          "i810"
        BusID           "PCI:0:2:0"
EndSection

---

### Post by darrenm on 2006-08-06
There seems to be a specific driver available for that VGA chip: [http://downloadfinder.intel.com/scripts-df-external/filter_results.aspx?strTypes=all&ProductID=1862&OSFullName=Linux*&lang=eng&strOSs=39&submit=Go%21](http://downloadfinder.intel.com/scripts-df-external/filter_results.aspx?strTypes=all&ProductID=1862&OSFullName=Linux*&lang=eng&strOSs=39&submit=Go%21) 
If you dont have any luck with the tar.gz file you can always use alien on the RPM. Although I think you would be best with the 2nd one down with the GART and DRM kernel modules.

---

### Post by raspberryh on 2006-08-06
Hey, thanks a lot!
Okay I used the second file but it only gave me the extra options of 800x600 and 640x480. I couldn't figure out how to use the first one. The last one though - well I installed alien and I used it on the rpm file.
But in [the readme]("http://downloadmirror.intel.com/df-support/8211/ENG/readme.txt"), it says after doing all that:
> 1. Run SuSE's own configurator called 'YAST' 
under System from SuSE application broswer menu
	a. Select the 'Hardware' icon
	b. Select the 'Graphics Card and Monitor' icon
	c. Select 'Grapihcs desktop environment'radio button
	d. Select 'Change'
	e. Under 'Desktop' select 'Graphics Card'
	f. Select 'Add new card'
	g. Under 'General' tab, select 'Intel' and then '915G'
	h. Accept all changes and exit 'YAST'
What the heck? SuSE's own configurator called 'YAST'? What the heck is that? I don't see it anywhere. What are they talking about??? Grrrr :(

---

### Post by darrenm on 2006-08-07
First, check the installed didnt change the driver in xorg.conf, if it is still i810 then run ```
sudo dpkg-reconfigure xserver-xorg
``` and when asked for the video card choose intel 915g.

---

### Post by raspberryh on 2006-08-07
Do you mean where it used to say "Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller" change it to "Intel 915G"?

---

### Post by darrenm on 2006-08-07
No, run the code below
```
sudo dpkg-reconfigure xserver-xorg
```
and choose intel 915g

---

### Post by raspberryh on 2006-08-07
I DID run that code, and where it said "Enter an identifier for your video card", it automatically said "Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller", so I changed it to "Intel 915G"

---

### Post by raspberryh on 2006-08-12
I GOT IT TO WORK!!!!
Check it out! I went to [How to Get Widescreen Resolution in Linux]("http://linuxmint.com/content/view/212/52/") and I did everything they said and now my resolution is perfect!!!!!
Woo-hoo :-)
Thanks for all your help.

---

