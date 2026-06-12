---
title: "installation crashes"
date: 2006-10-09
forum: Absolute Beginner Talk
---

### Post by fromalk on 2006-10-09
Hello everyone,

I'm quite new to the linux scene, got a litle bit of experiance with fedora and red hat but that's everything and scince I wanted to try something new I turned to ubuntu.

Downloaded the iso file; ubuntu-6.06.1-alternate-i386.iso 
scince i run an itel duo core t2300. So far so good,
burned the cd, did some partitioning from out of windows xp:
80gb hard disk partitioned into:
54gb windows drive
16gb nfts drive to be formatted.

So booted up the cd, ran the memory test flawless, checked the disk which worked fine the system said and then tried tyo install it... 
Things wrent wrong really fast from then on.

When I got to the part to partition the drive, I entered the menu to do so myselves scince I didn't want ubuntu to take my entire hard drive. So i slitted the 16gb partition in a 15.1gb ext3 drive tagged with: '/' what for my understanding stands for root ?
And I then made a 900mb drive swap3 for the physical memory?
This should be fine right?

When I continue the instalaltion goes on  retrieves a number of files (somewhere in 84x) and after this is done it does install a the openofiice cores and few seconds after that it crashes,
my entire screen is black with 2 white/grey fields on in ](*,) 

My major concirn; Will the windows partitions till have it's data?
Cause I tried booting the hard drive again, and it tells me there is no operating system found :-k  

By the way, I configured both partitions I made for ubuntu as primary, hope that is ok to?

---

### Post by bluefrog on 2006-10-09
this reminds me of the following bug I had (since then I am using a livecd to install Ubuntu on this laptop)

[https://launchpad.net/distros/ubuntu/+bug/46643](https://launchpad.net/distros/ubuntu/+bug/46643)

if it is the same problem, the installation has not crashed, you just don't see the screen anymore. without windows on it, it wouldn't be a problem as hitting enter from time to time would do the trick, but with windows on you need to write where you want to put grub and if you have no install experience this is going to be a no-no for you.

Try installing from the livecd instead

James

---

### Post by fromalk on 2006-10-09
is it difficult to install windows later on? cause thze repartitioning has obvisouly removed every file on my notebook.
So 
I will now installubuntu on a clean system, leave a lot of gb's of space for windows and install it afterwards,

but how about the dualboot?

WIll it be easy to set up afterwards and will it take me a lot of time? 
Scince I need to be on the road again within a few hours ](*,)

---

### Post by bulldog on 2006-10-09
If you install Ubuntu before windows your grub will be lost.

But in about 10 minutes is it reinstalled with the live cd.

Here's how to do that.

This will restore grub if you already had grub installed but lost it to a windows install or some other occurence that erased/changed your MBR so that grub no longer appears at start up or it returns an error.


Boot into the live Ubuntu cd. This can be the live installer cd or the older live session Ubuntu cds.

When you get to the desktop open a terminal and enter. 


```
sudo grub
```


This will get you a "grub>" prompt (i.e. the grub shell). At grub>. enter these commands


```
find /boot/grub/stage1
```

This will return a location. If you have more than one, select the installation that you want to provide the grub files.
Next, THIS IS IMPORTANT, whatever was returned for the find command use it in the next line (you are still at grub>. when you enter the next 3 commands)


```
root (hd?,?)
```

Again use the value from the find command i.e. if find returned (hd0,1) then you would enter root (hd0,1)

Next enter the command to install grub to the mbr


```
setup (hd0)
```

Finally exit the grub shell


```
quit
```

---

### Post by x64Jimbo on 2006-10-09
Install Windows first so that it thinks it's the only OS on your computer.
Install it on a smaller partition. 
Next, get the Alternate Install CD. If you have errors installing from the LiveCD, the Alternate is designed to help with that.

---

### Post by fromalk on 2006-10-09
aren't i allready installing from the alternate cd?
ubuntu-6.06.1-alternate-i386.iso

even now that i'm trying without windows it still crashes ](*,)

---

### Post by lemonsCC on 2006-10-09
You may want to look at this site.  It has amazing detail and tells EVERY step to dual boot.  [http://www.hezardastan.org/breezy_xp_dualboot/en/]("http://www.hezardastan.org/breezy_xp_dualboot/en/")

---

### Post by fromalk on 2006-10-09
So I got ubuntu running finally, and I just need to install gparted now.
Scince I have no experiance what so ever with the terminal I did some searching and found this code:

cd /tmp
#unpack the tarball:
tar -xjf gparted-x.y.tar.bz2
cd gparted-x.y/
./configure --prefix=/usr
make
su -
make install
# that's all. Problems may arise if you haven't the right dependencies

all seems to go well untill i type 'su -'
it prompts me for my pasword, when I enter it it returns an error :-? 
LAst try I got it right but it still wont do the 'make isntall' command:

stijn@ubuntustijn:~$ make install
-su: make: command not found
stijn@ubuntustijn:~$


Hope someone can give me a quick hand here? :-k

---

### Post by gn2 on 2006-10-09
Perhaps try installing with Synaptic instead?

---

### Post by x64Jimbo on 2006-10-10
Definitely use the synaptic package manager to install your programs. Linux isn't windows - you rarely ever need to download an installer from within your web browser.

---

