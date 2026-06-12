---
title: "Upgrage to 11.10 reboot failed"
date: 2011-10-16
forum: Apple Hardware Users
---

### Post by ibokg4 on 2011-10-16
Hello

i made a distro upgrade for my ibookg4 to v 11.10.

the upgrate itself had an error installing one package named firmeware... (don't know the name exactly) but afterwards finished with success.

i rebootet after the distroupgrade and the ibook failed to boot.

what i see when i press the power button:
1. there is a boot menu: 
First Stage upbuntu boot, l=linux, c = cdrom
i choose l

2. there is a yaboot screen (i choose nothing after a few seconds the boot process continues)

3. The cd rom makes some noise, nothing happens for about 15 s

3. An error and the busybox is displayed:

WARNING bootdevice may be renamed. Try root=/dev/sda3
Gave up waiting for root device........

then BusyBox v1.18.4 is displayed.

when i look at /dev there is a device /dev/sda3 (wich is the root device)

i can then mount the root device
cd /
mount /dev/sda3 /root

then:
exit
but the same error is displayed again.

how does i manage to get the system to boot from /dev/sda3 ?
i don't catch the boot progress. doesn't yaboot mount the root device ?

thanks stefan

---

### Post by rsavage on 2011-10-16
*EDIT:*
*At the BusyBox terminal type the command:*
 
*modprobe pata_macio*
 
*then press ctrl+D to resume the boot. See post #8 for more info on this. If this doesn't work follow orginal instructions....*
 
 
My wild stab in the dark:
 
At the second yaboot prompt type
 
```

Linux root=/dev/sda3

```
That is assuming you have a standard Ubuntu install on partition 3.  If you are dual-booting then you may have linux installed on another partition.
  
There are various ways you can setup a yaboot.conf to point to root [http://ubuntuforums.org/showpost.php?p=11039429&postcount=10](http://ubuntuforums.org/showpost.php?p=11039429&postcount=10)
You could also try setting the root value using the UUID number.
 
```

Linux root="UUID=big-long-number-000"

```
I think there has been some sort of renaming thing going off so hda3 maybe now sda3?
 
Will it boot if you type at the second yaboot prompt:
```

old

```
This will be a temporary fix using the 11.04 kernel. However, once you receive a kernel package update through the Update Manager the 'old' will link to a 11.10 kernel.

---

### Post by rsavage on 2011-10-16
Just to add some more to this:
 
On some installs the yaboot.conf has this line:
 
boot=/dev/hda2
 
On others it has this:
 
boot="/dev/disk/by-label/bootstrap"
 
So you may have to fiddle with the boot= line too! I think the boot path is only used when you run the ybin/yabootconfig commands, so don't worry about this until you get the system running!

---

### Post by ibokg4 on 2011-10-16
That did the trick.

After booting with Param: "Linux root=/dev/sda3" i finished the distro upgrade (there were some additional packages that needed an update / install).

after that i fixed yaboot with:
sudo yabootconfig -r /dev/sda3

now, everything works

Thanks
Stefan

---

### Post by kensanata on 2011-10-16
Thanks, worked for me as well!

---

### Post by rsavage on 2011-10-17
That yabootconfig command you've found is a very neat way to do it!  I'm sure a lot of people will benefit from that.  Thanks for posting back with the solution!

---

### Post by canhoto on 2011-10-20
In the second yaboot prompt, I just typed "old" and, apparently, I'm in the 11.10 Xubuntu (with a healthy CPU usage!). What does this "old" mean? Can the yaboot fix be done from this "old" (new) system?

---

### Post by rsavage on 2011-10-21
"old" boots into the old kernel image. It's used in case the new kernel image causes problems.
 
However, in this case it's best to boot using the root= parameter otherwise things get confusing.
 
The safest way to update changes to the yaboot.conf is to edit the file yourself.  The "yabootconfig" command formats the bootstap partition so I assume there is a greater chance of something going wrong.
 
To open yaboot.conf type one of the following (depending on the text editor you want/have):
 
sudo nano /etc/yaboot.conf
gksudo gedit /etc/yaboot.conf
gksudo leafpad /etc/yaboot.conf
gksudo mousepad /etc/yaboot.conf
 
When you've made and saved your changes use the command "sudo ybin -v" to copy it across to the boot partition.
 
Type "man yaboot.conf" for an explanation of what it all means.
 
Note, on some machines just changing the root= parameter is not sufficient and you may have to do more steps to get it to boot with the new kernel [http://lists.debian.org/debian-powerpc/2011/08/msg00050.html](http://lists.debian.org/debian-powerpc/2011/08/msg00050.html) . The ubuntu commands to make it permanent are slightly different to those given in the link for debian:
 
```

echo pata_macio | sudo tee -a /etc/initramfs-tools/modules
sudo update-initramfs -u

```
 
The above is just a fancy way of adding the word "pata_macio" to the end of the modules file. You could alternatively type "sudo nano /etc/initramfs-tools/modules" to open the file and add the word on a new line yourself. You must always run "update-initramfs -u" for the changes to take effect.

---

### Post by new to ubutnu on 2011-12-02
Hello
 
I am having the exact same problem but when i enter in any of the above options at the second yaboot menu i get nothing or Linux: is not a file they find (for the Linux root=/dev/ada3)
I looked in the /dev folder and i see an ada and ada1
 
Help soon would be great thanks

---

### Post by rsavage on 2011-12-03
Hi, a bit more info would be good. Is this an upgrade (from 11.04 to 11.10) or a direct install of 11.10? Also, what machine do you have as I have never heard of ada, ada1 etc (except the prgramming language of course!)? Is this some sort of RAID setup?
If it is an upgrade you should always be able to use "old" until you get the problem sorted. By the sounds of it you need something different to pata_macio although I am a bit confused if ada1 is a hard drive partition (why are the others not showing up?). Running a live cd (try 12.04) maybe useful to figure out the modules used.

---

### Post by new to ubutnu on 2011-12-03
This is an upgrade from 11.04 to 11.10 because there was an error with installing straight to 11.10 (no hard drive found) I had used an article saying how to install lubuntu through a minimal cd in cliThe computer is a 400 MHz iMac g3 with 512 ram

---

### Post by new to ubutnu on 2011-12-03
Oh I had said Ada when I ment Sda sorry also I don't know how to use old besides entering it in which I did and nothing happened

---

### Post by new to ubutnu on 2011-12-03
i got past the busybox error with the pata_macio command with ctrl+d
but now i have a different problem it was supposed to boot to gui but it just went to cli and it wont let me change the yaboot file to make the file boot everytime (i used sudo yabootconfig -r /dev/sda3 or sda1 or sda)

---

### Post by rsavage on 2011-12-03
It will only boot to a GUI if you have installed a GUI.
 
If you have a standard install with only linux and no mac os then you should run "sudo yabootconfig -r /dev/sda3".  If you have installed linux on a different partition (other than 3) then you need to ammend the command accordingly.
 
Since you needed to modprobe the pata_macio module then you should run the commands in post 8.
 
I will try and ammend the instructions to make this clearer.

---

### Post by new to ubutnu on 2011-12-03
for the gui i think i used your article on how to install lubuntu on ppc at this website [http://ubuntuforums.org/showpost.php?p=11020435&postcount=1](http://ubuntuforums.org/showpost.php?p=11020435&postcount=1)
so i should have the gui after the code there

i had an external hard drive plugged in so that turned out to be my sda and the only other thing i have in /dev that looks like a disk is sdb but when i edit the yaboot.conf to boot to this the openfirmware says it doesn't have a partition on it

i dont know where the drive is so here are some that could be all with different numbers(i.e. 0,1,2,3,4,5): vcsa, ram, tty, usbmon, loop, vcs, hvc

also i tried the sudo yabootconfig -r /dev/sda3 and other extension but like i said i dont know which is which

thanks for the help

---

### Post by rsavage on 2011-12-03
I'm a bit confused.  Are you still at a command line?  
 
If "sudo yabootconfig -r /dev/sda3" etc has always produced an error message then I don't think it will have ammended any files and you will probably be able to reboot okay.
 
To make sure though open the yaboot.conf with
 
sudo nano /etc/yaboot.conf
 
and look at the root= line.  If it is UUID="blah-blah-blah-blah" then you'll be okay I think.
 
> 
i dont know where the drive is so here are some that could be all with different numbers(i.e. 0,1,2,3,4,5): vcsa, ram, tty, usbmon, loop, vcs, hvc

They're not drives.
 
 
I'm off to bed now....

---

### Post by rsavage on 2011-12-03
Forgot to say use the commands
 
sudo blkid
cat /etc/fstab
 
to find out about your partitions.

---

### Post by new to ubutnu on 2011-12-04
i used sudo yabootconfig -r /dev/sdb because the external hard drive was sda and nothing else looked like a drive and i confirmed to writing a yaboot.conf file on there or something and when i rebooted it caused the same error but the modprobe pata_macio didn't work so i can't get into ubuntu at all

All thats there is a (initramfs) line with the computer waiting for a command

i think i screwed something up so i want to get back to where i was but it would be nice to do a fresh ubuntu install if nothing else so what is the command to boot from my cd because i dont know how to do that

---

### Post by rsavage on 2011-12-05
I have amended the ‘lubuntu’ instructions to try and make it clearer for people doing a new install.
 
As I understand it, you will end up at a BusyBox shell for one or more of following reasons:
1. You need to ‘modprobe’ the pata_macio module (only needed for some computers)
2. You need to change the root= parameter (only needed if you do successive upgrades from an old version of ubuntu?)
3. You need to ‘modprobe’ some other module (G5s?)
 
By the sounds of it you only had problem 1, but by trying the fixes for 2 you have made things worse.
 
Personally, I wouldn’t use the yabootconfig command. It reformats your bootstrap partition and therefore I would imagine there is a greater chance of things going wrong. I would use the ybin command instead as I describe in post #8.
 
You shouldn’t have to re-install. All you need to do is work out the path to where you installed ubuntu (but, only you can do this). I don’t understand why you can’t boot a cd as you must have done it previously? At the first yaboot prompt you can press ‘c’ to boot the cd.
 
For future people, if the problem is 3 then I would suggest running the old 11.04 kernel or a recent live cd (12.04) and using the “lsmod” and “lspci -k” commands to work out what modules you need. If the appropriate modules are missing in 11.10 and 12.04 then you need to raise a bug on this. You can overcome it in 11.10 by apt-pinning the 11.04 kernel packages or compiling the appropriate module to add to the 11.10 kernel. You’ll have to do your own research on these things, but feedback the results here for the benefit of other PowerPC users.

---

### Post by rsavage on 2011-12-05
Forgot to say a problem 4 could be:
 
4. You need to add a rootdelay parameter (maybe needed for USB/firewire)
 
See links in 'lubuntu' instructions for more on this, but most people's problems when this occurs on an upgrade will be 1 to 3 I would of thought.

---

### Post by new to ubutnu on 2011-12-05
i had made the changes to the root= parameter and modprobe pata_macio and that didn't do anything also i had upgraded from 11.04 to 11.10 so i think doing changing the yabootconfig with sudo nano to that file was needed.  the problem was more that i didn't know what i should change the root= to so i tried different extensions like sda or sdb or hda or anything all coming up with the yaboot error

i found out how to boot to disc and by the time you posted i had already written over everything i am going to redo the install and i will probably get the same error when i try to upgrade to 11.10 from 11.04 mini.iso disk so i will come back then

---

### Post by new to ubutnu on 2011-12-05
Ok so I reinstalled then updated to 11.10 again same error and I did exactly what you said with adding the modprobe pata_macio line to the initramfs file and I confirmed it with the update line and I rebooted but same busybox error comes up

One other thing when running update-initramfs -u I get an error saying it can't create a hard link cannot create a regular file that's in boot/initrd.img and so on

---

### Post by rsavage on 2011-12-06
> **new to ubutnu said:**
> Ok so I reinstalled then updated to 11.10 again same error and I did exactly what you said with adding the modprobe pata_macio line to the initramfs file and I confirmed it with the update line and I rebooted but same busybox error comes up

 
You should just add "pata_macio" not "modprobe pata_macio".  If you still get an error, then can you print it out exactly please.

---

### Post by new to ubutnu on 2011-12-06
ok i had only added pata_macio, modprobe pata_macio, modprobe pata_macio and on the next line exit but when i went back to just pata_macio it worked so thank you rsavage for the help

one more thing i used your post at [http://ubuntuforums.org/showpost.php?p=11020435&postcount=1](http://ubuntuforums.org/showpost.php?p=11020435&postcount=1) to install the programs and gui but now it wont go into the gui just a command line interface even before i updated so how can i fix that[URL="http://ubuntuforums.org/showpost.php?p=11020435&postcount=1"]
[/URL]

---

### Post by rsavage on 2011-12-06
If you are following the guide then it says to upgrade before installing the GUI.
 
Any GUI problems are best sorted on a new thread, but I wrote a massive section in the guide on how to solve them.  I will help you if you don't understand something in that section, but please try to follow the information in the guide first.  Considering the time difference between us, ultimately you'll getter a quicker setup that way.

---

### Post by new to ubutnu on 2011-12-06
in your article there is a place for no gui just a blank screen which i dont have i have a cli environment

also where should we go for new thread about gui thanks

---

### Post by rsavage on 2011-12-07
I have re-tweaked the 'Screen Resolution/Blank screen/No GUI' instructions yet again to try and make them clearer.  
 
If you have any problems I would suggest posting them on this thread [http://ubuntuforums.org/showthread.php?t=1888881](http://ubuntuforums.org/showthread.php?t=1888881) since it is about a similar computer to your own and is the thread I link to from my instructions.  It would be good if you could test some things.

---

### Post by Brompton5007 on 2012-02-03
[FONT=Arial][SIZE=2]**2004 G4 ibook**, CPU PPC 800mhz, RAM 1.1GiB, HD 320GB IDE
5 partitions, Triple Boot.
**yaboot error on Upgrade from 11.4 to 11.10**[/SIZE][/FONT][FONT=Arial][SIZE=1]
[SIZE=2]Firstly big thanks to* rsavage* and the other posters.
*(There is nothing new in this post, just a single description of what worked for me and the ibook).*[/SIZE][/SIZE][/FONT][FONT=Arial][SIZE=2]
After initial despair at getting a constant hang with the error warning:[/SIZE][/FONT][FONT=Arial][SIZE=2]
WARNING bootdevice may be renamed. Try root=/dev/sda11[/SIZE][/FONT][FONT=Arial][SIZE=2]
Gave up waiting for root device....[/SIZE][/FONT][FONT=Arial][SIZE=2]
[/SIZE][/FONT][FONT=Arial][SIZE=2]I had my first success by typing[/SIZE][/FONT][FONT=Arial][SIZE=2]```
old
```[/SIZE][/FONT][FONT=Arial][SIZE=2]in the second stage of the yaboot boot screen, this for me prevented the BusyBox shell and loaded the old 10.4 kernel.[/SIZE][/FONT][FONT=Arial][SIZE=2]
- The 11.10 sign-in screen came up. I could now successfully sign in and the upgraded version of Ubuntu 11.10 loaded. - I found that a couple of modules had not been upgraded correctly, so I re-ran  the upgrade manager and successfully completed the install.                        *- this was progress.*
The ¨pata_macio¨ tip was for me to turn out to be a dead end...[/SIZE][/FONT]
[FONT=Arial][SIZE=2] Despite the successful reboot and correcting the failed modules of the original install, on the  subsequent attempt to run 11.10 I had the same ¨boot device renamed¨ error (; when no  additional commands were added to the second yaboot login screen). It attempted to  load the 11.10 kernel screen only to run the BusyBox shell and hang at the initramfs prompt, [/SIZE][/FONT] [FONT=Arial][SIZE=2]so I tried the...[/SIZE][/FONT][FONT=Arial][SIZE=2]```
modprobe pata_macio
ctrl+ D
```[/SIZE][/FONT][FONT=Arial][SIZE=2]then[/SIZE][/FONT][FONT=Arial][SIZE=2]```
root=/dev/sda11
```(sda11 being my Ubuntu partition)* - but no luck*
However after reboot, by using[/SIZE][/FONT][FONT=Arial][SIZE=2] ```
Linux root=/dev/sda11
```instead of ¨old¨ in  the second stage of the yaboot login screen, I as able to boot directly into Ubuntu 11.10 and signin. *- more progress*
This time I decided (as per the recommendations of earlier posts) to  change the name of the partitions used in the yaboot config file from  hda to sda.[/SIZE][/FONT][FONT=Arial][SIZE=2]
In terminal[/SIZE][/FONT][FONT=Arial][SIZE=2] to open the  yaboot config file use.[/SIZE][/FONT][FONT=Arial][SIZE=2]```
sudo nano /etc/yaboot.conf
```You can use the up down, left right arrow keys to navigate around the  list of partions to change their names from hda to sda.  (In the example  of my Linux partition, hda11 became sda11, and hda12 became sda12, and  so on for all 5 of my partitions). [/SIZE][/FONT][FONT=Arial][SIZE=2]
Save the changes of the yaboot config file by ...                     ```
ctrl+ D
```(that is by pressing the control key and the letter D)Then the changed yaboot file must be copied to the boot partition. Use[/SIZE][/FONT][FONT=Arial][SIZE=2]```
sudo ybin -v
```Then restart and *success*, system boots smoothly into 11.10 with no  errors, (and no need to add any additional information to the second  stage of the yaboot screen).  [/SIZE][/FONT]        [FONT=Arial][SIZE=2]
Seems that my problem (with the ibook) was caused by the renaming of the  partitions from hda to sda in the 11.10 upgrade and the old yaboot  config file pointing with the deprecated partition naming scheme. Fortunately the new install does  not seem to have any other of the reported errors. [/SIZE][/FONT][FONT=Arial][SIZE=2]

*Thanks again,once again, ¨I am living the dream¨.*[/SIZE][/FONT]

---

