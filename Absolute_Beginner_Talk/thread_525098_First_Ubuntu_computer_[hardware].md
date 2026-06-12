---
title: "First Ubuntu computer [hardware]"
date: 2007-08-13
forum: Absolute Beginner Talk
---

### Post by zeehat on 2007-08-13
Hi everyone, 

I am new to the boards, and to linux.  On my PC I am currently running Windows XP.  I would like to know if my hardware will be compatible with Ubuntu.  Any help is appreciated.  I downloaded Ubuntu to a CD already, and am awaiting install.  However, I am planning to buy another hard drive, dedicated to Ubuntu, so I will not need to re-install my Windows; to partition it properly.

My current specs on my PC are:
Nvidia Nforce3-a motherboard
AMD Sempron (tm) 2600+ processor
Seagate S-ATA 80 GB HD [Windows boot]
Seagate S-ATA 250GB HD [Storage drive]
2x 512 MB Kingston DDR 400 memory
Onboard sound and (onboard) wireless card
ATI X 800 All in One Wonder 
Pioneer 18X CD/DVD Writer DVR-112D

//I am planning on buying a 160 GB Seagate IDE HD, for my Ubuntu boot [If my computer hardware is all compatible].  Here is a link to it: [http://canadacomputers.com/index.php?do=ShowProduct&cmd=pd&pid=013496&cid=HD.443](http://canadacomputers.com/index.php?do=ShowProduct&cmd=pd&pid=013496&cid=HD.443)

The reason I am buying an IDE HD is that, my motherboard is out of S-ATA drive connectors.  It has open IDE connectors, hence the IDE drive.

\\I really am motivated to get Ubuntu up and running.  Thanks in advance for all your help.

---

### Post by RomeReactor on 2007-08-13
Hi. The only real way to know if your hardware will work properly is to download and burn the [Live CD]("http://www.ubuntu.com/getubuntu/download") and run it (it won't install anything until you tell it to, it'll just run from RAM) to see if there are any compatibility problems. Form the specifications you posted, the items that *could* be troublesome are the integrated sound and wireless devices, depending on the chipset they actually have. Give the Live CD a try; if you encounter compatibility problems, they could be solved during installation or after you have it installed.

And we'll be here to help you. :)

---

### Post by zeehat on 2007-08-14
Ok, I have that already downloaded.  That was the file I got.  [Standard personal computer].  If I run that, all I have to do is set my CD drive to master, and run the CD?  Is it that simple?  It won't corrupt my Windows?   And if it works, does that mean everything is compatible?

---

