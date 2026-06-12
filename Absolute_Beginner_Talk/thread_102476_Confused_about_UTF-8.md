---
title: "Confused about UTF-8"
date: 2005-12-12
forum: Absolute Beginner Talk
---

### Post by CodyJarrett on 2005-12-12
Hi,
I'm a total newbie, so please excuse my ignorance ;) 

I've tried learning something about UTF-8, and it seems to me like it's the way to go!

However, I have some mounted VFat-discs with leftover stuff from Windows. On these discs I have all my mp3-files. When mounting these discs with ISO-8859-1 everything looks fine, but some of the music apps I'd like to use on Ubuntu can´t show characters like ÆØ and Å. 

Thats's why I thought that the best thing to do was to mount the discs with UTF-8, but now all the filenames look wrong in Nautilus... Björk looks like BjÃrk and so on...

I tried using the tool convmv to no avail... it just complains about the files not being encoded in ASCII, and I don't understand a thing..... :confused: 

What is the correct way of handling files? How do I change all filenames to UTF-8 - and is that the right thing to do?

Any help VERY appreciated!!!
Thanks!

---

### Post by Gustav on 2005-12-12
You can use the program utf8migrationtool to convert all your filenames in you home directory to utf8 (for some reason it doesn't work for me, but it might for you)

---

### Post by timetunnel on 2005-12-12
Here's how I solved this. I did that on dual boot systems with Windows 2000 / XP, so if you're running Windows 98 / ME, it might not help (I have no idea about their character encoding):

```
sudo gedit /etc/fstab
```

Find the line that is responsible for mounting you windows partition. In that line, I did some changes so it looks like this now (the options on the right of "vfat" are relevant for you):

```
/dev/hda6  /mp3  vfat  defaults,auto,uid=1000,gid=1000,utf8,shortname=winnt 0 0

```

short explanation:
these options tell "mount" to handle the file names and their character encoding on the windows (vfat) partition in a certain way. I have no access to a linux system right now, therefore I can't elaborate more right now, but if you do a 
```
man mount
```
an read the part about the "shortname" option, you might get a hint.

I don't remember exactly why I had to set "uid" and "gid" to 1000, but it only worked this way for me (another solution might have been to create a new group, add users to that group and put it's "gid" in there, but I'm the only one on my system, and my uid is 1000, so it justed worked).

Jens

---

### Post by CodyJarrett on 2005-12-12
thanks a lot for your answers.

utf8migrationtool can only scan my home folder, but I have all my mp3 on the FAT partition, and the utf-conversion.sh script does not seem to work right for me - it gives me an error message everytime I ask it to scan:

morten@ubuntu:~$ /media/BACKUP1/mp3/Bob Hund/Bob Hund/ bash: /media/BACKUP1/mp3/Bob: No Such File or Folder

It seems that it has problems with spaces?

The UTF-8 option in fstab does not seem to work either. I think it enables UTF-8 alright, but Nauilus still displays filenames like this: 

bob hund - 10 ÃÂÃÂ¥r bakÃÃÂ¥t och 100 framÃÂÃÂ¥t - 01 - ett fall och en lÃÂÃÂ¶sning.mp3

Not very pretty :( 

Is this only a case of seek and replace? Or is it more complicated?

And would I be better of formatting my discs to EXT3?

---

### Post by timetunnel on 2005-12-12
[QUOTE=CodyJarrett]
morten@ubuntu:~$ /media/BACKUP1/mp3/Bob Hund/Bob Hund/ bash: /media/BACKUP1/mp3/Bob: No Such File or Folder
It seems that it has problems with spaces?
[/QUOTE]
If you don't use colons, the "Hund" part is interpreted as option you are passing, not as part of the directory. Therefore, if you have spaces in filenames, you always have to use colons:
```
morten@ubuntu:~$ cd "/media/BACKUP1/mp3/Bob Hund/Bob Hund/"
```

> The UTF-8 option in fstab does not seem to work either
Did you remount the partition after you changed fstab (I forgot to mention this in my previous post)? To see the changes in Nautilus, a logon/logoff from GNOME might be neccessary (or: just reboot your system)

> And would I be better of formatting my discs to EXT3?
If you're sure you never need to access the partition from a Windows OS again, it's certainly better to switch to a Linux file system like EXT3 (there are some tools to access an EXT3 partition from Windows, but they can only **copy** files from EXT3 to your Windows partition, so they won't be useful if you want to organize your mp3s in iTunes, for example).

Jens

---

### Post by Arwyn on 2005-12-12
Have you tried setting the iocharset and codepage of the vfat partition?

For all the mount options RTM (man mount). You want the fat and vfat sections.

Also I noticed you were trying to execute a directory above. You probably meant:
fake@ubuntu:~$ **ls** /meadia/BACKUP1/mp3/Bob**\** Hund/

Try using the tab-autocompletion feature. Not only does is speed up typing, but it also makes sure you don't make silly typos :)

As for using EXT3, well if your system is 100% linux or if you don't need windows to be able to read those mp3s then yes a native journaling filesystem would be better, but I'd suggest ReiserFS over Ext3.

---

### Post by CodyJarrett on 2005-12-12
hello again - and thanks for the answers,

I accidentally inserted the wrong code-snippet - here's the right one:

morten@ubuntu:~$ sh utf-conversion.sh "/media/BACKUP1/mp3/Bob Hund/"
find: /media/BACKUP1/mp3/Bob: No such file or directory
find: Hund/: No such file or directory

I try to convert the contents of the folder "Bob Hund" to UTF-8 with the script, but it gives me this error whether I use colons or not.

Arwyn - I don't know much about this (although I tried reading all kinds of stuff about utf-8 vs. iso, but would it not be best for me to convert all the filenames on my FAT-partition to UTF-8 to ensure compatibility with Linux applications? I think this is my main question.

As I stated before, everything looks peachy in Nautilus when I mount the FAT-disc with Iso-8859-1, but then the files look wrong in the Linux mp3-apps... sigh...

I would really like to learn - I appreciate all the feedback :smile:

---

### Post by az on 2005-12-12
[QUOTE=CodyJarrett]When mounting these discs with ISO-8859-1 everything looks fine[/QUOTE]

I seem to remember only ever using 8859-10 (or was it 8859-15) for this reason, but I may be wrong.  I am not at home to see, right now...

---

### Post by CodyJarrett on 2005-12-12
What I would really like is to convert all filenames to utf-8 so that they look and act right in for instance Quod Libet, which seems to be my favourite mp3 manager/player for now (Amarok looks cooler, but that didn't really work for me in Gnome).

Is this possible? Or should I try another way? Please help :confused:

---

### Post by az on 2005-12-12
dora@dora:~$ apt-cache show convmv
Package: convmv
Priority: optional
Section: universe/utils
Installed-Size: 88
Maintainer: Raphael Zimmerer <killekulla@rdrz.de>
Architecture: all
Version: 1.08-1
Depends: perl
Filename: pool/universe/c/convmv/convmv_1.08-1_all.deb
Size: 17478
MD5sum: 6331f9c2e0cb72f63debe60b5f7fdc2d
Description: filename encoding conversion tool
 convmv can convert a single filename, a directory tree or all files
 on a filesystem to a different encoding. It only converts the
 encoding of filenames, not files contents. A special feature of
 convmv is that it also takes care of symlinks: the encoding of the
 symlink's target will be converted if the symlink itself is being
 converted.
 .
 It is also possible to convert directories to UTF-8 which are already
 partially UTF-8 encoded.
 .
 Keywords: rename, move
Bugs: mailto:ubuntu-users@lists.ubuntu.com
Origin: Ubuntu




dora@dora:~$ apt-cache show utf8-migration-tool
Package: utf8-migration-tool
Priority: optional
Section: misc
Installed-Size: 176
Maintainer: Tollef Fog Heen <tfheen@canonical.com>
Architecture: all
Version: 0.3
Depends: python (<< 2.5), python (>= 2.4)
Filename: pool/main/u/utf8-migration-tool/utf8-migration-tool_0.3_all.deb
Size: 15606
MD5sum: 48969c8289420fa92f12fe38a36eaa47
Description: convert to UTF-8 locale including renaming of files
 This program will change your default locale to the equivalent UTF-8
 locale to the one you are using.  It will also rename any files to
 the equivalent UTF-8 file name.
Bugs: mailto:ubuntu-users@lists.ubuntu.com
Origin: Ubuntu

---

### Post by CodyJarrett on 2005-12-16
Thanks, azz, but I know these applications already, and I have tried to run them, but everytime I let convmv convert my Latin1 files to UTF-8 it also adds all these weird characters, like Ã and so on.

An example: 

1) I create a folder named æøå on my fat-disk. 
2) I open a terminal and write:

convmv --notest -r -f latin1 -t utf-8 /media/fatdisk/æøå

3) After this the æøå-folder looks like this: Ã¦Ã¸Ã¥

why? :confused:

---

### Post by CodyJarrett on 2005-12-17
Please, guys, I really need some help!!!

How do I convert everything on all my disks to UTF-8?

Utf8-Migration-Tool doesn't work. 
Convmv doesn't work.

What am I doing wrong?:confused: :confused:

---

### Post by adamkane on 2006-03-05
convmv Nautilus script:
[http://www.ubuntuforums.org/showthread.php?t=139154&highlight=convmv](http://www.ubuntuforums.org/showthread.php?t=139154&highlight=convmv)

---

### Post by adamkane on 2006-03-05
!

---

