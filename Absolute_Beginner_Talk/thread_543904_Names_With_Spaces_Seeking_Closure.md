---
title: "Names With Spaces: Seeking Closure"
date: 2007-09-05
forum: Absolute Beginner Talk
---

### Post by _crash_ on 2007-09-05
Hi everybody,

First off, I apologize for the length of this post.  Sorry!

The topic of this thread is about folder / file naming with spaces in Linux.  

So everybody knows, I did some homework before posting this.  I feel that this thread should prove to be different than others on this forum that have talked about this topic.  

I am trying to formulate a concrete policy for myself that I will use from this point forward, not just solve my current problem.  

I welcome all opinions!

All roads point back to the user right?  I am right now in kind of a gray area.  I know enough about Ubuntu to be comfortable with it in the GUI.  (No big accomplishment there, granted).  But I still have not had the time to take the plunge and learn Bash programming.  So, the CLI is still a struggle for me.  I have messed around with Bash some, but very little.  I basically live in the Gnome GUI.  So anyway that is where I am at right now.

As I said, I did some research before posting this.

Examples:

The [[COLOR="Red"]Puppy Linux FAQ[/COLOR]]("http://www.puppyos.com/faq.htm") has a nice explanation of why not to use spaces in folder and file names.  (If you want to see said explanation, select the above link and scroll down to "Q: Spaces in filenames and directory names").

[[COLOR="Red"]tuXfiles has a page[/COLOR]]("http://www.tuxfiles.org/linuxhelp/weirdchars.html") that talks about the subject some.

I also read several posts on the Ubuntu Forum.  (I used the search feature to find said posts).

I had more web pages bookmarked than what I have shown here.  And I was going to include said web pages in this post.  But for some reason I can not find said bookmarks.  (Sorry).

Anyway, the point is, I read up on this subject before posting.

Recently somebody gave me a P2 with a 4G native Travan tape drive in it.  The CPU was not used much at all.  And I REALLY need a tape drive, so this P2 is going to be a real big help to me!

The power supply died on this P2 shortly after the CPU was given to me, and I have not gotten around to fixing it yet.  However, once I get the above P2 fixed, I am going to do a dual boot with Win NT 4 Workstation and Linux.  (The Linux distro used will probably be Ubuntu for the time being).

When I get the above P2 up and running, I was thinking about using [[COLOR="Red"]BackupPC[/COLOR]]("http://backuppc.sourceforge.net/").  BackupPC is GPL.



BackupPC Quick Overview
---------------------------------------------
BackupPC seems like what I want.  It can automatically grab data off of the workstations on your LAN, and mirror said data to the BackupPC CPU.  When doing incremental or differential back ups, it will back up only the part of the file that has changed.  This is great for large files.  

For the above reasons and also others not repeated here, BackupPC, (if it works as advertised), would really be a huge help to me.

Like other Linux apps that I have seen with a GUI front end, it appears that BackupPC is built on or uses Linux tools/modules already written by others to get the job done.  (Please correct me if I am wrong on this).  

A side note about BackupPC and tape drives.  The author of BackupPC says that there is some kind of archive function in BackupPC to get the data from the BackupPC CPU's hard drive to tape.  On the BackupPC site, if you go to the [[COLOR="Red"]Backup basics section[/COLOR]]("http://backuppc.sourceforge.net/faq/BackupPC.html#backup_basics") and scroll down to the "Backup Policy" sub-section you will see a blurb on this.  He also says that you can use [[COLOR="Red"]Amanda[/COLOR]]("http://www.amanda.org") or [[COLOR="Red"]Bacula[/COLOR]]("http://www.bacula.org") to get the BackupPC data to tape.

Anyway enough about BackupPC for now.

What got me started thinking about all the subject of this post was some problems I had with File Roller.  So I will use my problems with File Roller as an example of why I think I need to avoid the space character.  This happened on my Ubuntu CPU.  Everything I am going to explain here I did while in the Gnome GUI.



Main Data Folder
---------------------------------
I have a bunch of folders and files, all of which are located in one main data folder.  The main data folder is on my desktop.  

Here are the specs for the main data folder:

1374 items, totalling 70.7 MB

