---
title: "Meld and pacnew files"
date: 2018-05-08
forum: Arch and derivatives
---

### Post by anon_private on 2018-05-08
Ref: Manjaro OS

Hello,

I recently undertook an update and now have a number of pacnew files.

Evidently, I need to merge the pacnew file into the original file. Automattion seems like a good idea,

Can someone tell me how involved is the process, and how to begin? I have the programme in my repo.

Thanks.

Ps. If I don't meld what are the consequences?

---

### Post by #&amp;thj^% on 2018-05-08
> **anon_private said:**
> 
Ps. If I don't meld what are the consequences?
Nothing right away but in time though could get very messy. ;)
Time consuming way and not pretty.
```
find /etc -type f -name "*.pacnew"
```
and just go through them one at a time then:
```
kdesu meld /etc/config /etc/config.pacnew
```

Gosh they make things complicated...just plain Arch and I don't see such things
Maybe this>>> fits into my knowledge of bash. Credit to Alan from Arch Forums.
```

#!/bin/bash
# etc-update - merge *.pacnew files with original configurations with meld

pacnew=$(find /etc -type f -name "*.pacnew")

for i in $pacnew
do
  kdesu meld $(basename $i .pacmew) $i &
  wait
done
```
Call it automeld or something like that so remember.
Also In yaourt-git, you can find a new feature for automerging of .pacnew files. Just add "AutoSaveBackupFile yes" in /etc/yaourtrc to use it later with yaourt -C.
Note: auto-merge will only work next time. When a new .pacnew arrives.

---

### Post by anon_private on 2018-05-08
Ref. OS is manjaro

Thanks for responding.

Are you saying that I may as well meld each pair manually? That is, meld the new into the old, then delete the new.?

Or, is it better to let meld do the job, on a pair basis, and one pair at a time?

---

### Post by Xian on 2018-05-09
> **anon_private said:**
> 
Are you saying that I may as well meld each pair manually? That is, meld the new into the old, then delete the new.?

Or, is it better to let meld do the job, on a pair basis, and one pair at a time?

Do them in pairs -- use Meld and _manually_ edit the new into old. 

Only way to be sure. Then delete the new. 

If you never previously changed the file then you can probably just use the new one as is. 

I use dotpac to identify the .pac files and meld to edit (if necessary).

