---
title: "New Serengeti Usplash for Dapper 6.06 LTS"
date: 2006-05-31
forum: Art &amp; Design
---

### Post by j_baer on 2006-05-31
Working up to the bitter end has produced a new Usplash which IMHO puts ubuntu's boot at the same level of quality as Fedora and SuSE.

*Change log*
- Changed colors to match RC.
- Added "humanity to others"
- Added expanded 640x480 option

**The Packages (32bit):**

*mockup-053161.png* - a preview of the splash screen.

*serengeti-usplash640x480.tar.gz* - usplash for those running at 800x600 or greater.

*serengeti-usplash640x400.tar.gz* - usplash for those running at 640x480.

**The Installation:**

1. Download the appropriate file to a local folder.

2. Extract the archive.

3. Run **sudo sh inst-serengeti.sh** from terminal.

4. Select serengeti from the usplash alternatives when prompted.

Example (1):  =============
**Usplash-artwork alternative**
===========================

There are 2 alternatives which provide `usplash-artwork.so'.

Selection Alternative
-----------------------------------------------
* 1 /usr/lib/usplash/usplash-default.so
2 /usr/local/lib/usplash/serengeti_usplash.so

Press enter to keep the default[*], or type selection number: <**2**>

***************************

5. Add **vga=** to grub menu.lst file. The script loads menu.lst using gedit and the boot kernel line is toward the end (line 113 on my computer).

vga = 785 for standard vga
vga = 788 for 800x600
vga = 791 for 1024x768 *
vga = 794 for 1280x1024

Example (2):  =============
**Menu.lst**
===========================

title Ubuntu, kernel 2.6.15-23-386
root (hd0,0)
kernel /boot/vmlinuz-2.6.15-23-386 root=/dev/hda1 ro quiet splash **vga=791**
initrd /boot/initrd.img-2.6.15-23-386
...

***************************

Save, exit, reboot, and enjoy!

Thanks Ubuntu team for an outstanding effort!

---

### Post by Sukarn on 2006-05-31
It looks good, but I prefer a black background, so i'll stick with the current usplash.
I'll try it out later though, it looks good (didn't I say that already?).

Thanks.

---

### Post by johnc4510 on 2006-05-31
This is very nice, but I have a question:

1.Is this offical artwork, or is this something you have created?

---

### Post by GoA on 2006-06-01
Not official.But looks good and I'm going to test it.

---

### Post by j_baer on 2006-06-01
[QUOTE=johnc4510]This is very nice, but I have a question:

1.Is this offical artwork, or is this something you have created?[/QUOTE]

johnc4510,

Not offical, just my contribution to the community ...

:)

---

### Post by frodon on 2006-06-01
j_baer, it's a really nice contribution  ;)

Thanks a lot, i love this tip, i will include it to the [UDSF]("http://doc.gwos.org/index.php/Main_Page")

---

### Post by xXx 0wn3d xXx on 2006-06-01
Is there an install script for 64 bit Dapper ?

---

### Post by j_baer on 2006-06-01
[QUOTE=MasterChief1234]Is there an install script for 64 bit Dapper ?[/QUOTE]

Not yet but I am working on it,

Should have it shortly ...

:)

---

### Post by Jedeye on 2006-06-01
very nice :)

---

### Post by darknuala on 2006-06-02
I followed the instructions to a 'T', but however, whenever I reboot, all I get is a completely brown screen, the same color brown as shown in the screenshot, but no text, nothing, just a blank screen. After a couple of minutes the login screen appears.  I get the same thing on shutdown too.

---

### Post by i3dmaster on 2006-06-02
Hey, this is a nice work. Indeed!

---

### Post by jazzi on 2006-06-03
[QUOTE=i3dmaster]Hey, this is a nice work. Indeed![/QUOTE]
when 1152*864 ,what my vga should be?
vga=? 1152*864

---

### Post by mulperi on 2006-06-03
Without knowing the answer I'd try vga=792 and vga=793...

---

### Post by jazzi on 2006-06-03
[QUOTE=mulperi]Without knowing the answer I'd try vga=792 and vga=793...[/QUOTE]
I tried vga=791.and it works fine,but who know what's the accuracy answer?
](*,)

---

### Post by rado_london on 2006-06-03
Thanks this is really great!

---

### Post by migraineboy on 2006-06-05
[QUOTE=j_baer]
**The Installation:**

1. Download the appropriate file to a local folder.

2. Extract the archive.

3. Run **sudo sh inst-serengeti.sh** from terminal.

4. Select serengeti from the usplash alternatives when prompted.

[/QUOTE]

I did just like you say here but all I've got is a " ile or directory not found message" on terminal.. What  am I doing wrong?

---

### Post by mulperi on 2006-06-05
To extract the archive you need to type:
[B]tar xvzf  serengeti-usplash640x480.tar.gz
[/B]
then run rhe script
**sudo sh ./inst-serengeti.sh**

---

### Post by migraineboy on 2006-06-05
[QUOTE=mulperi]To extract the archive you need to type:
[B]tar xvzf  serengeti-usplash640x480.tar.gz
[/B]
then run rhe script
**sudo sh ./inst-serengeti.sh**[/QUOTE]

Thx man. I was using right button extract here.:mrgreen: :mrgreen:
Problem is now I only got a bromn screen when loading. I did the step 5 but I guess there&#347; something still missing...

Here&#347; my changed menu.lst:

# menu.lst - See: grub(8), info grub, update-grub(8)
#            grub-install(8), grub-floppy(8),
#            grub-md5-crypt, /usr/share/doc/grub
#            and /usr/share/doc/grub-doc/.

## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not change this entry to 'saved' or your
# array will desync and will not let you boot your system.
default		0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout		10

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
#hiddenmenu

# Pretty colours
#color cyan/blue white/blue

## password ['--md5'] passwd
# If used in the first section of a menu file, disable all interactive editing
# control (menu entry editor and command-line)  and entries protected by the
# command 'lock'
# e.g. password topsecret
#      password --md5 $1$gLhU0/$aW78kHK1QfV3P2b2znUoe/
# password topsecret

#
# examples
#
# title		Windows 95/98/NT/2000
# root		(hd0,0)
# makeactive
# chainloader	+1
#
# title		Linux
# root		(hd0,1)
# kernel	/vmlinuz root=/dev/hda2 ro
#

#
# Put static boot stanzas before and/or after AUTOMAGIC KERNEL LIST

### BEGIN AUTOMAGIC KERNELS LIST
## lines between the AUTOMAGIC KERNELS LIST markers will be modified
## by the debian update-grub script except for the default options below

## DO NOT UNCOMMENT THEM, Just edit them to your needs

## ## Start Default Options ##
## default kernel options
## default kernel options for automagic boot options
## If you want special options for specific kernels use kopt_x_y_z
## where x.y.z is kernel version. Minor versions can be omitted.
## e.g. kopt=root=/dev/hda1 ro
##      kopt_2_6_8=root=/dev/hdc1 ro
##      kopt_2_6_8_2_686=root=/dev/hdc2 ro
# kopt=root=/dev/hda6 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,5)

## should update-grub create alternative automagic boot options
## e.g. alternative=true
##      alternative=false
# alternative=true

## should update-grub lock alternative automagic boot options
## e.g. lockalternative=true
##      lockalternative=false
# lockalternative=false

## additional options to use with the default boot option, but not with the
## alternatives
## e.g. defoptions=vga=791 resume=/dev/hda5
# defoptions=quiet splash

## altoption boot targets option
## multiple altoptions lines are allowed
## e.g. altoptions=(extra menu suffix) extra boot options
##      altoptions=(recovery mode) single
# altoptions=(recovery mode) single

## controls how many kernels should be put into the menu.lst
## only counts the first occurence of a kernel, not the
## alternative kernel options
## e.g. howmany=all
##      howmany=7
# howmany=all

## should update-grub create memtest86 boot option
## e.g. memtest86=true
##      memtest86=false
# memtest86=true

## should update-grub adjust the value of the default booted system
## can be true or false
# updatedefaultentry=false

[COLOR="Red"]vga=791[/COLOR] --> [COLOR="Red"]that&#347; the line I added[/COLOR]

## ## End Default Options ##

title		Ubuntu, kernel 2.6.15-23-386
root		(hd0,5)
kernel		/boot/vmlinuz-2.6.15-23-386 root=/dev/hda6 ro quiet splash
initrd		/boot/initrd.img-2.6.15-23-386
savedefault
boot

title		Ubuntu, kernel 2.6.15-23-386 (recovery mode)
root		(hd0,5)
kernel		/boot/vmlinuz-2.6.15-23-386 root=/dev/hda6 ro single
initrd		/boot/initrd.img-2.6.15-23-386
boot

title		Ubuntu, memtest86+
root		(hd0,5)
kernel		/boot/memtest86+.bin 
boot

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda1
title		Microsoft Windows XP Professional
root		(hd0,0)
savedefault
makeactive
chainloader	+1

---

### Post by JimmyBEng on 2006-06-05
[QUOTE=migraineboy]
Problem is now I only got a bromn screen when loading. I did the step 5 but I guess there&#347; something still missing...[/QUOTE]

the vga=791 is in the wrong place.  the simple option is to add it in the kernal listing for your default kernal, i have used yours below.

```
title Ubuntu, kernel 2.6.15-23-386
root (hd0,5)
kernel /boot/vmlinuz-2.6.15-23-386 root=/dev/hda6 ro quiet splash **vga=791**
initrd /boot/initrd.img-2.6.15-23-386
savedefault
boot

