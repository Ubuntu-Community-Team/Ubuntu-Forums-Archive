---
title: "[SOLVED] VMware Server - Not Starting / Installaling XP on Mounted NTFS drive"
date: 2007-08-26
forum: Absolute Beginner Talk
---

### Post by ashishgoel on 2007-08-26
Hi all,

Currently, I'm dual bootin Ubuntu 7.04 and Win XP. - becuase 1.  Novice Linux User ;  2. Few programs which r required are not supported on Linux

After readin and learnin about VMWare Server - i thought to give it a shot. After installing the Server - On tryin to makin a new virtual drive/operatin system (Win XP) - if i choose a directory/location that is on NTFS/Win XP system which is automatically mounted for read/write in Fiesty Fawn - the VMware doesn't load even after it recognizes the mounted drives (after clickin POWER ON - I get only blank screen and again goes back to main console - askin to power on) and hence unable to install a virtua machine.

But if i change the location of a new Virtua Machine to my /home (or any directory on Linux System) - it works perfectly - I'm able to Install windows and work on it.

My Linux System has only 900 MB free (Total Size 5 GB with 750 Swap)- and to Install windows I had to use small xp installation (only 400 MB in size - TinyXP - Beast edition) and keepin the size of Virtua system to 600 MB max, as regular XP cannot be installed.

Problem / Questin 1 :- How Can I install VMware on NTFS drive in Ubuntu ?? (If not possible, then please tell me so that i can drop the Idea - Needed so that I can have regular XP installation as my apps are not supported on TinyXP as needs .Net 2 and other updates.)

Problem/ Question 2 :- I've free 5 GB space on NTFS system and I have Acronis Disk Utility - Is it possible to Increase Ubuntu Disk Space without disturbing the Ubuntu File System and the GRUB loader - as it took me approx 2 hrs to thoroughly update and bring it present condition after fresh Ubuntu 7.04 installation. I read about Gparted - but have apprehensions about disturbing the XP file system then..
I mentioned GRUB also, because when i partiotioned my new Dell Laptop (other machine) in Windows XP with the Acronis Disk Utility - that messed up with the Boot Loader - and then had to completely format and install everythin as the Recovery option also didn't worked owin to boot failure.

Please help.

Thanx alot

---

### Post by anewguy on 2007-08-26
Okay, I normally wouldn't recommend this because there are some inherit risks, but since you have VMWare Server, you can set up the virtual machine to actually be your already installed Windows partition.  I did that for a while but eventually just got rid of Windows, went with Ubuntu, and used VMWare Server to create a larger virtual disk within Linux and loaded Windows and my other "must haves" to there.  That works great as well.  Post back if you'd like information on using your existing partition.:)

---

### Post by RoflCake on 2007-08-26
I would like that info.

EDIT: Actually I would prefer your take on whether the HD method or the virtual disk method performs better...if its the virtual disk I'll just move a few things (its a fresh XP install) over to my FAT32 partition and delete the XP partition.

---

### Post by anewguy on 2007-08-26
To answer one question first as best I can, my VM runs a little slower, but I also have low memory and a so-so processor.  Those with newer/better machines seem to indicate in the posts I have seen that the VM performs just as good as stand alone.  The one thing always worth noting is that if you are a gamer, the posts seem to indicate that the virtual video provided by the virtual machines is not up to most gaming.

So, you want to use your existing partition/installation?  A couple of warnings first:

(1) you can physically mess up your partition
(2) if you plan to run Windows stand alone at some point in time, then using the partition in a virtual machine is probably not your best choice.  Why?   My experience (others may be different) is that Windows wants to be reactivated once you bring it up in the virtual machine.  It will want to do that each time you go to stand alone Windows it will want to do it again, and again when you go back to the virtual machine.  I tried the thing posted previously in this forum about setting up 2 hardware profiles in Windows, but it made no difference for me.  So, if you want to use the physical partition in a virtual machine, you will need to reactivate Windows and then probably never want to boot Windows stand alone again.


