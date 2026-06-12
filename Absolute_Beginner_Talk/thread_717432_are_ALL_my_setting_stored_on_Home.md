---
title: "are ALL my setting stored on /Home?"
date: 2008-03-07
forum: Absolute Beginner Talk
---

### Post by Sonic Reducer on 2008-03-07
i recently messed up GRUB on my laptop when i was fooling around trying to install Linux Mint on a 4gb thumbdrive.

i have a separate /home partition on my hard drive, i'm kind of curious about Linux Mint, and would like to install it on this laptop, if i install and flag the partition i used as /home for Gutsy will all my bookmarks, extensions, preferences in firefox still be there? how about other programs?

is there any way i can also create a list of all the programs i have installed on my computer from the Daryna live CD? it would be nice to run a *sudo aptitude --with-recommends install _______________* on a big list of programs i have installed already.

if there is anything else i need to do to make this as seamless as possible?

---

### Post by spiderbatdad on 2008-03-07
Dont know about the Daryna Live CD's capabilities, but the is aptoncd. [http://aptoncd.sourceforge.net/](http://aptoncd.sourceforge.net/)  which kind of works.

---

### Post by some_random_noob on 2008-03-07
A lot of settings are stored in /etc. But Firefox cache/history/bookmarks should be in ~/.mozilla. Along with other basic stuff.

---

### Post by Paqman on 2008-03-07
> **Sonic Reducer said:**
> 
i have a separate /home partition on my hard drive, i'm kind of curious about Linux Mint, and would like to install it on this laptop, if i install and flag the partition i used as /home for Gutsy will all my bookmarks, extensions, preferences in firefox still be there? how about other programs?


Yes, but you'd also need to make sure you set up your users the same on both systems. Otherwise you'll get permissions problems. In particular you need to make sure the user number and group are the same. However, you may find some weird behaviour from using the same user on two distros, as programs may overwrite each others config files.

It's worth playing around with, as it'll teach you a lot about permissions and config files. Have a browse thorugh ~/.gconf to see what sort of stuff lives there.

> 
is there any way i can also create a list of all the programs i have installed on my computer from the Daryna live CD??

[Create a list of installed packages](http://ubuntuforums.org/showthread.php?t=261366)

---

### Post by hyper_ch on 2008-03-07
user based configs are stord in your home folder... server wide settings are to be found in /etc

---

### Post by cjm5229 on 2008-03-07
Most of your settings are in .gconf and .gconfd both in your home folder. Some of those are going to conflict with Mints settings. Especially your desktop settings, which I believe are in .gconfd. If you wish to dual boot Ubuntu and Mint make a separate /home folder about 4 Gigs, and use the other home folder as a Data file. You can even share your .mozilla file for both OS by pointing FF to it. or just copy it from the old /home to the new one. Same thing with your email client. Just use the old /home for all your Data files.

---

### Post by Paqman on 2008-03-07
> **cjm5229 said:**
>  If you wish to dual boot Ubuntu and Mint make a separate /home folder about 4 Gigs, and use the other home folder as a Data file.

You don't need multiple /home partitions to run multiple distros. You can avoid any conflicts by simply setting up different users on the different systems. Each will have their own directory within /home, so they won't clash.

A separate data partition might make sense though. /home has to have it's permissions set a certain way (744? I think?) so sharing data from another users /home could be tricky.

---

### Post by rockinlinux on 2008-03-07
I didnt this same thing with mandirv and it worked very well. I used aptoncd to amke the install process faster so ic ould have all the same apps.

---

