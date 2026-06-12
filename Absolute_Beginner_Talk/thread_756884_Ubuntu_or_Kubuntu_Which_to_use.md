---
title: "Ubuntu or Kubuntu? Which to use?"
date: 2008-04-16
forum: Absolute Beginner Talk
---

### Post by gilweber on 2008-04-16
Hello, everyone. My first post.

I am new to Ubuntu (1 week), but I have used SuSE for several years. I am NOT a sophisticated user (e.g., weak on the command line), but I am comfortable using Linux with the GUI.

This new pooter came from Dell with Ubuntu. After 1 week I am really enjoying it and seriously considering not going back to SuSE. So here are my questions, and I'd appreciate your thoughts. 

1) Should I leave Ubuntu 7.10 as installed, or should I remove it and instead install Kubuntu with its KDE emphasis? I am very comfortable with KDE and very much less experienced with Gnome, and so if there is a reason to use Kubuntu rather than Ubuntu maybe it would make sense to make the switch. What would I gain, or lose, by moving from Ubuntu to Kubuntu? Or should I just install the avaialble KDE packages (e.g., KMail) into Ubuntu and go with the flow?

In anticipation I did download Kubuntu and now have kubuntu-7.10-dvd-i386.iso sitting on my desktop.

2) Whatever the answer to #1, I think I do have to reinstall in any case. The Dell install came with everything as one partition. Using SuSE I always partitioned the disk with roughly 10GB for the operating system and the remainder in separate partitions for my home directory and a small swap file.

I figure it would be wise to do the same thing here so that if I update Ubuntu (or Kubuntu) I can simply tell the pooter to write over the OS partition but to leave the other partitions untouched.

If I do this, what will I see during the install process with Ubuntu/Kubuntu? As with SuSE, will I be offered the chance to partition the hard drive, and is the install as utterly simple as it was with SuSE? 

Don't want to shoot myself in the foot here, so your wise guidance is greatly appreciated. Thanks!
Gil

---

### Post by ace007 on 2008-04-16
You can easily download the KDE environment from synaptic package manager.  You can then choose to boot to that session from the login window.  Just choose KDE session and make it default.  You don't have to format anything.  Gnome will still be available.  And if you really want to you can remove it.  I have both available on my "pooter"

---

### Post by smurphy_it on 2008-04-16
That is personal preference.  You can keep running Ubuntu (with gnome interface) and simply downkload the KDE desktop through a package manager of the command line.  Then it's just a matter of choosing which manager you prefer (or set say kde as the default).

As for your comments about re-partitioning.  I woiuld probably just boot the ubuntu live cd and run the partition editor (gparted) and change the size of the partition, create necessary partitions etc....

If there is no data on the computer, it might be faster to just re-load the O/S.

That's my two cents worth.

---

### Post by philinux on 2008-04-16
Click on the psychocats link below then scroll down the page to the Gnome/Kde links.

---

### Post by bumanie on 2008-04-16
You can do as above, have the choice of either desktop environment or do what you alluded to and add particular kde programs you like to use, and use them in gnome. Kde programs work fine in gnome as do gnome programs on kde.

---

### Post by Paqman on 2008-04-16
> **gilweber said:**
> 
2) Whatever the answer to #1, I think I do have to reinstall in any case. The Dell install came with everything as one partition. Using SuSE I always partitioned the disk with roughly 10GB for the operating system and the remainder in separate partitions for my home directory and a small swap file.


