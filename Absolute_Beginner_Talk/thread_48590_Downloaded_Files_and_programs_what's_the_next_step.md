---
title: "Downloaded Files and programs what's the next step?"
date: 2005-07-13
forum: Absolute Beginner Talk
---

### Post by mookie2125 on 2005-07-13
Hi all
I have downloaded some files and programs to get some firewall and antivirus protection up and running plus printer drivers for a canon i560 printer.
After downloading the files to "home" how do I get them to install
to where they need to be.
Do I need to create folders with specific names for those programs, how do I extract files etc.
I didn't have much luck with get-apt or synaptic so I ended up downloading the files i needed via the websites
Pardon my extreme lack of knowledge on this subject-  1and 1/2 days of linux experience.
Rgds

---

### Post by Leif on 2005-07-13
What problems did you have with apt ? You really should be using it whenever you can. Have you looked at ubuntuguide.org ?

---

### Post by felipe on 2005-07-13
hi,

Forget windows and its crappy packaging system! almost everything you want to install has been already packaged exactly for your system, *digitally signed* and locally searchable/available from your box via a centralized GUI: Synaptic.

So launch synaptic, then locate and install

1) firestarter (graphical interface to iptables - firewall)
2) clamav (antivirus)

for everything else just dig synaptic, there are over 17000 packages ready for you

---

### Post by Kvark on 2005-07-13
Add more repos to synaptics sources by following [http://ubuntuguide.org/#repositories](http://ubuntuguide.org/#repositories) then look again to see if you can find the programs in synaptic, it is very rare that you can't find what you need there.

If you still can't find it in synaptic then install the downloaded file by typing "sudo alien --install /path/file.deb" in a command terminal. There is also more complicated ways to do it that are worth trying if alien doesn't work. But no matter what method you use to install the .deb file you risk dependancy issues or other problems so use synaptic if at all possible.

---

### Post by aysiu on 2005-07-13
[QUOTE=mookie2125]Hi all
I have downloaded some files and programs to get some firewall and antivirus protection up and running plus printer drivers for a canon i560 printer. [/QUOTE] You don't need antivirus protection. There should be a firewall program in Synaptic, especially if you enable extra repositories (as outlined above). You didn't receive any instructions from Canon when you downloaded the driver? Does it look like blahblahblah.tar.gz?

---

### Post by mookie2125 on 2005-07-13
Hi all
Thanks for all the suggestions.
1. I printed out the "Unofficial Ubuntu users guide, followed all the instructions
to update the repositories. Downloaded lots of files automatically ( so far so good)
2. Tried to get clamav  via apt-get - down loaded files- then error message stating that the it could not install due to unbuntu file xxx-xx -92 when clamav needed xxx-xx-81. - try to get update to fix file
3. Tried to install firestarter with much the same result - Now I am beginning to learn about dependencies ( I think) You cant can't have a cheese sandwich without having  the tomato as well.
I  have also printed out the linux users guide.( linuxquestions.org ) 
4 Now waiting for the next release - perhaps i will have some luck there

In the meantime I have an audio and video problem that I haven't even tried to fix.
I have a mitsubishi dvd/cd rom and a lite-on dvd burner. Everything pertaining to getting one of these to play audio or video is useless.

While I have sound available during start up, and the the cdroms can extract audio via juicer  and I can  play those tunes, every time I put a disk in to one of the units it appears to play - but nil sound.  same with movies in either drive - "unknown format" message. In all cases I have to reboot the computer to get the video disk out of either drive as it refuses to eject the disk and closing the program has no effect either.

My last attempt with a new movie, unit proceded to try to thrash itself to death until I shut the computer down with the power button.

From the various cd play screens that come up , it would appear that the units have an identity crisis, the computer can't differentiate which CD rom is operating, so with an audio disk in one player I end up with 2 cd player screens on the desktop

On the subject of printer drivers , I found the info from LinuxQuestions.org.  Canon do not support any linux drivers except in japan. Therfore following the advice I downloaded the "tar" and "rpm" files for the printer from the Japanese site. They are now in my "home" directory awaiting me to gain sufficient knowledge to open/extract them to where they need to be.

Now  I am a reasonably patient person to a point. I don't expect everything to be perfect, but at least to work in one fashion or another even if there is a "work around " to get things to operate.

I try to take all advice on and I will get round to trying various things, and following leads, however there is only so much time available to do these things. ](*,) 
Rgds.

