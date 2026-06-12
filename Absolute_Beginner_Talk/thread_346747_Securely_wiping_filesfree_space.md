---
title: "Securely wiping files/free space?"
date: 2007-01-26
forum: Absolute Beginner Talk
---

### Post by Catsworth on 2007-01-26
Hi Guys,

Is there any way to securely wipe files/free space within a Ubuntu install.

Previously I have used software (within Windoze) which overwrites the file/free space a set number of times, this effectively making it (and therefore the data in it) unrecoverable.

Is this possible in Ubuntu?  If so, could someone please point me at the program that I require.

Thanks.

---

### Post by cudjoe on 2007-01-26
You could give us the name of this software and look for an equivalent.
It is always a good method to find tools on Linux.

---

### Post by Pobega on 2007-01-26
Can't you just use the rm command from the terminal, or shift+delete from your file browser? I'm not sure if files are really recoverable after they're deleted, but I highly doubt it.

---

### Post by hyper_ch on 2007-01-26
I have something installed in Xubuntu and that put a "shredder icon" on the desktop.. looking at it it executes "kgpg -X %U" --> it's GPG for the KDE Desktop (I use it on Xubuntu because I have Kontact running there)...

Maybe for your gui also something exists...

---

### Post by Catsworth on 2007-01-26
> **Pobega said:**
> Can't you just use the rm command from the terminal, or shift+delete from your file browser? I'm not sure if files are really recoverable after they're deleted, but I highly doubt it.

Not sure how the *nix file system works but with Fat32/NTFS when you 'delete' a file it isn't removed from the disk.  A flag is set within the file system that tells the OS that the area of the disk that the file is in can be overwritten - this means that you can simply change that flag back and 'recover' the file.

---

### Post by Catsworth on 2007-01-26
> **cudjoe said:**
> You could give us the name of this software and look for an equivalent.
It is always a good method to find tools on Linux.

Can't remember the name of it unfortunately, it was part of my Windows install and I lost it when I reformatted the drive (don't seem to have anything on disk/disc either).  Anything that shreds files will do.

---

### Post by lamego on 2007-01-26
> Not sure how the *nix file system works but with Fat32/NTFS when you 'delete' a file it isn't removed from the disk. A flag is set within the file system that tells the OS that the area of the disk that the file is in can be overwritten - this means that you can simply change that flag back and 'recover' the file.
Unix file systems don't do this, when you delete the file the entry for it is completely removed, however the data is not erased untill new data gets over it.

---

### Post by Catsworth on 2007-01-26
> **lamego said:**
> Unix file systems don't do this, when you delete the file the entry for it is completely removed, however the data is not erased untill new data gets over it.

Ok, that's a start at least, but it could still leave orphaned data on the HDD.  If possible I'd like to be sure that I'm not leaving any trace of the data on the HDD.

Thanks for your input though.

---

