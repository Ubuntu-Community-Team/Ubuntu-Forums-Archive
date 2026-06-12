---
title: "Problems with iSight webcam on 10.04 Lucid  (MBP 5,3)"
date: 2010-05-04
forum: Apple Hardware Users
---

### Post by proycon on 2010-05-04
I'm having a strange issue with my built-in iSight webcam, on a Macbook Pro 5,3. I recently upgraded to 10.04, but I could swear I saw it working in 10.04 as well. 

It all worked fairly well in 9.10, only on some occassions it seemed the webcam wasn't detected properly, a reboot usually fixed it.  But now it seem it's continuously not detected. I get no /dev/video0, and thus no applications detect the webcam.

The boot log shows a 'No valid video chain found' error:

May  4 20:56:38 aurora kernel: [   18.202190] uvcvideo: Found UVC 1.00 device Built-in iSight (05ac:8507)
May  4 20:56:38 aurora kernel: [   18.202194] uvcvideo: No valid video chain found.
May  4 20:56:38 aurora kernel: [   18.202218] usbcore: registered new interface driver uvcvideo
May  4 20:56:38 aurora kernel: [   18.202329] USB Video Class driver (v0.1.0)

As far as I know, all relevant modules seem to be present in lsmod:

uvcvideo               62403  0 
v4l1_compat            15495  2 uvcvideo,videodev
v4l2_compat_ioctl32    12020  1 videodev
videodev               40486  1 uvcvideo

I attached also a more verbose log of modprobe uvcvideo trace=15 .
The cam works fine in Mac OS X, and worked decently before my upgrade as well.

What am I missing? Does anybody have the same issue? And more importantly, does someone have a solution?

---

### Post by proycon on 2010-05-04
I found a post on RedHat's bugzilla with the same problem ( [https://bugzilla.redhat.com/show_bug.cgi?id=572648](https://bugzilla.redhat.com/show_bug.cgi?id=572648) ), and this guy fixed it by changing something in SElinux. I don't have SELinux installed, nor do I understand what it has to do with it, but it may perhaps provide some clues for someone?

---

### Post by proycon on 2010-05-04
I found a bug report that matches my problem: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/544469](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/544469)  

However, no solution yet.

---

### Post by Mmmm on 2010-05-12
I can confirm that the isight camera no longer works on my MBP 5,2 after upgrading to 10.04.  I tried installing the isight-firmware-tools package but it doesn't help.  I do have /dev/video0. Running gstreamer-properties shows "Built-in iSight" as an option for Device under the "Video for Linux 2 (v4|2)" plugin, but clicking the Test button gives:

> libv4l2: error turning on stream: Input/output error
gstreamer-properties-Message: Error running pipeline 'Video for Linux 2 (v4l2)': Error starting streaming on device '/dev/video0'. [gstv4l2object.c(1952): gst_v4l2_object_start_streaming (): /GstPipeline: pipeline0/GstV4l2Src:v4l2src1:
system error: Input/output error]

in the console window.  Any thoughts?

---

### Post by jord99 on 2010-05-16
Just installed latest ubuntu, had a quick look for a solution to isight but non as yet. Will try and get one over the next couple of days and post back with what happens. Very annoying:guitar:

---

### Post by buntuLo on 2010-05-16
just to report that i rapidly checked it on MacBookPro 5,1.
the iSight does work running a kubuntu-10.04-desktop-i386 livecd and the default instant messenger, kopete.

---

### Post by KilianValkhof on 2010-05-17
I am on a macbook 5,5 with 10.04 and receive the OP's error as well.

---

### Post by Ravernomina on 2010-05-18
I got mine to work by doing this. Lucid has a lot of Trouble Trying to control USB Powered Devices. What i did was unplug all USB Devices on my MacBook Pro 5,4, Then it was able to run the iSight camera Fine. Try that.

---

### Post by jord99 on 2010-05-20
Afraid to say I've had no luck. Although I have a macbook 3.5, but still, should be a similar fix. I just want to use skype on it. Is anyone else having problems with the mic?

---

### Post by Shutter4U on 2010-05-22
I was having a problem getting it to work in Lucid (on my macbook 4,1), but then I tried the following and it works now:

```
sudo modprobe -r uvcvideo
sudo modprobe uvcvideo

```

Cheese acts a little weird though, video goes to black unless I move the window around - but skype finds the webcam which it didn't before.:)

---

