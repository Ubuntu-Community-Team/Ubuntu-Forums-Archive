---
title: "help installing ubuntu.. :/"
date: 2005-09-18
forum: Absolute Beginner Talk
---

### Post by rollercoaster on 2005-09-18
when i boot it from the cd (which i made by burning the iso file i downloaded)... it will display the ubuntu logo and will say...

the default.. blah blah

to insall only the base system, type 'server' then ENTER.
For the default installation, press ENTER.

boot:_

ok... so when i press enter for the default installation
it will say...

Loading /install/blah.. blah...
then it will say...

Your CPU does not support long mode. Use a 32bit distribution.

what does this mean?? i'm really desperate... lol tnx!!

---

### Post by UbuWu on 2005-09-18
Sounds like you downloaded the wrong iso: amd64 while you needed i386? What kind of processor do you have and which iso did you download?

---

### Post by rollercoaster on 2005-09-18
i'm using AMD ATHLON XP 2400 processor... i downloaded the AMD64 Install CD ISO... is that wrong??

---

### Post by xmastree on 2005-09-18
Yes, that's wrong. The 64 bit is for athlon64 processors. Your athlon 2400 (same as mine) is 32 bit, so you need the PC (Intel X86) "For almost all PCs. This includes most machines with Intel/AMD/etc type processors " version.

---

### Post by rollercoaster on 2005-09-18
king ina!! ganun lng pala!! hehehe salamat par!! ^_^

---

### Post by redenjaja on 2005-09-18
mga kabayan, ask ko lang kase ngayon lang araw na ito ako nakagamit ng linux, sinubukan ko kanina yung live cd pero cd rom lang nakita nya, baket?

---

### Post by rollercoaster on 2005-09-18
huh?? panong cd rom lng nakita nya??

---

### Post by XDevHald on 2005-09-18
[QUOTE=rollercoaster]huh?? panong cd rom lng nakita nya??[/QUOTE]
 I don't mean to be rude in any way here when I say "Please speak english"

Thank You.

---

### Post by redenjaja on 2005-09-18
sorry,  ](*,)    it means it only detected my cd rom...

---

### Post by rollercoaster on 2005-09-18
sory for speaking our own language... lol ^_^

well, to answer the question... u just downloaded the 'Live CD' w/c means it will not install anything on the hd... but instead it will run the ubuntu os from the cd... you should download the 'install cd' so you can install it permanently in your hd.. ^_^

---

### Post by redenjaja on 2005-09-18
so do you mean live cd will not detect all my hardwares, it will just let me use it and cant access all my files from the hdd

---

### Post by xmastree on 2005-09-18
[QUOTE=Steve Myers]I don't mean to be rude in any way here when I say "Please speak english"[/QUOTE]Heh, that's probably my fault, for displaying the fact that I'm in the Philippines. 
Redenjaja and rollerdoaster must be pinoy, and assume that I am too. Guess they didn't look at my public profile.
I don't speal Tagalog. A little visayan, (the language used in Mindanao) but not tagalog, which they were using. About the only thing I picked up was salamat. Thank you.  :) 

Anyway, **redenjaja**, to answer your question about accessing your hard disk from the liv CD. Once you've booted from the live CD, you can mount your hard disk and access it. Depending on how it's partitioned, and what filesystem,

Assuming it's windows, FAT32 and drive C: you will need to do this from a terminal:

