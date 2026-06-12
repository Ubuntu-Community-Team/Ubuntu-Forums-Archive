---
title: "Cannot write to Authorisation File?!"
date: 2006-02-27
forum: Absolute Beginner Talk
---

### Post by Kid G on 2006-02-27
Hi,

I installed a second harddrive in my pc and in my efforts to move my Home Directory to that drive I encounterd the folowing message the next time I rebooted:

[INDENT]GDM could not write to your authorisation file. This could mean that you are out of disk space or that your home directory could not be opened for writing. Please contact your system administrator[/INDENT]

Is there any way I can rescue my Home directory?

Thanks

---

### Post by paulmilliken on 2006-02-27
The problem may lie in your /etc/fstab file.  Please post the result of typing
"cat /etc/fstab" or "sudo cat /etc/fstab" at the command line.

---

### Post by Kid G on 2006-02-27
The results of cat /etc/fstab:

# <file system>  <mount point>  <type>  <options>      <dump>    <pass>
proc                 /proc               proc      defaults          0             0
/dev/hda4         /                     ext3      defaults, errors = remount -ro   0    1
/dev/hda5         /media/hda5      vfat    isocharset = utf8, umount = 000  0    0
/dev/hda6         none                swap       sw              0              0
/dev/hdd           /media/cdrom0   udf,      iso9660      user,noauto    0         0
/dev/hdc           /media/cdrom1   udf       iso9660      user,noauto    0         0
/dev/fd0            /media/floppy0   auto       rw, user, noauto           0         0

The new harddrive doesnt seem to be listed?

---

### Post by Sandlst on 2006-02-27
Could you please also post what steps you took to try and move /home to the new drive?

---

### Post by Kid G on 2006-02-27
I was using the guide posted here:

[http://ubuntu.wordpress.com/2006/01/29/move-home-to-its-own-partition/](http://ubuntu.wordpress.com/2006/01/29/move-home-to-its-own-partition/)

I obviously did something wrong - I formated the new drive using Gparted as ext3 if that helps?

---

### Post by Sandlst on 2006-02-27
"Add a line to the &#8220;/etc/fstab&#8221; file that looks like the following:"

Were you able to complete this section? From reading your fstab above it would seem that this is where the trouble is-if you know the label (probobly /dev/hd(a,b,c,or other)(somenumbergoeshere) I would add it from the command prompt with:```
sudo nano /etc/fstab
```and follow the guide about this part:```
/dev/[COLOR="DarkOrange"]hda5[/COLOR][COLOR="Black"] /home ext3 nodev,nosuid 0 2
``` changing hda5 to the correct setting-if you dont know the label this will be much more difficult, but sorting it out should be possible with this command:```
sudo fdisk -l /dev/[COLOR="DarkOrange"]hda[/COLOR]
```[/COLOR]-this will show what partitions are on your first hard drive-change to hdb hdc hdd, etc as needed to list those partitions as well-hopefully you can tell which part. it is and on which drive using this method.  Post back if you have any problems...

*EDIT* looking at your fstab, if you do have to search for the right partition and use the above method, it will show /dev/hda4 as "linux", /dev/hda6 as "Linux Swap / Solaris" and, unless you have another ext formated part., the other one that says "linux" will be the right one.

---

### Post by Kid G on 2006-02-27
Still stuck with the same problem - not sure exactly which point in the tutorial I got to - is there any other way I can retrieve my Home directory?

Thanks

---

### Post by Sandlst on 2006-02-27
At one point in the guide, you are to move the entire home drive to /old_home...if you got this far my best bet would be to run ```
sudo mv /old_home /home
``` Good luck!

*EDIT* if doing this doesnt work, try this after you reboot```
cd /home/old_home
```
after this type in ```
ls
```-you should see a folder with your user-name on it.  If you do see the folder, do this ```
sudo mv [COLOR="DarkOrange"]****[/COLOR] /home
``` where [COLOR="DarkOrange"]****[/COLOR] is your user-name

---

### Post by muz1 on 2006-08-12
Hey I have been having the same problem.
When I try to login, I get 

GDM could not write to your authorisation file. This could mean that you are out of disk space or that your home directory could not be opened for writing. Please contact your system administrator

I have not been creating, moving or doing anything with partitions or HDD's. I suspect that I am out of room as when I was trying to burn a cd image in my last session, it would not do it and told me that Iwas out of space. As I have another partition mounted where I move all of my files over to, I am thinking that maybe my temp memory or whatever has filled up.
Is there a way to get to these and empty them via command line. Also, if I cannot login, how do I get to command line?

Any help would muchly be appreciated. 
Cheers
Muz

---

### Post by wapowell on 2007-04-23
This thread is kinda old, so I hope you are not still stuck with this.  :)

Just thought I would post the solution that worked for me.  I had the same error message, and I also had not moved my home directory or anything of the kind.  I *did* run a dist-upgrade which went successfully, but after a reboot I got the cannot write to authorisation error.

I booted into recovery mode which dropped me at a root prompt.  I ran apt-get clean then rebooted.  That was all I needed to do to get things back on track.  My disk had simply become too full.

I hope this helps anyone that may be searching the older threads.

---

### Post by justin-888 on 2007-09-23
WOW ! My first great experience with a bug.
Just Registered first time in Ubuntu Forum, search for "Cannot write to Authorisation File" and found this thread.

My problem was that I left some downloads running, used up all available hdd spcae and then my system wouldnt let me login again with my root or my user password. 

So I found this thread - the last post was most "apt"  (EXCUSE THE PUN).

My next problem was "HOW DO I RUN apt-get clean at the command line" ?

So I searched for "How to run apt-get clean in google and found that I have to type :  

"  sudo apt-get clean "

I have seen someone do that before - SUDO

I also saw at the same place the command "apt-get install localepurge"

did that too - you need to select the languages that you want to keep and the rest will be deleted which is supposed to free up a good few more meg - perhaps enough to get you out of trouble ??

Anyway, with my attitude of "I am no expert - but I'll take a look !"  I did these things, then typed exit, to get me back to root, then typed reboot then was VERY VERY HAPPY to find that I could now login again with everything back to normal. GREAT !!!

I know most of your guys and girls know this very basic stuff, but as a new comer to ubuntu and linux I just had no idea about these last few points so thought perhaps others may find this useful.

All the best to everyone
Justin
[www.supersynergy.com]("http://www.supersynergy.com")

---

