---
title: "Kernel Panic - not syncing: VFS: Unable to mount root fs on unknown-block(0,0)"
date: 2007-10-14
forum: Absolute Beginner Talk
---

### Post by nhandler on 2007-10-14
I finally got around to installing a large batch of updates for Gutsy. However, when I restarted my computer, I got this error:
> Kernel Panic - not syncing: VFS: Unable to mount root fs on unknown-block(0,0)


I'm able to boot an older kernel, but the login screen never loads. I just get a colored background and a loading mouse. However, by doing that, I am able to use Ctrl+Alt+F6 to get a terminal. I have tried sudo apt-get update. But if I try to do a dist-upgrade, I get an error telling me to do sudo dpkg --configure -a. When I run that, I get a ton of dependency errors and then "dpkg: ../../src/packages.c:252: process_queue: Assertion `!queuelen' failed." I am also able to use a live cd to get to a terminal. Is there anything I can do to get a GUI back? I don't mind if it is an older kernel. However, I do not want to reinstall if it is not needed.

---

### Post by juantovarm on 2007-10-15
have you tried reinstalling gdm? if i were you i would try sudo apt-get remove --purge gdm && sudo apt-get install gdm, if that doesn't work i would try installing kdm

---

### Post by jr.gotti on 2007-10-15
Pop in the live CD...when it boots open a terminal, and remount your root partition.

sudo mount /path/to/root/partition /

then sudo grub-install hd0,0

reboot, and youll be good.

---

### Post by Vengeance_AU on 2007-10-15
I've put up an alternative option [here]("http://ubuntuforums.org/showpost.php?p=3536178&postcount=2") - didn't need a boot CD to get it working.

---

### Post by MessiahAngel on 2007-10-16
Hi :)
I had the same error and i saw that a line was missing in menu.lst (/boot/grub/menu.lst)
So i added the line manually and it worked, ubuntu boots now on kernel 2.6.22-14 :D

Missing line :
> initrd		/boot/initrd.img-2.6.22-14-generic

hope it will help :)

---

### Post by nhandler on 2007-10-16
I am unable to install or uninstall any packages. So reinstalling GDM is not an option. If I do try and install/remove a package, I get told to run dpkg --configure -a, which gives a ton of dependency errors.

The grub-install command didn't do anything.

The alternative option didn't work either.

I don't have a line missing from my menu.list

---

### Post by MessiahAngel on 2007-10-16
Maybe my answer is not clear enough, or focused enough, my bad.

this line comes here in your menu.lst :
> ## ## End Default Options ##

title		Ubuntu 7.10, kernel 2.6.22-14-generic
root		(hd0,5)
kernel		/boot/vmlinuz-2.6.22-14-generic root=/dev/mapper/isw_baiagddche_ARRAY6 ro quiet splash
**initrd		/boot/initrd.img-2.6.22-14-generic**
.
.
.


check again if it's there, if yes then my bad

---

### Post by nhandler on 2007-10-16
> **MessiahAngel said:**
> Maybe my answer is not clear enough, or focused enough, my bad.

this line comes here in your menu.lst :


check again if it's there, if yes then my bad

No, I didn't misunderstand you. I have that section in my menu.list:

> ## ## End Default Options ##

title           Ubuntu 7.10, kernel 2.6.22-14-generic
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.22-14-generic root=UUID=6890e9a2-3e7b-47e2-b4eb-cfa233bbcb16 ro quiet splash
quiet


But thanks for trying to help. I really appreciate it.

---

### Post by IMcD23 on 2007-10-20
Hey, I am having the same problem...I put the initrd /boot/initrd.img-...in and it said 15 file not found. press any key to continue.  should I have kept the quiet line in there?

EDIT:  I tried it and I gave me the same error

---

### Post by IMcD23 on 2007-10-20
> **IMcD23 said:**
> Hey, I am having the same problem...I put the initrd /boot/initrd.img-...in and it said 15 file not found. press any key to continue.  should I have kept the quiet line in there?

EDIT:  I tried it and I gave me the same error

