---
title: "boot loader screwed with Fedora"
date: 2009-04-15
forum: Apple Hardware Users
---

### Post by bbarabas on 2009-04-15
Hi,
I have an iBook G4 (not Intel-based). 
So far I used Ubuntu 8.04 on my Mac laptop. I wanted to install Fedora using the partitioning option by which I created a smaller, new partition on the free space (this worked fine when I installed Fedora on a PC, along with XP). However, after reboot I could not access Ubuntu any more, it looks like the Ubuntu partition disappeared completely. At booting there is a list similar to the one that started when I booted Ubuntu, but when I press L only Fedora boots. How can I get back Ubuntu and my /home directory? 
I never had such problems with Ubuntu, please give me the steps as detailed as possible. I have the Ubuntu install disk and I am willing to delete Fedora if necessary. Thanks a lot.

---

### Post by ajgreeny on 2009-04-15
No need to delete anything I hope, but you will need to either edit the fedora menu.lst file or reinstall ubuntu grub and edit that to include fedora.

If I were in the same situation, I would reinstall ubuntu's grub and edit that, but only because I prefer to use grub from ubuntu and understand it better.  In fact I have only ever looked at fedora for a few days and could not get to grips with it so got rid fairly quickly.

Anyway, boot into the ubuntu live CD
open a terminal and run :
    ```
sudo grub
```This gets you to a simple grub command line.  Then:
    ```
find /boot/grub/stage1
```This will tell you where your /boot/grub/stage1 is which is needed to boot ubuntu. If you have more than one linux install you may get more than one answer here.  Use the one from which you want to use grub, ie ubuntu (so you will need to know what partition name it is on).  Replace the question marks in the following command with your chosen output of the this last command :
    ```
root (hd?,?)
```
[like : root (hd0,1) ,probably, or the grub equivalent of sda2, likely if you also have windows and were dual booting with that],  then:
    ```
setup (hd0)
```
This is where your windows partition MBR, or grub normally is, but if you want grub on another disk, use hd1, etc as appropriate. It's much easier to use the windows MBR and then just change the default boot system later if others in the family demand windows boots by default.
Then:
    ```
quit
```
Finally reboot, and hopefully you will now have a working ubuntu grub bootloader.

Now you will have to add fedora's grub entry to the ubuntu grub menu.lst, and that may be where I get out of my depth, as I can't remember where fedora keeps its menu.lst file (/boot/grub?), but I'm sure you will be able to find it.  Alternatively, while you can boot into fedora from its own grub, make a copy of the grub stanza from its own menu.lst file and then when you have ubuntu up and running add that to the ubuntu grub menu.lst file.

---

### Post by bbarabas on 2009-04-15
> **ajgreeny said:**
> 
This is where your windows partition MBR, or grub normally is, but if you want grub on another disk, use hd1, etc as appropriate. It's much easier to use the windows MBR and then just change the default boot system later if others in the family demand windows boots by default.


I have no Windows on my computer, that was another test, before I installed Fedora on the iBook. So the situation right now is: I had Ubuntu 8.04 and tried to install Fedora so that Ubuntu remains on the computer too, and I can go back to Ubuntu if I am not satisfied with Fedora. This is when things went wrong and now I can only boot Fedora.

---

### Post by tiresia on 2009-04-15
Since an iBook g4 is a PowerPC, the Linux Bootloader is not Grub but Yaboot.
Unfortunately, according at least to my experience, Anaconda (the Fedora Installer) installes uncorrectly Yaboot (it fails often to detects a MacOSX partition and just ignore other GNU/Linux Systems). Debian (and Ubuntu) Installer do this job very good.