Okay, with those warnings, you need to install VMWare Server first.  It is free, as is VirtualBox, and just requires you register to get a key to unlock the software (again free).  The best/easiest instructions for installation I have found are at this site:

[https://help.ubuntu.com/community/VMware/Server]("https://help.ubuntu.com/community/VMware/Server")

For the portions that show command lines you need to be in a terminal window.  To get that, click on "Applications", then scroll down to "Accessories" then over to and click on "Terminal".

When you are going through setting up your virtual machine, you need to direct the disk to your existing installation.  There are many tutorials for that on this forum, so I'll just give you the basics:

- start up VMWare Server via "Applications/System Tools/VMWare Server Console
- select create a new virtual machine and select "custom"
- follow the prompts until you get to the "Select Disk" window.  Click on the Use a Physical Partition button and click next
- On the Select a Physical Disk window, you need to select the disk first.  If you only have 1 disk you can leave it at the default.  You must also click the Use Individual Partitions button and then click next
- For the next screen, I can't tell you now exactly what it says, as I don't have a Windows partition anymore.  The thing you must do is select your Windows boot partition and also the Ubuntu main partition (you don't need to select the swap) then click next.
- Follow the rest of the screens until you are finished
- now for one little step you may need to do before you can boot:

If you don't have a scsi card (I don't in my laptop) you need to make 1 edit to the definition file for the virtual machine.  If you have tried to power on your virtual machine and it just aborts out, try this edit as well.  

type gksudo gedit "/var/lib/vmware-server/Virtual Machines/xxxxx/xxxx.vmx" where xxxx is the version of Windows you selected (such as Windows XP Home Edition).

look for the line that says    scsi0.present = "true"   and change the true to false then save the file and exit.

You should now be able to start your virtual machine.  Once it is started and running you will want to install the VMWare Tools.

Please note that since the system is still set for dual boot, you must click the mouse in the VM window and then select Windows from the grub menu.  If you let it default into your Ubuntu, you will need to shutdown/power off that virtual machine [COLOR="Red"]immediately.[/COLOR]

I think I've included everything.  It's been a while since I set mine up so if you have questions please post back.:)

---

### Post by ashishgoel on 2007-08-27
thanx alot for replyin, but i think my question was different. I can run VMware Server (No probs with the Installation of VMware Server) with the Installation directory of new virtual OS set to be in the linux file system (i.e. /home ~anywhere - /var/lib being default) _only_ but if i select the location to be /media/hd1 (which are mounted drives of Windows system in Ubuntu) - Vmware Server program/console run but when I try to start the Virtual OS (Powerin ON) - it doesn't runs (even if i move the virtual OS files from /var/lib~ to /media/hd1) after the setting the corrected parameters.

Also I read somehere in the forums only that either SAMBA can be used to move files to n fro from Vmware OS Win XP to base Ubuntu or I can make one extra Fat32 partition, which can be recognized by both Ubuntu and native Win XP and Vmware OS.

PS - I'm not askin to touch native Win XP disk from Vitrual Win XP in Ubuntu
     - I've 6 partitions in Windows which are loaded in ubuntu as ~/hd1 - hd6

Also, any idea about increasin ubuntu/linux disk space from windiws??

---

### Post by ashishgoel on 2007-08-27
well i took the plunge - made one 2 GB Fat32 disk in win-xp and it is easily identified by linux and by virtua system....

will use n post moore soon....

Still question remains about increasin the native linux disk space/size

Hopin to get some help.

---

### Post by bryonak on 2007-08-27
I've replied to [this thread]("http://ubuntuforums.org/showthread.php?p=3261598#post3261598"), but it's better to keep it all in one ;)


> **anewguy said:**
>  So, if you want to use the physical partition in a virtual machine, you will need to reactivate Windows and then probably never want to boot Windows stand alone again.

That' my setup right now, and for me it works with 2 different hardware profiles, without having to reactivate on every switch.

