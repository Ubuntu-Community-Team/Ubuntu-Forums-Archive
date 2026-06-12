---
title: "Disk Full"
date: 2007-07-03
forum: Absolute Beginner Talk
---

### Post by se2schul on 2007-07-03
I had a perfectly working Xubuntu Feisty system until I managed to fill up the disk.
I installed wine and the one windows app that I really need. It seems to have filled my disk, and now I'm unable to log into XFCE. When I use the 'df' command, I saw that it's my root partition that is full. Since XFCE won't start, I'm able to get to the command line and try to free up space. The problem is that I don't know what to delete since I don't really understand where linux sticks its files. Any suggestions as to how I can free up the space?

---

### Post by joe.turion64x2 on 2007-07-03
> **se2schul said:**
> I had a perfectly working Xubuntu Feisty system until I managed to fill up the disk.
I installed wine and the one windows app that I really need. It seems to have filled my disk, and now I'm unable to log into XFCE. When I use the 'df' command, I saw that it's my root partition that is full. Since XFCE won't start, I'm able to get to the command line and try to free up space. The problem is that I don't know what to delete since I don't really understand where linux sticks its files. Any suggestions as to how I can free up the space?
I am not very familiar with apt-get or apt (the package manager), but if you type *man apt* or *man apt-get* to learn apt options to free space.

Perhaps *apt-get autoclean* makes the trick for you, according to this [http://www.debian.org/doc/manuals/apt-howto/ch-apt-get.es.html#s-clean](http://www.debian.org/doc/manuals/apt-howto/ch-apt-get.es.html#s-clean) it deletes old files.

Joe.

---

### Post by KIAaze on 2007-07-03
First of all, try:
```
apt-get clean
```

You could also remove packages by using dpkg, apt-get or aptitude.
```
dpkg --remove <package>
apt-get remove <package>
aptitude remove <package>

```
See their man pages for more info.
aptitude has some kind of consol GUI, so it might be easier to use.

To search for packages, you can use:
```
dpkg -l <regular expression>
aptitude search <expression/regular expression>
```
ex:
```
dpkg -l konso*
aptitude search konso
```

You can also safely delete language support files ending in .mo as well as documentation files.

They are stored in /usr/local/share and /usr/local/share/doc generally.
For the language files, they should always be in an LC_MESSAGES folder. So all LC_MESSAGES folders can be deleted safely, even the ones of your language if you want since when no language files are available, the programs use the text messages hard-coded into the source code (english usually).

After, you've got your system back working, you might be interested in installing **"localepurge"** to do this automatically and safely. ;)
Other interesting programs are **"debfoster"** and **"deborphan".**

---

### Post by KIAaze on 2007-07-03
Oh, and a very useful command, which isn't obvious at all:
```
dpkg-query -W --showformat='${Installed-Size;10}\t${Package}\n' | sort -k1,1n
```

It will list installed packages by size. :)

---

### Post by se2schul on 2007-07-04
Thanks. It´s fixed, but I still have more questions. I used this to free up 7% of my disk.
```
apt-get clean
```

I don´t have very much installed - just xubuntu desktop, skype, wine and a windows program to run in wine. Do all things get installed on my root partition? Is there any way to install the programs to some other partition?

It sounds like I made my root partition too small. This sounds like I might have to reinstall everything making the partition bigger. Is there a way to use GParted to increase it by using space from my windows partition?

```

steve@TheDecoStop:/usr/local/share$ df
Filesystem           1K-blocks      Used Available Use% Mounted on
/dev/sda2              1921188   1684944    138652  93% /
varrun                   63008       100     62908   1% /var/run
varlock                  63008         0     63008   0% /var/lock
procbususb               63008       112     62896   1% /proc/bus/usb
udev                     63008       112     62896   1% /dev
devshm                   63008         0     63008   0% /dev/shm
lrm                      63008     33788     29220  54% /lib/modules/2.6.20-15-generic/volatile
/dev/sda4              6736132    190200   6203748   3% /home
/dev/disk/by-uuid/CA18D99818D9843B
                      10241400   5026972   5214428  50% /media/sda1

```

---

### Post by bren on 2007-07-04
> s there a way to use GParted to increase it

yes.

step 1: backup your windows essential data or parition (whichever you choose)
step 2: righclick on the windows partition and choose resize and reduce by a few gb
step 3: rightclik on the sda2 partition and increase the size