### Post by Wim Sturkenboom on 2007-08-14
Go in BIOS and set boot sequence to boot from CD first. (you don't have to set CD to master). Windows is safe unless you do 'stupid' things. If it all works, you are OK. If it does not all work, you might still be OK as well. Your ATI card might not work perfectly with the live CD and the same might apply to your wireless card. The rest should be OK.

I'm not a big fan of live CDs for this purpose, but that's personal. Reasons:[LIST]
[*]do not give the full capabilities related to hardware
[*]fixes to get stuff working are not permanent
[/LIST]

I would create a bit of space (5GB will do, 10GB if you can miss it) on one of the drives for a new partition. Next use that to install Ubuntu and try. 

Note: Burn the CD at low speed and burn it as an image. After burning you should see a whole bunch of files on the CD, not one file.

---

### Post by p_quarles on 2007-08-14
> **zeehat said:**
> Ok, I have that already downloaded.  That was the file I got.  [Standard personal computer].  If I run that, all I have to do is set my CD drive to master, and run the CD?  Is it that simple?  It won't corrupt my Windows?   And if it works, does that mean everything is compatible?
Correct. The live CD runs on RAM, and does not change anything on your hard drive. If it works with all of your hardware, you have an easy installation ahead. If it doesn't, it will most likely still work, but with a few extra hassles. 

Yeah, it's that simple. Before you decide to install, though, you should go to Windows and defragment the hard drive twice. And back up any critical data to other media.

---

### Post by michaelramm on 2007-08-14
That is correct. The LiveCD does not touch the hard drive.

I think that you are going to need the IDE hard drive. I don't think that SATA drives play very nice with linux (at least that is what I always heard).

I am also new to ubuntu and linux, so I feel your hesitations and anxiety.

Michael

---

### Post by p_quarles on 2007-08-14
> **michaelramm said:**
> That is correct. The LiveCD does not touch the hard drive.

I think that you are going to need the IDE hard drive. I don't think that SATA drives play very nice with linux (at least that is what I always heard).

I am also new to ubuntu and linux, so I feel your hesitations and anxiety.

Michael
Dunno where you heard that, but SATA drives work just fine with Linux. The current version of Ubuntu actually *assumes *that your HDD is a SATA.

---

### Post by zeehat on 2007-08-14
It won't even boot the CD.  I worked with the bios, and the black screen comes up where it basically says "loading CD", then it skips it, and goes straight to the windows gui.  What did I do wrong?

---

### Post by misfitpierce on 2007-08-14
Correct as said it runs from CD drive and uses ram I believe. It will not install anything to corrupt your windows data and will let you preview from disc. READ: Keep in mind that while on live CD you may notice it being slow. Ubuntu and other linux are not this slow just remember that your running the OS from a disc in your drive :) lol

---

### Post by steve-shinn on 2007-08-14
> **zeehat said:**
> It won't even boot the CD.  I worked with the bios, and the black screen comes up where it basically says "loading CD", then it skips it, and goes straight to the windows gui.  What did I do wrong?

Did you run a checksum on the cd after you burned it .... as it sounds like a problem with the download or burn process.

---

### Post by BaffledMollusc on 2007-08-14
> **zeehat said:**
> It won't even boot the CD.  I worked with the bios, and the black screen comes up where it basically says "loading CD", then it skips it, and goes straight to the windows gui.  What did I do wrong?

The Live CD file you download is an ISO, i.e. an image file. You have burn it as an image file to your CD; you can't just copy the file onto the CD and have it work.

Most CD burning software has an option like "burn image" somewhere.

Regarding your hardware - it should all work fine, with the possible exception of the on-board wireless. That will depend on what type of wireless chip it is.

---

### Post by zeehat on 2007-08-14
Yup, I think I figured it out.  I burnt it as data, not an image.  I am getting Nero now, to burn it as an image.  I don't know why it wouldn't go to the live CD as data.  Is there a reason why it only boots, if you burnt it as an image ?

---

### Post by zeehat on 2007-08-14
It's actually not wireless.  I use ethernet in the LAN port going 100mb/ps, if that makes a difference.

---

### Post by RomeReactor on 2007-08-14
> **zeehat said:**
> Yup, I think I figured it out.  I burnt it as data, not an image.  I am getting Nero now, to burn it as an image.  I don't know why it wouldn't go to the live CD as data.  Is there a reason why it only boots, if you burnt it as an image ?

That's because burning it as data, you are essentially copying the image itself to the CD, so you end up with one big file there (the image); if you burn it as an image, it creates many files and folders necessary to boot and/or install.

> It's actually not wireless. I use ethernet in the LAN port going 100mb/ps, if that makes a difference.

In that case, if you have the LAN cable connected, Ubuntu will pick up the connection and enable it, so you should have internet working once it boots.

---

### Post by BaffledMollusc on 2007-08-14
> **zeehat said:**
> It's actually not wireless.  I use ethernet in the LAN port going 100mb/ps, if that makes a difference.
Oh, okay. That should be fine. Ethernet is very well supported under linux.

Regarding the image thing: an image is a single file that describes what the final CD should look like, which can include multiple files and so on.

Edit: Oops, beaten to it!

---

