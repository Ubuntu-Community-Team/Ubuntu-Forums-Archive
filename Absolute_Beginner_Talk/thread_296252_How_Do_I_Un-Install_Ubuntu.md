---
title: "How Do I Un-Install Ubuntu?"
date: 2006-11-09
forum: Absolute Beginner Talk
---

### Post by Neo_Angelo on 2006-11-09
Heya guys, i was wondering, i'm having problems with running linux programs and i wish to unistall and re-install ubuntu and try to set it up again from scratch. i'm running the 6.06 LTS distro and was wondering what i need to do to remove ubuntu so i just have my windows XP OS again, then i'll install it again and try and follow the guides to setting it up as i think i might have broken linux (ha ha).

---

### Post by hotbrainz on 2006-11-09
Just put in the XP CD and install and wallah it will make sure it destroys evrything else in the system :)

---

### Post by bulldog on 2006-11-09
If it's broken beyond repair just delete the ext3 and your swap.

If you just want to reinstall on the same partitions just format them and reinstall.
To remove GRUB you have to use the windows install cd and go to the recovery console where you can use fixboot and/or fixmbr.

That should do it

---

### Post by mo79 on 2006-11-09
> **Neo_Angelo said:**
> Heya guys, i was wondering, i'm having problems with running linux programs and i wish to unistall and re-install ubuntu and try to set it up again from scratch. i'm running the 6.06 LTS distro and was wondering what i need to do to remove ubuntu so i just have my windows XP OS again, then i'll install it again and try and follow the guides to setting it up as i think i might have broken linux (ha ha).

A reinstallation for such problems might be like using a truck to crush a walnut, but if you desire...

I'm assuming you have XP and Ubuntu on the same drive, you can use [GParted]("http://gparted.sourceforge.net/") to delete the Ubuntu partitions (typically just root and swap). You will the need to put in your Windows XP CD on boot up and enter the recovery console to fix the master boot record for just XP. I believe the command is Fixmbr. It can be found searching the forum.

---

### Post by mo79 on 2006-11-09
Bugger. I hate being late. :rolleyes:

---

### Post by LLRNR on 2006-11-09
Hi Neo_Angelo, I had somekind of a same problem - when I installed Ubuntu the first time, I let it have a default minimum partition of 2 gb, and then I soon ran out of space, as you can figure. So I thought I had to re-install it, so I firstly grabbed the XP install cd and from the recovery console i typed **fixmbr** that's for restoring the MBR i.e. to get rid of GRUB. And the second thing to do is to pop in the install CD and I let it do its job - mainly I reconfigured my partitions, I reformatted them and everything went on well the second time (be AWARE of what you're doing, you don't want to format your data partition...)

HTH,

LLRNR

EDIT : Whoops sorry others posted before me :P

---

### Post by Neo_Angelo on 2006-11-09
thanks guys, is there a was of re-installing ubuntu without uninstalling, it....like when you overwrite it something? if so how? i'm not really an expert with partitioning and i'm completly new to installing new OS's thanks for your quick responces.

if there isn't a way to overight the settings. is there a way to restore all the files that were on the disc?

i also think what i did wrong when i installed ubuntu was i think i used ALL the memory i had left to install it. i clicked on Use available memory to install (or something somilar).

i really hope i can get this sorted as i really like ubuntu.

---

### Post by CatKiller on 2006-11-09
> thanks guys, is there a was of re-installing ubuntu without uninstalling, it....like when you overwrite it something?

When you go through the install process, you'll have the option of formatting the partitions Ubuntu will be installed on. Do this.

---

### Post by Neo_Angelo on 2006-11-09
okay i will do.....ok i think i've come across a problem. the installation CD for windows doesn't want to work....though i'll keep trying it.

thank you very much for all your help. *suscribes to this for future reference*

---

### Post by TheRingmaster on 2006-11-09
please just tell us your problem and we can help you more.

---

### Post by bulldog on 2006-11-09
> **Neo_Angelo said:**
> okay i will do.....ok i think i've come across a problem. the installation CD for windows doesn't want to work....though i'll keep trying it.

thank you very much for all your help. *suscribes to this for future reference*

If you reinstall Ubuntu you don't have to remove GRUB.
You only do that if you don't want to use Ubuntu anymore,and why should you want to do that?:D

---

### Post by Neo_Angelo on 2006-11-09
well currently my problem is, i think i allowed way to much memory for linux to be installed on.

the second issue is i cannot access any of the features on SYSTEM drop down menu on the descktop. so without an internet connection linux on my PC is useless. my third problem is trying to set up my wireless card. people told me that linux would automatically detect cards and set up connections. but my linux doesn't appear to find my Router nor detect my wireless card. also the installation CD for the wirless card only has an .exe setup file to which ubuntu can't read it. so i wish to unistall linux and start over with everyones help ^_^

EDIT: How do i re-install ubuntu without removing GRUB. and with the re-install can i set the partitions up again as i think i gave too much memory for linux to run from (my HDD is 200GB of which only 45GB is used from data and windows XP)

---

### Post by bulldog on 2006-11-09
You can download the Gparted live cd [aprox 25MB] and boot from it.
You can resize your partitions to suit your needs.

