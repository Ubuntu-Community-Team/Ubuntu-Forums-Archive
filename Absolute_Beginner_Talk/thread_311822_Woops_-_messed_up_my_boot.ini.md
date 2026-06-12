---
title: "Woops - messed up my boot.ini"
date: 2006-12-03
forum: Absolute Beginner Talk
---

### Post by SteveJ on 2006-12-03
Please spare me having to explain why, just let admit that I am an idiot and move on. Here is my problem.

I got a used computer - two drives, C: and D: (C: is primary). I installed windows onto D:, later decided it was a bad idea and installed onto C:, then formatted D:. I, however, erased the wrong installation from boot.ini. When I turned on the computer I got;

Windows XP
Default Windows

Using Windows XP pointed to the old install - on D:, default pointed to the correct install. I was OK with choosing default. 

Now comes the UBUNTU problem. I installed it onto the formatted D: drive. In doing so it modified the boot.ini (I think) and left only the Windows XP option available (the one that incorrectly points to the D: drive). 

Now I can't open Windows, only Ubuntu. I know that you might argue that it is a good thing, but I do need to access some college specific programs so I really do need windows back. 

How can I edit the boot.ini from Ubuntu so that it will point to the correct location of Windows (on the C: drive?)

Remember, I'm a beginner's begineer to Ubuntu, 

Thanks;

SteveJ

---

### Post by nixclusive on 2006-12-03
The Ubuntu installation never really modified your boot.ini file. Can you paste the contents of your boot.ini here? 

To do so, first you'll have to mount your windows partition (C:) in Ubuntu. Assuming you are an absolute beginner, lets do this step by step. First open the terminal by clicking 

Applications>System>Terminal 

in the menu bar you see when the Ubuntu installation is up and running.

Now in the window that appears, type the following:

```
sudo fdisk -l
```

And paste the output here, this will help us to identify your windows partition of C:. Then we'll proceed with the mounting and editing stuff.

Good luck. :-)

---

### Post by tuxcantfly on 2006-12-03
this boot.ini you speak of is actually /boot/grub/menu.lst

try alt-F2 gksudo gedit /boot/grub/menu.lst

---

### Post by SteveJ on 2006-12-03
Hey, thanks for the reply. Sorry I wasn't here to see it right away. I had to go to church. At any rate - I entered the command into the terminal as requested (sudo fdisk -l), but I'm not certain how to get the information pasted too you. 

I should probably have dealt with one thing at a time. Firefox doesn't seem to work properly in Ubuntu. Some web sights work (such as ebay and google), but most won't load up. The ones that do, don't load so fast. Unfortunately, [www.ubuntuforums.com](www.ubuntuforums.com) is one of the ones that don't. I am having to write this from another computer.

Were I reading this email I would be thinking to myself - 'hey fellow, go get a book'. I will be doing that soon. In the mean time, I got to get the other computer going :)

Is there some something specific that you are looking for from the fdisk command? I can tell you that it reports the exisitence of both drives.

Perhaps the better question at this point would be how to get all websights to display since, until that point, I will not be able to get much information to or from the computer.

I'm not so fond of wearing the beginner hat again.....

Thanks again


SteveJ

---

### Post by SteveJ on 2006-12-03
OK, a fellow in another thread helped me get Firefox going, so I am able to copy/ past now. The result that I got from fdisk was

steve@ubuntu:~$ sudo fdisk -l

Disk /dev/hda: 30.6 GB, 30603724800 bytes
255 heads, 63 sectors/track, 3720 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1           2       16033+  12  Compaq diagnostics
/dev/hda2               3        3720    29864835   42  SFS

Disk /dev/hdb: 41.1 GB, 41174138880 bytes
255 heads, 63 sectors/track, 5005 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1               1        2263    18177516    7  HPFS/NTFS
/dev/hdb2            2551        5005    19719787+   7  HPFS/NTFS
/dev/hdb3   *        2264        2533     2168775   83  Linux
/dev/hdb4            2534        2550      136552+   5  Extended
/dev/hdb5            2534        2550      136521   82  Linux swap / Solaris

---

### Post by SteveJ on 2006-12-03
Well, 

I am afraid that I had to reinstall windows back on my primary drive. My wife homeschools and needed the computer going by tomorrow. Sorry for all of the trouble. 

Now, I have Windows on my C: drive and (I think) that I still have Ubuntu installed on my secondary drive. 

Unfortunately, Ubuntu no longer comes up as an option when I boot the machine. 

My question is now this: How to modifiy the boot file from Windows to allow Ubuntu to be recognized upon boot-up?

SteveJ

---

### Post by seshomaru samma on 2006-12-04
Linux is probably still there
Boot from your Ubuntu CD in
Open a terminal
then:
```
sudo grub
```
put your password in (it wont display it on the screen while you are inputing it)
then:
```
find /boot/grub/stage1
```
replace the question marks with the output of the last command :
```
root (hd?,?)
```
(probably hd0,1)
then :
```
setup (hd0)
```
and
```
quit
```
you have just installed grub ,next time you boot you will be able to choose between windows and linux

---

### Post by SteveJ on 2006-12-04
Thank you very much for the reply - and the help. 

When you say boot from the CD, do you mean from the GUI version (standard download)? The reason that I asked is that I installed from the alternate (text) install version. I happen to have the GUI CD available though, I just wanted to clarify. 

Thanks,

SteveJ

---

### Post by Bigbluecat on 2006-12-04
It's a bit late in Shanghai so I'll jump in.

Yes. Use the GUI live CD. This will let you open a terminal and get to the grub command line.

It's also useful to keep a copy of Super Grub Disk lying around. Very useful programme. I'm sure you can Google and download it. You do not need this for what you are doing now but worth having.

---

### Post by SteveJ on 2006-12-04
Wow! It worked like a charm!

I am officially on my way! 

Thank you so very much. 

SteveJ

---

### Post by SteveJ on 2006-12-05
I guess I spoke too soon. Ubuntu is indeed working like a charm, but windows is not. I am back to my original situation. The windows pointed to when I turn on my computer is the wrong one (see my original post at the top). 

At this point, unless someone can help me otherwise, I am simply going to install windows back on the primary drive and forget about ubuntu entirely. I don't normally like the silly little animations that folks include with text, but after 3 windows installs and 2 ubuntu installs it is appropriate. 
](*,)

---

