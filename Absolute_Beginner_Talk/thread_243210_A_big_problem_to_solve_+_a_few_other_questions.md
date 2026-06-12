---
title: "A big problem to solve + a few other questions"
date: 2006-08-24
forum: Absolute Beginner Talk
---

### Post by maccer on 2006-08-24
Hi, 

i started to use ubuntu about a week ago. I love it really, even though i spent more time fixing things than actually using it. Im a complete newb to linux, i only know a few UNIX commands because i use OS X a lot. So please be very straight forward and clear in ur solutions to my problems.

So, i have a big problem now: ubuntu freeses right after login and there is no way of getting out of its death, only to restart and either boot XP or OS X from GRUB (im triple booting by way). I choose, as always, to boot ubuntu when GRUB starts. No problem at all, all goes fine. The login screen comes in, fully operatable. I enter user name and password and it even logs me in... for about 5-10 seconds. Nautilus and the other system programs load and than it freeses. Im searching a solution that does not include reinstalling the system again as ive done it 3 times already ](*,)(once it was my mistake completely) Oh, the mysterious thing is, that i have done nothing with the system that should cause this. All i did was install avast! antivirus and adobe reader 7. 

Once i will be able to start up ubuntu, i would like to know if thers a way to change the default boot os in GRUB from ubuntu to XP. Unfortunately i need to use XP quite often so its more logical that way.

Another thing: i would like to know how to repair disk + folder permissions under linux/ubuntu. I tried some UNIX commands i got from darwin/UNIX under OS X but none worked. If there is an application that does it for me, the better.

Can linux recognize and make accessible hfs+ partitions? How? (wanna access OS X files from a separate HD)

There is a mac on my network and i want to share files with it  under linux (other oses work)When i go to network icon in my places menu i can see my mac but when i double click it its completely empty. Trust me, in real it isnt. (might be a permission issue?)

And the least important: is there a Program Files or Applications folder under ubuntu like under XP + OS X? If there is where to access it?


Sorry for the lengthy thred, i had all the questions in mind now so i thought i better ask now.

Tnx a great deal if u can help, especially with my first problem!!

---

### Post by LadyDoor on 2006-08-24
> Once i will be able to start up ubuntu, i would like to know if thers a way to change the default boot os in GRUB from ubuntu to XP. Unfortunately i need to use XP quite often so its more logical that way.

