---
title: "[SOLVED] Feisty Fawn is on a Go Slow"
date: 2007-07-16
forum: Absolute Beginner Talk
---

### Post by Andavane on 2007-07-16
Greetings.
I am new, and my fourth day into Ubuntu 7.04.
My first job today was to listen to and accompany some chants (stored in drive 0)
After that, there was some email to attend to.

Then everything started to go really slowly.
I used 'restart', planning to reboot into Windows as I was in a hurry, hopwever it started rebooting into Ubuntu, but incredibly slowly, and in the end I had to switch the machine off and boot into Windows from cold.

I had to hurry things up as I need to get on with the day.

I know that the team like as much information as possible on 'what happened'... however there was not really anything much to notice.

I will boot into Linux again when I get back from work, and ask: Has the team any suggestions as to what checks I can make when I do log into ubuntu again?

I have thought about this, and wonder whether it is anything to do with the fact  that all my files are on drive "0", stored in a FAT32 folder. ubuntu is accessing them by going to another drive.

Another memory I had was that when I dipped my toes in Linux earlier in the year, I would run Knoppix from the DVD. It would work fine as long as I kept doing doing things, however if I went away and came back later, the same "Go Slow" was happening.

In those days, I used to enjoy watching all the commands mounting up on the screen when it loaded, and being dismounted or "killed" when the system was shut down. So I could work out mentally what stage it had got to. I calculated that it would take two hours for the shut down to complete on one occasion, and that was exactly what happened. After it had been through that laborious process, everything worked fine, as long as I kept on "doing things", but if I just left it, the same thing would start happening all over again.

I put this down to it doing everything from the CD, and assumed that a Linux install would prevent this from occurring.

In Ubuntu I kind of miss being able to see all the commands going on as the OS loads up and shuts down.

I expect that it is possible to get them back.

Any suggestions as to how to proceed when I get in from work and boot into ubuntu again?

Kind regards

John




[b]PC: IBM Think-Centre A-50 : 40 Gb

Hard Drive 0) Windows XP-Pro
Hard Drive 1) Ubuntu 7.0.4 “Feisty Fawn”, : 110 Gb[/b]

---

### Post by avik on 2007-07-16
To see the commands during boot up, either boot into recovery mode via GRUB (press Esc for the GRUB menu when it says to).

Or, go to the GRUB menu, highlight the item you want, and press e.  Choose the second item, press e, and remove the words splash and quiet.  Press Esc, then b.

---

### Post by Andavane on 2007-07-16
Thank you.
I did try this, but am afraid I got confused..:confused:
I move very slowly and like to have good read of all these things, however it does not give much time before the seconds tick down and it starts booting.
It would be good if there was more time available to read all the options (while in this beginner stage)
I got recovery mode to go, then came the command lines, then a winking cursor where absolutely nothing happened.

i had to switch the power off and then back on again.

One thing I did manage to jot down:
there were some lines of text, and the last one said:
**/dev/sdb1 has been mounted 20 times without being checked. Check forced**.
I am also getting messages which say (when I start firefox) that the sessions did not close down properly and to "start a new session?".

Sorry for appearing a bit thick!

Regards

John

---

### Post by forestpixie on 2007-07-16
when it boots to the grub screen - if you move the highlighted line with an arrow key - the countdown stops and you've got all the time in the world. At least I think everyones is like that.


The check forced is normal - it checks your drive once in a while - if it stops with an error message write that down and search for it in the forum - or ask a question.

Firefox will ask if you want to restore if the last session crashed or if gets turned off by a restart etc.


And HOW long are your legs to be in England and India - :D

Edit - and no-ones thick everyone knows different things :)

---

### Post by Andavane on 2007-07-16
Well, forestpixie I do like your logo...
>And HOW long are your legs to be in England and India - 
well... the legs packed up ages ago I'm afraid, but it's fine, if tough work for the guys who push me all over the planet on wheels (well to be truthful the odd plane hop is used these days) ;)
Destination is a misty mountain in South India... perhaps it will lead to a series of posts along the lines of “Net-less Ubuntu”, for we will be only making trips to an internet cafe in town, and the power lines are erratic there...)
I'll certainly have a crack at those things...
We learn by the doing, don't we?
anbudan
John
PS:
>Edit - and no-ones thick everyone knows different things
Indeed.
[b]That which we do know is as small as a grain of rice.
That which we do not know is as vast as the Universe.[/b]
#-o

---

### Post by forestpixie on 2007-07-16
Well good luck with a netless Ubuntu :)

---

### Post by Andavane on 2007-07-16
Thank you, we'll see how it goes.

However, when I got back Feisty Fawn was not in the least feisty... It now loads things so slowly it is like watching paint dry.

I have thought hard about this, and note that it has done this since I tried to install my "Accountz" program. I followed the instructions on the forum given by the company who sells the program; the boss said the program worked fine on Ubuntu 6.06, and I am sure it did. When trying it here, however (double clicking) a screen flashed up fast and then disappeared down again. I wonder if something has been done to the program and whether there is any way I can go back to where I was.

Am writing this using Windows XP....

Any suggestions would be most welcome.

Regards

John

---