[http://sourceforge.net/project/showfiles.php?group_id=115843&package_id=173828](http://sourceforge.net/project/showfiles.php?group_id=115843&package_id=173828)

If done,pop in the Ubuntu cd and boot from it.
When you come to the partitioner just mount the partitions you've made with the gparted live cd.

Some tips,
Create a 10GB /  (root) partition.
Create a  1GB swap partition.
Create a  /home to your needs.

---

### Post by Neo_Angelo on 2006-11-09
ok, i don't have a cd burner to burn that CD :(. and i'm useless at setting up partitions....if you wouldn't mind. would you write me a simple guide on how to set ubuntu up right partition wise?

thanks for your patience as i'm a complete n00b and haven't got a clue about some of the things. i'm glad you lot have a lot of patience with someone like myself.

---

### Post by bulldog on 2006-11-09
If you gonna do it from the live cd just throw away all the **non windows** partitions.
You will have a lot of free unallocated space then [besides your windows]

Now right click the unallocated space and choose new partition.
Make a / partition about 10GB [it counts in mb so multiply 1024 x 10]
Make it bootable if this option is given.
Make a swap 1GB the same way you made your /
Then decide how big your /home should be and create it the same as before.

The remaining free space you can make a NTFS partition for data or make a small FAT32 partition to exange data between windows and linux.
Keep in mind Ubuntu can't write to a NTFS partition by default.
Now you should be able to install Ubuntu again.

---

### Post by Neo_Angelo on 2006-11-09
ok, i have partition magic from norton, so will this be ok to edit/add partitions?

and when setting up a /home partition what is that for? and how much memory should i allocate to it?....with this method include dual boot to?

---

### Post by bulldog on 2006-11-09
Don't use Partition Magic,just use the live cd or the alternate cd which ever you prefer.

Boot it and hit the install button.
Then answer the simple questions and it goes to the partitioner.

Here you see your existing partitions including your windows.
Now delete your ext3 and if you want your swap.

Now you have a lot of unallocated space next to your windows [if this is installed ofcourse]

Now create as I described before.

Your /home partition will allow you, when you do a reinstall,to keep all the data which is stored there.
It's usefull to do this this way.
How big it should be is for you to decide.

---

### Post by Neo_Angelo on 2006-11-09
right ok, i'm a little confused as to when you said boot the live CD. by that you mean the ubuntu CD i got sent? or do you mean the .iso file i downloaded from the link you gave me?

---

### Post by bulldog on 2006-11-09
Well if you got the Gparted live cd and burned it to cd you can use that one instead to partition your hdd.
It's more easy to use then the partitioner on the live ubuntu cd.

If you made your partitions to your liking with Gparted live cd,then you can fire up the Ubuntu live cd and install Ubuntu.
You just mount the partitions you created at the right place and of you go.

Some note to take care of.
If you want to give space to your existing windows partition,you should choose the amount of free space on forehand,and make sure to have this space **before** your Ubuntu partitions.
It makes things easier when you want to add space to your windows partitions,if not forget this.

---

### Post by scc4fun on 2006-11-09
> **Neo_Angelo said:**
> people told me that linux would automatically detect cards and set up connections. but my linux doesn't appear to [...] detect my wireless card. also the installation CD for the wirless card only has an .exe setup file to which ubuntu can't read it. so i wish to unistall linux and start over with everyones help ^_^

Neo_Angel, when you put in the Ubuntu Live CD did your wireless card work then? If not then you may need ndiswrapper or madwifi... or firmware and a driver from the manufacturer of your wireless card. You didn't say what model it is.

> **Neo_Angelo said:**
> EDIT: How do i re-install ubuntu without removing GRUB. and with the re-install can i set the partitions up again as i think i gave too much memory for linux to run from (my HDD is 200GB of which only 45GB is used from data and windows XP)

To re-install Ubuntu without removing GRUB you just need to put in the Live CD (or alternate CD if you have that) and go through the installation steps--being sure to reformat your Linux partitions as others have advised. You don't need to use the fixboot or fixmbr from the Windows XP CD if you want to keep GRUB.

---

### Post by Neo_Angelo on 2006-11-09
ahh i see, i get you now, thank you for you help. now all i need is a CD burner lol! (yeah my PC doesn't have one....suprise suprise).

i'll go buy one tommorow. thanks again for your help its much appreciated!

---

### Post by bulldog on 2006-11-09
> **Neo_Angelo said:**
> ahh i see, i get you now, thank you for you help. now all i need is a CD burner lol! (yeah my PC doesn't have one....suprise suprise).

i'll go buy one tommorow. thanks again for your help its much appreciated!

You can do all what I said with the Ubuntu live cd,you only have to read carefully what you're going to do,and all should be fine.

---

### Post by Neo_Angelo on 2006-11-09
> **scc4fun said:**
> Neo_Angel, when you put in the Ubuntu Live CD did your wireless card work then? If not then you may need ndiswrapper or madwifi... or firmware and a driver from the manufacturer of your wireless card. You didn't say what model it is.



To re-install Ubuntu without removing GRUB you just need to put in the Live CD (or alternate CD if you have that) and go through the installation steps--being sure to reformat your Linux partitions as others have advised. You don't need to use the fixboot or fixmbr from the Windows XP CD if you want to keep GRUB.

ok, and the the problem is i have no idea what manufacturer made my wireless card since i threw away the box since i didn't think i'd need it. and no the wireless didn't work when i initially started, the CD i have to install the wireless driver etc has only an .exe file so won't work with linux. do you have any idea's as to what i can do?

---

### Post by scc4fun on 2006-11-09
> **Neo_Angelo said:**
> ok, and the the problem is i have no idea what manufacturer made my wireless card since i threw away the box since i didn't think i'd need it. and no the wireless didn't work when i initially started, the CD i have to install the wireless driver etc has only an .exe file so won't work with linux. do you have any idea's as to what i can do?
You could use ndiswrapper with the windows driver. I believe ndiswrapper is on the Live CD if you look for it. You should look in Windows XP to see what type of wireless card you have and also to see what driver it uses. Then copy the driver to a floppy disk or thumb drive.

---

### Post by Neo_Angelo on 2006-11-09
ok i'll attempt to do that, thank you very much for your help. once i do that where do i put these drivers and how do i use the ndiswrapper? i'm even worse at command lines that partitioning lol.

---