There are many files and folders in the above main data folder.  The folder's contents are nothing special.  PNG pics, text files, HTML files, etc..  Common data files, nothing exotic or large.  Everything that is important I keep in my main data folder.  Because one is "allowed" to use spaces in folder and file names, I did just that.  So in this main data folder, there are thousands of sub-folders and files in them that have spaces in their names.

Well, I should back the above folder up, right?  I have not learned much about Ubuntu since first installing it.  I just use it.  I installed Samba, but I have not seen if it works or not with my Win CPUs on my LAN.  So I figured for the time being I would just back up my main data folder to my flash drive.  I could then copy said data files over to one of my Win CPUs that has a CD-RW for archiving.

When first using Ubuntu, the main data folder was small, with only a few folders and files.  Backing up said folder via copy and paste to the flash drive went fine.  No errors.

But the more I used Ubuntu, the more I loved it.  It is so much more stable than Windows!  My Ubuntu CPU was used more and more, and my Win CPUs less and less.  

The Ubuntu CPU's main data folder started to grow.  I started going wild grouping my data files into many nested sub-folders, (as was my habit with Windows).  Throughout all of this, the quantity of sub-folders and data files grew.  The file sizes themselves remained small.

It was at this time that copying said folder to the flash drive started to bomb out.  I got error messages during the copy process.

Below are some samples of what I have experienced during one copy session to the flash drive.  I copied these error messages out of the error dialog box as the copying procedure progressed.


```

Error "Invalid parameters" while copying "/home/crash...y" email~".

Error "Invalid parameters" while copying "/home/crash/De...amera
 Notes~".

Error "Invalid parameters" while copying "/home/crash/Desktop/Sam...ftware v 5.2 Read Me~".

Error "Invalid parameters" while copying "/home/crash...config.png"
```



The above is only a sample of the error dialogs that I got.  In the above example, I actually told the error dialog box to skip  7 items while the copying process progressed.

In all, here is what made it across to the flash drive:

1371 items, totalling 70.5 MB

Repeating here for clarity, here is what the main data folder looks like on the desktop:

1374 items, totalling 70.7 MB

But like I said, I told the error dialog box to skip 7 items.  So I am wondering how much data really did not actually make it over to the flash drive during the copy process.  Anyway...

I know next to nothing about Linux.  So in my ignorance I thought that maybe the reason why this was happening was because the flash drive is FAT formatted, and maybe folders/files created on an EXT3 partition and a FAT formatted flash drive don't get along too well.  Or maybe because I am not supposed to store so much stuff on my desktop, but in my home directory instead.  

Either way, I thought maybe I could get around this problem by creating a TAR archive of the main data folder, and then copy the TAR archive to the flash drive.  (This method also had the added benefit of me being able to do an MD5 check sum on the desktop TAR archive and then compare it to an MD5 sum of the TAR archive on the flash drive).

I used File Roller to create the TAR archive of my main data folder.  I chose uncompressed TAR, (nothing fancy).

Then File Roller generated an error dialog.  In said dialog, the path of the offending folder was displayed, with the following text afterwords:



```
Cannot stat: No such file or directory
tar: Error exit delayed from previous errors
/bin/sh: line 1:  Notes~: command not found
/bin/sh: line 2: Software v 5.2 Read Me~: command not found
/bin/sh: line 3:  Notes: command not found

```


File Roller then quit the archive process, and the archive was empty from that point forward.

It was at this point I started looking at info about File Roller.  I discovered that File Roller is actually a GUI front end for some different tools that, (I assume), come with Linux.  Said tools appear to be CLI based.  And I am guessing that is why File Roller bombed out.  Because the vast majority of my nested folder names and file names all have spaces in them.  (I started using the underscore character recently, because I started to get scared of loosing data.  But I still have thousands of folders/files that have spaces in them).

As far as I understand it, if I were in the CLI, and just copying a few files around, I could quote or escape out the folder / file name(s) that have the spaces.  But I think that this technique will break down severely when I start using and heavily relying on an application like BackupPC.  I am saying this because I suspect that BackupPC is built on or heavily relies upon POSIX CLI applications.

It seems as if File Roller is like this.  If I am guessing right, File Roller is a GUI front end for several CLI applications.  I am guessing that in order to get File Roller to archive and un-archive folders / files that have spaces in them, I would have to do some fairly tricky modifications to File Roller and/or the CLI applications on which it may be built.  My situation would probably be even worse with an application like BackupPC.

