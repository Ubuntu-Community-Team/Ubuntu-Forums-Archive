---
title: "How do you &quot;rm | grep&quot; correctly?"
date: 2007-12-14
forum: Absolute Beginner Talk
---

### Post by jingo811 on 2007-12-14
I have this on my webhost with shell access and I want to remove all the *.html~ files.
How do I pipe the "rm | ls | grep" commands correctly for this task?
```
/html/renaissance/ndiswrapper2$ ls
allsparks.css~   chapter2.html~  chapter5.html   chapter7.html~  css
chapter10.html~  chapter3.html   chapter5.html~  chapter8.html   css colors~
chapter1.html    chapter3.html~  chapter6.html   chapter8.html~  gfx
chapter1.html~   chapter4.html   chapter6.html~  chapter9.html   index.html
chapter2.html    chapter4.html~  chapter7.html   chapter9.html~  index.html~

```

I only manage to do an ls pipe but not removing things.
"rm | grep html~" didn't work :confused:

```
/html/renaissance/ndiswrapper2$ ls -l | grep html~
-rw-r--r-- 1 gara gara  4429 2007-08-07 11:15 chapter10.html~
-rw-r--r-- 1 gara gara  6730 2007-08-11 17:46 chapter1.html~
-rw-r--r-- 1 gara gara  8752 2007-08-11 17:47 chapter2.html~
-rw-r--r-- 1 gara gara  5664 2007-08-11 17:48 chapter3.html~
-rw-r--r-- 1 gara gara 11714 2007-08-11 17:48 chapter4.html~
-rw-r--r-- 1 gara gara  8875 2007-08-11 17:48 chapter5.html~
-rw-r--r-- 1 gara gara  6828 2007-08-11 20:16 chapter6.html~
-rw-r--r-- 1 gara gara  6535 2007-08-11 18:05 chapter7.html~
-rw-r--r-- 1 gara gara  5119 2007-08-11 17:58 chapter8.html~
-rw-r--r-- 1 gara gara  4912 2007-08-11 19:56 chapter9.html~
-rw-r--r-- 1 gara gara  4524 2007-12-14 20:59 index.html~
```

---

### Post by SOULRiDER on 2007-12-14
Try 
```
ls -l | grep html~ | rm
```

---

### Post by llamakc on 2007-12-14
xargs will do it but be very careful. 

```

ls *.html~

```

If THAT list is EXACTLY what you want to remove, THIS will work. Be forewarned, it WILL remove the files that match.

```

ls *.html~ | xargs rm

```

DO NOT run that until you are certain it does what you want it to.

---

### Post by jingo811 on 2007-12-14
```
gara@sama:~/Desktop/html/z_Backups/Ndiswrapper_tgz$ ls -l *.html~
-rw-r--r-- 1 gara gara  4429 2007-08-07 11:15 chapter10.html~
-rw-r--r-- 1 gara gara  6730 2007-08-11 17:46 chapter1.html~
-rw-r--r-- 1 gara gara  8752 2007-08-11 17:47 chapter2.html~
-rw-r--r-- 1 gara gara  5664 2007-08-11 17:48 chapter3.html~
-rw-r--r-- 1 gara gara 11714 2007-08-11 17:48 chapter4.html~
-rw-r--r-- 1 gara gara  8875 2007-08-11 17:48 chapter5.html~
-rw-r--r-- 1 gara gara  6828 2007-08-11 20:16 chapter6.html~
-rw-r--r-- 1 gara gara  6535 2007-08-11 18:05 chapter7.html~
-rw-r--r-- 1 gara gara  5119 2007-08-11 17:58 chapter8.html~
-rw-r--r-- 1 gara gara  4912 2007-08-11 19:56 chapter9.html~
-rw-r--r-- 1 gara gara  4044 2007-10-27 18:42 index.html~
gara@sama:~/Desktop/html/z_Backups/Ndiswrapper_tgz$ ls -l *.html~ | xargs rm
[COLOR="Red"]rm: invalid option -- w
Try `rm --help' for more information.
[/COLOR]
```

It didn't work.  And as usual "man xargs" only made my head more confused than ever :confused:

......(one moment later)......	:oops:
Sorry I shouldn't have used "ls -l" when I only used "ls" it worked like you promised.  Hooray!

---

### Post by llamakc on 2007-12-14
I use that command all of the time, and verified that it would work with file~'s with the tilde after the name, and it worked.

I'm uncertain where you're getting the stray "w" as an option.

EDIT: COOL. Problem solved. Be careful with `xargs` and pipes. It is very powerful.

---

### Post by jingo811 on 2007-12-14
One last question.
As you can see I had other ~files initially but I didn't dare do just use *~ to remove files.

```


