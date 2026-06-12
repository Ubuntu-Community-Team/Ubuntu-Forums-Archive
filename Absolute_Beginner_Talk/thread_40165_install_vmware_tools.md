---
title: "install vmware tools"
date: 2005-06-08
forum: Absolute Beginner Talk
---

### Post by YokQ on 2005-06-08
i use vmware workstation 5 and install ubuntu inside..
but then the vmware said that i need to install vmware tools..
i click on the button to install vmware tools, but nothing happened..
what should i do then..
thanks..

---

### Post by Lunde on 2005-06-08
[QUOTE=YokQ]i use vmware workstation 5 and install ubuntu inside..
but then the vmware said that i need to install vmware tools..
i click on the button to install vmware tools, but nothing happened..
what should i do then..
thanks..[/QUOTE]

This is a cut and paste:
You wont see the file untill you click on install VMware tools, you should be able to see the instructions on how to install. The tools is not a seprate download

VMware Tools for Linux Guests

1. Power on the virtual machine.
2. After the guest operating system has started, prepare your virtual machine to install VMware Tools.

Choose VM > Install VMware Tools.

The remaining steps take place inside the virtual machine.

3. Be sure the guest operating system is running in text mode. You cannot install VMware Tools from a terminal in an X window session.

Some recent distributions of Linux are configured to run the X server when they boot and do not provide an easy way to stop the X server. However, you can switch to a different workspace that is still in text mode and install VMware Tools from that workspace.

To switch between Linux workspaces in a virtual machine, press Ctrl-Alt-Space, release Space without releasing Ctrl and Alt, then press the function key for the workspace you want to use — for example, F2. If you change your hot key combination to something other than Ctrl-Alt, use that new combination with Space and the function key.
4. As root (su -), mount the VMware Tools virtual CD-ROM image, change to a working directory (for example, /tmp), uncompress the installer, then unmount the CD-ROM image.

Note: You do not use an actual CD-ROM to install VMware Tools, nor do you need to download the CD-ROM image or burn a physical CD-ROM of this image file. The VMware Workstation software contains an ISO image that looks like a CD-ROM to your guest operating system. This image contains all the files needed to install VMware Tools in your guest operating system.

Note: Some Linux distributions use different device names or organize the / dev directory differently. If your CD-ROM drive is not /dev/cdrom or if the mount point for a CD-ROM is not /mnt/cdrom, modify the following commands to reflect the conventions used by your distribution.

mount /dev/cdrom /mnt/cdrom
cd /tmp
tar zxf /mnt/cdrom/vmware-linux-tools.tar.gz
umount /mnt/cdrom
5. Run the VMware Tools installer.

cd vmware-tools-distrib
./vmware-install.pl

Respond to the questions the installer displays on the screen. Be sure to respond yes when the installer offers to run the configuration program.
6. Log out of the root account.

exit
7. Start X and your graphical environment.
8. In an X terminal, launch the VMware Tools background application.

vmware-toolbox &

Note: You may run VMware Tools as root or as a normal user. To shrink virtual disks, you must run VMware Tools as root (su -). 


Note: 
*mout the cdrom to /cdrom not /mnt/cdrom
*the filename of the packet is different, cd to the mounted drive and so ls -al to see the packet name

Just edit this, did it myself now and sorry for giving you a bit incomplete information earlier.

---

### Post by mattisking on 2005-07-06
I'm really stuck. Today I installed Breezy "Colony 2" under VMWare Workstation 5. Actually, everything is running fine so I'm not sure why I NEED to get VMWare tools running.... but I do. 

There's so many threads on here about this... but none are helping me right now. Please, someone help. Ok, so I've cut out of gdm and am running without X. When I setup this VM I chose "Other Linux 2.6.x kernel". I list a floppy drive, CD Drive, and "filesystem" under "Computer" when inside GNome. I go to "VM" menu item and say "Install VMWare Tools". It gives me the "are you sure" warning and I say yes. Then I get nothing... as I would expect.

