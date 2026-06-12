---
title: "Something that is obviously needed!!"
date: 2007-06-20
forum: Absolute Beginner Talk
---

### Post by gcos7 on 2007-06-20
;)Okay, I got your attention, now for what is needed:

I have posted various questions using various virtual machines to get a virtual machine running in Linux using my existing Windows partition.  This is on a dual-boot laptop - Windows XP in 1 partition, Linux swap and ext3 in the other 2 (Ubuntu 7.04).  I CAN NOT get this to work.  I have gone into custom setup in VMware Server and selected physical partitions (Windows and the ext3 Linux partition).  Windows starts up, show the Windows XP screen briefly, then blue screens with a screen that says Windows has detected an error and has been shut down, check for viruses, remove new drives and adaptors, etc..  At one point in time I actually had VMplayer boot Windows but the mouse wasn't available and it wanted to activate Windows again - which got me into a deadly embrace:  just booting Windows wanted to reactivate because of hardware changes, booting the virtual machine wanted to reactivate because of hardware changes, around and around and around.

I can tell from the number of views of my previous queries that I am far from alone in this.  Just do a search/advance by my user name and check the view counts on my questions about VMplayer, VirtualBox, VMserver and generic "Windows in a virtual machine in Linux" type questions.

I've been through many web sites, many posts on this forum and many trial and error tries of each of the virtual machine products and I get nowhere.  I feel I've done my research - I now need help!!

Why am I so persistent with this??  Well, you know the hype about Linux and about Ubuntu in particular.  I went through a lot of work to get my wireless working and my video working.  I'd like to use LInux as my main OS, with just access to Windows for Family Tree Maker 10 (until a Linux replacement is created) and for (yes, laugh!!) access to shockwave player so I can play the daily jigsaw.  I hate dual-booting.  I'd like Windows just to be in a virtual machine in Linux.  
I've tried creating a virtual disk and loading it from the system restore disk provided with my laptop by Gateway.  I get the same blue screen abort when I go that way.

Thanks.:)

---

### Post by gcos7 on 2007-06-20
;)I really do need help here.  If dual-booting is my only choice, I hate it and then would have to go back to the dreaded Windows.  Help me keep my Linux - help me find a solution.

---

### Post by paradoc on 2007-06-20
Do you have a Linux/Ubuntu _Experienced _ friend  who can physically help you out (i.e. do a clean dual boot for you)? IMHO you'll soon get to like it..

    I have a triple boot (Feisty and Edgy on 20G drive) with $win$ on the slave IDE 80Gig drive (which I can't reach in windows unless I pull the PC to bits and shift the pins, but Gnome partitioning has no trouble at all in making it (well not fully) useable, as it's NTfs, but completely and comprehensibly  bootable in its own right as a WindowsXP system....slight snag, you have 8 seconds or so on boot-up to your other choices, but in practice this hasn't proved problematic so far.                              

    I would think it's a tad better than your  virtual Windows in Linux--this can be done-- see postings,    Personally,  I didn't much like the VM way of doing things It's OK, but after  I tried this early on , it didn't  impress me too much.

    Currently, I use a Feisty liveCD on my laptop when I'm away from base station, and the linksys
wireless link works even better  than on the provided Asus-win  setup.

Hoping this helps a little!;)

---

### Post by molly_001 on 2007-06-20
Courtesy of ghost_ryder35 who is very adept at the VM and VT environment in Ubuntu Linux:

(I am just copy-paste here)

