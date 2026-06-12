---
title: "having some problems installing ubuntu"
date: 2007-03-02
forum: Absolute Beginner Talk
---

### Post by someusername on 2007-03-02
Hello everybody

I'm having some trouble installing Ubunto on my machine. First, let me give the specs, so that you can perhaps can spot any troubles early.
CPU: Core 2 Duo 6600
RAM: 2 GiB, DDR2
Graphics: AMD/ATi X1950 Pro
Harddrives: 2x350 GiB SATA2 -- striped mode, one partition, windows xp pro (0) 
and 1x160GiB SATA partitioned in 2 partitions, "primary" and "secondary". (well, now it's just one, the primary was a previous windows installation which I wasn't using at the time of ubuntu installation.
Screen: DVI hp2335

Anyhow... I burnt the CD and rebooted. Ubunto asked if I wanted to install or start it. I did. It started... Slowly. At the progress bar screen, the screen got some digital noise for a couple of seconds. (don't like that) and also part of the progress bar put itself outside itself, so to speak.

So it started and I was happy. This is cool. First thing I notice is that everything lags... Must be graphics drivers I think. Anyhow, I continue with double clicking the install. Accidentally clicks cancel at one stage and computer freezes. Great.

I do a manual reboot. Start Windows... Consider very hardly whether it's worth the trouble!!!

Reboot again, start ubunto, thinking, let's try some stuff out and see what I like of it then, before I install. But the graphics still lags and laggy interfaces pain me a lot, being amongst other things an interface designer for a living...

Go to AMD's site and find linux drivers for my graphics card. It says download, so I do that. Double click the file... Nothing special happens. (me: hmm... no installer??? w00t?? and that .run? eh?) Reads some on the AMD page: "navigate to where you saved the file and run the installer by [...]" (me: aha! so I need to use the console!) I go to the menu and try to find somewhere to get the console up... Nothing... I go to add/remove programs. Find the console there - not installed (me: eh? isn't linux all about nerdery with the console and stuff???) Start installing the console. It downloads the pieces. Starts installing (and mind that I'm still running from the CD!), then freezes. AGAIN! omfg.

I restart manually again, thinking, this can't be good for the rotating disks in my harddrives...

I figure I should call some of my friends who are linux enthusiasts. Do that... talk a bit with them... They convince me not to give up.

So I try again... Launch the slow ubuntu again. (got CD:52x Read, dvd burner, but it's still slow!) Start the install. Mind the cancel button (it's very dangerous). I was told to go into manual mode with the partitions (primary, secondary). I do that. My striped drives are listed as separate drives (wtf???) and as scsi (wtf??) and as unformatted (wtf??), confused... Then there are three others as well. One seems to be my USB-memory (1 GiB) the other two my partitions saying NTFS. (which they actually ARE! wow...) So I choose the primary partition. It thinks a little and starts that partitioning program. Moving on, I'm thinking, no crashing; great! Then I remove the primary partition, more or less by deleting it. The space becomes unused/unformatted/whatever it's called. So I add a partition, ext3 (and what are all those other types??) and a small swap (why, when it's the same disk, I think, what's the aim?)... Move on. Come to a screen where it tells me to select three partitions, one for root, one for swap and one for one dropdownlist-item out of four (where the first item is completely blank). My secondary partition is selected to be used for one item... I try to make set it to the blank item. Click next. It tells me I have to select three.

I freak out (me: wtf is this ****??? let me just install the **** on the two free partitions and be done with it!!! all my work is on secondary so you can't use that you greedy *******!) and press cancel. The computer freezes and I have to manually reboot.

It was the first time I tried linux ever... Should I ever bother again? And I'm a developer; imagine the pain for a regular user. (AND IMAGINE PRESSING NEXT WHEN _ONE_ (not the complete striped unit or both) OF MY STRIPED HDDs WAS SELECTED IN THE FIRST SCREEN: WHAT A MESS!)

What I'm looking for is really a good development environment where I can test out stuff like ruby on rails and perhaps PHP if I can get over the nasty syntax..

Could someone advice?

---

### Post by tsanoff on 2007-03-02
1. The lagg you get is probably from the fact that you are running the os from the CD, and your drive may be a bit slow. I am running 2 servers and 3 laptops with ubuntu and no lagg at all. 

2. Software for linux can be gotten in variuos ways, source, packages and tarballs. If you are looking for something you can double click and install, just download packages that end with an extention ".deb" 

3. The ubuntu distros have drivers for the ATI x1950, just open up your synaptic package managment and search for ATI (after install would be prefered).

4. Every linux distro requires a SWAP partition, which is equal to the windowz's virtual memory but causes less problems reguarding the fragmentation.  i recoment that you let the installer choose your hard disk options for you so it would be less confussing, just make sure you dont select your windowz partition, otherwise bye-bye microsoft. The reason why you get so many mount options is in case you want to mount a backup device, or partition, or you want to mount a partition (ex. hda3) to your /home/username where your local settings and documents are stored in case you decide to try out a diffrent linux distro or you system crashes. You dont get that with windowz.

5. For a development suite, you can use the system itself!!! (hint-hint gcc, g++) But if u want an idk, u can try eclipse it is pretty good for java, c and c++ development.

Cheers mate!!!

---

### Post by someusername on 2007-03-02
> **tsanoff said:**
> 1. The lagg you get is probably from the fact that you are running the os from the CD, and your drive may be a bit slow. I am running 2 servers and 3 laptops with ubuntu and no lagg at all. Might be yes... Strange though since there's no data to be read from the CD by moving a window, but the GUI should be loaded into RAM.... no?

> **tsanoff said:**
> 2. Software for linux can be gotten in variuos ways, source, packages and tarballs. If you are looking for something you can double click and install, just download packages that end with an extention ".deb"  Thanks m8

> **tsanoff said:**
> 3. The ubuntu distros have drivers for the ATI x1950, just open up your synaptic package managment and search for ATI (after install would be prefered). What's a synaptic package management? What do I do when I find ATi? Does it help solve the lagging interface when using the CD or should it all be fixed when I have completed the install?

> **tsanoff said:**
> 4. Every linux distro requires a SWAP partition, which is equal to the windowz's virtual memory but causes less problems reguarding the fragmentation.  i recoment that you let the installer choose your hard disk options for you so it would be less confussing, just make sure you dont select your windowz partition, otherwise bye-bye microsoft. The reason why you get so many mount options is in case you want to mount a backup device, or partition, or you want to mount a partition (ex. hda3) to your /home/username where your local settings and documents are stored in case you decide to try out a diffrent linux distro or you system crashes. You dont get that with windowz.

Alright, I understand the SWAP part, but why did it want me to select three different partitions? If I let the installer choose, and press next, I lose Windows because it doesn't seem to recognize RAID? I don't really care to do it the long way if I just understand what it's asking for... What's hda3 and why would my system crash? And what does "mount" mean in the context of changing the size and positions of my harddrive partitions? What don't I get in windows? The ability to move the personalizations to different installations of the OS?

> **tsanoff said:**
> 5. For a development suite, you can use the system itself!!! How do you mean?

> **tsanoff said:**
> (hint-hint gcc, g++) Do you mean changing the OS itself? Because as I wrote, I'm looking for an environment to try out RoR in, not specifically an IDE (that's the next step ;)). > **tsanoff said:**
> But if u want an idk, u can try eclipse it is pretty good for java, c and c++ development. yeah, thanks, I know :) My friends at the informatics program use it ^^ and Hibernate has some sweet plugins to it as well (reflection of classes at runtime as tooltips/dropdowns as you write XML mapping files, just to take one example)