But this does not mean that you need to delete Fedora. The easy way is to restart the computer from the Ubuntu alternate Installer and boot in rescue-mode. You can rescue Ubuntu and generate a correct /etc/yaboot.conf file, that detects correctly also Fedora. For more info about multibooting you can have a look to these links 
[http://ubuntuforums.org/showthread.php?t=994882](http://ubuntuforums.org/showthread.php?t=994882)
A similar situation
[http://www.ppclinux.info/boards/5/topics/show/509#message-552](http://www.ppclinux.info/boards/5/topics/show/509#message-552)

---

### Post by ajgreeny on 2009-04-15
Whoops, sorry!  I did not notice this was a mac problem, which I know even less about than Fedora.  I hope I didn't confuse you too much.

---

### Post by bbarabas on 2009-04-15
> **tiresia said:**
>  The easy way is to restart the computer from the Ubuntu alternate Installer and boot in rescue-mode. [/url]

I am looking at the links but in the meanwhile how do I do that? Using the live cd?

---

### Post by tiresia on 2009-04-15
> **bbarabas said:**
> I am looking at the links but in the meanwhile how do I do that? Using the live cd?
You can use the alternate cd to boot in the rescue mode, or you can use the live-cd to edit the file /etc/yaboot.conf
Follow the first link I gave you to edit it, or post here that file for help

---

### Post by bbarabas on 2009-04-15
So I booted Ubuntu live cd and after it installed I ran Terminal from Applications/Accessories and typed
sudo gedit /etc/yaboot.conf
it opened up the gedit windows but it was completely blank, there was nothing in there.

UPDATE> Also after starting ubuntu from live cd I found yaboot.conf in /boot/etc/ but still cannot see anything in it with gedit.

---

### Post by tiresia on 2009-04-15
> **bbarabas said:**
> So I booted Ubuntu live cd and after it installed I ran Terminal from Applications/Accessories and typed
sudo gedit /etc/yaboot.conf
it opened up the gedit windows but it was completely blank, there was nothing in there.

Since you booted from the LiveCD, the file you opened refers to the actually 'working root' (of the LiveCD). Instead you need to edit the file of the installed system.

If you are not experienced I do really suggest you to rescue the system using an alternate CD (if you edit manually that file from the installed system you need also to chroot the installed system)
Here an another link right for your needs (see the last section HOW TO RECOVER A BROKEN YABOOT IF YOU ALREADY HAVE A SUCCESSFUL DEBIAN INSTALL)
[http://www.ppclinux.info/wiki/maclin/Yaboot](http://www.ppclinux.info/wiki/maclin/Yaboot)

---

### Post by bbarabas on 2009-04-15
I will try that, thank you. Two more questions:
- what is an alternate CD? where do I get one? (it's ok if you just give me a link to an iso file)
- under the link that you gave me is it ok if I use the ubuntu live cd for the "Debian CD" they ask for?

---

### Post by tiresia on 2009-04-15
> **bbarabas said:**
> I will try that, thank you. Two more questions:
- what is an alternate CD? where do I get one? (it's ok if you just give me a link to an iso file)
An alternate CD is just a CD without any grafical interface (no desktop)
Download it here (choose Intrepid or Hardy)
[http://ubuntuforums.org/showthread.php?t=427714](http://ubuntuforums.org/showthread.php?t=427714)

- under the link that you gave me is it ok if I use the ubuntu live cd for the "Debian CD" they ask for?[/QUOTE]
Ubuntu is Debian based (also for the installer), therefore no difference about the installing process. You can follow that link using an ALTERNATE ubuntu CD
At the (first) yaboot prompt hit the TAB-key, and choose a rescue mode. It's very easy

---

### Post by bbarabas on 2009-04-20
> **tiresia said:**
> Here an another link right for your needs (see the last section HOW TO RECOVER A BROKEN YABOOT IF YOU ALREADY HAVE A SUCCESSFUL DEBIAN INSTALL)
[http://www.ppclinux.info/wiki/maclin/Yaboot](http://www.ppclinux.info/wiki/maclin/Yaboot)

Hi again, 
So I made an alternate cd and followed the steps under the link above until I had to type CTL ALT F2. The console appeared, but there was no such command as mac or mac-fdisk. I also hit TAB but it was not in the list so I could not go further to identify and select my root partition. 
Or is there some way I can access the yaboot.conf file after booting from the alternate cd?

---

### Post by tiresia on 2009-04-20
When you boot from the Alternate CD, at the very first prompt hit the TAB-Key.
What (kernel) options do you get? Do you get one (or more) rescue mode options?
The 'mac-fdisk -l' is just a command to get a list of your partitions - if you already know them, you don't need to use it.

---

### Post by bbarabas on 2009-04-20
There is a *rescue* and *rescue-powerpc* command and I typed rescue. After that I followed the instructions under the link you gave me: 
[I]
Enter your language
Enter you keyboard layout
Enter your key map
Enter hostname 
Enter domain name 
Then you are given a list of partitions on your machine and asked for your root partition select your root partiton.
If you dont know which partition is your root partition do this. 

CTL+ALT F2 <all at the same time>

This will give you a console with a prompt like this #
CODE:

 mac-fdisk -l

This will list all partitons, as an example mine is below. look down YOUR list until you see your root partition. [/I]

At that point, the  mac-fdisk -l command did not work which si important because I do not know which is my root partition.

---

### Post by tiresia on 2009-04-20
> **bbarabas said:**
> 
At that point, the  mac-fdisk -l command did not work which si important because I do not know which is my root partition.
What do you mean, that you don't get any 'answer' or the there is not such a command?

---

### Post by bbarabas on 2009-04-20
I will try again in half an hour so that I can give you the exact error message.

---

### Post by bbarabas on 2009-04-20
It seems that I mistyped something, the command
*mac-fdisk -l*
worked after all but now I have another problem: immediately after it lists the partitions, it starts listing something else which looks like this: 
*12434: @ 0 for 0, type=0x0*
this is the last line, the first begins with a smaller number and it keeps listing the same line very fast over several screens and I cannot get back to the partition list. 
(Sorry, I must be very annoying by now but I just cannot get over this...)

---

### Post by tiresia on 2009-04-20
Ok, try following```
mac-fdisk /dev/hda
``` (I guess hda is your HD)
You will get a prompt '?', press 'p' to print the partition map
There you should get the list you need. Press 'q' to quit mac-fdisk (don't do anything else, you could mess up your system)

---

### Post by bbarabas on 2009-04-20
OK, so I managed to find this: 

```
		type name		size	system

dev/hda1	Apple partition map 	31k	Partition map 
dev/hda2	Apple bootstrap		977k	Newworld bootblock
dev/hda3	UNIX SVR2		20.3G	Linux native
dev/hda4	UNIX SVR2		2.3G	Linux swap
dev/hda5	Apple bootstrap		1M	Newworld bootblock
dev/hda6	UNIX SVR2		200M	Linux native
dev/hda7	Linux LVM		33G	Unknown
```

Before I installed Fedora I partitioned 20 gigs for it, so hda3 must be the Fedora partition, which means that hda7 must be the Ubuntu (the 'unknown' label attached to it sounds bad...)> [QUOTE][/QUOTE]

---

### Post by tiresia on 2009-04-20
Are you sure? I would say that hda3 is the Ubuntu /root, and hda6 and hda7 is Fedora.
I think so, because, if you used a guided partitioning and installation, than you have a Logical Volume on hda6 and hda7 (as the Fedora Installer usually does - and therefore, bdw, it does not sound bad but normal :)

---

### Post by bbarabas on 2009-04-20
Hmmmhh, I am not sure of anything any more but I could swear I did not want to waste too much space on Fedora just to test it... 
So what should I do now? continue with the rescue operation by selecting hda3 (or rather hda2 since this is the bootblock) and then 'reinstall yaboot boot loader'?

---

### Post by tiresia on 2009-04-20
Don't worry, even if it is not the right Ubuntu Partition, it does not screw up our system. You can always retry it again&#8230;
Choose hda3 - you need to choose the root partition.
I must say, it is not very beautyfull to see two bootstrap partitions, but it happens, when you install the second gnu/linux system using a guided partitioning. Anyway, don't worry, just go ahead, and try this way - the next installation will be perfect :)

---

### Post by bbarabas on 2009-04-21
Goood morning, 
Houston, we have another problem. 
if I choose hda3, as you suggested, it gives me 4 options and "Reinstall yaboot boot loader" is not among them. However, hda6 does have this option. As for the rest of the hda's, it gives me the following message: 
*An error occurred while mounting the device you entered for your root file system (/dev/hda*) on /target. Please check the syslog for more information. *
So the only partition I can choose for reinstalling yaboot is hda6 (200 megs, Linux native). Should I proceed?

---

### Post by tiresia on 2009-04-21
Yes, you can try - as I said, it can't mess up your system. After that, we can edit yaboot.conf, if it does not work properly.

---

### Post by bbarabas on 2009-04-21
Got another nice red error message: 
[COLOR="Red"]failed with exit code 255[/COLOR]
however, if I go back to the Ubuntu installer menu, there is one command in the list which says "Install yaboot on a harddrive". This could not be helpful for me?

---

### Post by tiresia on 2009-04-21
Can you still boot in Fedora?

---

### Post by bbarabas on 2009-04-21
Yes, Fedora boots fine.

---

### Post by tiresia on 2009-04-21
Ok, sorry&#8230; I was a bit stupid. I don't know why, but I understood that both Linux Systems are gone. So, it's should be easier.
Reboot the computer from fedora, and post here the file /etc/yaboot.conf (to access it you need to be root)
Just a question - to avoid other misunderstadings You did not install MacOSX and you won't, right?

---

### Post by bbarabas on 2009-04-21
No, there was just Ubuntu on it. So, the yaboot file looks like this: 

```
# yaboot.conf generated by anaconda

boot=/dev/hda5
init-message="Welcome to Fedora!\nHit <TAB> for boot options"

partition=6
timeout=80
install=/usr/lib/yaboot/yaboot
delay=5
enablecdboot
enableofboot
enablenetboot
magicboot=/usr/lib/yaboot/ofboot

image=/vmlinuz-2.6.27.21-170.2.56.fc10.ppc
	label=2.6.27.21-170.2
	read-only
	initrd=/initrd-2.6.27.21-170.2.56.fc10.ppc.img
	append="rhgb quiet root=/dev/VolGroup00/LogVol00"

image=/vmlinuz-2.6.27.5-117.fc10.ppc
	label=linux
	read-only
	initrd=/initrd-2.6.27.5-117.fc10.ppc.img
	append="rhgb quiet root=UUID=50d529a6-370e-4274-af4b-a76c867fc948"
```

---

### Post by bbarabas on 2009-04-21
And this is what I see if I boot from Ubuntu live cd:

[IMG]http://computerworld.hu//upload/hir/2009/04/21/ubpart.jpg[/IMG]

---

### Post by tiresia on 2009-04-21
Attached you will find the yaboot.conf file, you can use to boot Ubuntu (and Fedora).
Start from Fedora```
su -
```
Backup your old xorg.conf```
cp /etc/yaboot.conf /etc/yaboot.conf.bak
```
Download and extract the attached file to your Desktop (or wherever you like) and Copy it in /etc ```
cp Desktop/yaboot.conf /etc/yaboot.conf
```
It will overwrite the 'old' file.
Update yaboot ```
ybin -v
```
Restart your computer

---
Please note:
1. /dev/hda3 is your Ubuntu Partition (no doubt)
2. With the attached file, your bootstrap partition is /dev/hda2
(The alternate cd had some problems in rescuing ubuntu because you have two bootloader - ?) You don't need anymore the second bootloader /dev/hda5 - you could even delete it
3. If it works, hitting TAB at bootup, you will be given the option to boot three kernel: linux (for Fedora), ubuntu, ubuntu.old

If you want, you can customise some options reading this thread
[http://ubuntuforums.org/showthread.php?t=994882](http://ubuntuforums.org/showthread.php?t=994882)
---------

If it does not work, please run this command to get the openfirmare path and post it here ```
ofpath /dev/hda
```

---

### Post by bbarabas on 2009-04-21
OK but are you sure everything you wrote down is ok? Because you mentioned xorg.conf and the command refers to yaboot.conf and vicerversa.

---

### Post by tiresia on 2009-04-21
> **bbarabas said:**
> OK but are you sure everything you wrote down is ok? Because you mentioned xorg.conf and the command refers to yaboot.conf and vicerversa.

thanks, I corrected it

---

### Post by bbarabas on 2009-04-21
> **tiresia said:**
> 
3. If it works, hitting TAB at bootup, you will be given the option to boot three kernel: linux (for Fedora), ubuntu, ubuntu.old 

It is almost ok: at bootup I get the same boot option with openfirmware among them. If I choose this and press TAB, it gives me the three options you mentioned. However, if I type ubuntu or ubuntu.old it says that the path or directory does not exist. 
The ofpath you asked for is the following: 
/pci@f4000000/ata-6@d/disk@0:

---

### Post by tiresia on 2009-04-21
I posted two versions. Try the first, because I made (again) a mistake before. Sorry, but I'm trying to help you while doing other stuff...
Do not forget to run 'ybin -v' after coping the file

---

### Post by bbarabas on 2009-04-21
> **tiresia said:**
>  Sorry, but I'm trying to help you while doing other stuff...

I thought so and I can't be grateful enough. I'll get you a fine bottle of Tokaji Aszu next time I'll be in Berlin :)

---

### Post by tiresia on 2009-04-21
> **bbarabas said:**
> I thought so and I can't be grateful enough. I'll get you a fine bottle of Tokaji Aszu next time I'll be in Berlin :)
What??? Just one bottle of Tokaji Aszu?!?
;)

---

### Post by bbarabas on 2009-04-22
Bear in mind that you don't drink an Aszu like beer. You taste it actually ;)
And now, back to work! the first file worked just the same ("no such file or directory"), the second gave me an "input/output error" message...

---

### Post by tiresia on 2009-04-22
Ok, hope this will work!
As always, do not forget to run ybin -v after extracting and copying the file

---

### Post by bbarabas on 2009-04-22
nnope, the same input/output error again. 
I don't like defeats, but let's just accept that I screwed up something really bad here... I don't want to torture you any more with this :(

---

### Post by tiresia on 2009-04-22
Well, it shouldn't be so difficult! When do you get this input/output error - when you run ybin? Or when you reboot the system?

Just to be sure:
1. download the attached file
2. extract it to your desktop
3. copy the EXTRACTED File to /etc
4. run ybin
5. reboot

---

### Post by bbarabas on 2009-04-22
> **tiresia said:**
> Well, it shouldn't be so difficult! When do you get this input/output error - when you run ybin? Or when you reboot the system?


I did exactly as you said, and this is what happens: 
- run ybin, reboot the system 
- the following menu appears: 
[LIST]
[*]l (fedora)
[*]n (network)
[*]c (cdrom)
[*]o (openfirmware)
[/LIST]

if I press TAB here nothing happens but if I press enter another command line appers and if I press TAB here it gives me four options: 
linux
(some numbers and letters)
ubuntu
ubuntu.old

and if I type ubuntu or ubuntu.old it gives me the input/output error message. 
(Have I done something wrong?)

---

### Post by tiresia on 2009-04-22
Before installing Fedora, you could use Ubuntu without any problems, right? Did you need to give any argument when booting (such as nosplash)? Did you perform any upgrade?

Please, boot in Fedora, and mount hda3 (just click on the icon in gnome > places > Removable Media). Fedora should mount hda3 as 'disk' on /media
If you go to /media/disk/etc/yaboot.conf, you will find the yaboot.conf generated by Ubuntu. Can you please post it here?

---

### Post by bbarabas on 2009-04-22
> **tiresia said:**
> Before installing Fedora, you could use Ubuntu without any problems, right? Did you need to give any argument when booting (such as nosplash)? Did you perform any upgrade? 

No, Ubuntu worked fine before and I did not do any upgrade (not even to 8.10). And there is no such thing as Removable Media in Places...

---

### Post by tiresia on 2009-04-22
Ok, tell me if you want to stop and just reinstall - I can go on without problems until we find the solution :)

Try please following ```
su -
mount /dev/hda3 /mnt
```

On /mnt you should see now your Ubuntu
```
ls /mnt
cd /home/your_user_name_on_fedora
cp /mnt/etc/yaboot.conf Desktop/
chown your_user_name:your_user_name Desktop/yaboot.conf
```
please, post it here

---

### Post by bbarabas on 2009-04-22
> **tiresia said:**
> Ok, tell me if you want to stop and just reinstall 

Nonoooo, I want my files back! Besides, I am quite curious if we can make this thing work again. Not to mention how much fun I am having with bloody linux :D

---

### Post by bbarabas on 2009-04-22
> **tiresia said:**
> Ok, tell me if you want to stop and just reinstall - I can go on without problems until we find the solution :)

Try please following ```
su -
mount /dev/hda3 /mnt
```

On /mnt you should see now your Ubuntu
```
ls /mnt

``` 

Well, after I typed this last command, I got the following: 

```
[root@barabas bbarabas]# ls /mnt
ls: /mnt/initrd nem érhet&#337; el: Be/kimeneti hiba
ls: /mnt/opt nem érhet&#337; el: Be/kimeneti hiba
ls: /mnt/sbin nem érhet&#337; el: Be/kimeneti hiba
ls: /mnt/media nem érhet&#337; el: Be/kimeneti hiba
ls: /mnt/dev nem érhet&#337; el: Be/kimeneti hiba
ls: /mnt/tmp nem érhet&#337; el: Be/kimeneti hiba
ls: /mnt/mnt nem érhet&#337; el: Be/kimeneti hiba
ls: /mnt/usr nem érhet&#337; el: Be/kimeneti hiba
ls: /mnt/lib nem érhet&#337; el: Be/kimeneti hiba
ls: /mnt/sys nem érhet&#337; el: Be/kimeneti hiba
ls: /mnt/boot nem érhet&#337; el: Be/kimeneti hiba
ls: /mnt/home nem érhet&#337; el: Be/kimeneti hiba
ls: /mnt/proc nem érhet&#337; el: Be/kimeneti hiba
ls: /mnt/etc nem érhet&#337; el: Be/kimeneti hiba
bin   cdrom  etc   initrd  lost+found  mnt  proc  sbin  sys  usr
boot  dev    home  lib     media       opt  root  srv   tmp  var
```

Where *nem érhet&#337; el: Be/kimeneti hiba* means something like "not available: input/output error". I suppose that is not ok, should I go ahead though?

---

### Post by tiresia on 2009-04-22
Well, yes, you can just copy the yaboot.conf as said - if it is still there…
Your system looks not ok. If you do ```
ls /mnt/home/your_user_name_on_ubuntu
``` you should see listed all your files in ubuntu. By the way, if those are important for you, you should backup them.

Of course, you could open the file manager and see them under /mnt

---

### Post by bbarabas on 2009-04-22
> **tiresia said:**
>  you should see listed all your files in ubuntu. By the way, if those are important for you, you should backup them. 

Yes, this is what I am trying to do, otherwise I would have reinstalled ubuntu a long time ago... especially now, that jaunty comes out.

---

### Post by bbarabas on 2009-04-23
> **tiresia said:**
> Ok, tell me if you want to stop and just reinstall - I can go on without problems until we find the solution :)

Try please following ```
su -
mount /dev/hda3 /mnt
```

On /mnt you should see now your Ubuntu


No I don't, under /mnt there is an empty etc with 0 bytes. 
Oh and I can't see any Jaunty for PowerPC either :(

---

### Post by tiresia on 2009-04-23
Sorry, but I'm starting to think that this is not a yaboot problem.
Maybe, you should just start from the LiveCD (you can use Jaunty, it works well), and first of all back up your data - if they are still there :(

---

### Post by bbarabas on 2009-04-24
Yes, I'm afraid too... So right now I am in ubuntu, booted from Hardy live cd. The partition looks like in the image I posted before (with Gparted). In the second section of Places (below Documents, Pictures etc.) there is Computer, 21.8 GB Media and /boot. Where should I look for my old files?

---

### Post by tiresia on 2009-04-24
Ubuntu should be the 21.8 GB Media. To mount it, click just on that icon. It will appear on your desktop. See there if you can find your files - if they are still there you are lucky. Do you have an external HD?

---

### Post by bbarabas on 2009-04-24
I have one at home (I am at work now). 
I mounted the media but none of my files are there, only a lost+found directory which I cannot access (you do not have permissions necessary to view).

---

### Post by tiresia on 2009-04-24
Close nautilus (the file browser) and run in a terminal```
gksudo nautilus
``` so that you can see (and copy) anything you need

---

### Post by bbarabas on 2009-04-24
Nope, it is dead empty as well. So I think that concludes our rescuing efforts... all passengers got drowned in the Fedora ocean :)

---

### Post by tiresia on 2009-04-24
I'm sorry, but I'm afraid that installing Fedora you erased your Ubuntu System (but Fedora is not guilty&#8230;) I hope that they were not important files!

---

### Post by bbarabas on 2009-04-24
> **tiresia said:**
> I'm sorry, but I'm afraid that installing Fedora you erased your Ubuntu System (but Fedora is not guilty…)

Now that was mean :( There were a lot of files actually, most of them personal. I tried installing Fedora on a PC first, which had XP installed before. It worked fine, I can access both XP and Fedora. I tried to do the same on PowerPC after and this is what happened. It is true, I should have backed up the files before. Tough lesson.

---

### Post by bbarabas on 2009-04-24
One more thing: where can I download Jaunty for PPC?

---

### Post by tiresia on 2009-04-24
[http://ubuntuforums.org/showthread.php?t=1135080](http://ubuntuforums.org/showthread.php?t=1135080)

---