Good links:
[http://www.easyvmx.com/](http://www.easyvmx.com/) (Create virtual machines for VmWare player or Server)
[http://monkeyblog.org/ubuntu/installing/#source](http://monkeyblog.org/ubuntu/installing/#source) (Learn how to install **anything**)
[http://www.howtoforge.com/ubuntu_fei...e_server_howto](http://www.howtoforge.com/ubuntu_fei...e_server_howto) (How to Install VmWare Server 1.0.3)
[http://ubuntuforums.org/showthread.p...+player&page=2](http://ubuntuforums.org/showthread.p...+player&page=2) (How to uninstall VmWare)


VmWare Player or Server (Just in case you have files that will only run on Windows, or your in to Virtualization)
(To completely remove VmWare Server or Player you need to run the command sudo apt-get remove --purge vmware-server vmware-player if you installed from the repositories or sudo vmware-uninstall.pl if you installed from a .tar package. You also need to run sudo rm -r /etc/vmware two times to make sure it removes the folder!)

---

### Post by gcos7 on 2007-06-20
Thanks for the replies!:D

I'll do some more research via the links you have both provided, and let you know if I succeed.;)

---

### Post by hyper_ch on 2007-06-20
why not simply use a virtual windows partition instead of a physical one?

---

### Post by gcos7 on 2007-06-20
First, some results of my checking the links mentioned prior:

I appreciate the information, but I have gone beyond what is there and have gone into the VMware server custom setup.

As far as running a virtual partition is concerned, if you read me 1st post in this thread, you will see I have already tried that, and it resulted in the blue screen when Windows tried to boot.  Also, I have limited disk space in which to work (60gig total)

If I have not specified things clearly, I apologize.  Here's my current setup:

Gateway MX3215 laptop
dual-boot
  1. Windows XP
  2. Ubuntu LInux 7.04 (feisty fawn??).

I am running LInux, have installed the VMware Server, gone through the custom option for creating a virtual machine, defining the disk as physical, and including my Windows XP partition and my Ubuntu ext3 partition (needed to save the .vmdx to).  The idea is to avoid dual-booting, and instead run Linux as my OS and run Windows, when it is needed, within Linux so I don't have to keep shutting down, rebooting, etc..  There was a web page I followed to do the physical disk thing within VMware Server for the virtual machine, but I don't remember nor have I kept the link as I "thought" it was going to work.

I hope that provides perhaps a better image of what I want to do.  Thanks for the replies, and please keep them coming.

When I get this to all work (notice I said when, not if), I will post a new thread as a how-to for installing Ubuntu 7.04 on a Gateway MX3215 laptop with a Broadcom 4318 wireless adaptor (note ndiswrapper), Via/s3g unichrome pro integrated graphics processor and of course getting VMware server to run with my existing Windows XP installation.

Thanks again guys!  Please keep replies coming!!:D

---

### Post by molly_001 on 2007-06-20
I'm going to send a note to ghost_ryder35 and ask him to have a look at this thread.  I think he knows a lot more, but the links I gave were from his advice to others who are in a beginning phase (which you are past).  [I would be in the beeeeeginer phase on VM.]

---

### Post by hyper_ch on 2007-06-20
All virtual partitions have been fine for me so far... either with vmware or vbox... but then how can you get a blue screen when booting from windoze install cd?

---

### Post by paradoc on 2007-06-20
You can edit the Grub boot loader:
```
gksudo  gedit  /boot/grub/menu.lst
```
I haven't needed this yet,  but you might want to  design your system to load however you want it to should you choose to dual boot , which seems to be a very popular choice, I think

---

### Post by gcos7 on 2007-06-20
Regarding the virtual partition comments - if you follow my other threads, you will see that it did not work for me.  My laptop came with a system restore CD, not a XP cd.  The restore runs within virtual partition, but when you try to boot windows it blue screens.  The best explanation I have received so far is that the restore defines hardware that is not known because of the virtual machine.

This brings me to another thing I have been thinking about but have no clue about:

I created a 2nd hardware profile in Windows and boot to it as recommended.  I am wondering if there is a way to get rid of the devices, etc., in the profile so Windows can re-detect them.  Will disabling them do it?  How do you disable devices with in a hardware profile?

thanks guys -please keep it coming!!:p

---

### Post by molly_001 on 2007-06-20
I have found that a lot of brands of these laptops that come with a Restoration CD media (or which use a Restoration partition; or, where the Restoration media writes a Restoration partition to the hard drive and then boots it)
... anyway, a lot of these particular laptops have proprietary master boot record (MBR) formats which cannot easily be worked alongside Linux *after* GRUB has been removed.  I can easily imagine that a VM situation would lead the same problem, wherein the MBR (once changed by GRUB or LILO installation to the MBR) cannot properly point a start of the partitions after GRUB is removed.

On reading your first post it reminded me of these experiences I have had with these OEM laptops.  I don't know if this has any directional finding for your query -- sorry if it does not.

P.S.  Is it a Dell laptop?

---

### Post by gcos7 on 2007-06-20
It is a Gateway laptop, and a very cheap one at that!  The mbr thing is something I have wondered about, but without the detailed knowledge you have.  instead, I noticed that for the VMware player, I had to run a command line to create a mbr file in the same directory as the rest of the virtual machine - is it possible I need something similar for VMware server, even if I haven't found a documented need for it?

Thanks again!!  Please keep it coming!!!:KS

---

### Post by gcos7 on 2007-06-20
Here's the command I found before for creating the mbr image:

dd if=/dev/hda of=windowsxp.mbr bs=512 count=63

I created a new virtual machine called "windowsxp", using the custom options as described earlier, and ran the above command to create a file called windowsxp.mbr in the same folder as the rest of the virtual machine.  Got same blue screen when booting.

---

### Post by gcos7 on 2007-06-20
:KSBTW - if it can be of help to anyone trying to help me find a solution, here's the website I used for trying to get this working in VMware player:

[http://www.advicesource.org/ubuntu/Run_Existing_Windows_Instalation_On_Ubuntu_With_Vmware_player.html](http://www.advicesource.org/ubuntu/Run_Existing_Windows_Instalation_On_Ubuntu_With_Vmware_player.html)

Again, thanks for the replies, and keep them coming!!;)

---

### Post by ghost_ryder35 on 2007-06-20
wow I am completly lost after reading this thread.  However, your trying to use a physical disk in VmWare and boot with the cd and it crashes?  Download a real XP cd from isohunt or something or borrow a friends and use your serial code.  That will solve the blue screen problem, and you should be rocken out then.  Let me know, I'll gladly make mine into an .iso so you can use it.  Cheap *** restore cd's :)

---

### Post by gcos7 on 2007-06-21
Sorry it took so long to get back here - my DSL was down until just a minute ago.

To further confuse matters to everyone:

- I tried using VirtualBox with a raw disk defined to my Windows installation, and it just doesn't do anything after I select Windows from the grub menu.  I do this by not defining a disk initially to the virtual machine being defined, then using VBoxManage internalcommands createrawvmdk with the options to get my 1st and 3rd partitions (Windows XP and the ext3 partition for Ubuntu respectively) and using the -register option.  I then go back into the new virtual machine, click on the hard disk and select the raw disk I just created.  This is all in the "help" when VirtualBox is running, however it is noted that it is experimental and for Linux hosts only.  If I drop my Ubuntu ext3 partition from the raw disk definition, grub gives me an error 17, which I'm sure means it is not able to find the menu.lst file because the ext3 partition containing it is no longer defined.   The "help" says you can define a mbr file by adding the -mbr filename option to the definition, but I have no idea how to create mbr file for it to use!

For the last reply (sorry, I forgot your id and I'm in the entry screen now), what I am trying to do is find a way to use virtual machine software in Linux, using my EXISTING Windows XP installation (i.e., I don't want to reload Windows to a large file [the virtual disk] inside of Linux).

So, to sum things up to this point:

- VirtualBox, VMWare player and VMWare server all have problems trying to run off an existing Windows XP installation (partition).  If someone wants to try these things out on their systems, let me know and I'll pass along what I know to try it.

- creating a new virtual disk within each and loading my Gateway restore CD to it causes Windows to blue screen almost immediately at boot.  Probably a problem with using a system restore CD since I don't have a XP CD.

Would I be breaking the law or messing up my friends Windows XP license if I used his full install CD but with my registration key from the bottom of my laptop?

I'm going to keep trying - I will either get this to work or just give up on the whole mess after I go completely nuts!!:D

---

### Post by gcos7 on 2007-06-21
Forgot to mention - I tried the dd command I had found earlier to create a mbr file, then pointed to it with -mbr in the VBoxManage command, but when I try to start the virtual machine grub comes up with error 17 again.  

Anyone know how to create a master boot record for Windows XP in the first partition and copy it to Linux??

Thanks again!!  keep the replies coming!!   We WILL get this to work!!;)

---

### Post by molly_001 on 2007-06-21
> **gcos7 said:**
> gcos7 wrote ...
 
 
Would I be breaking the law or messing up my friends Windows XP license if I used his full install CD but with my registration key from the bottom of my laptop?
 
 

 
 
I'm not qualified to answer on the VM issues -- it does look like you've researched through a lot, though.
 
Regarding the reinstallation of Windows on your laptop: I *highly* recommend that you acquire a Windows installation disk for either your specific laptop brand and model, or as a second choice, an installation disk for the OEM brand of the laptop.  (a Dell reinstallation disk, or a Toshiba desk, etc.)
 
Especially with laptops, there are all sorts of functionality for things like hotkeys, special Function +keyboardkey options, hardware buttons for sound (volume) and optical media (press Play button) etc.  These are functions you'll want to have most likely within Windows.
 
The other issue is Windows validation which is almost sure to be tied to a ROM chip on the mainboard in your laptop.  Without the correct disk, you run the very likely risk of being unable to use Windows after 30 days if you can't pass validation.  
 
What I do is to call the tech support for the OEM manufacturer (Dell, Lenovo, Toshiba, Acer, etc) and explain to them that all partitions on the hard drive have been wiped out -- including their Restore and Utility partitions.  So you have a machine without an OS.  (so they think)
 
I've been very lucky with this, and have always got them to send me the disks (Restore imaging, or, outright normal Windows install).  Just this week I got Dell to send to me the install CDs for an Inspiron 6000 that I do not own.  In fact, it has had two owners before arriving to me temporarily for a repair.  Yet they are sending the CDs to me at my address, for free.
 
Although it would delay you by a couple of days,

---

### Post by molly_001 on 2007-06-21
I've been meaning to ask you, to please investigate whether it is possible to change,
the Title of this thread you created.  It will be much more helpful to other future users when they search and for you right now, would draw attention from VM experts !!  Thanks!!

---

### Post by gcos7 on 2007-06-21
Thanks for the reply!:KS

If I understand you correctly, I believe I have the disks you are talking about.  My laptop came with the Gateway system restore CD and I followed their directions when I first powered it up and made the backup disks.  The system restore CD restores the harddrive back to factory settings (2 patitions, 1 recovery, 1 for Windows XP) and loads Windows and some other files Gateway decided to include.  The additional backup disks contain things like the drivers, the pre-installed software, etc..  Due to having so many problems trying to load this into a virtual disk and actually have it boot, I decided to go the route of pointing the VM's to my existing Windows partition.

Also, I'll try to change the name of this thread if I can figure it out (i'm not the sharpest knife in the box);).