### Post by Andavane on 2007-07-16
PS: Sad to that that Windows on the net get in there really fast... Ubuntu gets slower and slower...
Oh dear

---

### Post by djchandler on 2007-07-16
> **Andavane said:**
> PS: Sad to that that Windows on the net get in there really fast... Ubuntu gets slower and slower...
Oh dear

Since Ubuntu is on the second and separate hard drive, that is where the problem must be. Is the XP hard drive also a SATA drive? This is sounding more and more like a hardware problem. Otherwise, it is the incompatibility  with FAT32. It is possible is that Ubuntu is having a difficult time finding files, and that could be due to incompatible  differences in the formatting of the two drives. The problem is probably being caused closing files that for some reason are on the XP drive. How many applications are you leaving open when you shut down Ubuntu? If you are not closing applications before shutting down Ubuntu, that may make a difference. Try closing all your applications first before shutting down Ubuntu.

If the XP drive was formatted NTFS, this may not be happening. Is there some reason you chose FAT32 instead of the more stable and feature rich NTFS system? I think there is a way to change a Fat 32 drive to NTFS without data loss in XP.

DJ
:confused:

---

### Post by splintercellguy on 2007-07-16
That would be convert <drive letter> /fs:ntfs. Backup before doing that of course.

---

### Post by Andavane on 2007-07-16
I feel that there is a lot in what you have said, djchandler.
May I answer a few points:
**>Is the XP hard drive also a SATA drive?**
Sorry i don't know what a SATA drive is, but I do have a windows program which gives all sorts of info on hardware, so will go to see if it is SATA.
**>Is there some reason you chose FAT32 instead of the more stable and feature rich NTFS system?**
The reason for making a FAT32 partition on "Drive 0" is that I want to write to my files in both Windows and and in Ubuntu Linux, and I understand that Linux does does write to NTFS.

I am indeed closing everything in linux before closing down.

One thing I forgot to relate: For some time now when I boot my PC from cold, it has been making some noise. As time proceeds, the noise has got louder until sometimes it is a bit like an aeroplane revving up. Our local village man says to call him if it gets too bad. Hardware indeed seems to be a major factor. After it has been running awhile, things quieten down and go quiet. (on this occasion, I booted from a cold motor and straight into Ubuntu

After some time running in Windows and things  quieting down, I restarted and went into ubuntu, which loaded much faster and it is now all running very crisply.

So I think we are getting somewhere on this one. ;)

PS: splintercellguy:
**>That would be convert <drive letter> /fs:ntfs. Backup before doing that of course.**
thanks for this: however I do not feel confident enough yet to do that, being a newbie and all.

---

### Post by avik on 2007-07-17
> **Andavane said:**
> 
**>Is the XP hard drive also a SATA drive?**
Sorry i don't know what a SATA drive is, but I do have a windows program which gives all sorts of info on hardware, so will go to see if it is SATA.


Is the hard drive connected with one of the [thick cables]("http://www.gshop.com.au/images/ide_133_cable.jpg") or a [thin one]("http://www.cwol.com/serial-ata/images/sata18ra1-l.gif")?

> **Andavane said:**
> 
**>Is there some reason you chose FAT32 instead of the more stable and feature rich NTFS system?**
The reason for making a FAT32 partition on "Drive 0" is that I want to write to my files in both Windows and and in Ubuntu Linux, and I understand that Linux does does write to NTFS.


Do you mean Linux *doesn't* write to NTFS?  Because it does, with some setting up.

---

### Post by djchandler on 2007-07-17
Are you in England or India now?If you are in India running the computer with no air conditioning somewhere, that could explain a lot. How is the humidity and the daily high temperature?

Sorry I didn't think of this before. Opening the case and cleaning and lubricating fans could be helpful.

D. J.

PS Don't forget the heatsinks!

---

### Post by Andavane on 2007-07-17
Re the hard drive:
I need help from someone to open the case for me, and will report back when I can get assistance.
In the meantime, I have this info on it from "PC Wizard 2007" in Windows:

IDE Controller :	82801EB/ER (ICH5/ICH5R) EIDE Controller 
IDE Channel :	#1  -  Master Drive 
Model :	ST340014A 
Serial Number :	4JX0H16Z 
Revision :	8.10 
Serial ATA :	No 
Support :	ATA/ATAPI-6 
Size :	40 GB 
Cache :	2 048 KB 
ECC Size :	4 
Multiple Sector :	16 
IORDY :	Yes 
LBA Mode :	Yes 
DMA Mode :	Yes 
NCQ Mode :	No 
Multiword DMA Mode :	2 
PIO Mode :	PIO 4 
UDMA Mode max. :	5 (ATA-100) 
UDMA Mode Enabled :	5 (ATA-100) 
SMART :	Yes   -   Enabled 
Power Management :	Yes 
Acoustic Management :	No 
Security Mode :	Yes 
Write Cache :	Yes 
48-bit Address :	Yes 
Cylinders :	77536 
Heads :	16 
Sectors per Track :	63

----
Does this help?
=========================
Regarding the other question:
No I am in England now, but have a stack of point to raise for the Indian stay,
and will raise them in a separate post.

Thanks
John

---

