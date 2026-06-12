---
title: "[SOLVED] ubuntu does not want to load"
date: 2007-09-01
forum: Absolute Beginner Talk
---

### Post by lunamystry on 2007-09-01
I decided to try different linux distros today and i had an openSUSE DVD and I decided what better place to start than there. I have two hard drives and I wanted to install SUSE on the smaller of the two which was running GUSTY gibbon. I tried to install and unlike ubuntu SUSE did not give me an option of where do I want to install the new OS. I then aborted the installation thinking there was something i missed, but on the install summary there was still no option to install on the smaller hard drive. I then remembered something  i read in a thread one time that the best way to dual boot would be to install the new OS separately and then Ubuntu would recognize it. I decided to do that. I turned off the PC removed the one hard drive then turned it on again and installed SUSE. it installed nicely and worked fine. I then decided to watch a movie to celebrate, so log out and login to ubuntu. Grub suddenly had openSUSE on it and it did not have ubuntu listed. I restarted the PC and still nothing, I turned off the PC and disconnected the hard drive with SUSE and tried to boot again and I got Grub error 21. I logged in to SUSE and used konsole to and typed 

sudo mkdir /media/ubuntu ( which i use to mount my hard drive for the first time in ubuntu)

and:

sudo mount /dev/sda1 /media/ubuntu

and nothing came up when I went to the /media/ubuntu/homefolder. The other stuff appears to be there but no music, documents nothing that i saved. only the root folder. 

Will I be able to save my ubuntu installation or is it gone forever or should I go find a SUSE forum?

---

### Post by southernman on 2007-09-01
Can you please repost the problems your having and break it down a little more. I've read your post a few times and still confused as the first time.

Thanks...

---

### Post by lunamystry on 2007-09-01
I installed openSUSE now ubuntu does not want to boot. I get error 21 when I try to boot ubuntu. 

(WOW i really broke it down.)

---

### Post by southernman on 2007-09-01
> **lunamystry said:**
> I installed openSUSE now ubuntu does not want to boot. I get error 21 when I try to boot ubuntu. 

(WOW i really broke it down.)
[http://www.google.com/search?hl=en&client=firefox-a&rls=com.ubuntu%3Aen-US%3Aofficial&hs=5Ka&q=error+21+ubuntu&btnG=Search]("http://www.google.com/search?hl=en&client=firefox-a&rls=com.ubuntu%3Aen-US%3Aofficial&hs=5Ka&q=error+21+ubuntu&btnG=Search")
Me too! ;)

Good Luck

---

### Post by meierfra on 2007-09-01
Let's first see what is on  your hard drive. Plug in all your hard drives.
Open a terminal in suse. Type


```
su
```

to become root. Type

> fdisk -l 
and post the out put.

---

### Post by meierfra on 2007-09-01
In ubuntu, do  you have \home on a separate partition?

---

### Post by lunamystry on 2007-09-01
> **meierfra said:**
> Let's first see what is on  your hard drive. Plug in all your hard drives.
Open a terminal in suse. Type


```
su
```

to become root. Type


and post the out put.

Okay that was cool. Seeing what is on my hard drives like that

```
dhcppc11:/home/lunamystry # fdisk -l

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        2611    20972826   83  Linux
/dev/sda2            9546        9729     1477980    5  Extended
/dev/sda3            2612        9545    55697355   83  Linux
/dev/sda5            9546        9729     1477948+  82  Linux swap / Solaris

Partition table entries are not in disk order

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       19273   154810341   83  Linux
/dev/sdb2           19274       19457     1477980    5  Extended
/dev/sdb5           19274       19457     1477948+  82  Linux swap / Solaris

```

---

### Post by meierfra on 2007-09-01
On which drive is Suse? sda (80GB) or sdb (160 GB)?

---

### Post by lunamystry on 2007-09-01
> **meierfra said:**
> In ubuntu, do  you have \home on a separate partition?

