---
title: "Ubuntu-trying to change the mount point caused system failure"
date: 2006-11-08
forum: Absolute Beginner Talk
---

### Post by kjazz16 on 2006-11-08
I installed Ubuntu 6.10 on my laptop with windows Dual boot configuration fine. Both Ubuntu and Windows were booting up fine, but i tried to change mount points with Ubuntu which caused Ubuntu start only with recovery or terminal safe mode and I seem not to be able to fix the issue: Here is what happenned:
During Ubuntu installation, I specified a seperate partition for /home directory, but after the installation, df -k command and gparted showed that /home directory is under / partition.My disk configuration is as follows
hda1- Dell utility partition
hda2- windows partition
hda3- / partition
hda4- extended partition
hda5-linux swap partition
hda6- /media/hda6 ( I specified this partition be /home using gparted with live CD)
The fact that hda6 was mounted as /media/hda6 , not as /home bothered me, and I wanted to change that. I wanted to make /dev/hda6 partition mounted to /home. I first used cp -r /home /media/hda6 command to copy the home directory to hda6 partition. I then used rm -r /home directory. Unmounting hda6 from /media/hda6 and mounting to /home directory did not work. I was unable to boot. then I tried to create a link using ln -s /media/hda6 /home command. All the files are there, but I am getting error messages after typing my password. The error is User's $HOME/.dmrc file is being ignored. Users home directory must be owned by user etc. and it only lets me in with terminal failsafe. I know the issue is with the cp process. I think it did not copy files with permissions etc.How can I fix this issue and make hda6 mounted to /home directory? I know this is a long story, sorry for that, but help will be appreciated.
Thanks

---

### Post by bsussman on 2006-11-08
> **kjazz16 said:**
> How can I fix this issue and make hda6 mounted to /home directory? I know this is a long story, sorry for that, but help will be appreciated.
Thanks

Put back the mount point.  If /home doesn't exist, how can the system mount your filesystem there?

A mount point is a directory just like any other.  It is used to link the separate filesystem into the general file tree that starts with '/'.

try starting with google, search for 'what is a mount point?' and study - the search results start with several good links for this.

---

### Post by kjazz16 on 2006-11-08
Thank for the reply. I actually put back the mount point. The file system /dev/hda6 is mounted as /media/hda6.Under this partition I can see my home folder( since I copied it here before I removed /home folder). I created a /home folder again and copied back home folder under /media/hda6 to /home. I have a home folder with my user name  and all the settings etc .However I am getting the error messages that I mentioned above.

---

### Post by bsussman on 2006-11-09
> **kjazz16 said:**
>  I created a /home folder again and copied back home folder under /media/hda6 to /home.

OIC - so you don't want to have home on a separate filesystem.
>  However I am getting the error messages that I mentioned above.

That error is reported several times - look for previous threads.

---

### Post by jaytek13 on 2006-11-09
I always found this kind of annoying also. With other distro's, the /home partition is on a seperate partition from the root directory by default, which is incredibly convenient when you don't want to do a upgrade to a new release and would rather do a new install while saving the contents of your home directory.

For the life of me I can't understand why Ubuntu chose to do this differently.

---

### Post by kjazz16 on 2006-11-09
Yes. I want /home directory on dev/hda6 filesystem. But since I am unable to log on using the only user account i have, i recreated /home directory on dev/hda3 ( which is mounted as /) and copied my folder back there. I am still unable to boot. As I said previously, i think it is due to cp process not copying security settings etc. 
With my disk configuration, how can I make /dev/hda6 filesystem mounted to /home?( that is what i intended during installation, but somehow did not work). Of course, I have to fix the error message first and be able to log on. 
Thank you.

---

### Post by bsussman on 2006-11-09
> **kjazz16 said:**
> 
With my disk configuration, how can I make /dev/hda6 filesystem mounted to /home?( that is what i intended during installation, but somehow did not work). Of course, I have to fix the error message first and be able to log on. 
Thank you.

See [http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome)

This tutorial is very good.  I recommend you carefully review the first part on creating the new partition but you may not need to do it as hda6 exists already.  In the tutorial hda7 is used as the new home.  You need to remember to use 6 instead of 7 :)  I do recommend you move anything on it out of the way to avoid unexpected results.


You definitely need to do from "**Using the new partition" **on.

This tutorial preserves permissions and ownerships and has helped many folks do this task.

BTW the parameter to cp that preserves metadata is -p

The tutorial uses a find/cpio method to do the actual copying instead of cp which is very thorough and reliable.

---

### Post by bsussman on 2006-11-09
I like a separate /home too but one of the hazards of dual release support is that some apps may have mutually exclusive or not-downward-compatable configs and no app I know of has multi release config management built in.  Unlike the os/module scheme whereby modules for one os release are kept separately from modules for another :)

How do I know this?  Firefox is making me crazy with it's automatic plugin compatability check and disablement.  When I go back to the release that is compatable, it just cannot manage to turn them back on!

---

### Post by kjazz16 on 2006-11-09
Thanks a lot. I read the tutorial and based on what I read, I think that was what I needed at first before I attempted to change the /home directory to a different file system than / directory. The problem is that I used cp -r command instead of all the other commands described there to do a proper copy to /dev/hda6 filesystem. To make things worse, I user rm -r /home command after cp command to delete the original /home directory on /dev/hda1 without making a backup. Since I was unable to convert my /home folder to /dev/hda6 filesystem, I recreated /home folder on /dev/hda3 (/ folder) and copied my home directory back there from /dev/hda6. I only had one user account created and I am unable to log on to Ubuntu except with failsafe terminal. What's the best way to be able to log on? I think since I do not have the properly used command back up of my original home directory, I totally lost the option to log on to  Ubuntu with the only account I created. Can I create another user account and log on at this point? Can I use live CD to recover?
Thanks

---

### Post by bsussman on 2006-11-09
I think the answer is yes:

1. Try using the  live cd to allow you to chown all files in 'your' home dir to your ownership and then rebooting and logging in.

2. If that does not work, you could use live to add an new user using adduser which sets up a home directory for the new user.

This might be a situation where absolute repair (saving everything in your old, busted home) is not worth the labor.

---

### Post by kjazz16 on 2006-11-09
OK. That was easier than I thought. I am able to log on. Thanks. I did not even use live CD. I rebooted with Recovery kernel mode during Grub menu. Did a chown on my home directory. I realized root was the owner. That must be due to the way cp operates on file security. I changed the ownership and it worked. Now I will have to work on switching my /home directory to a seperate filesystem.
Also just curious, how come I am able to boot to kernel recovery mode without any user authentication. Anyone can use my pc with this mode and do a damage? Am i missing something?

---

### Post by bsussman on 2006-11-09
> **kjazz16 said:**
> Did a chown on my home directory. I realized root was the owner. That must be due to the way cp operates on file security. I changed the ownership and it worked.

You are conceptually correct but I am fussy with words - this is a matter of file ownership, not file security per se.

when you are root and you cp files without preserving current metadata, yes - it assigns you(root) as the owner.  What else could it do?
>  Now I will have to work on switching my /home directory to a seperate filesystem.
go slowly - it is not that hard to do.
> 
Also just curious, how come I am able to boot to kernel recovery mode without any user authentication. Anyone can use my pc with this mode and do a damage? Am i missing something?No - you are not missing anything - without deep encryption, physical access equals unlimited access for those who know how to use a boot cd or diskette.

---

