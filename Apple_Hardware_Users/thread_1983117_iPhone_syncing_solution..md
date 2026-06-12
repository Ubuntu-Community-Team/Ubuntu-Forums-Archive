---
title: "iPhone syncing solution."
date: 2012-05-19
forum: Apple Hardware Users
---

### Post by Solitary7 on 2012-05-19
Good day all. 

I'm trying to figure out what is the Linux alternative to iTunes so that I could continue backing up my iphone. I figured out that I can sync music with Rhytmbox, but I'm concerned about apps and such.

---

### Post by neofreud on 2012-05-19
I am not sure about a program that works like itunes (in the sense of app management and backups) However the latest version of iOS is cloud based so you essentially never need to hook it up to itunes in order to get backups, updates, etc.. everything is stored in the cloud and if you ever have issues you should be able to simply re-download any apps or whatnot. 

I am assuming this is a recent model of iPhone of course. 

Hope this helps.

---

### Post by Solitary7 on 2012-05-20
> **neofreud said:**
> I am not sure about a program that works like itunes (in the sense of app management and backups) However the latest version of iOS is cloud based so you essentially never need to hook it up to itunes in order to get backups, updates, etc.. everything is stored in the cloud and if you ever have issues you should be able to simply re-download any apps or whatnot. 

I am assuming this is a recent model of iPhone of course. 

Hope this helps.

Hey, thank you for the reply. 

The cloud is a confusing thing. I hate the fact that I can't upload to the cloud exactly what I want. If i could just upload contacts, with Shotwell and Rhytmbox taking care with the rest, I'd be calm. 