### Post by Andavane on 2007-07-17
> **avik said:**
> Is the hard drive connected with one of the [thick cables]("http://www.gshop.com.au/images/ide_133_cable.jpg") or a [thin one]("http://www.cwol.com/serial-ata/images/sata18ra1-l.gif")?



Do you mean Linux *doesn't* write to NTFS?  Because it does, with some setting up.

it's the thick cable (looks like a wide ribbon).
I was unaware that Linux could write to NTFS.
Am always learning.

Regards

John

---

### Post by djchandler on 2007-07-18
> **Andavane said:**
> it's the thick cable (looks like a wide ribbon).
I was unaware that Linux could write to NTFS.
Am always learning.

Regards

John

Always learning, still  living.

Your told us all about your Master drive on IDE 1 only before. I am still curious what the other drive is.

As for being in England still, that somewhat eliminates exterior heat and humidity as a problem, at least in contrast to what you would have in India. Have you tried cleaning the indside of dust and such? Computers are magnets for dust. You can eliminate a lot of dust by having your fans  blowing in, instead of pulling air out. I filter the incoming air with a toe of my wife's old nylon hose that has been cut just short enough to fit over the fan. This filters the incoming air and creates positive air pressure within the computer's enclosure. Heat will escape through other vents. Then all you have to do to clean the interior next time is to open one side of the case, remove the fan filters, and clean those and/or replace them. While you are in there, see if it is the fans making all the noise you are hearing.

DJ

---

### Post by Andavane on 2007-07-18
> **djchandler said:**
> Always learning, still  living.

Your told us all about your Master drive on IDE 1 only before. I am still curious what the other drive is.

As for being in England still, that somewhat eliminates exterior heat and humidity as a problem, at least in contrast to what you would have in India. Have you tried cleaning the indside of dust and such? Computers are magnets for dust. You can eliminate a lot of dust by having your fans  blowing in, instead of pulling air out. I filter the incoming air with a toe of my wife's old nylon hose that has been cut just short enough to fit over the fan. This filters the incoming air and creates positive air pressure within the computer's enclosure. Heat will escape through other vents. Then all you have to do to clean the interior next time is to open one side of the case, remove the fan filters, and clean those and/or replace them. While you are in there, see if it is the fans making all the noise you are hearing.

DJ

Hello djchandler,
Thanks for this.
A friend in the village does the hardwork things for me, like opening cases and putting in parts as I am unable to perform these functions myself.
He returns from holiday on Monday, and I'll certainly show him what you said.
Let's see if this has an effect!
Many thanks and kind regards
John
PS: oh, I shall want some information about the "heat sink"; I'll ask him about that too; it will be necessary to know for India, as I think they are going to build a PC for me there.
And another thing: Feisty Fawn has suddenly become much more rapid-- not quite sure why.

---

### Post by Seisen on 2007-07-18
Open up a terminal put this in it

```
top
``` then post what it says here.

---

### Post by Andavane on 2007-07-18
> **Seisen said:**
> Open up a terminal put this in it

```
top
``` then post what it says here.

Lots and lots of things are continuing to appear in the terminal.
Shall I highlight, copy and paste some or all of them in?

John

Tasks: 103 total,   1 running, 102 sleeping,   0 stopped,   0 zombie
Cpu(s):  2.0%us,  0.5%sy,  0.0%ni, 97.5%id,  0.0%wa,  0.0%hi,  0.0%si,  0.0%st
Mem:   1027092k total,   700392k used,   326700k free,    93460k buffers
Swap:  3004112k total,        0k used,  3004112k free,   308364k cached

---

### Post by Seisen on 2007-07-18
Post all of it if you could.

---

### Post by Andavane on 2007-07-18
> **Seisen said:**
> Post all of it if you could.
It says:

top - 18:57:33 up 12 min,  2 users,  load average: 0.00, 0.06, 0.07

Tasks: 104 total,   1 running, 103 sleeping,   0 stopped,   0 zombie

Cpu(s):  3.0%us,  0.2%sy,  0.0%ni, 96.7%id,  0.0%wa,  0.2%hi,  0.0%si,  0.0%st

Mem:   1027092k total,   657280k used,   369812k free,    99116k buffers