---

### Post by Kvark on 2005-07-13
You know these websites with online security tests and firewall scans?
Try some of those on linux without firewall, they won't find any open ports at all.

If you set up some kind of server without double checking so it doesn't give out too much. For example a fileserver giving write access or sharing secret files or a webserver showing admin-tool pages to anyone. Then you got a security hole. But you are safe as long as you don't do that.


As for viruses, you'll have a hard time getting them on linux even if you try to get infected on purpose. [Here](http://os.newsforge.com/article.pl?sid=05/01/25/1430222) is a report from a guy who tried to get infected by using the windows emulator wine.

If you manually install things from some fishy unknown source then you never know what might be in it. But the risk of automatically getting viruses or of getting spyware from well known sources is very small, most likely non existant.  


Yeah, multimedia is a problem. Make sure you got w32codecs and try the player totem-xine (both are in synaptic ofcourse). Search for some howtos about sound.

I'd do "sudo alien --install /path/file" on the printer drivers and see what happens. It might work but it might mess up. Guess it depends on if you're feeling lucky.

Btw, To eject a CD, right click on it and select "unmount".

---

### Post by maruchan on 2005-07-13
mookie:

the ubuntuguide tells you to use a repositories list that prefixes "archive" with "us." In my experience this didn't work, so I did this:

1.sudo gedit /etc/apt/sources.lst
2.change all instances of "us.archive" to just "archive" - then save & close.
3.load synaptic, and hit the reload button. Then try getting those apps again.

---

### Post by maruchan on 2005-07-13
btw mookie, regarding your printer, it's an iXXX series, correct? Check:

[http://ubuntuforums.org/showthread.php?t=10540](http://ubuntuforums.org/showthread.php?t=10540)

How does that work for you?

Edit: With updated repositories, have you now tried the DVD/video instructions at ubuntuguide.org?

---

### Post by mookie2125 on 2005-07-14
Hi There
Followed all the instructions for setting up drivers
Everything went per the directions 
Added printer, selected the correct driver
Print Test Page  - yes please....
This is where the wheels fell off..
not a hint of action.
USB shows i560 connected
device manager shows up OK
rebooted , replugged USB , cycled printer switch
removed printer, reinstalled, relected both combinations of USB drivers
no more options. 
I will get a parallel cable and try that instead of USB 
Not sure where to go from here :-? 
Rgds
PS will get round to the DVDs and CDROM's later.
Tried some of the suggestions eg right click  -unmount- to eject
I do not have "unmount" , but I do have "eject" and (already tried) and still no joy.
If I pop a CD or DVD in the the number one unit it flashes a couple of times as if it is reading the cd/dvd, then automatically goes to the nbr 2 unit and it flashes a couple of times then I get a message saying there is no disk (I already know that!)
the cd player box comes up on the screen as a blank, then the second cd player box also comes up on the screen and shows the AUDIO disk playing - alas no sound
If you're really lucky  you may be able to get one of the disks to eject.
Any DVD - forget it, " unknown format" msg  cmptr freezes - cannot eject DVD 
turn the computer off and remove disk while it is rebooting.
Good news - at least "open office" keyboard and mouse (plus internet) works
Must confess my windows machine is starting to look better and better
as one of my prime uses is cutting and burning music
Life goes on....

---

### Post by AntiDragon on 2005-07-14
Just a thought - but which version of Ubuntu are you using? And what architecture (Did you install from a I386 CD or an AMD64 CD) ?

I had  very similair DVD problems  - the disc wouldn't be mounted. Or it would but Totem wouldn't see it. Or it would but would crash and I couldn't eject etc.. ](*,) 

I'm running AMD64 and had to install LibDVDCSS2 to enable proper DVD playback. It also stopped all my weird disk problems too. However, the instructions in Ubuntuguide worked fine on a normal I386 machine.

---

### Post by AntiDragon on 2005-07-14
Oh and for MP3 ripping/encoding and burning:

Look for GRIP and Xtunes to encode you music (obviously just to backup your existing CDs of course  :smile: )

And Gnomebaker is a CD burning package.

---

### Post by mookie2125 on 2005-07-14
Hi There
Computer has ASRock K7VM4 M/B with 1 gig of ram
120 Gig Primary HDD 80 Gig Sec. HDD one FDD
AMD Athlon 2600+ Processor
Leadtek DV2000 Video capture card
Geforce mx440 64mb video card
Aopen Cobra AW-850 deluxe 5.1 sound card ( C-Media 8738 chip) 
Mitsubishi CD/DVD rom , and Lite-On CD/DVD dual layer burner
( Computer is home built ).
I set up 3 partitions on the prim hard drive with Windows XP on the first
Clean install of Ubuntu 4.10 on the 2nd partition and 3rd partition unused.
I've updated the repositories as advised in the notes and other forum users -
Tried to get Xine with Synapt- downloaded lots then finally said "server problem unable to fetch one package (1 out of 9) do you still want to go ahead with installation ? Check sumMD5 incorrect  -  I optioned for NO.
Maybe the 64 bit add-on will work however it seems ther is a problem firstly in the system being able to identify which CD/DVD rom is actually playing when disks are inserted even though all indications looking at "disks"  and "device manager"etc show  them in their correct order. 
Will try again when I get some spare time
Rgds

---

### Post by poofyhairguy on 2005-07-14
[QUOTE=mookie2125]Hi There
Computer has ASRock K7VM4 M/B with 1 gig of ram
120 Gig Primary HDD 80 Gig Sec. HDD one FDD
AMD Athlon 2600+ Processor
Leadtek DV2000 Video capture card
Geforce mx440 64mb video card
Aopen Cobra AW-850 deluxe 5.1 sound card ( C-Media 8738 chip) 
Mitsubishi CD/DVD rom , and Lite-On CD/DVD dual layer burner
( Computer is home built ).
I set up 3 partitions on the prim hard drive with Windows XP on the first
Clean install of Ubuntu 4.10 on the 2nd partition and 3rd partition unused.
I've updated the repositories as advised in the notes and other forum users -
Tried to get Xine with Synapt- downloaded lots then finally said "server problem unable to fetch one package (1 out of 9) do you still want to go ahead with installation ? Check sumMD5 incorrect  -  I optioned for NO.
Maybe the 64 bit add-on will work however it seems ther is a problem firstly in the system being able to identify which CD/DVD rom is actually playing when disks are inserted even though all indications looking at "disks"  and "device manager"etc show  them in their correct order. 
Will try again when I get some spare time
Rgds[/QUOTE]


Why are you using Warty and not Hoary?

---

### Post by mookie2125 on 2005-07-14
Waiting for disk to arrive
Dial up is not really an option
Rgds

---

### Post by poofyhairguy on 2005-07-14
[QUOTE=mookie2125]Waiting for disk to arrive
Dial up is not really an option
Rgds[/QUOTE]

Ok...ok...good call...you might have to wait though....Warty has many, um, warts

Here is some advice:

[http://www.ubuntuforums.org/showpost.php?p=227549&postcount=3](http://www.ubuntuforums.org/showpost.php?p=227549&postcount=3)

---

### Post by mookie2125 on 2005-07-17
Hi Mr PoofyHairGuy 
The link to the "good information was worth reading and probably sound advice.
At this point in time Ubuntu is more of my hobby horse. An introduction to Linux.
 I am getting more familiar with some of the commands in the terminal windows, as I find this easier to use than synaptic. 
The latest bug I have is that firefox has locked up in the "downloads " section.
It has both open with and save to disk selected and will not deselect either. 
When I try to download it asks me which associated helper program I wish to use but the dialogue window won't let me type anything. I am unable to change anything in preferences .
Talking about updating things, I thought I'll update firefox to the latest vers. I'll go to synaptic and get the new version...not that easy..... It tells me that to load firefox it will need to virtually delete the whole Ubuntu installation ( it needs to remove a "gazillion" files.) This kind of response does not fill me with lots of confidence. So with extra repositories added  from Hoary,  running Warty with a suspect FireFox that doesn't make a sound, (or print) and doesn't like movies and tells me there is always a reason that it can't install the program I have just spent time downloading , then I guess this would be relatively normal for a first release of an OS.
While the "getting of wisdom" in linux is a kind of steep learning curve by itself, all the other obstacles thrown in don't help. In all fairness nearly everyone has been really patient with the obviously dumb questions I/we ask. ( My philosophy is that "It is better to ask a dumb question that fix a stupid mistake)
So every now and then I venture to play with Ubuntu 
My only question now is will the new disk install straight over the old OS but still leave the updated files etc I have downloaded or  wil I have to go throught the same problems .. extra repositories :-? .. get codecs.. printer drivers etc
Rgds

---