Yes!!! I got it!!! You do edit the line, except, you have to go to /media/disk/boot/ and take off the .bak part of initrd.img-2.6.22-14-generic.bak 


:guitar::popcorn:

---

### Post by nhandler on 2007-10-20
Well, I downloaded and burnt the official Gutsy release to a cd. Then, using the live cd, I backed up all my documents and generated a list of all installed programs (so that I could reinstall them). Then I totally wiped the drive and installed gutsy. I also set up a separate partition for /home.

---

### Post by Krankr on 2007-10-21
> **MessiahAngel said:**
> initrd /boot/initrd.img-2.6.22-14-generic

If I'm trying to compile a custom kernel and this wasn't created automatically, what might I have missed?
(The new kernel was added to /boot/grub/menu.lst, but no /boot/initrd.img-blaha was created and no subsequent loading of such in the grub-menu file..?)

---

### Post by DestroyMicroshaft on 2007-10-22
Well this was a ball buster but I fixed this on my machine so Im going to try my best to relay the steps to all of you on how I managed this workaround.

Ok, first off I was unable to mount my file system via gutsy live cd, so boot into feisty live cd. Once your in feisty live cd, go up to System >> Administration >> Gnome Partition Editor, which should force your file system mount, probably as "disk", once its mounted just close the editor, and open a terminal and run > sudo gedit /boot/grub/menu.lst

This will open a new window, scroll to the bottom of this window, and you will see something that looks similar to this...>  ## ## End Default Options ##

title		Ubuntu 7.10, kernel 2.6.22-14-generic
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.22-14-generic root=/dev/hda3 ro quiet splash
initrd		/boot/initrd.img-2.6.22-14-generic
quiet

title		Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.22-14-generic root=/dev/hda3 ro single
initrd		/boot/initrd.img-2.6.22-14-generic 

See the line there that says kernel, then across from kernel it says /boot/vmlinuz-2.6.22-14-generic root= , well after root= your gonna wanna change that to /dev/whatever you partitions in labelled, ex. hda3, like mine. make sure to leave "ro quiet splash" at the end, now save.

now its back to the terminal, this time run: >  sudo gedit /etc/initramfs-tools/conf.d/resume

A new window will open up and it say something like this inside
> RESUME=/dev/sda3

You need to put the same /dev/whatever you did for the last file you edited after the "RESUME=" similar to how mine looks in the box above.

Now reboot, exiting the live cd. now boot normally and hooray, you should be at you login window in no time. Once you get logged in, your gonna wanna do one more thing, open up a terminal, and run this: > sudo update-initramfs -u

And for good measure why don't you give it another reboot to make sure your machine is ok. I hope this helps some of your out, I know it worked for me :):guitar:

---

### Post by logos34 on 2007-10-24
> **MessiahAngel said:**
>  > initrd /boot/initrd.img-2.6.22-14-generic 

yep, I noticed that right away.  The first thing I did today after upgrade finished and before restarting was check menu.lst.  Sure enough initrd line was missing.  Strange, I thought, did they integrate it into the kernel somehow?  No, the  initrd.img- is there in /boot.  Let's see what happens anyway on boot.  Bam, kernel panic.  So I added the line and all is well now in ubuntuland.

They should have fixed this bug in the upgrade script--it's been nearly a week since gutsy final was released.

EDIT: For all those having the same problem:

If the upgrade hasn't stripped out the initrd line from your feisty recovery kernels as well, boot into the latter and add it to menu.lst:

**# nano -w /boot/grub/menu.lst**

[EDIT] OR see post #17 below.


Otherwise boot from the live cd and edit menu.lst from there

---

### Post by tormod on 2007-10-24
> They should have fixed this bug in the upgrade script--it's been nearly a week since gutsy final was released.
Did you guys with the missing initrd line issue fully update your Feisty system (from the feisty-updates repository) before starting the upgrade to Gutsy?

---

### Post by logos34 on 2007-10-24
> **tormod said:**
> Did you guys with the missing initrd line issue fully update your Feisty system (from the feisty-updates repository) before starting the upgrade to Gutsy?