Thanks again, and keep the replies coming!:D

---

### Post by kelvin spratt on 2007-06-21
i think you might be over your head here i don't know nothing about vm but i do know that a restore disc will try to restore the system it will not work for anything else to run windows in vm, you need to obtain a proper windows installation disc not a restore disc, i personal don't see the point of what you are trying to achieve you have plenty of disc space just do small partion for Linux resise your windows partition and convert to NTFS 
apart from the Linux partition enable Read-write in my opinion you will  encounter less problems trying to find drivers for windows and you can use both systems with ease, vm is ok for testing it is not an ideal alternative for a proper install. But if you carry on i wish you luck.

---

### Post by gcos7 on 2007-06-21
Obviously some people ARE missing the point - WHY should I RELOAD Windows in a virtual disk when I HAVE an existing installation of Windows, with the software and files that I need for my Family Tree Maker (to be specific - over 20000 people)  that is already running???????  It would just be a waste of disk space.  BELIEVE ME,  I AM NOT ALONE IN WANTING TO DO THIS - JUST CHECK THE NUMBER OF VIEWS OF MY POSTS ON THIS SUBJECT.  Just because you may not have done it, don't knock me for wanting to do so!!  It IS SUPPORTED in the virtual machine products I have mentioned!

Okay, now I'm off my bitching throne.  Here's an update:  I have Windows running off my existing partition in VMware player again.  In other words, I'm back to were I started, with the same problems for which nobody posted any ideas for fixing:

- my Synaptics touchpad/mouse doesn't work
- a usb mouse doesn't work, even with USB enabled in the vmx file
- I have no network connection, and can't seem to get it to work

SO, IF someone can help me get through these 3 problems, I will have succeeded at what I wanted to do: save disk space, save reinstalling Windows, save reinstalling the apps I need in Windows for which there is NO equivalent in Linux and save loading the data files to go with those apps.  Clear now why I wanted to do this??  (Sorry, I'm just a little ticked at people who reply the way they do when obviously they haven't dug as far as I have into trying to make a virtual machine product work the way I want).

For the rest of you, who have been SO HELPFUL, my deepest THANKS!!  Your type of input is what will make or break Linux as a viable desktop replacement for the masses.  

Since I have found no way to rename this thread, I'm going to start a new thread and see if anyone can respond to the 3 issues (nobody did last time, that's how I got this messy thread started, but I have learned a lot in the process!!):D

---

### Post by kelvin spratt on 2007-06-21
These 3 items you mention are not working in Windows or Linux or both? if in Windows you need to install drivers you do not explain yourself very well you need to calm down and clear your head. I know its frustrating
when things don't go right or the way you planned but i've read the replies and i find most of them ok.

---

### Post by gcos7 on 2007-06-21
Kelvin, please go back to the beginning of this thread and follow the links it mentions for my other posts that brought me to this large one.  Perhaps a little background will help you understand you are not dealing with a typical idiot here:  I have over 25 years experience as a systems programmer, systems administrator in large scale, mid-frame, mini and micro computers.  I come from the days when there was no such thing as a "PC" and even "DOS".  We built our own computers then in ways people now would not even begin to understand.  Operating system?? - even CP/M (for you youngsters out there, a precursor to DOS before there was a Microsoft) was a blessing.  I understand drivers - enough said.

Now, if you have read everything you understand that I am running an existing Windows XP installation in a virtual machine in Ubuntu 7.04 Linux - I can't state it any clearer than that.  Of course the mouse and network work fine in Linux.  The virtual machine window is another animal.  The cursor is available and works in the VMplayer, but when the virtual machine itself has focus the mouse pointer there does not respond (yes, I know to give the virtual machine "control" of the input devices from the VMplayer).  

Within this same virtual machine the network also doesn't work.

I've done a lot of digging on this whole process.

I eventually followed the below link to get my existing Windows installation working in a virtual machine in Linux:

[http://www.advicesource.org/ubuntu/Run_Existing_Windows_Instalation_On_Ubuntu_With_Vmware_player.html](http://www.advicesource.org/ubuntu/Run_Existing_Windows_Instalation_On_Ubuntu_With_Vmware_player.html)

I am sure there are entries in vmx file (they have 2 letters transposed in the web page) that either need to be changed, deleted or added, but I have no idea what.  I have searched through the available documentation I could find for VMplayer and haven't found anywhere where each of the entries possible in a vmx file and what they mean and do is explained.  That is why I am looking for help.

Some web pages have mentioned adding VMware Tools to the guest host, but I have not found a way to get VMware Tools without having to pay close to $200 for VMware workstation.

If it's as simple as "adding a driver to Windows" then SOMEONE *PLEASE* EXPLAIN IT TO ME. 

Meanwhile, please be sure you have read this entire thread, as well as the threads under my userid in this forum, before making some of the statements.

I have tried to be professional and open minded in my approach to this - after all, it's just a hobby for me.  Even though I may get upset I have tried in the past to keep that out of my posts, because there is no room for such things on any forum.  I am not a Linux basher.  I am not a Windows basher.  I am not a complete idiot.  I  AM new to Linux and therefore may ask some naive questions (please note no question is DUMB - it simply means the person doesn't know!).

So, I now will get away from being upset with some responders, and try to get back to being civil.  To those not to blame for my frustration, I apologize.  Please, all responders, try to be kind and civil in return!:D

---

### Post by RedRover1 on 2007-06-21
If you have VMWare Server running then adding VMWare tools will be in one of your menu options across the top.  I don't have access to my laptop right now to give you the sequence.  In Player 2.0 (believe the windows version) comes with ISO files that you mount to get you VMWare Tools.  Also as far as the network try setting it to NAT and see if that helps.

You may want to post your issue in the VMWare Forums also under Server or Player