I am NOT a programmer.  I have done some really basic programming in a few courses I had to take once.  But I know I do NOT have the expertise to take on modifying File Roller, BackupPC, or the applications that they may be built upon.

Like I mentioned earlier, I have done some playing around in the CLI.  But I just don't have the time to sit down and learn it now or at any time in the near future.  I just want to live in the Gnome GUI for now.  (And I am happy there, for the time being).

I am sure that there are some tricks I could use in the CLI to make the copy to the flash drive work.  But when I start to try to do the things that BackupPC can do, forget it.  I would rather just use an app like BackupPC and stay in the GUI.  For somebody like me, I can't imagine how hard it would be to back up stuff to a legacy tape drive via the CLI!  (Although I am sure that it probably can be done, right)?

For my Ubuntu CPU's main data folder, I could probably replace all of the space chars with underscore chars in a few hours.  It is not that big deal of a deal.  But I want to point out that the REAL reason why I did this post was to enlighten myself, not save myself a few hours of work at this time.



Conclusion
--------------------
If any of you could answer the following, that would be great!


1)
Is it not really better to NEVER use the space char when naming/re-naming folders and files in Linux?


2)
Does what I have recounted here about my flash drive and File Roller copying problem kind of prove point 1) above?


3)
Would it be fairly safe to say that an app like BackupPC would error out when trying to back up a folder whose contents are filled with folders/files whose names have spaces in them?

Earlier, I said that it seems as if BackupPC is built on or uses Linux tools/modules already written by others.  If the above statement is true, perhaps some or many of those modules are CLI based.  

If the above is true, then could it be said that it is almost critically important to avoid the space char in folder/file names when attempting to use an app like BackupPC?  Because if one did use the space char, I would think that similar errors or worse would happen like what I experienced with File Roller.  Correct?


4)
In regards to fixing my current problem with backing up my main data folder to the flash drive.  Should I go through and rename all folders/files that have spaces in their names to use the underscore char instead?  Whether I use File Roller or not when backing up to the flash drive?



Anyway, when using Linux, I am beginning to think that I should completely abandon using the space char in folder and file names.  Do you folks think that this sounds like the right thing to do in the long run?  Remember, I want to do things in the GUI as much as I possibly can.  I want to start using apps like BackupPC, etc., and I want them to work right.

Thanks for taking the time to read this long winded post!  Any and all opinions would be welcome!


Sincerely & Gratefully,


_crash_

---

### Post by Paul133 on 2007-09-05
I'd recommend you just use _ (underslash) instead of a space. It's not that hard, and you'll never have a problem. Seems like what you have to do now is replace all your spaces with underslashes. Don't do this by hand. If you really have tons of files and directories, it would not be worth it. Someone here (who's skilled in the ways of sed) can write you a simple script to do it. I'll look into it for you.

---

### Post by dwhitney67 on 2007-09-05
> 1)
Is it not really better to NEVER use the space char when naming/re-naming folders and files in Linux?
I personally do not like spaces in my file/folder names.  But there is nothing within Linux that prevents this. If you have a folder with the name of "My Documents", then precede the white-space with a \ character and all will be fine.  For example:
[FONT="Courier New"]
$ cd My\ Documents[/FONT]

"Is it not really better to NEVER" --- I would focus more in English composition than Linux if I were you.  :shock:


> 2)
Does what I have recounted here about my flash drive and File Roller copying problem kind of prove point 1) above?
I'm too lazy to read a post with over a 100 lines of text.  However I will guess the answer is "no".


> 3)
Would it be fairly safe to say that an app like BackupPC would error out when trying to back up a folder whose contents are filled with folders/files whose names have spaces in them?
If it does, it is a poorly written application.

> If the above is true, then could it be said that it is almost critically important to avoid the space char in folder/file names when attempting to use an app like BackupPC? Because if one did use the space char, I would think that similar errors or worse would happen like what I experienced with File Roller. Correct?
See the answer to question 1.


