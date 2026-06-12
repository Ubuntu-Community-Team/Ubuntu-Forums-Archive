---
title: "Installation Issue"
date: 2006-10-19
forum: Absolute Beginner Talk
---

### Post by Coinnach on 2006-10-19
Hi all,

Firstly do want to say that I did do a lot of research on trying to resolve my install issue but between being new to linux and having a piece of crap to try and install it on, I guess I failed miserably.

I am trying to install Ubuntu 6.06 Server edition onto an eMachine - ok once you have stopped laughing - reason is I am trying to get 2 of my small start-ups running on more linux boxes than Windows (licensing is a killer). This ebox is an old machine. I put in a new 80Gb hard drive, added some more memory (now 256Mb) and then I found out that the CDRom isn't working and it isn't the cdrom.

I added a USB cdrom but the eMachine doesn't support booting from USB. I tried following this thread - [https://help.ubuntu.com/community/Installation/WithFloppies](https://help.ubuntu.com/community/Installation/WithFloppies) - but got totally lost. I don't know the Linux commands - I am a totally virgin.

I get totally lost and have tried GRUB and some other things I have never heard of.

If anyone out there can suggest a mthodology for me to achieve my goal - getting Ubuntu installed. I would greatly appreciate it.

Remember if you ask me any questions then I will answer them as a complete moron because I am that new.

Thanks in advance

---

### Post by podunk on 2006-10-19
There is nothing wrong with e-machines. :-) They are good basic boxes to do the grunt work of the computer world.

When you say "It's not the CD-ROM" - does this mean drive itself works in another OS but not Linux? 

Does the CD work on another machine - and if yes can you borrow the CD-ROM from that machine to try it in the Linux machine to be?

If the CD doesn't work on another machine maybe you should re-burn it at a slower speed.

---

### Post by CatKiller on 2006-10-19
Or as an alternative to getting a cd-rom drive that works into that computer, you could put the hard drive into a computer with a working cd-rom drive and install it that way. Whatever would be easiest for you, really.

---

### Post by Coinnach on 2006-10-20
When I say its not the CDRom, I have swapped in multiple CDRom devices and changed ribbon cables etc. I don't know if the original cdrom was working in the box - the box had been sitting dormant for  8 mths.

Catkiller, thanks for the suggestion - question if I install onto the hard-drive in a different machine - what is the procedure then when I switch it back in to the other machine - drivers etc, will Ubuntu automatically detect the new hardware?

---