[http://www.vmware.com/community/index.jspa](http://www.vmware.com/community/index.jspa)

---

### Post by gcos7 on 2007-06-21
:KSThanks, redrider.  You, Molly and Ghost Rider (?) [I don't have the message thread visible right now so I may be wrong on the names).  You 3 seem to understand what I am doing, and I will try going to the other forum.  

As far as the tools go, when I reinstalled VMware player in Ubuntu it seems to have screwed up the VMware server so it doesn't start now.

Thanks again!;)

---

### Post by RedRover1 on 2007-06-21
Yeah,  I'm pretty sure you can't have Server and Player loaded at the same time.  Workstation and Player can be but like you said workstation costs money.  I would stick with server until you get things worked out because it has more options even though Player 2.0 is optimized for faster display and can support USB 2 though you need to create the VM in Workstaion 6 for the new features to work with Player 2.

---

### Post by gcos7 on 2007-06-21
:DRedRover - again thanks for the replies.  I tried server but couldn't get it to work with the raw image of my existing Windows installation, so I eventually went back to "ground zero" with player running my existing Windows installation within Linux.  I would imagine VMware doesn't like the idea of giving out the commands for their VMX and VMDK files, as then people could just download player for free and do anything they wanted,  and probably not need to buy one of their products.

---

### Post by gcos7 on 2007-06-22
Everybody, thanks for your replies.  I realize not everyone would understand why I wanted all of this to work, but seriously if you look at the number of people that have viewed my other threads as well as this one, you will see that others are interested as well.

I have come to a difficult decision.  I will be going back to solely Windows.  Please, no Windows bashing, no Linux bashing, no personal bashing. 

I have a few of what I hope are constructive comments for the Linux community.  Please understand the intent of these, and understand how thankful I am to the people who have put so much effort in to  Linux and in particular Ubuntu.

As I mentioned elsewhere, Linux, for those who don't know, is sort of a "clone" of the Unix operating system.  Linux has been developed with the intent of it being an open source opened license operating system, basically meaning anyone can do what they want with it within a few restrictions.  This development has taken and still is taking a HUGE engineering effort to accomplish.  The people involved in its' development and support should be greatly thanked.

However (you knew there had to be a "but" coming, didn't you??);), the current P/R push I have seen touting Linux, and particular Ubuntu, as a viable desktop replacement is premature.  I have over 25 years of experience as a systems programmer and systems administrator on large scale, mid-frame, mini and micro computers, so I say this looking at it from both a developers' standpoint but also from an average "Joe-Blow" user.  I have seen many magazines, including PC World and Maximum PC, talking about Linux.  I'm sure many others have as well.  Unix/Linux has come a LONG way since my first cryptic experiences with it.  On one hand, it was developed by engineers for engineers, and Linux continues that tradition well.  The current push to make it a viable replacement for the average desktop user is just not realistic yet.  Great strides have been made - I can see that in the ease of installation and configuration to get a default installation going with X-Windows without all of the old hassles.  Some applications have been developed with the idea of providing the same functionality of programs the average user would be used to from Windows.  Some of these applications, however, still have an "engineering" feel to them.  I could name a few but the idea here isn't to bad mouth anything.  There is also a lack for some of us of the applications we truly need (in my case, Family Tree Maker - none of the Linux "equivalent" softwares I have seen even come close to it).  OpenOffice is a big step in the right direction, but is should be when its' base is from an ex-commercial piece of software.  What I am trying to say is that it is time to stop messing around purely for the sake of the operating system and start developing more products that would allow the software available to truly compete with the vast world of software available to Windows users.  I have read many, many statements about the availability of Linux software that serves the same function as Windows software packages, but everyone always gets defensive.  The Linux mentality has always been to dig on your own until you have exhausted every possible place you can look, tried everything you can possibly try, and THEN ask for help.  This mentality, which is an engineering way of thinking, must be changed on the portion of things that are being made to form a viable desktop replacement.  
     Can things be made to work - sure.  I got my wireless running after a lot of searching, installing ndiswrapper, finding the correct version of my WINDOWS driver, well, you know the story, most of you have been there in one way or another.  The same applied to my video - in my case a onboard IGP.  As hard as it may be for some of you to believe, the average user for which you are aiming when you say a viable desktop replacement would not go through what I did to get those things working.
     Can you blame manufacturers for not developing some of the drivers and software needed in Linux? Honestly, they need to see it move away from the server market and into the "main stream" user base successfully before they will ever do that.  Unlike the developers of Linux, those manufacturers are in business as a profit making organization - they exist to make money.  The Linux base doesn't offer the chance at that money yet.

     Everyone has made great strides with Linux, I am amazed.  Now we need regular developers to step up and build the application software to support it.  Keep the engineering in the background.  Look at the types of question being asked in the beginner forum, realize the vast majority of those people aren't engineers but still have a stronger than average computer background, and you'll see the changes that still need to be made.

    Please take all of these comments in the way they intended.  They are not personal barbs at people.  They are not meant to "tear-down" Linux.  They are an honest appraisal for how things look if you aren't strongly computer oriented.  I hope everyone keeps working on this - it is a VERY worthwhile thing, and great progress has been made.  Please also understand that for me personally, I love using Linux, but my application requirement says "Windows".  My programs in particular do not work in Wine.  I have gone through a lot to get a virtual machine working in Linux in which I would just run Windows, instead of needing to dual boot.  Someday I hope to be back. 

     For those of you new to the Linux world and looking, I say whole heartedly to try it - just don't get rid of your Windows installation and software base until you have it all up and working on Linux equivalents.

    To everyone who has tried so hard to help me, thank you!  The free support that is given willingly in this forum is a rare thing.  Thank you to all.

---

### Post by molly_001 on 2007-06-22
All your efforts made with your laptop were/are admirable efforts.   I agree with many if not most of your treatise, too.  Windows is a more productive, more user-friendly environment thanks to the support of the the software and thus computer hardware and engineering world.  Linux will remain more for the enthusiast community until it gains much more of the same support.  I do think Linux is fun and stimulating.  "Laptops are special" however and that is a fact often not readily apparent to the new user hoping to get Linux up and running on their laptop hardware.  I don't blame you for going back to MS Windows.  However, do check back with Ubuntu every 12 months and fire up the LiveCD on your hardware to see what native drivers they are now including.  I have been testing Gutsy Gibbon this week and I also watch the daily development threads and am amazed at how hard people are working to make it a substantial leap ahead of 7.04.  Good luck !!

---

### Post by kevpatts on 2007-06-22
Hey guys, I'm new to this tread but I've been tring to do EXACTLY the same thing for some time now and I can possibly point you in the right direction??? Saying that I haven't quite got it working yet myself, but my config is slightly more complicated, because my Win installation is on a RAID array!

I have to say I've only skimmed through cause I'm at work. Can I ask you a few questions first:
[LIST=1]
[*]Am I right in assuming that the primary, bootable drive (with GRUB installed in it's MBR), contains your Linux installation?
[*]Have you attempted to set up multiple hardware profiles in Windows?
[*]Do you know, for configuring VMware Server to use a physical drive, does it have to be mounted (or specifically not mounted)?
[*]Do you have a Windows disc with which you can boot to the Repair Console?
[*]Are you as frustrated as me at trying to get this working?
[/LIST]

Kevpatts

---

### Post by lazyart on 2007-06-22
Dare I suggest that you run Linux in a virtual machine inside Windows?

---

### Post by kevpatts on 2007-06-22
I believe we both have specific reasons for requiring to do it this way.

---

### Post by gcos7 on 2007-06-23
Okay, GOOD NEWS!!   I know have my existing Windows XP installation running as a guest in a virtual machine on my Ubuntu LInux host!!  I have full touchpad, sound and network support, including BOTH my hard-wire and wireless connections!!  This was accomplished with the Virtual Box software.

I had to reactivate Windows once I had the vm running, and then to my surprise I am able to boot Windows in at least 3 separate ways on my laptop now with no reactivate hassles, etc.:

- the just mentioned guest within the Linux host
- stand-alone from the dual-boot menu
- also as a guest in VMware player within the Linux host.  Note, however, I still have NO idea how to get the touchpad, sound and networking all working with VMware player.

Just quick observations, nothing scientific here:

- I only have 512mb memory on my laptop, which works okay when running Windows only or Linux only.  However, with the vm running, each operating system gets about half that, so obviously LInux is slower and there are times in the vm you wonder what the heck happened and how soon you'll actually see something happen.  Again, I believe this is mainly due to memory issues, with a LOT of swapping going on both in Windows and in Linux.  Top that off with having an integrated graphics processor that uses part of that memory as well.

- It may be because I don't have the touchpad, sound or networking working in VMware player, but it just seems (again, NOTHING scientific here!) that Vmware player is faster than Virtual Box when running this on my PC.  I suspect that as soon as I add the overhead of sound, networking and the touchpad (if I can EVER find out HOW!!) that it will slow down as well.

I could just say to do as I did - read the helps like crazy, read associated web pages like crazy.  However, I come from a different school of thought that says just because I had to dig to make something work doesn't mean you should have to (i know this is a little different than some of the Linux users).  Why should you have to reinvent the wheel?  So, let me know if you want to know what I did to get this working, and just how simple those instructions should be.

Also, for all you Gateway MX3215 laptop users out there (or for that matter, anybody with a really cheap laptop - Celeron processor, integrated graphics chip instead of a dedicated video card, etc.), if you would like a how-to on how I got my laptop (including wireless) running Ubuntu 7.04, with 1024x768 video resolution, etc., working, please let me know.  I could also add to that getting your existing Windows installation running within Linux as well.

Please be advised I am both up (from actually getting this working) and very tired (from doing so much on this) so any advice or how-to may take a while to get out.

In the mean time, I can keep Linux as my OS of choice, run my EXISTING Windows installation as a virtual machine within Linux - no dual booting needed.  I have already run my Family Tree Maker without rebooting into Windows.  

Some may think this venture silly - others will see the need.  Others with a deeper technical background will also understand that it's just dang hard to give up on something so you stick with it to make it work purely on principal.

To all who helped along the way - a GREAT thanks!!

NOW, anyone know how to get sound, touchpad and networking working in Vmware player?????

---

### Post by gcos7 on 2007-06-23
bump

---

### Post by molly_001 on 2007-06-23
gcos --

I know you've struggled with that for a few weeks.  Congratulations on your stubborn success!

When you get the time to finish your step-by-step tutorial, please edit the original post by you in this thread and in that other thread which is appropriately titled for VM Windows inside of Linux, to hyperlink or point to those steps. This will be helpful since most people don't read much beyond the first few posts in any given thread.

If you need any bandwidth for posting your tutorial, just let me know.  Thanks!

---

### Post by bodhi.zazen on 2007-06-23
I have not read each and every of these long posts, but I think what most people do is convert their windows install to a virtual machine. You can then run the virtual machine with VMWare or Vbox or continue the conversion to a vbox image.

You can then boot the VMWare with virtualbox (versoin 1.4.0 +) or convert to a virtualbox image.

If you boot (not convert) the VMWaer image with vbox, you will have limited options as Vbox is still in development. Vbox is converting to the same image format as VMWare so I expect increased compatibility in the future...

To convert : 

[http://doc.gwos.org/index.php/VirtualBox#Convert_.28Migrate.29_your_Windows_Insallation](http://doc.gwos.org/index.php/VirtualBox#Convert_.28Migrate.29_your_Windows_Insallation)

HTH

---

### Post by kevpatts on 2007-06-24
I've just tried the VirtualBox method and Windows gets stuck just before the splash screen shows up (i.e. there's a full grey progress bar on the screen when it hangs). Even in Safe Mode it gets stuck after "Mup.sys" in whatever hardware profile I try to load. Did you run into this problem?

---

### Post by bodhi.zazen on 2007-06-24
he he he ...

Well I have no windows install to convert :twisted:

See if this link helps (it is a link from my first link so perhaps you saw it already)

[http://www.virtualbox.org/wiki/Migrate_Windows](http://www.virtualbox.org/wiki/Migrate_Windows)

---

### Post by kevpatts on 2007-06-25
Thanks man, but that seemed to have no effect. Still freezes at after Mup.sys. Also, I don't have an AGP port. PCI-E all the way.

---

### Post by stianalm on 2007-06-25
gcos:

I am trying to do the same thing as you so I have to congratulate you on your success! Please do write a guide so others can see what you did to make it work.  I haven't seen any good straight-forward guide to make it work on VirtualBox so I'm sticking with VMWare. Any reason why you're not happy with VirtualBox?

---

### Post by kevpatts on 2007-06-25
yeah, this would be seriously appreciated!

---

### Post by gcos7 on 2007-06-25
;)bodhi.zazen, your input is greatly appreciated, but also please understand that some of use don't want to duplicate a disk within a virtual machine - we may be short on disk space, we may have enough things installed in our existing Windows installation that we don't want to reinstall them.  Perhaps some have lost their Windows CD.  Perhaps they have lost the installation disks for other programs.  Also, the migration of an existing Windows installation to a VM image has always involved an external device, a network storage, or some other medium to create the VM to first, then copy into the host.  Some of us do not have those things.

Some of use want to make the best use of our limited disk space and still be able to stand alone boot Windows if we so desire.;)

Then there is always for someone more technically oriented like myself - if it is supposed to work but doesn't, fix it.

So, as mentioned, your input is greatly appreciated, but please keep posts to the subject at hand:  running an existing Windows installation as a guest within a Linux host, not as a virtual disk image but using the existing image.

---

### Post by gcos7 on 2007-06-25
stianalm,  I hope to write something up soon.  For everyone interested, it will probably be at a very basic level, so for more advance users it may seem to light, but please read it.  It may be a little while before I get it posted, and it really doesn't need to be very long, so it won't be a lot of reading anyway.


kevpatts - I did private message you, but just in case:  I was having trouble also with having the white "progress" bar go across the screen and never getting the Windows splash screen.  I did a few things for this, but not really sure which was the problem (I was frustrated and looked at several things at once).  The first thing I would do is use VBoxManage and set ACPI to "on" and also set APIC to "on".  I think you already know, but VBoxManage is in a section all it's own in the help that's accessible from the VBox window.  I found I had to do them one at a time.  At the same time I changed access on a couple of files to be "world" accessable (via 777 and chmod) that were only read accessable to my userid.  I have been searching like the devil to find where I found that so I can post it for you (and include it in the how-to!!), but so far I haven't found the reference again.  I don't know about others, but I have a tendency not to keep the address of where I found something once I have something working (I think I "gotta change that";) ).  I'll repost if I find the reference again (it may have been inside a message on the VirtualBox message forum.  Also, I learned the hard way NOT to install the guest tools if you plan on booting your Windows stand-alone from the dual-boot menu.  I'm working that out right now.

For all others, I do plan on writing up to simple how-to's:

(1) Getting Ubuntu with wireless, sound, etc., running on a Gateway MX3215 laptop.  Please note that I haven't gone to the trouble yet to get movies, mp3's, etc., working as those are low priority items to me as I usually don't use them.

(2) Getting an existing Windows XP installation running as a guest vm on an Ubuntu host.

It will probably be a little while before I have those ready.  For those who are in a hurry, I apologize, but I'm a little tired from working on it, plus I honestly have to go back and find the references I used as I "did" but record the "how".  I hope they will be available within a week or so!  I'll repost here (and on a couple of other threads) after they are available.

---

### Post by kevpatts on 2007-06-25
In my case I use Ubuntu for 80% of daily use. I need Windows in a virtual machine for the other 20%, but I'd also like to be able to proper boot that windows only to play games.

---

### Post by bodhi.zazen on 2007-06-25
> **gcos7 said:**
> ;)bodhi.zazen, your input is greatly appreciated, but also please understand that some of use don't want to duplicate a disk within a virtual machine - we may be short on disk space, we may have enough things installed in our existing Windows installation that we don't want to reinstall them.  Perhaps some have lost their Windows CD.  Perhaps they have lost the installation disks for other programs.  Also, the migration of an existing Windows installation to a VM image has always involved an external device, a network storage, or some other medium to create the VM to first, then copy into the host.  Some of us do not have those things.

