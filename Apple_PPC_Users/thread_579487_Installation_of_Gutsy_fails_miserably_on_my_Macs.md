---
title: "Installation of Gutsy fails miserably on my Macs"
date: 2007-10-18
forum: Apple PPC Users
---

### Post by slartibertfast on 2007-10-18
Hello,

I've tried to install Gutsy on my Mac mini G4 as well as on my Powerbook G4. On both Macs the installation stops shortly after the boot promt. The screen gets dark (monitor goes into sleep mode) and thats it.
The command "live video=ofonly" obviously does nothing useful.

This has also been the case with all pre-released versions I've tested.

I'm currently installing Opensuse 10.3 PPC which seems to work without a hitch. But I want Gutsy !! ;-)

Anybody some suggestions ??

Thanks.

---

### Post by grazie on 2007-10-18
Sounds like there's a problem with the video driver if you're using the Desktop (Live CD) image. Have you tried booting into recovery mode? At the boot prompt I suggest you enter the following
```
live-nosplash single
```
If this gets you into recovery, you've narrowed down the problem, but it means installing from the Desktop image will be difficult. I'll take a closer look when I try Gutsy myself. There was a very similar problem on Feisty for some Radeon 9xxx cards. You could try installing from the Alternate image (if you are currently using the Desktop), but the servers are going to be very busy for the next few days. I'd suggest you use a torrent download if decide to try this way.

---

### Post by slartibertfast on 2007-10-18
Thanks, I'll try the alternate cd.

---

### Post by grazie on 2007-10-18
Just in case I didn't make myself clear, if there is a graphics driver problem for your card wth Gutsy, using the Alternate will propably not fix the problem. What it will do is allow you to boot and install Gutsy. Hopefully, if there is a driver problem, it'll soon be fixed or a workaround found.

---

### Post by lunalot on 2007-10-18
same problem with 7.10 desktop cd on a 12" ibook g4 (radeon 9200).  downloading (via bt) alternate cd now... but grazie, are you saying that i won't be able to install a graphical desktop even with the alternate cd?  i know ppc isn't officially supported, but why even bother providing the iso's when such a fatal bug exists?

---

### Post by touann on 2007-10-18
I have the same problem with my PB 12" Nvidia...

---

### Post by BladeMelbourne on 2007-10-18
I upgraded from Feisty to Gutsy on my Mac Mini a month ago. I did this by updating my apt-sources to point to Gutsy repos.

There are problems with the "xserver-xorg-video-ati" package combined with my Radeon 9200. I got the black sleeping screen and non-responsive keyboard. Even the latest debs from here didn't help: [http://http.us.debian.org/debian/pool/main/x/xserver-xorg-video-ati/](http://http.us.debian.org/debian/pool/main/x/xserver-xorg-video-ati/)

My solution was to install (dpkg -i packageName.deb) the working "xserver-xorg-video-ati" package from Feisty. I'm at work now, so I can't provide an exact package version number or a direct download link.

I don't have compiz/beryl running, but at least xwindows starts at full resolution.

---

### Post by AlphaMack on 2007-10-19
15" Al PowerBook G4

Just downloaded and burned the PPC ISO.  Same exact issue as the OP.  My fiancee has an iBook G4 as well (Radeon 9200) and I'm pretty sure that her machine will have the same result.

Oh well, it has been a good run for 4 versions.  Off to openSUSE.

---