No, i was gonna create one but then I decided since I have two hard drive and I can access them both, I would make the one sort of my home partition and then the other one is where i install and play with anything new that I want to try out.

---

### Post by meierfra on 2007-09-01
> ]but no music, documents nothing that i saved. only the root folder. 

Was your music and documents on the hard drive you installed Suse on?

---

### Post by lunamystry on 2007-09-01
> **meierfra said:**
> On which drive is Suse? sda (80GB) or sdb (160 GB)?

SUSE should be on /sdb 

Question, the sdb thing, is to do with where i connected the hard drive on the motherboard? I have four slots for hard drives and I think I connected them the way that I had connected them when I installed gusty before and gusty was on the 80GB sdb drive.

---

### Post by lunamystry on 2007-09-01
> **meierfra said:**
> Was your music and documents on the hard drive you installed Suse on?

No, there were some but since I knew they would be deleted, I copied all the important stuff to the other hard drive.

---

### Post by Inxsible on 2007-09-01
> **meierfra said:**
> Let's first see what is on  your hard drive. Plug in all your hard drives.
Open a terminal in suse. Type


```
su
```to become rootI would say that's a bad idea. You should use  ```
 sudo fdisk -l
``` that way your root privilege is only for that one command thereby decreasing your chances of screwing up some system file.

```
su
``` gives you root privs for the entire session. NOT A GOOD IDEA !

---

### Post by southernman on 2007-09-01
+1 What inxsible said.

To escape the root session just use "exit"

---

### Post by meierfra on 2007-09-01
> I would say that's a bad idea. You should use

He is working on suse. No such thing as "sudo" on suse.

---

### Post by meierfra on 2007-09-01
My bad. I  thought suse does not have "sudo"

What is on your sda3 partition? Do 

```
 sudo mkdir /media/sda3
```

```
sudo mount /dev/sda3 /media/sda3
```

Maybe your data is there?

---

### Post by lunamystry on 2007-09-01
> **meierfra said:**
> My bad. I  thought suse does not have "sudo"

What is on your sda3 partition? Do 

```
 sudo mkdir /media/sda3