I understand most of these issues. However, the point of converting a windows partition, as I outlined, it is createes a virtual HD with windows as is on the hard drive, including programs ;)

> Some of use want to make the best use of our limited disk space and still be able to stand alone boot Windows if we so desire.;)

Then there is always for someone more technically oriented like myself - if it is supposed to work but doesn't, fix it.

So, as mentioned, your input is greatly appreciated, but please keep posts to the subject at hand:  running an existing Windows installation as a guest within a Linux host, not as a virtual disk image but using the existing image.

Well you should read these things then :

[http://www.virtualbox.org/download/UserManual.pdf](http://www.virtualbox.org/download/UserManual.pdf)

^^ See section "**9.8.2 Access to individual physical hard disk partitions**"

Then look here :

[http://oopsilon.com/Running-a-Windows-Partition-in-VMware](http://oopsilon.com/Running-a-Windows-Partition-in-VMware)

Should be similar in VirtualBox ^^

Then for a few final issues :

[http://www.virtualbox.org/wiki/Migrate_Windows](http://www.virtualbox.org/wiki/Migrate_Windows)

Here is a thread in Arch Linux : [http://bbs.archlinux.org/viewtopic.php?id=30768](http://bbs.archlinux.org/viewtopic.php?id=30768)

Now most of that is for vmware, but vmware is in the ubuntu repos , so do you care if you boot windows iwth Vbox or vmware ? ;)

---

### Post by gcos7 on 2007-06-25
bodhi.zazen,  I understand perfectly the idea of a virtual disk and everything else you have said.  Please understand the purpose of this thread:  getting an EXISTING Windows partition RU
NNING (not COPIED to a virtual disk) as the guest OS with Linux as the host.  For the purpose of this thread, please reduce comments to only that idea.  Running a virtual disk is completely understood, and I understand some people just don't understand why I am doing it this way.  Please restrict comments about virtual disks, etc., to some other message thread so as not to confuse those who are actually trying to do what I am doing:  running my EXISTING Windows partition in the VM in Linux - no virtual disk, no converting, etc..

---

### Post by gcos7 on 2007-06-25
;)bodhi.zazen,  I understand perfectly the idea of a virtual disk and everything else you have said.  Please understand the purpose of this thread:  getting an EXISTING Windows partition RU
NNING (not COPIED to a virtual disk) as the guest OS with Linux as the host.  For the purpose of this thread, please reduce comments to only that idea.  Running a virtual disk is completely understood, and I understand some people just don't understand why I am doing it this way.  Please restrict comments about virtual disks, etc., to some other message thread so as not to confuse those who are actually trying to do what I am doing:  running my EXISTING Windows partition in the VM in Linux - no virtual disk, no converting, etc..  As for the link you mentioned for VMware using an exisiing Windows partition, it seems to be a copy of the data contained on the page I have already provided a link for in this thread.  The problem with it is that the touchpad, a USB mouse, and apparently networking do not work for me using this method.  IF you can provide a way to have the touchpad/mouse and networking working using this method and VMware player,   then please be all means post that information here - THAT is the kind of information needed in this thread!

Again, thanks for responding!  Please continue to respond, but keep comments in this thread limited to just it's topic.  The other things are of interest to MANY people as well, but should probably be in a different thread.;)

---

### Post by kevpatts on 2007-06-25
Can I state another reason why I wish to do this? I build many PC's for many people and a lot of my freinds come to me looking for suggestions around specific problems or advice on PC related issues. In my endless quest to move people off windows onto Linux I often offer them to install Ubuntu as a dual boot alternative, for them to dabble with without risk of messing anything up.

When they're comfortable enough using Ubuntu they never move over fully because "there's still something I want to use in Windows". If I could load the windows partition as a virtual machine, they could use it from within Ubuntu without risk of losing it, even if they mess up they're Ubuntu partition while experimenting. They can always just wipe they're Linux partition and start again.

bodhi.zazen, the question isn't "Why are you doing it that way?", but instead it's "Can it be done this way too?"

kevpatts

---

### Post by bodhi.zazen on 2007-06-25
> **gcos7 said:**
> ;)bodhi.zazen,  I understand perfectly the idea of a virtual disk and everything else you have said.  Please understand the purpose of this thread:  getting an EXISTING Windows partition RU
NNING (not COPIED to a virtual disk) as the guest OS with Linux as the host.  For the purpose of this thread, please reduce comments to only that idea.  Running a virtual disk is completely understood, and I understand some people just don't understand why I am doing it this way.  Please restrict comments about virtual disks, etc., to some other message thread so as not to confuse those who are actually trying to do what I am doing:  running my EXISTING Windows partition in the VM in Linux - no virtual disk, no converting, etc..  As for the link you mentioned for VMware using an exisiing Windows partition, it seems to be a copy of the data contained on the page I have already provided a link for in this thread.  The problem with it is that the touchpad, a USB mouse, and apparently networking do not work for me using this method.  IF you can provide a way to have the touchpad/mouse and networking working using this method and VMware player,   then please be all means post that information here - THAT is the kind of information needed in this thread!

Again, thanks for responding!  Please continue to respond, but keep comments in this thread limited to just it's topic.  The other things are of interest to MANY people as well, but should probably be in a different thread.;)

I think you need to read my links as all them are regarding doing exactly as you ask. They are all about booting an existing windows (physical) partition and how it is done with VMWare. The virtualbox links describe how to do it with virtualbox. The Arch linux links discuss the VMWare configuration in some detail. I also do not think you understand what is it means to convert a physical windows installation to a virtual machine.

So ... you will need to read and adapt ...

I know virtualization is sometimes hard, but, like most, networking/mouse/keyboard/dual monitors are all working for me with both VirtualBox and VMWare. I am not sure if you have a hardware issue in that your mouse or network card are incompatible (booting your windows partition does NOT change the virtual hardware or compatibility/incompatibility ; keep in mind, even if you boot your windows partition you still have the SAME mouse/keyboard/network card in the virtual machine [this is how virtual machines work]) or if you need help with configuration.

Hate to burst your bubble ... but ...

I think your "problem" is that you do now understand how a virtual machine works. All the components (mouse/keyboard/monitor/network card/etc) are *emulated* with VirtualBox or VMware. For example, you can not currently run Beryl in a guest because the emulated hardware in vbox/vmware does not emulate a nvidia/ATI card. It does not matter if you boot a virtual HD or a physical HD, the guest still will not emulate a nvidia/ati card. Likewise the guest does not use your host mouse,keyboard,network card, etc. All those are emulated in the guest and interact with the host via Vbox/VMWare.

Now I also know at least video emulation is under development so the situation may improve in the near future, but, to the best of my knowledge, not much of what you are asking is currently possible.

You may have to resort to a more standard mouse ??? I don't know.

So, rather then ranting, I think you will have more success if you take the time to read and understand what you are trying to do (it is not so straight forward is it ?) and ask specific questions.

---

### Post by bodhi.zazen on 2007-06-25
> **kevpatts said:**
> Can I state another reason why I wish to do this? I build many PC's for many people and a lot of my freinds come to me looking for suggestions around specific problems or advice on PC related issues. In my endless quest to move people off windows onto Linux I often offer them to install Ubuntu as a dual boot alternative, for them to dabble with without risk of messing anything up.

When they're comfortable enough using Ubuntu they never move over fully because "there's still something I want to use in Windows". If I could load the windows partition as a virtual machine, they could use it from within Ubuntu without risk of losing it, even if they mess up they're Ubuntu partition while experimenting. They can always just wipe they're Linux partition and start again.

bodhi.zazen, the question isn't "Why are you doing it that way?", but instead it's "Can it be done this way too?"

kevpatts

LOL

I understand more then you presume ;) I teach a Linux course and offer vobx/vmware as an alternate to dual booting.