You can [set up a /home partition without re-installing](http://www.psychocats.net/ubuntu/separatehome).

But yeah, for KDE, just install [kubuntu-desktop](apt:kubuntu-desktop). Big download though.

---

### Post by ace007 on 2008-04-16
On Pyschocats Page, as stated above, click  "Install KDE" and its exactly what you're looking for.

---

### Post by acirilo on 2008-04-16
i prefer the responsiveness and feel of xubuntu. it's all personal taste.

---

### Post by gilweber on 2008-04-16
> **Paqman said:**
> You can [set up a /home partition without re-installing](http://www.psychocats.net/ubuntu/separatehome).

But yeah, for KDE, just install [kubuntu-desktop](apt:kubuntu-desktop). Big download though.

Many thanks to everyone for the quick replies!

To Paqman re: above...  If I download kubuntu-desktop from the URL you give, when I install that what happens? Does it duplicate what I have already gotten with the Synaptic Downloader ( Kmail, Kaffeine, KMPLayer, etc.)? Does it replace what I have now? Sorry for what may be a naive question, but I'm not clear on what I get with the download you suggest.

Thanks for a few clarifying thoughts.  :)
Gil

---

### Post by packrat on 2008-04-16
Being weak on the command line and having used Suse for a long time with KDE, too, I switched to Ubuntu 7.04 then to  7.10...both Gnome last year - and now 8.04 beta...all using Gnome...have never looked back...tried Kubuntu 7.04 to discover it was not as easy to use as Ubuntu running Gnome.

Had a few growing pains with 8.04 and networking...however, it's been solved...

For me, it Ubuntu with Gnome...I'm not a geek...a sophisticated and application user...I want something that works...this one works!

---

### Post by conscious on 2008-04-16
> **gilweber said:**
> To Paqman re: above...  If I download kubuntu-desktop from the URL you give, when I install that what happens?

kubuntu-desktop is a metapackage which depends on the components of KDE, so by installing it you will get a full KDE system. More information here: [https://help.ubuntu.com/community/InstallingKDE](https://help.ubuntu.com/community/InstallingKDE)

---

### Post by Paqman on 2008-04-16
> **gilweber said:**
> 
To Paqman re: above...  If I download kubuntu-desktop from the URL you give, when I install that what happens? Does it duplicate what I have already gotten with the Synaptic Downloader ( Kmail, Kaffeine, KMPLayer, etc.)? Does it replace what I have now? Sorry for what may be a naive question, but I'm not clear on what I get with the download you suggest.


The link I posted is just a little browser trick. It uses the same apt-get system that Synaptic does, and will get the download from your normal repos.

Downloading kubuntu-desktop will install the core set of KDE bits and pieces. If you've installed some KDE aps you may have some of this already. If that's the case it won't download those packages again. You can see what will be installed in Synaptic. Search for kubuntu-desktop and in it's properties check out the dependencies. These are the actual packages that will be installed.

Basically, the package manager is quite smart. It'll only download what it needs.

Once everything is downloaded you'll have to log out to enter KDE. At the login screen choose Options > Sessions > KDE. It'll ask you if you want to change the default session to KDE from then on. Voila! Your Ubuntu is now Kubuntu for as long as you want it be.

---

### Post by gilweber on 2008-04-16
> **conscious said:**
> kubuntu-desktop is a metapackage which depends on the components of KDE, so by installing it you will get a full KDE system. More information here: [https://help.ubuntu.com/community/InstallingKDE](https://help.ubuntu.com/community/InstallingKDE)

Thank you. Also a very helpful link. :)
Gil

---

### Post by jm2003uk on 2008-04-16
Just go with whichever you prefer. Or install both and just switch when you want something different. Gnome was the first environment i used while trying out fedora core 3 (iirc) and used gnome again when i switched to Ubuntu. I have now and then switched to KDE but always find myself back using gnome. I guess that's just personal preference on my part. No-one else can really make the final choice for you. I suppose on a plus, the apps from each environment work in the other one.

---

### Post by gilweber on 2008-04-16
> **Paqman said:**
> The link I posted is just a little browser trick. It uses the same apt-get system that Synaptic does, and will get the download from your normal repos.

Downloading kubuntu-desktop will install the core set of KDE bits and pieces. If you've installed some KDE aps you may have some of this already. If that's the case it won't download those packages again. You can see what will be installed in Synaptic. Search for kubuntu-desktop and in it's properties check out the dependencies. These are the actual packages that will be installed.

Basically, the package manager is quite smart. It'll only download what it needs.

Once everything is downloaded you'll have to log out to enter KDE. At the login screen choose Options > Sessions > KDE. It'll ask you if you want to change the default session to KDE from then on. Voila! Your Ubuntu is now Kubuntu for as long as you want it be.

Thanks, Paqman. Very helpful. 

Once I've added kubuntu-deskop and repartitioned the drive I'll let everyone know the results.

Again, thanks to everyone for the helpful suggestions. I really anticipate that I'll like Ubuntu/Kubuntu. :grin:
Gil

---

### Post by ace007 on 2008-04-16
Whoa, Whoa, Whoa!!!

Did I miss something?  You're not repartitioning anything solely for the use of KDE are you?  There is no need to format/re-partition anything just to get the use of KDE.  Just logout and use the session chooser.  

Maybe I missed something...

---

### Post by gilweber on 2008-04-16
> **ace007 said:**
> Whoa, Whoa, Whoa!!!

Did I miss something?  You're not repartitioning anything solely for the use of KDE are you?  There is no need to format/re-partition anything just to get the use of KDE.  Just logout and use the session chooser.  

Maybe I missed something...

No, as I explained in the opening post to this thread I'm partitioning solely to separate my home directory from the OS so that when I update the OS I don't also wipe my data.

Gil

---

### Post by ace007 on 2008-04-16
I knew I missed something!

---

### Post by Ozeuss on 2008-04-16
> **gilweber said:**
> Hello, everyone. My first post.
1) Should I leave Ubuntu 7.10 as installed, or should I remove it and instead install Kubuntu with its KDE emphasis? I am very comfortable with KDE and very much less experienced with Gnome, and so if there is a reason to use Kubuntu rather than Ubuntu maybe it would make sense to make the switch. What would I gain, or lose, by moving from Ubuntu to Kubuntu? Or should I just install the avaialble KDE packages (e.g., KMail) into Ubuntu and go with the flow?
In anticipation I did download Kubuntu and now have kubuntu-7.10-dvd-i386.iso sitting on my desktop.
2) Whatever the answer to #1, I think I do have to reinstall in any case. The Dell install came with everything as one partition. Using SuSE I always partitioned the disk with roughly 10GB for the operating system and the remainder in separate partitions for my home directory and a small swap file.
Gil
Hey Gil,
The issue is really weather you like KDE as a DE vs gnome, since you can always install kde apps. I am personally using KDE, but i think the initial ubuntu experience is much better on gnome (form my point of view, no advantage in using kubuntu instead of say, debian+kde)
I think the best way is to do as advised here- install either the kubuntu or the kde package and run it alongside gnome (I would use a different user, to keep things clean).
Setting up a seperate home partition is always helpful.