```

```
sudo mount /dev/sda3 /media/sda3
```

Maybe your data is there?

/dev/sda3 has my SUSE home folder.

---

### Post by meierfra on 2007-09-01
Actually I have suse 10.2 installed and I just tested it. "sudo fdisk -l" gives command not found. 
su followed by "fdisk -l" works

---

### Post by meierfra on 2007-09-01
Maybe ubuntu is on sdb. 

mount sdb1 and see wants in there.

---

### Post by lunamystry on 2007-09-01
> **meierfra said:**
> Maybe ubuntu is on sdb. 

mount sdb1 and see wants in there.

IT WAS!! Thank you vey much eveybody. and tihis means that the place you connect the hard drive to matters then because i checked the hard drive connections and I had the ubuntu hard drive on the 'back' slot rather than whwere I usually connect it.

I think to solve the boot problem i will have to go to the SUSE forum as now i think it is SUSE not recognising Ubuntu. Thank you everyone for the help. 

:guitar:

---

### Post by meierfra on 2007-09-01
You just have to edit the "menu.lst" file. If you want I can tell you how to do it.

---

### Post by lunamystry on 2007-09-02
What menu.lst file? How do i get to it? :confused:

---

### Post by southernman on 2007-09-02
find it in /boot/grub/menu.lst

---

### Post by meierfra on 2007-09-02
The file is /boot/grub/menu.lst

Start by creating a backup


```
sudo cp /boot/grub/menu.lst   /boot/grub/menu.lst.backup
```


Open it

```
kdesu kate /boot/grub/menu.lst
```

(you can replace kate by your favorite editor)

The easiest way to edit the file is by copy and paste from your ubuntu menu.lst:

mount sdb1 as before (say to /media/sb1)

Open the file

```
kdesu kate  /media/sdb1/boot/grub/menu.lst
```

Look for something like this:


> title           Ubuntu, kernel 2.6.20-16-generic
root            (hd0,4)
kernel          /boot/vmlinuz-2.6.20-16-generic root=UUID=a6af4a0e-dd38-4b40-985d-e1e2f76fc5a3 ro quiet splash
initrd          /boot/initrd.img-2.6.20-16-generic
quiet
savedefault

title           Ubuntu, kernel 2.6.20-16-generic (recovery mode)
root            (hd0,4)
kernel          /boot/vmlinuz-2.6.20-16-generic root=UUID=a6af4a0e-dd38-4b40-985d-e1e2f76fc5a3 ro single
initrd          /boot/initrd.img-2.6.20-16-generic



Copy it and paste it in the 
 suse menu.lst file  just below something like this (but leave a blank line in between)


> title openSUSE 10.2
    root (hd0,7)
    kernel /boot/vmlinuz-2.6.18.2-34-default root=/dev/sda8 vga=0x317 resume=/dev/sda6 splash=silent showopts
    initrd /boot/initrd-2.6.18.2-34-default


Save the file and reboot. If you can't choose  to boot into ubuntu, come back here and post your suse menu.lst.

---

### Post by lunamystry on 2007-09-02
> **southernman said:**
> find it in /boot/grub/menu.lst

Which one do i edit? the ubuntu one or the suse one and what do i add or remove or delete. I saw a few things on the ubuntu menu.lst that I would like to delete and see what happens but that would risk loosing useful stuff i think. 

I attached my menu list.

---

### Post by meierfra on 2007-09-02
Correction:

You need to use "kdesu kate" instead of "sudo kate" ( assuming your are using kde, for gnome it would be "gksudo" instead of  kdesu)

(I fixed the previous post  accordingly)

---

### Post by lunamystry on 2007-09-02
lunamystry@dhcppc11:~> sudo kate /boot/grub/menu.lst
kate: cannot connect to X server

I cant open it, and when i open it via konquerer nothing appears in the file.

Would using```
kdesu konqueor 
```work?

---

### Post by lunamystry on 2007-09-02
Problem is I think some of the lines on the list are for when i was still using gusty gibbon and feisty and dual booting them. Should I copy all the lines or leave out the linux kernel 22 because they were for gusty and I installed SUSE on gusty.

Can i change the title to feisty instead of ubuntu,kerne... ?

The line that has root says has (hd0,0) and so does the SUSE line, will they not clash? should i change one of them to (hd0,1).

---

### Post by lunamystry on 2007-09-02
I did not work, error 15 is what i get when i choose to boot ubuntu.

---

### Post by meierfra on 2007-09-02
You are right all the way:

The (hd0,0) in the ubuntu part needs to be changed to (hd1,0).  Do this also  for the recovery mode. This should fix the errror 15. Sorry that I didn't realize that before hand.

Leaving out the kernel 22   part is fine , 

Changing the titel to feisty is  o.k, too.

---

### Post by lunamystry on 2007-09-03
Okay this is what happened since  my last post here: 
      I got irritated with trying to find a way to mount my usb as SUSE was not giving me an error everytime I tried to mount a CD or DVD or USB. I then inserted the install DVD and then chose the repair mode. I reckoned I would get a file system problem as my hard drive has somethng wrong with it. The repair went well i thought. even though there was a lot of stuff that was found like swaps that were wrong and stuff like that. I am not sure what i did but then when the repair was done I could not log into SUSE anymore. I had an assignement to finifsh by the way. I then decided i will give it a clean install. I installed it again and it still did not gave me an error when mounting the devices. I then took my Kubuntu gusty disc and i installed that on the SUSE and I worked fine. I was able to boot into my feisty again. 

I am going to try and install SUSE again tomorow (i like the colour when I choose operating systems) and maybe this time i'll read the instruction, Which i have never done for Ubuntu. I guess that may be because Ubuntu is made for Humans:)

What do i do to make sure that SUSE and does not try to install on the hard drive that has Ubuntu which is 160GB but install on the 80GB one?

---