[https://aur.archlinux.org/packages/dotpac/dotpac/dotpac](https://aur.archlinux.org/packages/dotpac/dotpac/dotpac)

---

### Post by anon_private on 2018-05-09
> **Xian said:**
> Do them in pairs -- use Meld and _manually_ edit the new into old. 

Only way to be sure. Then delete the new. 

If you never previously changed the file then you can probably just use the new one as is. 

I use dotpac to identify the .pac files and meld to edit (if necessary).

[https://aur.archlinux.org/packages/dotpac/dotpac/dotpac](https://aur.archlinux.org/packages/dotpac/dotpac/dotpac)

I see meld in my repo. I also see python2-meld3.

Do I need both to use meld?

Out of interest, is it too complex to attempt the editing manually, that is, without the help of meld

---

### Post by Xian on 2018-05-09
> **anon_private said:**
> I see meld in my repo. I also see python2-meld3.

Do I need both to use meld?

Just install Meld:

[https://www.archlinux.org/packages/extra/any/meld/](https://www.archlinux.org/packages/extra/any/meld/)

> **anon_private said:**
> Out of interest, is it too complex to attempt the editing manually, that is, without the help of meld

It's definitely not too complex. Meld (or similar program) just makes it easy to see the diffs.

---

### Post by anon_private on 2018-05-09
I have installed meld from the manjaro repo. There are no help pages with the application.

I can see how to input one file for comparison, but how do I input the second file?

How can I ensure that the meld process proceeds in the right direction, that is, from the pacnew file to the initial file.

What then happens to the pacnew file?

UPDATE: Please see later post

---

### Post by anon_private on 2018-05-09
I am having problems with permission.

I am looking at files in the /etc folder.

The programme meld is owned by root.

how an I run meld as root, or, is there a better way of using meld?

---

### Post by Dennis N on 2018-05-09
Could you not just use **cp** command?
```
cp -n directory1/* directory2/
```
should merge files from directory1 into directory2 but will not replace any existing files.

---

### Post by anon_private on 2018-05-09
I would like to try meld. But I am having problems with the file permissions

---

### Post by Xian on 2018-05-09
> **anon_private said:**
> I would like to try meld. But I am having problems with the file permissions

Most people would use the terminal command:

```
sudo meld
```

Or login as root in a terminal and then run meld:

```
su
<password>
meld
```

But running GUI applications as root is considered hazardous. 

I'll point you to the Arch wiki page for a more detailed explanation:

[https://wiki.archlinux.org/index.php/Running_GUI_apps_as_root](https://wiki.archlinux.org/index.php/Running_GUI_apps_as_root)

---

### Post by anon_private on 2018-05-09
Thank you for the link.

Am I right in thinking that kdesu meld is a safe way to run meld as administrator

I use manjaro under Plasma and KDE

---

### Post by Xian on 2018-05-09
> **anon_private said:**
> 
Am I right in thinking that kdesu meld is a safe way to run meld as administrator


Ubuntu took gksu out of 18.04 because of in part security concerns.

So ... take from that what you will. 

Would I usde kdesu to run meld as admin? Yes.

Am i supposed to advise others to do the same? Probably not.

---

### Post by anon_private on 2018-05-10
How can I use 'meld' to compare files in /etc unless I run as admin. There must be a recommended and safe procedure

---

### Post by Xian on 2018-05-10
The official Arch recommended way is to use pacdiff.

See here:

[https://wiki.archlinux.org/index.php/Pacman/Pacnew_and_Pacsave#Managing_.pacnew_files](https://wiki.archlinux.org/index.php/Pacman/Pacnew_and_Pacsave#Managing_.pacnew_files)

---

### Post by anon_private on 2018-05-11
> **Xian said:**
> Do them in pairs -- use Meld and _manually_ edit the new into old. 

Only way to be sure. Then delete the new. 

If you never previously changed the file then you can probably just use the new one as is. 

I use dotpac to identify the .pac files and meld to edit (if necessary).

[https://aur.archlinux.org/packages/dotpac/dotpac/dotpac](https://aur.archlinux.org/packages/dotpac/dotpac/dotpac)

As a I recall, when looking at the pairs (original, original.pacnew), it was the original that was the more extensive file. So, if I have never made changes to the original file then I can use it as is (delete original.pacnew).

The files are in /etc, and, hence, cannot be saved, other than as a new file. Presumably, then deleting the original, and re-naming the new file to that of the original. Bit of a pain.

There are some files (e.g. password) which should probably be left alone.

I have got another update to undertake.

No doubt more pacnew files

---

### Post by Dennis N on 2018-05-11
> **No doubt more pacnew files**
Just wondering: What are pacnew files anyway? I have Manjaro here, but a search doesn't turn up any files containing 'pacnew'.
Edit: Now I found some (14 - since original install in Jun 2017) searching from /. There is one for fstab for example, but looks like an empty version except comment lines at the top. Same with some others. Some have a config setting. 

Googled explanation answers my question:
> when pacman upgrades a package which includes a new config file created by the maintainer differing from the currently installed file, it saves a .pacnew file with the new configuration. pacman provides notice when these files are written.

Glad they are kept in case there is a problem! So far there hasn't been.

---

### Post by anon_private on 2018-05-11
I am wondering if the pacnew files need to be merged before another update is initiated, or, does it not matter

---

### Post by #&amp;thj^% on 2018-05-11
> **anon_private said:**
> I am wondering if the pacnew files need to be merged before another update is initiated, or, does it not matter
If yours looks anything like mine I would not worry about it ATM
```
locate pacnew <run this to see the below code>
/etc/locale.gen.pacnew
/etc/profile.pacnew
/etc/lightdm/lightdm-gtk-greeter.conf.pacnew
/etc/pacman.d/mirrorlist.pacnew
/etc/systemd/logind.conf.pacnew

```
And your system should merge these by default.
Now I'm not that familiar with Manjaro or Octopi>>>But when suggesting GUI package installers for Arch I highly recommend "[pamac-aur]("https://wiki.manjaro.org/index.php?title=Pamac")" it will search and update from yaourt also. :)
But I simply just use the terminal to keep my system tidy "pacman -Syyu" and also a couple of times a month I will remove Orphans.
Have a look here might ease your worrying a bit: [https://bbs.archlinux.org/viewtopic.php?id=182428](https://bbs.archlinux.org/viewtopic.php?id=182428)
And Look at Dennis N's post below mine.

---

### Post by Dennis N on 2018-05-11
> I am wondering if the pacnew files need to be merged before another update is initiated, or, does it not matter
After my last post, I eyeballed the *.pacnew files and decided on a case by case basis (14 files) what action to take. Most look like they would revert to the original (like the passwd and fstab). So I didn't see a reason to change anything in my existing files. But its up to you to decide. I installed this Manjaro MATE in Sept 2015, and have never looked at the pacnew files until now, but all is running fine regardless.

---

### Post by anon_private on 2018-05-11
If yours looks anything like mine I would not worry about it ATM
```
locate pacnew <run this to see the below code>
/etc/locale.gen.pacnew
/etc/profile.pacnew
/etc/lightdm/lightdm-gtk-greeter.conf.pacnew
/etc/pacman.d/mirrorlist.pacnew
/etc/systemd/logind.conf.pacnew

```

Mine looks like this. Interestingly the command locate is not active in my version of manjaro

folder /etc

```
[andrew@Dell-pc etc]$ ls *.pacnew
crypttab.pacnew  gshadow.pacnew     passwd.pacnew       shells.pacnew
fstab.pacnew     hosts.pacnew       resolv.conf.pacnew
group.pacnew     locale.gen.pacnew  shadow.pacnew

```

---

### Post by anon_private on 2018-05-11
> **Dennis N said:**
> After my last post, I eyeballed the *.pacnew files and decided on a case by case basis (14 files) what action to take. Most look like they would revert to the original (like the passwd and fstab). So I didn't see a reason to change anything in my existing files. But its up to you to decide. I installed this Manjaro MATE in Sept 2015, and have never looked at the pacnew files until now, but all is running fine regardless.

What have you done with the pacnew files. My guess is that you have left them in /etc.

When you updated further, did you notice any increase in the number of pacnew files

---

### Post by Dennis N on 2018-05-11
> What have you done with the pacnew files. My guess is that you have left them in /etc.
Right. I left them and didn't delete any. Never have deleted any.
> When you updated further, did you notice any increase in the number of pacnew files 
This is the first time I looked at them. But there are only 14 since Sept 2015 so probably safe to say that they do not accumulate very quickly. I just installed a Manjaro Gnome last month on Apr 15 and it has 10 pacnew files.

---