gara@sama:~/Desktop/html/z_Backups/Ndiswrapper_tgz/ndiswrapper2$ ls -l *~
-rw-r--r-- 1 gara gara  4045 2007-08-01 13:11 allsparks.css~
-rw-r--r-- 1 gara gara  4429 2007-08-07 11:15 chapter10.html~
-rw-r--r-- 1 gara gara  6730 2007-08-11 17:46 chapter1.html~
-rw-r--r-- 1 gara gara  8752 2007-08-11 17:47 chapter2.html~
-rw-r--r-- 1 gara gara  5664 2007-08-11 17:48 chapter3.html~
-rw-r--r-- 1 gara gara 11714 2007-08-11 17:48 chapter4.html~
-rw-r--r-- 1 gara gara  8875 2007-08-11 17:48 chapter5.html~
-rw-r--r-- 1 gara gara  6828 2007-08-11 20:16 chapter6.html~
-rw-r--r-- 1 gara gara  6535 2007-08-11 18:05 chapter7.html~
-rw-r--r-- 1 gara gara  5119 2007-08-11 17:58 chapter8.html~
-rw-r--r-- 1 gara gara  4912 2007-08-11 19:56 chapter9.html~
-rw-r--r-- 1 gara gara   106 2007-07-31 14:00 css colors~
-rw-r--r-- 1 gara gara  4524 2007-12-14 20:59 index.html~
gara@sama:~/Desktop/html/z_Backups/Ndiswrapper_tgz/ndiswrapper2$ 
```



But when I tried this then the file: "css colors~" remained while the file "allsparks.css~" got removed.  Is it becuase "css colors~" have a space in the filename?
And why did it try to remove my CSS directory?

```
$ **ls *~ | xargs rm**
rm: css: is a directory
rm: colors~: No such file or directory
```

---

### Post by llamakc on 2007-12-14
> **jingo811 said:**
> One last question.
As you can see I had other ~files initially but I didn't dare do just use *~ to remove files.

```