Swap:  3004112k total,        0k used,  3004112k free,   366764k cached


 PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND                        

 4979 root      15   0  221m  17m 7184 S    5  1.8   0:08.30 Xorg                           

 5774 andavane  15   0 77208  16m  10m S    1  1.6   0:00.87 gnome-terminal                 

 5512 andavane  15   0 17560 9.9m 7516 S    0  1.0   0:02.01 metacity                       

 5667 andavane  15   0 16236 2316 1372 S    0  0.2   0:00.20 gnome-screensav                

    1 root      15   0  2908 1844  524 S    0  0.2   0:01.43 init                           

    2 root      RT   0     0    0    0 S    0  0.0   0:00.00 migration/0                    

    3 root      34  19     0    0    0 S    0  0.0   0:00.00 ksoftirqd/0                    

    4 root      RT   0     0    0    0 S    0  0.0   0:00.00 watchdog/0                     

    5 root      RT   0     0    0    0 S    0  0.0   0:00.00 migration/1                    

    6 root      34  19     0    0    0 S    0  0.0   0:00.00 ksoftirqd/1                    

    7 root      RT   0     0    0    0 S    0  0.0   0:00.00 watchdog/1                     

    8 root      10  -5     0    0    0 S    0  0.0   0:00.00 events/0                       

    9 root      10  -5     0    0    0 S    0  0.0   0:00.00 events/1                       

   10 root      12  -5     0    0    0 S    0  0.0   0:00.00 khelper                        

   11 root      10  -5     0    0    0 S    0  0.0   0:00.00 kthread                        

   35 root      10  -5     0    0    0 S    0  0.0   0:00.00 kblockd/0                      

   36 root      10  -5     0    0    0 S    0  0.0   0:00.00 kblockd/1                      

   37 root      18  -5     0    0    0 S    0  0.0   0:00.00 kacpid                         

   38 root      20  -5     0    0    0 S    0  0.0   0:00.00 kacpi_notify                   

  126 root      13  -5     0    0    0 S    0  0.0   0:00.00 kseriod                        

  147 root      17   0     0    0    0 S    0  0.0   0:00.00 pdflush                        

  148 root      15   0     0    0    0 S    0  0.0   0:00.00 pdflush                        

  149 root      13  -5     0    0    0 S    0  0.0   0:00.00 kswapd0                        

  150 root      13  -5     0    0    0 S    0  0.0   0:00.00 aio/0                          

  151 root      14  -5     0    0    0 S    0  0.0   0:00.00 aio/1                          

  777 root      15   0     0    0    0 S    0  0.0   0:00.00 kirqd                          

 1999 root      10  -5     0    0    0 S    0  0.0   0:00.00 ksuspend_usbd                  

 2000 root      18  -5     0    0    0 S    0  0.0   0:00.00 khubd                          

 2011 root      10  -5     0    0    0 S    0  0.0   0:00.00 ata/0                          

 2012 root      10  -5     0    0    0 S    0  0.0   0:00.00 ata/1                          

 2013 root      19  -5     0    0    0 S    0  0.0   0:00.00 ata_aux                        

 2120 root      18  -5     0    0    0 S    0  0.0   0:00.00 scsi_eh_0                      

 2121 root      10  -5     0    0    0 S    0  0.0   0:00.00 scsi_eh_1                      

 2421 root      10  -5     0    0    0 S    0  0.0   0:00.02 kjournald                      

 2620 root      14  -4  2896 1236  372 S    0  0.1   0:00.47 udevd                          

 3612 root      17  -5     0    0    0 S    0  0.0   0:00.00 kpsmoused                      

 4318 root      18   0  1652  508  440 S    0  0.0   0:00.00 getty                          

 4319 root      18   0  1652  512  440 S    0  0.0   0:00.00 getty                          

 4321 root      18   0  1652  512  440 S    0  0.0   0:00.00 getty                          

 4323 root      18   0  1648  508  440 S    0  0.0   0:00.00 getty                          

 4325 root      18   0  1652  508  440 S    0  0.0   0:00.00 getty                          

 4326 root      18   0  1652  508  440 S    0  0.0   0:00.00 getty                          

 4591 root      18   0  2260 1172  656 S    0  0.1   0:00.00 acpid                          

 4708 root      18   0  1704  648  536 S    0  0.1   0:00.03 syslogd                        

 4763 root      15   0  1796  524  432 S    0  0.1   0:00.04 dd                             

 4765 klog      18   0  2432 1376  400 S    0  0.1   0:00.05 klogd                          

 4786 messageb  15   0  2852 1064  736 S    0  0.1   0:00.14 dbus-daemon

---

### Post by Andavane on 2007-07-18
Dear Members
I use a radio trackball mouse.
The battery was rather flat, and has just been changed.
Could that have been a contributory factor?
Regards
John

---

### Post by Andavane on 2007-07-23
> avik's Avatar  	
avik avik is offline
Way Too Much Ubuntu
	  	
Join Date: Aug 2006
Location: Same place as Apple HQ
Beans: 282
Ubuntu 7.04 Feisty Fawn User
Re: Feisty Fawn is on a Go Slow
To see the commands during boot up, either boot into recovery mode via GRUB (press Esc for the GRUB menu when it says to).

Or, go to the GRUB menu, highlight the item you want, and press e. Choose the second item, press e, and remove the words splash and quiet. Press Esc, then b.
Thank you.
When I did this, Ubuntu just booted up as normal.
(The object of the exercise is to see the commands on bootup and shutdown).
Instead of pressing escape then b, should I have pressed "ENTER"?
I didn't do this in case it was wrong.

Note: The issue is the system starts to crawl along. it dids this earlier in dsl and knoppix on occasions, and I put this down to running from a live CD. I thought the problem would solve whe  there was an installation, but the problem is back (intermittently).

Symptoms when I could see the commands on other system:
I got to know them, and started to know what the next xommand would be.
It took ages, but once it had got through the commands, a restart caused everything to speed up and start again normally.

I wanmt to see the bootup/shutdown commands so that when it happens again (which it will!) I can see what commands are doing.

Regards
John

---