### Post by lamego on 2007-01-26
Check this:
[http://ubuntuforums.org/archive/index.php/t-243881.html](http://ubuntuforums.org/archive/index.php/t-243881.html)

---

### Post by ComplexNumber on 2007-01-26
> **Catsworth said:**
> Ok, that's a start at least, but it could still leave orphaned data on the HDD.  If possible I'd like to be sure that I'm not leaving any trace of the data on the HDD.

Thanks for your input though.
there is a nice application called fslint. i couldn't find it in the repos, so i got the deb file from the homepage [here]("http://www.pixelbeat.org/fslint/"), then went to the terminal and installed it with 'sudo dpkg -i fslint*'. to delete anything outside of your home directory, it needs to be run from the commandline with 'sudo fslint-gui', BUT DON'T DELETE ANYTHING THAT YOU ARE UNSURE OF

---

### Post by Catsworth on 2007-01-26
> **lamego said:**
> Check this:
[http://ubuntuforums.org/archive/index.php/t-243881.html](http://ubuntuforums.org/archive/index.php/t-243881.html)

Thanks for that, doesn't look like what I want can actually be accomplished then as Ext3 is a 'journalled' file system....damn :(

---

### Post by willbur on 2007-01-26
Hi Catsworth
The Windows app you were trying to remember may have been Sure Delete. That overwrites all unused areas of your HDD with random data a number of times while leaving everything else alone. Sorry, but a Linux version isn't offered :( 
Hope this helps...

---

### Post by bugster on 2007-01-26
Didn't Norton Utilities for Windows have a wipe and/or secure wipe program to permanently delete data?  Unfortunately can't check as I no longer use it or have the cd.  But I'm pretty sure it was there.

---

### Post by Darko Beta on 2007-01-26
For Windows, I used CCleaner--a free utility (it stands for crap cleaner).  That sounds exactly like what you're talking about.  I was actually thinking about this recently because it was a great utility for wiping personal data, and it was very easy to manage cookies in firefox.  You could view all your cookies and pull in the ones you wanted to allow forever.  In Firefox settings you have to type in any cookies you want to keep, and it's difficult to account for the varying versions of urls.

---

### Post by punx45 on 2007-01-26
if you are looking to clean a whole drive or whole partition you can use 'dd'   I haven't used it personally, but I have read up on it, and I would consider it dangerous, and not noob friendly, so excercise caution.
Basically what dd does is it reads bit for bit from one device and writes to a partition (and possibly a file).   So basically, if you wanted to clean out a disk or partition you dd from /dev/null to the particular partition, etc. and it will write zeroes to it.   but like i said, I just read about it, have not tried it or anything else, as dd is a rather versatile tool. 

heres a wiki on it for general info:
[http://en.wikipedia.org/wiki/Dd_(Unix)]("http://en.wikipedia.org/wiki/Dd_%28Unix%29")

on a side, and somewhat related note, I also learned today that with some programs (fmt in my case) if you pipe a file back into itself you end up with a blank file.   In my case I started with a 100ish line file ```
fmt -w 75 ~/blog.txt > ~/blog.txt
```
and ended with a 0 line file.   Also interesting, attempting to cat and pipe a file into itself  resulted in an error and was not executed.

---

### Post by SyvanX on 2007-01-26
There is a unix utility called "shred"  It's included in coreutils, so everyone should have it.

It overwrites a file a specified number of times, with the option to delete the file when complete.  

```
man shred
```

---

### Post by kosmic on 2007-01-26
Yes 'shred' can do what you ask, but be carefull if you use a Journaling system

From the shred man page :

> 
CAUTION:  Note  that  shred relies on a very important assumption: that
       the file system overwrites data in place.  This is the traditional  way
       to  do  things, but many modern file system designs do not satisfy this
       assumption.  The following are examples of file systems on which  shred
       is not effective, or is not guaranteed to be effective in all file sys&#8208;
       tem modes:

       * log-structured or journaled file systems, such as those supplied with

              AIX and Solaris (and JFS, ReiserFS, XFS, Ext3, etc.)

       *  file  systems  that  write  redundant data and carry on even if some
       writes

              fail, such as RAID-based file systems

       * file systems that make snapshots, such  as  Network  Appliance’s  NFS
       server

       * file systems that cache in temporary locations, such as NFS



---

### Post by SyvanX on 2007-01-26
You're going to have those problems with any "secure" deletion program.  

The problems shred is referring to are due to caching data in other places, the journal.  Unless you plan on wiping the drive multiple times, then running it through a wood chipper, there isn't good way to reliably delete anything.  

Courtesy of Wikipedia, here is an entry for [file wiping]("http://en.wikipedia.org/wiki/File_wiping#File_wiping_on_journaling_file_systems")

```
dmesg | grep ordered
```
If that returns, "EXT3-fs: mounted filesystem with ordered data mode"  It means that your EXT3 journal is only journaling the metadata and not the contents of the file.  This is the default for new versions of EXT3 and is how mine is setup.

You should be able to successfully shred the data in place on EXT3 ordered data mode.

---

### Post by Catsworth on 2007-01-26
Unfortunately that doesn't return anything, nada, not a sausage.

I guess I'm out of luck then :(

Never mind, I guess I'll have to take extra special care of what I save where.

Thanks guys.

---

### Post by ineluki12 on 2007-01-28
Catsworth,
If you can configure firefox to store your cache in a tmpfs partition, all the data would go to ram instead of your hdd. Once you turn the computer off, *poof*, all gone. I looked for a method of changing your cache location in FF 2.0, but couldn't find one. There may be an option in about:config, though, didn't look there. Or, perhaps you could setup a symlink.

Also, all that stuff about having to write over deleted disk blocks several times to completely erase the data is rubbish. As long as *all* the data is covered at least once, it's g-o-n-e. I'm personally GCFA certified, and I can tell you nobody's going to take an electron microscope to your hd to see what you got mom for mother's day, or what sites you're looking at. Hard drives are getting too dense anyway. Here is what most professional labs and the government will most likely be using:
[http://www.sleuthkit.org/sleuthkit/tools.php](http://www.sleuthkit.org/sleuthkit/tools.php)

As long as all the disk blocks (not just the used sectors; watch out for slack space) are overwritten, the journal is touched up, and the filename erased through traditional deletion, the file cannot be recovered in any meaningful way. You will run into trouble clearing out the journal, though. Never tried that myself. If you want to do a whole drive, the dd method will definitely work well.

P.S. I definitely don't mean to start a flame war here. I'm speaking practically, not theoretically.

---

### Post by gpeck157 on 2007-02-06
[QUOTE=Catsworth;2065817]Hi Guys,

Is there any way to securely wipe files/free space within a Ubuntu install.

Previously I have used software (within Windoze) which overwrites the file/free space a set number of times, this effectively making it (and therefore the data in it) unrecoverable.

Is this possible in Ubuntu?  If so, could someone please point me at the program that I require.

Thanks.

[shred --help]

Glen

---

### Post by Ocxic on 2007-02-06
the XFS filesystem has no undelete policies, that was a selling point for me.

---

### Post by go2dell on 2007-02-12
You could also use *wipe*, which is available in Universe.  It has lots of options that greatly increase security.  Just be prepared to leave it running overnight, depending on what you're wiping.  An entire hard disk, even using the Quick options, takes hours, as it overwrites four times with different random data.

*dd* will also work fine, with the caveat that you will be responsible for inventing the data on your own.  Many of the "secure wipe" programs out there simply write over the file a few times with new data, for instance once with zeros, once with ones, again with zeroes.  You can easily do the same thing with dd.  You'll also note that hard drive manufacturers' "low level format" routines in their diagnostic utilities do exactly this, since low level formats haven't been possible for the end-user since the advent of IDE drives.

Unless you actually expect Homeland Security to take an interest in your drive, you can probably just use dd, especially if you will be keeping the drive.  If you want to wipe the whole drive, you can use something simple, like
```
dd if=/dev/zero of=/dev/hda bs=1k
```
which means for dd to write zeros (input file is /dev/zero) to the entire drive (output file is /dev/hda -- substitute with your drive letter here) using a block size of 1k (you can even leave this part off) and takes a very long time.  It will give an error message about no more space being on the drive when it's complete.

To very quickly make the drive appear new and ready for an OS install, you can just do
```
dd if=/dev/zero of=/dev/hda bs=512 count=1
```
which takes under a second.  This is also sufficient to "destroy" data for anyone who isn't sophisticated enough to use a data-recovery utility, which is the majority of users.

---

### Post by Catsworth on 2007-02-13
Great info, thanks - I'll give those two methods a whirl.

With *wipe* (or even *dd*) is it possible to specify individual files to be securely deleted?

---

### Post by go2dell on 2007-02-14
> **Catsworth said:**
> Great info, thanks - I'll give those two methods a whirl.

With *wipe* (or even *dd*) is it possible to specify individual files to be securely deleted?

Absolutely!

Remember that *everything* is a file in the *nix world, at least as far as identifying it to the O.S. goes.  Whether you're wiping a file, a whole partition, or an entire disk, it's all a file to Linux.

If you want to perform the operation on a single file, you can just do something like
```
dd if=/dev/zero of=/home/joeuser/filename bs=1k count=27
```
for a file in your home directory named "filename" that's 27k in size.

Then when it finishes
```

mv /home/joeuser/filename /home/joeuser/ridiculous_filename
rm /home/joeuser/ridiculous_filename
```.

You'll need a blocksize (bs) and count (count) to keep dd from writing until it runs out of room on the device, which it will be happy to do.  It understands various sizes, and for a full list you can just do
```
info dd
```.

The result is that the file becomes all zeros, and even if someone casually "undeletes" the deleted file, they'll only get zeros for their trouble.  For input file you could also use something like */dev/random* or */home/joeuser/text_of_the_Gettysburg_Address.txt* for fun.

*wipe* is much more thorough and you should really read the manpage on it before you use it, but the principle is much the same.  It writes over the file, 34 times as a default or four times for the quick option, and then deletes it, even zapping evidence of the filename for you.

One important note here:  if you're using a journaling filesystem (Ubuntu's default ext3 or the popular ReiserFS, for instance), running any kind of secure delete on the files is essentially meaningless.  Read the manpage for *wipe* for the full, paranoid explanation, but in short, the journal can keep lots of interesting information about the files you just deleted.  You basically have to eliminate the information from the journal if you want to make certain it's truly gone... and even then the disk might have an extra copy stashed away somewhere.  Read the *wipe* manpage if you really want to become nice and paranoid about this stuff. ;-D

---

### Post by yme on 2007-02-20
> **Pobega said:**
> Can't you just use the rm command from the terminal, or shift+delete from your file browser? I'm not sure if files are really recoverable after they're deleted, but I highly doubt it.

No, no and no again! It is extremely easy to recover that data with a tool such as Foremost:
[http://pcburn.com/data_recovery-Foremost.php](http://pcburn.com/data_recovery-Foremost.php)

Any hacker with a bit of computer knowledge could run it to recover whatever sensitive personal and financial data they like from your hardrive.

There seem to be many tools to overwrite such 'deleted' data in Windows and it seems to be pretty popular (BCWipe supposed to be among the best) so I'm surprised there none seems to be available for Ubuntu or Linux via standard add/remove applications procedures.

From what I have read Secure Delete from The Hackers Choice seems to be best tool for Linux allowing overwriting of free space and other features that Wipe does not have:
[http://www.thc.org/releases.php?o=1&s=4](http://www.thc.org/releases.php?o=1&s=4)

I have had quite some problems in trying to install it though.

---

### Post by go2dell on 2007-02-21
> **yme said:**
> 

From what I have read Secure Delete from The Hackers Choice seems to be best tool for Linux allowing overwriting of free space and other features that Wipe does not have:
[http://www.thc.org/releases.php?o=1&s=4](http://www.thc.org/releases.php?o=1&s=4)

I have had quite some problems in trying to install it though.

I'm not certain exactly why this utility would be better in any way than *wipe*, especially as it doesn't appear (from my reading) to allow one to choose any alternate methods for wiping a file.  Unlike wipe, it also requires learning several different commands to do different aspects of the same operation.  I also notice that the documentation is completely silent on ***any*** Linux filesystem, and is also completely silent on how wiping the journal is accomplished -- an important consideration since our filesystems are typically journaled.  The documentation also appears to be just plain wrong regarding the options available in wipe, beginning with the default number of passes it makes to delete a file, which is clearly stated in the man page.  Is there an additional source of documentation I didn't notice?

Wipe still seems to be far superior.

---

### Post by FRuMMaGe on 2007-05-02
> **Pobega said:**
> Can't you just use the rm command from the terminal, or shift+delete from your file browser? I'm not sure if files are really recoverable after they're deleted, but I highly doubt it.

"rm" doesn't delete the files, it just unlinks it from the filesystem

---

### Post by kitsuneymg on 2007-07-20
You can TRY srm (avalible in repository)

or you can drop the following into a file and sudo chmod 755 it and move it to /usr/bin/

This overwrites the files passed in 10 times with random data and then zeros it.
It is SUPPOSSED to overwrite in place. But with a journaled FS, who knows?

if you want higher entropy random data, change /dev/urandom to /dev/random, but this may be slower depending on how /dev/random works on your system.

#!/usr/bin/ruby
$*.map{|x|
  size = File.size(x)
  10.times{|i|
    str = "dd if=/dev/urandom of=\"#{x}\" bs=#{size} count=1 conv=notrunc 2>/dev/null"
    `#{str}`
    `sync`
  }
  `dd if=/dev/zero of="#{x}" bs=#{size} count=1 conv=notrunc 2>/dev/null`
  `sync`
  puts "#{x} shredded"
  File.delete(x)
}

---

