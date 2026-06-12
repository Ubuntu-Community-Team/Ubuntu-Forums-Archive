---
title: "Problem installing on powerbook g3 wallstreet"
date: 2005-05-16
forum: Apple PPC Users
---

### Post by bronchandes on 2005-05-16
hey everyone,

i tried to install the new ubuntu 5.04 on my powerbook g3 wallstreet (300mhz, 192mb ram) but i couldnt boot from cdrom (burned the iso with nero on a pc). the book will boot from the original system cdrom by pressing "c" but wont boot from the ubuntu cd. and i also couldnt launch a setup under os 9.2.

please help....  :-? 



bronchandes

---

### Post by Bug on 2005-05-16
You've got to use Bootx, it's a control panel (and extension) that will reboot your machine into Linux. So when you install Linux, you will need to have an OS 8/9 partition to boot to that will load bootx sortof restart and then finish booting up in linux. Your OS 8/9 partition needs to be just big enough to hold a copy of os 8/9, so a couple hundred mb's should be enough. I think mine's 400MB, but I'm using Maconlinux too so theres some software I needed on there. So, remeber to save a couple hundred megs when you partition your drive. Do a search for Wallstreet in these forums, you should get some good tips.

Adam

---

### Post by bronchandes on 2005-05-16
thx bug for your reply!

now i found some useful information at the ubuntu wiki page:
[http://www.ubuntulinux.org/wiki/InstallOnOldWorldMacs](http://www.ubuntulinux.org/wiki/InstallOnOldWorldMacs) 

also managed to boot with bootx, thankx. went through the setup until the end... but now i have problems again. couldnt copy the kernel and the initrd file to the os9 partition. the howto on the ubuntu page recommends a "pivot_root" trick.

here is what i tried:
- setup is quite finish and says: no boodloader found. need to start with the kernel /boot/vmlinux with the parameter root=dev/hda10 
- then i entered the command line mode:

mkdir /target/mnt/foo
pivot_root /target /target/mnt/foo    .... making a new root?
mkdir /mnt/foo2
mount -t hfs /dev/hda9 /mnt/foo2
cp /boot/vmlinux-2.6.8.1-1-powerpc /mnt/foo2/Linux\ Kernels/    ... whats happening here? "/Linux\ Kernels/"

and here is the point where my problems start. system wont let me copy the file. ](*,)  says: cp: cannot create regular file "/mnt/foo2/vmlinux-2.6.10-5-powerpc" : Read-only file system. i was able to mount the hfs partition, no problem. asaik hda9 is my os9 partition. i must admit, i am a complete newbie to linux.

too many questions... :smile:  sorry. but as i already said: im a complete newbie. pls help


greetz bronchandes

---

### Post by karl_kashofer on 2005-05-17
Hi !

>You've got to use Bootx, it's a control panel (and extension) that will reboot your >machine into Linux. 

This is only true if you want a dual-boot machine.
I have installed Ubuntu on a Lombard and on a Pismo without any problems, just booting from the CD and wiping the HD in the installer.

If you are unsure about the switch (or have lots of software on your mac drive) just get a second hard drive, and replace the original one, so you can always go back. I tried to mirror the Apple drive with qparted or Norton Ghost, but they would not let me read the HFS partition.

You can boot the Powerbook from the CD. 
Sometimes it has problems reading the CD, try to burn your iso in Nero with slow speed (1x or 2x). I could not boot from the DVD drive in one of the Powerbooks, just swapping it for a CD-ROM worked.

Let me repeat: In my experience you do not have to go the BootX route if you do not want to dual-boot. Yaboot (the default boot loader in Hoary and on the Live CD) works fine.

BTW: Ubuntu works fine on a Pismo 400 mhz with 256 RAM, and also on a 333mhz Lombard with 196.

Hope this helps,
Cheers,
Karl

---

### Post by pitachu on 2005-05-17
The problem is that (from what I understand) the Wallstreet powerbook is oldworld where as the Lombard and Pismo powerbooks are new world (by the version number of the Open Firmware) so for a wallstreet BootX (or similar) must be used to install.

