---
title: "Advice on installing Ubuntu on older Macbook with OSX 10.6.8"
date: 2017-04-24
forum: Apple Hardware Users
---

### Post by themusicman on 2017-04-24
Hi All

Totally new to Ubuntu and Linux, but really wanting to set up an old Macbook I have and install Ubuntu on it.

So, I have an old Macbook 2GHz Core 2 Duo running OSX 10.6.8, 1GB RAM, that works pretty well, but I am after some expert advice on how to install Ubuntu (*dual boot or default*), and which version of Ubuntu it will be best to use on a machine of this spec.

The Ubuntu requirement I have is really just for my own general learning, but I would also like to use it for IoT stuff.  I have an several Arduinos and ESP8266's, so would love to be able to run these apps using it - maybe using it instead of using my MacbookPro - who knows? I guess it depends on the performance of Ubuntu on this older Macbook.

I have seen some Youtube vids where people have installed Ubuntu on older Macbooks, and they report that are delighted with the performance, often saying that the Macbook has a new lease of life!  Sounds great to me!

So folks, the questions I have are:

1. Which version of Ubuntu should I install on this machine? I'd like the latest if possible, but appreciate this might not be possible given the age of my Macbook.  Advice needed.
2. Should I create a dual boot version using USB, or would it be best to install Ubuntu as the default OS on this macbook? (*i.e. and not have OSx on this machine*)

Looking forward to reading your advice and hoping the machine I have can be put to good use!

Thanks all
John

---

### Post by howefield on 2017-04-24
Thread moved to the "*Apple Hardware Users*" forum.

---

### Post by LastDino on 2017-04-24
Hello there,

I don't have Mac experience but I've lot of old hardware experience, bit too similar one that to your hardware
For Q.1
I would suggest using Xubuntu LTS release 16.04 Xenial Xerus

Why? Because although you're okay on processor side, you're lacking on RAM side. You should at least have 2 Gigs for Flagship Ubuntu.

Xubuntu is Ubuntu without its bells and whistles, so you should be able to do all that you could with your Ubuntu

For Q.2
I would start with dual boot. 

Why: It helps to preserve your machine when you're in learning stage and be at your disposal when you need it for any kind of serious work, also, troubleshooting can be easier.

I would start telling you on process but I don't have any mac experience with dual booting, so I'll wait for someone to come along.

Alternatively, if bit too curious, I'm sure if you googled you will find plenty of Mac dual booting guides with Ubuntu/Linux, you can start with it.

---

### Post by themusicman on 2017-04-24
Hi - thanks for the prompt reply... you know what us geeks are like! I am impatient to get it installed... :)

So, are all 'flavours' of Ubuntu pretty much the same and what you can do on one you can do on another?

---

### Post by LastDino on 2017-04-24
> **themusicman said:**
> Hi - thanks for the prompt reply... you know what us geeks are like! I am impatient to get it installed... :)

So, are all 'flavours' of Ubuntu pretty much the same and what you can do on one you can do on another?

You can install and tweak packages to your needs as much as you want with any flavor. That is the basic benefit of Linux in general.

I wont go as calling them same as their purpose decides how they are tbh.

For example, you can even install Lubuntu and which is barebones and start to put together pieces to  build your desired desktop. You can even build something new, just based on Ubuntu. Possibilities are limitless. 

But for a starter, there are things to consider, like;

1. Is it long term support version which is well tested? (LTS versions are)
2. Too much tweaking  can create conflicts with updates/package management
3. How much time should be available from me to put in this curiosity of mine
4. Is the machine spare or I need it to actually work sometimes for serious work
etc