However, after this point, the directions, nor any derivative I've tried for "mounting" the "cd" for retrieving the tar file work. No matter what I put: "sudo mount /dev/cdrom /mnt/cdrom" or "sudo mount /cdrom /mnt/cdrom" or "sudo mount /dev/cdrom /cdrom"... etc. work. In every case I get this: "mount: you must specify the filesystem type". Nothing else seems to do a thing. I will note that the real CDRom drive appears after a default Breezy install to exist at either /cdrom, /media/cdrom, or /media/cdrom0. Trying all these doesn't help either. I'm a bit lost at this point. Help?

---

### Post by Lunde on 2005-07-06
[QUOTE=mattisking]I'm really stuck. Today I installed Breezy "Colony 2" under VMWare Workstation 5. Actually, everything is running fine so I'm not sure why I NEED to get VMWare tools running.... but I do. 

There's so many threads on here about this... but none are helping me right now. Please, someone help. Ok, so I've cut out of gdm and am running without X. When I setup this VM I chose "Other Linux 2.6.x kernel". I list a floppy drive, CD Drive, and "filesystem" under "Computer" when inside GNome. I go to "VM" menu item and say "Install VMWare Tools". It gives me the "are you sure" warning and I say yes. Then I get nothing... as I would expect.

However, after this point, the directions, nor any derivative I've tried for "mounting" the "cd" for retrieving the tar file work. No matter what I put: "sudo mount /dev/cdrom /mnt/cdrom" or "sudo mount /cdrom /mnt/cdrom" or "sudo mount /dev/cdrom /cdrom"... etc. work. In every case I get this: "mount: you must specify the filesystem type". Nothing else seems to do a thing. I will note that the real CDRom drive appears after a default Breezy install to exist at either /cdrom, /media/cdrom, or /media/cdrom0. Trying all these doesn't help either. I'm a bit lost at this point. Help?[/QUOTE]
 1) You do need the VMware tools to run your screen configuration correct.

2) When you press Install VMware tools in the VMware menu you need to be logged out of gnome, nothing will happen, the VMware tools image will take over your cdrom, so check the content of your /cdrom first, if it's nothing there, mount it with:

$ sudo mkdir /mnt/cdrom
$ sudo mount /dev/cdrom /mnt/cdrom

I dont know about Breezy, but you can also try

$ sudo mount /dev/hdc /mnt/cdrom

---

### Post by mattisking on 2005-07-07
Hmmm. It still says "mount: you must specify the filesystem type"

---

### Post by Lunde on 2005-07-07
[QUOTE=mattisking]Hmmm. It still says "mount: you must specify the filesystem type"[/QUOTE]
 Strange.. I did just teh same with kubuntu Hoary as guest with no problems. 

Possible solution:
OK. I've never done this, but I did some research. The tools I belive is located in the installer:
open the **VMware-workstation-5.0.0-13124.tar.gz **in Archive Manager. Inside is a file named **linux.iso**, this is also possible to open in archive manager and inside there agian the file you want is **vmwareto.tgz**.

Share a folder in VMware and mount this in the guest. Or, try to mount the iinux.iso as your cdrom.

Hope this helped

---

### Post by Lunde on 2005-07-07
[QUOTE=Lunde]Strange.. I did just teh same with kubuntu Hoary as guest with no problems. 

Possible solution:
OK. I've never done this, but I did some research. The tools I belive is located in the installer:
open the **VMware-workstation-5.0.0-13124.tar.gz **in Archive Manager. Inside is a file named **linux.iso**, this is also possible to open in archive manager and inside there agian the file you want is **vmwareto.tgz**.

Share a folder in VMware and mount this in the guest. Or, try to mount the iinux.iso as your cdrom.

Hope this helped[/QUOTE]
 Sorry wait, I might be wrong...

---

### Post by Lunde on 2005-07-07
[QUOTE=Lunde]Sorry wait, I might be wrong...[/QUOTE]
 Looks like I'm right afterall... when you extract the vmwareto.tgz I get the installer files for vmware tools for linux.

