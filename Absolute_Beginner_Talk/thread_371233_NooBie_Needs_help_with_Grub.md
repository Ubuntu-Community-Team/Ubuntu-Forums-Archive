---
title: "NooBie Needs help with Grub"
date: 2007-02-26
forum: Absolute Beginner Talk
---

### Post by kittyhawk63 on 2007-02-26
Partially Resolved:

I got Grub working per instructions from others. I now need GRUB to "freeze" on screen without continuing into Linux. It will give my wife time to choose the HDD she wants...Linux or Windows. At this time the ESC key has to be pressed to go to the Menu. I want the Menu to come up and hold until a choice is made. Any suggestions?

Please, keep it simple for this newbie.

Thanks in advance.
KH

---

### Post by LotsOfPhil on 2007-02-26
I think you need to start by posting the contents of /boot/grub/menu.lst
```
sudo cat /boot/grub/menu.lst
```

I think we'll need the output from fdisk -l too
```
sudo fdisk -l
```

---

### Post by ieee488 on 2007-02-26
Grub doesn't know that there is another OS to boot into.
You'll have to modify  */boot/grub/menu.lst* and probably */etc/fstab*

---

### Post by kittyhawk63 on 2007-02-26
kittyhawk63@kittyhawk63:~$ sudo cat /boot/grub/menu.lst
Password:
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
# kopt=root=/dev/hda1 ro

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

title           Ubuntu, kernel 2.6.15-28-386
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.15-28-386 root=/dev/hda1 ro quiet splash
initrd          /boot/initrd.img-2.6.15-28-386
savedefault
boot

title           Ubuntu, kernel 2.6.15-28-386 (recovery mode)
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.15-28-386 root=/dev/hda1 ro single
initrd          /boot/initrd.img-2.6.15-28-386
boot

title           Ubuntu, kernel 2.6.15-26-386
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.15-26-386 root=/dev/hda1 ro quiet splash
initrd          /boot/initrd.img-2.6.15-26-386
savedefault
boot

title           Ubuntu, kernel 2.6.15-26-386 (recovery mode)
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.15-26-386 root=/dev/hda1 ro single
initrd          /boot/initrd.img-2.6.15-26-386
boot

title           Ubuntu, memtest86+
root            (hd0,0)
kernel          /boot/memtest86+.bin
boot

-------------------------------------------------------------------------------------
kittyhawk63@kittyhawk63:~$ sudo fdisk -l

Disk /dev/hda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        9541    76638051   83  Linux
/dev/hda2            9542        9729     1510110    5  Extended
/dev/hda5            9542        9729     1510078+  82  Linux swap / Solaris

Disk /dev/hdb: 40.9 GB, 40982151168 bytes
240 heads, 63 sectors/track, 5293 cylinders
Units = cylinders of 15120 * 512 = 7741440 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1   *           1        4915    37157368+   c  W95 FAT32 (LBA)
/dev/hdb2            4916        5293     2857680    f  W95 Ext'd (LBA)
/dev/hdb5            4916        5293     2857648+   c  W95 FAT32 (LBA)

---

### Post by loserboy on 2007-02-26
just by glancing at this I would say theres a good chance the problem is with windows, xp usually wants to be primary/master.

I've seen that as being the problem for others, although it might not be the case here

---

### Post by kittyhawk63 on 2007-02-26
> **ieee488 said:**
> Grub doesn't know that there is another OS to boot into.
You'll have to modify  */boot/grub/menu.lst* and probably */etc/fstab*

Huh? Noobie remember?

---

### Post by Maestro23 on 2007-02-26
> **kittyhawk63 said:**
> Huh? Noobie remember?

You never learn.:)

---

### Post by kittyhawk63 on 2007-02-26
> **Maestro23 said:**
> You never learn.:)

What kind of response is this Maestro? I have two HDD and I want both connected and working. I've been only working with one HDD until now. That is the Linux HDD.

---

