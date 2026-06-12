---
title: "FAT32 vs. ext3; no support for Japanese?"
date: 2006-06-07
forum: Absolute Beginner Talk
---

### Post by Sydney Losstarot on 2006-06-07
Two main things about this thread:

1. Could you guys give me some pros/cons of going with a FAT32 partition instead of an ext3 partition?

2. I just tried booting ubuntu, and it did that forced filesystem check thing it does every 33 times a filesystem is mounted.  It told me that a file I have on some volume that has illegal characters in its name, and I eventually found myself back at the command line.  That's not really what I want to have happen.  Are the illegal characters the Japanese in the filename, or is there actually something wrong with the filename?  Can support for Japanese be downloaded?

Edit:

I had 'fsck' fix the problems with the offending files, but I accidentally deleted the backups of them.  Not a problem, it was just a ripped CD, but I was wanting to see what 'fsck' did to them to fix them.

---

### Post by fluffington on 2006-06-07
> **Sydney Losstarot]
1. Could you guys give me some pros/cons of going with a FAT32 partition instead of an ext3 partition?
[/QUOTE]

FAT32 doesn't have permissions, links, flags, or case sensitivity, all of which are very nice things to have in Linux. FAT32 can, however, be read and written by both Windows and Linux, whereas Windows can't even see ext3 partitions, let alone read or write from them.

The only good reasons I've heard for going with FAT32 are being able to boot Linux and Windows from the same partition (which is sometimes useful, but more often than not, a bad idea), and transferring files between the two operating systems (so long as I have Windows and Linux living in the same box, I'll keep an extra partition around for this said:**
> 
2. I just tried booting ubuntu, and it did that forced filesystem check thing it does every 33 times a filesystem is mounted.  It told me that a file I have on some volume that has illegal characters in its name, and I eventually found myself back at the command line.  That's not really what I want to have happen.  Are the illegal characters the Japanese in the filename, or is there actually something wrong with the filename?  Can support for Japanese be downloaded?

Edit:

I had 'fsck' fix the problems with the offending files, but I accidentally deleted the backups of them.  Not a problem, it was just a ripped CD, but I was wanting to see what 'fsck' did to them to fix them.

Can't help you there, but at least you got it working.

---

### Post by Horizon on 2006-06-07
My Ubuntu always has problems with Japanese characters from windows computers. People on windows usually use a weird encoding that just doesn't work in Ubuntu because its language support sucks. Even when talking to people in Instand Messaging software I have to ask them to change their encoding to something "ubuntu-compatible" so I can actually read it, which really sucks. They really have to pull their socks up in the language support area. I just hope it won't take them too long, they seem to be aware of the problem. Who knows, they may me working on it as we speak.

---

### Post by dmizer on 2006-06-07
[QUOTE=Horizon]My Ubuntu always has problems with Japanese characters from windows computers. People on windows usually use a weird encoding that just doesn't work in Ubuntu because its language support sucks. Even when talking to people in Instand Messaging software I have to ask them to change their encoding to something "ubuntu-compatible" so I can actually read it, which really sucks. They really have to pull their socks up in the language support area. I just hope it won't take them too long, they seem to be aware of the problem. Who knows, they may me working on it as we speak.[/QUOTE]
i've never had a problem with japanese viewability on my machine, and since i actually live in japan, i use alot of japanese file naming, as well as alot of file shares between japanese windows boxes and my ubuntu box.

i think the problem is not ubuntu, but rather windows.  because i know for a fact that window's japanese support DOES suck.  especially if you're trying to use japanese on a non-japanese os version of windows.  just a few examples of problems encountered with japanese on english version windows:
1) no japanese ability in file names
2) limited japanese support in native applications (ie. no japanese in notepad etc)
3) no japanese keyboard support
4) no japanese in cli

if you're having problems viewing japanese sent to you from windows computers in ubuntu, i suggest you take another look at your install of japanese support, because my guess is that it's not complete.

---

### Post by catlett on 2006-06-07
[http://packages.ubuntulinux.org/dapper/translations/language-pack-gnome-ja-base](http://packages.ubuntulinux.org/dapper/translations/language-pack-gnome-ja-base) Ubuntu keeps to a 1 cd install philosophy. So it doesn't pack every conceivable package in with the install. It is meant to get you up and running quickly and then you add to your system from the repositories.
This link is the japanese language pack (just in case you didn't download it already)

P.S. This is the ubuntu japanese language "updating" pack. [http://packages.ubuntulinux.org/dapper/translations/language-pack-gnome-ja](http://packages.ubuntulinux.org/dapper/translations/language-pack-gnome-ja) It is needed to make sure you get the latest updates to the language pack. (don't ask me why updates aren't automatic, I'm just copying from the ubuntu package document)

---

### Post by Horizon on 2006-06-07
[QUOTE=dmizer]1) no japanese ability in file names
2) limited japanese support in native applications (ie. no japanese in notepad etc)
3) no japanese keyboard support
4) no japanese in cli