```
sudo mount /dev/hda1 /media/windows/ -t vfat -o iocharset=utf8,umask=000
```
If it's ntfs, (win XP), do this:```
sudo mount /dev/hda1 /media/windows/ -t ntfs -o nls=utf8,umask=0222
```Note the difference inthe umask part. that sets the permissions to read only, as linux can't write to an ntfs partition.

I should add that furst you need to make sure that mount point, /media/windows/ exists. I'm not sure, but I think the default in the live CD is /mnt/hd or similar. It doesn't really matter where you mount it, just make sure the mount point exists before you run the command or it won't work.

If it's an extended partition, with a virtual drive, it'll be hda5 instead of hda1.

All this and more can be found in [** the guide**](http://www.ubuntuguide.org)

---

### Post by redenjaja on 2005-09-19
here's the setup of my pc on xp:
c: 40gig 7200rpm
d: dvd rom
e: cd writer
f:  120gig 7200rpm SATA

both hdd are in ntfs. here's what i have after installing live cd:
[IMG]http://img.photobucket.com/albums/v476/redenjaja/Screenshot.png[/IMG]

guys please post what commands are needed to view my hdd's so ill just paste it to the terminal. thanks guys

---

### Post by xmastree on 2005-09-19
First you need to make a mount point, so type:```
sudo mkdir /media/windows
```
Then one of those commands I gave you in the post above will mount your c: drive, depending on what filesystem you're using. FAT 32 or ntfs.

If you're not sure which, take a guess. if it's the wrong one you'll just get an error, but no harm will be done, just run the other command.

---

### Post by redenjaja on 2005-09-19
here's what appeared on the terminal:


ubuntu@ubuntu:~$ sudo mkdir /media/windows
mkdir: cannot create directory `/media/windows': File exists
ubuntu@ubuntu:~$ sudo mount /dev/hda1 /media/windows/ -t ntfs -o nls=utf8,umask=0222
ubuntu@ubuntu:~$

nothing appeared on the desktop

---

### Post by xmastree on 2005-09-19
But no error message, that's good. Now, go to the places menu, computer, and browse to /media/windows

You should see it there.

---

### Post by redenjaja on 2005-09-19
yipee! how about my other hdd its in drive f: its SATA and ntfs

[IMG]http://img.photobucket.com/albums/v476/redenjaja/Screenshot-5.png[/IMG]

thanks kabayan!

---

### Post by xmastree on 2005-09-19
[QUOTE=redenjaja]yipee! how about my other hdd its in drive f: its SATA and ntfs[/QUOTE]I don't know about that, I suggest you start a new thread in [the live CD forum]("http://www.ubuntuforums.org/forumdisplay.php?f=61") and ask there.

good luck.

---

### Post by redenjaja on 2005-09-19
thank you very much xmastree! :grin:  :grin:  :grin:  :grin:  :grin:

---

### Post by oragon on 2005-09-20
[QUOTE=xmastree]Please do. I suspect we're in similar situations here...

BTW, I found a way to use Chikka messenger. There's a package called chix which adds chikka protocol to gaim.

[http://sourceforge.net/projects/chix](http://sourceforge.net/projects/chix)

Works fine with Breezy(5.10) preview, but not with Hoary (5.04) as libc6 is the wrong one.[/QUOTE]

Thats cool! but im stick with Hoary... :( i think... better update with Breezy. Tnkz!

---

### Post by pongster on 2005-09-21
[QUOTE=oragon]LOL! mga Kabayan pala nand2! Mga Kabayan! dagdag kaalaman lang... Grabe hulihan mga Micro$oft sa Pinas diba? kaya... 

Goodbye Window$.... Welcome UBuntu!!! hehehehe.

guys, ive always encouter setting up icafes here in Bicol Philippines, problems with samsung cd-roms, i thinks samsung does'nt support linux device kernels.... i really enjoy Ubuntu Linux right now... and my desktop looks like and functions like Mac OSX ! its real DamKool! the perfect Linux desktop distro!!!! fine graphics, fine memory management... etc... and Its perfect for Browsing the net. playing same games on windows just use cedega emulator, and your On with gaming!

problems with workgroup networkring? try install NFS or SMB for "file-n-print" sharing!!!

goodluck mga kabayans!!!!

"PHILIPPINES NOW SHIFTING TO UBUNTU" :)[/QUOTE]
 Good to know that active ang mga Pinoy in this Forum! Just about ready to try out Ubuntu (after 12hrs of dl the ISO)! Just need to read up some more before jumping in!  It's nice to be a newbie and learn the ropes of Linux, especially the Ubuntu Linux!  
(mods, forgive me for posting in Visayan, the major language used in our part of the Philippines)
@xmastree
maayong gabi-i bai! if duna koy pangutana re: ubuntu, etc. patabang lang ko bai be? taga Cagayan de Oro ko!

@Pinoys in Ubuntu
Time to show M$ Phil. that there is a real alternative in Linux!  FREEDOM!

---