### Post by paulinchen on 2010-05-22
It worked again last week, but stopped working yesterday. Tried install /uninstall isight firmware, doesn't work. 
Camera gets recognized, but neither Skype nor cheese can't get them started. The green light of the camera stays dark ...
f***

---

### Post by Shutter4U on 2010-05-22
> **Shutter4U said:**
> I was having a problem getting it to work in Lucid (on my macbook 4,1), but then I tried the following and it works now:

```
sudo modprobe -r uvcvideo
sudo modprobe uvcvideo

```

Cheese acts a little weird though, video goes to black unless I move the window around - but skype finds the webcam which it didn't before.:)

:redface: d'oh! sorry, after a reboot I found it wasn't working again. I tried the above reload of uvcvideo and that *didn't* work. Before I did that the first time, I had reinstalled the firmware using ift-extract from the isight-firmware-tools package to extract isight.fw from the AppleUSBVideoSupport file using the following command:

```
sudo ift-extract -a AppleUSBVideoSupport
```

That is with AppleUSBVideoSupport in my home folder, but it will work in whatever folder its in (if it works at all - sometimes the AppleUSBVideoSupport won't work :roll:)

Anyway, it seems that is what got it working again. Might need to be done after every reboot (or whenever I want to use the webcam, at least).:mad:

---

### Post by paulinchen on 2010-05-24
I copied the AppleUSBVideoSupport file to /lib/firmware and extracted it via 

```
 sudo ift-extract -a /lib/firmware/AppleUSBVideoSuppor
```after a shutdown and reboot the camera works again.


Maybe the problem is that the isight.fw is not in its right place ... Can anyone check?

---

### Post by WindPower on 2010-05-24
I have exactly the same problem (and same dmesg output) on Kubuntu 10.04 64-bit on Macbook Pro 5.3. I have tried paulinchen's suggestion without success; ift-extract moves isight.fw to /lib/firmware anyway.
I can get the camera working by booting into OS X, starting Photo booth to get OS X to load the firmware, then reboot (not poweroff) in Kubuntu, but it obviously lasts only until the next poweroff and is very annoying.

---

### Post by jmoney on 2010-05-29
> **paulinchen said:**
> I copied the AppleUSBVideoSupport file to /lib/firmware and extracted it via 

```
 sudo ift-extract -a /lib/firmware/AppleUSBVideoSuppor
```after a shutdown and reboot the camera works again.


Maybe the problem is that the isight.fw is not in its right place ... Can anyone check?

extract of firmware followed by reboot didn't help. Is full shutdown necessary?

---

### Post by paulinchen on 2010-05-29
Yes a complete shutdown is required to set the new driver correctly.

But this solution didn't last long, my camera again doesn't work since two days. I tried everything. Install and -purge remove the isight-firmware tools, reset the batterystats, reboot after get the camera started in osx.

Didn't help...

It makes me really pissed that it STOPPED working, so just want to reset everything to these glory days in the past, where this little camera works OUT-OF-THE-BOX.

Can anyone make this happen????? Please

---

### Post by EvCrock on 2010-06-14
Has anyone fixed this yet?  I've tried this solution and dozens of other on the internet, and none have worked.

This one seemed to work for people in the comments, can anyone help me with the specifics of the command line?  I'm one week old at Ubuntu.  [http://handyfloss.net/2008.07/making-isight-camera-work-in-ubuntu/](http://handyfloss.net/2008.07/making-isight-camera-work-in-ubuntu/)

---

### Post by WindPower on 2010-06-14
> **EvCrock said:**
> Has anyone fixed this yet?  I've tried this solution and dozens of other on the internet, and none have worked.

This one seemed to work for people in the comments, can anyone help me with the specifics of the command line?  I'm one week old at Ubuntu.  [http://handyfloss.net/2008.07/making-isight-camera-work-in-ubuntu/](http://handyfloss.net/2008.07/making-isight-camera-work-in-ubuntu/)

I have not been able to fix it. The article you linked to is the same "solution" as one of those mentioned previously: extracting the video firmware from OS X's files, which worked for previous versions of Ubuntu but not Lucid.

I guess we'll have to wait for 10.10 and hope the bug is fixed then.

---

### Post by euph on 2010-06-24
EDIT: After rebooting back in, I don't seem to be able to get /dev/video0 to appear anymore. How odd. Just get the "No valid video chain" message again from uvcvideo.

Feel free to disregard my original post below.


[FONT="Courier New"][SIZE="2"][I]So I'm having this issue as well

In order to get the firmware loading correctly I had to download and compile the latest version of isight-firmware-tools, from here: (I downloaded 1.5.93)

[https://launchpad.net/isight-firmware-tools/+download]("https://launchpad.net/isight-firmware-tools/+download")

After extracting the firmware as usual using the newly compiled ift-extract (in ./src/ I think) and getting the firmware loaded (shutdown, restart hal, whatever you like to do) I was able to get the camera started using guvcview

```
sudo apt-get install guvcview
```

But only at a resolution less than 640x480. This was the same in Cheese, I would get a stream IO error if I tried with that resolution.

I get the same error from gstreamer-properties when trying to test the device. But since I don't know how to set the resolution in gstreamer properties, I cant use the camera in pidgin, for gtalk video :-(

I'll post the error later, I'm in OSX at the moment (so I can use the camera!).

Cheers,
euph[/I][/SIZE][/FONT]

---

### Post by somerville31 on 2010-06-24
I just started using ubuntu and I'm happy (?) to see that I'm not the only one having this problem. I've tried everything that's been posted to date. Can anyone find a way to make it work. I'm using MBP 2.1, but I haven't heard of anyone having any luck with any version.
 
One recommendation I found was booting into mac osx and manually booting the driver from there, then moving back into ubuntu. I don't have my install CD handy, but it might be worth a shot.

---

### Post by drkitty on 2010-07-16
After beating my head against the wall ](*,)for the last few days on this problem I actually think I've got the solution. It works even after a reboot:D

(1) Extract the isight driver and use ift-extract-firmware tools. See [this]("http://ubuntuforums.org/showthread.php?t=1259166") and [this]("http://ubuntu-tutorials.com/2008/11/03/enable-apple-isight-camera-ubuntu-810/") for more info about installing and using the tool.
If you get an error like "no valid driver found" you'll need to find an older AppleUSBVideoSupport.

(2) In the /etc/default/acpi-support file, find MODULES and make it MODULES="isight_usb"

(3) Modify the file: /etc/udev/rules.d/isight.rules to be:
ACTION=="add", SYSFS{idVendor}=="05ac", SYSFS{idProduct}=="8507", RUN+="/usr/lib/udev/ift-load --firmware /lib/firmware/isight.fw"

Step 1 sets up the isight driver. Step 2 seems to fix the /dev/video0 problem. Step 3 changes the Product ID to 8507 from the default 8300 which is incorrect. Skype, cheese, and gstreamer-properties can now find the camera.

---

### Post by WindPower on 2010-07-20
> **drkitty said:**
> After beating my head against the wall ](*,)for the last few days on this problem I actually think I've got the solution. It works even after a reboot:D