### Post by djchandler on 2007-07-23
> **Andavane said:**
> Thank you.
When I did this, Ubuntu just booted up as normal.
(The object of the exercise is to see the commands on bootup and shutdown).
Instead of pressing escape then b, should I have pressed "ENTER"?
I didn't do this in case it was wrong.

Note: The issue is the system starts to crawl along. it dids this earlier in dsl and knoppix on occasions, and I put this down to running from a live CD. I thought the problem would solve whe  there was an installation, but the problem is back (intermittently).

Symptoms when I could see the commands on other system:
I got to know them, and started to know what the next xommand would be.
It took ages, but once it had got through the commands, a restart caused everything to speed up and start again normally.

I wanmt to see the bootup/shutdown commands so that when it happens again (which it will!) I can see what commands are doing.

Regards
John

John,

Pressing "enter" after "esc" and "b" is the way to go if nothing happens after pressing "b."

Intermittent problems are no doubt the most vexing. Heat is your enemy, and that is why a restart helps, at least for a while. Most computers should cool slightly in between the shutdown and the restart. In the meantime, until your friend can help you, try getting a portable cooling fan like you would use in a room in your house, aim it at the computer, and see if that helps a little. I once kept a refrigerator running which had a bad condenser cooling fan by aiming a box-type fan at it until I could get the replacement condenser fan the next day. It seems as though you only discover these things at night, after every one who can help you is closed for the night. I managed to keep everything in the freezer compartment from thawing, and the milk was still fresh and cold for breakfast the next morning.

I hope you are not in the midst of the flooding in England. I saw a television news story  this evening and it was looking very bad for some people. I hope all is well with you.

Regards,
Dan

---

### Post by Andavane on 2007-07-24
Thanks for this, Dan

I've had quite a lot of thinking time about this, and am not entirely convinced that in this case it is a heating thing.
When the unit gets hot, an extra fan kicks in, so I am reasonably happy with that.

It seems to happen when I go away and do something else for a bit, leaving it on. It just goes "sleepy", it's like when you rouse somebody from their dreams and although they get up, they remain on go-slow for about two hours. Even although I can't see what command are going on yet, I just know that they are on a really slow phase. To reiterate, when it happened with Knoppix or dsl, I calculated that it would be another hour and a half before it shut down; so I went to the village, came back and it shut down when I thought it would.

So I am currently shutting the machine down when I am going to go away for more than a few minutes.

You know, I wonder whether the hard drive being situated in the bay which used to be the CD drive has anything to do with it?  

> I hope you are not in the midst of the flooding in England. I saw a television news story this evening and it was looking very bad for some people. I hope all is well with you.

Thank you very much for this. It is certainly very terrible for a lot of people (and an embarrassment for a red-faced government who, it was revealed had plans to build stacks of houses on flood plains :twisted:); mercifully, we are fine.

Best wishes

John

---

### Post by djchandler on 2007-07-24
> **Andavane said:**
> Thanks for this, Dan

I've had quite a lot of thinking time about this, and am not entirely convinced that in this case it is a heating thing.
When the unit gets hot, an extra fan kicks in, so I am reasonably happy with that.

It seems to happen when I go away and do something else for a bit, leaving it on. It just goes "sleepy", it's like when you rouse somebody from their dreams and although they get up, they remain on go-slow for about two hours. Even although I can't see what command are going on yet, I just know that they are on a really slow phase. To reiterate, when it happened with Knoppix or dsl, I calculated that it would be another hour and a half before it shut down; so I went to the village, came back and it shut down when I thought it would.

So I am currently shutting the machine down when I am going to go away for more than a few minutes.

You know, I wonder whether the hard drive being situated in the bay which used to be the CD drive has anything to do with it?  



Thank you very much for this. It is certainly very terrible for a lot of people (and an embarrassment for a red-faced government who, it was revealed had plans to build stacks of houses on flood plains :twisted:); mercifully, we are fine.

Best wishes

John

John,

You might be right about the hard drive placement-that would explain a lot. When 7200 RPM hard drives first appeared 7 or 8 years ago, many of us put extra fans in the plate in front of the hard disk. Heat dissipation has improved since then, but have your friend put it down lower inside the case, preferably near where there is better incoming airflow. And make sure it is mounted circuit board side down, metal casing up. I have seen upside down hard drives before too, and that is very bad.

Shutting down and coming back to reboot all the time can get hard on things too, especially the power supply. Perhaps you could open up System>Preferences>Screensaver, choose blank screen (uses less power) for your screen saver, then click the button labeled "Power Management." Try setting the the computer to go to sleep after twenty or thirty minutes of you being away. See if it comes back to life better after that. So far, you are in what we call a "no win" situation. Do the best you can until your friend has time to work on your computer.

Glad to see you are not swimming to your village. Stay safe.:)

Dan

---

### Post by Andavane on 2007-07-27
> **djchandler said:**
> John,

You might be right about the hard drive placement-that would explain a lot. When 7200 RPM hard drives first appeared 7 or 8 years ago, many of us put extra fans in the plate in front of the hard disk. Heat dissipation has improved since then, but have your friend put it down lower inside the case, preferably near where there is better incoming airflow. And make sure it is mounted circuit board side down, metal casing up. I have seen upside down hard drives before too, and that is very bad.