Again.. hope this helped

---

### Post by Lunde on 2005-07-07
[QUOTE=Lunde]Looks like I'm right afterall... when you extract the vmwareto.tgz I get the installer files for vmware tools for linux.

Again.. hope this helped[/QUOTE]
 and a simpler way to get it.. it's located under
**/usr/lib/vmware/isoimages**

---

### Post by Virtues of Evil on 2005-07-08
Sorry for the slight thread hijack but I'm having some trouble installing VMWare Tools. I'm currently at the step where it basically does some stuff automagically after you hit enter but at one point it stops cause it wants to create some hgfs directory but it can't. I tried to create it myself but it said it was read only.

[img]http://img205.imageshack.us/img205/6154/vmwareproblem0up.jpg[/img]

Any help is appreciated and sorry if I should have created another thread.

---

### Post by Lunde on 2005-07-08
[I]"Sorry for the slight thread hijack but I'm having some trouble installing VMWare Tools"
[/I] 
Not at all, if you have a question regarding the subject, just ask. A tread is for everybody in the forum and it's best to collect the questions regarding the same subject in one place so it's easy to find for others.

Sounds strange.. Unable to create a directory under **/mnt** as root, unless it's already there. try to 
**$ umount /mnt/hgfs**
and run the **/usr/bin/vmware-config-tools.pl** again

---

### Post by Virtues of Evil on 2005-07-08
"bash: $: command not found"

 ](*,)

---

### Post by Lunde on 2005-07-09
[QUOTE=Virtues of Evil]"bash: $: command not found"

 ](*,)[/QUOTE]
 the **umount** command is not found?

---

### Post by Virtues of Evil on 2005-07-09
[QUOTE=Lunde]the **umount** command is not found?[/QUOTE]
 I think the "$" was not found. Not sure. I don't even know what $ does  :-| 

[img]http://img47.imageshack.us/img47/2893/vmwareproblem29gp.jpg[/img]

---

### Post by Lunde on 2005-07-09
[QUOTE=Virtues of Evil]I think the "$" was not found. Not sure. I don't even know what $ does  :-| 

[img]http://img47.imageshack.us/img47/2893/vmwareproblem29gp.jpg[/img][/QUOTE]
 Sorry, you have to type the command without the $. The $ is just a sign to type the command in the terminal window.

---

### Post by Virtues of Evil on 2005-07-09
[QUOTE=Lunde]Sorry, you have to type the command without the $. The $ is just a sign to type the command in the terminal window.[/QUOTE]
 Now it says the umount command is not found.

---

### Post by Lunde on 2005-07-09
[QUOTE=Virtues of Evil]Now it says the umount command is not found.[/QUOTE]
 Very strange if you don't have the mount / umount command installed, but try:
$ sudo apt-get install mount

you have to run this command as root, or use the sudo like:
$ sudo umount /mnt/hgfs

Again without the $ :-)

---

### Post by Virtues of Evil on 2005-07-09
[QUOTE=Lunde]Very strange if you don't have the mount / umount command installed, but try:
$ sudo apt-get install mount

you have to run this command as root, or use the sudo like:
$ sudo umount /mnt/hgfs

Again without the $ :-)[/QUOTE]
 It says it's already at the newest version. 

Have other people installed VMware Tools sucessfully on Ubuntu?

---

### Post by Lunde on 2005-07-09
[QUOTE=Virtues of Evil]It says it's already at the newest version. 

Have other people installed VMware Tools sucessfully on Ubuntu?[/QUOTE]
 Yes me.. without any problems. In Hoary 5.04 tho.

If you do a full reboot, the /mnt/hgfs should be removed. Then try again to run the /usr/bin/vmware-config-tools.pl again

---

### Post by Virtues of Evil on 2005-07-09
[QUOTE=Lunde]In Hoary 5.04 tho.[/QUOTE]
I am in Hoary 5.04  :?

Ok. Got pass that small hurdle. Now it says: 

