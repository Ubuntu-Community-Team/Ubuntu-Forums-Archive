---
title: "You said Beginner..."
date: 2007-09-15
forum: Absolute Beginner Talk
---

### Post by DJ_OB1 on 2007-09-15
ok, I am totally the new guy to this.  I have heard of Linux and I know it is a seperate operating system and that is about all I know.  Here are my VERY beginner questions.

Does DL'ing this and using wipe out/replace windows?
Can I use both Windows and Ubuntu?  Would I need 2 hard drives to do that?
If I use it what happens to all my programs I already have?
What are the advantages of Ubuntu, why switch?

---

### Post by danny joe ritchie on 2007-09-15
Yes , you can use both, until you decide which one you want too keep!

---

### Post by danny joe ritchie on 2007-09-15
No, you do not need two hard drives to use Ubuntu , you can install it on the same one!

---

### Post by rsambuca on 2007-09-15
> **DJ_OB1 said:**
> ok, I am totally the new guy to this.  I have heard of Linux and I know it is a seperate operating system and that is about all I know.  Here are my VERY beginner questions.

Does DL'ing this and using wipe out/replace windows?
Can I use both Windows and Ubuntu?  Would I need 2 hard drives to do that?
If I use it what happens to all my programs I already have?
What are the advantages of Ubuntu, why switch?

I suggest that you download the Ubuntu LiveCD and see for yourself.  The liveCD loads itself into your system ram, so it will not touch your hard drive or existing Windows installation in any way.  

You will then get a feel for what ubuntu does and can offer you.  There are many different open source programs that will take care of your regular computing needs.  Just keep in mind that the liveCD will run much slower than if it were actually installed onto your hard drive.

After a while, if you like Ubuntu, you can install it onto a new partition on your existing hard drive and do what is known as a dual boot.  When you turn your computer on there will be an option screen (called grub) where you choose which OS you want to boot up.

---

### Post by lisati on 2007-09-15
Different things suit different people...

It is possible to have both Windows and Ubuntu on the same computer without the need for a second disk drive - a common way of doing this is through a process called "dual booting", where, once everything's installed, you are given a choice of which to run when you "boot" your computer.

Have a "play" with a LiveCD, which won't install anything unless you tell it to. This way, you'll be able to get an idea if Ubuntu (or any other OS) meets your needs.

If you decide to install, it's a good idea to make a backup of important data, just in case - mixups can (and do) happen.

---

### Post by VraiChevalier on 2007-09-15
> **DJ_OB1 said:**
> 
What are the advantages of Ubuntu, why switch?

I had the same sort of questions not too long ago. It took me a while to fully appreciate what "Free/Open Source" software truly means but I would say that is the primary reason to actually switch.

Free as in freedom. Freedom of choice.

---

### Post by voided3 on 2007-09-15
Hello and welcome. If you would like to dual boot your computer w/ Windows and Ubuntu, first off all you are going to need to download a disk image .ISO of Ubuntu and you'll need to write the image to disk with a program like Nero or CD Burner XP Pro (make sure you write it as an image and not a data disk). 

Before I go further though, what kind of system are you running? The most important thing is that you at least 256mb of RAM installed. You can check this in Windows by right clicking on My Computer, then go to properties and it should say it right there. I recommend you have 512mb RAM or more installed, but 256mb or more is fine. Also make sure you have enough free hard drive space; you are installing a whole other operating system so you'll need to make sure you have room. I recommend you have at least 8 or 10 GB.

Next, you need to boot your computer off of the CD. Depending on what kind of computer you have, you can go about this a few different ways. If you have a manufactured computer like a Dell, HP, Compaq, etc. you can consult the company's website to find which key you need to press when you power up the computer. Usually for any computer it will be one of the function (F1-F12) keys or the delete key. This will either bring you into BIOS or a boot menu. If it is BIOS, look for something that looks like "Standard CMOS Setup" and look for "boot sequence" (this may be under another menu as well, so look around for it and set it as per the on screen instructions, making sure to save and exit). If you get a boot menu, just select your CDROM. 