I too have been trying to install ubuntu on my wallstreet powerbook (G3 300 w/ 256 mb ram) and have encountered the same problems when reaching the final stages. The CD I have did not boot on the powerbook but boots fine on my partners flat panel iMac (G4 666 w256 mb ram) so I am happy that it is not burnt incorrectly.

I know this isn't much help but it slears up the Lombard/Pismo confusion of the last post.

P

---

### Post by bronchandes on 2005-05-17
thanks for the replies!

i have now managed to install ubuntu!  =)  finally!
but there are some problems left. first thing, which confuses me most, is a problem with the mesh driver. very often when i try to boot to ubuntu i get a kernel error because of double definition of mesh...?

the second thing is the display. from the first time i startet into the setup with bootx, my display was divided in 4 parts. where the top left quater was pretty much a full screen and the other 3 quaters are copies of the first quater but only half a screen or less. this kernel argument solved the problem: video=atyfb:vmode:14,cmode:32,mckl:89.

but ubuntu doesnt recognize my display. puts the desktop to 640x480 and 30hz and i cant change these values! tried to fix it in the device manager but couldnt find an entry for monitor...? in the device manager i also found dozens of urecognized hardware. 

people with wallstreet experience, please help... once again


bronchandes

---

### Post by Bug on 2005-05-18
Hi,

Yeah, bootx is the only way to go with the oldworld machines. For the video, I had to edit one of the files to add it the modes I wanted, and at 16 bit no less to try to speed things up, but I'm not on the powerbook right now so I don't know which one to tell you to edit. Maybe a google search for 'wallstreet ubuntu video' would help, and I'll check it out on my powerbook later today. I think I bookmarked everything, but I can't promise...

Adam

---

### Post by Bug on 2005-05-18
it's the xorg.conf file, when I get onto the powerbook I'll post the section from mine,

Adam

---

### Post by jaytbird on 2005-06-16
Hi everyone, new to the forum, new to linux, been using macs since the IIc days.
I have an old Wallstreet G3 that is sitting gathering dust. I had hotrodded it with a Powerlogix G3 466 CPU, and was running OS X 10.2.8 up until about a year ago, when it started getting real flaky, so I copied everything and then bought a TiBook. I was thinking of setting the Wallstreet up in the kitchen as an internet terminal / picture(slide show) display for my wife. What I want to do is this:
1. Wipe the HD clean and reinstall OS 9.1 on the first partition ~1GB
2. Install Ubuntu on the second partition...if memory serves I had a 20 GB HD in there, so the second partition would be ~ 18 GB
3. I understand I'll have to get BootX..is this corrrect?
4. It seems from this thread that there appears to be some problems with the video...has that been resolved and/or what needs to be done?
5. Anthing else I've missed and/or need to do? 
Thanks in advance.
JW

---

### Post by tango on 2005-06-29
Hi everybody

I received the Ubuntu original CDs and have tried unsuccessfully to install it in my Powerbook Wallstreet 233. 

I already installed BootX, but the rest of instructions in InstallOnOldWorldMacs is Chinese for me. It says something about preparing the boot.conf file. How do I open it? Or the tarball file, I unstuffed it, but where do I place the files? And it also says that I have to write several parameters in BootX. Where in BootX? there is only a line about kernel arguments, and nothing else. 

Finally, I tried to boot in Ubuntu Linux from BootX running in OS 9.2 (both the installer and the livecd), but it only reaches to arch:exit and then the screen goes white, or half-black half-white, and halts. I have to unplug the Mac to restart it. 

Sorry if I sound desperate, but I'm already several hours trying to install it, and can't do it.

---

### Post by tango on 2005-06-30
Ok, that's it. I give up. Nothing worked. I tried bootx. I tried, and tried, and tried. I'm gonna put all those linux CDs in the microwave oven, and burn them. They're totally useless.

I'll keep OS 9. At least, that's crap that is easy to install.

---

### Post by antwerx on 2005-07-01
Hello - I hope you really dont give up. Ubuntu is a very nice complete system.  

I had some trouble booting the Ubuntu 5.04 PPC install but then figured it out.

If this has been suggested, I am sorry. I am at work and didn't have time to go over all the posts.

This is what worked for me, and after I realized this method I just laughed.

Go to the Apple menu - Prefrences - Start Up Disk - (select) CDRom.