### Post by CatKiller on 2006-10-20
As I understand it, the thing you're most likely to have to do is ```
sudo dpkg-reconfigure xserver-xorg
``` to reconfigure your keyboard, mouse and graphics. It's probably a bad idea to use a computer that's vastly different - like a Mac if you want to use a x86 computer, and if you install an optimised kernel you may have to switch to a more appropriate one after you switch.

It is possible to install over a network, although I've never done it and I don't know exactly how it works. That might be an option to look into as well. Also, by choosing the Server install you've chosen to not have a GUI of any sort. Either you're more brave than I am, or you'll want to get Internet access to it as quickly as possible to install one of the desktop packages.

---

### Post by Coinnach on 2006-10-20
Brave or foolhardy Catkiller -not sure which.

I want the server version because thats what I will want to run on the other servers once I can get the install process down pat. Also I figure it is a good way to learn Linux commands etc - in at the deep end.

The link I posted above I was doing well with except for a couple of things.

1. One the Http: mirror site he talks about no longer has the deboootstrap files so I used an Aussie FTP mirror and got the file.

2. Doesn't say what packages I need to install in order to get everything I need to continue following his lead.

3. He says to type ALT+F2 to get to the editor but the only one I can get to is the default Debian editor.

4. I assume the ar- command runs correctly but the zcat command fails stating it doesn't understand the --arch command, also the mirror is incorrect again.

At this point I can get access to the USB cdrom with the Server ISO but I don't know what commands I need to start the install and what files to use.

Any suggestion greatly accepted as the boss is now bugging me over it.

---

### Post by podunk on 2006-10-20
If you put the disk in another machine will it boot? e-Machines are so plain jane that Ubuntu shouldn't have any problems (well, win modems)and I'd tend to suspect a hard problem rather than a sowftware problem.

Since you have a new 80 gig drive I assume there is no OS on the machine. Will the machine load a windows install cd? Any chance the new memory is of a different speed or latency than the old?

---

### Post by Coinnach on 2006-10-20
The memory is the correct version per eMachine. I think that the motherboard ribbon connector is suspect, it will allow the hard drive to function but not the cdrom - ie there is power etc but no transferral of data.

Swapped in a different CDRom and a different ribbon with no joy. Hence the Debian floppies route.

---

### Post by Iowan on 2006-10-20
> **Coinnach said:**
> ...I think that the motherboard ribbon connector is suspect, it will allow the hard drive to function but not the cdrom - ie there is power etc but no transferral of data.
I've heard of (but unfamiliar with) eMachines.  Are the HD and CD sharing a cable?  Does the CD need to be set "slave" (or is it "cable select")?

---

### Post by underdog512 on 2006-10-20
> **Coinnach said:**
> Hi all,


If anyone out there can suggest a mthodology for me to achieve my goal - getting Ubuntu installed. I would greatly appreciate it.

Remember if you ask me any questions then I will answer them as a complete moron because I am that new.

Thanks in advance

you know what.  If you don't mind spending a little bit of cash, check [http://system76.com](http://system76.com).  they have really great deals and get started with ubuntu in a snap.

---

### Post by Coinnach on 2006-10-20
Iowan - in this case the CDRom and the HD use separate ribbons and controllers. The CDRom is set to cable select, I have also changed it to Slave. I have tried it in tandem with the HD, swapped it to the HDs IDE controller - every possible combination - nothing can't get it to boot or be recognized when I install Debian. I tried to upgrade the BIOS but can't find an update for it. eMachines website don't have any updates I can find for this machine.

Thanks Underdog512 - I will check it out.

Update: I have managed to get Debian on there with floppies and network connection, so maybe I can get it to dual boot with ubuntu. Will it then be possible to remove Debian?

---

### Post by Coinnach on 2006-10-20
Well I found this thread - [http://www.ubuntuforums.org/showthread.php?t=75372&highlight=debian+ubuntu+floppies](http://www.ubuntuforums.org/showthread.php?t=75372&highlight=debian+ubuntu+floppies) - saviour and I am running through that now. I guess that I will have version 5.10 on the box after this is finished. I have two more questions to ask:

1) What is the easiest way to tell which version I am running?

2) What are the steps involved in upgrading from 5.10 to 6.06?

Thanks for everyone's help and suggestions

---

### Post by rccharles on 2006-10-20
>  Originally Posted by Coinnach  View Post
...I think that the motherboard ribbon connector is suspect, it will allow the hard drive to function but not the cdrom - ie there is power etc but no transferral of data.

Have you checked your bios? 

You may have to change your bios to boot from the cd.

Many PC have two ide connectors which support two devices per connector.  A lot of time your bios will tell you how many ide connectors you have and the number of devices supported on each connector.

Most hd and cd devices have a chart on the back which indicates how to set the jumpers.



Did you say you had an external encloser?  

You could put the hd in the external excloser and connect the cd-rom to the pervious hd connector.  Boot up the cd-rom with a live cd. Install onto the hd. Move the hd back to the pc.
* I have not tried this.  *

--- 

Old machines are very cheap on ebay.

---

You could put the hd in some other pc and dual boot the pc so that you can learn ubuntu.


I'd start with the desktop version so you can learn Ubuntu.  My understanding is that you will be running the same software.  Doesn't seem bad to me to 'waste' a little hd space on destop software.  What's a gig or two today.

---

You could try the Debian net install.  Look at the floppy option.

[http://www.us.debian.org/distrib/netinst](http://www.us.debian.org/distrib/netinst)

You'd loose a major advantage of Ubuntu ... namely, these forums.

Robert

---

### Post by Coinnach on 2006-10-21
Hi Robert,

Have tried ever setting in the BIOS to see if I could get it to boot to CD - Two IDE controllers in it, tried everything no joy. Jumper settings are correct.

I have tried an external USB CdRom but the BIOS doesn't allow boot from USB.

The BIOS on this eMachine is AMIBios (American Megatrends) but the Motherboard is Florida TG 109554 (I think made by a Korean Company) - searched exhaustively for a BIOS upgrade but AmiBios don't have updates for non-AmiBios Boards and the Korean company is MIA - found an update for a Florida TG Board but not sure what version so that is out.

I like the System76.com machines that one of the poster's directed me to, I think I would purchase a new machine rather than go old. This is to be a test box and to justify switching to Linux and away from Windows.

As for installing Desktop, thats cool I'll run with that. I read on a post on the forum that you can install server and then install desktop on top for a GUI - thats pretty cool. At this stage I have tried every type of install I could - thank God I found the post listed above - at least something is installing.

---

### Post by Quintin Riis on 2006-10-21
> **CatKiller said:**
> Or as an alternative to getting a cd-rom drive that works into that computer, you could put the hard drive into a computer with a working cd-rom drive and install it that way. Whatever would be easiest for you, really.
What he said.  After installing if you crash onto a command prompt, login and do 'sudo dpkg-reconfigure xserver-xorg' to make a new X config file.  

Don't worry about drivers.  Linux is fine if you move it to a totally different machine unless you have optimized binaries and move down an arch or have a very modified kernel.

---

### Post by Coinnach on 2006-10-21
Thanks Quitin, that will be the next step in my odyessy - a good learning experience in installing Linux!

---

### Post by CatKiller on 2006-10-21
> **Coinnach said:**
> Have tried ever setting in the BIOS to see if I could get it to boot to CD

Allegedly it's in the Boot menu ("Boot Device Priority"), that you get to by pressing right from the first screen, but I've never used either an eMachine or American Megatrends BIOS - I just got that from their website.

---

### Post by Coinnach on 2006-10-21
Hi CK, yeah I have looked in the BIOS and tried everything they had listed, but nothing worked and there was no USB boot.

I did manage to get CDRom access after I had used the DEbian Floppoes but couldn't get the Ubuntu Install to run - ie I don't know the commands to initialise the install. The CD itself is burnt correctly as I stuck it in my laptop and it booted.

I tracked down a thread by Curufir (sp?) about Network Install Floppies for Ubuntu. It has worked to the point that it is now installing the base system from the Ubuntu Mirror - left it running at the office as I had to get some sleep. Hopefully this will install and I can go from there.

---

### Post by CatKiller on 2006-10-21
Excellent. My fingers are crossed for you.

---

### Post by Coinnach on 2006-10-21
Thanks mate - appreciate yours and everyone elses help and suggestions

---

### Post by CatKiller on 2006-10-21
Welcome to the community.

---

### Post by Coinnach on 2006-10-22
Thanks Catkiller - glad to be aboard!

Success! I have an installed version of Ubuntu - that net install floppies thread is worth its weight in gold!

Now to learn how to use it - expect more dumb questions

---

### Post by CatKiller on 2006-10-22
> **Coinnach said:**
> Success! I have an installed version of Ubuntu - that net install floppies thread is worth its weight in gold!

If there isn't one already on this forum, it might be worth you writing a HOWTO on how exactly you did it - I'm sure there are many people that would be in the same situation as you were and have no idea how to proceed.

Good luck with the other computers, too.

---

### Post by Coinnach on 2006-10-22
May just do that CK although I can't take credit as I just followed Curufir's lead

Quick question for you though - how do you upgrade from breezy to dapper? I tried sudo apt-get dist-upgrade but it returned no updates.

---

### Post by CatKiller on 2006-10-22
> **Coinnach said:**
> Quick question for you though - how do you upgrade from breezy to dapper? I tried sudo apt-get dist-upgrade but it returned no updates.

I think that I just had a notification in the update manager asking if I wanted to upgrade, and that handled the rest. You may find [this page]("https://help.ubuntu.com/community/DapperUpgrades") of interest, though. I think that if you're still on the server install and on the command line you could change each instance in your /etc/apt/sources.list of breezy to an instance of dapper, and then ```
sudo apt-get update
sudo apt-get dist-upgrade
``` That upgrade page may well give you more information and tell you not to do that, though. Hey, you could wait for a few days and then update from Breezy to Edgy.

---

### Post by Coinnach on 2006-10-24
CK - thanks for the link to the upgrade page, much appreciated.

Have a weird question for anyone that can help, I am upgrading from Brezzy desktop to Dapper on an eMachine eTower 466is - it took almost 24 hours to download everything and go through the upgrade process. I kicked off the remove and clean up portion of the upgrade approx 9 hours ago and it is still running - in the terminal window the last thing it says it completed was to do with Openoffice dictionary list - the progress bar is just sliding across the screen from side to side like Kit's light in Knightrider.

Has it stalled? Is it still running? If I force a reboot will it start up again? If it is still running how much longer?

Does anyone have an idea?

---

