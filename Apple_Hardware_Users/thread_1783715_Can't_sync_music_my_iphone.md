---
title: "Can't sync music my iphone"
date: 2011-06-16
forum: Apple Hardware Users
---

### Post by kirill578 on 2011-06-16
I tried to sync my music to my iphone 4 with banshee player, all goes smooth, but when i open my ipod i can't find it can't find any music, i tried to reconect it to my pc and then i noticed that the music that i synced diapered, I looked into music folder, on my iphone and i could found it (manually)/

I think there is a problem with updating the DB of the ipod

---

### Post by zacbarton on 2011-06-16
See [_here_]("http://ubuntuforums.org/showpost.php?p=10883291&postcount=2")

---

### Post by kirill578 on 2011-06-16
There is written that there is support for 4.3.3 so what I should wait for?!

so I tried to install it. I added this source to my Ubuntu software center, but there is no download for libimobiledevice 1.0.6
there just 1.0.3 ( this one is aready installed ).

[https://launchpad.net/~pmcenery/+archive/ppa]("https://launchpad.net/%7Epmcenery/+archive/ppa")

---

### Post by kirill578 on 2011-06-17
Bump

---

### Post by kirill578 on 2011-06-24
Bump

---

### Post by BrianMal on 2011-06-25
bump

---

### Post by haqking on 2011-06-25
[http://www.psychocats.net/ubuntu/itunes](http://www.psychocats.net/ubuntu/itunes)

[http://www.simplehelp.net/2007/07/08/10-alternatives-to-itunes-for-managing-your-ipod/](http://www.simplehelp.net/2007/07/08/10-alternatives-to-itunes-for-managing-your-ipod/)

---

### Post by kirill578 on 2011-07-24
> **haqking said:**
> [http://www.psychocats.net/ubuntu/itunes](http://www.psychocats.net/ubuntu/itunes)

[http://www.simplehelp.net/2007/07/08/10-alternatives-to-itunes-for-managing-your-ipod/](http://www.simplehelp.net/2007/07/08/10-alternatives-to-itunes-for-managing-your-ipod/)

I've just tried all the alternatives. Banshee, Rhythmbox and gtkpod detected my iphone but non of them was able to mange ipod 4.3.3 database successfully. Has anybody found a solution so far?_****_**[]("http://www.simplehelp.net/2007/07/08/10-alternatives-to-itunes-for-managing-your-ipod/#gtkpod")**

---

### Post by kirill578 on 2011-08-27
I've found a solution:

1. Jaibreak the phone (via [http://jailbreakme.com]("http://jailbreakme.com/"))
2. Install openssh from cydia
3. ssh to the phone
4. change DBVersion to 4 in the /system/library/lockdown/Checkpoint.xml
5. Generated HashInfo following the link [http://ihash.marcansoft.com/](http://ihash.marcansoft.com/)
6. copy HashInfo to the folder /var/mobile/Media/iTunes_Control/Device/
7. Reboot the phone
8. Mounted device automatically using Ubuntu Natty (libmobiledevice, ifuse and so on already installed)
9. Sync using Banshee

***to get your UUID connect the iphone and execute:***
lsusb -v | grep -i iSerial

---

### Post by messymurder on 2011-09-04
> **kirill578 said:**
> I've found a solution:

1. Jaibreak the phone (via [http://jailbreakme.com]("http://jailbreakme.com/"))
2. Install openssh from cydia
3. ssh to the phone
4. change DBVersion to 4 in the /system/library/lockdown/Checkpoint.xml
5. Generated HashInfo following the link [http://ihash.marcansoft.com/](http://ihash.marcansoft.com/)
6. copy HashInfo to the folder /var/mobile/Media/iTunes_Control/Device/
7. Reboot the phone
8. Mounted device automatically using Ubuntu Natty (libmobiledevice, ifuse and so on already installed)
9. Sync using Banshee

***to get your UUID connect the iphone and execute:***
lsusb -v | grep -i iSerial

Is this confirmed?

---

### Post by chayzer on 2011-09-12
Just confirmed on an iPhone4 running 4.3.3. Thanks kirill!

Used rhythmbox to sync and I have the latest libimobiledevices installed. Not sure if that's necessary though.

---

### Post by carmenrqjones on 2011-09-13
To download music onto iPhone from the internet, you will obviously need  an internet connection. Having a really good broadband connection will  obviously be a great help, but dial up will certainly do. Music  downloads are much smaller than movies, and once you have downloaded a  track once, you can then listen to it as many times as you like without  having to download it again.

[iPhone5 release date](http://iphonereleases.com/)

---

### Post by jameskevindoyle on 2011-09-16
I agree, thanks kirill!  I've been trying to sync music to the ipod touch I was given almost a year ago now, and the directions in this forum thread are the first that have ever worked for me!

I've got an ipod touch 4g running iOS 4.1, and even jailbroken I had the toughest time updating its iTunes database from Linux.  The DBVersion=4 and HashInfo approach did the trick.

I've got an up-to-date Natty (11.04) install, but with the daily build of Banshee (currently 2.1.4) because the Natty Banshee didn't have the latest updates needed to get song info from MusicBrainz.  Natty always had no trouble recognizing the iPod and showing it in Banshee.  But the DBVersion=4 and HashInfo trick now makes it so that Banshee can sync without errors, and the songs show up under the iPod's Music.

Thanks again!
Jim

---

### Post by loughmillermedia on 2011-09-27
I have the exact same problem and was looking all over the web for some help. This forum has been the most helpful by far.

---

### Post by blueidealist on 2011-10-12
In my case, this solution only half works.
I've made progress, because now once banshee/rhythmbox tell me the iphone is synced and I disconnect/reconnect it, I can indeed play files that I have just added to the iphone...

However, the iphone itself (Through the iPod app) does not see any of the added music files...

---

### Post by kirill578 on 2011-10-19
> **blueidealist said:**
> In my case, this solution only half works.
I've made progress, because now once banshee/rhythmbox tell me the iphone is synced and I disconnect/reconnect it, I can indeed play files that I have just added to the iphone...

However, the iphone itself (Through the iPod app) does not see any of the added music files...

It works for me on ubuntu 11.04 and IOS 4.3.3. maybe you miscopied the uuid

---

### Post by GrouchyGaijin on 2011-10-30
So do I understand correctly that the only way to move mp3s from my Ubuntu 11.10 PC to my iPhone4 (and be able to play them) is to Jail Break the phone?

I don't care about syncing I just want to move a few albums, maybe 40 or 50 songs.

---

### Post by Evelyn1984 on 2011-10-31
What about ipod nanon 6gen??? I'm a newbe here... please help me out, it's driving me insane :)

---

### Post by GrouchyGaijin on 2011-11-01
Ok,here is the thing - maybe this is covered in a guide I didn't get but if you install EZMP3, you can drag music to the documents folder (the EZMP3 folder in documents) and play your mp3s.

11.10 mounted my iPhone 4 without problem,

---

### Post by slcpunk on 2012-01-27
wrong thread...

---

### Post by Huss on 2012-03-18
GrouchyGaijin: I tried to use EZmp3 but couldn't transfer files across - even with file transfer mode on in the app. 

I'm using FileApp at the moment. For others not wanting to jail break their phone, there's a quick guide here: [http://ubuntuforums.org/showthread.php?p=11774578#post11774578]("http://ubuntuforums.org/showthread.php?p=11774578#post11774578")

Edit: Thanks GrouchyGaijin, just needed to create a folder in the 'managing folders' section of EZmp3 and then was then able to access through nautilus.

---