### Post by LotsOfPhil on 2007-02-26
These changes are all in your /boot/grub/menu.lst file.

First thing: 
```
 sudo cp /boot/grub/menu.lst /boot/grub/menu.lst.bk
```

Put a # in front of "hiddenmenu" This will comment it out and make it so your grub menu isn't hidden.

Then, add this after the first Ubuntu option (right near the end of the file, "title Ubuntu, kernel 2.6.15-28-386 ... boot").

```

title           Microsoft Windows XP
root            (hd1,0)
savedefault
makeactive
chainloader     +1

```

---

### Post by LotsOfPhil on 2007-02-26
Also, someone else mentioned your /etc/fstab. This file tells Linux what hard drives you have. We'll need to change that if you want to see your Windows HD with Ubuntu. Is this something you want to do?

---

### Post by jingo811 on 2007-02-26
I didn't read through your problem, too tired right now.
But maybe the GUI grub editor will make your life easier:
[http://www.ubuntuforums.org/showthread.php?t=228104](http://www.ubuntuforums.org/showthread.php?t=228104)

---

### Post by Maestro23 on 2007-02-26
> **jingo811 said:**
> I didn't read through your problem, too tired right now.
But maybe the GUI grub editor will make your life easier:
[http://www.ubuntuforums.org/showthread.php?t=228104](http://www.ubuntuforums.org/showthread.php?t=228104)

Beat me to Jingo.  Just dug that thread up as well.

---

### Post by kittyhawk63 on 2007-02-26
Ok everyone. I need to try a few of these suggestions. I'll get back later if none have resolved the problem.

Thanks again for the help.

That's not like you Maestro23. You've been so helpful up till now. Me thinks you went to bed too late last night. I've always appreciated your willingness to stay with my issues as a noobie. I am an aging man and don't learn as quickly as I used to.

I need the Windows HDD because I do editing for a business and they use MS Word.
I have to keep Windows going. That is the reason that I need now to connect the WinXP HDD with Grub.

---

### Post by kittyhawk63 on 2007-02-26
> **Maestro23 said:**
> Beat me to Jingo.  Just dug that thread up as well.

Maestro23, I posted before you did and we crossed paths. I thought you must have been tired. I forgive you. Thanks for your suggestion.
KH

---

### Post by Maestro23 on 2007-02-26
> **kittyhawk63 said:**
> Maestro23, I posted before you did and we crossed paths. I thought you must have been tired. I forgive you. Thanks for your suggestion.
KH

No prob man.  Was just messing with you. (Hence the smiley face).

Good luck.

---

### Post by kittyhawk63 on 2007-02-26
> **Maestro23 said:**
> No prob man.  Was just messing with you. (Hence the smiley face).

Good luck.

Maestro23,
Missed your smile. Here's back at ya. :)

---

### Post by kittyhawk63 on 2007-02-26
This is the first response I get.

kittyhawk63@kittyhawk63:~$ /boot/grub/menu.lst file.
bash: /boot/grub/menu.lst: Permission denied
kittyhawk63@kittyhawk63:~$

---

### Post by LotsOfPhil on 2007-02-26
I didn't say to do that. (It doesn't make any sense). Reread my post. The first thing to type is:
```
sudo cp /boot/grub/menu.lst /boot/grub/menu.lst.bk
```

---

### Post by kittyhawk63 on 2007-02-26
> **LotsOfPhil said:**
> I didn't say to do that. (It doesn't make any sense). Reread my post. The first thing to type is:
```
sudo cp /boot/grub/menu.lst /boot/grub/menu.lst.bk
```

I did do the sudo thing you mentioned.

Here, below, is the reply. Am I supposed to see a list to place the "#" ?

kittyhawk63@kittyhawk63:~$  sudo cp /boot/grub/menu.lst /boot/grub/menu.lst.bk
Password:
kittyhawk63@kittyhawk63:~$

---

