---
title: "[SOLVED] Moving ubuntu from usb HD to internal HD"
date: 2008-02-05
forum: Absolute Beginner Talk
---

### Post by Blue Sassley on 2008-02-05
I have ubuntu installed and running completely on a external USB HD (GRUB too) I want to know what I need to do after I resize my internal partition and copy my ubuntu partition to the internal HD how do I move GRUB and also what do I need to edit so I can dual boot?

Thanks for the help,
Blue

PS when I did my install of ubuntu I removed my internal HD because I didn't want to have GRUB installed there well I was playing around, but now I fell in love with ubuntu and I want it to be running as a dual boot on the same drive.

---

### Post by bodhi.zazen on 2008-02-05
You should manage your partitions from a live CD.

You can use gparted to resize / move the partition, and afterwards install grub to your MBR.

Last you need to edit /etc/fstab and possible /boot/grub/menu.lst

See this thread for hints : [http://ubuntuforums.org/showthread.php?t=316237](http://ubuntuforums.org/showthread.php?t=316237)

And for grub : [uwiki]RecoveringUbuntuAfterInstallingWindows[/uwiki]

post if you get hung up ...

---

### Post by Blue Sassley on 2008-02-05
I understand what /boot/grub/menu.lst is, but what is /etc/fstab and I'm running Windows XP so I'm thinking I would be able to just use the Live CD to get GRUB installed via terminal?

Thanks,
Blue

---

### Post by bodhi.zazen on 2008-02-05
/etc/fstab is the configuration file in Ubuntu that dictates where partitions are mounted. As you are changing your root partition you need to edit the file manually.

[http://ubuntuforums.org/showthread.php?&t=282018](http://ubuntuforums.org/showthread.php?&t=282018)

[http://ubuntuforums.org/showthread.php?&t=283131](http://ubuntuforums.org/showthread.php?&t=283131)

---

### Post by Blue Sassley on 2008-02-05
Ok my last question is I have resized my windows partition and now I have 40GB open for ubuntu in the middle of my HD how can I move /dev/sda5 to the end of my windows partition so ubuntu gets the very end of the drive? Do I have to make it fill the whole area and then shrink it? to get it to move to the end of the windows partition?

Thanks for all the help!
Blue

---

### Post by bodhi.zazen on 2008-02-05
My guess is to resize your extended partition first ( sda3) , then move sda5.

---

### Post by Blue Sassley on 2008-02-06
Well I'm totally lost I did get GRUB loaded but course none of the ubuntu listings worked just gave me an error (sorry I don't remember what it was) I do have a screen of my layout with my ubuntu install copied over to the internal HD, I cheated for now and put the Windows boot loader back in place just so my computer is not a doorstop. Can you give me a detailed list of what I need to do as most of everything you linked me to seems very foreign to me. I can tell you when I tried to open the /boot/grub/menu.lst in a editor (nano) it was just a blank "new file" I'm guessing I wasn't opening the right thing.

Thanks,
Blue

---

### Post by bodhi.zazen on 2008-02-06
Boot the live CD

Now, lets check your menu.lst :

```
sudo mkdir /media/ubuntu
sudo mount /dev/sda4 /media/ubuntu
gksu gedit /media/ubuntu/boot/grub/menu.lst
```

Make sure in the Ubuntu Stanzas you have :

1. In the options section,

> ## ## Start Default Options ##
## default kernel options
## default kernel options for automagic boot options
## If you want special options for specific kernels use kopt_x_y_z
## where x.y.z is kernel version. Minor versions can be omitted.
## e.g. kopt=root=/dev/hda1 ro
##      kopt_2_6_8=root=/dev/hdc1 ro
##      kopt_2_6_8_2_686=root=/dev/hdc2 ro
# kopt=root=UUID=xxx-yyy-zzz ro

Unlike other config files , comments are ##
# single = configuration options.

make sure the kopt=root=UUID line points to your ubuntu partition.

You can list your uuid in the terminal:
```
blkid
```

Or change to:
#      kopt=root=/dev/sda4 ro


In your Ubuntu stanzas, check the partition as well :
**root (hd0,3)**
kernel vmlinuz-xxx.yyy.zzz **root=/dev/sda4** bla bla bla

OR kernel vmlinuz root=UUID=xxx.yyy.zzz

Last, check your windows stanzas.

Save your changes to /media/ubuntu//boot/grub/menu.lst

======

Confirm /etc/fstab

```
gksu gedit /media/ubuntu/etc/fstab
```

Again make sure your root partition ( / ) is correct, either using uuid or /dev/sda4 in the first column

======

Install grub to your MBR :

```
sudo grub
```

That will give you a grub prompt,

> grub >

At the grub prompt :

```
root (hd0,3)
setup (hd0)
quit
```

reboot & you should be good to go.

---

### Post by Blue Sassley on 2008-02-06
Ok thanks for the step by step, I will try that later today or tonight! Also thanks for pointing out the comments thing that was also screwing me up as I was only looking at lines that didn't have any # at the beginning.

Thanks,
Blue

---

### Post by Blue Sassley on 2008-02-06
I just finish following everything gave me and it worked perfectly! Although in FSTAB I did comment out my swap partition, I have 3.5GB of RAM available so I though I would run with out one for now. I also search through the other links you gave me and added the Windows boot option to my menu so I am able to work for a living :p

I did have one problem after I made all the changes and rebooted to the drive all worked great, then I applied 4 updates "linux headers" I think and after I rebooted I got a code 17 error in GRUB so I rebooted again and got on the Live CD and doubled checked everything and found in the menu.lst file the Windows stuff was removed and the "root (hd0,3)" was changed back to "(hd0,0)". I donno what happened but I changed it again and saved it and now all seems to be working again and I was able to boot to both Windows and Ubuntu perfectly!

Oh and the other problem I had was that the "blkid" command for some reason would not give me the UUIDs for my internal HD it would only give me the IDs for my 3 external HDs, but since I copied the partition with Gparted they were never changed anyway.

Thanks for all your great help!
Blue

---

### Post by bodhi.zazen on 2008-02-07
You are most welcome, sounds as if you learned a little something in the process :)

---

### Post by Blue Sassley on 2008-02-07
Yeah I did, like I said I only came across those two problems and I don't know what happened there... now I need to find out how to make GRUB wait longer and also maybe how to reorder the GRUB menu... but I search that out later.

Thanks,
Blue

---

### Post by bodhi.zazen on 2008-02-07
Best GRUB guide :

[http://users.bigpond.net.au/hermanzone/p15.htm](http://users.bigpond.net.au/hermanzone/p15.htm)

---

### Post by Blue Sassley on 2008-02-17
Ok I seem to be having a problem when every time I get a kernel update after I restart my computer my GRUB menu.lst file keeps changing back to a (hd0,0) and I have to keep going in and changing back to (hd0,3) with a live cd... Have I missed a step? MY FSTAB stays and everything else stay it seem to just keep changing my menu.lst file... it also removes my Windows XP option I have that I put at the bottom of the list.

Thanks,
Blue

---

### Post by bodhi.zazen on 2008-02-18
One of the config lines in /boot/grub/menu.lst is off

> ## default grub root device
## e.g. groot=(hd0,0)
**# groot=(hd0,0)**

Or this one :

> ## ## Start Default Options ##
## default kernel options
## default kernel options for automagic boot options
## If you want special options for specific kernels use kopt_x_y_z
## where x.y.z is kernel version. Minor versions can be omitted.
## e.g. kopt=root=/dev/hda1 ro
##      kopt_2_6_8=root=/dev/hdc1 ro
##      kopt_2_6_8_2_686=root=/dev/hdc2 ro
**# kopt=root=UUID=xxx-yyy-zzz ro**

---

### Post by Blue Sassley on 2008-02-18
Ok well I checked it over I think think I dod miss this part:

> ## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,0)

So I changed that to:

> ## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,3)

So I'll find out the next time I get a kernel update.

Thanks again,
Blue

---