Reboot and bingo, boots from CD. I figured this out after trying all the methods of keyboard key combinations etc.

I installed on a first gen. clamshell iBook and am very impressed with the speed of the system.

---

### Post by Tommy on 2005-07-01
[QUOTE=antwerx]
Go to the Apple menu - Prefrences - Start Up Disk - (select) CDRom.

Reboot and bingo, boots from CD. [...]

I installed on a first gen. clamshell iBook and am very impressed with the speed of the system.[/QUOTE]

Yes, it's very nice when you have a newer Mac (Made after about 1998 ) . If the Mac is beige or black, it's most likely an Old World, and may require a more complicated procedure, sometimes using special tricks particular to that model! (There are a few exceptions, but it's a good general rule.)

As has been said earlier, the easiest way on an "old world" Mac is to create a smallish Mac OS 9 partition, and install BootX in it. (There is another bootloader called Quik but I haven't read of anyone getting it to work reliably on an oldworld Mac.)

The next step after installing BootX is to copy a kernel and an installation initrd from the installation CD to the Mac partition, and use BootX to start the installer. From there you partition the rest of the drive. The trick is getting the new running kernel (and initrd if needed) from the linux partition to the Mac partition because the installer doesn't know how to write to HFS or HFS+ (Mac file system) and the Mac OS doesn't know how to read linux.

Once you're up and running you have more options for getting data back and forth. It IS possible -- I have installed Debian on several oldworld Macs -- but there's a reason it's not "officially" supported in Ubuntu. It's quite tricky!

---

### Post by Tommy on 2005-07-09
[QUOTE=Bug]it's the xorg.conf file, when I get onto the powerbook I'll post the section from mine,

Adam[/QUOTE]

We're discussing installation issues in another thread. Did I miss your version of the xorg.conf file? 

My system works using the default version created when xorg upgraded the defaults from xfree86, but it's not ideal. I ran dpkg-reconfigure xserver-xorg but I think the resulting file was even worse, so I think I will try to tune it. (It would be cool if there was a graphical tool that would help... ?)

---

### Post by jaqkar on 2005-08-11
Hi Guys

I have a prob with the Ubuntu install on a Wallstreet Powermac an someone please help me, I created a thread here: [http://ubuntuforums.org/showthread.php?t=55826](http://ubuntuforums.org/showthread.php?t=55826)

---

### Post by Tommy on 2005-08-11
[QUOTE=jaqkar]I have a prob with the Ubuntu install on a Wallstreet Powermac [http://ubuntuforums.org/showthread.php?t=55826](http://ubuntuforums.org/showthread.php?t=55826)[/QUOTE]

For anyone following the thread from this side the problem is you can't install Hoary on a Wallstreet -- the installer fails with a red screen and I don't know how to get around it.

It works fine to do a Warty install and upgrade to Hoary. You can download the warty iso at this link [http://us.releases.ubuntu.com/releases/4.10/warty-release-install-powerpc.iso](http://us.releases.ubuntu.com/releases/4.10/warty-release-install-powerpc.iso)

(substitute the link to your closest mirror)

---

### Post by jaqkar on 2005-08-12
Hi guys

I got warty now and I am trying to install but once again I am running into some problems. If anyone can help out and maybe do some handholding I will really appreciate it. I have opened channel #ubuntuppc on irc.freenode.org for anyone that wants to help.

BTW. Can anyone please try and explain this part on the wiki ([https://wiki.ubuntu.com/Installation/OldWorldMacs](https://wiki.ubuntu.com/Installation/OldWorldMacs)) to me:

"(Note: With the tarball of kernels and initrds from above, which has the install kernel and the 'normal' kernel, put them *both* in place when you are getting ready to install. Then you'll just quit the installer when it prompts you to reboot. Reconfigure BootX/miboot to boot with the 'normal' kernel and initrd to finish the second stage install.)"

---

### Post by luzhin on 2006-04-22
Hey y'all. Powerbook G3 (Old World) Ubuntu Install: [http://www.flexion.org/site/index.php?gadget=StaticPage&action=Page&id=60](http://www.flexion.org/site/index.php?gadget=StaticPage&action=Page&id=60)

---