Shutting down and coming back to reboot all the time can get hard on things too, especially the power supply. Perhaps you could open up System>Preferences>Screensaver, choose blank screen (uses less power) for your screen saver, then click the button labeled "Power Management." Try setting the the computer to go to sleep after twenty or thirty minutes of you being away. See if it comes back to life better after that. So far, you are in what we call a "no win" situation. Do the best you can until your friend has time to work on your computer.

Glad to see you are not swimming to your village. Stay safe.:)

Dan

Hello Dan et al

It definitely goes sleepy if I leave the Ubuntu desktop on, chat to someone and forget about it and then when I return it all crawls. With Windows XP I can go away and chat for as long as I like and when I come back, all is fine.  Another symptom is that pressing Esc returns weird symbols when in the black screen. I think the next step is to get this thing so it shows the commands and processes during booting and shutting down; then I would get an idea about what is going on.

I thought I had followed the instructions given, but apparently not correctly, but will try again.

Regards

John

PS: The friend is back, but busy; he may be available Monday. I will collate the info we have and present it to him.

---

### Post by djchandler on 2007-07-27
> **Andavane said:**
> Hello Dan et al

It definitely goes sleepy if I leave the Ubuntu desktop on, chat to someone and forget about it and then when I return it all crawls. With Windows XP I can go away and chat for as long as I like and when I come back, all is fine.  Another symptom is that pressing Esc returns weird symbols when in the black screen. I think the next step is to get this thing so it shows the commands and processes during booting and shutting down; then I would get an idea about what is going on.

I thought I had followed the instructions given, but apparently not correctly, but will try again.

Regards

John

PS: The friend is back, but busy; he may be available Monday. I will collate the info we have and present it to him.


John,
I did not realize you were on a dual boot setup. You probably posted you were, I just forgot. You know we loose 50,000 brain cells a day after age 20 or so, and I'm 55.

Anyway, if windows is running fine, and you are on a dual boot, not running Feisty on an emulator, then something is not right with the Linux installation. As you said, something is running your machine down. Have you tried running System>Administration>System Monitor? There are ways to find out where all the cpu cycles are going in System Monitor. If you click on the Processes tab, you can sort by %cpu and see what is using up your cpu. Something may be running that you don't need. I'll post a screen shoot to show you what I mean.

[ATTACH]39191[/ATTACH]

See if this helps solve your mystery.

Dan

---

### Post by Andavane on 2007-07-28
Oh Dan,
[color=blue]>I did not realize you were on a dual boot setup. You probably posted you were, I just forgot. You know we >loose 50,000 brain cells a day >after age 20 or so, and I'm 55.[/color]
And here was I, thinking I was the oldest fogey on the forum... well I mean be as I'm comin' up 58, but great to me s/o about my generation. ;) An old lady phoned me this morning and I had to explain what the dots were in an email address... reminded me how much things have moved on....

Yes indeedy, any help in solving my mystery would be more than welcome. I am having a Tamil lesson at two, and after that I'll look at the thingie you suggest. I felt the installation was OK because it displayed no problems, but let's see.
I'm very keen in getting at the bottom of the mystery, because I have to read through a 700-page doument which is in pdf format. I have a text file sitting alongside for pasting in bookmarks. The way the setup goes here, I keep getting called away to attend to things, it happens all the time, and there's nothing worse than coming back to an Ubuntu which looks as though it's been given a shot of tranquilisers! 8-[

Just a reminder: the same thing happened when I ran dsl from CD, Knoppix from DVD, and Ubuntu 7.04 from DVD live --  no installation was involved.

getting back to you soon,

John

---

### Post by Andavane on 2007-07-28
Yes Dan I did that, and everything says "Sleeping" which comes as no surprise; at least it shows an appropriate title for the thread was given   :)
Regards
John

---

### Post by Andavane on 2007-07-28
Well, Dan,
Acting on a hunch, I took off my big "OM Sign" Wallpaper and reverted to the blank screen.
Since then have done several things, including going off, and having a meal and coming back,
and all appears to be normal with no slow down at all.
As I said, removing it was just a hunch, but who knows? ;)
This is while I await the friend who will carry out the measures you sugest.
Regards
John

---

### Post by djchandler on 2007-07-29
> **Andavane said:**
> Well, Dan,
Acting on a hunch, I took off my big "OM Sign" Wallpaper and reverted to the blank screen.
Since then have done several things, including going off, and having a meal and coming back,
and all appears to be normal with no slow down at all.
As I said, removing it was just a hunch, but who knows? ;)
This is while I await the friend who will carry out the measures you sugest.
Regards
John

John,

You may be older but probably more fit. I'm probably in as bad shape as my dad, and he's 83, almost 84. Just got diagnosed with fairly advanced Hashimoto's Thyroiditis 6 weeks ago, have 6 goiters, taking 12 prescriptions. Then there's a bony cyst in the socket (glenoid) of my right shoulder, may need a joint replacement, maybe just arthroscopic removal of cyst. It depends on how much other damage there is. A lot of the spondylosis due to osteoarthritis has been taken care of by corticosteroid injections. I haven't seen the MRIs, but the report states there's a lot of other "mechanical" damage to the joint, as well as some effusion. Seeing a major orthopedic specialists in shoulders at Kansas University Medical Center on August 17th. I won't know anything else until then. So I may be 3 years younger, but I will bet I feel 10 or more years older. At least you are getting your exercise walking in to the village. Ignore this rubbish. It's just the hydrocodone, orphenadrine, and diazapam talking. But for some reason I feel you understand this jargon.