(1) Extract the isight driver and use ift-extract-firmware tools. See [this]("http://ubuntuforums.org/showthread.php?t=1259166") and [this]("http://ubuntu-tutorials.com/2008/11/03/enable-apple-isight-camera-ubuntu-810/") for more info about installing and using the tool.
If you get an error like "no valid driver found" you'll need to find an older AppleUSBVideoSupport.

(2) In the /etc/default/acpi-support file, find MODULES and make it MODULES="isight_usb"

(3) Modify the file: /etc/udev/rules.d/isight.rules to be:
ACTION=="add", SYSFS{idVendor}=="05ac", SYSFS{idProduct}=="8507", RUN+="/usr/lib/udev/ift-load --firmware /lib/firmware/isight.fw"

Step 1 sets up the isight driver. Step 2 seems to fix the /dev/video0 problem. Step 3 changes the Product ID to 8507 from the default 8300 which is incorrect. Skype, cheese, and gstreamer-properties can now find the camera.
I assume you need to put the extracted firmware at /lib/firmware/isight.fw. I did that and then followed your instructions, rebooted, but no webcam.

---

### Post by gstlouis on 2010-07-24
> **drkitty said:**
> After beating my head against the wall ](*,)for the last few days on this problem I actually think I've got the solution. It works even after a reboot:D

(1) Extract the isight driver and use ift-extract-firmware tools. See [this]("http://ubuntuforums.org/showthread.php?t=1259166") and [this]("http://ubuntu-tutorials.com/2008/11/03/enable-apple-isight-camera-ubuntu-810/") for more info about installing and using the tool.
If you get an error like "no valid driver found" you'll need to find an older AppleUSBVideoSupport.

(2) In the /etc/default/acpi-support file, find MODULES and make it MODULES="isight_usb"