BUT you should know there are risks with what your are doing. If you boot your windows physical HD with VBox or VMWare you *are risking corruption of the partition*. What you say is true if you convert your windows partition to a virtual hard drive (this leaves the windows partition untouched).

That is why most people do it the way I have outlined (additional hard drive space and additional RAM are cheaper then a whole new box).

Now I do not mind you playing with your hardware, as you wish. BUT if you are advising others to boot their physical partitions please consider warning them of the possibility of data loss.

Also, as in my last post, the hardware emulation is currently limited (beryl/directX) so just because you can install/boot windows does not mean all applications, especially games , will work on the virtual machine. 

As both VMWare and Vbox are under fairly heavy development I expect the situation to improve.

---

### Post by gcos7 on 2007-06-25
> **bodhi.zazen said:**
> LOL

I understand more then you presume ;) I teach a Linux course and offer vobx/vmware as an alternate to dual booting.

BUT you should know there are risks with what your are doing. If you boot your windows physical HD with VBox or VMWare you *are risking corruption of the partition*. What you say is true if you convert your windows partition to a virtual hard drive (this leaves the windows partition untouched).

That is why most people do it the way I have outlined (additional hard drive space and additional RAM are cheaper then a whole new box).

Now I do not mind you playing with your hardware, as you wish. BUT if you are advising others to boot their physical partitions please consider warning them of the possibility of data loss.