---

### Post by coolen on 2007-07-04
> **se2schul said:**
> Thanks. It´s fixed, but I still have more questions. I used this to free up 7% of my disk.
```
apt-get clean
```

I don´t have very much installed - just xubuntu desktop, skype, wine and a windows program to run in wine. Do all things get installed on my root partition? Is there any way to install the programs to some other partition?

It sounds like I made my root partition too small. This sounds like I might have to reinstall everything making the partition bigger. Is there a way to use GParted to increase it by using space from my windows partition?

```

steve@TheDecoStop:/usr/local/share$ df
Filesystem           1K-blocks      Used Available Use% Mounted on
/dev/sda2              1921188   1684944    138652  93% /
varrun                   63008       100     62908   1% /var/run
varlock                  63008         0     63008   0% /var/lock
procbususb               63008       112     62896   1% /proc/bus/usb
udev                     63008       112     62896   1% /dev
devshm                   63008         0     63008   0% /dev/shm
lrm                      63008     33788     29220  54% /lib/modules/2.6.20-15-generic/volatile
/dev/sda4              6736132    190200   6203748   3% /home
/dev/disk/by-uuid/CA18D99818D9843B
                      10241400   5026972   5214428  50% /media/sda1

```

Unless I'm counting wrong, it sounds like you've gone for the bare minimum (Ubuntu's bare minimum is 2GB...probably smaller for Xubuntu, but not by much).
The application you installed in Wine, from what I understand, should have gone to your home folder. ~/.wine/c_drive should be your fake C drive for Wine. Unless you did the installer as root, your root partition should be fine.
Also, with resizing partitions and such, there's a GParted Live CD based on Fluxbox. I'd be a little worried about resizing partitions I have mounted, and it's just a good tool to have around in general.

---

### Post by se2schul on 2007-07-04
> **coolen said:**
> 
The application you installed in Wine, from what I understand, should have gone to your home folder. ~/.wine/c_drive should be your fake C drive for Wine. 

Yes, my fake drive C is on my home partition, but what about wine itself. Where is wine installed? On the root partition? I will try using gparted tomorrow night to improve my root partition´s size. Thanks.

---

### Post by davidjmayo on 2007-07-05
> step 1: backup your windows essential data or parition (whichever you choose)
step 2: righclick on the windows partition and choose resize and reduce by a few gb
step 3: rightclik on the sda2 partition and increase the size

Add step 1a: defragment the windows partition before resizing

setp2 and and step3 are for when you use GParted 


Also in xubuntu check your Trash is empty

---

### Post by nitro_n2o on 2007-07-05
Just to make your life a little bit easier 
use: ```
df -H
``` for Human readable format

---

### Post by KIAaze on 2007-07-05
yes, but be careful:
> -h, --human-readable
              print sizes in human readable format (e.g., 1K 234M 2G)

       -H, --si
              likewise, but use powers of 1000 not 1024


I prefer df -h.

> **se2schul said:**
> Yes, my fake drive C is on my home partition, but what about wine itself. Where is wine installed? On the root partition? I will try using gparted tomorrow night to improve my root partition´s size. Thanks.

Programs are installed in "bin" directories.
/bin : essential programs like cd, mv, ls, ...
/usr/bin : programs that come with the distro
/usr/local/bin : additional programs installed by the user

Note that this is not absolute and wine could be installed in any of those three.
I never installed it so I don't know, but you can easily find out where it is by typing > which wine
supposing that wine is the command used to run it. ;)

Generally anyway, all programs installed by the user are in /usr. (including program data, documentation and language files)
That's why the space allocated to /usr should be about 5-10GB.
Since in your case /usr is on the same partition as /, you'll have to increase the / partition.

edit:
And games usually get installed in /usr/games or directly in the home directory.

Note:
You can install programs elsewhere like in your home directory if you wish.
If you install from source, use > ./configure --prefix=<directory> to install in <directory> instead of just "./configure".
.deb packages can just be extracted instead of installed:
> dpkg -x <package>

You should then find the game in one of the bin directories inside the extracted directory.

Warning: If you use this method to install a program, you won't be able to uninstall it with the usual package management tools!!!
If you extracted the contents of the .deb, just delete the extracted files, if you installed from source, run "make uninstall".

---