### Post by kittyhawk63 on 2007-02-26
> **LotsOfPhil said:**
> I didn't say to do that. (It doesn't make any sense). Reread my post. The first thing to type is:
```
sudo cp /boot/grub/menu.lst /boot/grub/menu.lst.bk
```


Sorry I did do as you suggested. Here is the response. Am I supposed to see alist for placing the "#" ?
kittyhawk63@kittyhawk63:~$  sudo cp /boot/grub/menu.lst /boot/grub/menu.lst.bk
Password:
kittyhawk63@kittyhawk63:~$

---

### Post by LotsOfPhil on 2007-02-26
Now you need to open up /boot/grub/menu.lst for editing. 

I don't understand when you say 'Am I supposed to see a list to place the "#" ?'
Put the # in front of where it says "hiddenmenu"

---

### Post by kittyhawk63 on 2007-02-26
I am not clear on what I am supposed to do to unhide the menu.

You stated:
Put a # in front of "hiddenmenu" This will comment it out and make it so your grub menu isn't hidden.

Can you tell me step by step what I do to unhide the menu?
See the reply already posted just above to see what I go with the sudo command.

[B]I now see what you are referring to with hidden menu. Sorry about that. Really, I am. I thought that the sudo command was supposed to show me the menu.
[/B]
I'll be back when I do what you say and will let you know how it went.

---

### Post by LotsOfPhil on 2007-02-26
Do you know how to edit files? 

Edit /boot/grub/menu.lst
Find the line that is "hiddenmenu"
     Here is some context:
```

...
timeout 3

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
hiddenmenu

# Pretty colours
#color cyan/blue white/blue
...

```

I don't know what I am not telling you. I am not trying to skip any steps, nor am I assuming you know something (besides how to edit a file).
The "sudo cp ..." command I had you run earlier was just to make a backup of the file we are editing, in case something messes up.

---

### Post by kittyhawk63 on 2007-02-26
[QUOTE=LotsOfPhil;2217942]Do you know how to edit files? 

Edit /boot/grub/menu.lst
Find the line that is "hiddenmenu"
     Here is some context:
```

...
timeout 3

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
hiddenmenu

# Pretty colours
#color cyan/blue white/blue
...

```

Everything is already as you state it.

---

### Post by wesley_of_course on 2007-02-26
Wesley here ;

    In a terminal  :    sudo gedit /boot/grub/menu.lst 

  This makes a backup : sudo cp /boot/grub/menu.lst /boot/grub/menu.lst.bk


   Not trying to hijack here , I'm a NOOBIE  , too !   :)

   Just trying to help is all.

---

### Post by kittyhawk63 on 2007-02-26
This is what is confusing me. You said to place a # before hiddenmenu to unhide the menu. According to the input on the line, placing the # hides it. Hitting ESC unhides it. I will try this and follow the next step to your instructions.

---

### Post by kittyhawk63 on 2007-02-26
Well, if you're still with me, I really don't know how to edit these lines...yet. May I have your list of instructions on how to do this?

---

### Post by Patrick K on 2007-02-26
Just do this to unhide the grub menu.

Open a terminal (Applications>Accessories) 

In the terminal type
> gksudo gedit /boot/grub/menu.lst (Ignore any warnings or error messages)
Once gedit opens with the file displayed go to the hiddenmenu item and put a hash mark (#) in front of hiddenmenu. This now means that the hiddenmenu item is not active. So the menu will now be shown. It may seen counterintuitive but that's the way it works. 

I also suggest changing the timeout from 3 to 10. This number is in seconds and this will give you more time before grub auto boots to the default OS. 

Close gedit. When you do this it will ask if you want to save the changes. Select yes. When you do this gedit will make a backup copy of the original file and save the changes to the active file.

---

### Post by kittyhawk63 on 2007-02-26
Thanks Patrick,
I guess that the other person got tired of my ignorance and left me hanging. I've been waiting for a response from him/her for over 30 minutes. Of couse, maybe they checked out to eat supper or had to run errands. I wished they had let me know one way or the other. Being a noobie is frustrating enough.
Thanks for your information. It put me right in to the edit feature. :)