---

### Post by gilweber on 2008-04-18
Hey, everyone. I decided to go with Kubuntu, so I put the .iso into the DVD drive and rebooted and tried to let Kubuntu to install. Some odd things happened. Hopefully you can answer or clarify.

1) During the install I was never asked what packages or other items I wanted to install. It just ran. Whenever I loaded SuSE in the past I was always asked to select what I did and did not want. Is Kubuntu different? Do I automatically get a default install?

2) The install took forever and never seemed to finish. After an hour I still had a box on the screen that said "system loading." In the hour's time the screen changed maybe 3-4 times to show what seemed to be progress, but I'm just not sure what I was looking at. I eventually had to powerdown the pooter to get the DVD out of the drive and clear the screen.

3) How do I get rid of the "busy cursor" (the bouncing cursor)? I knew where to get rid of it in SuSE, but I sure can't find how to kill it in Kubuntu.

4) I just did an initial update of the 190 or so updates that were identified as available. I said "yes" to everything, but got several error messages about incomplete downloads, and it also appeared to try to download Ubuntu. Not sure, and I don't know how to verify since I can't seem to find where things are located.

This Kubuntu is not Ubuntu, and it's not SuSE/KDE. It's sort of both and neither, so I'm just a bit frustrated not knowing what's been loaded, or how to control what's been loaded, etc.

Sorry to sound so bummed, but this install was far from what I expected. Writing to you from my SuSE laptop since I have not figured out Kubuntu!  ;o)
Thx. for your understanding.
Gil

---

### Post by gilweber on 2008-04-21
Hello again, everyone. A status update.

After getting Kubuntu to insatall and working with it for awhile I decided that I liked Ubuntu better. So I partitioned the drive and re-installed Ubuntu 7.10. 

The install went very smoothly. I let the pooter update itself and added a few packages from KDE plus codecs and other stuff to let the box do what I wanted.

Again, all very smooth.

After a few days working with Ubuntu I really like it. I look forward to participating in the Ubuntu community, neophyte that I am. :D

Thanks again.

---

### Post by MONODA on 2008-04-21
i suggest that when hardy comes out, you upgrade to the KDE version of that (i think there will be KDE3 and KDE4 to choose from, choose whatever you are more comfortable with.)

---

### Post by c4v3m4n on 2008-04-21
I'd say stick with Ubuntu and if you want to you can install some of the kde applications that you prefer.  A complete reinstall isn't really necessary.

---

### Post by SuryaS on 2008-04-21
hi all ,
          i am new to ubuntu(2 days). got dual bootable system (windows & ubuntu) with internet connection.
  
         i am able to access internet from windows . but facing problem from ubuntu.plz help me setting up the system so as to access net from ubuntu .


Thanks in advance
surya

---

### Post by conscious on 2008-04-22
Hello SuryaS,

Please refer to this guide:
[https://help.ubuntu.com/community/InternetHowto](https://help.ubuntu.com/community/InternetHowto)

If is doesn't help, I suggest you create a new topic in the "Networking and Wireless" section ( [http://ubuntuforums.org/forumdisplay.php?f=336](http://ubuntuforums.org/forumdisplay.php?f=336) ) There you should give some more information about your means of connecting to the internet (which type/model of device you are using etc).

---