gara@sama:~/Desktop/html/z_Backups/Ndiswrapper_tgz/ndiswrapper2$ ls -l *~
-rw-r--r-- 1 gara gara  4045 2007-08-01 13:11 allsparks.css~
-rw-r--r-- 1 gara gara  4429 2007-08-07 11:15 chapter10.html~
-rw-r--r-- 1 gara gara  6730 2007-08-11 17:46 chapter1.html~
-rw-r--r-- 1 gara gara  8752 2007-08-11 17:47 chapter2.html~
-rw-r--r-- 1 gara gara  5664 2007-08-11 17:48 chapter3.html~
-rw-r--r-- 1 gara gara 11714 2007-08-11 17:48 chapter4.html~
-rw-r--r-- 1 gara gara  8875 2007-08-11 17:48 chapter5.html~
-rw-r--r-- 1 gara gara  6828 2007-08-11 20:16 chapter6.html~
-rw-r--r-- 1 gara gara  6535 2007-08-11 18:05 chapter7.html~
-rw-r--r-- 1 gara gara  5119 2007-08-11 17:58 chapter8.html~
-rw-r--r-- 1 gara gara  4912 2007-08-11 19:56 chapter9.html~
-rw-r--r-- 1 gara gara   106 2007-07-31 14:00 css colors~
-rw-r--r-- 1 gara gara  4524 2007-12-14 20:59 index.html~
gara@sama:~/Desktop/html/z_Backups/Ndiswrapper_tgz/ndiswrapper2$ 
```

But when I tried this then the file: "css colors~" remained while the file "allsparks.css~" got removed.  Is it becuase "css colors~" have a space in the filename?
And why did it try to remove my CSS directory?

```
$ **ls *~ | xargs rm**
rm: css: is a directory
rm: colors~: No such file or directory
```

xargs takes ALL output of the command fed to it, so it TRIED to remove the directory because the directory's name was in the output of your `ls` command.

Be careful about using the wildcard * like that. There are ways in BASH to accomodate for these issues like files with spaces in their names. I'll find a more comprehensive howto for BASH and link it in.

By the way, if you have installed ndiswrapper already, why do you need anything in that parent directory?

---

### Post by bodhi.zazen on 2007-12-14
what is wrong with :

rm -i ./*.html~

or

rm -i ./*~

The -i flag will give you warning before removing a file.

You can also :

rm -i `ls *~`

note, those are back tics by the number 1 and not single quotes.

---

### Post by jingo811 on 2007-12-16
> **llamakc said:**
> .......

By the way, if you have installed ndiswrapper already, why do you need anything in that parent directory?

Don't know what you mean but those file paths are only to my website tutorials I'm trying to work on which never seems to get finished by some peculiar way :)


> **bodhi.zazen said:**
> 
......

You can also :

rm -i `ls *~`

note, those are back tics by the number 1 and not single quotes.

I will try those sometime during this week.  By the way what is the purpose with those back tics?
I've seen tutorials with commands in OFFTOPIC situations use them while other tutorials ignores them alltogether.  Using similar looking commands.

---

### Post by llamakc on 2007-12-16
backticks are awesome. I always forget to use them. 

In the example above the command "rm -i" will be applied to the output of what is IN the backticks.

---

### Post by jingo811 on 2007-12-16
Another thing that confuses me is some Linux users say this using this character " (shift+2)
```
"rm -i"
```

While others suggest commands using this backtic character ` .
```
rm -i `ls *~`
```

Even though those 2 commands isn't identical these 2 conventions or ways to do things makes me confused and uncertain about what it does, mean and when to properly implement it :confused:

---

### Post by llamakc on 2007-12-16
> **jingo811 said:**
> Another thing that confuses me is some Linux users say this using this character " (shift+2)
```
"rm -i"
```While others suggest commands using this backtic character ` .
```
rm -i `ls *~`
```Even though those 2 commands isn't identical these 2 conventions or ways to do things makes me confused and uncertain about what it does, mean and when to properly implement it :confused:

They are not identical and represent different things. The backticks will execute the code & commands inside of the backticks. In my previous post I used double quotes around rm -i to show you the separation between that part and the stuff inside of the backticks.

---

### Post by bodhi.zazen on 2007-12-16
Yes. backtics `<command>` run the command between the backtics.

Many times in tutorials one wants to get the kernel headers, so, you can list the cruuent, running, kernel with :```
uname -r
```

So rather then assuming someone knows what kernel they are running, or listing an outdated kernel & having to update the tutorial,```
sudo apt-get install linux-headers-`uname -r`
```

So, uname -r, with back tics, fills in the running kernel and one can now proceed with compiling kernel or kernel modules.

Another example I use is is killing a process. Now you can use "top" or "ps aux | grep process" to get the PID and manually kill the process. If you know the process, say audacious, and killall audacious does not work, what to do ?

```
kill -9 `pidof audaciouis`
```

One step, done, RIP audacious :twisted:

HTH

---

### Post by jingo811 on 2007-12-16
Ah ic :) now I feel more secure about how to interpret instructions from other ppls tutorials in the future.
All this piping and backticking business is confusing :)

---

### Post by jingo811 on 2007-12-16
Another offtopic question.  How can I check the total amount of filesize in MB for a certain folder via Terminal?
Is piping involved this time for solving the problem?

```
gara@sama:/media/disk$ **df -h /dev/sda1**
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda1             123M   71M   53M  58% /media/disk
gara@sama:/media/disk$ **df -h /dev/sda1/html**
df: `/dev/sda1/html': Not a directory
gara@sama:/media/disk$ 
```

---

### Post by rukuartic on 2007-12-16
> **jingo811 said:**
> Another offtopic question.  How can I check the total amount of filesize in MB for a certain folder via Terminal?
Is piping involved this time for solving the problem?