> 4)
In regards to fixing my current problem with backing up my main data folder to the flash drive. Should I go through and rename all folders/files that have spaces in their names to use the underscore char instead? Whether I use File Roller or not when backing up to the flash drive?
Up 2 you.  Like I said earlier, I personally do not like spaces in filenames/folders.  The reason for this is because I generally interface with Linux using the terminal (command line) and not the UI.  I guess I am an "old-school" Unix/Linux user.

---

### Post by Paul133 on 2007-09-05
Here's how you tar your main data folder wihtout worrying about spaces. You wll have to do this with the commandline, but don't worry. It's petty easy and I've tried to provide explanations as to what the commands do.
```
cd /the/path/to/the/directory/you/want/to/tar
``` will change directory to he one you want to tar.
```
tar -cvf ../main.tar *
``` will tar the directory and anyting in it and call the tar file 'main.tar'. It will be saved in the parent directory.
```
cd ..
``` will bring you to the parent directory.
```
mv main.tar /wherever/the/flash/drive/is/mounted
``` will move the tar to the flash drive and change directory to the flash drive.. You need to kow where the flash drive is mounted.
```
cd /wherever/the/flash/drive/is/mounted
``` will change the directory to wherever the flash drive is mounted. You only need to do this if you want to untar the file on the flash drive. You might prefer to put the flash drive in another computer and then untar it. Finally,
```
tar -xvf main/tar
``` will untar the tar file.

---

### Post by dwhitney67 on 2007-09-05
I hate hijacking a thread... but

Paul133,

Since it looks like you have a "lot" of Ubuntu experience, I have a question.  Why does everybody precede their tar command options with a '-' character?

I never do, and I am wondering if the results I get from creating and unpacking tar files differ from those who use that character.

---

### Post by Paul133 on 2007-09-05
Well, I wasn't sure. 'man tar' just showed options/flags with '-'. On further review, though, the '-' is optional. There's no difference. ' tar -cvf' and 'tar cvf' will do the same thing, so you don't have to worry.

---

### Post by dwhitney67 on 2007-09-05
> **Paul133 said:**
> Well, I wasn't sure. 'man tar' just showed options/flags with '-'. On further review, though, the '-' is optional. There's no difference. ' tar -cvf' and 'tar cvf' will do the same thing, so you don't have to worry.

That's a relief.

---

### Post by _crash_ on 2007-09-07
dwhitney67 and Paul133, 


Thanks for replying!

Unfortunately I have some other stuff come up that I have to deal with over the next couple of days or so.  Said stuff  prevents me from giving the kind of replies that I want to right now, due to lack of time.  But I promise I will reply to all of your posts here in this thread.  The stuff that you have said here so far is helpful!

Again, thanks for replying, I greatly appreciate your time to help me, and everything that you guys have said.  I will be back as soon as possible.


Thanks,


_crash_

---

### Post by Paul133 on 2007-09-07
No problem; I'm glad to help those who need help with Ubuntu. The thanks is greatly appreciated, though. :) Good luck.

---

### Post by _crash_ on 2007-09-21
Frustration!

But not with you guys though!  I am STILL trying to get my head above water on stuff.  Said "stuff" is preventing me from working on my computer for the past 2 weeks.  

I have not forgotten about this thread, and I want you guys to know I am going to get at this stuff as soon as I can.  (Hopefully in about 4 days or so).

Paul133, hey thanks for the CLI stuff!!!  Like I said above, as soon as I get my ducks in a row, I am going to try it.  Let me tell you, I GREATLY appreciate you coming down to my level and spelling everything out for me, (the CLI code that you gave me).  Just reading your reply, I can almost understand just about everything you suggested.  And I am anxious to get started on it.


> No problem; I'm glad to help those who need help with Ubuntu. The thanks is greatly appreciated, though.  Good luck.


Yes, well, the help is VERY MUCH appreciated by me!  I can't tell you what a relief it is to FINALLY begin to get a handle on this stuff after banging my head against the wall for so long.  I have been trying to do things on my own and not be an excessive burden on the Ubuntu / FOSS community and everything.  But I finally gave up and had to ask for help.

Again Paul133, I want to thank you for being so helpful and taking the time to bail me out!  (dwhitney67, thanks to you also, I will reply to the stuff you said as well).

Anyway, I will be back as soon as possible to try the stuff you guys suggested, and also to reply to everything you guys have said here so far.

Thanks again!

crash

---

