---
title: "syncing iphone 4s with iOS 5.1 in ubuntu 12.04"
date: 2012-05-19
forum: Apple Hardware Users
---

### Post by BigWillieC on 2012-05-19
Hi, I'm trying to sync iphone 4s with iOS 5.1 in ubuntu 12.04. I've tried using the Rythmbox and gtkpod iPod manager. However they seem to be laced with errors. 

Question 1: Can you actually sync in 12.04?
Question 2: Do I need to have my iphone unlocked/jailbroken to manage it in 12.04?

Thanks

---

### Post by neofreud on 2012-05-19
Are you trying to simply sync music and podcasts, or perform backups, app management, etc.. ?

---

### Post by BigWillieC on 2012-05-19
I'm  trying to sync music, video and podcasts etc.

Cheers

---

### Post by BigWillieC on 2012-05-21
[FONT=Arial]Does anyone know how to sync music, video and podcasts etc on iphone 4s with iOS 5.1 in ubuntu 12.04??[/FONT]

---

### Post by dude2040 on 2012-05-22
This is currently not possible with iOS 5. For more details see [http://www.libimobiledevice.org/](http://www.libimobiledevice.org/). search for donate in the webpage.

---

### Post by orbitur on 2012-06-01
Actually, if you read libimobiledevice's page, they use libgpod for music sync.  libimobiledevice basically handles everything but music sync.

[http://www.gtkpod.org/wiki/Libgpod](http://www.gtkpod.org/wiki/Libgpod) <-- info

I've been on the gtkpod mailing list for a long time, and not much progress is being made on the iOS 5 front.  Last activity I saw regarding that was back in January, I think.  I don't know if it's a lack of interest or a lack of resources.

---

### Post by dierocck on 2012-07-30
anything new about this matter???

---

### Post by petersphilo on 2012-08-20
i'd be interested also...
i will test this in the next few days to see what can be done..
Cheers..

---

### Post by Nick Johnson on 2012-08-21
I have a kinda solution for this but its not realted to ubuntu so, its up to you taht you find it suitable or not.
I have finally found how to insert music into the iphone 4 database,  without using itunes. A program from cydia called  Mewseek,works on  my  jailbroken iphone 4, on IOS 5.01.

---

### Post by M4r5h4ll on 2012-09-29
i am very sick from this iphone thing. i wonder for how long we will suffer from it & why nobody posts a real helpful solution to us ?

---

### Post by spaceshipguy on 2012-09-29
> **M4r5h4ll said:**
>  i wonder for how long we will suffer from it & why nobody posts a real helpful solution to us ?

Sorry, but the sad truth is...

This situation will not change soon. Every iOS update includes code changes and other tricks to make it hard for non-Apple products to interact with it. Apple are taking ever more steps to make the wall round their walled garden higher. They want every piece of hardware you own to have an Apple logo on it. 
If you're not OK with this they are going to try and make your life difficult.

The only workarounds right now are to give in and buy a MacBook, not ideal because iTunes is unstable and every time it trashes your iPod the only solution is to reinstall the iOs and content from a backup, a process that can take hours, Mac forums are full of such tales of woe. 

 Or run iTunes in a virtual box - not easy, but I got it to work, again you have to deal with iTunes, which is suboptimal in device management, but very good at selling content.

Or, install OPlayer Lite, (free from the app store) and drag and drop music to the documents folder it provides - (how long Apple will allow them to keep providing this workaround is another question).

P.S. Do not update your device iOS, no matter how insistently it asks you too, this will only make things worse as far as connecting it to non-Apple hardware and software goes.

---

### Post by Paddy Landau on 2012-09-29
> **M4r5h4ll said:**
> i am very sick from this iphone thing. i wonder for how long we will suffer from it & why nobody posts a real helpful solution to us ?
Simply, Apple is not interested in supporting Linux. Period.

I don't know why, because Linux is much closer to iOS (Unix) than is Windows.

---

### Post by buckyaustin on 2012-09-30
This really should have its own thread, for easy access. So if anyone here wants to make this its own thread please do so.

Requires jailbroken device,dTunes or VLC4iPhone or YouTubeToMP3, all available in cydia.This tutorial is for YouTubeToMP3.Works for all iDevices to my knowledge, on all Linux machines.

Step 1; Install openssh

This step requires you to install openssh from cydia on your iDevice.
Open cydia, go to search. Look for openssh, then click openssh from the list. Click install on the top right of the screen. Wait till complete, then switch to your pc.

Step 2; Install filezilla

Method A(advanced/fast)
Type the below command without qoutes into a terminal.
"sudo apt-get install filezilla"

Method B (for beginers/slower)
Open ubuntu-sofware-centre and search for filezilla. Once fonud righ click and install.

Step 3; Using filezilla
Once complete run filezilla, in the host type sftp://root@[your-iDevice-IP-Address].

To Find your ip address open Settings, go to Wi-Fi, click the little blue icon just right of your internet connection. You will find it there. An example of a host is as follows:

sftp://192.168.1.100

In username type "root". This works for all iDevices.

Then in password type "alpine". You should change this password.

Then click Quickconnect.

The rest is drag and drop.

The location of music on an Idevice is "/var/mobile/Media/Downloads"
The location of music on Ubuntu is "/home/[username]/Music/"

Tested on iTouch 4g iOS 5.1.1 jailbroken. Kubuntu 12.04 and 12.10.

---

### Post by beavenburt on 2012-10-16
Not sure whether this is the solution you're after but it works for me. I installed File Manager by Tapmedia from the appstore which allows you to create folders. Then I created a music folder and just drag and drop mp3s into it using nautilus or in my case pcmanfm. Voila, play them on your iphone directly from the file manager. No itunes needed.

---

### Post by Jgonick on 2012-10-25
Spaceshipguy,

Another option.  CopyTransManager  [http://www.copytrans.net/copytransmanager.php](http://www.copytrans.net/copytransmanager.php)

It still needs Windows, but I run it in VirtualBox w/usb support.   Not the perfect solution, but its free (at least right now) and  I don't have to use Itunes....

---

### Post by mitulv4u on 2012-10-30
This one works. thanks a lot buckyaustin.
But cannot copy music from desktop to iPod Touch. It does not show up on iPOD. I am able to view all existing podcasts and mp3 songs and download to my Ubuntu from iPod Touch.

It seems you cant even check what the content is from filename. They rename all songs and other content in your Pod.

> **buckyaustin said:**
> This really should have its own thread, for easy access. So if anyone here wants to make this its own thread please do so.

Requires jailbroken device,dTunes or VLC4iPhone or YouTubeToMP3, all available in cydia.This tutorial is for YouTubeToMP3.Works for all iDevices to my knowledge, on all Linux machines.

Step 1; Install openssh



---

### Post by icebird1942 on 2012-11-09
There is a free Ubuntu program called Banshee which is a media player with the ability to sync with devices INCLUDING Apple. Website is banshee.fm. There are no complicated installs because it is available on the Ubuntu Software Center. You might want to try it out.

---

### Post by hatredman on 2013-03-08
> **icebird1942 said:**
> There is a free Ubuntu program called Banshee which is a media player with the ability to sync with devices INCLUDING Apple. Website is banshee.fm. There are no complicated installs because it is available on the Ubuntu Software Center. You might want to try it out.

Not at all. Banshee uses libgpod and it supports only iOS version 4 and lower. 

Anyone using iOS 5 (or 6) is stuck.

---

### Post by bl4ck74ck on 2013-04-15
Hi there is always the choise of using something like [bridge]("http://ipad-os.net/bridge-cydia-tweak-iphone-ipad/"). You just have to transfer the songs to a folder inside your device and then use the app to import them into the music.app's database. Pretty straightforward. It works with the latest ios version.

---