if you're having problems viewing japanese sent to you from windows computers in ubuntu, i suggest you take another look at your install of japanese support, because my guess is that it's not complete.[/QUOTE]
I am pretty sure I have everything, how did you install yours?

I'm pretty sure windows does all those things you listed by the way (other than cli) if you install the right stuff. Also viewing japanese files on shares doesn't exactly work the same way as viewing them locally. I can also view them fine through shares but it's when I transfer them to my computer using an external drive or something that I get garbage characters. I also frequently get filenames with garbage characters when people send files to me. I asked around and it seems the only way to get proper japanese support would be to install the japanese version of ubuntu instead of the english version + ja support. I just gave up and have been renaming stuff manually...installing the japanese version of ubuntu would be more hassle than it's worth:-k

---

### Post by fluffington on 2006-06-07
[QUOTE=dmizer]1) no japanese ability in file names
2) limited japanese support in native applications (ie. no japanese in notepad etc)
3) no japanese keyboard support
4) no japanese in cli
[/QUOTE]

I got all but #4 to work fine in Windows XP back when I was taking Japanese classes. Even had Japanese handwriting recognition (which worked significantly better than the English HWR, but that may just be my sloppy handwriting).

It took a significant amount of effort, though, and the default setup is most definately not compatible with non-western languages.

---

### Post by Sydney Losstarot on 2006-06-07
> **fluffington]The only good reasons I've heard for going with FAT32 are being able to boot Linux and Windows from the same partition (which is sometimes useful, but more often than not, a bad idea), and transferring files between the two operating systems (so long as I have Windows and Linux living in the same box, I'll keep an extra partition around for this said:**
> 

I would do that, if I knew that what I am going to try won't work well.  I'm trying 'fs-driver', an interesting program for making ext2 and ext3 partitions usable from Windows.  I'm not sure how it'll work, but I've formatted a partition as ext3, installed 'fs-driver', and I plan on using that partition as my main data partition for both Windows and ubuntu.  I hope it works well, as I'm eager to take advantage of ext3's ... advantages ... over FAT32.

[QUOTE=dmizer]if you're having problems viewing japanese sent to you from windows computers in ubuntu, i suggest you take another look at your install of japanese support, because my guess is that it's not complete.

That's entirely possible.  I did just reinstall Windows, and I never actually checked some of my files with Japanese filenames to see if they display correctly.  I'll probably check that right now.

Edit: Turns out I don't have my Japanese installed properly in Windows.  I just booted into Windows and checked a folder name that should have some katakana in it.  There were a bunch of question marks instead.  I can't remember right now exactly how I went about adding Japanese language support last time, but I'm going to say that's because I'm tired.

