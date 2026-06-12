---
title: "Modprobe Config Already Contains Alias Directive Problem"
date: 2007-03-31
forum: Absolute Beginner Talk
---

### Post by dnguyen527 on 2007-03-31
I have been working on this for over 10 hours now. Trying to get my f5d6050 netowork usb card to work. 

Me and this other guy got to the part in these directions:

Download the driver. Extract to a new directory using unzip. Extract the CAB files (DATA1.CAB, DATA1.HDR, DATA2.CAB) using "unshield x" . cd Drivers/WINXP . edit bkusb.in_ and uncomment the CopyFile.XP.Sys section. Run ndiswrapper -i bkusb.in_ as root followed by ndiswrapper -m . modprobe ndiswrapper. ifdown wlan0. ifup wlan0 and you are there.

We got to: 

```
sudo ndiswrapper -i bkusb.in_
```

That part says its installed and present. 

Now when we go to:

```
sudo ndiswrapper -m
```

It says:

```
Modprobe config already contains alias directive
```

So we cant continue to the rest of the directions that say to type:

```
sudo modprobe ndiswrapper
```

and so on....

Refer to the posts in [http://ubuntuforums.org/showthread.php?p=2382991#post2382991](http://ubuntuforums.org/showthread.php?p=2382991#post2382991)

Its pretty long.

Any help would be great. I just want to get online!

Please keep in mind that my Linux computer has no online connection. I transfer downloaded files from this laptop and transfer with a flash drive.

I have installed:

ndiswrapper and alien 

Just stuck now :( I dont want to go back to XP!

---