```
gara@sama:/media/disk$ **df -h /dev/sda1**
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda1             123M   71M   53M  58% /media/disk
gara@sama:/media/disk$ **df -h /dev/sda1/html**
df: `/dev/sda1/html': Not a directory
gara@sama:/media/disk$ 
```

```

du -h /path/to/folder

```

This will list the contents of the folder, and the total size.

```

ls -lh /path/to/folder

```

This will list all the files in the current folder, but it will also list folders... Try it out

- Ruku

---

### Post by jingo811 on 2007-12-16
Tnx that worked liked a charm :-)

---

### Post by jingo811 on 2007-12-18
I have yet another off-topic question.
My mother have this 1GB USB stick that gets recognized as filetype NTFS in Ubuntu Feisty.  I'm guessing that you can't write to NTFS just by dragging files over.

In Debian Etch this stick gets recognized as filetype VFAT but still no dragging possible.  However I managed to write to it with terminal as root.  But my mother don't want to use the terminal for this she just want to copy and paste files via Nautilus.

So I'm thinking about reformatting the whole USB stick to FAT16,32 or VFAT.  How can I do that?
I already tried as root in Debian to mkfs but nothing.

> 
mike@debian:~$ **su -**
Password:
debian:~# **fdisk -l**

Disk /dev/hda: 15.0 GB, 15020457984 bytes
255 heads, 63 sectors/track, 1826 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1         608     4883728+  83  Linux
/dev/hda2             609        1826     9783585    5  Extended
/dev/hda5             609         730      979933+  82  Linux swap / Solaris
/dev/hda6             731        1826     8803588+  83  Linux

Disk /dev/sda: 999 MB, 999817216 bytes
21 heads, 20 sectors/track, 4649 cylinders
Units = cylinders of 420 * 512 = 215040 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        4650      976257    6  FAT16


debian:~# **mkfs -t vfat /dev/sda1**
[COLOR="Red"]mkfs.vfat: No such file or directory[/COLOR]
debian:~#



> debian:~# **df -Th**
Filesystem    Type    Size  Used Avail Use% Mounted on
/dev/hda1     ext3    4.6G  1.4G  3.0G  32% /
tmpfs        tmpfs     62M     0   62M   0% /lib/init/rw
udev         tmpfs     10M   64K   10M   1% /dev
tmpfs        tmpfs     62M     0   62M   0% /dev/shm
/dev/hda6     ext3    8.3G  124M  7.8G   2% /home
**/dev/sda1     vfat    954M   78M  876M   9% /media/sda1**
debian:~#

---

### Post by Majorix on 2007-12-18
Install ntfs-3g and you should be able to write to NTFS. If not, you probably don't have configured your computer to do so, so also install ntfs-config and enable writing to NTFS. But it usually works without ntfs-config.

EDIT: Also, if you still want to format it, you have to do it like this:
```
sudo mkdosfs -F 32 /dev/sda1
```
Or easier yet, you can use GParted.

---

### Post by jingo811 on 2007-12-20
I'm gonna try all your apt-get suggestions.  The weird thing is my experimentations PC using Debian Etch only have support for EXT2 / EXT3 and SWAP.  I can't access those others filesystems in the drop down list they are greyed out in Gparted. :confused:

Guess that removing and installing mkfs and mkdosfs from scratch should give me access to those other filesystems to play with.

---

### Post by jingo811 on 2007-12-23
ONTOPIC question again:
So Linux doesn't like files created with spaces in it.  As it has trouble identifying such files for deleteting.  How can I delete such files?

```

$ **rm -i css colors~**
rm: css: is a directory
rm: colors~: No such file or directory
$ **rm css colors~**
rm: css: is a directory
rm: colors~: No such file or directory
$ 
```

---

### Post by lgambett on 2007-12-23
Put the names with spaces inside quotes eg. 'name with spaces' or double quotes.

---

### Post by lgambett on 2007-12-23
...and you can also "escape" with a \ the blank, as in

rm file\ with\ spaces

that is the same as

rm "file with spaces"

or

rm 'file with spaces'

---

### Post by jingo811 on 2007-12-23
:mrgreen: TNX

---

