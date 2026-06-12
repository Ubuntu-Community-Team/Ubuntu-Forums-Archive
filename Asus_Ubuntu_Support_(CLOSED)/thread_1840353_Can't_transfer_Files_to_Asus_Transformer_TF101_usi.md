---
title: "Can't transfer Files to Asus Transformer TF101 using mtpfs"
date: 2011-09-07
forum: Asus Ubuntu Support (CLOSED)
---

### Post by BcRich on 2011-09-07
Hi
By following instructions [http://forum.xda-developers.com/archive/index.php/t-1077572.html](http://forum.xda-developers.com/archive/index.php/t-1077572.html) (Roach2010's post) I managed to get mtpfs working on ubuntu and connect my transformer tf101 tablet via usb such that i can see the contents of my tablet in nautilus (on maverick). I can also copy files from my tablet to my ubuntu computer, but i cannot copy files from my ubuntu computer to my tablet. 
I also tried this with gmtp but the results are the same.
Here's the results from gmtp (after mounting with mtpfs)
```
Device 0 (VID=0b05 and PID=4e1f) is UNKNOWN.
Please report this VID/PID and the device model to the libmtp development team
ignoring usb_claim_interface = -16ignoring usb_claim_interface = -22PTP_ERROR_IO: Trying again after re-initializing USB interface
inep: usb_get_endpoint_status(): Device or resource busy
outep: usb_get_endpoint_status(): Device or resource busy
usb_clear_halt() on IN endpoint: Device or resource busy
usb_clear_halt() on OUT endpoint: Device or resource busy
usb_clear_halt() on INTERRUPT endpoint: Device or resource busy

Error getting file from MTP device.
Error 1: LIBMTP_Get_File_To_File(): Could not create file.
Error sending track.
Error 2: PTP Layer error 02ff: LIBMTP_Send_File_From_File_Descriptor(): Could not send object.
Error 2: (Look this up in ptp.h for an explanation.)
Error 1: LIBMTP_Send_Track_From_File_Descriptor(): subcall to LIBMTP_Send_File_From_File_Descriptor failed.
Unsupported abstract list type: ba03
Error creating or updating album.
(This could be due to that your device does not support albums.)
Error 1: create_new_abstract_list(): player does not support this abstract type.
Segmentation fault

```
the mountpoint of my tablet is media/TF101 and I used chmod 775 to set permissions for it.
This is all very odd because I definitely have permission to install apps from ubuntu via usb to the tablet. I set this up and tested it, using the Processing IDE (processing.org) I can easily run apps I've made in Processing and send them to my tablet for testing (which I thought was going to be the difficult part, but was actually not following instructions [http://developer.android.com/guide/developing/device.html](http://developer.android.com/guide/developing/device.html) with usb debugging turned on in android's settings app).
If you have any suggestions other than mtpfs or gmtp for transferring files from ubuntu  to transformer TF101 I'd really like to hear about them, as I find gmtp's interface a little odd and mtpfs seems to really slow down the process of connecting to other usb devices (for a period of time after the tablet is unmounted). If you have suggestions of how I can make any one of gmtp or mtpfs work with ubuntu I would also really like to hear from you please..
Any help is greatly appreciated!
Ubuntu Studio 10.10, Asus Transformer TF101, Android 3.2

---

### Post by _Aries_ on 2011-09-08
You have to use adb shell and push the files through. If you installed ubuntu using lilsteve's install through xda forums, then look through the other posts and it shows you how to connect using adb. If you cant find it, I can help you here. I'll look for it also and try to post links for you.

---

### Post by _Aries_ on 2011-09-08
Download the SDK for linux here:

[http://developer.android.com/sdk/index.html](http://developer.android.com/sdk/index.html)

Unzip somewhere that you know how to access (like destop ~/Desktop/android-sdk_r12-linux_x86/)

I used this website to install and get it working:

[http://onthefencedevelopment.com/?p=455](http://onthefencedevelopment.com/?p=455)

After getting everything installed, go to your folder where you installed the sdk, and go to /platform-tools/ and type ./adb [command]

A list of commands can be found here:

[http://developer.android.com/guide/developing/tools/adb.html](http://developer.android.com/guide/developing/tools/adb.html)

but this is what you want:

Copying Files to or from an Emulator/Device Instance

You can use the adb commands pull and push to copy files to and from an emulator/device instance's data file. Unlike the install command, which only copies an .apk file to a specific location, the pull and push commands let you copy arbitrary directories and files to any location in an emulator/device instance.

To copy a file or directory (recursively) from the emulator or device, use

adb pull <remote> <local>
To copy a file or directory (recursively) to the emulator or device, use

adb push <local> <remote>
In the commands, <local> and <remote> refer to the paths to the target files/directory on your development machine (local) and on the emulator/device instance (remote).

Here's an example:

adb push foo.txt /sdcard/foo.txt



Hope this helps!!

---

### Post by BcRich on 2011-09-08
Hi _Aries_
Thanks 4 the reply :)
I have already tried the adb 'platform-tool' and it is the one method that does work, re transferring files to my tablet. sorry, i forgot to mention that in my previous post. it's definitely a method worth pointing out so thanks for sharing that :)
I was kinda looking for a more user "friendly" approach that doesn't involve a command line interface, something like with an improved working GUI over gmtp or like mtpfs works with nautilus. do you perhaps know of something along those lines?
Don't get me wrong though, i think adb is great (i.e. it does exactly what it's supposed to do) and it's what i'm currently using for transferring files to the tablet, and using mtpfs to transfer files to my computer 'cause being able to use nautilus makes selecting multiple files quicker and easier for me.
once again thanks again for pointing out the abd tool!

---

### Post by dgrafix on 2011-12-23
Dunno if it is helpful, but on mine i cannot transfer files (the MSD way) if usb debugging is turned on it reports device busy.

---