Also, as in my last post, the hardware emulation is currently limited (beryl/directX) so just because you can install/boot windows does not mean all applications, especially games , will work on the virtual machine. 

As both VMWare and Vbox are under fairly heavy development I expect the situation to improve.

You, sir, FAR, FAR, FAR underestimate what somebody understands.  You think I would even be looking at this if I didn't know that dangers, and if I DIDN"T ALREADY KNOW what a damn virtual disk is???  Did you read this thread in it's entirety?  Did you notice it mentioned at the start that nobody had answered my other posts??  I don't play games on my computer, so don't insult me.  Don't insult me when you have no idea how high my education really has gone - you don't know me.  Don't think I read your links??  How in the hell could I have told you the one looks just like a copy of the one I have quoted elsewhere in this thread?????  I have NEVER ranted or raged in this thread until now.  Where the hell were you when my other posts where up?  Didn't bother to answer those, did you???  TEACHER - don't quote titles - I've taught a LOT of computer science classes, so it doesn't impress me.  A true teacher, away from the classroom in a BEGINNERS forum, would have said "here's what you need to do.  For reference on why these steps were taken, please see these websites".  You've got the same "RTFM" attitude that is the reason this OS will not be a true desktop replacement, not until that way of thinking changes.

You're so damn smart so here's deal for you:  take over the thread.  Answer the people who have said I want to this as well.  Write the how-to.  Why??  Because I'm sick of this whole attitude that permeates the Linux community.  Yes, the engineers and developers who have done so much to make this all happen are to be thanked a million times over.  Now, get past the mind set  and start looking at things for the "average" Windows user - if you don't you'll never make big inroads into the installed base.  A vendor offering Linux on some of their machines - what do you think people are going to do when they buy it and then find out they can't do anything without re-learning a lot of stuff, and with communicating with a bunch of asses??  They'll go back to Windows.  I'm not, but I'm done with this thread, done with this and any other forum.  I'm done with doing something and being insulted because I did.   I was going to offer  a step-by-step to get this working, THAT'S want "they" want.  Guess what - your turn.  I hope when you're all done with this thread and have told everyone everything they ever wanted to know about doing this, that some smart *** comes up at the end and tells you what an idiot you are - you deserve it.

You think I'm so stupid as to not know the risks - give me a break.  And even if you still want to believe that (you'd be SO wrong), what makes you think I didn't read the info at VMware about physical partition support being experimental?  Or that the instructions for doing it in VirtualBox are in the "advanced" section of the included help???

I'm SICK of people like you with the way you approach these things in this forum.  If all you want to do is tell somebody RTFM, then just say so.  If you know an answer, PROVIDE IT, not links to some other site.  People look to these forums for ANSWERS not to be bounced around to a bunch of other web sites.  As someone with my background, I understand you wanting to people to read and learn.  However, a lot of people looking at threads such as this one are not technically oriented.  They just want a simple "do this".

---