My advice would be to start with standard Xubuntu and learn basics, then basic commands, then try tweaks and learn as you experience many problems (if you're lucky, you know what I mean :P )

---

### Post by themusicman on 2017-04-24
> **LastDino said:**
> You can install and tweak packages to your needs as much as you want with any flavor. That is the basic benefit of Linux in general.

...

My advice would be to start with standard Xubuntu and learn basics, then basic commands, then try tweaks and learn as you experience many problems (if you're lucky, you know what I mean :P )
Great advice there, thanks! I think you've helped me decide.

Dual boot Xubuntu it is!:D

---

### Post by LastDino on 2017-04-24
Don't forget to check compatibility, like x64 or x86. And download from official torrent link, that keeps the chances of ISO getting damaged during download to its minimum.

---

### Post by themusicman on 2017-04-24
Yep, that's the first thing I checked after I replied.  My Macbook is 32-bit, so am now downloading the 32-bit version of Xubuntu from the Xubuntu download page via torrent (which is the way they advise).

Thanks for the help, you're a star!

---

### Post by LastDino on 2017-04-24
We all started somewhere...

Also, almost forgot but backups!

---

### Post by themusicman on 2017-04-24
> **LastDino said:**
> We all started somewhere...

Also, almost forgot but backups!

I use Time Machine! :)

One note... reading the detail on if my Macbook is 32 or 64 bit, advice is...

If it is a Core 2 - then it's a 32-bit and if it's a Core 2 Duo then it's a 64-bit.  Mine is a Core 2 Duo, so i assumed 64-bit, but another test someone suggests to do is look at an entry in system profiler and that suggests it is 32-bit.  hence downloading the 32 bit version... will this be an issue do you think?

---

### Post by LastDino on 2017-04-24
Why would you want to install 32 bit on 64 bit capable machine? 

That would limit your hardware potential. IF it is x64, go with x64 only.

Though, to find answer to that IF would require some digging on your part. Sorry, like I said, no experience with Mac. But I'm assuming since it is Intel chip, probably x64.

---

### Post by themusicman on 2017-04-24
> **LastDino said:**
> Why would you want to install 32 bit on 64 bit capable machine? 

That would limit your hardware potential. IF it is x64, go with x64 only.

Though, to find answer to that IF would require some digging on your part. Sorry, like I said, no experience with Mac. But I'm assuming since it is Intel chip, probably x64.

Totally agree with you, but I am a tad confused as to if I actually am capable of running 64-bit apps.  Doing some research, some of the tests I have done suggest my machine is 32-bit capable, but others (at the Terminal) suggest it isn't!

Therefore opting for the safer bet!

---

### Post by LastDino on 2017-04-24
What I'm thinking is that your processor may be x64 capable, meaning you can install x64 OS. But the kernel that is your OSX is utilizing is only x32, therefor some results show it x32 but some have it pegged as x64

If this is the case, I'm fairly certain that you can run x64 Xubuntu, as it will install its own kernel supporting the processor architecture.

---

### Post by themusicman on 2017-04-24
> **LastDino said:**
> What I'm thinking is that your processor may be x64 capable, meaning you can install x64 OS. But the kernel that is your OSX is utilizing is only x32, therefor some results show it x32 but some have it pegged as x64

If this is the case, I'm fairly certain that you can run x64 Xubuntu, as it will install its own kernel supporting the processor architecture.

OK... in which case I will download the 64-bit version. I guess if it fails or doesn't work as it should, I can then use the 32-bit version.

Thanks again, appreciate your help and prompt answers.

---

### Post by LastDino on 2017-04-24
Oh no problem, I guess your adventure started even before you actually got around to start the installation. 

Even I learned something new, so we both got something out of it. Do post the results, as I would also like to get answer to my hunch

Also, read bit about Linux partitioning wizard "Gparted" in this case and types of partitions. If you understand this part, you can probably install any Linux around with graphical installer

---

### Post by mörgæs on 2017-04-24
With 1 GB of memory there is not much difference between 32 and 64 bit. Actually the former might be fastest.

---

### Post by themusicman on 2017-04-24
> **LastDino said:**
> Oh no problem, I guess your adventure started even before you actually got around to start the installation. 

Even I learned something new, so we both got something out of it. Do post the results, as I would also like to get answer to my hunch

Also, read bit about Linux partitioning wizard "Gparted" in this case and types of partitions. If you understand this part, you can probably install any Linux around with graphical installer

Ha... you nearly had me there! I was about to download and install Gparted on my Mac... alas... I will need to download the Ubuntu version when that is installed, eh!:P

---

### Post by LastDino on 2017-04-24
You will see Gparted during installation only, as you will see this window

[ATTACH=CONFIG]274742[/ATTACH]

Here usually I  select "something else" and then after you will need knowledge of Gparted and linux partitions while dual booting, as a mistake here may erase all your HD.

Note: This may vary for Mac OS, as apparently it does from what I saw somwhere

---

### Post by themusicman on 2017-04-24
> **LastDino said:**
> You will see Gparted during installation only, as you will see this window
[spoiler]
[IMG]https://www.dizwell.com/wordpress/wp-content/uploads/2017/01/VirtualBox_Ubuntu-1610_18_01_2017_20_10_20.png[/IMG]

[/spoiler]


Ahh, so I choose option 3 there then? As I see no specific 'dual boot' option?

Progress so far: downloaded Xubuntu on my MacBookPro - copied to USB - copied to Macbook - didn't work!!! Said no mountable volume.  SO had to download Transmission onto Macbook, and am now downloading Xubuntu 64-bit on that.  Then I start the install!

---

### Post by LastDino on 2017-04-24
Again, process may differ on Mac, so find Mac specific tutorials. Or wait for someone to help you here. I can only help you till this much :(

Videos like this may help
[https://www.youtube.com/watch?v=IQIaDO9nR6Y](https://www.youtube.com/watch?v=IQIaDO9nR6Y)

---

### Post by themusicman on 2017-04-24
> **LastDino said:**
> Again, process may differ on Mac, so find Mac specific tutorials. Or wait for someone to help you here. I can only help you till this much :(

Videos like this may help
[https://www.youtube.com/watch?v=IQIaDO9nR6Y](https://www.youtube.com/watch?v=IQIaDO9nR6Y)

Please excuse my ignorance... that video is for Ubuntu, rather than Xubuntu! So, are the insall processes the same for each flavour of Ubuntu?

---

### Post by LastDino on 2017-04-24
> **themusicman said:**
> Please excuse my ignorance... that video is for Ubuntu, rather than Xubuntu! So, are the insall processes the same for each flavour of Ubuntu?

Yeah, installation process will be not varying other than you seeing Xubuntu logo and info from Ubuntu. At least doesn't for me when I install it on WIndows dual boots

---

### Post by themusicman on 2017-04-24
> **LastDino said:**
> Yeah, installation process will be not varying other than you seeing Xubuntu logo and info

Awesome... again, sorry for the noobie questions! (what chance do I stand with Linux eh!!) haha

I am wondering with the install file I downloaded, it is an ISO file.  Mountable files on a Mac are usually DMG.  Also, I couldn't see anywhere on Xubuntu www site to differentiate for downloads for Mac and Win so I downloaded the one presented to me.  I wonder if that's the issue here?

---

### Post by LastDino on 2017-04-24
You have to create bootable USB/Media. Not directly mount.

Here is how 

[https://www.ubuntu.com/download/desktop/create-a-usb-stick-on-macos](https://www.ubuntu.com/download/desktop/create-a-usb-stick-on-macos)

Also, this is one more guide I found 

[https://www.howtogeek.com/187410/how-to-install-and-dual-boot-linux-on-a-mac/](https://www.howtogeek.com/187410/how-to-install-and-dual-boot-linux-on-a-mac/)

It has all the info you may need, things beyond this are bit out of my scope too as they may be mac specific.

---

### Post by themusicman on 2017-04-24
I feel bad!!! :)

I am trying, honestly hahaha!!!

Thanks again! Onto it now.

---

### Post by themusicman on 2017-04-24
Bugger! Now I am getting 'unetbootin quit unexpectedly' error on the Macbook. I wonder if I should create the USB bootable disc using my MBPro? Safe/not safe?

---

### Post by LastDino on 2017-04-24
That video I posted also has different method, have you tried that?

---

### Post by themusicman on 2017-04-24
> **LastDino said:**
> That video I posted also has different method, have you tried that?

Doing it now! USB drive being created as we speak!!

Progress... ;)

---

### Post by LastDino on 2017-04-24
Watch that video carefully, as it might be able to help more. 

Keep up the good job!

---

### Post by themusicman on 2017-04-24
> **LastDino said:**
> Watch that video carefully, as it might be able to help more. 

Keep up the good job!

Even more progress... USB drive created and in process of installing.

However, I am at the stage where you posted the screenshot earlier.  Do I tick the 3rd option "Use LVM with the new Xubuntu installation" ? Will this allow me to dual boot?

Not a huge issue if not, as I have an OSX boot USB.

---

### Post by themusicman on 2017-04-24
Hmmm, I see it'snot that option, there's a 'Do something else' option, which I selected.  now to try to fathom out how to create a dual boot!

---

### Post by LastDino on 2017-04-24
No no, not LVM, show me exactly what u see.

And this part is also covered in Video..

Edit: Yes, usually something else. Please the Video.

<I feel that is all I'm saying lately.lol

---

### Post by themusicman on 2017-04-24
> **LastDino said:**
> No no, not LVM, show me exactly what u see.

And this part is also covered in Video..

Edit: Yes, usually something else. Please the Video.

<I feel that is all I'm saying lately.lol

OK, I waited :) Just taking screenpic now and will post asap

---

### Post by themusicman on 2017-04-24
Here's the Screenshot I am faced with...

Watching Video in background... :)
[ATTACH=CONFIG]274743[/ATTACH]

---

### Post by themusicman on 2017-04-24
Drat... I missed the step for creating another partition for Xubuntu to reside!!!

Will quit this, do that, and start again.

---

### Post by LastDino on 2017-04-24
Okay, firstly

Please post Img as attachment to avoid it capturing so much space

Now to business,
Here you should select "Something else"

Did you make use of DIsk Utility when you were using Mac to create partition? see vid @4:36

If yes, then proceed according to the vid @7:31

Edit: Looks like you realized that before me posting

---

### Post by themusicman on 2017-04-24
Ahh, sorry about the image... will post an attachment from now on!

Yep, you've nailed it, that's the step I skipped!  Onto it!

---

### Post by themusicman on 2017-04-24
BOOM!!! All installed, and thanks so much for your help and pointers, invaluable. Thank you.

Now though, I can't seem to locate any WiFi spots.  Pressing on.... :)

---

### Post by LastDino on 2017-04-24
No, no thanks to you. I also learned something new.

So, x64 was successful? 

 Though, like someone said, you wont see much difference from x32 as you've only 1 gig Ram, but it's okay.

I suggest marking this thread as solved and making new thread for your Wifi issue, otherwise people wont know that it is different problem.

Welcome to Ubuntu family

Regards

---

### Post by themusicman on 2017-04-24
> **LastDino said:**
> No, no thanks to you. I also learned something new.

So, x64 was successful? 

 Though, like someone said, you wont see much difference from x32 as you've only 1 gig Ram, but it's okay.

I suggest marking this thread as solved and making new thread for your Wifi issue, otherwise people wont know that it is different problem.

Welcome to Ubuntu family

Regards

Yep, x64 successful, Xubuntu runs very effectively actually! (apart from the WiFi).

Yep - I already posted a new thread on that issue, but good point re marking this thread as SOLVED.  Shall do so straight away.

Thanks again for your help... you really did help me push this forward at an accelerated rate :)

---