[QUOTE=catlett]http://packages.ubuntulinux.org/dapp...-gnome-ja-base Ubuntu keeps to a 1 cd install philosophy. So it doesn't pack every conceivable package in with the install. It is meant to get you up and running quickly and then you add to your system from the repositories.
This link is the japanese language pack (just in case you didn't download it already)[/QUOTE]

Makes sense.  And I appreciate the reference; I'll download is very soon, and make sure to get the updater.

---

### Post by dmizer on 2006-06-07
[QUOTE=fluffington]It took a significant amount of effort, though, and the default setup is most definately not compatible with non-western languages.[/QUOTE]
i should have clarified i guess.  i haven't played with xp very much, so my experience is with win2000.  where (to be completely honest) i did actually get japanese keyboard to work as well ... with a registry hack.

if you can read japanese ... there is a very active ubuntu/japanese community here: [http://www.ubuntulinux.jp/](http://www.ubuntulinux.jp/) 

the guide i followed is here: [https://wiki.ubuntu.com/JapaneseInputHowto?highlight=%28japanese%29](https://wiki.ubuntu.com/JapaneseInputHowto?highlight=%28japanese%29) ... there's one for dapper too.

---

### Post by fluffington on 2006-06-08
[QUOTE=dmizer]if you can read japanese ...[/QUOTE]

It's been a while since I was even remotely proficient in Japanese. I've been meaning to pick it back up, though. Thanks for the links.

---

### Post by Sydney Losstarot on 2006-06-08
I've downloaded both of the packages you referred me to, catlett, and I still see question marks where there should be katakana.  I'm using nautilus.  I can't seem to get to my file using the terminal (see below).

Did I do it right?  I just clicked on the link towards the bottom of the page, under the Download section, under Architecture, and told it to open with the GDebi package installer, which it seemed to do after it was done downloading (it looked like it installed really quick).  Then I rebooted.

Since that didn't seem to work, I tried downloading the "metapackage" that the page you referred me to recommends, and when I get to installing it, the package installer tells me that the same thing is available from a software channel, and recommends that I download that version.  Where can I find this software channel?

Does the terminal not like spaces?  I seem to be unable to navigate into directories that have spaces in them, using 'cd'.  It tells me the file doesn't exist, and then I 'ls', and it shows me the file with spaces I'm trying to get to.  What's going on here?

Should anybody else have info on my FAT32 vs. ext3 question, go ahead and tell me.  Or if fluffington pretty much covered it, tell me that too.  I'm kinda uninformed here.

---

### Post by dmizer on 2006-06-19
the shell doesn't care if there is a space in your file/folder name or not.  but you have to type the name a special way so that the cli doesn't think you're entering a new command.

here's an example from my own directory:
the file name in question is: Japan export_Basis OWB.  if i want to view this file, i have to tell the shell that the space is a space in the file name and not a break for a new command by typing a "\" in front of the space like so:
```
nano Japan\ export_Basis\ OWB
```
kind of a pain really.  but there's an easier way.  if you look at my directory, i have the following files:
```
Backup.tar.gz  essential-20060611  ifsig.txt~              linksys
Desktop        ifsig.txt           Japan export_Basis OWB
```
notice, there's only one file that starts with the letter "J".
so if i type: somecommandhere J<tab> (or whatever first characters are distinguishing) the shell will fill in the rest of the file name for you with the \ marks in it and everything.  the tab key simply takes a look in the directory for matching characters and fills in the rest of the untyped information for you.  a VERY handy feature.

as for your japanese problem, i'm not sure why you're having a problem at all.  i just followed the wiki for japanese input, and i have 100% viewability for japanese filename resolution in cli or otherwise, as well as japanese input ability in cli, and any other program i've tried (incliding volume names on cd's in k3b).

the files you're trying to view with japanese names ... are they saved locally?  ie. are they in your home folder on your ubuntu box?  have they ever been saved on an english version of windows before you tried to view them on your ubuntu box?

english windows really has no idea what to do with japanese file names.  for example, if you do a defrag on a fat32 volume, the defrag will destroy the file name as well as damage the file itself.  using a winzip to create an archive with japanese filenames included will kill the file and the file name unless you use a version of winzip that has japanese resolution.  virus scanners in english windows also do not have any idea what to do with japanese file names and sometimes mark them as viral.

so, even though everything may look hunky dory when you browse your windows files through explorer, things are not necessarily as they seem.  for japanese file name resolution in windows, the only way to really accomplish this is to install a japanese version of windows.

---

### Post by nge on 2008-04-08
hi .. 
I guess I fell into the same problem. Installed Gutsy 5 days ago. Last using Linux was Mandrake 9, then migrated into XP until now.

If I put my FAT32 partitions into fstab, I'll get a complete fs check at every boot. It ALWAYS told me that a file I have on that volume has illegal characters in its name, and afterwards renamed the file into 000*. And it also happens that that file's name has at least one Japanese or Korean character.

Any ideas? It really messes up with the iTunes in the Windows side.. 

Currently, I wiped the entries for that FAT32 volume in fstab. Interestingly, the filenames appear correctly after logon, be it mounted with fstab or manually. I guess all I need is disabling the automatic dosfsck at every boot. Hmm, how ? [currently Googling..]

Can I come into conclusion that dosfsck itself is messing up with Japanese/Korean characters?

---

### Post by ByteJuggler on 2008-04-08
> **fluffington said:**
> whereas Windows can't even see ext3 partitions, let alone read or write from them.

A correction: There is a driver for Windows that will allow it to read and write EXT2/3 filesystems, [here]("http://fs-driver.org/").

---

### Post by nge on 2008-04-09
Okay. So I gave the fstab a few zeroes at the end of the lines.

Guess that will solve my problem ..

---

### Post by nge on 2008-04-09
Okay. So I gave the fstab a few zeroes at the end of the lines.

Guess that will solve my problem ..

[edit] double post because of network failure .. now how do I delete this ?

---

### Post by zhanglini on 2008-04-29
I don't mean to hijack the thread, I have a similar problem with Chinese characters.
Basically I have XP and Hardy dual boot, and use a FAT32 partition to share between the two OSs.  Some of the file/folder names are in Chinese, they are fine in XP, but are a bunch of ???'s in Hardy.
Anyone know how to fix this?
Thanks in advance

---

### Post by ASULutzy on 2008-04-29
Just FYI, I believe there are things that can be installed in Windows to read ext3. EXT2IFS works I believe, and there are a couple others... I think one may even be able to write to ext3, it's been a while though

---

### Post by hellonull on 2008-04-30
I've tried a lot of the ext2/ext3 drivers for Windows (Vista) but all of them have caused fsck to run on my ext3 partition at the next boot for Ubuntu.

Also, mounting NTFS/FAT32 drives with UTF-8 enabled helped resolve my issues with illegal characters. Not sure if it will work for any of the Asian languages though, as my problems were with accented western characters. To see if this will work simply add "utf8" to the list of options for the drive in fstab.

---

### Post by zhanglini on 2008-04-30
Yeah, I got my chinese file name problem fixed (on FAT32) by adding "iocharset=utf8".

---

### Post by ByteJuggler on 2008-04-30
> **ASULutzy said:**
> Just FYI, I believe there are things that can be installed in Windows to read ext3. EXT2IFS works I believe, and there are a couple others... I think one may even be able to write to ext3, it's been a while though

Which is what I said already a few posts up... :confused:  (included a link as well)

---

