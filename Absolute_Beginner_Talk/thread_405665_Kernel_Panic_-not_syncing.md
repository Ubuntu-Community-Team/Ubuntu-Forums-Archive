---
title: "Kernel Panic -not syncing"
date: 2007-04-10
forum: Absolute Beginner Talk
---

### Post by Kay The Bantu on 2007-04-10
Hi guyz fairly new to linux this is the most major issue I've encountered. The background of the scenario is I had forgotten my password so I did the 'md5' edit trick(obviously I did it wrong) because now when I boot it goes directly to grub.

I did some research and I've tired alot of stufff, (again obviously wrong) basically I did 

find /boot/grub/stage2 (which gave me)

(hd0,0)

#to which i

root (hd0,0)

#then 

setup (hd0,0)

it told me all was well -it lied coz I haven't been able to boot. All my projects are in my laptop and I can't afford to reinstall the system. I desparately need a step by step guide. Please help me out.

---

### Post by Kay The Bantu on 2007-04-10
This is a continuation of the above. After "setup (hd0,0)" it gives me the following output

checking if "/boot/grub/stage1" exists...yes
checking if "/boot/grub/stage2" exists...yes
checking if "/boot/grub/e2fs_stage1_5 exists...yes
running "embed /boot/grub/e2fs_stage1_5(hd0,0)"...failed(this is not fatal)
running "embed /boot/grub/e2fs_stage1_5(hd0,0)"...failed(this is not fatal)
running "install /boot/grub/stage1(hd0,0) /boot/grub/stage2 p /boot/grub/menu1st...succeed
done

To which I then
boot

All goes well until it gives me
No Volume Groups found
ALERT! does not exist. Dropping to a shell

Which goes the shell "ash". Please any suggestions are welcome

---

### Post by LaurelLynn on 2007-04-10
Dear  Kay The Bantu ,

I´m a little hesitate to respond, because it´s midnight here, and I really can´t stay online any longer.

The problem seems to be that you broke the GRUB bootload trying to change the password.
Because of that it fails to load your kernal and falls back to it´s second boot option, which is recovery mode. That is why you get a prompt.

IF the prompt is a ¨#¨ instead of a ¨$¨ you can fix the password right now. Type:

# passwd  the-username

and enter a new password.

This link should help you to fix the bootloader:

[http://ubuntuforums.org/archive/index.php/t-24113.html](http://ubuntuforums.org/archive/index.php/t-24113.html)

It should reinstall the GRUB bootloader from scratch.

Sorry I can´t stick around to help, but I will bookmark this thread and try to check back tommorrow, to see if you are still having problems.

THIS CAN BE FIXED WITHOUT LOOSING YOUR STUFF!

In fact it should all be readable from a Live CD boot, like when you installed Ubuntu. And thus you can back up everything to a USB or network drive if you have them.

Good Luck

---

### Post by Kay The Bantu on 2007-04-10
Thanks alot let me go try that-Superb to hear I don't have to lose my work- I'll let you know what happens tomorrow(your time).Goodnight

---

### Post by Kay The Bantu on 2007-04-11
AAAAAAAAAAAAAAAARRRRRRRRRRRRRRRRRRRRRRRRRRRRGGGGGGGGGGGGGGGGGGGGGGG.

Ok I needed that I've tried literally everything to fix my grub. First I tried using the live cd and mounting the partitions but not formatting them - the installer crashes everytime before completion(original shipit cd 6.06), I've tried the terminal but  NOTHING  happens. What's most frustrating is I can see all my files,work but CANNOT do anything (excuse me one moment) 

AAAAAAAAAAAAAAGDS^%&*R^WIWB&^O&*NO_<M

Ok back again I'm still going thru the advice LaurelLynn prescribed but I'm very much open to ANY suggestions before I chuck my laptop out the window(a wise man said "never trust a computer you can't throw out the window) and I religiously follow this maxim so pleeeeeeeeeaaaaaaaase help.

By the way LaurelLynn thanx a million for your help *sob* *sob* I can see my files again- you are a gem. Anyone else want to join my gem list please help

---

### Post by LaurelLynn on 2007-04-11
Ok, I´m going to tell you what things that I would try if it were my system.

Keep in mind that that some if this is last ditch stuff that needs to be copied with complete accuracy to prevent making things even worse (though it sounds pretty desparate now).

Step 1:  Backup

Before doing anything I would use the live cd to backup everything that is important to an external drive or network share, in fact, I would seriously consider buying an external USB harddrive to backup every partition first. (it is always a good thing to have on hand)

At the very least get a USB memory stick to backup the Master Boot Record with this command:

$ sudo dd  if=/dev/hda of=someplace-safe  bs=512 count =1

Your harddrive may not be hda, if you have a SATA drive it will be sda, or even hdb/sdb.  To find out use the Live cd to read the /etc/fstab  file on your ¨/¨ partition, just remove any numbers from the end.  Be very careful! ¨if¨"means in file, and ¨of¨ means out file.  Mixing those up or getting the numbers wrong can destroy the partition table (making everything unreadable).  You need a backup of the MBR first so you can put it back if need be!  Remember, without the partition table, all the existing files disappear ( they are still there, but no operating system will know where, the MBR is life itself).

That sounded more dire than it is in practice.  I routinely backup my MBRs all the time with that command, just be careful.

If you have enough external space you can back up the whole drive but it will take a long time:

$ sudo dd  if=/dev/hda   of=someother-safeplace

Those commands backup every bit at the lowest possible level.  If you ever need to get it back change if -> of, and  of -> if.

Adding a number ¨/dev/hda1¨ picks only a specific partition.

Step 2.  Delete GRUB from the MBR so I´m starting with a clean slate.

$ sudo dd if=/dev/zero of=/dev/hda/ bs=446 count=1 

Note:446 is critical, not one byte more or less.

Step 3. Try to restore GRUB

I would start with this guide:

[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

Here is an unofficial one:

[http://www.shahidhussain.com/wordpress/index.php?p=33](http://www.shahidhussain.com/wordpress/index.php?p=33)

There are many more which can be found from Google with the seach strings ¨ubuntu ¨reinstalling grub¨¨ or ¨ubuntu grub-install¨.

Step 4:  If I exhausted all GRUB options I would try using LILO instead.

Some people actually prefer using LILO to boot Ubuntu. Instructions on several methods of installing it can be found here:

[http://users.bigpond.net.au/hermanzone/p4.html](http://users.bigpond.net.au/hermanzone/p4.html)

Finally:

Getting the bootloader working is the first step as it is what gets you to a boot menu or command prompt.

Since you can read the partitions from the Live CD, and you haven´t reformatted.  Based on the error message, I suspect that the operating system is in perfect working order. So if you can get a working boot loader, your system should come back to life.

I will be checking this thread as I get a chance, several times a day, for the next few days to see  if you are making any progress or need additional advice.

---

### Post by Kay The Bantu on 2007-04-12
YYYYYYYYYAAAAAAAAAAAAAAAAAy
You're my hero i'd marry you right now. I managed to salvage my docs, but as for restoring my grub, well let's just say familiarity breeds contempt and me and grub-very familiar.

Anyway THHHHHHHHHHAAAAAAAAAAAANNNNNNNNNNNNNNNNNKKKKKKKKKKKKKKK YYYYYYYYYOOOOOOOOOOOOOOOOOOOOOOOOU soooooooooooooooooooooooo(pause for breathing)ooooooooooo much LaurelLynn(are you sure about the proposal?) thanx

I've reinstalled the os and now I'm updating my software thanx to you.

---

### Post by LaurelLynn on 2007-04-12
Glad I could be of help  :D 

As to marriage proposals, I actually have an email account setup just for them:

/dev/null@LaurelsProposals.com

Just kidding. Take care, and try to stay out of trouble. ):P

---

### Post by Kay The Bantu on 2007-04-13
> **LaurelLynn said:**
> Glad I could be of help  :D 

As to marriage proposals, I actually have an email account setup just for them:

/dev/null@LaurelsProposals.com

Just kidding. Take care, and try to stay out of trouble. ):P

LMAO, i actually got that. does this mean i'm getting beter in linux :D 

thanx for all your help

---