> **tsanoff said:**
> Cheers mate!!! Cheers to you too ^^. Still confused though...

---

### Post by someusername on 2007-03-02
I'm also thinking that perhaps ubunto isn't the right distribution for me? Is it?

---

### Post by Maestro23 on 2007-03-02
Just want to throw out some links for the OP:

[http://www.psychocats.net/ubuntu/index](http://www.psychocats.net/ubuntu/index)

[http://www.cutlersoftware.com/ubuntuinstall/](http://www.cutlersoftware.com/ubuntuinstall/)

---

### Post by someusername on 2007-03-02
Yeah, ok, so I chose the HDD and let the partitioner take some x amount of space on the "third" drive.

It installed in 12 minutes. (compared to Windows' 20 minutes).

It told me to be sure to take out the cd, before restarting. So I pressed restart-button and simultaneously pressed the CD-eject button on the computer. The system showed the reverse-loading bar. Then it came to a halt, the cd came out, I took the cd, and then the turning-off screen told me to remove the cd then press enter... So I inserted the empty tray and pressed enter... Nothing... Pressed CTRL+ALT+DELETE. The screen told me the same thing, but ejected the CD-try. It wouldn't restart...

Again, manually restarting with reset button... Computer starts.

Windows loads.

F:\>CHKDSK

Checks F:, finds (128, $Bad) sector. 

Windows starts, tells me a new hardware item has been successfully installed. My files are still there.

So how the * do I start linux then??!

---

### Post by someusername on 2007-03-02
Ok, that does it... The installation process of Ubuntu is seriously flawed, buggy and sux generally.

I tried to change the harddrive prio. in bios to make the ubuntu harddrive prio 1 instead. Got a message "Cannot start operating system...". That was it.

So to the developer: you should SERIOUSLY fix the partitioning tool to make sense, work for multiple harddrives and work for RAID, and make it stop saying I've got scsi harddrives as well. And the quitter doesn't work either.

---

### Post by someusername on 2007-03-02
Stage one:
[IMG]http://img77.imageshack.us/img77/1513/dsc00111ac8.jpg[/IMG]

Two:
[IMG]http://img252.imageshack.us/img252/3170/dsc00112ph1.jpg[/IMG]

Three:
[IMG]http://img252.imageshack.us/img252/7286/dsc00113li1.jpg[/IMG]

Four: 
[IMG]http://img409.imageshack.us/img409/4255/dsc00114xn2.jpg[/IMG]

Five, the great result!
[IMG]http://img96.imageshack.us/img96/5748/dsc00115lq0.jpg[/IMG]

---

### Post by someusername on 2007-03-09
Bump.

Someone help!

---

### Post by someusername on 2007-03-11
bump

---

### Post by Famicommie on 2007-03-11
Seems like the install got borked.

Now, personally, I had virtually no problems at all with Ubuntu. It ran pretty nice from the liveCD (though the resolution was only 640x480 until I installed the OS and the proper ATI drivers). I didn't use partitions, I happened to have a hard drive sitting around and installed onto that.

Your first problem seems to be that GRUB wasn't installed. On your master drive, a program called GRUB should take the place of the windows MBR. It's what allows you to choose which OS you want to boot into. Since GRUB is installed by default, I am assuming that the whole process got messed up somewhere.

Since the process only takes ten minutes anyways, I suggest that you try installing again. Go get yourself a beer or something while it does its business, and make sure not to remove the disk before the tray automatically pops open.

You might also want to google search the compatability of your RAID array with Ubuntu; some RAID arrays simply don't work well with various flavors of linux.

Also, Ubuntu DOES come with a console, called Terminal. It will be under the menu Applications->Accessories

When it comes to installing drivers/programs/libraries, use the repository. Open up System->Administration->Synaptic, and you will be assaulted with thousands of files that will automatically download and install if you so choose. There are no tedious install wizards to go through, no threats of malware, etc. Repositories are one of linux's main draws.

---

### Post by fdrake on 2007-03-11
did you try to use a different cd-rom or ubuntu alternate? 
[http://ubuntuforums.org/showthread.php?t=368435](http://ubuntuforums.org/showthread.php?t=368435)

---