### Post by zeehat on 2007-08-14
So even if I burn it as an image, if I choose to install it on a blank HD later, it will work?  And there should be no problems with my other drives right?  When it asks where to install I can just say Drive :F [or whatever one is the new blank one], and there should be no problem right?

---

### Post by zeehat on 2007-08-14
Also, approx. How long should it take to boot? [live CD, not installing it]

---

### Post by GerryB on 2007-08-14
[QUOTE=zeehat;3185776]Hi everyone, 

I am new to the boards, and to linux.  On my PC I am currently running Windows XP.  I would like to know if my hardware will be compatible with Ubuntu.  Any help is appreciated.  I downloaded Ubuntu to a CD already, and am awaiting install.  ....

If you get stuck, try this:
[http://ubuntuforums.org/showthread.php?t=498538&page=4](http://ubuntuforums.org/showthread.php?t=498538&page=4)
This utility seems to burn images at the right speed. I've used countless times with never a problem. Good luck!

---

### Post by RomeReactor on 2007-08-14
> **zeehat said:**
> So even if I burn it as an image, if I choose to install it on a blank HD later, it will work?  And there should be no problems with my other drives right?  When it asks where to install I can just say Drive :F [or whatever one is the new blank one], and there should be no problem right?

Yes, that's right. Just be absolutely sure that you choose the correct drive, so you don't overwrite windows. The Live CD is an installer also. When it boots, and you get to the desktop, you'll see an icon that says **Install Ubuntu** or something similar. Double-click it to begin the installation process, or leave it alone and just use Ubuntu from the Live CD.

As for how long it takes to boot from the Live CD, I'd say around 5 minutes or less, depending on your system specifications.

---

### Post by BaffledMollusc on 2007-08-14
> **zeehat said:**
> So even if I burn it as an image, if I choose to install it on a blank HD later, it will work?

Yes. The burning the image creates a CD that is both a Live CD and an installer. When you boot from the Live CD, you will actually be using Ubuntu as the OS (but it's running off the CD, not the hard drive, so it's *slow*). On the desktop when you boot into Ubuntu you'll see an icon labelled "install". Clicking on this will start the install process, should you wish to do so.
> 
 And there should be no problems with my other drives right?  When it asks where to install I can just say Drive :F [or whatever one is the new blank one], and there should be no problem right?
Ahh... kind of. In the install process you get to choose where to install Ubuntu. But you install to a partition, not a drive. The A: B: C: drives are a Windows convention labelling drives and partitions. What you'll have to do in the installer is select the hard disk you want to install to, create a partition on it, and install to that partition.

This is where you have to be careful you don't install to your windows partition, as this will destroy windows. Searching the forums and web for "linux dual boot" will probably throw up lots of helpful links.

---

### Post by zeehat on 2007-08-14
So in the installer, I can partition my new drive that I am buying?  And then install it to that partition?

---

### Post by zeehat on 2007-08-14
If it is a 160 GB drive, how should I partition it?  What size of partition.  And am I partitioning it for the Ubuntu boot?  Then the rest of the drive is for programs and anything else?

---

### Post by RomeReactor on 2007-08-14
If you plan on using only Ubuntu in that drive, you can select the **Guided Partitioning** option when it asks you, and then choose **Use Entire Hard Drive** (or something very similar). Then Ubuntu will take it from there.

---

### Post by steve-shinn on 2007-08-14
> **RomeReactor said:**
> If you plan on using only Ubuntu in that drive, you can select the **Guided Partitioning** option when it asks you, and then choose **Use Entire Hard Drive** (or something very similar). Then Ubuntu will take it from there.


Yep thats the way to go ..... :guitar:

---

### Post by RomeReactor on 2007-08-14
> **steve-shinn said:**
> Yep thats the way to go ..... :guitar:

Thanks for the confirmation, steve. Installed 64-bit feisty a week ago and I already forgot the process! :redface:

---

### Post by zeehat on 2007-08-14
Ok, I started a burn with Nero.  I couldn't find burn as image option, but the Ubuntu file said it was an image file, before the burn.  So I am burning that as it is.  Hopefully it will work.  If someone has experience with Nero, and knows what to do, please help.

---

### Post by RomeReactor on 2007-08-14
If you're having problems with Nero, you can try with the [program suggested by GerryB]("http://www.terabyteunlimited.com/downloads/burncdcc.zip"). Or with [InfraRecorder]("https://help.ubuntu.com/community/BurningIsoHowto").

---

### Post by zeehat on 2007-08-14
That didn't seem to work either.  Maybe I burnt it wrong again, or there is something wrong with my BIOS. I think it is set to, if there is a CD boot from it, if not boot with C: drive.  Because the boot from CD screen comes up, loads for a few seconds, and then loads the windows GUI.  Can someone help me burn an image file with Nero?

---

### Post by RomeReactor on 2007-08-14
Try [this]("http://www.wizardskeep.org/mainhall/tutor/neroiso.html").

---

### Post by zeehat on 2007-08-14
I used the burndcc instead.  I hope I can get it to work.  Thanks for all your help guys.

---

### Post by zeehat on 2007-08-14
This is awesome! I am posting from the Ubuntu via Live CD!  I am gonna get my hard drive and install it. :D  I want to know will it be exactly like this when I install it, or will I need to install some of the applications and such.  Because as of now, everything that I have tried just works. :D:D:D:D

---

### Post by RomeReactor on 2007-08-14
Most likely everything will work just as well it does now, only faster; you'll get the same applications you see there now, plus be able to install tons more. You'll also be able to install drivers for your video card (if it's Intel, ATi or nVidia) so you get 3D acceleration.

---

### Post by p_quarles on 2007-08-14
The only application that's on the installation disk that's not on the installed system is gparted. Everything else is installed automatically. And it will be significantly faster once it's installed in the hard disk.

---

### Post by zeehat on 2007-08-14
Would it be ok, if I installed Ubuntu on an old 10 GB drive?  Just for the boot.  Would I be able to use the same drive for storage, that I do for Windows?  I am not able to get that new drive right now, and I really want to install this amazing OS.  Thanks.

---

### Post by RomeReactor on 2007-08-14
Yes, you can. If the storage drive is NTFS you'll need to install a package called **ntfs-3g** in order to be able to write to that drive. If it's FAT32, then Ubuntu already has that capability.

---

### Post by zeehat on 2007-08-14
I was planning to, from the Live CD, just write over it.  Wouldn't I need to choose the HD format then?  It's only 10 GB so I assume it would be FAT32.  Or is it harder than just writing over the old drive, to use it as an Ubuntu boot.

---

### Post by RomeReactor on 2007-08-14
> **zeehat said:**
> I was planning to, from the Live CD, just write over it.  Wouldn't I need to choose the HD format then?  It's only 10 GB so I assume it would be FAT32.  Or is it harder than just writing over the old drive, to use it as an Ubuntu boot.

I understood what you said as:

Drive 1: windows
Drive 2: storage
Drive 3: Ubuntu

The 10 GB drive will only have Ubuntu, correct? If so, the installation will be pretty straightforward.

---

### Post by zeehat on 2007-08-14
Yes, that is how it will be.  I want to know can I store Ubuntu files or any downloads I do in Ubuntu, to the Storage Drive?  10 GB can not go too far. :(  I figured then the 10 GB will just be Ubuntu and necessary programs.  After that it's just my own preferential programs and such.  If I have a program saved in the Storage drive will it still work?  Sorry for all the questions.

---

### Post by RomeReactor on 2007-08-14
Yes, you can use that storage-only drive for your downloads or personal documents/files. If, as you say, the Ubuntu drive will only have the OS and any programs you decide to install later on, I think 10 GB should be more than enough.

If your storage drive is ntfs, hopefully someone will comment on how stable ntfs-3g is; personally, I haven't used it.

---

