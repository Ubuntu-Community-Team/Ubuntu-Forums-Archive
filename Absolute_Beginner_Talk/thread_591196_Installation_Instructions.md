---
title: "Installation Instructions"
date: 2007-10-25
forum: Absolute Beginner Talk
---

### Post by birtley on 2007-10-25
I decided to try Ubuntu after reading about it in a newspaper article and after becoming dienchanted with Windows. I have downloaded the file and burned a CD. I have a CD with a file 'ubuntu-7.10 desktop-386.iso.'
Now what? I can't find any instructions for what to do next, despite searching all over the place. Have I missed something obvious? Wouldn't it be useful to include a text file with the download for beginners ob how to proceed?

---

### Post by stump138 on 2007-10-25
Make sure that you burn the cd from an "image" file and not a data cd, then pop it in the cd tray, reboot, and enjoy :)

---

### Post by slibuntu on 2007-10-25
> **birtley said:**
> I decided to try Ubuntu after reading about it in a newspaper article and after becoming dienchanted with Windows. I have downloaded the file and burned a CD. I have a CD with a file 'ubuntu-7.10 desktop-386.iso.'
Now what? I can't find any instructions for what to do next, despite searching all over the place. Have I missed something obvious? Wouldn't it be useful to include a text file with the download for beginners ob how to proceed?

I made this very same mistake before, what you've done is simple burned the file onto a CD, which won't work, what you need to do is burn an image CD, most burning programmes provide this option, if you can't figure it out, post here and tell me what burning program you are using and i'll try and help

Once the image cd is ready, reboot your pc with the cd inside, and on most pc's Ubuntu will boot automatically, if it doesn't, reboot your computer, and enter setup mode, usually by pressing f2 of f12 as the computer boots. Now change the boot sequence in the setup mode, so that the cd drive boots before the internal harddrive, reboot and you're away!

---

### Post by birtley on 2007-10-25
Could you explain what you mean by 'burn from an image file'? I burned the CD from the file that I downloaded. I chose the ISO option for the CD forma. Is that OK?

---

### Post by kellemes on 2007-10-25
[https://help.ubuntu.com/community/BurningIsoHowto?highlight=%28iso%29]("https://help.ubuntu.com/community/BurningIsoHowto?highlight=%28iso%29")

---

### Post by birtley on 2007-10-25
> **slibuntu said:**
> I made this very same mistake before, what you've done is simple burned the file onto a CD, which won't work, what you need to do is burn an image CD, most burning programmes provide this option, if you can't figure it out, post here and tell me what burning program you are using and i'll try and help

Once the image cd is ready, reboot your pc with the cd inside, and on most pc's Ubuntu will boot automatically, if it doesn't, reboot your computer, and enter setup mode, usually by pressing f2 of f12 as the computer boots. Now change the boot sequence in the setup mode, so that the cd drive boots before the internal harddrive, reboot and you're away!

Ah! I think that I have found the option in Nero to burn as an image file and I am burning it as I write. Thanks!

---

### Post by slibuntu on 2007-10-25
Hope it works swimmingly for you! Welcome to the wonderful world of Ubuntu, and if you run into trouble, there are always plenty of people on here willing to help. Also, take a look at my blog, it's got all the stuff i had to spend ages looking for when i started using Ubuntu! :)

---

### Post by birtley on 2007-10-25
> **slibuntu said:**
> Hope it works swimmingly for you! Welcome to the wonderful world of Ubuntu, and if you run into trouble, there are always plenty of people on here willing to help. Also, take a look at my blog, it's got all the stuff i had to spend ages looking for when i started using Ubuntu! :)

Thanks, I will look at your blog. I have burned the image file and have checked it for errors and it passed. I have been looking at the ubuntu interface and I like it. I haven't installed it yet, but I will do as soon as I have backed up my files.
I don't want Windows XP,that is on my disk now. Should I uninstall it and reformat the disk before installing ubuntu?

---

### Post by forestpixie on 2007-10-25
if you're COMPLETELY sure that you won't be putting windows back on - when it gets to the partition stage of the install - choose use the whole disc. It's easier to leave windows on if you're not sure.

If you're not sure, I'd dual boot - I did to start with - as do many, many on here. Games are a problem at the moment.

If you decide to dual boot have a look at these 2 pages
[http://www.psychocats.net/ubuntu/installing](http://www.psychocats.net/ubuntu/installing)
[https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot)

There's much more about to look at and I'm sure you'll get other replies

Good luck

---

### Post by birtley on 2007-10-26
> **forestpixie said:**
> if you're COMPLETELY sure that you won't be putting windows back on - when it gets to the partition stage of the install - choose use the whole disc. It's easier to leave windows on if you're not sure.

If you're not sure, I'd dual boot - I did to start with - as do many, many on here. Games are a problem at the moment.

If you decide to dual boot have a look at these 2 pages
[http://www.psychocats.net/ubuntu/installing](http://www.psychocats.net/ubuntu/installing)
[https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot)

There's much more about to look at and I'm sure you'll get other replies

Good luck

Thanks, perhaps I will dual boot. I have two hard disks. would I need to partition the second disk between Windows and Ubuntu? Are files the Windows partition visible in Ubuntu? I presume that the file format is completely different so files created in Windows couln't be edited in Ubuntu.

---

### Post by forestpixie on 2007-10-26
You first need to defrag you're windows install a couple of times. Then decide on how much room you're going to give ubuntu for it's partition. When I dual booted I had windows on a 30Gb partition with it's programs, Ubuntu on a 30Gb partition and 20Gb data - which was music, I also had a separate 80Gb with music and movies on to give you an idea.

Once you're ready start the livecd - make sure you're hardware is working with it, then once you start the install you'll get to the partition part of the install - what you'll be needing to do is resize you're original win partition to give Ubuntu some room - then you install to the newly created free space.

It will recognise you're win partition and any other NTFS partitions - once you're running in Ubuntu you'll be able to access you're NTFS files as read only (although I think maybe gutsy has read/write as default not too sure ) - you can install read/write later.

You can also install a package in windows that'll access you're linux files - 

Make sure you backup anything you don't want to lose.

when you are actually installing - if you're not sure about anything - assuming that you've not got a problem getting online you will be able to run firefox, so will be able to ask the question.

Bit of a tome - but if you've any questions ask now before it's too late 

Good luck

---

### Post by birtley on 2007-10-26
It's beginning to make sense. I now realise it would not be sensible to switch from Windows completely until I am sure that all my hardware works with Ubuntu. I have a second PII 233Mhz machine running on Windows ME. I wonder if it would run Ubuntu so I could try it out without changing anything on my main computer? I have tried to install it but it doesn't have an option to boot from the CD. Is there an easy way around this problem?

---

### Post by petegreenhorn on 2007-10-26
yes boot the live version and when it finishes loading click on the install icon on the desktop

---