---

### Post by kittyhawk63 on 2007-02-26
Patrick,
I just wanted to tell you how I appreciated that you treated me like a noobie. You told me the exact steps I needed to take to unhide the GRUB menu. It was clear, concise, and effective.
Thanks again. :) 
KH

---

### Post by kittyhawk63 on 2007-02-26
> **wesley_of_course said:**
> Wesley here ;

    In a terminal  :    sudo gedit /boot/grub/menu.lst 

  This makes a backup : sudo cp /boot/grub/menu.lst /boot/grub/menu.lst.bk


   Not trying to hijack here , I'm a NOOBIE  , too !   :)

   Just trying to help is all.

Thanks "brother" Wesley.
):P

---

### Post by Patrick K on 2007-02-26
Glad to help. I was, and still am in most respects, a nubee. But I have had to deal with grub on a couple occasions so have a basic understanding of it. The same with video drivers. I've had to reinstall them a few times. 
So you can see the menu and have more time to select, correct?

---

### Post by kittyhawk63 on 2007-02-26
> **Patrick K said:**
> Glad to help. I was, and still am in most respects, a nubee. But I have had to deal with grub on a couple occasions so have a basic understanding of it. The same with video drivers. I've had to reinstall them a few times. 
So you can see the menu and have more time to select, correct?

Well, Patrick, I changed the time to 10 seconds. However, the other suggestion that I got to add some lines into Grub did not work. 

I found Grub by hitting ESC during boot up. When I first had Grub loaded onto my Windows HDD Grub was visible. I like the fact that it is hidden since I had Grub loaded onto the Linux HDD.

I found Windows XP listed. When I chose it the screen froze. Any suggestions?

---

### Post by Patrick K on 2007-02-26
Sorry, not really. You've gone into territory I am unfamiliar with. 

If you still have to esc after commenting out hiddenmenu, I have no idea what else will work. Your problems have surpassed my knowledge of grub.

---

### Post by kittyhawk63 on 2007-02-26
> **Patrick K said:**
> Sorry, not really. You've gone into territory I am unfamiliar with. 

If you still have to esc after commenting out hiddenmenu, I have no idea what else will work. Your problems have surpassed my knowledge of grub.

What exactly do you mean by "commenting out hiddenmenu"? The "#" was already on hiddenmenu by default on my install of Dapper 6.06. In other words, I did not have to comment it out.

I am back-tracking and placing a "#" in front of the lines I inserted earlier per instructions I had been given. I may need them yet.

Thanks for your help. Very much appreciated. I saved a copy of it and will print it out.

KH

---

### Post by LotsOfPhil on 2007-02-26
As far as commenting out hiddenmenu goes, I think you might be confused by there being 2 lines with hiddenmenu in them. It doesn't matter anymore. If you can get to GRUB by hitting escape during bootup, that's fine.

To fix the problem you are having with it freezing after picking windows XP, make the following change. Instead of what I told you before, use this: 
```

title           Microsoft Windows XP
root            (hd1,0)
map        (hd0) (hd1)
map        (hd1) (hd0)
savedefault
makeactive
chainloader     +1

```

Good luck.

---

### Post by kittyhawk63 on 2007-02-26
I think that is what I am looking for. I shall give it a try. I will let you know how it went.
KH

---

### Post by kittyhawk63 on 2007-02-26
> **LotsOfPhil said:**
> As far as commenting out hiddenmenu goes, I think you might be confused by there being 2 lines with hiddenmenu in them. It doesn't matter anymore. If you can get to GRUB by hitting escape during bootup, that's fine.

```

title          Microsoft Windows XP
root         (hd1,0)
map        (hd0) (hd1)
map        (hd1) (hd0)
savedefault
makeactive
chainloader     +1

``` Good luck.

**Eureka! **   You succeeded in giving me the right instructions. :popcorn: 