```

that is one option.  The problem is that if you install a new kernal you will have to add that line manually.  to make in add to every default kernal that gets installed add it here.

```
## additional options to use with the default boot option, but not with the
## alternatives
## e.g. defoptions=vga=791 resume=/dev/hda5
# defoptions=quiet splash **vga=791**
```

if you add it in the second location you will need to run the command

```
sudo update-grub
```

so that your entires in your grub menu all get updated.  hope this helps.

---

### Post by xtacocorex on 2006-06-06
This is a very slick usplash theme and looks great with it set to 1024x768.

Thanks for the good work!

---

### Post by migraineboy on 2006-06-06
[QUOTE=JimmyBEng]the vga=791 is in the wrong place.  the simple option is to add it in the kernal listing for your default kernal, i have used yours below.

```
title Ubuntu, kernel 2.6.15-23-386
root (hd0,5)
kernel /boot/vmlinuz-2.6.15-23-386 root=/dev/hda6 ro quiet splash **vga=791**
initrd /boot/initrd.img-2.6.15-23-386
savedefault
boot

```

that is one option.  The problem is that if you install a new kernal you will have to add that line manually.  to make in add to every default kernal that gets installed add it here.

```
## additional options to use with the default boot option, but not with the
## alternatives
## e.g. defoptions=vga=791 resume=/dev/hda5
# defoptions=quiet splash **vga=791**
```

if you add it in the second location you will need to run the command

```
sudo update-grub
```

so that your entires in your grub menu all get updated.  hope this helps.[/QUOTE]


Thank you very much man!! that really worked. Now I can show my ubuntu to my friends and make them envy. ;-)

---

### Post by jatilq on 2006-06-15
Thank you, very nice job.

---

### Post by robenroute on 2006-07-27
Is there a simple way of undoing the serengeti install? I've installed it following the instructions to the letter, but I keep getting problems with with starting X. Tried vga=785, 791, 792, 794, 795..... none of them work properly and now I'm stuck with a 'dead' brown screen on start-up and shutdown.

Thanks, Rob

---

### Post by nanophobic on 2006-07-28
I too am getting brown screen. Tried all the options :(

---

### Post by robenroute on 2006-07-30
I've been tinkering a bit more, but can't get it to work. Neither can I get my original Ubuntu splash back. Anyone? Please....

Thanks, 
Rob

---

### Post by Karlos on 2006-08-05
i too can't seem to get it to work but i have managed to get the default splash back.
What you do is run the script again and select the other option (default) when you get to the select 1 or 2 bit. Then dont do anything when it comes to adding the vga just close gedit down, reboot and your good to go..

---

### Post by robenroute on 2006-08-08
> **Karlos said:**
> i too can't seem to get it to work but i have managed to get the default splash back.
What you do is run the script again and select the other option (default) when you get to the select 1 or 2 bit. Then dont do anything when it comes to adding the vga just close gedit down, reboot and your good to go..

Thanks Karlos, that indeed did the ol' trick. I guess I just missed the first option (default setting) when I ran the serengeti shell script the first time...

Rob

:D

---

### Post by adalbertus on 2007-02-05
> **j_baer said:**
> Working up to the bitter end has produced a new Usplash which IMHO puts ubuntu's boot at the same level of quality as Fedora and SuSE.

*Change log*
- Changed colors to match RC.
- Added "humanity to others"
- Added expanded 640x480 option

**The Packages (32bit):**

*mockup-053161.png* - a preview of the splash screen.

*serengeti-usplash640x480.tar.gz* - usplash for those running at 800x600 or greater.

*serengeti-usplash640x400.tar.gz* - usplash for those running at 640x480.

**The Installation:**

1. Download the appropriate file to a local folder.

2. Extract the archive.

3. Run **sudo sh inst-serengeti.sh** from terminal.

4. Select serengeti from the usplash alternatives when prompted.

Example (1):  =============
**Usplash-artwork alternative**
===========================

There are 2 alternatives which provide `usplash-artwork.so'.

Selection Alternative
-----------------------------------------------
* 1 /usr/lib/usplash/usplash-default.so
2 /usr/local/lib/usplash/serengeti_usplash.so

Press enter to keep the default[*], or type selection number: <**2**>

***************************

5. Add **vga=** to grub menu.lst file. The script loads menu.lst using gedit and the boot kernel line is toward the end (line 113 on my computer).

vga = 785 for standard vga
vga = 788 for 800x600
vga = 791 for 1024x768 *
vga = 794 for 1280x1024

Example (2):  =============
**Menu.lst**
===========================

title Ubuntu, kernel 2.6.15-23-386
root (hd0,0)
kernel /boot/vmlinuz-2.6.15-23-386 root=/dev/hda1 ro quiet splash **vga=791**
initrd /boot/initrd.img-2.6.15-23-386
...

***************************

Save, exit, reboot, and enjoy!

Thanks Ubuntu team for an outstanding effort!

Hi!
I can't download the archive, why? Is it only "attachment.php"?.
Any sugestions?
Thx

---

### Post by jvc26 on 2007-02-06
love it it looks really nice :)
Il

---