I was going to install windows on a 20-30gb partition just to have it if I run out of ways (i'm a noob) to replace windows programs, so I might have to do that still.

---

### Post by Vignesh Sankaran on 2012-05-21
> **Solitary7 said:**
> Hey, thank you for the reply. 

The cloud is a confusing thing. I hate the fact that I can't upload to the cloud exactly what I want. If i could just upload contacts, with Shotwell and Rhytmbox taking care with the rest, I'd be calm. 



It is possible to just use Google/iCloud/ (insert desired online contact syncing service) for contact syncing, and use other programs in ubuntu to sync music onto your iPhone. 

I believe the iCloud menu in the iPhone helps you to choose what you'd like to sync to iCloud or not. For example, I sync notes and emails with iCloud, but I sync my contacts with Google. 

The fact that the iPhone integrates so tightly with iTunes makes it difficult to use on other platforms that are outside of it. I myself had that problem when I got my iPhone 3GS in 2010.

---

### Post by Solitary7 on 2012-05-28
> **Vignesh Sankaran said:**
> It is possible to just use Google/iCloud/ (insert desired online contact syncing service) for contact syncing, and use other programs in ubuntu to sync music onto your iPhone. 

I believe the iCloud menu in the iPhone helps you to choose what you'd like to sync to iCloud or not. For example, I sync notes and emails with iCloud, but I sync my contacts with Google. 

The fact that the iPhone integrates so tightly with iTunes makes it difficult to use on other platforms that are outside of it. I myself had that problem when I got my iPhone 3GS in 2010.

Hey, yes I figured out how to sync specific things to iCloud, because it would want to sync pictures and then would say that I do not have enough space.

---

### Post by dbunnell on 2012-05-29
Hi, how did you get your iPhone to sync with Rhythmbox or Banshee? I cannot for the life of me get it to sync to my phone. Any help would be greatly appreciated

---

### Post by Solitary7 on 2012-05-30
> **dbunnell said:**
> Hi, how did you get your iPhone to sync with Rhythmbox or Banshee? I cannot for the life of me get it to sync to my phone. Any help would be greatly appreciated

Hey, I do not have music on my phone because I also have a 160gig ipod. BUT. Everytime I plug in my iphone the Rhytmbox wants to sync music with it. I didnt have to do anything special. Sorry.

---

### Post by VE6EFR on 2012-05-30
> **dbunnell said:**
> Hi, how did you get your iPhone to sync with Rhythmbox or Banshee? I cannot for the life of me get it to sync to my phone. Any help would be greatly appreciated

On my system, when I plugin my iPhone I then launch Banshee. If you look on the left side you should see your device listed. Click on your device and you should find some options available to you for managing music, podcasts, etc. 

Hope this helps

---

### Post by dbunnell on 2012-05-30
> **VE6EFR said:**
> On my system, when I plugin my iPhone I then launch Banshee. If you look on the left side you should see your device listed. Click on your device and you should find some options available to you for managing music, podcasts, etc. 

Hope this helps
Well, I have done this, but once it finishes syncing, I look at my phone and the music isn't there.

---

### Post by user256 on 2012-06-08
Having exactly the same problem on this. Any news?

---

### Post by Solitary7 on 2012-06-10
> **user256 said:**
> Having exactly the same problem on this. Any news?
Nope

---

### Post by MisterGaribaldi on 2012-06-10
@OP: There may be ways to do this at any given moment in time, but remembers something very important: Apple does not want you doing any of these tasks with anything besides iTunes. So, even if the F/OSS community figures out a way tomorrow to make an iPhone fully work in Banshee (or anything else), "next Thursday" Apple could have an update out that will stop that.

Using an iPhone on Linux is nothing but a major cat-and-mouse game.

---

### Post by Solitary7 on 2012-06-12
> **MisterGaribaldi said:**
> @OP: There may be ways to do this at any given moment in time, but remembers something very important: Apple does not want you doing any of these tasks with anything besides iTunes. So, even if the F/OSS community figures out a way tomorrow to make an iPhone fully work in Banshee (or anything else), "next Thursday" Apple could have an update out that will stop that.

Using an iPhone on Linux is nothing but a major cat-and-mouse game.

Thank you for your reply. 

Unfortunately, I believer that iPhone is the best cell phone out there and I am very satisfied with it. I came to the conclusion that my best bet is to install Windows in VirtualBox and use it just for itunes. Now i just gotta figure out what virtual windows does not recognize my USB ports..

---

### Post by eric-yorba on 2012-06-13
> **Solitary7 said:**
> Now i just gotta figure out what virtual windows does not recognize my USB ports..
Two things:
1. Make sure your VM is in single-core mode.   VirtualBox has a long standing bug where USB doesn't work with multicore VMs.
2. Install the proprietary VirtualBox Extensions.

---

### Post by Ashtechsmith on 2012-06-14
Nexthaus SyncJe is software that wirelessly synchronizes your mobile  Calendar, Contacts, Tasks, and Notes with SyncML Servers.  You can  easily sync your iPhone or BlackBerry with your desktop computer and  Outlook. SyncJe is easy to setup, and free to try.

---

### Post by Solitary7 on 2012-06-15
> **eric-yorba said:**
> Two things:
1. Make sure your VM is in single-core mode.   VirtualBox has a long standing bug where USB doesn't work with multicore VMs.
2. Install the proprietary VirtualBox Extensions.

Thanks for suggestion. But i installed those and VB is only using one core. still can't get it to work:confused:

---

### Post by joesully on 2012-08-26
> **user256 said:**
> Having exactly the same problem on this. Any news?
im having the exact same problem aswell this is what i have done so far
:
how do i sync my iphone 3gs with ubuntu 12.04 ive tried all the apps amarok,rhythmbox etc itunes 7 from playonlinux and the newest itunes using wine and none are working i have tried for a couple of weeks to do it myself but i havent got any were so i ask you please answer

---

### Post by melinda on 2012-09-25
have EXACT issue with ALL Ubuntu players.  any resolution?

---

### Post by linuxvstheworld on 2012-09-27
If you actually like iTunes (many don't), you can run it via Wine but i'm not sure if everything'll work.
How well Wine runs it: [http://appdb.winehq.org/objectManager.php?sClass=application&iId=1347](http://appdb.winehq.org/objectManager.php?sClass=application&iId=1347)
If you want to jump on a limb and not look at that link just do the following: [http://www.winehq.org/download/ubuntu](http://www.winehq.org/download/ubuntu)

EDIT: But rhythmbox should do you well if you just want to sync music and get everything else over the cloud.

---

### Post by spaceshipguy on 2012-09-29
> **melinda said:**
> have EXACT issue with ALL Ubuntu players.  any resolution?

Sorry it just isn't possible. The brave people that must reverse engineer ways of talking to iPods, iPads and iPhones every time Apple change the codes on the strange database system they use have not cracked the code on databases after iOS 4.

My Ipod Touch (with iOS 5.0.1) will not sync for example, the iOS database type 5 code is not yet cracked.

I add music to my iPod via OPlayer Lite (free from app store). It provides a folder in the documents section for darg and drop files to be added. 
So I can drag and drop music from Ubunti, but sync is not going to happen any time soon. 

My advice, if you need sync, is install virtual box - I got it working but setting up Windows 7 64 to see Apple drivers was just as hard as setting up the virtual environment.

Every time you update iOS on your Apple device you add 6 months or longer to the arrival of Ubuntu support for your device because every iOS update intentionally adds new obstacles. These must then be overcome by the dedicated people making sure these devices are supported, despite Apple's attempts to prevent this.

---

### Post by gabriele.bianchi on 2012-11-29
I just want to report on my recent experience with Iphone 5.

I have tried to copy songs on the iphone  via banshee without success. The files are copied on the iphone but the "Music" app on the iphone does not show them.

The solution suggested by spaceshipguy, to install Oplayer Lite, and to use a file manager on the PC to copy songs files to the folder created by Oplayer Lite in the Iphone Document folder, this solution works. 
Thanks spaceshipguy.

Trying to connect to the iphone via itunes, both when run in windows in virtualbox and when run in ''real windows'', did not work. My daughter's  Iphone is pretty new, about one week, and she has done no strange thing with it, except possibily the  copy of songs via banshee. In any case this is sufficient to make itunes complain, refuse to connect to the iphone and ask to (I do not remember the exact word) ''reinitialize it'', wiping all her personal data. Of course she refused and we will have to live without itunes....

Gabriele Bianchi

---