@ashishgoel: specifying /dev/hda1 means that you want to run an already configured partition (correct table headers etc), **not** a virtual image file, which is what VMware gives you if you create a new VM... these are two different things, /dev/hda1 is a device interface, not an image file.
You can change the boot order by pressing F2 quickly after powering it on (does it even get that far?), put CD boot above HD boot, insert a Windows CD, restart and check if it recognizes the already installed Windows (it should). Then you should decide if you want to "repair" it, which will make it functional in VMware. Or you can make a new image file on that partition, which means mounting it in Linux in something like /media/yourpartition and creating an a new VM there.

---

### Post by ashishgoel on 2007-08-27
bryonak earlier replied-

First of all, could you give a bit more specific information about your disk layout?
One HDD? How many/how big partitions?
Did you use ntfs-3g to mount the Windows partition? You can check by typing "cat /etc/fstab" into your terminal and look your Window's partition mountpoint, the third column should be "ntfs-3g". If not, here's a short HowTo.

I myself have a 80GB Linux hard disk and another 40GB with Windows, loading the existing Windows partition in VMware. Of course, you should have at the very least 1GB RAM (but rather more, I have 1.5GB) to run a VM efficiently...
I recommend that's what you should do, since it spares you reinstalling all your applications and wrestling with Windows' post-install configuration, plus you need less space since you get virtual and "real boot" windows in one. Just follow this HowTo. I had to do a repair-install in VMware afterwards, but that's because that HDD's MBR was screwed anyway (I just used the drive as storage).

Which version of VMware-server are you using?
I'd suggest you download v1.0.3 here . Also don't forget to install VMware-tools (included in the server), especially for the mouse performance.