At this point, your computer will be loading the entire operating system into RAM form the CD (note that this does absolutely nothing to your hard drive). This may take a few minutes since CD drives are generally slow. Once the desktop has completely loaded, feel free to play with the operating system a bit and check out some programs and see if your internet connection is working, especially if you use wireless. Once you feel you are ready to install, double click the Install icon on the desktop and follow the instructions. Once you get to a page that says "setting up the partitioner" it will ask you where and how you would like to install Ubuntu. If you only have one hard drive, you will have to partition it and resize Windows. Resize your Windows partition with the slider to a size that will leave enough space for Ubuntu (IMPORTANT: the size reported by the slider is the size of WINDOWS and not your new partition; the remainign free space is to be used for Ubuntu). From there, the partitioner will resize your drive and create the necessary EXT3 and swap partitions. You also have the option along the way of migrating your user info and files from Windows during the install process.  Once all of the options are selected, just click install and let it do the rest. When it's done, just reboot. When you boot your computer, you will now get a GRUB loader screen that allows you to select which operating system you want to use. To boot Ubuntu, select the top entry, or use the arrow keys to go down and select Windows.

Once you are booted into Ubuntu, make sure to install any updates you may need (it automatically checks for you) and set up your video drivers (if you need help, you can just ask). Enjoy!

---

### Post by SunnyRabbiera on 2007-09-15
Alright first question:
Does DL'ing this and using wipe out/replace windows?
No, Ubuntu is something called a live CD, a live CD is practically an entire OS loaded onto a single disk.
The live CD is basically the whole OS compacted onto a single disk, where you can run and experiment with the system without harming your computer.
Just make sure you have a program to burn ISO's as windows is not friendly with burning them

second:
Can I use both Windows and Ubuntu?  Would I need 2 hard drives to do that?
Not really, but some do suggest having a secondary hard drive nearby just in case you frag your system.

Third:
If I use it what happens to all my programs I already have?
nothing if you dual boot, however i will remind you that Ubuntu does have alternatives to a good majority of windows apps.
Just remember Linux is not a windows replacement, no operating system will ever be windows unless it is in fact windows.
I personally ubuntu/ linux apps are suitable alternatives to windows ones.
XMMS/ Beep/ Audacious are all great winamp like programs
Amarok is a good alternative to itunes
Firefox of course is a well known alternative to IE
Open office is also fair if you are a MS word/office user
it really depends on what you need, if you are a net junkie ubuntu and other linux distros out there might suit your needs.
Multimedia might be an issue at first, if you listen to a lot of music then initially ubuntu will not work for you right away on things like MP3's
But this is no fault of Linux, there are a lot of legal issues concerning MP3 and many other popular windows and apple formats such as certain audio and video formats.
But this is easy to correct and it is easy to learn if you are willing to learn.
Games though, a major weakness, this is why if you are a gamer it would benefit you to dual boot windows as most games are windows only, in this respect linux is like apple.
Another issue you might find is that linux might not work for your favorite things like controllers, keyboards, mice, graphic cards and other add ons.
Again no fault of linux, as i said before a lot of things are made for windows only and it is no fault of linux if certaijn things might not work.
This is why a live CD is a good thing, it gives you a test run of everything before you decide if you want to install ubuntu/linux 

Now final question:
What are the advantages of Ubuntu, why switch?
Ubuntu like other linux distributions are far more secure then windows, this is because linux is not the leader on computers, windows is.
Windows biggest advantage and disadvantage is that its the most used OS.
Windows desktop share is gigantic but as a result many people out there like to hack it.
Even Vista with its promises of being more secure lags behind linux, linux is based on unix even though its not really a part of the main unix tree it is inspired by unix.
Unix is a very high peak in security, thus why it is a very popular basis for many operating systems out there, BSD, Apples OSX, Sun's Solaris and Linux are all based around the ideals of unix, but unix itself is really a moot point in the end as by now there are so many spin offs of it that practically unix as it was before now is practically a benchmark.
The thing is that you really dont need to switch to linux, if you want you can keep windows for as long as you want until you are forced buy the next microsoft OS.
in this case is why a alternative to windows might be desirable, as really Micorsoft forces its consumers to update by totally dropping support of its older systems.
now of course concering some linux distro's like ubuntu you are also sort of forced to upgrade, but in ubuntu's defense it is one of the easiest linux variants to upgrade and normally you probably wont need new hardware all the time there is an upgrade...
Just concider this, when most people were forced to upgrade from windows 2000 to XP it was quite a big hunk as 2000's demands were far less then XP, but in retrospect for a lot of people the transition from 2000 to XP is lightyears better then the transition from XP to Vista.
Vista is a mega beast compared to XP, bogged down with more eye candy then actually real groundbreaking features Vista is basically XP with more eye candy, extra bullcrap tools, and a load of bloat.
Even XP is a lightweght to it and XP too had a lot of bulge to it.
but really its all choice, and keep and open mind as Ubuntu is not the only Linux out there so if ubuntu doesnt work for you there are many other variants out there, Mepis, PClinux, Mandriva, Fedora... who knows what might work for you.

---

