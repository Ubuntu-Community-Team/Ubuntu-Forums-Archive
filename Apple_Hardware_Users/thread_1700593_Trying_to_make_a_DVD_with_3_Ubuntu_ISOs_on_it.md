---
title: "Trying to make a DVD with 3 Ubuntu ISOs on it"
date: 2011-03-05
forum: Apple Hardware Users
---

### Post by MacintoshLover on 2011-03-05
Dear all, I'm still kind of a n00b at this, so bear with me.
I am trying to make an Ubuntu Install DVD with all 4 versions of Ubuntu on it (Server, Netbook, Desktop, Desktop 64). I downloaded the 4 ISOs, copied their contents into respective folders on the DVD, and was about to click "burn", when I realized that it might not work that way. What should I do to put all 4 on the disk, and still have it bootable into all 4 (not all 4 at once)? I am semi-proficient at Terminal, I know what a bang is (!), and I have a fast internet connection. Please don't try to scam me with a command that erases my HDD.:confused:

---

### Post by MacintoshLover on 2011-03-06
Does anyone have any ideas? The issue is kind of pressing! :frown: :frown: :frown: :frown:

---

### Post by wilee-nilee on 2011-03-06
> **MacintoshLover said:**
> Does anyone have any ideas? The issue is kind of pressing! :frown: :frown: :frown: :frown:

If you have a thumb you can load a bunch of diffract ISO's, in this link at the bottom is the Linux version.
[http://www.pendrivelinux.com/boot-multiple-iso-from-usb-multiboot-usb/](http://www.pendrivelinux.com/boot-multiple-iso-from-usb-multiboot-usb/)

It can be done from a dvd, but as you see nobodies doing it really, nor do I know how, you would need a bootloader.

---

### Post by MacintoshLover on 2011-03-06
My Mac can't boot from USB. Thanks 4 the help though!

---

### Post by dubmartian on 2011-03-07
[http://multicd.tuxfamily.org/](http://multicd.tuxfamily.org/)

this multicd script has worked pretty well with the few multi boot dvds ive made. only thing, small utilities like clonezilla / gparted seem to boot very slow when started from multicd disks ive made... thank goodness for pmagic!

---

### Post by Kallun on 2011-03-07
> **MacintoshLover said:**
> My Mac can't boot from USB. Thanks 4 the help though!

What Mac is it? I would assume it should be able to do so, but of course there are some exceptions.

If you want to try and boot from USB, power off, then power on whilst holding the 'alt' key on your keyboard until it shows the bootable media, then just select which one you want to boot from.
 
Provided your board supports it, this should work fine, or if you still have an OS X partition, boot into that and install 'rEFIt' (Google it) it's a nice little bootloader that makes booting from USB easy, if you do try the rEFIt option, make sure to reboot into your mac partition 3 or 4 times after install to ensure it knows your boot layout, then try booting with a bootable USB in :) 

Hope this helps!

---

### Post by MacintoshLover on 2011-03-07
Dubmartian: I looked at the website, and that should solve my problem. Thanks!
Kallun: I have an older MacBook Pro, the kind that is just before the Unibody. When I try and boot while holding alt, only my HDD shows up as a bootable disk. rEFIt's webpage says "Booting Windows or Linux from an external disk is not well-supported by Apple&#8217;s firmware. It may work for you, but if it does not work, there is nothing rEFIt can do about it.", so I'm guessing i'm kind of stuck.
Also, Dubmartian, do you know if there is a less terminal-hevy way to do that? I'm fine with the terminal stuff and all, but I'm still afraid I might screw something up.

---

### Post by dubmartian on 2011-03-07
most of that page is gibberish to me as well.
just using the script is pretty simple.
[ftp://downloads.tuxfamily.org/multicd/multicd-6.4.sh](ftp://downloads.tuxfamily.org/multicd/multicd-6.4.sh)
you can copy/paste the page to a text file or "save as"
if you save both the script and your renamed ISOs to your /home/MacintoshLover directory, these are the only two lines you need to enter in the terminal: 
chmod +x multicd6.4.sh (run once to make the script executable)
sudo ./multicd6.4.sh (the multicd.iso will be saved to your home folder)

i got a language error when adding ubuntu install/live isos but it didnt seem to effect booting or installation. 

then just burn the multicd.iso like any other.

---

### Post by viper250 on 2011-03-08
to boot multi iso files from a dvd you would have to create and install a grub menu with the entires of the iso&#347; you are putting on the dvd
but with the cost of media being so cheap it may not be worth the bother 
as it&#347; easier to just burn the iso on thier own media.

using a usb stick you can use unetbootin to choose between iso&#347;

---

### Post by MacintoshLover on 2011-03-08
using one disk for the convienience

---

### Post by MacintoshLover on 2011-03-08
Thanks for the method dubmartian! I should be good to go! If not, I'll post any errors/screwups.

---

### Post by MacintoshLover on 2011-03-08
it gives me an error saying
```
Copying ubuntu-10.10-desktop-amd64...
grep: /etc/mtab: No such file or directory
mount: -o loop: option not supported 
```
any help you can offer? BTW i'm using a Mac to do this. Should I use Ubuntu?
EDIT: I just ran it under Ubuntu, and I got output as follows:
```
sudo ./multicd-6.4.sh
ubuntu-10.10-desktop-i386
ubuntu-10.10-netbook-i386
ubuntu-10.10-server-amd64
Memtest86+

Continuing in 2 seconds - press Ctrl+C to cancel
Copying ubuntu-10.10-desktop-i386...
cat: /tmp/multicd-root/tags/lang: No such file or directory
./multicd-6.4.sh: line 321: [: !=: unary operator expected
Copying ubuntu-10.10-netbook-i386...
cat: /tmp/multicd-root/tags/lang: No such file or directory
./multicd-6.4.sh: line 321: [: !=: unary operator expected
Copying ubuntu-10.10-server-amd64...
cp: cannot stat `/tmp/multicd-root/ubuntu-10.10-server-amd64.ubuntu/casper': No such file or directory

```
Anybody got any ideas?

---

### Post by kashish on 2011-03-09
machintosh lover.. i think there must be some problem in USB check it out.

---

### Post by MacintoshLover on 2011-03-09
> **kashish said:**
> machintosh lover.. i think there must be some problem in USB check it out.
Please clarify, I fail to understand what you are saying.

---

### Post by dubmartian on 2011-03-10
Sorry, that script should be run using linux.

---

### Post by beatskobe on 2011-03-10
These document sharing websites have good amounts of daily traffic  volumes and visitors search different keywords on them. This means,  you’ll get more exposure with using right keywords phases for your  documents.

---

### Post by dubmartian on 2011-03-10
oops again, missed the post with the error output. i wasnt clear when i mentioned the "renamed ISOs." forgot the website wasnt  clear to me either. it wasn't until i looked at the script as text and stumbled on the file names its looking for. for ubuntu they would need to go with one of these..  

amd64.ubuntu.iso 
ubuntu-alternate.iso
i386.ubuntu.iso 

hmm, looking again seems like anything before .ubuntu.iso might work. so maybe server.ubuntu.iso
would work.  i'm guessing at this point.

---

### Post by MacintoshLover on 2011-04-05
Ill try that! Thanks!

---