As for your first problem...
Because ntfs is quite different from Linux' ext3 filesystem, there might be problems with the permissions. You should check the permissions on your .vmx, .vmdk and the other files in your config folder (you can view/set it in the server's preferences) aswell as on the virtual image itself. Try running VMware as root.
Perhaps adding yourself to the disk group (Users and Groups in Gnome's System->Administration) might help. Gotta admit, I simply don't know whether you can have the virtual image on ntfs, because I've never toyed around with that.

The other one...
GRUB is easily reinstalled via "sudo /sbin/grub-install" from your Ubuntu-install or Live-CD, you just need to backup your menu.lst file, since it's the only relevant configuration file.
I know absolutely nothing about that Acronis thingy, so no help in that case.
Gparted is my partition-editor of choice, epecially the even more powerful Live-CD version (you can download it here). Resizing ntfs should be just fine, I'm not sure about moving the Ubuntu partition afterwards, you might have to delete it and make a bigger one.
For rescuing lost partitions/screwed up boot records, there's an amazing tool called TestDisk (download here)... I have yet to encounter a HDD this program can't save


Besides, have you tried running your apps in wine? (open a terminal, type: sudo aptitude install wine, double-click on your exe's...) You get native performance (almost, startup takes a little bit longer), unfortunately many apps won't work. Still it's preferable to emulating a whole OS, if your programs work...

Oh and.. welcome to the wonderful world of free choice and software!

---

### Post by ashishgoel on 2007-08-27
@brynok
1. I tried WIne - but my apps are not supported because they were developed specifically for Windows (some personal a/c software)

2. Where is menu.lst file?? How and where to backup??

3. Fat32 was painfully slow (VMware workin fine) - so i again went to windows - converted FAT32 to ext3 - a new prob arises - Ubuntu don't mount it automatically - after manually mounting the drive - i'm not able to write on it (though able to use it under gksg natutils - could make a directory / move files but only under it) - so need help on it - i went thru other pages which gives info about chmod - tried but no use - see if u can help
 
4. I don wanna touch native Win XP at the moment - please do tell little explainatory procedure to do that also - as will like to try it later...

---

### Post by ashishgoel on 2007-08-27
I think i've messed up very badly....

What i have done is -
 $ sudo mkdir /media/sda12
$  sudo ... /dev/sda.... /media/sda12
$ sudo chmod.....

Now I'm not able to do any sudo operation - gives me an error of  ' sudo: must be setuid root '    , net not working, not able to get any administration app workin

Help

---

### Post by bryonak on 2007-08-27
You'll find the menu.lst in /boot/grub/
Copy it somewhere else (USB-stick, some safe partition...) and after reinstalling grub just copy it back.
If you want to customize it, [here's]("http://www.howtoforge.com/working_with_the_grub_menu") a point to start with. However if you don't change it there's no point in making a backup, since grub-install creates a default one.

Concerning your third point... maybe I have to clear up things first.
You can either format a partition to whatever format you want, then mount it in a folder in Linux (which you can call something like /media/partitionXY), start VMware and create a new image file in the mount folder. I'd suggest ext3 as format here, since it's Linux' native.
The other option is to specify /dev/hdXY (you have to know the interface to this partition) as HDD in VMware: click on new VM... ok, next... until "Select Disk" and there you choose "Physical Disk" and your /dev/hdX interface. Then you pop in your Windows CD, start the virtual machine, and install Windows directly on this partition, no virtual image files in this case. But then the format must be either fat32 or ntfs, because Windows does not run on ext3 (I strongly recommend ntfs).

The second way is what I have done, except that I made 2 hardware profiles in Windows which allows me to boot it directly (with grub of course ;) ) or from within VMware.

To automatically mount the drive, you have to edit /etc/fstab
Here's the /etc/fstab entry for my Windows Partition:
```
/dev/hda1    /media/WINDOWS    ntfs-3g    defaults,umask=0000    0    0
```
All stuff in there gets mounted at boot, so you have to restart Ubuntu. The syntax is very similar to the mount command.
You have to change /dev/hda1 to your partition, and the /media... to the mount folder you have created (you sure know that the folder must already exist before mounting something to it).
The rest of the line can be taken as is, just make sure you have ntfs-3g installed (in aptitude/synaptic) since it offers the best read/write support for ntfs.

In order to boot 2 hardware profiles, you have to install Windows the **normal way first**, then set the hardware profiles there, then start with VMware... it's all in the tutorial I gave a link to in the other thread.

...
Oh well, all this is in reply to your previous post. Hmm, is your Ubuntu-install by chance on sda12? That'd be quite bad...
But please give as many details as you can, I can't really help you with as little as that. You're still in a fully working system, except not being able to execute sudo? What did you do exactly?
Seems like the sudo tool isn't executed as root...

---

### Post by bryonak on 2007-08-27
Thinking about it.. I'd first check if some files are owned by root.. you do this with ```
ls -la
```
The directories are:
/bin/
/sbin/
/usr/bin/
/usr/sbin/
all the listed files should look like ```
-rwsr-xr-x 1 root root      91508 2006-10-09 13:37 /usr/bin/sudo
```
If you've got another owner than "root", give the following a try... Gnome-pane -> System -> Administration -> Users and Groups... now if you can enter, change the user root's password by hand, open a terminal and type "su". Enter the new password... then ```
chown root filename
```
on all files that aren't owned by root. For whole directories:
```
sudo chown -r root /bin
``` and all the other dirs.

If you can't get into "Users and Groups", reboot and select the "recovery mode" kernel in grub, then type this into a terminal: ```
chmod 4755 /usr/bin/sudo
```
Or try to reboot with your Ubuntu Live-CD, type "su" into the terminal and then the same line as above... (this should work pretty sure)

---

### Post by ashishgoel on 2007-08-27
what i undertand in my system is that sudo is not working - and administration apps r not running/start that requires root/sudo permission.

i searched the forum and got the followin (and run those commands after goin in the recovery mode)

on doin $ ls -l /usr/bin/sudo   -> i'm gettin ->  -rwsr-xr-x 1 ashish ashish  93844 2006-05-17 08:41 /usr/bin/sudo
(ashish is the root on which i orginally installed the system )
then i do
chown ashish:ashish /usr/bin/sudo

then
chmod 4755 /usr/bin/sudo         and restarted

but nothing happened... still on runnin sudo in terminal - i'm gettin error -  "sudo : must be setuid root"
I even ran these commands in regular ubuntu -> terminal - they just execute - gives no error - but nothin changed/happened

Help

---

### Post by schorsch on 2007-08-27
Right at the moment your sudo is setuid ashiash ......
ashiash is not root but a user that can get root permissions via sudo, that is a big difference! The file /usr/bin/sudo has to belong to root:
```
chown root:root /usr/bin/sudo
chmod 4755 /usr/bin/sudo
```
Enter these command in recovery mode again, restart and you should be done.
BTW: On every *nix system the root user is called root .....

---

### Post by bryonak on 2007-08-27
Another user than root owning these files is indeed uncommon on Ubuntu...
Do you remember after which command (or set of commands) you weren't able to execute sudo anymore?
Try assigning them to root, you can revert it later with sudo if it works, or else with the Live-CD or recovery-mode.

By the way, you needn't restart the system for such changes.

---

### Post by ashishgoel on 2007-08-27
> **bryonak said:**
> .....with sudo if it works, or else with the Live-CD or recovery-mode.

By the way, you needn't restart the system for such changes.


then how can i start the console in the recovery mode if i don't reboot??

---

### Post by bryonak on 2007-08-27
Ah, I was referring to chown/chmod... of course your'e right, reboot is needed for recovery mode ;)

how's it going?

---

### Post by ashishgoel on 2007-08-27
thanx BRYONK ans SCHORSCH .....

as i'm not able to connect to net in Ubuntu (gettin - Network tryin to get address - since after that some weird command that messed up with sudo), i've to boot in WinXp to check /reply....

I'll try n post it as soon...

---

### Post by ashishgoel on 2007-08-27
I'm back - what i've done after bootin in recovery mode
1. i ran "$ ls -la" and go the list of files - all were havin ashish:ashish instead of root:root.
 2. So i ran "$ chown root:root 'filename'" for all files
3. i also ran "$ chown -r root /bin"
4. and also then "$ chown root:root /usr/bin/sudo"  and "$ chmod 4755 /usr/bin/sudo"

I reboot back - but nothin much happened/changed.
Still i'm not able to start Adminis Apps.
In terminal when i ran "$ su" -> it ask for password and puttin in the right pass - it gave me an error of Authentication failure - Pass incorrect

In the terminal only, then i ran "sudo -s" and it gave error - " sudo : /etc/sudoers is owned by uid 1000, should be 0"

Help (i think we're near to solve this riddle)

---

### Post by schorsch on 2007-08-27
Did you change every file to belong to the user ashish as the user id 1000 is given to the user that installed the system? If so I would suggest to do a clean install as it will be nearly impossible to recover the right permissions for every file.
Right now you can boot back into recovery mode and do
```
chown root:root /etc/sudoers
chmod 440 /etc/sudoers
```
And please check before if you are in the group "admin" by typing the command "id ashish"
If not you should add your user to this group when running recovery mode via
```
usermod -aG admin ashish
``` .... this way you will have on recovery boot less ...

---

### Post by bryonak on 2007-08-27
[I]edit: yup, first do everything schorsch said ;)
additionally, you can chmod/chown whole directories with all files and subfolders in them with the -R or --recursive switch.. "sudo chown -R root /bin"[/I]

For some reason, your chown/chmod didn't really work... uid 0 is root, uid 1000 is the first human user on the system, in your case "ashish".

This seems pretty strange.. did you check with "ls -la" if your chown/chmod really took effect, right after execution?
If it doesn't work in recovery mode, you might want to try the whole thing with the Live-CD, (just don't forget to type everything with sudo, or better login to the root account with "su", when you do things with the Live-CD)

Just for information, the password for "su" is not the same as for "sudo"... its the password for the root account, not the "execute as root" password (=sudo). On Ubuntu, it's defaulted to a random string since the root account shouldn't be used (only sudo), but you can change it in "Users and Groups".

---

### Post by schorsch on 2007-08-27
> **bryonak said:**
> For some reason, your chown/chmod didn't really work... uid 0 is root, uid 1000 is the first human user on the system, in your case "ashish".

... we have reached the file /etc/sudoers now ....

---

### Post by anewguy on 2007-08-27
> **bryonak said:**
> I've replied to [this thread]("http://ubuntuforums.org/showthread.php?p=3261598#post3261598"), but it's better to keep it all in one ;)




That' my setup right now, and for me it works with 2 different hardware profiles, without having to reactivate on every switch.

Interesting, as I have never been able to make that work no matter how many times I reinstalled Windows and Linux to get a clean start.  The separate profile stuff just never had worked for me.:)

---

### Post by ashishgoel on 2007-08-27
@bryonak  - yes i've checked by ls -la command - and all listed files were now root:root

@schorsch - i'll do as u say - and post it then (re-installing is the last option for me - when everyone fails - that use to happen with Win XP)

---

### Post by bryonak on 2007-08-27
Complete reinstall? C'mon, we're better than that ;)
You probably wan't to chown all files/folders except home to root (**not** root:root, just the user, not the group), so check the other system folders later... you can ignore /tmp/ and the like.

@anewguy:It depends on your hardware and Windows state...
If you have a preinstalled version of Windows, try adding the line```
SMBIOS.reflectHost = TRUE
``` to your .vmx file. Come to think of it, add in every case, it might be magic ;)
I don't use SP2, but most of the security patches, so perhaps this is another factor. Also I've read that on Dell's notebooks you can't bypass reactivation when switching between VMware and direct boot. (Not sure about this since I don't own a Dell, but I remember reading it more than once)

---

### Post by ashishgoel on 2007-08-27
I'm back again... i did what was told by schorsch - get back the sudo command and was able to run all the adminis apps as usual...  but the INTERNET probs have not resolved - the Connection Manager in the Task Bar - continues to try to connect (round thing goes on n on) and after doin some tweaks (like disable wired connection and then enable it etc) it do get connected but i'm not able to surf net - on checkin the connection status - only Hardware address is there ; rest IP address, subnet, DNS etc all have 0.0.0.0 in front of it..

Any suggestions ??

---

### Post by ashishgoel on 2007-08-27
also, as i'm dual bootin XP installed first then Ubuntu - which would be best and easiest method to re-install ubuntu without affectin the Win XP??

---

### Post by ashishgoel on 2007-08-27
also, my original question - I made a new ext3 partition in windows using Acronis Disk Manager - i boot up ubuntu - i can mount that new ext3 partition (manually) but not able to write/edit on it - hw can i do that??

PS - usin gtkp nautils - i can make new directory in it / in short -> can write/edit on it...

---

### Post by bryonak on 2007-08-27
It's either because some system files still belong to ashish or because some files that should be owned by special users/groups (dialout, netdev etc) are now owned by root...

Reinstalling with the Ubuntu Live-CD should be safe if your partitions are already defined (well it gets more tricky if you want the Windows bootloader instead of grub, but not a big problem though)

As I've already stated, I don't know a thing about Acronis... but it might be that it's ext3 isn't completely flawless. Did you try with gparted? ("sudo gparted")

---

### Post by ashishgoel on 2007-08-27
@bryonak  - if i reinstall ubuntu - i need to increase the size of the partition

- at the moment i'm dual bootin with the GRUB - no probs with it at all

- jus consider - i have a new ext3 drive/disk/partition that is being mounted only for read only purpose and wanna it to be writable too...

Please suggest

---

### Post by bryonak on 2007-08-27
The problem with moving/resizing partitions is that you must not use them, i.e. not even have them mounted.
The best way to ensure this is by using a partition-editor Live-CD, because the HDD is not booted, so I hope you have a CD-writer. If you choose this way, I'd recommend downloading [gparted Live-CD]("http://gparted.sourceforge.net/livecd.php"), you can do almost everything with it. Acronis might be ok too, but do not use PartitionMagic, since this tool doesn't handle Linux fileformats correctly.

If you can't burn a CD, give it a try with Acronis, be sure not to use (running programs, etc) any of the partitions you touch, and be prepared to completely reinstall the stuff on the affected partitions (backups are always a good idea). You probably should join your existing Ubuntu partition with the new one, but that's up to you. Good luck!

As for the read-only ext3... check if you have mounted it as read-only (also look at /etc/fstab and /etc/mtab, do not edit mtab yourself!). And there's still the possibility that Acronis didn't get it right.

One more thing: if you resize the Windows main partition, it'll probably complain because keeps track of the partition size. You can resolve this by booting the Windows CD and choosing to install Windows, then it checks whether there is a copy already installed and offers you to repair it. This keeps all your settings and files intact.

---

### Post by ashishgoel on 2007-08-27
thanx for replyin....

i searched forum for my net problem - but couldn't get much...

Thankxxx alot...

---

### Post by ashishgoel on 2007-08-27
Update - 
I used Acronis to resize the Ubuntu Disk - and it does that beautifully - no probs with it or with native XP or Ubuntu file system

I even tried to chown root:ashish to all files - but no effect on net workin..

Hence - i've planned to re-install Ubuntu on the resized disk

---

### Post by ashishgoel on 2007-08-28
Update - 
I reinstalled Ubuntu n really amazed by power of VMware - Win Xp is runnin seemlessly..

I think - in short span of time - i'll definately switch-over completely to Ubuntu...

---

### Post by bryonak on 2007-08-29
Nice to hear you like it...

By the way, if you want to try running your Windows applications within Ubuntu (still virtualized by VMware, but the program shows on your Ubuntu desktop, not within the Windows environment):  [here's a tutorial]("http://www.venturecake.com/10-minutes-to-run-every-windows-app-seamlessly-on-your-ubuntu-desktop/")
For me it **did not work**, because I couldn't connect from Ubuntu to Windows via the local network, don't know why... but many others succeeded.

---

### Post by ashishgoel on 2007-08-29
Thanx alot Bryonak.....

i really wanna run Joost in ubuntu - no solution for their latest version - and old version (people were usin it with WINE) doesn't run anymore...

---

### Post by ashishgoel on 2007-08-29
i went thru the tute - and it worked perfectly well - but nothin much - 'cause its jus bringing the screen from VMware - nothin else - its better in VMware definately - if u're unable to do so - donn bother...

also - for the above - i believe u need a SAMBA setup....

---

### Post by bryonak on 2007-08-29
You're welcome!

Since I use VMware only now and then, I don't mind the above tutorial not working for me. And if you say so, it seems like I'm not missing much anyway.

Concerning Joost (which I haven't tried yet), you might want to open a new thread ;)

---

### Post by Otpadnik on 2008-02-04
Hi, I think I hove lost it.
I still don't understand how to use image of virtual XP that is on an NTFS partition??
My problem is just the same as the one stated at the beginning of this thread, same image on Desktop is working, but on NTFS partition isn't...

If the solution (as I've understood) is to reformat partioin to Fat32, then this should be more like workaround?

Thanks,
Otpadnik

---

### Post by ashishgoel on 2008-02-05
dear, VMWARE doesn't able to read NTFS.... so the image should either be on FAT32 or linux partition.....

i'll prefer to have image on linux partition as image on fat32 causes very slow runnin of winxp....

---

### Post by Otpadnik on 2008-02-06
Hm... If I'm not completly mistaken, VMWare as any other application reads mounted NTFS partioins through Gutsy's API for accessing files, it would be really dumb if every application would have to know how to acces files phisicially stored on disc...
So if host OS can access partioin so should application, right?

Therefore, I belive that problem isn't with VMware itself, but more wit configuration of host operationg sistem, in this case Gutsy, and the strange thing is that host can access disc, and vmware cannot.

And furthermore, host can write on that partioin, so application should also be able to do this, and because of this I don't understand where is the problem, and how it can be solved?

---