Sometimes simplifying things works wonders (we're back to your computer now). If you were running one of the Open GL screensavers, that could make a huge difference too. Sounds like you may have things running much better already. This wouldn't have taken so long if I had asked the right questions. So much for me being helpful.

Have a great Sunday,
Dan

---

### Post by Andavane on 2007-08-08
> **djchandler said:**
> John,

You may be older but probably more fit. I'm probably in as bad shape as my dad, and he's 83, almost 84. Just got diagnosed with fairly advanced Hashimoto's Thyroiditis 6 weeks ago, have 6 goiters, taking 12 prescriptions. Then there's a bony cyst in the socket (glenoid) of my right shoulder, may need a joint replacement, maybe just arthroscopic removal of cyst. It depends on how much other damage there is. A lot of the spondylosis due to osteoarthritis has been taken care of by corticosteroid injections. I haven't seen the MRIs, but the report states there's a lot of other "mechanical" damage to the joint, as well as some effusion. Seeing a major orthopedic specialists in shoulders at Kansas University Medical Center on August 17th. I won't know anything else until then. So I may be 3 years younger, but I will bet I feel 10 or more years older. At least you are getting your exercise walking in to the village. Ignore this rubbish. It's just the hydrocodone, orphenadrine, and diazapam talking. But for some reason I feel you understand this jargon.

Sometimes simplifying things works wonders (we're back to your computer now). If you were running one of the Open GL screensavers, that could make a huge difference too. Sounds like you may have things running much better already. This wouldn't have taken so long if I had asked the right questions. So much for me being helpful.

Have a great Sunday,
Dan

Hi there Dan et al
I took quite a break as due to a sudden workload, this case was put onto the back burner.
Well, I'm back in Windows!
The main reason being that my friend has taken out the fan which fans the secondary hard drive. He brings a new one on Friday. 
Anyway, I have been doing some more thinking on this:
Now in this thread, members have suggested that part of the problem may be that Ubuntu is on disc 1, and the files I work on are in disc 0, and that part of the "crossing over" may be an issue.
So I have had an idea: Hre is a picture of my hard drive set-up (courtesy Windows Disc management ;) )

[IMG]http://farm2.static.flickr.com/1317/1047680460_87173d143f_o.gif[/IMG]

So I was thinking, "Why not stored my data on that little partition at the end of disc 1?"

If members think this a worthwhile thing to do, I'll study it...:guitar:


best wishes
John

PS:
> At least you are getting your exercise walking in to the village. Ignore this rubbish. It's just the hydrocodone, orphenadrine, and diazapam talking. But for some reason I feel you understand this jargon.
I do indeed. Steady on the hydrocodone et al, mate!

> So I may be 3 years younger, but I will bet I feel 10 or more years older. At least you are getting your exercise walking in to the village.
Oh, I wager, Dan that if you race me to the village shops, YOU will be the winner! :-)

[http://www.youtube.com/watch?v=QH8_4fX3SQA]("http://www.youtube.com/watch?v=QH8_4fX3SQA")

Take Care, Now....

[color=blue]PC: IBM Think-Centre A-50 : 40 Gb

Hard Drive 0) Windows XP-Pro (NTFS), partitioned (my data folder on a FAT32 partition)
Hard Drive 1) Ubuntu 7.0.4 “Feisty Fawn”, : 110 Gb (ext3)[/color]

---

### Post by djchandler on 2007-08-09
> **Andavane said:**
> Hi there Dan et al
I took quite a break as due to a sudden workload, this case was put onto the back burner.
Well, I'm back in Windows!
The main reason being that my friend has taken out the fan which fans the secondary hard drive. He brings a new one on Friday. 
Anyway, I have been doing some more thinking on this:
Now in this thread, members have suggested that part of the problem may be that Ubuntu is on disc 1, and the files I work on are in disc 0, and that part of the "crossing over" may be an issue.
So I have had an idea: Hre is a picture of my hard drive set-up (courtesy Windows Disc management ;) )

[IMG]http://farm2.static.flickr.com/1317/1047680460_87173d143f_o.gif[/IMG]

So I was thinking, "Why not stored my data on that little partition at the end of disc 1?"

If members think this a worthwhile thing to do, I'll study it...:guitar:


best wishes
John

PS:

I do indeed. Steady on the hydrocodone et al, mate!


Oh, I wager, Dan that if you race me to the village shops, YOU will be the winner! :-)

[http://www.youtube.com/watch?v=QH8_4fX3SQA](http://www.youtube.com/watch?v=QH8_4fX3SQA)

Take Care, Now....

[COLOR=blue]PC: IBM Think-Centre A-50 : 40 Gb

Hard Drive 0) Windows XP-Pro (NTFS), partitioned (my data folder on a FAT32 partition)
Hard Drive 1) Ubuntu 7.0.4 “Feisty Fawn”, : 110 Gb (ext3)[/COLOR]