### Post by stmiller on 2007-10-19
This is another heads up:
Gutsy has a show stopper bug where it fails to boot on some PowerPC machines. Despite bug reports made a fix was not made in time for the disc isos. :(

Here is the bug report:

[https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.22/+bug/126337](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.22/+bug/126337)

And a related thread:

[http://ubuntuforums.org/showthread.php?t=559099](http://ubuntuforums.org/showthread.php?t=559099)

Related: (?)
[https://bugs.launchpad.net/ubuntu/+bug/126146](https://bugs.launchpad.net/ubuntu/+bug/126146)

---

### Post by BladeMelbourne on 2007-10-19
I'm running Gutsy with this package (to avoid the black screen):

[http://ftp.egr.msu.edu/debian/pool/main/x/xserver-xorg-video-ati/xserver-xorg-video-ati_6.6.3-2_powerpc.deb](http://ftp.egr.msu.edu/debian/pool/main/x/xserver-xorg-video-ati/xserver-xorg-video-ati_6.6.3-2_powerpc.deb)

---

### Post by deanna2007 on 2007-10-19
Thanks BladeMelbourne,
That worked perfectly for me getting my g4 mac mini up and running.

---

### Post by grazie on 2007-10-19
> **lunalot said:**
> ... but grazie, are you saying that i won't be able to install a graphical desktop even with the alternate cd?  i know ppc isn't officially supported, but why even bother providing the iso's when such a fatal bug exists?
I don't know the answer to that, but I'd imagine it would be something like this. As PPC is now community supported, Canonical will not stop a release if there are problems on that platform.

The impact is that PPC releases may or may not contain fairly serious bugs on release. There's lot of work involved in releasing software and I'd imagine Canonical automate the process as much as possible. If THEY didn't do it, who else would? They're certainly not going to release PPC builds on their own. If you launch criticisms about Gutsy and other builds you may be upsetting others in the community that work hard to ensure that PPC builds get released at all. Also as there are likely to be workarounds to this problem, it's not fatal.

To get back to the original problem, I've downloaded both the Desktop and Alternate images. I get the same result using the Desktop image. My main machine is a G4 PowerMac with a Radeon 9000 graphics card, so I'll raise a bug report if required. I've installed Gutsy from the Alternate CD and got the black screen as expected on reboot. Downgrading the ATI video driver as described by BladeMelbourne solves the problem.

Incidentally, I've also got an old B&W G3 with a Rage 128 graphics card and the Desktop image boots OK on that machine, but there are other problems...Also I don't get the IDE problem stmiller mentions with either machine.

---

### Post by lunalot on 2007-10-19
> **grazie said:**
> I don't know the answer to that, but I'd imagine it would be something like this. As PPC is now community supported, Canonical will not stop a release if there are problems on that platform.

The impact is that PPC releases may or may not contain fairly serious bugs on release. There's lot of work involved in releasing software and I'd imagine Canonical automate the process as much as possible. If THEY didn't do it, who else would? They're certainly not going to release PPC builds on their own. If you launch criticisms about Gutsy and other builds you may be upsetting others in the community that work hard to ensure that PPC builds get released at all. Also as there are likely to be workarounds to this problem, it's not fatal.

Ah I see.  I didn't intend to criticize.  I'm a software developer and have been using FOSS since 2001.  I was genuinely curious as to why the release engineering process the PPC developers chose permits broken builds to be released.  But maybe I should have worded my curiosity more tactfully.

> To get back to the original problem, I've downloaded both the Desktop and Alternate images. I get the same result using the Desktop image. My main machine is a G4 PowerMac with a Radeon 9000 graphics card, so I'll raise a bug report if required. I've installed Gutsy from the Alternate CD and got the black screen as expected on reboot. Downgrading the ATI video driver as described by BladeMelbourne solves the problem.

Incidentally, I've also got an old B&W G3 with a Rage 128 graphics card and the Desktop image boots OK on that machine, but there are other problems...Also I don't get the IDE problem stmiller mentions with either machine.

Thanks for the report.  I'm about to try the same.

---

### Post by lunalot on 2007-10-19
Ok loading with break=top and doing modprobe ide_core seems to be working for me.  Thanks for the tips.

---

### Post by SycloneMedia on 2007-10-19
> **BladeMelbourne said:**
> I'm running Gutsy with this package (to avoid the black screen):

[http://ftp.egr.msu.edu/debian/pool/main/x/xserver-xorg-video-ati/xserver-xorg-video-ati_6.6.3-2_powerpc.deb](http://ftp.egr.msu.edu/debian/pool/main/x/xserver-xorg-video-ati/xserver-xorg-video-ati_6.6.3-2_powerpc.deb)

Help me for a sec please, ok, so if I'm having the same problem, how do I 'run Gutsy with that package' ?

I'm on OSX right now... when i boot up in Kubuntu am I supposed to first get into the system by typing 'linux break=top' at yaboot? ..and then am I supposed to do something else to first get to login and THEN download that package?

Thanks. 

:confused:

---

### Post by BladeMelbourne on 2007-10-19
> **SycloneMedia said:**
> Help me for a sec please, ok, so if I'm having the same problem, how do I 'run Gutsy with that package' ?

I'm on OSX right now... when i boot up in Kubuntu am I supposed to first get into the system by typing 'linux break=top' at yaboot? ..and then am I supposed to do something else to first get to login and THEN download that package?


It's a three step process.
1) Boot Linux into a text mode (so it doesn't start xwindows automatically)
2) Download the .deb package, or mount a USB key with the .deb package already on it.
3) Run sudo dpkg -i xserver-xorg-video-ati_6.6.3-2_powerpc.deb from the directory in which the deb file is.

I would recommend copying this DEB package into your home directory.
Basically whenever you check for updates, you need to avoid getting the newer version of this package. If you forget, you will need to run the same process again.

Does the above make sense?

---

### Post by SycloneMedia on 2007-10-19
> **BladeMelbourne said:**
> It's a three step process.
1) Boot Linux into a text mode (so it doesn't start xwindows automatically)
2) Download the .deb package, or mount a USB key with the .deb package already on it.
3) Run sudo dpkg -i xserver-xorg-video-ati_6.6.3-2_powerpc.deb from the directory in which the deb file is.

I would recommend copying this DEB package into your home directory.
Basically whenever you check for updates, you need to avoid getting the newer version of this package. If you forget, you will need to run the same process again.

Does the above make sense?

I understand your instructions in theory, but my mistake, I didn't fully convey my situation properly...

I already had Feisty dual-booting happily alongside Panther on my 1.25 AlBook. I wanted to do a clean upgrade to Gutsy so I backed up my stuff and downloaded the PPC iso, burned it, all ok so far.

When trying to install, after booting from the CD, it would go to a chromatic screen (leaving default option 'live') and just stay there. Then I tried 'live video=ofonly', same thing. Then I tried 'live-nosplash-powerpc video=ofonly' and it worked! It loaded up the live system. I installed from there like usual.

At first system launch, yaboot comes up like normal, but when it starts to load Kubuntu ('loading...') it just goes to a black screen and the fans come on like crazy and that's all... hangs.

So... from that point, how could I implement your package fix?

Thanks!

---

### Post by casfindad on 2007-10-20
On my 1 GHz Powerbook G4, I also get a black screen and cursor prompt when I try to boot with the live Gutsy desktop CD.

After updating my Feisty installation via Update Manager yesterday, I see today an option in Update Manager to upgrade to 7.10. Does anyone know if the black screen problem shows up when updating this way instead of a clean install?

casfindad

---

### Post by k49 on 2007-10-20
I had the same problem with my G3 iMac. I got the live CD to boot and install onto my hard drive, but now my installed system has the same problem, and I don't know how to fix it.

In case anyone wants to know in detail how I got this far: I downloaded the old version of the driver package (xserver-xorg-video-ati_6.6.3-2_powerpc.deb, linked above) onto a USB flash drive. Then I booted the live CD using "live-nosplash single" at the prompt. This logged me in as root in text-mode. From the command line, I mounted the USB flash drive: "mount -t vfat /dev/sdb1" in my case (this will vary depending on the disk you're using). Then I went to the directory on that drive where I had saved the driver package, and installed it using "dpkg -i xserver-xorg-video-ati_6.6.3-2_powerpc.deb". Then I started gdm (by just typing "gdm"), which brought me to the GNOME desktop. I got some error messages at first, but the installation was fine.

Now I need help: the system installed on my hard drive won't boot at all, just like the CD. What should I type at the yaboot prompt to get into command-line mode, so I can install the old driver again?

---

### Post by grazie on 2007-10-20
A number of folks seem to be having problems getting into text mode, so although this information is on wiki's and other places, I thought it might be useful to post here.

About the most useful way to get a terminal (Linux text mode) when X is giving problems is to hit <alt>+<ctrl>+<f1> together. This launches a virtual console and there are usually 6 configured (f1 through to f6). Hitting <alt>+<ctrl>+<f7> returns you to X. These can nearly always be used from an installed Linux or Live CD. However, if you've got problems with the current Gutsy video driver, then virtual consoles don't appear to be working.

If you're using the Alternate image, you can switch to a different terminal by hitting <alt>+<f2>. I think f2 to f6 are available as standard. Hit <alt>+<f1> to return to the install.

If you can't get a virtual console (as described above), adding "single" as a kernel boot parameter will get you into single user mode, which is text mode. This is equivalent to the "recovery mode" boot menu option that is available on x86 Ubuntu installations. Also the splash screen hides useful boot messages and can sometimes cause problems, so I usually recommend disabling the splash screen. So from the Live CD at the boot prompt you'd enter
```
live-nosplash single
```
And for an installed system
```
Linux single
```
Note, "Linux" above is the Ubuntu default label, so change accordingly for your own system. One of the disadvantages of single user mode is that network connections are not set up.

Another way is to temporarily disable gdm (or kdm if you using KDE). Enter single user mode as described above and perform the following.
```
$ cd /etc/X11
$ sudo cp default-display-manager default-display-manager.backup
$ sudo nano default-display-manager
```
The file should contain the text "/usr/sbin/gdm". Change this to "false" and save (don't include the quotes). On reboot gdm will be disabled and you'll start up in text mode. To re-enable gdm later, restore the backup file as follows
```
$ sudo cp /etc/X11/default-display-manager.backup /etc/X11/default-display-manager
```

---

### Post by lunalot on 2007-10-20
Sigh.  So I have succeeded in installing 7.10 on my iBook.  Had to do 'live-nosplash break=top' and then 'modprobe ide_core' to get the live CD to load.  But now I am still getting a black screen upon rebooting the system.

I first thought I'd rebuild the init ram image.  So I used the live CD to boot into single user mode (had to set break=top and 'modprobe ide_core' like usual), then mounted / and /boot and chroot'd in.  I modified /etc/initramfs-tools/modules to include ide_core and did 'update-initramfs -u'.  When I rebooted I still got the black screen.

Next I tried chroot'ing in with the live CD again to install the xserver-xorg-video-ati package linked to earlier in this thread.  I rebooted and still get the black screen.

Just to clarify, the black screen I'm getting is occurring at the point when the bootsplash/usplash stuff should appear.  In other words, after yaboot, I get the black on white screen with "found display: [stuff] opening...", then briefly black on white screen with some device id's and "Loading, pease wait...", then black screen.

Any pointers or suggestions?

---

### Post by SycloneMedia on 2007-10-21
grazie, thanks for the instructions, but it doesn't seem to work... at yaboot, i have to choose 'l' for my linux partition, and then when it goes to the boot prompt and I enter 'Linux single' it says no such file or directory... or it just starts loading and hangs on black screen again... :(

I typed 'help' and read what it said, and then I hit tab for some options, and all it says is 'Linux   old'...

so basically I still can't get into this elusive 'text mode'...

thanks for any help, please!

---

### Post by k49 on 2007-10-21
Thanks for the instructions, grazie, but I could not get into text mode by booting from my hard drive with "Linux single"--the screen still goes black. I tried the same thing as lunalot and booted into text mode from the CD again (though I don't know what "modprobe ide_core" means and I didn't have to do that to make the CD boot). I installed the xserver-xorg-video-ati package (using "dpkg --root=*myharddrive*" rather than chroot), but I still get the black screen. Lunalot's description is exactly what happens to my computer too.

I am beginning to think that maybe the xserver-xorg-video-ati package is not actually the problem, and that something else is broken. Has anyone who had the black-screen problem actually fixed it? If so, please say what you did!

---

### Post by codeman38 on 2007-10-21
Don't know whether I should just make this a new thread, but I've been trying to run the Gutsy Live CD on my PowerBook G4 (Aluminum 1.67GHz) with no luck.  (Feisty had no problem on the same machine.)

Specifically, the things I've tried:

Running the default 'live' at the boot prompt gives me weird psychedelic colors on my screen when the splash screen should come up.

Running 'live-nosplash' or 'live-nosplash single' avoids that issue, but then gives me the BusyBox prompt.  I've tried entering 'modprobe ide_core' at the prompt and then exiting, but then I get this:

> cp: unable to open `/root/var/log': No such file or directory
mount: Mounting /root/dev on /dev/.static/dev failed: No such file or directory
mount: Mounting /sys on /root/sys failed: No such file or directory
mount: Mounting /proc on /root/proc failed: No such file or directory
Target filesystem doesn't have /sbin/init

'live-nosplash break=top' gets me to the BusyBox prompt... where I'm unable to type the modprobe command because the keyboard's not recognized (either internal or USB)! ](*,)

Any suggestions?  Or should I just stay with Feisty?

---

### Post by k49 on 2007-10-21
I think the modprobe ide_core thing is entirely separate from the xserver-xorg-video-ati problem. It's been discussed in other threads, and it seems like other people have gotten it to work. (I don't know what "modprobe ide_core" does, but from the errors it seems like it might work if you try doing it while you're in / rather than in /root. That is, type "cd /" first. It might be a lot more complicated though.)

I sure hope that someone who actually knows what's going on will read this thread...

---

### Post by codeman38 on 2007-10-21
No, typing 'cd /' beforehand doesn't change the results. Still kicks me back into BusyBox.

---

### Post by zjokke on 2007-10-21
3rd attempt to use Ubuntu on my iBook G3... installed 7.10 with the Alternate CD and now have an non-working install (I get the text loading... and then my screen blocks and slowly turns black, starting from the outside, and then slowly it turns almost white). I don't really understand how I can get into a terminal window. I tried ALT-F1 and ALT-CTRL-F1 at various screens, typed all kind of stuff I read here, couldn't find a busybox... guess I'm giving up. Maybe I'm a spoiled Mac user and I think that when a system tells me it will reboot, it actually does so.... Should I wait another 3-4 months to see if Ubuntu works on my Mac? Sorry if I sound a bit frustrated or dissappointed... just lost 16 hours again trying to become a member of the Ubuntu community... :-(

---

### Post by k49 on 2007-10-21
We seem to have two separate problems here. Someone please confirm that:[INDENT]
1. The bug with IDE drivers not being loaded at startup (if that is what the "ide_core" thing is about) is completely unrelated to the bug with the screen going black.

2. The bug with the screen going black, which some people blamed on the new version of the xserver-xorg-video-ati package, is not actually fixed by downgrading to the old version (6.6.3-2) of that package.[/INDENT]

I know the IDE problem is being fixed, since there was already a bug report about it (linked on the first page). If anyone has found a way around the bug with the screen going black, please post. (And then submit a bug report saying what you did, since there doesn't seem be one about this yet.)

---

### Post by Eberbachl on 2007-10-22
Thanks to everyone for this great thread!

Followed BladeMelbourne's instructions to downgrade the ATI video driver on my G4 Mac Mini, and Gutsy is working nicely now.

I get notification that an updated ATI driver is available for installation of course, but as long as I don't do that I think everything should be fine.

For the record, this is what was happening:

Neither the 7.10 live CD or the alternate install CD worked. Installation was ok from the alternate Cd, but after install I just had the black screen bug. I could access a CLI ( [CTRL]+[ALT]+[F1] ), but not X windows.

I did the following (thanks BladeMelbourne for the instructions a few pages ago)

1: I downloaded xserver-xorg-video-ati_6.6.3-2_powerpc.deb
2: Copied it to a CD (becasue I had trouble mounting my USB key at the CLI)
3: Boot into the CLI ( *Linux single* at the boot menu)
4: Mount CD, then copy the xserver-xorg-video-ati_6.6.3-2_powerpc.deb file to /home/*user*/
5: *sudo dpkg -i /home/user/xserver-xorg-video-ati_6.6.3-2_powerpc.deb*

Reboot, and now everything works very nicely.

Although graphics worked nicely, I then took some further instructions (from the PowerPC FAQ) to enhance 3D Graphics, and changed the name of the driver from "ati" to "radeon" in xorg.conf, also adding 

Option          "AGPMode" "4"
Option          "AGPFastWrite" "true"

...to the Device section.

Cheers,

;)

Luke.

---

### Post by BladeMelbourne on 2007-10-22
Hi Luke,

Are you using the Apple DVI->VGA adapter by any chance? I am - one of the recent changes after 6.6.3 was to add a MacMini option, which specifies the connectortable (presumably for the DVI-VGA conversion). Unfortunately this didn't work for me (I spent hours researching and experimenting).

Out of curiousity, what framerate do you get with glxgears?

Mike

---

### Post by Eberbachl on 2007-10-22
Hi Mike,

I'm just using the DVI out on the mini directly to a Samsung 740b LCD screen. No adapter.

...not sure on the glxgears frame rate - will look later tonight when I get home from work.

( EDIT: Never mind ;) I answered my own noob question :D )

;)

Cheers,

Luke.

---

### Post by SycloneMedia on 2007-10-22
> **codeman38 said:**
> Don't know whether I should just make this a new thread, but I've been trying to run the Gutsy Live CD on my PowerBook G4 (Aluminum 1.67GHz) with no luck.  (Feisty had no problem on the same machine.)

Specifically, the things I've tried:

Running the default 'live' at the boot prompt gives me weird psychedelic colors on my screen when the splash screen should come up.

Running 'live-nosplash' or 'live-nosplash single' avoids that issue, but then gives me the BusyBox prompt.  I've tried entering 'modprobe ide_core' at the prompt and then exiting, but then I get this:



'live-nosplash break=top' gets me to the BusyBox prompt... where I'm unable to type the modprobe command because the keyboard's not recognized (either internal or USB)! ](*,)

Any suggestions?  Or should I just stay with Feisty?

Try this, it's what worked for me... 'live-nosplash-powerpc video=ofonly'
That'll get you to where most of us are stuck...

No one yet is telling us yet how to get INTO the text mode to change that driver in our specific situation. The people who have managed to get into text mode I guess are not having to go through yaboot? I don't know... waiting patiently... please, someone... with a cherry on top?  :)

---

### Post by BladeMelbourne on 2007-10-22
> **SycloneMedia said:**
> 
No one yet is telling us yet how to get INTO the text mode to change that driver in our specific situation. The people who have managed to get into text mode I guess are not having to go through yaboot? I don't know... waiting patiently... please, someone... with a cherry on top?  :)

I have a yaboot option to boot into text mode. Gutsy has been installed for a while now, so I can't remember if I put it there.
When at home, I will report back my /etc/yaboot.conf contents.

Out of interest, have you tried pressing Tab at the yaboot menu to see a list of available options?
(Not the 1st menu that choses between OS X, Linux and CD ROM, the second menu that allows you to pick which kernel and parameters you want to boot with.)

---

### Post by SycloneMedia on 2007-10-22
> **BladeMelbourne said:**
> I have a yaboot option to boot into text mode. Gutsy has been installed for a while now, so I can't remember if I put it there.
When at home, I will report back my /etc/yaboot.conf contents.

Out of interest, have you tried pressing Tab at the yaboot menu to see a list of available options?
(Not the 1st menu that choses between OS X, Linux and CD ROM, the second menu that allows you to pick which kernel and parameters you want to boot with.)

Yes, I pressed Tab and it replied with only one option: 'Linux            old'

:confused:

...and I tried typing 'Linux single' there but it just ignores the 'single' and boots as 'Linux' to the black screen of death... 

...an interesting tidbit (which may or may not mean anything) at the black screen the keyboard is NOT inactive: if you have your sound on, and you type some characters (which are invisible to you since the screen is black, and then hit delete the same number of characters you typed, it is silent (hence erasing) and then it'll beep every time you hit delete when it's empty again... but I guess that just proves it's a display driver issue, duh, nm... lol...

---

### Post by Eberbachl on 2007-10-22
If "Linux single" at the boot menu doesn't work (it did for me - but it was from the second boot menu, not the first), once you have the black screen try pressing [CTRL]+[ALT]+[F1]

That should take you to a CLI login prompt.

---

### Post by BladeMelbourne on 2007-10-22
> **SycloneMedia said:**
> 
...and I tried typing 'Linux single' there but it just ignores the 'single' and boots as 'Linux' to the black screen of death... 

...an interesting tidbit (which may or may not mean anything) at the black screen the keyboard is NOT inactive: if you have your sound on, and you type some characters (which are invisible to you since the screen is black, and then hit delete the same number of characters you typed, it is silent (hence erasing) and then it'll beep every time you hit delete when it's empty again... but I guess that just proves it's a display driver issue, duh, nm... lol...

Your black screen issue is different to the way mine was - the keyboard was non-responsive after the first keypress. Ctrl-Alt-F1..F8 didn't work.

This inside /etc/yaboot.conf allows me to boot into a text console.

image=/boot/vmlinux
        label=LinuxText
        read-only
        initrd=/boot/initrd.img
        append="video=ofonly single"
(Edit using sudo nano /etc/yaboot.conf -> then run sudo ybin -v to write the changes to the bootsector.)

Do you have another box at home (Windows, Mac or Linux)? You could ssh over the network to your Linux box, and then type "sudo telinit 2" to kill xwindows and drop to a terminal. Or you could ssh and update Yaboot, then reboot the box.

---

### Post by grazie on 2007-10-22
Oh dear! This thread is beginning to drop into 'Chinese Whispers'. If you really want Gutsy up and running NOW THIS INSTANT start learning how to use[ Launchpad]("https://launchpad.net/") and how to raise or add to [bug reports]("http://www.ubuntu.com/community/reportproblem")
> **k49 said:**
> I sure hope that someone who actually knows what's going on will read this thread...
Comments like that  don't often get answered.

> **SycloneMedia said:**
> No one yet is telling us yet how to get INTO the text mode to change that driver in our specific situation.
You serious? I thought I gave a number of suggestions earlier in the thread. However, I'm very surprised "Linux single" doesn't work for you. As you can get into text mode from the Live CD why not fix the problem from there? You could chroot, but an easier option would be to disable gdm by mounting the installed Gutsy partition. So, boot into text mode using your Live CD. Find out which partition Gutsy has been installed to using the following command
```
$ fdisk -l
```
The correct partition can be identified by "Linux native" in the output of the above command. If you've got more than 1 Linux installation hopefully you can identify the correct one. I'm assuming it's installed on /dev/hda (for IDE/PATA) or /dev/sda (for SCSI or SATA), so the Gutsy root partition will be either /dev/hdax or /dev/sdax,  where x  is 1, 2, 3, etc, but your installation may be different. Then mount the partition as follows (using the correct device name)
```
$ mount /dev/hdax /mnt
```
Edit to disable gdm as described earlier with the following command
```
$ nano /mnt/etc/X11/default-display-manager
```
Unmount and reboot
```
$ umount /mnt
$ reboot
```
BladeMelbourne's suggestion above makes things more complicated than needed and it requires that you know the Linux box has successfully booted (and you've set up an account which you can login with). It is possible to update yaboot by chrooting from another Linux image, but I'm not going to explain that now as it isn't necessary. The important part of that posting is the line 'append="video=ofonly single"'. This is no different to adding "video=ofonly single" kernel paramaters at the boot: prompt (but the video=ofonly isn't needed)

There appears to be some confusion about kernel parameters and what they actually do and labels that can be given to kernel images when using yaboot. The kernel parameter "video=ofonly" instructs the kernel to load and use the ofonly driver when using X. It very similar to the vesa driver on x86. If you're not using  X (i.e. text mode) it has no use. It is often used when you get display problems in X due to a buggy video driver. However, it doesn't appear to be working on Gutsy for my machine, but others on this thread have had success. The kernel parameter "single" instructs the kernel to boot into single user mode (or runlevel 1), which uses text mode.

There are quite a few boot options on the Desktop (Live) and Alternate CDs, such as "live", "live-nosplash", "install", "cli", etc. These are all labels that have associated kernel paramaters used by yaboot. On installation "Linux" and "old" labels are set up for yaboot by Ubuntu as default. "Linux" will point to the latest installed kernel and "old" will point to kernel prior to the latest. On new installs they are the same.

Hitting <alt>+<ctrl>+<f1> keys together will launch a virtual console (f2 to f6 can also be used). <alt>+<ctrl>+<f7> will return to X. They have nothing to do with runlevels. Again they don't appear to be working for everyone on Gutsy.

---

### Post by grazie on 2007-10-22
> **SycloneMedia said:**
> Yes, I pressed Tab and it replied with only one option: 'Linux            old'

That's two options, "Linux" and "old".

---

### Post by BladeMelbourne on 2007-10-22
> **grazie said:**
> 
BladeMelbourne's suggestion above makes things more complicated than needed and it requires that you know the Linux box has successfully booted (and you've set up an account which you can login with).

Those of us who did network upgrades don't have Gutsy installation CDs to boot off. At the end of the day, using ssh to add a new boot option will be more useful than disabling gdm - it doesn't need to be reversed when the xorg configuration is corrected. This suggestion is off Ubuntu/Debian/Freedesktop bug-trackers. Not much use if booting off a live cd though...

> **grazie said:**
> 
There appears to be some confusion about kernel paramaters and what they actually do and labels that can be given to kernel images when using yaboot. The kernel parameter "video=ofonly" instructs the to kernel to the load and use the ofonly driver when using X. It very similar to the vesa driver on x86. If you're not using  X (i.e. text mode) it has no use.
I was running startx and X from runlevel 1 after editing my xorg configuration file.

---

### Post by grazie on 2007-10-22
> **BladeMelbourne said:**
> Those of us who did network upgrades don't have Gutsy installation CDs to boot off. At the end of the day, using ssh to add a new boot option will be more useful than disabling gdm - it doesn't need to be reversed when the xorg configuration is corrected. This suggestion is off Ubuntu/Debian/Freedesktop bug-trackers. Not much use if booting off a live cd though...Remotely logging in is a very useful option for fixing problems. All I was saying was that doing so (and knowing that you're doing it right) maybe is more than is needed here when you can add kernel parameters at the boot prompt. If for some unknown reason adding kernel parameters isn't working (this is unusual) then I think your aproach would be good.

> **BladeMelbourne said:**
> I was running startx and X from runlevel 1 after editing my xorg configuration file.I wasn't referring to any of your posts with my comments about kernel parameter confusion. Apologies if it came over that way.

---

### Post by Eberbachl on 2007-10-22
> **grazie said:**
> 

Hitting <alt>+<ctrl>+<f1> keys together will launch a virtual console (f2 to f6 can also be used). <alt>+<ctrl>+<f7> will return to X. They have nothing to do with runlevels.

Of course you're quite right. Apologies, and thanks for the correction...:oops:

---

### Post by k49 on 2007-10-22
First of all:

> **k49 said:**
> I sure hope that someone who actually knows what's going on will read this thread...

grazie, I didn't mean that as a complaint; I meant that I didn't know what was causing the problem, so I hoped that someone who did know would read it and answer better than I could. Sorry it sounded like a complaint.

Secondly, it seems like I was wrong that the xserver-xorg-video-ati package was not the problem--downgrading it seems to fix the black-screen bug for at least some people. Any ideas about what else might be wrong if downgrading the package doesn't change anything?

Also, while I can get into text mode when booting from the CD, no kernel parameters seem to get me into text mode when booting from the hard drive; I still get the black screen. I think I'm not the only one that this happens to. (I can get into BusyBox by booting from the hard drive with "break=top", but I can't type anything there.)

---

### Post by grazie on 2007-10-22
K49,

The best thing to do is raise a bug report once you've collected enough information. I see from an earlier post that you've got a G3 iMac which is well known for black screen problems and is detailed in [FAQ]("https://wiki.ubuntu.com/PowerPCFAQ#head-def39b758fa5328bd61aaead82e4c0588b4a4f70"). Is this the first time you've tried Ubuntu on this machine? How much RAM does it have? Have you tried the Desktop or Alternate CDs (or both). You should still be able to boot using text mode, but if kernel parameters aren't working...I dunno. Once you've given a bit more detail on your machine and what you have and haven't tried we should get a bit further. However, if this is you first go with Linux you may be better trying Feisty or perhaps Dapper, which was the last PPC build with full Canonical support.

---

### Post by lunalot on 2007-10-22
Recap: iBook G4, installed 7.10, added ide_core to initramfs, downgraded ati drivers. Still getting black screen.

I haven't tried using 'video=ofonly' on my installation yet to get the boot to succeed. I will try that tonight.  But is it possible that this is usplash related?  Or does usplash use xserver?

---

### Post by Eberbachl on 2007-10-22
> **BladeMelbourne said:**
> Hi Luke,

Are you using the Apple DVI->VGA adapter by any chance? I am - one of the recent changes after 6.6.3 was to add a MacMini option, which specifies the connectortable (presumably for the DVI-VGA conversion). Unfortunately this didn't work for me (I spent hours researching and experimenting).

**Out of curiousity, what framerate do you get with glxgears?**

Mike

Consistently around 717 FPS (G4 1.42 Ghz Mac Mini, 1GB RAM, 32MB on-board Radeon 9200 graphics)

;)

---

### Post by BladeMelbourne on 2007-10-22
Hey Luke,

I'm getting 813 FPS with my current xorg.conf - with the exact hardware that you have.
It's still a work in progress, but I can upload a copy if you're interested.

Unfortunately, compiling the latest sourcecode from git ([http://gitweb.freedesktop.org/?p=xorg/driver/xf86-video-ati.git;a=summary](http://gitweb.freedesktop.org/?p=xorg/driver/xf86-video-ati.git;a=summary)) resulted in the same behaviour as the latest Gutsy xserver-xorg-video-ati.

My next step will be to compare /var/log/Xorg.0.log output generated for the working Feisty driver and compare that to the not-working Gutsy driver. Followed by either raising a bug or identifying which change caused the issue, and attempting to compile a working version.

On our hardware, I believe that Compiz detects that it can do effects on a desktop 1024x1024 pixels at 32 bit. This sucks, because I want 1280x1024. I can only do 1280x1024 with Compiz at 16 bit colour. But that doesn't belong in this thread ;-)

Mike

---

### Post by lunalot on 2007-10-23
> **lunalot said:**
> Recap: iBook G4, installed 7.10, added ide_core to initramfs, downgraded ati drivers. Still getting black screen.

I haven't tried using 'video=ofonly' on my installation yet to get the boot to succeed. I will try that tonight.  But is it possible that this is usplash related?  Or does usplash use xserver?

So I just tried 'video=ofonly' with my ide_core-modified ramdisk and downgraded ati drivers, and can now add it to my list of Things That Don't Fix the Black Screen.

I ask again if anyone knows if the problem could be usplash...  The reason I ask is that I was only able to boot the Live CD using the live-nosplash kernel.  Is it possible to disable the graphical boot?

---

### Post by Eberbachl on 2007-10-23
> **BladeMelbourne said:**
> Hey Luke,

I'm getting 813 FPS with my current xorg.conf - with the exact hardware that you have.
It's still a work in progress, but I can upload a copy if you're interested.

Unfortunately, compiling the latest sourcecode from git ([http://gitweb.freedesktop.org/?p=xorg/driver/xf86-video-ati.git;a=summary](http://gitweb.freedesktop.org/?p=xorg/driver/xf86-video-ati.git;a=summary)) resulted in the same behaviour as the latest Gutsy xserver-xorg-video-ati.

My next step will be to compare /var/log/Xorg.0.log output generated for the working Feisty driver and compare that to the not-working Gutsy driver. Followed by either raising a bug or identifying which change caused the issue, and attempting to compile a working version.

On our hardware, I believe that Compiz detects that it can do effects on a desktop 1024x1024 pixels at 32 bit. This sucks, because I want 1280x1024. I can only do 1280x1024 with Compiz at 16 bit colour. But that doesn't belong in this thread ;-)

Mike

Thanks - but I'm thinking I might cut over to Gutsy on an AMD64 platform. The little mini is neat but I think some of it's limitations might frustrate me ;)

I might have to ssend my faithful little mini off to eBay ;)

---

### Post by lunalot on 2007-10-23
Success!

I disabled usplash after reading the recommendation here: [http://ubuntuforums.org/showthread.php?t=289302#2](http://ubuntuforums.org/showthread.php?t=289302#2)

However, that didn't work as described there.  I had to use the Live CD (with 'live-nosplash break=top single', at the initramfs prompt issued 'modprobe ide_core; exit') and then mount my root filesystem (on /mnt).  **Then I edited /mnt/etc/yaboot.conf, and then ran '/mnt/usr/sbin/ybin -C /mnt/etc/yaboot.conf'.** (This didn't work when chroot'd because the chroot environment doesn't have the /dev node for the HFS boot device and thus can't install the loader.)  After that I was able to reboot successfully without any futzing with kernel options or modules.

Now onto other problems I'm having in my installation.

Thanks to everyone's help here.

---

### Post by boweer on 2007-10-23
i have tried for several hours to install 7.10 on my tibook g4 400 mhz with 384 mb ram...

but i cant get any further than to the black screen that appears after i started the "live" alternative


i want it so much to work, dont know thou...

---

### Post by grazie on 2007-10-23
> **boweer said:**
> but i cant get any further than to the black screen that appears after i started the "live" alternative
I don't understand what you mean by this. Have you tried the Desktop (Live) CD or Alternate CD or both? Have you tried any of the workarounds suggested on this thread?

---

### Post by boweer on 2007-10-23
yeah, havnt worked yet...

i have tried 6.06 on the computer and that version worked just fine.

---

### Post by k49 on 2007-10-23
> **grazie said:**
> I see from an earlier post that you've got a G3 iMac which is well known for black screen problems and is detailed in [FAQ]("https://wiki.ubuntu.com/PowerPCFAQ#head-def39b758fa5328bd61aaead82e4c0588b4a4f70"). Is this the first time you've tried Ubuntu on this machine? How much RAM does it have? Have you tried the Desktop or Alternate CDs (or both). You should still be able to boot using text mode, but if kernel parameters aren't working...I dunno. Once you've given a bit more detail on your machine and what you have and haven't tried we should get a bit further. However, if this is you first go with Linux you may be better trying Feisty or perhaps Dapper, which was the last PPC build with full Canonical support.

I've been using Ubuntu on this computer since 6.06/Dapper and until recently it was working fine with 7.04/Feisty. It has 512 MB of RAM, so that shouldn't be a problem. I'm aware of the original G3 iMac black-screen issue, but I think they may have fixed it by now because I didn't need to change anything in xorg.conf when doing a clean install of 7.04 (or when booting from the CD). I haven't tried the alternate CD, but I assume the installed system would be the same.

In this case, unlike with the original iMac black screen problem, it's impossible to get into text mode by pressing control-alt-F1 because the boot process doesn't make it that far. Also, the strange thing is that my hard disk spins down when the screen goes black--the only way to tell that the computer is still on is that the LED in the power button is still lit. Does this happen to anyone else?

---

### Post by grazie on 2007-10-23
> **k49 said:**
> I haven't tried the alternate CD, but I assume the installed system would be the same.

In this case, unlike with the original iMac black screen problem, it's impossible to get into text mode by pressing control-alt-F1 because the boot process doesn't make it that far. Also, the strange thing is that my hard disk spins down when the screen goes black--the only way to tell that the computer is still on is that the LED in the power button is still lit. Does this happen to anyone else?

Your correct in that the installed system will have the video driver problem, but as the Alternate installer is text base (not X as per the Desktop) you can at least install Gutsy without too many problems - hopefully none as I did.

The effect of the X video driver bug which has been raised but not confirmed last time I checked (I and others here should add to it), is that you lose video and keyboard. Linux still runs OK. This loss of keyboard is why you can't get a virtual console (control-alt-F1). Your only practical options are to remotely login (but you can't) and shutdown or hit the power (off) switch. If you've got on Old World Mac with serial ports you can possibly get in using those, but that doesn't apply to many now.

In addition to what's already been discussed, I cannot get virtual consoles after the video driver has been rolled back to an earlier version, but I've not investigated the reasons why yet.

---

### Post by k49 on 2007-10-23
> **grazie said:**
> Your correct in that installed system will have the video driver problem, but as the Alternate installer is text base (not X as per the Desktop) you can at least install Gutsy without too many problems - hopefully none as I did.

I'm not sure I made this clear before, but I actually did manage to boot the live CD and install--I can get to a virtual console when booting from the CD, so I downgraded the video driver and it worked fine. But I can't get to a virtual terminal when booting from the hard drive, even after I downgraded the video driver (while running from the CD). When I get a chance, I will try installing the alternate CD to see if anything is different.

If my hard drive spins down, is that a different problem entirely?

---

### Post by grazie on 2007-10-23
Erm, I think you may be a little confused...I certainly am. 
> **k49 said:**
> I'm not sure I made this clear before, but I actually did manage to boot the live CD and install--I can get to a virtual console when booting from the CD, so I downgraded the video driver and it worked fine.

I can't tell when you're referring to the booted Live CD image or the booted HD image. The scenario you may be describing is that you booted from the Live CD, got the black screen, launched a virtual console, downgraded the video driver, restarted X and did your install. Yes/No? If yes, there still a few things that don't add up.

> **k49 said:**
> But I can't get to a virtual terminal when booting from the hard drive, even after I downgraded the video driver (while running from the CD).
You can't downgrade the video driver on the HD installation by using the Live CD unless you chroot. Did you do this? If not, all you did was downgrade the video driver of the loaded Live CD image. It also seems rather odd that you can get a virtual console when booting from the Live CD, but not when booting from the HD.

> **k49 said:**
> When I get a chance, I will try installing the alternate CD to see if anything is different.
If I half understand you correctly, this will not achieve anything.

---

### Post by k49 on 2007-10-23
> **grazie said:**
> Erm, I think you may be a little confused...I certainly am. 


I can't tell when you're referring to the booted Live CD image or the booted HD image. The scenario you may be describing is that you booted from the Live CD, got the black screen, launched a virtual console, downgraded the video driver, restarted X and did your install. Yes/No?.

Yes. Sorry I was unclear.

> **grazie said:**
> You can't downgrade the video driver on the HD installation by using the Live CD unless you chroot. Did you do this?

Yes. I tried it first using "dpkg --root" and another time with chroot.

> **grazie said:**
> It also seems rather odd that you can get a virtual console when booting from the Live CD, but not when booting from the HD.

I thought so too.

> **grazie said:**
> If I half understand you correctly, this will not achieve anything.

Probably not. But I figured that since I didn't know what was happening, I might as well try the alternate CD--if there's a mysterious difference between the live CD and the HD, there might also be a mysterious difference between installing from the live CD and installing from the alternate CD.

---

### Post by SycloneMedia on 2007-10-23
> **lunalot said:**
> Success!

I disabled usplash after reading the recommendation here: [http://ubuntuforums.org/showthread.php?t=289302#2](http://ubuntuforums.org/showthread.php?t=289302#2)

However, that didn't work as described there.  I had to use the Live CD (with 'live-nosplash break=top single', at the initramfs prompt issued 'modprobe ide_core; exit') and then mount my root filesystem (on /mnt).  **Then I edited /mnt/etc/yaboot.conf, and then ran '/mnt/usr/sbin/ybin -C /mnt/etc/yaboot.conf'.** (This didn't work when chroot'd because the chroot environment doesn't have the /dev node for the HFS boot device and thus can't install the loader.)  After that I was able to reboot successfully without any futzing with kernel options or modules.

Now onto other problems I'm having in my installation.

Thanks to everyone's help here.

:KS :KS :KS

Bravo! Yes your fix worked! Thank you very much for posting it back here for others to try.

So... I guess the problem for us was not with the ATI package, but rather just the splash at bootup.

As a review for others in the same black-screen-of-death boat:

1. Use the live CD, at the prompt, I typed: ```
live-nosplash-powerpc video=ofonly
```
This should get you loaded and able to install. Once you've installed, you'll probably still have the black screen. No worries now, let's continue...

2. Repeat step 1. (to get into a working environment)

3. Mount your real installation as follows (in a terminal of course which should be no problem now as you're loaded): ```
sudo mount "type the name of your installed system partition here--- mine was /dev/hda5---without these quotes" /mnt
```

4. Edit the INSTALLATION yaboot.conf file. I used the terminal: ```
sudo nano /mnt/etc/yaboot.conf
```

- remove the words "quiet splash" (or just "splash" - I'm going to try that later) from the append line.

- save the file. in nano, you just hit ctrl-x, and then 'y' for yes to save, and then enter again to confirm the file name save (don't change it)...

5. in the terminal, type: ```
sudo /mnt/usr/sbin/ybin -C /mnt/etc/yaboot.conf
```

That's it! You're done... now just restart without the CD and you should be good to go...
thanks to everyone for the help and research, and thanks to lunalot for the fix. :)

---

### Post by lunalot on 2007-10-24
> **SycloneMedia said:**
> :KS :KS :KS
...
thanks to lunalot for the fix. :)

you're welcome, and thanks for putting together the nice write up.  also, for clarification, i'm using the latest xorg ati drivers, not the ones linked in this thread.

(on a separate note, i then had to wrestle with the wifi firmware, which was tripping up the GNOME subsystems, dbus and hal.  i used the tool here: [http://ubuntuforums.org/showthread.php?t=405990](http://ubuntuforums.org/showthread.php?t=405990) and ignored its warning about the incompatible kernel.  rebooted and it works.)

---

### Post by 4Jazz on 2007-10-24
Hello 1st post I am definitly a noob I followed the directions and was able to hit alt+f2 and get rid of and edit Yaboot and do the update of yaboot, but upon reboot I still have the same problem it stops in Busybox /etc/rc.local and stays there no gnome but if I say startx it will try and fail if i type gdm it says it is already running I am not @ the computer right now but any help would be helpfull.

---

### Post by k49 on 2007-10-25
Somehow, I got my computer to boot up in 7.10. I'm still not sure what the problem was, but I'll post everything I did in the hope that it will help someone else:

I reinstalled 7.10 using the alternate CD, which worked fine. When booting from this installation (with nothing changed yet), I didn't get the black screen problem--instead, my computer froze as soon as the splash screen appeared, so I had to restart.

I did what SycloneMedia said and tried booting from the live CD with "live-nosplash-powerpc video=ofonly", but I got dropped to BusyBox, where typing "modprobe ide_core" didn't work. I tried booting with a some other combinations of parameters, including "live-nosplash single" (which had worked for me before!) but these all had the same effect. So instead, I tried booted from a 7.04 (Feisty) live CD using "live-nosplash single"--and that got me into text mode.

I made the changes to the yaboot.conf file as SycloneMedia said. When I rebooted, it seemed like it was going to work, but part-way through the boot process I got dropped to BusyBox again, with an error message saying "/dev/hda3" (my hard drive) did not exist. This time, typing "modprobe ide_core; exit" *did* work, and everything else was fine.

Thanks for your help, everyone. I hope at least some of what I did works for someone else.

Also, I had some minor problems when I logged into the GNOME desktop: the volume-control applet and the GNOME settings daemon either crashed or would not start, and (consequently?) all the windows are displayed in the ugly default theme. I'd like to know if anyone else had that problem or knows what to do about it.

---

### Post by Caraibes on 2007-10-25
> **k49 said:**
> Somehow, I got my computer to boot up in 7.10. I'm still not sure what the problem was, but I'll post everything I did in the hope that it will help someone else:

I reinstalled 7.10 using the alternate CD, which worked fine. When booting from this installation (with nothing changed yet), I didn't get the black screen problem--instead, my computer froze as soon as the splash screen appeared, so I had to restart.

I did what SycloneMedia said and tried booting from the live CD with "live-nosplash-powerpc video=ofonly", but I got dropped to BusyBox, where typing "modprobe ide_core" didn't work. I tried booting with a some other combinations of parameters, including "live-nosplash single" (which had worked for me before!) but these all had the same effect. So instead, I tried booted from a 7.04 (Feisty) live CD using "live-nosplash single"--and that got me into text mode.

I made the changes to the yaboot.conf file as SycloneMedia said. When I rebooted, it seemed like it was going to work, but part-way through the boot process I got dropped to BusyBox again, with an error message saying "/dev/hda3" (my hard drive) did not exist. This time, typing "modprobe ide_core; exit" *did* work, and everything else was fine.

Thanks for your help, everyone. I hope at least some of what I did works for someone else.

Also, I had some minor problems when I logged into the GNOME desktop: the volume-control applet and the GNOME settings daemon either crashed or would not start, and (consequently?) all the windows are displayed in the ugly default theme. I'd like to know if anyone else had that problem or knows what to do about it.
I had most of the same. I wiped Gutsy for Dapper, because Dapper PPC will be officially supported by Canonical until 2009 on the desktop...

---

### Post by helixblue on 2007-10-25
> **slartibertfast said:**
> Hello,

I've tried to install Gutsy on my Mac mini G4 as well as on my Powerbook G4. On both Macs the installation stops shortly after the boot promt. The screen gets dark (monitor goes into sleep mode) and thats it.
The command "live video=ofonly" obviously does nothing useful.

This has also been the case with all pre-released versions I've tested.

I'm currently installing Opensuse 10.3 PPC which seems to work without a hitch. But I want Gutsy !! ;-)

Anybody some suggestions ??

Thanks.

I found that switching out of X11 (Ctrl-Alt-F1) and switching back  (Cmd-F7) when you see the black screen makes X11 work for on my ATI Radeon. At least that works on the 7.10 Live CD.

---

### Post by Tommy on 2007-10-25
> **Caraibes said:**
> I wiped Gutsy for Dapper, because Dapper PPC will be officially supported by Canonical until 2009 on the desktop...

I don't want to pull this thread TOO far off track, but I have seen differing statements on this issue -- one item I read said the LTS PowerPC support was intended for *servers* and not for the desktop. HOWEVER, there was a Dapper upgrade to Firefox just the other day, so the answer may ultimately boil down to how you're using it. 

Dapper still *works*, but there are several important applications that won't easily  upgrade in Dapper because the supporting libraries have moved on.

IMHO the problem goes back to the Debian structure Ubuntu depends upon -- a leadership vacuum developed in the Debian PowerPC community and the problems bubbled downstream into Ubuntu.

There are some really knowledgeable people working actively with Ubuntu (as with Debian) so the "community support" may eventually get it straight. But we need somebody with the right credentials taking some control on behalf of the PowerPC community.

---

### Post by Caraibes on 2007-10-25
PPC for Linux seems to be getting less and less momentum... Too bad for all of us with a PPC machine that still works great...

---

### Post by Connelley on 2007-10-30
I'm trying to install Gutsy on an iMac; 400; 40 gig HD with Ubuntu Desktop CD(purchased) and got the same black screen.

I followed SycloneMedia's instructions.

"1. Use the live CD, at the prompt, I typed:
Code:
live-nosplash-powerpc video=ofonly
This should get you loaded and able to install. Once you've installed, you'll probably still have the black screen. No worries now, let's continue..."

It didn't load.  After 30 secs. or so. I got BusyBox re: Built-in Shell [Ash]

(Screen)
Loading, Please wait...

BusyBox _ _ _  Built-in shell (Ash)

(initramfs) modprobe ide_core
   * I waited until disk spun down*
(initramfs) exit

cp: unable to open 'root/var/log/' : No such file or directory
mount: Mounting /root/dev/.static/dev failed : No such file or directory
mount: Mounting /sys on/root/sys failed : No such file or directory
mount: Mounting /proc on/root/proc failed : No such file or directory
Target filesystem doesn't have /sbin/init

*Back to BusyBox*

I'm a 70 year old, and not the sharpest knife in the drawer when it comes to computers.

What's the next step?  I've downloaded the Alternate disk and had no luck there either.

Connelley

---

### Post by vijaym on 2007-11-02
I had the same problem installing ubuntu 7.10. but it was erratic. did not have the message all the time. 

tried a few times and it avoided that problem sometimes.

if you really want to try i would suggest that you say
live-nosplash-powerpc break=top video=ofonly

on the next screen say

modprobe ide_core; exit

This should take you to the live cd screen. you willl need to wait a while until this happens. go have coffee or tea or something.

At this point explore the system or try and install.

I am not sure if it will work as my attempt failed to install 7.10.

I then reverted to 7.04 and everything installed fine.

There are better skilled people on the forum who can give you better advice.

---

### Post by oswaldkelso on 2007-11-02
> **Tommy said:**
> 
IMHO the problem goes back to the Debian structure Ubuntu depends upon -- a leadership vacuum developed in the Debian PowerPC community and the problems bubbled downstream into Ubuntu.

There are some really knowledgeable people working actively with Ubuntu (as with Debian) so the "community support" may eventually get it straight. But we need somebody with the right credentials taking some control on behalf of the PowerPC community.

There are some very good discussions as to the differences between ubuntu and debian in the ubuntu cafe. 


[URL="http://ubuntuforums.org/showthread.php?t=179304&page=7"]
http://ubuntuforums.org/showthread.php?t=179304&page=7[/URL]
[URL="http://ubuntuforums.org/showthread.php?t=341553&page=2"]
http://ubuntuforums.org/showthread.php?t=341553&page=2[/URL]

IMHO the problems are not leadership but goals. And i can only see the gap widening and ubuntu development being able to  take less from debian as time moves on due to these differing goals. I see a split in the future and ppc users will have to change  to 386 or move to debian like me, or fedora suse etc.

The only way I can see them staying close is if either debian chooses to support less architectures (13 I think ) or ubuntu  helps them support those architectures. And as we see with ppc that just aint going to happen.

i think we may be going off track but at least ppc user may get an understanding off what may be at the core of the gusty problems.

---

### Post by Tommy on 2007-11-02
Thank you, oswaldkelso, for the links. This helps me sort out some of the things I have been learning lately.

Unfortunately for Ubuntu PowerPC users, there has not been an obvious person or avenue to take over the releases since Canonical dropped support. Ubuntu PPC has nobody apparently in charge, and the Gutsy "release" seems to have been an un-tested snapshot with the automated Ubuntu tweaks injected and no additional fixes applied. (This is my perception -- I would love to be proven wrong.)

If nobody takes control now, it seems there's no reason to stay with Ubuntu on PowerPC, unless you're on Dapper until its end of life. Fortunately (assuming Debian developers assert some level of control and continue the platform) Debian is a natural place to go for PPC folks. Everything you've learned here (except for the Ubuntu tweaks) applies.

But the answer may be different for everyone. Gentoo is apparently one of the best distros for learning about the guts of the system. I personally like Debian's package management and attention to quality better than some of the other distros I tried, and (so far) have been able to run it on my PPC as well as Intel hardware. I'd like to learn more about the guts but I also want a stable platform to build upon, and some user-attention and consistency across systems seems easier with Ubuntu than in Debian or Gentoo. 

Weighing it all, however, I'm more likely to drop **PowerPC** than to switch from Ubuntu, at least at the moment. As my needs change, I'll re-evaluate with each release.

For now I'm running my 1998 PowerBook G3 (using 6.0.6.1 Dapper) as an X terminal to a 1999 Pentium system running Gutsy 7.10. So I'm probably not a typical example. But right now it's working for me.

---

### Post by jbeckford1 on 2007-12-21
> **lunalot said:**
> Success!

I disabled usplash after reading the recommendation here: [http://ubuntuforums.org/showthread.php?t=289302#2](http://ubuntuforums.org/showthread.php?t=289302#2)

However, that didn't work as described there.  I had to use the Live CD (with 'live-nosplash break=top single', at the initramfs prompt issued 'modprobe ide_core; exit') and then mount my root filesystem (on /mnt).  **Then I edited /mnt/etc/yaboot.conf, and then ran '/mnt/usr/sbin/ybin -C /mnt/etc/yaboot.conf'.** (This didn't work when chroot'd because the chroot environment doesn't have the /dev node for the HFS boot device and thus can't install the loader.)  After that I was able to reboot successfully without any futzing with kernel options or modules.

Now onto other problems I'm having in my installation.

Thanks to everyone's help here.

Just posting this off the top of my head from last night...  After reading through this and MANY posts, I got Gutsy installed on my G3 iBook 700Mhz... After using the ide_core method, when I boot, displayed would be "loading", then the screen would lock and varying lines of color appeared until they became blended...  I used Lunalot method and was able to boot the system to the desktop but kept thinking "there must be some config file for splash that is messed up or missing"... Some searching brought up [/etc/usplash.conf], most errors had the values set too high... Checking mine I found it had NO VALUES... Since I did not find a reference to it in this or any PPC topic, I figured I would post an *easier* fix for the "black screen of death" that will still leave you with a SPLASH... All you need to do is change/add in your values and you *should* now get a splash and boot... For example my iBook is 1024x768 so I would use... ```
# Usplash configuration file
xres=1024
yres=768
```
then run the following to update the configuration...
```
sudo update-usplash-theme usplash-theme-ubuntu
```
One note though, is that I did do this while I was downloading updates for Gutsy after booting w/ Lunalot's method... 
On another note if the scrolling boot text is appealing to you, just comment out (instead of delete) the append line in yaboot.conf, mine looked like ```
##append="quiet splash"
``` Then to go back uncomment the line and do the whole ybin -C yaboot shabang... 
Good luck to you guys... 
Unfortunately, I continued to have errors w/ "the gnome settings Daemon" restarting, losing the theme, and neither the GUI sound or network configurations programs would open... At the moment I am attempting a CLI (command line interface) install, and will try to build an Openbox based DE... Aside from having to learn some XML, my main concern is that glxgears is performing at 71fps, vs 700-900fps on Feisty w/ a full Gnome install... Grrrrrr...!!

-------------------------------------------------------------------------------------

Well attempting yet another install, I realized that you can kill two birds with one stone... Once you have booted to the live environment using the modprobe ide_core method and have finished the installation, just select Continue using live CD...

Then open a terminal and run fdisk -l, then mount the / partition on the HDD to /mnt... Chroot into /mnt, run the ide_core, ide_disk changes in initramfs-tools/modules file, then run update-initramfs -u... Afterwards, make the changes to your /etc/usplash.conf file and run the update-usplash string, it will take a little while to complete and once done, just reboot and you go right to the desktop of your new installation...

---

### Post by codeman38 on 2007-12-26
> **vijaym said:**
> I had the same problem installing ubuntu 7.10. but it was erratic. did not have the message all the time. 

tried a few times and it avoided that problem sometimes.

if you really want to try i would suggest that you say
live-nosplash-powerpc break=top video=ofonly

on the next screen say

modprobe ide_core; exit

I've tried this on my PB G4 1.67GHz, but when I run it with "break=top", I'm unable to type at the BusyBox screen. Keyboard input seems to be completely ignored.

When I *don't* do "break=top", I can type at the BusyBox screen, but doing the modprobe just kicks me back into BusyBox again.

Any suggestions?  Or am I just stuck with Feisty?

---

### Post by mirak63 on 2007-12-29
I had this problem with ide_core module missing in initrd, and since I was upgrading from feisty I could update the initrd from a feisty kernel.

so I guess you could do feisty install and do an upgrade.

this sucks but it would work

i am also wondering why the kernel for ppc still isn't upgraded in the repositories.

---