(3) Modify the file: /etc/udev/rules.d/isight.rules to be:
ACTION=="add", SYSFS{idVendor}=="05ac", SYSFS{idProduct}=="8507", RUN+="/usr/lib/udev/ift-load --firmware /lib/firmware/isight.fw"

Step 1 sets up the isight driver. Step 2 seems to fix the /dev/video0 problem. Step 3 changes the Product ID to 8507 from the default 8300 which is incorrect. Skype, cheese, and gstreamer-properties can now find the camera.

I can confirm that (at least for me) this seems to have resolved the issue (5.5 MBP). Note that I've got a brand new install of 10.04 and I downloaded the latest source from the isight-firmware-tools website (the version on aptitude seems broken as it wouldn't recognize my firmware file). After building the downloaded source and installing the fw file in /lib/firmware, I followed the steps above, rebooted, and I've got working 640X480 resolution in cheese and Skype. Let's hope that it stays this way.

---

### Post by faust99 on 2010-08-04
These [instructions ]("https://help.ubuntu.com/community/MactelSupportTeam/AppleiSight?action=show&redirect=AppleiSight") worked for me.

---

### Post by gast0r on 2010-08-16
None of the above solutions have worked on my Macbook Pro 5.3. Anyone else managed to make any progress with this?

---

### Post by jamiewan on 2010-08-23
hi, i had same issues with webcam exactly as mentiond in these threads, my solution worked for me and that was re updated the cheese dependencies and away it goes, hope that helps

---

### Post by shea.dan on 2010-09-29
Not sure about the extraction part. I extract the AppleUSBVideoSupport using ift-extract and then I test out the ift-load:

```
$ sudo /usr/lib/udev/ift-load --firmware /lib/firmware/isight.fw 
ift-load: USB device 0x05AC:0x8300 not found
ift-load: No iSight found
```

It's looking for a device with a product ID of 8300... interesting because: 

```
$ lsusb -d 05ac:
Bus 004 Device 003: ID 05ac:8213 Apple, Inc. 
Bus 003 Device 003: ID 05ac:0236 Apple, Inc. 
Bus 003 Device 002: ID 05ac:8242 Apple, Inc. 
Bus 002 Device 003: ID 05ac:8403 Apple, Inc. 
**Bus 001 Device 002: ID 05ac:8507 Apple, Inc.** 
```

The bolded is (I believe according to above posts) the isight.

Anybody know how to fix this error? The isight firmware isn't associating itself with the camera.

---

### Post by gast0r on 2010-09-29
I get the same ift-load output. Maybe this only requires the editing of a script to direct it towards the correct device ID.

---

### Post by rmcellig on 2010-10-02
I am so frusterated as are some of you that getting the little isight camera in my iMac is a real pain!! I even installed 10.10 to no avail as far as the isight is concerned. There has to be a way around this. Here we are in 2010 still trying to figure out things that should just work plain and simple.

---

### Post by gast0r on 2010-10-02
I should probably point out that my iSight seems to work out of the box perfectly well after doing a fresh install of the Maverick RC.

---

### Post by rmcellig on 2010-10-02
Thanks gastOr!

So you are saying that I should delete my Ubuntu partition on my iMac and do a clean install of 10.10? You had no configuring to do or anything like that?

On a seperate note I would like to ask you about something else I am having problems with regarding Sound Preferences/Input/Line-In. I can't record anything from my Line In. No problem recording from the built in mic on the iMac. I have a radio attached to my Mac. Works fine in my Mac partition but not in Ubuntu. All I get is white noise if I try to record from Line-In. Are you able to try it out and see if it works for you? This is the main thing I need to get going in Ubuntu dual boot.

Thanks!!

---

### Post by gast0r on 2010-10-02
> **rmcellig said:**
> Thanks gastOr!

So you are saying that I should delete my Ubuntu partition on my iMac and do a clean install of 10.10? You had no configuring to do or anything like that?

On a seperate note I would like to ask you about something else I am having problems with regarding Sound Preferences/Input/Line-In. I can't record anything from my Line In. No problem recording from the built in mic on the iMac. I have a radio attached to my Mac. Works fine in my Mac partition but not in Ubuntu. All I get is white noise if I try to record from Line-In. Are you able to try it out and see if it works for you? This is the main thing I need to get going in Ubuntu dual boot.

Thanks!!

