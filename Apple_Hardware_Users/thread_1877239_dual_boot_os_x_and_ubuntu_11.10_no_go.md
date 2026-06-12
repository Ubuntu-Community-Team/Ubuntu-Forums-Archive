---
title: "dual boot os x and ubuntu 11.10 no go"
date: 2011-11-07
forum: Apple Hardware Users
---

### Post by Dr. McKay on 2011-11-07
I have a 2.8Ghz Core2duo iMac (24 inch), a ATI Radeon 2600 HD Pro w/256Mb, 4Gb RAM, 320Gb HD and running OS X.6.8.

I have tried to install Ubuntu 11.10 alongside os x using refit. Have partitioned my drive : using disk utility to create 30Gb for linux (free space), rest for os x.
In gparted (using live cd) I created a 2Gb swap partition, leaving about 28Gb for linux (ext4).
Was aware of booting problems, have installed ubuntu and rebooted with live cd, installed gptsync (latest version) but got message that 'disk will not be touched'. 
When booting into linux, I get the message 'missing operating system'. 
Have tried everything, please help. 
Booting into OS X works just fine, thankfully.

---

### Post by Dr. McKay on 2011-11-08
When installing Ubuntu, I noticed there were three options : replace OS X, install ubuntu alongside OS X and manual config.
What happens when you choose "install ubuntu alongside OS X". Does this means Ubuntu 11.10 has the means to automatically create partitions and install a bootloader for both OS'S ? 

Maybe I shouldn't have used rEFIt ?
Does anyone have the same iMac I have running Ubuntu alongside OS X ?  How did you do it ?

---

### Post by Rankun on 2011-11-09
Worked for me. Did you turn on FileVault (that is, the full HDD encryption) in Lion? If you do that, the boot loader doesn't recognize the file system on the OS X partition, and neither does Ubuntu, by the way, so you can't use GRUB to boot into OS X.

What should work, however, is holding down alt when you boot your machine, entering Apple's boot loader. There you should still see your OS X installation, but not your Linux. So basically if you want to boot Ubuntu, do not press alt and boot via GRUB, and when you do want to boot OS X, press alt and boot via Apple's boot loader.
It's a bit of a pain, but it works for me.

You can, of course, just turn off FileVault, then you can add the OS X partition to GRUB and boot from there.

Oh, by the way, I didn't use the "Install Ubuntu alongside OS X" option but used the advanced options to create the partitions myself. That might be a problem if you have the whole thing encrypted as well, because I could imagine that the partition manager might not recognize the encrypted space as a valid partition which it can resize or move. In that case, use BootCamp inside OS X to create a partition first and then use that one to create everything you need for installing Ubuntu. That's what I did.

/boot is /dev/sda1
OS X is on /dev/sda2
Lion's recovery partition is /dev/sda3
Ubuntu is /dev/sda4
And my swap partiton is /dev/sda5

No problems so far. ;)

---

### Post by Dr. McKay on 2011-11-09
Filevault is turned off, and I'm on Snow Leopard. Followed the instructions to the letter, manually creating partitions. I use rEFIt. Even tried to repair partition table with gptsync, but that didn't work. There lies my problem, I believe...

---

### Post by pete04 on 2011-11-09
> **Dr. McKay said:**
> Filevault is turned off, and I'm on Snow Leopard. Followed the instructions to the letter, manually creating partitions. I use rEFIt. Even tried to repair partition table with gptsync, but that didn't work. There lies my problem, I believe...

Just set up a dual boot last week, OSX 6.8 and 11.10. 

Just a question, because it sounds like you did everything else right... when you installed from the CD, you chose install alongside OSX, right? That's what you want to do. The installer will figure out that you want to place 11.10 on your Linux partition. You should get a screen that lets you choose how much space you want to allocate to your file system. If you get there, you should be good. 

Be ready to spend a little time on the install. I've installed Ubuntu on standard PCs and it never took as long as it took my macbook to install. It was almost an hour.

---

### Post by Dr. McKay on 2011-11-09
> **pete04 said:**
> Just set up a dual boot last week, OSX 6.8 and 11.10. 

Just a question, because it sounds like you did everything else right... when you installed from the CD, you chose install alongside OSX, right? That's what you want to do.

Nope, I chose the third option, manual install.  I didn't dare to choose the "alongside" option as I figured the installer was going to mess up my partition.
I followed a guide that said to create everything manually but I guess the version of Ubuntu was an older one. Still, must try again.
I'll wipe the 30Gb clean with diskutility in OS X and start over. See what happens...

---

### Post by pete04 on 2011-11-09
You know, I've never performed a manual install on any machine save an old ibook with a power pc chip.

But that alongside option should do the trick. Ubuntu's installer is a real work of genius.

---

### Post by Rankun on 2011-11-09
On top of that, I can't imagine what could have gone wrong with the manual installation, even if you did follow an outdated guide. The only thing it asks of you is to assign root and boot partitions. I don't think that a wrong partition setup might be the error here ...

What you could try is boot from your installation CD / pen drive again and choose the "Upgrade Ubuntu 11.10 to 11.10" option which should basically equal a system repair. It should redo the boot loader configuration as well. Maybe that helps.
Or, for an even "cleaner" re-installation, choose manual again, format the current root partition and choose it again without doing anything else.

---

### Post by Dr. McKay on 2011-11-10
I'll give another go tonight, if I can find the time. I'll keep you posted...

---

### Post by Dr. McKay on 2011-11-11
> **Rankun said:**
> What you could try is boot from your installation CD / pen drive again and choose the "Upgrade Ubuntu 11.10 to 11.10" option which should basically equal a system repair. It should redo the boot loader configuration as well. Maybe that helps.

Tried exactly that, and it worked !  rEFIt shows two Ubuntu installs but maybe I can live with that (nothings's changed as far as my partitions are concerned, still 2Gb linux swap partition, 28Gb linux OS partition and 290Gb OS X). Thanks for the info !

Right, next question : how do I install Kubuntu on top of Ubuntu so that I can choose between the KDE and Gnome desktop ?  I already have the Kubuntu 11.10 ISO on CD.

---

### Post by pete04 on 2011-11-11
You can grab kubuntu-desktop with synaptic package manager... I don't see it in the software center. You'll need to install synaptic and then just search kubuntu and you'll find the desktop. After that's installed, it should be available to you when you log in with lightdm.

Glad the install worked for you.

---

### Post by Dr. McKay on 2011-11-13
Installed Kubuntu desktop as well. So far so good.

Some annoying little things : I can't update Firefox 7.0.1 to 8.0 as Canonical removed that function. Still, it should auto-update, like in OS X or Win7 ?  Or am I expecting too much ? (same prob with Thunderbird).

Also, in Kubuntu, I cannot install new apps (don't have authority) even though I have admin rights. Seems that's a bug in Kubuntu. Anybody know a fix ?

Still, not too bad. Slight preference for Kubuntu, though. Looks fantastic.

---

### Post by Rankun on 2011-11-13
I have never worked with Kubuntu (not much of a KDE fan, here), so what I say might be just an educated guess rather than the truth, but on Linux, Firefox does not auto-updated like it does on Windows. It updates through the Software Center respectively through apt.
You should be able to update to Fx8 through a different repo as canonical only hosts Fx7 as of now.

$ sudo add-apt-repository ppa:mozillateam/firefox-stable && sudo apt-get update
$ sudo apt-get install firefox

---