John,

That race might be close, but at least you know the way, and where the cracks and potholes are in the road. Besides, my bursitis in my right hip is flared up too. Using Lyrica to ease back on the hydrocodone. Had several good days, no narcotics, but in the hydrocodone again tonight. BTW, that's a goiter with six nodules, just on the right side. Phone conversation with my MD's nurse got a little confusing. Seeing top notch orthopedic surgeon next week about the shoulder. Things will get better soon.

I'll have to come to England for that race some day. I'm a bit of an Anglophile anyway. I keep threatening my wife with flying the Union Jack on the Queen's birthday. Love the Barclay's Premier Football League too, but I have to subscribe to one teams' feeds to see games this year. How do you feel about an Arsenal fan?

Back to the computers, I think you are on to something with the multiple partitions across two different hard drives. If your data will fit, I think that's a good idea to put it on the same HD with Ubuntu.

Saw your budgie on YouTube. My cat that liked it too.

Have fun!

Dan

---

### Post by Andavane on 2007-08-14
Hi Dan...
There has been some development.
The friend in the village has returned from holiday; he came round and listened to the noise
(I booted the machine from cold - it's noisiest that way). He found that the wee fan which cools the hard drive on which Ubuntu is installed was not quite riding free; so he removed it to order a replacement.
During that period I was Ubuntuless and hence in Windows! 

Anyway the news is that he has replaced the fan, and thus far Ubuntu has behaved fine.

The only slight thing is, every so often when I boot (mainly from cold) I get the message:

"GRUB loading stage 1.5", and there it hangs; so I turn it off, then in again and it's fine. What does that mean?

So as things are presently, I think I just use it again and see how things go, eh?

[color=blue][i]PC: IBM Think-Centre A-50 : 40 Gb
Hard Drive 0) Windows XP-Pro (NTFS), partitioned (my data folder on a FAT32 partition)
Hard Drive 1) Ubuntu 7.0.4 &#8220;Feisty Fawn&#8221;, : 110 Gb (ext3)[/i][/color]

best wishes

John

PS: If you plan on a visit to come and see the Queen, I'll have the pot-holes in the road plugged, just for you.

---

### Post by djchandler on 2007-08-14
> **Andavane said:**
> Hi Dan...
There has been some development.
The friend in the village has returned from holiday; he came round and listened to the noise
(I booted the machine from cold - it's noisiest that way). He found that the wee fan which cools the hard drive on which Ubuntu is installed was not quite riding free; so he removed it to order a replacement.
During that period I was Ubuntuless and hence in Windows! 

Anyway the news is that he has replaced the fan, and thus far Ubuntu has behaved fine.

The only slight thing is, every so often when I boot (mainly from cold) I get the message:

"GRUB loading stage 1.5", and there it hangs; so I turn it off, then in again and it's fine. What does that mean?

So as things are presently, I think I just use it again and see how things go, eh?

[COLOR=blue][I]PC: IBM Think-Centre A-50 : 40 Gb
Hard Drive 0) Windows XP-Pro (NTFS), partitioned (my data folder on a FAT32 partition)
Hard Drive 1) Ubuntu 7.0.4 “Feisty Fawn”, : 110 Gb (ext3)[/I][/COLOR]

best wishes

John

PS: If you plan on a visit to come and see the Queen, I'll have the pot-holes in the road plugged, just for you.

John,

We have pot holes in Kansas too. I'm sure I'd like to see the Queen, but my first priority may be seeing Robin van Persie score a goal at Emirates Stadium since I will already be in London. It's a shame I couldn't attend a game at Highbury, but they are selling the vacated real estate, with new luxury condominiums erected upon the old pitch, at exorbitant prices. That's too rich for me. If I retire to another country, I could stretch my money further in South America.

As for your hard drive, if it's more than 3 years old, I would make sure I had all my data backed up, and begin planning to replace it. If heat was causing it to spin slower, there could be damage to bushings inside.

Good luck!

Regards,
Dan

---

### Post by Andavane on 2007-08-21
Dear Members:
Perhaps we may be now able to glean a clue from this long-running issue.

A reminder of the symptoms: Things begin to crawl slowly: when clicking on a window, the outline slowly appears, things begin to crawl like a snail, never getting anywhere.

A member has taught me a few commands;

I now shut down with "sudo halt" or "sudo reboot", and "ctr-alt-baclspace" when things get really stuck;  I see some messages.

The one which has repeatedly displayed goes something like:

[color=blue]Starting powernowd:
S20 powernowd: cannot create/sys/devices/system/cpu/cpu0/cpu freq/scaling governor
directory non-existent
cpu scaling not supported[/color]

Then when you type "Esc" (or anything) you get the symbols

[color=blue]^[^H[/color]

every time you type.

Are members able to diagnose what may be wrong now? Dow we have a clue? It doesn't sound very healthy from here!

Am now back in Windows (Ubuntu getting too unstable) and the is manuscript correcting which I must do.

Regards

John

PS: Hi Dan

---

