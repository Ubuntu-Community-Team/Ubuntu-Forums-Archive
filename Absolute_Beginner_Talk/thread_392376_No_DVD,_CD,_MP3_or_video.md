---
title: "No DVD, CD, MP3 or video"
date: 2007-03-24
forum: Absolute Beginner Talk
---

### Post by imacbo on 2007-03-24
Ok I installed the Unbuntu CD on my computer. And so far my wireless card (Broadcom 4318 which is the only way I can get online) is not supported with the CD. Also I can not play DVDs CDs MP3s or videos. So did the cd not come with any of the plug-ins needed? Or did I not get a good install? Is the plug-ins hidden on the install CD? Can someone help me with this? Right now the only way I can get online is windows. Can I download what I need in windows and save it to my portable hard drive and then install it with unbuntu? If so where do I download from? Can someone help with that as well? Thanks in advance for your help

---

### Post by chamberlain2006 on 2007-03-24
Ok, first, the wireless card you have, Broadcom 4318, is installed using this tutorial: [https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Edgy](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Edgy).  To install multimedia codecs, [https://wiki.ubuntu.com/RestrictedFormats](https://wiki.ubuntu.com/RestrictedFormats) should explain it.

---

### Post by imacbo on 2007-03-24
The link you sent for the wirelss driver only works if you have an internet connection with Unbuntu. The only way I can get online is in windows because the wireless card dont work with Unbuntu right now because I dont have the driver for it. I'm checking the other link you sent and so far all I see is how to download with Unbuntu. Once again which I can not get online with

---

### Post by rajeev1204 on 2007-03-24
Hi

for ur multimedia , install gxine or mplayer from synaptic.

It will play all ur vcd,dvd and stuff.For mp3 , install gstreamer fluendo mp3 from repository. Plays mp3 in rythmbox . Install mozilla-mplayer plugin for strreaming video in firefox

mplayer  is capable of playing almost any format.


By default ubuntu does not include proprietary codecs .But u can easily download from synaptic later .Enable universe and multiverse repos in synaptic .


Go to packages.ubuntu.com from windows and u can download these packages for ur version. (simple) . Watching a few movies will cheer u up before u cconfigure ur wireless conection 


regards


rajeev

---

### Post by chamberlain2006 on 2007-03-24
The installation is more complicated without an internet connection.  Do you have a wired connection that you can use for the time being?  In any case, you'll need some sort of internet connection to get the files and programs you need.

---

### Post by ramzai on 2007-03-24
Try the first part of [http://ubuntuforums.org/showthread.php?t=197102](http://ubuntuforums.org/showthread.php?t=197102) - you can download the file in windows, and then proceed instructions in ubuntu. If you'll have internet connection, things will be easier.

---

### Post by imacbo on 2007-03-24
All I have is a wireless connection. I am in Kuwait right now with the US Army and the only internet we have is wireless. I can connect with windows xp. that is the only way I can get online right now. so can i still get what I need

---

### Post by chamberlain2006 on 2007-03-24
Your card is listed as "unstable" so you might want to use the ndiswrapper driver.  This is available on the LiveCD.  When you insert it, you will have an option to use the CD as a software source.

---

### Post by imacbo on 2007-03-24
ok with the risk of sounding like a total bonehead do i start up with the disk or with unbuntu and will the driver be on the disk or how do i get the wireless driver

---

### Post by chamberlain2006 on 2007-03-24
You will need to place the CD in the compter while running Ubuntu.  It will ask you to enable it as a software source.  Then go into the Synaptic and install ndiswrapper-utils1.8 and ndiswrapper-common.  YOu will also need the driver for you wireless card.  Ndiswrapper uses the windows driver, so you will have to have that ready.

---

### Post by imacbo on 2007-03-24
where can i find the driver at and can i copy it to my portable hard drive and get it that way because i dont have my restore cd here

---

### Post by ramzai on 2007-03-24
> **imacbo said:**
> where can i find the driver at and can i copy it to my portable hard drive and get it that way because i dont have my restore cd here
In the link I provided, along with automated script. Hope this helps, I remember I followed another howto ( I also have this damn 4318 ), also with only wireless in windows.

---

### Post by kahrytan on 2007-03-24
For Video, use VideoLAN from [http://www.videolan.org/](http://www.videolan.org/)

It is better then any other video player on Linux. To play dvds with it, you need libdvdcss2. VLC will play Divx, xVid and any other video you through at it.

---

### Post by chamberlain2006 on 2007-03-24
Get [ftp://ftp.support.acer-euro.com/notebook/aspire_3020/driver/WLan%20Driver%20Broadcom%20802.11g%203.100.46.0.zip](ftp://ftp.support.acer-euro.com/notebook/aspire_3020/driver/WLan%20Driver%20Broadcom%20802.11g%203.100.46.0.zip)... it will have the necessary INF file: bcmwl5.INf.  Install it using

```

sudo su
ndiswrapper -i bcmwl5.inf
ndiswrapper -l
modprobe ndiswrapper
ndiswrapper -m
iwconfig wlan0 your_access_point_name
dhclient wlan0

```

---

### Post by imacbo on 2007-03-24
thanks guys i will try that and get back to you on it. thanks again

---

### Post by chamberlain2006 on 2007-03-24
Good luck, let me know how it works out!

---

### Post by imacbo on 2007-03-24
ok LOL this is such a pain in my neck!! I tried everything you guys said. I dont know if I did it right but i did it none the less. And now it says the driver is installed but i still have no internet and the setting is still on lo (loopback I think). I went a head and bit the bullet and bought a wireless pc card that is suppose to have linux drivers on it. I really like the idea of getting away from windows but this has been a major pain in the neck!! Why would an OS have to have an internet connection to get to play dvds cds videos and mp3s why would it not be ready for that? I like the idea of linux  and I like the interface that Unbuntu has but with out an internet connection you cant do anything with it. Why is that? Is there not someway to get all of the stuff i need ie. dvd player, cd, mp3 or video while online with windows and saving it to my exteral hd then coping it to Unbuntu? And why does it seem like it is such a pain to do anything like that? Well anyway hopefully in about a week I can get online and get the drivers I need when I get this wireless pc card. Then if things go well i might get rid of windows altogether.

---

### Post by ramzai on 2007-03-25
> **imacbo said:**
> ok LOL this is such a pain in my neck!! I tried everything you guys said. I dont know if I did it right but i did it none the less. And now it says the driver is installed but i still have no internet and the setting is still on lo (loopback I think). I went a head and bit the bullet and bought a wireless pc card that is suppose to have linux drivers on it. I really like the idea of getting away from windows but this has been a major pain in the neck!! Why would an OS have to have an internet connection to get to play dvds cds videos and mp3s why would it not be ready for that? I like the idea of linux  and I like the interface that Unbuntu has but with out an internet connection you cant do anything with it. Why is that? Is there not someway to get all of the stuff i need ie. dvd player, cd, mp3 or video while online with windows and saving it to my exteral hd then coping it to Unbuntu? And why does it seem like it is such a pain to do anything like that? Well anyway hopefully in about a week I can get online and get the drivers I need when I get this wireless pc card. Then if things go well i might get rid of windows altogether.

1. I found the howto I followed, maybe it will help - [https://help.ubuntu.com/community/WifiDocs/Device/Broadcom_BCM4311_rev_01_(ndiswrapper)](https://help.ubuntu.com/community/WifiDocs/Device/Broadcom_BCM4311_rev_01_(ndiswrapper))
2. If you need to download some package from windows, you can navigate to [http://archive.ubuntu.com/ubuntu/pool/main/](http://archive.ubuntu.com/ubuntu/pool/main/) , download required .debs and then sudo dpkg -i file.deb - that installs downloaded package.
3. Well, the only real major problem I had in linux, was that wireless issue. That is because the vendor of the card didn't bother to write a driver for linux, and also doesn't want to open specifications for other people to write it. So people who I writing drivers work with the card as a black box, trying to guess what commands should they issue to make it work.
As long as you have internet connection, everything is much easier.
4. DVD, CD, mp3 - see [https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats) , how to install support, and why it is not included be default (legal issues).

---