Well I'm running a 5.3 Macbook Pro, so I can't say it'll work for sure. But if you have little to loose, I'd definitely give it a try. About the Line-in; I wasn't able to record either until I installed Gnome ALSA Mixer (you'll find that in the repositories). From there you un-mute the mic, tic record, and turn it's volume up full.

Good luck.

---

### Post by rmcellig on 2010-10-02
Thanks. I am running Ubuntu dual partition because I would rather stay in the Ubuntu environment than OS 10.6.4. Go figure. I have been using Macs since 1988 and have always loved using them. Now that I discovered Ubuntu and all it has to offer, I really like using it!

I did the Alsa mixer thing and all levels were already up or unmuted. Very frustrating. When I run Ubuntu through VMware fusion, I have no problems at all. When I run Ubuntu dual boot, there are issues. The main ones I have are the isight camera and recording from Line-In. I noticed that while running Ubuntu in VMware fusion, the driver listed was different that the one listed when using Ubuntu dual boot. I wonder if there is a way to have the driver from Ubuntu (VMware Fusion) listed in Ubuntu dual boot?

Right now I am just testing Ubuntu dual boot so I have no problem starting over. Do I only have to delete the Ubuntu partition and then reinstall 10.10 in the unalocated Space when using the Ubuntu installer?

---

### Post by gast0r on 2010-10-02
Sorry to hear that was of no help. And yeah, fresh install.

---

### Post by rmcellig on 2010-10-02
Thanks!

Another option although not too elegant is to just buy a USB webcam and put it on top of my iMac so that I can use that when in the Ubuntu partition. Thoughts? If so, which make model would work in Ubuntu?

---

### Post by gast0r on 2010-10-02
I honestly couldn't bring myself to do that. The fact that I already have a perfectly good one built-in would drive me insane and I'd spend ages trying to fix it, or just not have the feature:P But if you must, I'd suggest a Logitech camera, as there hardware tends to run well with Ubuntu. Although I'm not sure a model, just Google for it.

---

### Post by rmcellig on 2010-10-02
I fully agree with you but I have spent the past few days trying to get something to work that should really just work, even if there was some kind of driver to insstall, I could live with that, but I don't think that is the case.

---

### Post by gast0r on 2010-10-03
Ok, camera is no longer working...

---

### Post by rmcellig on 2010-10-03
No Never got it to work on the iMac in dual boot with Ubuntu 10.04 and a clean install of 10.10. I knw there is an isight tools utility that I can instal that points to the iMac camera driver. I can't use that driver because I have 10.6 installed on my Mac and I can only use the driver prior to 10.6.

---

### Post by gast0r on 2010-10-04
> **rmcellig said:**
> No Never got it to work on the iMac in dual boot with Ubuntu 10.04 and a clean install of 10.10. I knw there is an isight tools utility that I can instal that points to the iMac camera driver. I can't use that driver because I have 10.6 installed on my Mac and I can only use the driver prior to 10.6.
  
You can always download the firmware. just google it. I'd help you out but for legal reasons you can't really post things like that.

---

### Post by rmcellig on 2010-10-04
Thanks. How would I know I am downloading the right file? I understand that the one included with 10.6 doesn't work. Now, I have an OS 10.5 installer CD. Maybe it's on there?

---

### Post by rmcellig on 2010-10-04
I just realized that I have OS 10.5.8 on my G4 so I managed to get the file from there.

---

### Post by rmcellig on 2010-10-04
Just installed the driver. Does this mean that it is installed correctly:

randy@randy-iMac:~$ ls /lib/firmware/isight.fw
/lib/firmware/isight.fw

---

### Post by linuxopjemac on 2010-10-04
looks good.

---

### Post by gast0r on 2010-10-04
I should now mention that yet again, iSight seems to be working. Very, very strange. Hopefully it'll not have any problems by 10.10's full release.

---

### Post by faust99 on 2010-10-17
THe problem is intermittent in my case. Not sure what the cause is...:confused:

---

### Post by vibe3 on 2011-02-19
I've been having similar problems. The only thing that fixed it (so far), was downloading the latest isight-firmware-tools (1.5.93) from [https://launchpad.net/isight-firmware-tools/](https://launchpad.net/isight-firmware-tools/). Then do:

> grep -r 8300 *

in the src directory. Change all instances of 8300 to: 8507 (this is the correct address for my isight). There is mainly a .h file and the isight-rules.in.in file to change.

Compile/install the code (you need to install some additional things like libusb-dev).

Shutdown and restart. My isight is now working

---

