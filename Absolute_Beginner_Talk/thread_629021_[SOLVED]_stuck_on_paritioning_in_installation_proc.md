---
title: "[SOLVED] stuck on paritioning in installation process (wanting dual boot)"
date: 2007-12-01
forum: Absolute Beginner Talk
---

### Post by Mythology on 2007-12-01
[IMG]http://picasaweb.google.com/momochan86/ScreenshotPartition/photo#5139206918536382722[/IMG]

I just burned my Ubuntu 7.10 cd and have been playing around on the desktop from the cd. I am trying to figure out the next step in "partitioning." Above is where I am stuck (I took a screenshot.) 

I would like to figure out which one of these are my C:\ drive. How can I tell?

I've been told I need to resize it.. or make ext3 partition in C? :confused:

Can someone please tell me the steps to finish installing this onto my C:\ drive so I can stop using the CD?

---

### Post by overdrank on 2007-12-01
> **Mythology said:**
> [IMG]http://picasaweb.google.com/momochan86/ScreenshotPartition/photo#5139206918536382722[/IMG]

I just burned my Ubuntu 7.10 cd and have been playing around on the desktop from the cd. I am trying to figure out the next step in "partitioning." Above is where I am stuck (I took a screenshot.) 

I would like to figure out which one of these are my C:\ drive. How can I tell?

I've been told I need to resize it.. or make ext3 partition in C? :confused:

Can someone please tell me the steps to finish installing this onto my C:\ drive so I can stop using the CD?

Hi and welcome maybe this link will help
[http://www.psychocats.net/ubuntu/installing](http://www.psychocats.net/ubuntu/installing)

---

### Post by Mythology on 2007-12-01
PS: I just noticed that I couldn't see the picture I attatched above so if you can't see the picture above here's what it is:

It shows the partition step in the installation process
and listed below are the follow:
                                                 size              used
/dev/sda
/dev/sda1   ntfs     /media/sd1     5379MB     4700 MB
/dev/sda2   ntfs     /media/sd2     16113MB    12500MB
/dev/sda5   ntfs    /media/sd5     18498MB     337MB
freespace                                 8MB

---

### Post by Mythology on 2007-12-01
> **overdrank said:**
> Hi and welcome maybe this link will help
[http://www.psychocats.net/ubuntu/installing](http://www.psychocats.net/ubuntu/installing)

Thats a great link. Im looking at it right now. I guess I will be using the first option... a friend of mine told me to select MANUAL but its way too confusing! 

I'll report back after I try it!

---

### Post by overdrank on 2007-12-01
> **Mythology said:**
> Thats a great link. Im looking at it right now. I guess I will be using the first option... a friend of mine told me to select MANUAL but its way too confusing! 

I'll report back after I try it!

Hi and please before you do anything **_BACK UP your data_**. Then after researching to partition you drive if you are still unsure please ask questions and post a screen shot. It is not a mistake until DATA it gone!

---

### Post by Mythology on 2007-12-01
Hmmm I tried to Guided partitioning (the first option)
But about 3 seconds in I got a popup window that read:

> 
An error occured while writing the changes to the storage devices.

The resize operation is aborted.

PS: were you able to see the picture I posted in the first post?? I can not see it... but I put it there in the IMG tags.

---

### Post by overdrank on 2007-12-01
> **Mythology said:**
> Hmmm I tried to Guided partitioning (the first option)
But about 3 seconds in I got a popup window that read:



PS: were you able to see the picture I posted in the first post?? I can not see it... but I put it there in the IMG tags.

Hi and no screen shot was attached. You may want to defrag windows a time or time also before attempting the installation. Another thing you may look out for is make sure the partitions you are trying to resize are not mounted. :)

---

### Post by Mythology on 2007-12-01
Defragmenting Windows would do what? Get rid of the 2 harddrives I have making it one larger hardrive?

Here's what I have on my computer:

C:\   free  4.72 GB
       total 15.0 GB
^^apparently 4GB is not enough space. Can I manually SELECT ALL and COPY into D:\ ? So I'll have almost 15 GB freed up for Ubuntu purposes! (Because if Windows crashes, D drive is always left intact.)

D:\   free 15.2
       total 17.2 GB

How do I know if the partitions are mounted? I think they are... Isn't that the " \ " ?
I just don't understant why there are three partitions listed (sd1, sd2, and sd5)?

---

### Post by Mythology on 2007-12-01
found a website explaining it: [http://www.geekgirls.com/windows_defrag.htm](http://www.geekgirls.com/windows_defrag.htm)

I'll do this first and come back on here, Hopefully I'll get this thing up and running by the end of the week! :p

---

### Post by Mythology on 2007-12-02
I defraged and disconnected outside harddrives... 
Installation worked... sorta

I'm still on the Install screen. It shows as 100% completed! (yay)
On the bottom is says "Copying installation logs."
BUT...It's been frozen on that little screen for 20 minutes now. Is this usual? What should I do?

---

### Post by hogwartsnigel on 2007-12-02
Myth,
Don't panic, as long as you backed everything up there really isn't anything you can't recover from.
I am a little cavalier and would assume the installation was indeed completed, and would restart..making sure to remove the disc.
I installed my first Linux distro only a month ago and one really reassuring thing is the live cd and a thing you can download called the super grub disc can just about rescue everything.

Keep us posted, if turning your machine off sounds too. gung ho! just wait these forums are full of Yodas just bursting to help.

Nigel

---

### Post by hogwartsnigel on 2007-12-02
Myth, you definately have 2 seperate hard drives? Not just a single hard drive partitioned yes?

Nigel

---

### Post by Mythology on 2007-12-02
Right after posting my last post I got impation (after half an hour of staring at the "100% complete")...and I shut the computer off, took cd out, and turned computer back on....

LOOKS LIKE A SUCCESS! 

I had a list of options to choosed from Ubuntu or Windows XP... and now I'm on Ubuntu with out the CD!

Very cool! 

The funny thing is there were 93 updates! :p

Thank you to everyone that helped. I'd still be ripping out my hair if it weren't for your help.

---

### Post by hogwartsnigel on 2007-12-02
Cool,
Mythology and welcome. If your experience is like mine you'll go from trepadation to just pure love for Ubuntu, stick with it and learn as much as you can. The guys on this forum rock and you never feel as if your on your own. The live disc and that super Grub Disc are great for when you want to experiment though.
Have Fun and if your happy with everything mark this as solved.

Nigel

---