I *believe* that this option can be found in **/boot/grub/menu.lst** (note that that's an "ell" in **menu.lst**, not a one). So what you need to do is first BACK UP your **/boot/grub/menu.lst** file, and then open it with your favorite editor, using the "sudo" command to temporarily gain administrative privileges. In this example, I'll use **GNU Nano** because I saw somewhere on the forums that using the graphikal Gedit gives you an error.

Open up a terminal (I'm not sure which *buntu you're using, and the way to do this is a little different in each). Now copy-and-paste (minus the dollar sign):

```

$ sudo cp /boot/grub/menu.lst /boot/grub/menu.lst.bak
$ sudo nano -w /boot/grub/menu.lst

```

A few lines down, you will now see a line that looks something like this, after several lines starting with the number sign (#; in the **menu.lst**, these are "comments," or lines that the program ignores--they're there to make life easier for you):

```
default         0
```

We'll come back to this line. Now scroll down a little bit until you come across your kernels/operating system options. These will be lines that are NOT commented and which say things like this (but not *exactly* like this):

```

title           Ubuntu, kernel 2.6.15-26-386
root            (hd0,0)
kernel          /vmlinuz-2.6.15-26-386 root=/dev/hda3 ro quiet splash vga=792
initrd          /initrd.img-2.6.15-26-386
savedefault
boot

```

Somewhere in there, there should also be one that mentions Windows or OSX instead of Ubuntu. Now, go to the first block of lines in the list (you'll see what I mean). This is number 0. That's right, zero. The *next* one is #1, etc. Now, count from 0 until you find the one that says Windows (let's say it's number 666...not that I'm biased or anything ;-), and for serious not that the list is going to be anywhere *near* that long) or OSX. I should also mention that this entry may be before your Ubuntu entries, and may even be number 0. Now just replace the number in the **default** line with the number of the OS you want to boot.

I hope that helps and wasn't too confusing...if you have any questions, do ask. And, experienced users, if I got anything wrong be sure to let maccer (and me) know.

--Door

---

### Post by LadyDoor on 2006-08-24
P.S.:  Press control-o and enter to save the file, and control-x to exit nano.

--Door

---

### Post by maccer on 2006-08-25
thank you very much for ur reply, i can see u spent time with it and i apprechiate that :)

i will even be abel to try ur suggestions... when ill be able to boot into linux itself :p 

i thought that i needed to edit the menu.lst file... i had to edit it once already so that ubuntu recognizes OS X on the other HD, i was looking for the default boot option but couldnt find it than. But now i might find it

tnx a lot again! :)

---

### Post by maccer on 2006-08-25
oh by the way: i use Ubuntu 6.06

---

### Post by Crosbie on 2006-08-25
My guess is that it's your Antivirus program causing the problem.  (Do you really need an antivirus prog for Linux...?)  Can you log in to a different session (select it on the login screen) to test this?  I'm hoping that a different session won't startup your antivirus program.

If that doesn't work, someone'll have to suggest a command-line solution to disabling/uninstalling the prog... probably as simple as aptitude uninstall avast, or somesuch, but I'm really not sure. :)

---

### Post by Jerome36 on 2006-08-25
Ya', I was going to ask about Avast Antivirus.  Did this problem happen as soon as that was installed, and you had restarted, or shut-down and booted back up at a different time?  Perhaps Avast is causing your system to hang.

I use Avast in Windows XP, but never installed it in Linux.

---

### Post by maccer on 2006-08-26
Hi,

No, different sessions dont work :( grrr... I dont know why i installed avast... well i do actually: in windows i was having big problems with viruses once and since than i promised myself that i will protect my system, be it whatever, with an antivirus program. It was stupid i guess... so how can i uninstall?

By the way, strangely enough the failsafe session, which should not start any scripts at startup doesnt work either. Only one session works: the failsafe terminal session. So if someone gives me a way to uninstall in the terminal command line i can most likely do it.

Tnx all

---

### Post by LadyDoor on 2006-08-26
Did you install avast from source (./configure, make, sudo make install)? If so, do **sudo make uninstall** in the source directory. I didn't see it in the repos, but I might have missed it. If you installed from synaptic/apt, do **sudo aptitude remove --purge avast** (or whatever the *exact* packagename was).

Good luck!
--Door

---

### Post by maccer on 2006-08-27
You know what guys?

Ill just reinstall.............
I didnt know avast will cause me such great trouble so i didnt pay attention to the install process or anything. I dont remember the exact folder i installed to, nor the package name, nor what install method i used...

So problem number one out of the list is out. I "solved" it. :P

The other problems are still on so feel free to solve them. :)

---

### Post by maccer on 2006-09-02
An other little problem.

I reinstalled and guess what i configured my system the way i wanted, rebooted and it froze again. avast was completely erased from the disk. I figured that my desktop panels caused the problem... i put too much effects on them i guess and my machine could not handle it.

But anyway...
Its working now. One funny thing though. For some reason my home flder getsmounted from filesystem folder. The thing is that i remember clearly that during install i set my home folder to be on a separate partition. Now, it opens from the file system partition, which is about 9 gb and when i open the home folder on that some partition, i have 25 gb of free space...

It works fine though. i can read and write on it. Its simply a bit confusing. Im missing my drive icon from the Computer folder :(

---

### Post by LadyDoor on 2006-09-04
Have you looked in your /etc/fstab, like this?

```
$ less /etc/fstab
```

Look at where it says your "home" partition is mounting. If it's somewhere other than /home, you can change /etc/fstab so that it will automount to /home.

Hope it helps!
--Door

---