[img]http://img193.imageshack.us/img193/7052/vmwareproblem34wu.jpg[/img]

---

### Post by Lunde on 2005-07-09
[QUOTE=Virtues of Evil]I am in Hoary 5.04  :?

Ok. Got pass that small hurdle. Now it says: 

[img]http://img193.imageshack.us/img193/7052/vmwareproblem34wu.jpg[/img][/QUOTE]
 Just do a: 
$ sudo apt-get install gcc
then start again

You may get another package missing, I don't remember which it is

---

### Post by Virtues of Evil on 2005-07-09
[QUOTE=Lunde]Just do a: 
$ sudo apt-get install gcc
then start again

You may get another package missing, I don't remember which it is[/QUOTE]
 [img]http://img26.imageshack.us/img26/9907/vmwareproblem43cf.jpg[/img]

I'm guessing I have to get those headers thingy? BTW, how do I exit the questions?

---

### Post by Lunde on 2005-07-09
[QUOTE=Virtues of Evil][img]http://img26.imageshack.us/img26/9907/vmwareproblem43cf.jpg[/img]

I'm guessing I have to get those headers thingy? BTW, how do I exit the questions?[/QUOTE]
 You can exit by:
Ctrl+c
Do you know how to install the headers?

---

### Post by Virtues of Evil on 2005-07-09
I had installed it before with that Synaptic program but that was in another snapshot (I reverted to where I'm currently at). Is it complicated from the command line?

---

### Post by Lunde on 2005-07-09
[QUOTE=Lunde]You can exit by:
Ctrl+c
Do you know how to install the headers?[/QUOTE]
 the command is:
$ sudo apt-get install linux-headers-`uname -r`

then you may have to type in /usr/src/linux-headers-2.6.10-5-XXX (Where XXX is the ex: 386, 686 or what fits your kernel headers)
when that same question comes up.

---

### Post by Virtues of Evil on 2005-07-09
[img]http://img286.imageshack.us/img286/3091/vmwareproblem57ky.jpg[/img]

Do I have to do anything else? How do I restart the X session?

---

### Post by Virtues of Evil on 2005-07-09
nm. Found it. 

Restarted and it worked perfectly. Thanks a lot dude. Know of any essentials things I should also install?

---

### Post by Lunde on 2005-07-10
[QUOTE=Virtues of Evil]nm. Found it. 

Restarted and it worked perfectly. Thanks a lot dude. Know of any essentials things I should also install?[/QUOTE]
 Glad it worked out for you.

Other things to install... Check out these pages:
Index of Howtos by **RastaMahata**
[http://www.ubuntuforums.org/showthread.php?t=31094](http://www.ubuntuforums.org/showthread.php?t=31094)

Unofficial Ubuntu 5.04 Starter Guide by **Chua Wen Kiat**
[http://www.ubuntuguide.org/](http://www.ubuntuguide.org/)

---

### Post by tweed on 2005-07-18
Fantasic info. Though, could anyone help me get a standard install of 5.04 into text mode. Relentless newbie though I can't figure it out at all.

Many thanks

tweed

---

### Post by Lunde on 2005-07-18
[QUOTE=tweed]Fantasic info. Though, could anyone help me get a standard install of 5.04 into text mode. Relentless newbie though I can't figure it out at all.

Many thanks

tweed[/QUOTE]
 At the Gnome login, press:
**Ctrl+Alt+F1**
(or F2, F3, F4, F5 or F6. ...F7 will take you back to Gnome login)

---

### Post by tweed on 2005-07-18
Amazingly cool of you Lunde.... i'll give it a go.
um, that'll be touch and go if i know what I know.

Becoming even slightly expert often requires a LOT of mis-takes.
Happily!


I'll be back!


tweed

---

### Post by Lunde on 2005-07-18
[QUOTE=tweed]Amazingly cool of you Lunde.... i'll give it a go.
um, that'll be touch and go if i know what I know.

Becoming even slightly expert often requires a LOT of mis-takes.
Happily!


I'll be back!


tweed[/QUOTE]
 If you have problems with this, check this out:
[http://www.faqts.com/knowledge_base/view.phtml/aid/26404/fid/107](http://www.faqts.com/knowledge_base/view.phtml/aid/26404/fid/107)

Ctrl+Alt is in use by VMware, I can't test this now because I only run Windows in VMware but I think it should work ok. The VMware command is on key-up, not key-down.

---

### Post by raardvark on 2005-07-27
I've just installed Kubuntu in VMWare on Windows. I was having the same problem with it not finding the headers.

I did "sudo apt-get install linux-headers-2.6.10-5-686" and that seemed to install fine, but when I try to install VMware Tools, it still says that it can't find the headers.

Do they install to a different directory to the one it is looking for or have I installed them wrong?

---

### Post by Lunde on 2005-07-27
[QUOTE=raardvark]I've just installed Kubuntu in VMWare on Windows. I was having the same problem with it not finding the headers.

I did "sudo apt-get install linux-headers-2.6.10-5-686" and that seemed to install fine, but when I try to install VMware Tools, it still says that it can't find the headers.

Do they install to a different directory to the one it is looking for or have I installed them wrong?[/QUOTE]
 Can type in terminal:
**uname -a**
and post the output here

---

### Post by raardvark on 2005-07-27
Thanks Lunde, did the uname and figured out what the problem was (used 686 instead of 386)

All working now :D

---

### Post by Lunde on 2005-07-27
[QUOTE=raardvark]Thanks Lunde, did the uname and figured out what the problem was (used 686 instead of 386)

All working now :D[/QUOTE]
 Glad to hear that.

---

### Post by mattisking on 2005-08-15
The latest Breezy seems to clear up most of my earlier problems. For myself, I took a bit of a different, more visual approach. I chose Install VMWare Tools while still inside GNOME (still in X). It popped up a nice CD-ROM icon on my desktop and opened it. I copied the *.gz file to /tmp, "Ejected the new CD-ROM", and used <Ctrl><F5> to bail out of X in another screen or whatever. I then called "sudo killall gdm" to cleanup X. Then I more or less followed the instructions.

It wanted to build against my headers but the right headers for my kernel don't seem to be available... and yet it seems to be working just fine.

---

### Post by peaz on 2005-08-21
Hi guys... a total Linux NooB here :D

Anyways. i've installed Ubuntu on VMWare 5.0 and everything works fine. But when I tried to install the VMWare tools... i absolutely have no clue how to do it. I went as far as to extract the tar.gz package to a local directory and tried running the .pl script in the root terminal. but it didn't work. I even tried to phyton and execute the script but there was errors. Hmm just wonderig what I did wrong. anyways, I'll go back home from work later today and grab a screenshot and post here for futher help. Hope you guys bare with this noob here :)

---

### Post by mattisking on 2005-08-24
[QUOTE=peaz]Hi guys... a total Linux NooB here :D

Anyways. i've installed Ubuntu on VMWare 5.0 and everything works fine. But when I tried to install the VMWare tools... i absolutely have no clue how to do it. I went as far as to extract the tar.gz package to a local directory and tried running the .pl script in the root terminal. but it didn't work. I even tried to phyton and execute the script but there was errors. Hmm just wonderig what I did wrong. anyways, I'll go back home from work later today and grab a screenshot and post here for futher help. Hope you guys bare with this noob here :)[/QUOTE]
 peaz, did you look at my post right above yours? Do you understand that you need to be out of X (Gnome, basically) when you run the script?

---

### Post by psypher on 2005-09-22
[QUOTE=mattisking]No matter what I put: "sudo mount /dev/cdrom /mnt/cdrom" or "sudo mount /cdrom /mnt/cdrom" or "sudo mount /dev/cdrom /cdrom"... etc. work. In every case I get this: "mount: you must specify the filesystem type". [/QUOTE]

maybe it's cos /mnt/cdrom doesn't exist, it's /media/cdrom or /media/cdrom0 etc.... ;-)

---

