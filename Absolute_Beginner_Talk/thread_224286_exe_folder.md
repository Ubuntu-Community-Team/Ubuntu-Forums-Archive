---
title: "exe folder"
date: 2006-07-27
forum: Absolute Beginner Talk
---

### Post by IrishGangsta on 2006-07-27
I want to make a new log in screen.
I downlaoded the theme and put the contents in a folder.
When i chose the folder as the theme it opens up...i want to make the folder its self executable i guess. 

What ever it takes so the folder doesnt open, but allows me to chose it as a theme

---

### Post by GuitarHero on 2006-07-27
You handle the login theme just like any other theme, with System>Preferences, Theme

---

### Post by aysiu on 2006-07-27
> **GuitarHero said:**
> You handle the login theme just like any other theme, with System>Preferences, Theme
Actually, the login theme is set elsewhere--System > Administration > Login Setup.

---

### Post by IrishGangsta on 2006-07-27
um
i know where its located.
its system>administration>Log in Window> then choose your theme.

I didnt ask where do i go to choose my theme.

The title also says it.  All of my themes contents is in a folder.  How do i make the folder executable to chose as my theme.  When i pickl my theme folder it opens up and then i have to pick a part....But i can't i need all the parts to create the whole theme.

anyone else with help,
much appreciated

---

### Post by aysiu on 2006-07-27
The folder has to be zipped up as a .tar.gz

Right-click the folder and select to create an archive.

---

### Post by IrishGangsta on 2006-07-27
When i saved it in my home directory i labled it login theme
Then inside log in theme i made a folder called SleekDragon.tar.gz

And then that folder opens up with all the contents. I want that folder (SleekDragon.tar.gz) to not open up and just allow me to use it as my theme.

I also just followed aysiu's instructions and created an archive .tar.gz for it, but when i go to my log in themes this SleekDragon folder still opens.  Maybe i should be putting the contents into something other then a folder? i dont know

which is why i am asking in beginner forums.
It's probably a silly mistake i am making?

Anymore suggestions?

---

### Post by aysiu on 2006-07-27
Are you able to install other GDM themes? Perhaps your .tar.gz isn't constructed properly?

---

### Post by IrishGangsta on 2006-07-27
Well, this is the first i am changing log in screen and i want to change splash and grub screens.

But maybe that might be the problem, i will try to download a different one.

---

### Post by IrishGangsta on 2006-07-27
I just downloaded another one and i could not install the theme.

Idk what it is i am doing wrong.
Mabe i am not extracting it right or something.
All i know is when i go to install it makes me chose one of the content files rather then the main file. 

We are back to where i started.
I originally tried throwing the cotents into a folder but the folder just opens.  I need to put all the contents in some kind of folder that will let me install it,rather then open it.

---

### Post by aysiu on 2006-07-27
Those are three separate things.

GDM themes control the login screen.
Then you have a separate splash screen.
Then you have a separate Grub splash.

---

### Post by aysiu on 2006-07-27
> **IrishGangsta said:**
> I just downloaded another one and i could not install the theme.

Idk what it is i am doing wrong.
Mabe i am not extracting it right or something.
 That's what you did wrong--you extracted it. Don't extract it. Keep it as a .tar.gz. Install it **exactly** the way you downloaded it.

---

### Post by IrishGangsta on 2006-07-27
ok, GOOD AND BAD NEWS!

Goodnews is, that i got the Log In screen to work, i made the silly mistake of extracting it.

The bad news is that i didnt get the log in screen i wanted.  I am using a different one i downloaded.

The error message i get is that it is not an archive theme.  Even though it  appears to be a .tar.gz file

Any more help anyone?

---

### Post by jimmygoon on 2006-07-27
> **IrishGangsta said:**
> ok, GOOD AND BAD NEWS!

Goodnews is, that i got the Log In screen to work, i made the silly mistake of extracting it.

The bad news is that i didnt get the log in screen i wanted.  I am using a different one i downloaded.