### Post by bodhi.zazen on 2007-06-26
Please read this article: [ Running VMWare on a Physical Partition 66](http://www.motin.eu/www/mirror/physvmware/)

> This article describes how to set up VMWare on a pre-existing Windows partition.

VMWare is an incredibly useful piece of software. Problem is, it feels like it's perched on the tip of an eggshell. Any change to its environment tends to cause it to fall over, isolating all your data in the VM until you can find the time to get it working again. It's not fun to trust important data to such a brittle environment.

**This article describes how to solve this by running VMWare on a physical disk partition**. That way, when VMWare dies, you just boot into your Windows partition and continue working as usual. The convenience of VMWare, the reliability of dual-boot, what's not to like?

Benefits:

    * Your data is still safe even if VMWare never works again.
    * You can use a pre-existing Windows partition under VMWare.

Drawbacks:

    * You can't suspend or snapshot the virtual machine.

Try it out. If you have a specific question or problem please post.

---

### Post by kevpatts on 2007-06-26
> **bodhi.zazen said:**
> Try it out. If you have a specific question or problem please post.

I tried this already and ran into a brick wall. See this post: [http://ubuntuforums.org/showthread.php?t=345835]("http://ubuntuforums.org/showthread.php?t=345835")

---

### Post by bodhi.zazen on 2007-06-26
Well, the how-to I linked to uses vmware server and the page you are referring to is vmware player.

so :

1. did you try it with vmwaer server ?

Other then that I would have to walk through what you did step by step ... 

You need to set up your windows install ...

Then you need to set up grub ...

Then you need to create a new machine (which I did not think you could do with player, thus you need vmware server).

---

### Post by kevpatts on 2007-06-26
> **bodhi.zazen said:**
> Well, the how-to I linked to uses vmware server and the page you are referring to is vmware player.

so :

1. did you try it with vmwaer server ?

Other then that I would have to walk through what you did step by step ... 

You need to set up your windows install ...

Then you need to set up grub ...

Then you need to create a new machine (which I did not think you could do with player, thus you need vmware server).

I have tried it with VMWare Server and get the same result. I already have configured my windows machine and I don't need to set up GRUB as there is no boot loader installed on the drive containing my windows installation (I swap between drives in the BIOS, this is because windows is installed on a RAID array and I couldn't get Ubuntu to recognise it during installation).

---

### Post by stianalm on 2007-06-26
> **bodhi.zazen said:**
> 

I think your "problem" is that you do now understand how a virtual machine works. All the components (mouse/keyboard/monitor/network card/etc) are *emulated* with VirtualBox or VMware. For example, you can not currently run Beryl in a guest because the emulated hardware in vbox/vmware does not emulate a nvidia/ATI card. It does not matter if you boot a virtual HD or a physical HD, the guest still will not emulate a nvidia/ati card. Likewise the guest does not use your host mouse,keyboard,network card, etc. All those are emulated in the guest and interact with the host via Vbox/VMWare.


If I understood him correctly, gcos said that network and mouse worked fine in VirtualBox, but not in VMWare. So the problem is not that the mouse is emulated. The problem is getting it to work in VMWare. One can always ask why he doesn't settle for VirtualBox but he obviously has his reasons. The why is not important, the how is. I have to admit I haven't had time to look at all your links but I will. Thanks.

I hope you do find time to write how you made it work, gcos. We all have different systems and we have to do small modifications to the routine to make it work. Seeing several recipes for the same thing makes it easier to find the right steps to make my system work.

---

### Post by gcos7 on 2007-06-27
Anybody ready for a REAL answer now??

The answer that SHOULD have been provided for the blue screen problem at Windows boot in VMware is that you have to (at least temporarily) disable scsi in the .vmx file, in my case in meant changing scsi0.present ="TRUE" to scsi0.present = "FALSE".

The answer that SHOULD have been provided for the touchpad/mouse problem in Windows in VMware is that it is a PS2 device, specifically mouse.hostType="DISABLED" must be changed to mouse.hostType = "ps2"  and mouse.filename = "auto.detect" must be changed to "/dev/psaux" in the .vmx file in my case.

The answer that SHOULD have been provided for the network problem in Windows in VMware is that the network is by default set to bridged, and only the wired connection was set up by vmware-config.  In my case, I for now just wanted the wired connection working, as once it was working it is a snap to add the wireless.  This meant changing the ethernet0.connectionType = "bridged"  to ehternet0.connectionType = "nat" in my case.

I don't know if these answers will help others or not, but it's all I NEEDED TO KNOW.  Not that difficult to just SAY IT HERE instead of questioning people's understanding of virtualizing now is it??

You still need to write the easy to follow step by step for the people who keep posting here.  You still need to write the easy to follow step by step for the Gateway MX3215.

Good luck.

For everyone else looking at this reply, I had intended not to reply here no matter what, but it has become obvious that some people do not know how to specifically state what to do and instead want to question your knowledge and anything you have done to date.  This reply is not intended as an easy how-to, but rather just simply states the facts.  If it helps anyone, good.  If not, that's okay to.;)

---

### Post by gcos7 on 2007-06-27
bump

---

### Post by kevpatts on 2007-06-27
gcos,

Did you encounter the "Inappropriate ioctl for device" problem? when trying to start the Virtual Machine in VMWare?

Kevpatts

---

### Post by gcos7 on 2007-06-27
kevpatts:

Sorry, but I haven't encountered that problem.  If I remember correctly you run a raid array for Windows?  Is this on sata devices?  (sorry I don't remember;)).  I run a very simple configuration, about as simple as it can get.  If you'd like, I can see if I can find anything on your problem, but it might take me a while, unless of course bodhi.zazen has an answer he can provide to you without bouncing you all over the place.:)

I knew from the beginning the "solutions" for my problems would be fairly specific to my configuration, but I thought if it could give anyone else ideas it was worth all the posts.;)

---

### Post by kevpatts on 2007-06-27
Thanks gcos.

Yeah, I run RAID on 2 SATA2 drives but I don't think that's the issue (hopefully not). Using dmraid this shows up as a single device (/dev/mapper/nvidia_egvfegahsen) and VirtualBox seems to be able to use it fine. It's just VMWare is having the problem.

Anyway, don't worry, you've done enough here.

Thanks,
kevpatts

---

### Post by gcos7 on 2007-06-27
I truely wish I could help you out.  I have seen some mention of sata devices being treated simliar to scsi devices in VMware.  I seem to remember some mention of special drivers or something.  One even mentioned something about pressing F6 or some such thing during Windows boot, installing some sata drivers, and then continuing with the boot.  I have worked with scsi and all sorts of raid arrays at work, but I haven't ever worked with a sata drive yet - just haven't run into it here at home or at friends.  I have looked on the web for your error message, and while it appears in quite a few places, I don't know if any of them would be of use to you or not.  Not to mention I'm sure you've already looked anyway!;)  I would prefer not to bounce you all over the place anyway.  A REALLY dumb question, I know, but have you posted this on the vmware server or player forums?  Forgive me for pointing out the obvious I'm sure you've already fought through as well!!;)

I'm going to keep searching for things with that error message that deal with vmware with Windows as the guest (I do remember seeing something on this but it dealt with Windows 2000 - maybe it would be the same for XP?).

I'm really sorry I can't help you yet.  I hope I can in the near future.  Meanwhile, if anyone else has encountered this please post back here so we can follow up!!

:D

---

### Post by gcos7 on 2007-06-27
;)As an additional follow up on things contained in this message thread, if you chose the virtual disk method, it is possible to install from the Gateway restore CD.  I don't know why I didn't think of it before, but you just have to edit the .vxm file and set scsi0.present to false.  While you're in there, add the things I mentioned in the a couple of posts back regarding the mouse.

For both cases, since I forgot to mention it and in case somebody doesn't know, you must add the sound device (if you are using VMware server you can do it in the console) and for my laptop (perhaps others as well?) set the device from auto detect to dev/dsp.

---

### Post by anewguy on 2007-07-11
kevpatts:

I have been watching this thread so I could set up my own VM.  In the course of searching things tonight, I found this in the VMware Converter documentation ([http://www.vmware.com/support/converter/doc/releasenotes_conv301.html](http://www.vmware.com/support/converter/doc/releasenotes_conv301.html))

that I thought might be of help to you of give you ideas.  I am just a beginner so I am just passing along something I found.:)

"Source with mixed IDE and SCSI disks might not produce a bootable virtual machine
A source machine with both SCSI and IDE disks has the IDE disks attached to the end of the disk list. If the source machine boots from an IDE disk, the target virtual machine created by Converter boots from the wrong disk because a VMware virtual machine looks for the first disk in the disk list. Workaround:

   1. Boot the imported virtual machine and press F2 to enter the BIOS
   2. Go to the Boot menu
   3. Highlight the Hard Drive row and press Enter
   4. Change the boot order of the disks so that the system disk is first
   5. Continue"

---

### Post by kevpatts on 2007-07-11
Thanks a million, but I don't believe that's the problem. The boot does select the correct drive and boots from it. I believe the problem lies in the Windows drivers not wanting to recognise that the hardware has changed.

---

### Post by anewguy on 2007-07-23
Hey, I'm just a novice here, but I did write a very simple (let me know how it can improved) how-to for the Gateway MX3215.  I included the 3 things noted by GCOS7 here that he did to get his vm working in VMWare.  It's nothing fancy, and absolutely nothing in there is original - it's a collection of what I needed to do to my laptop set up.:)

---