Now my wife said she would like the GRUB to HOLD until a choice is made without using the ESC key. Do you know how to do this?

---

### Post by LotsOfPhil on 2007-02-27
Right near the beginning of /boot/grub/menu.lst you have:
```

...
## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout 3

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
hiddenmenu
...

```

Change this to:
```

...
## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
#timeout 3

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
#hiddenmenu
...

```

NOTE: All you are doing is putting a # in front of timeout and putting a # in front of hiddenmenu. 2 changes, no more, no less. Do not put ... in there. I am using that to signify parts of the file I am not including.

---

### Post by confused57 on 2007-02-27
This explains how to set the time grub is displayed:
[http://users.bigpond.net.au/hermanzone/p15.htm#timer](http://users.bigpond.net.au/hermanzone/p15.htm#timer)

---

### Post by LotsOfPhil on 2007-02-27
That link is great. Kittyhawk, you should try and read through it when you are done here. It will explain all the advice you've received.

---

### Post by kittyhawk63 on 2007-02-27
Thanks for the suggestions. I will give them a try.
KH

---

### Post by kittyhawk63 on 2007-02-28
Here is the menu.lst file Patrick. I had to save it as a .txt file.
Looking for some great advise.
kh

You know, I don't see the attachment in "Preview Post." I hope that it came through. It showed it to be uploading under Manage Attachments.
Edit: I finally got it to paste. Let me know if the attachment worked. OK?

Here it is.
# menu.lst - See: grub(8), info grub, update-grub(8)
#            grub-install(8), grub-floppy(8),
#            grub-md5-crypt, /usr/share/doc/grub
#            and /usr/share/doc/grub-doc/.

## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number  is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not change this entry to 'saved' or your
# array will desync and will not let you boot your system.
default        

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout        10

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
# title        Windows 95/98/NT/2000
# root        (hd0,0)
# makeactive
# chainloader    +1
#
# title        Linux
# root        (hd0,1)
# kernel    /vmlinuz root=/dev/hda2 ro
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
# kopt=root=/dev/hda1 ro

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

title        Ubuntu, kernel 2.6.15-28-386
root        (hd0,0)
kernel        /boot/vmlinuz-2.6.15-28-386 root=/dev/hda1 ro quiet splash
initrd        /boot/initrd.img-2.6.15-28-386
savedefault
boot

# I added the next 5 lines per instructions of forum.
#title           Microsoft Windows XP
#root            (hd0,0)
#savedefault
#makeactive
#chainloader     +1

# I added the next 7 lines per instructions of forum.
title           Microsoft Windows XP
root            (hd1,0)
map        (hd0) (hd1)
map        (hd1) (hd0)
savedefault
makeactive
chainloader     +1

title        Ubuntu, kernel 2.6.15-28-386 (recovery mode)
root        (hd0,0)
kernel        /boot/vmlinuz-2.6.15-28-386 root=/dev/hda1 ro single
initrd        /boot/initrd.img-2.6.15-28-386
boot

title        Ubuntu, kernel 2.6.15-26-386
root        (hd0,0)
kernel        /boot/vmlinuz-2.6.15-26-386 root=/dev/hda1 ro quiet splash
initrd        /boot/initrd.img-2.6.15-26-386
savedefault
boot

title        Ubuntu, kernel 2.6.15-26-386 (recovery mode)
root        (hd0,0)
kernel        /boot/vmlinuz-2.6.15-26-386 root=/dev/hda1 ro single
initrd        /boot/initrd.img-2.6.15-26-386
boot

title        Ubuntu, memtest86+
root        (hd0,0)
kernel        /boot/memtest86+.bin 
boot

### END DEBIAN AUTOMAGIC KERNELS LIST

---

### Post by kittyhawk63 on 2007-02-28
Hey, with everyone's help, I was able to figure it out and got GRUB stay on screen until I made a selection. Thank you all. This thread is now marked "Resolved".

---