The error message i get is that it is not an archive theme.  Even though it  appears to be a .tar.gz file

Any more help anyone?

Yea, his original problem was that he was placing his files in a FOLDER named "foobar.tar.gz"... it wasn't actually an archive.

Just take the tar.gz, originally downloaded form and drag-n-drop it onto the login window... that should do it for you

---

### Post by IrishGangsta on 2006-07-27
thanx jimmy, but thats what i did
and one of them works, but the other comes up with an error message saying the file is not an archive...even tho i downloading it from the same spot under GDM themes.

any more suggestions?

---

### Post by IrishGangsta on 2006-07-27
both files are this:
25716-SleekDragon.tar.gz  (This one says it is not an archive theme, it needs to be .tar.gz or in tar form....i dont understand!?!)
43305-Fire_1024x768.tar.gz (This One Works)

Can Anyone input on my problem?

---

### Post by aysiu on 2006-07-27
SleekDragon.tar.gz is the one you created? Did you simply rename it with a .tar.gz extension, or did you actually zip it into a .tar.gz?

---

### Post by IrishGangsta on 2006-07-27
I never created anything?

I downloaded both of these themes from [www.gnome-look.org](www.gnome-look.org)
Then i hit alt+f2 and type gksudo nautilus
Then i dragged and dropped both of those themes into a folder i created /home/mike/login_themes

---

### Post by aysiu on 2006-07-28
I don't know why you're using *gksudo nautilus* for this.

There are two Sleek Dragon's on [www.gnome-look.org](www.gnome-look.org). Both are .tar.gz files.