AFAIK I was fully up to speed.  Was running 2.6.20-16-generic kernel (32-bit).  All pending updates were installed well before beginning upgrade.

---

### Post by tormod on 2007-10-24
Thanks for the workaround instructions. Note that you can select the boot line and press 'e' (instead of Enter) and then add just the initrd line with 'o', which will be a little easier than typing the whole thing from scratch with the 'c' command mode.

(See [http://www.gnu.org/software/grub/manual/grub.html#Menu-entry-editor](http://www.gnu.org/software/grub/manual/grub.html#Menu-entry-editor))

---

### Post by logos34 on 2007-10-24
> **tormod said:**
> Thanks for the workaround instructions. Note that you can select the boot line and press 'e' (instead of Enter) and then add just the initrd line with 'o', which will be a little easier than typing the whole thing from scratch with the 'c' command mode.

(See [http://www.gnu.org/software/grub/manual/grub.html#Menu-entry-editor](http://www.gnu.org/software/grub/manual/grub.html#Menu-entry-editor))

Yes, you're absolutely right.  (I was trying to do that originally but forgot how.  Thanks for refreshing my memory).

I've edited my post accordingly.

---

### Post by tormod on 2007-10-31
I think those of you who were missing an "initrd" line in the grub menu.lst do not have a postinst_hook line in /etc/kernel-img.conf. If this is the case, can you please tell me your install/upgrade history?

That issue is discussed in [https://bugs.edge.launchpad.net/bugs/156058](https://bugs.edge.launchpad.net/bugs/156058)

---

### Post by logos34 on 2007-10-31
> **tormod said:**
> I think those of you who were missing an "initrd" line in the grub menu.lst do not have a postinst_hook line in /etc/kernel-img.conf. If this is the case, can you please tell me your install/upgrade history?

That issue is discussed in [https://bugs.edge.launchpad.net/bugs/156058](https://bugs.edge.launchpad.net/bugs/156058)

here's mine:
> 
do_symlinks = yes
relative_links = yes
do_bootloader = no
do_bootfloppy = no
do_initrd = yes
link_in_boot = no

no postinst_hook line

I did an online upgrade to gutsy...The system was fully updated beforehand, although I noticed it replaced my nvidia-glx-new driver (9762?) with a newer version (100.14.19).  The initrd glitch was the only major problem (but several other minor ones)

---

### Post by tormod on 2007-10-31
> **logos34 said:**
> 
I did an online upgrade to gutsy...The system was fully updated beforehand

Please give the whole history, e.g was it installed from scratch with Feisty?

---

### Post by logos34 on 2007-10-31
> **tormod said:**
> Please give the whole history, e.g was it installed from scratch with Feisty?

Yes, fresh install of 7.04.  This is my first upgrade experience.  I'm not sure what other info you want...

---

### Post by tormod on 2007-11-01
> **logos34 said:**
> Yes, fresh install of 7.04.  This is my first upgrade experience.  I'm not sure what other info you want...
Did you install using the 7.04 Desktop CD or using the Alternate install cd? Any particularities like raid or lvm? I would like to find out under which conditions people can end up without the postinst_hook.

---

### Post by JeTDoG on 2007-11-02
I've got a problem that this thread seems most able to address, insofar as I'm getting the same type of kernel panic when trying to boot 7.10 with the 2.6.22-14 kernel.

This system, a Toshiba A105-S2712 laptop, was originally running XP Home. I installed Wubi 7.04 with the 2.6.20-15 kernel, upgraded to -16, and then converted the Wubi install to a full partition-based install via LVPM. Everything up until then was flawless, so I decided to go for the 7.04 -> 7.10 upgrade via the Update Manager.

Everything seemed to go fine, albeit slowly, until the upgrade hung hard during the cleanup stage, while removing gaim. Against my better judgment, but having no other option, I restarted my X session, and when I got what appeared to be a newer login window, everything seemed good. When my session told me I needed to reboot to complete my installation, everything seemed even better. When I rebooted and got the kernel panic, that told me something was wrong.

After gathering my wits and realizing I could still boot into the earlier kernels, I did some poking around. My kernel listings in menu.lst are:

title Ubuntu 7.10, kernel 2.6.22-14-generic
root (hd0,2)
kernel /boot/vmlinuz-2.6.22-14-generic
root=UUID=b53a6c82-6c26-4a98-8181-a3e66ab5c2e0 ro quiet splash
quiet

title Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)
root (hd0,2)
kernel /boot/vmlinuz-2.6.22-14-generic
root=UUID=b53a6c82-6c26-4a98-8181-a3e66ab5c2e0 ro single

title Ubuntu 7.10, kernel 2.6.20-16-generic
root (hd0,2)
kernel /boot/vmlinuz-2.6.20-16-generic
root=UUID=b53a6c82-6c26-4a98-8181-a3e66ab5c2e0 ro quiet splash
initrd /boot/initrd.img-2.6.20-16-generic
quiet

title Ubuntu 7.10, kernel 2.6.20-16-generic (recovery mode)
root (hd0,2)
kernel /boot/vmlinuz-2.6.20-16-generic
root=UUID=b53a6c82-6c26-4a98-8181-a3e66ab5c2e0 ro single
initrd /boot/initrd.img-2.6.20-16-generic

title Ubuntu 7.10, kernel 2.6.20-15-generic
root (hd0,2)
kernel /boot/vmlinuz-2.6.20-15-generic
root=UUID=b53a6c82-6c26-4a98-8181-a3e66ab5c2e0 ro quiet splash
initrd /boot/initrd.img-2.6.20-15-generic
quiet

title Ubuntu 7.10, kernel 2.6.20-15-generic (recovery mode)
root (hd0,2)
kernel /boot/vmlinuz-2.6.20-15-generic
root=UUID=b53a6c82-6c26-4a98-8181-a3e66ab5c2e0 ro single
initrd /boot/initrd.img-2.6.20-15-generic


so, as you can see, no initrd line for the 2.6.22-14 kernel. However, on investigating the contents of /boot, I see initrd.img's for the older kernels, but none for the .22-14 kernel. Also, the contents of my /etc/kernel-img.conf are identical to logos34, i.e., no postinst_hook. So, my questions are these:

Can I somehow generate an initrd for the newest kernel? I do have file sitting in /boot that is just called initrd

Barring that, what would it take to remove and reinstall the new kernel?

Go easy on me, I'm a complete n00b (which is why I'm posting here).

---

### Post by tormod on 2007-11-04
> **JeTDoG said:**
> 
so, as you can see, no initrd line for the 2.6.22-14 kernel. However, on investigating the contents of /boot, I see initrd.img's for the older kernels, but none for the .22-14 kernel. Also, the contents of my /etc/kernel-img.conf are identical to logos34, i.e., no postinst_hook. So, my questions are these:

Can I somehow generate an initrd for the newest kernel? I do have file sitting in /boot that is just called initrd

 sudo update-initramfs -u -k 2.6.22-14-generic
 sudo update-grub

And add the postinst hooks to /etc/kernel-img.conf to avoid future trouble.

---

### Post by JeTDoG on 2007-11-04
tormod, thanks for your reply; unfortunately, the plot thickens...

while trying to correct an unrelated problem with my swap partition not mounting (due to an incorrect UUID, now fixed), I discovered that I can't run the update-initramfs because I have no initramfs-conf....

I ain't givin' up yet....

---

### Post by tormod on 2007-11-04
You can try reinstalling initramfs-tools:
 sudo apt-get install --reinstall initramfs-tools
but if it's seriously messed up you should consider a full clean install. Make sure you don't run out of disk space.

---

### Post by JeTDoG on 2007-11-04
I was kind of afraid of that...

I had already tried the reinstall, both via Synaptic and apt-get, no dice

since everything else appears to be working fairly well under the earlier kernel version, I'm tempted to just stay there for now... so, shifting gears, how can I safely remove the 2.6.22-14 kernel?

---

### Post by tormod on 2007-11-04
> **JeTDoG said:**
> I was kind of afraid of that...

I had already tried the reinstall, both via Synaptic and apt-get, no dice?

Did you use --reinstall? If you otherwise run 7.10, you should try to get 2.6.22 working.

---

### Post by JeTDoG on 2007-11-04
yes, ran the command line exactly as you typed it... I agree, based on comments I've seen, it's to my advantage to get 2.6.22-14 running, I just need to figure out how...

anyone else care to weigh in on the best (non-destructive) way to remove a kernel?

---

### Post by tormod on 2007-11-05
sudo apt-get remove --purge linux-image-2.6.22-14-generic
removes the kernel package like any other package.

However, /etc/initramfs-tools/initramfs.conf belongs to the initramfs-tools package, so maybe you should try to purge that package and install it again.

---

### Post by JeTDoG on 2007-11-05
thanks, I'll give that a shot after I have everything in /home backed up and burn a current ISO of the latest dist... probably won't be until this weekend or later, but I'm in no hurry

---

### Post by speedyfs on 2007-11-06
I was having the same problem. I selected the Ubuntu 7.10, Kernel 2.6.15-23-386 (recovery mode). Then I typed dpkg --configure -a  It seemed to have fixed my kernel panic problem.

---

### Post by marcfell27 on 2008-01-23
> **jr.gotti said:**
> Pop in the live CD...when it boots open a terminal, and remount your root partition.

sudo mount /path/to/root/partition /

then sudo grub-install hd0,0

reboot, and youll be good.

How to find  "/path/to/root/partition /" when using live CD.

---

### Post by sml on 2008-01-26
How do these sorts of basic problems occur with our supposedly best linux distro challenger competing against Microsoft and Mac.

Surely the package(s) goes through testing & unstable stage trials first before being promoted to current?

Lucky I wasn't successful suggesting a few of my friends move to linux. They would be giving up very quickly.

---

### Post by tormod on 2008-01-27
Don't feed the troll, but:
This thread has a bunch of different issues from different users and configurations. Many of the suggestions are random and not relevant to the issues, especially to the original poster's issues. There are no "basic problems" here, some are caused by overfilled file systems or disk failures at a very unlucky moment, some by home-made kernel packages.

I would suggest to close this thread or at least stop posting to it. Please open new threads if you still have any issues, and describe in detail what the symptoms are, verbatim error messages and the history of your installation. You can add a link here, so that subscribed people can follow your new thread if they want. Thanks!

---

### Post by sml on 2008-01-27
Fair point.

I just had a vanilla 7.10 kubuntu install. A week later ran the update manager. That destroyed everything with the kernel panic not syncing unable to mount root fs etc etc error message ... and have wasted 6 hours trying to get it back it on track. I think simple distro like Arch are much better and easier to resolve problems. Ubuntu tries to be clever which is great but when things go wrong, I am in a pickle! Yet again, I think I will go back to Arch.

Sorry. Just a bit frustrated today. I like (K)ubuntu with a fresh install ... but about half-a-dozen times now I have being snagged with the ubuntu updates :(  I occassionally have problems with arch updates syncing with testing or unstable but at least they are easily fixed.

---

### Post by sml on 2008-01-27
For those who are having similar problems here is a solution ..... I gave up troubleshooting to get Kubuntu going again ... so my intent was to recover my data then move back to Arch. To do this, I tried to find a live cd that I could boot toram then burn my data on dvd, then re-format.

Tried
knoppix 5.1 - could not burn a good dvd
puppy 3.01 - ok burning isos but not dvd data
PCLinuxOS TR3 - failed booting toram
PCLinuxOS miniMe  - no cd/dvd burning software.
Slax 6 rc10 - could not graphics going
Kubuntu/Ubuntu/Mint - cannot boot toram

Next plan ....  GParted Live .... :)  Yippeee .. can save on burning dvds! I will just re-shuffle all my data!

---