[This one](http://www.gnome-look.org/content/show.php?content=26461) is a splash screen.

[This one](http://www.gnome-look.org/content/show.php?content=25716) is a GDM theme.

If you install the GDM theme, it **will** install and not just go inside of the folder. I tried it. I know it works. I've attached a screenshot of what I did.

---

### Post by IrishGangsta on 2006-07-28
Alright i did it once, i'll figure it out with the sleek dragon GDM. right now i am just using FIRE.

--------------------------------------------------------------------------

But can anyone help simplify these instructiosn for me with installing a SPLASH Screen?

[B][I][COLOR="Red"]What to do with the splash screen is less straightforward. The image for the splash screen is held in /usr/share/pixmaps/splash, and there are two copies of the same image - ubuntu-splash.png and ubuntu-slick.png.

Before doing anything, I made two copies of the downloaded splash screen and put them on the Desktop. I renamed the copies ubuntu-splash.png and ubuntu-slick.png. I then went into Applications > Accessories > Terminal and typed:

cd /usr/share/pixmaps/splash

And then -

sudo mv ubuntu-splash.png ubuntu-splash-old.png

Which renamed the old splash screen rather than deleted it, in case I ever wanted it. I did the same to ubuntu-slick -

sudo mv ubuntu-slick.png ubuntu-slick-old.png

Then migrate back to the Desktop using cd - the directory is /home/yourname/Desktop. I then typed -

sudo mv *.png /usr/share/pixmaps/splash

I rebooted my machine to test if it had worked; it had. You may want to do the same, if only to enjoy the fact that the brown has disappeared[/COLOR][/I][/B]

---

### Post by aysiu on 2006-07-28
This is where Alt-F2 ```
gksudo nautilus
``` would come in handy.

Just move your new splash screen to /usr/share/pixmaps/splash and make sure it's called *ubuntu-splash.png*

That's it.

---

### Post by IrishGangsta on 2006-07-28
Alright
thank you for your help Aysiu 
I now have a neat Splash Screen and Log In Menu
But now how do i change my Grub Screen.
What do i search for in [www.gnome-look.org](www.gnome-look.org) ?

---

### Post by aysiu on 2006-07-28
That's not something you get off Gnome-look.

This helped me:
[http://ruslug.rutgers.edu/~mcgrof/grub-images/](http://ruslug.rutgers.edu/~mcgrof/grub-images/)

---

### Post by IrishGangsta on 2006-07-28
I am trying to use this [http://www.gnome-look.org/content/show.php?content=25568](http://www.gnome-look.org/content/show.php?content=25568)

to boot a grub splash screen.

That is the only grub splash screen on the site.

I am following exactly what the guy is teling me to do and yet when i boot up my laptop it doesnt take into effect.

---

### Post by aysiu on 2006-07-28
Can you post the output of these commands? Just highlight the terminal and copy and paste into this thread.

```
cd /boot/grub
ls
cat menu.lst
df -h
```

---

### Post by IrishGangsta on 2006-07-28
> **aysiu said:**
> Can you post the output of these commands? Just highlight the terminal and copy and paste into this thread.

```
cd /boot/grub
ls
cat menu.lst
df -h
```


_____________________________________________________________________________
_____________________-_-_-____-----------------------------------------------
_______________________-------------------------_____________________________

mike@Finnegan:~$ cd /boot/grub
mike@Finnegan:/boot/grub$ ls
Debian_Ent_GRUB.xpm     e2fs_stage1_5  menu.lst~          stage2
Debian_Ent_GRUB.xpm.gz  fat_stage1_5   minix_stage1_5     xfs_stage1_5
default                 jfs_stage1_5   reiserfs_stage1_5
device.map              menu.lst       stage1
mike@Finnegan:/boot/grub$ cat menu.lst
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
default         0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout         3

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
hiddenmenu

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
# title         Windows 95/98/NT/2000
# root          (hd0,0)
# makeactive
# chainloader   +1
#
# title         Linux
# root          (hd0,1)
# kernel        /vmlinuz root=/dev/hda2 ro
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
# kopt=root=/dev/sda1 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,0)

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

## ## End Default Options ##

title           Ubuntu, kernel 2.6.15-26-386
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.15-26-386 root=/dev/sda1 ro quiet splash
initrd          /boot/initrd.img-2.6.15-26-386
savedefault
boot

title           Ubuntu, kernel 2.6.15-26-386 (recovery mode)
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.15-26-386 root=/dev/sda1 ro single
initrd          /boot/initrd.img-2.6.15-26-386
boot

title           Ubuntu, kernel 2.6.15-25-386
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.15-25-386 root=/dev/sda1 ro quiet splash
initrd          /boot/initrd.img-2.6.15-25-386
savedefault
boot

title           Ubuntu, kernel 2.6.15-25-386 (recovery mode)
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.15-25-386 root=/dev/sda1 ro single
initrd          /boot/initrd.img-2.6.15-25-386
boot

title           Ubuntu, kernel 2.6.15-23-386
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.15-23-386 root=/dev/sda1 ro quiet splash
initrd          /boot/initrd.img-2.6.15-23-386
savedefault
boot

title           Ubuntu, kernel 2.6.15-23-386 (recovery mode)
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.15-23-386 root=/dev/sda1 ro single
initrd          /boot/initrd.img-2.6.15-23-386
boot

title           Ubuntu, memtest86+
root            (hd0,0)
kernel          /boot/memtest86+.bin
boot

splashimage=(hd1,0)/boot/grub/Debian_Ent_GRUB.xpm.gz

### END DEBIAN AUTOMAGIC KERNELS LIST
mike@Finnegan:/boot/grub$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda1              72G  7.2G   62G  11% /
varrun                249M   96K  248M   1% /var/run
varlock               249M  4.0K  249M   1% /var/lock
udev                  249M  120K  248M   1% /dev
devshm                249M     0  249M   0% /dev/shm
lrm                   249M   19M  230M   8% /lib/modules/2.6.15-26-386/volatile
mike@Finnegan:/boot/grub$

---

### Post by aysiu on 2006-07-28
Do you notice how every single entry in your menu.lst says **(hd0,0)** and your splashimage line says **(hd1,0)**?

(hd0,0) means /dev/sda1
(hd1,0) means /dev/sdb1

So the menu.lst is looking for your splash image on a second hard drive that is not there.

---

