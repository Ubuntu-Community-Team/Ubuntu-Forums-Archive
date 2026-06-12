---
title: "fsck died with exit status 4 [Solved]"
date: 2007-02-22
forum: Absolute Beginner Talk
---

### Post by rubbsdecvik on 2007-02-22
So this morning when I started my computer up, I updated my system, and then I kept getting errors about how my file system was in read only mode.  So I thought I'd restart.

When it was booting back up, it started fsck, and said:

```
/dev/shm/root contains a file system with errors, check forced.
/dev/shm/root:
Inode 5849438 has illegal block(s).

/dev/shm/root: UNEXPECTED INCONSISTENCY; RUN fsck MANUALLY.
               (i.e., without -a or -p options)
fsck died with exit status 4
```

It then drops me into a maintenance shell, and I have no idea what to do really.  It will do this over and over again.

Hopefully this doesn't mean my harddrive is failing.

I'm running Edgy if it makes a difference.

Thanks,
Rubbs

---

### Post by rubbsdecvik on 2007-02-22
bump

---

### Post by rubbsdecvik on 2007-02-22
anyone?

I'd really like to figure this out without having to reinstall.

Thanks.

---

### Post by rubbsdecvik on 2007-02-22
if this helps here is some more info:

when It drops me into the maintenance shell, and I run an fsck, I get the following

```
fsck 1.39 (29-May-2006)
fsck.ext3: Unable to resolve 'UUID=4939f784-fbf9-40e5-9040-530412461665'

```

---

### Post by rubbsdecvik on 2007-02-23
guess I'll just have to reinstall... again

---

### Post by rubbsdecvik on 2007-02-23
I fixed it.

Ran LiveCD 

Ran fsck with auto fixing and verbose mode.

Restarted... worked like a charm.

Hope this may help someone else out there.

---

### Post by ed-j on 2007-02-23
Well done! I had been watching a bit, but there was nothing I could do as I'm just a Novice. I've only heard recently that the fs....thingy happens auto' after 30 times? Anyway, glad to see you got yourself sorted. Chow!

---

### Post by xyz on 2007-02-23
To decide if you want fsck or not:
```
sudo gedit /etc/default/rcS 
```
Now change the FSCKFIX line to the following:

> FSCKFIX=yes or no if you don't want it to run

To decide how often you want check disk:
```
sudo tune2fs -c 50 /dev/hdax
```
- change the 50 value to whatever
- change the x to whatever you get running sudo fdisk -l

---

### Post by SteveHoffmanUK on 2007-02-23
rubbsdecvik:

I awoke this morning to find the very same message on (Edgy). boot: ¨fsck died with exit status 4¨

Thanks for persevering with your question and thanks also for coming back with your solution of using a live CD. Now where did I put my live CD? :confused: 

I, too, don´t want to have to reinstall, so I´&#314;l have a go and report back.

---

### Post by rubbsdecvik on 2007-02-23
SteveHoffmanUK:

> thanks also for coming back with your solution of using a live CD

The way I figured it out was by trying to resize my partition.  I was going to install onto another partition, so I could try to recover my files.

When QParted ran, it automatically ran fsck with three options.  right now I can only remember that two of them were -y and -f.  The other I can't remember.  

What happened was that when I tried to resize my partition, it kicked back an error.  I read the log, and it fixed many of my broken blocks.  

It wouldn't work under the maintenance shell, but the LiveCD would do it.

Hope that helps!

~Rubbs

---

### Post by SteveHoffmanUK on 2007-02-23
rubbs:

Hmm, a bit too complicated for me! You&#341;e not actually a beginner if you feel that comfortable about repartitioning!:)  Well, no matter ... Here&#347; where I got to:

Downloaded  the Edgy iso image; 
Burned the iso CD
Booted and ran the live CD
Ran the disk check (OK)
Started the install (but I don´t really want  to install, I just want to run fsck to fix the disk)
Got to ¨prepare disk space¨
There are three choices: (1) Resize IDE1master. partition#1 (hda1) and use freed space; (2) Erase entire disk: IDE1 master (hda) - 82.0 GB Maxtor 6LD0L0; (2) Manually edit partition table.

Which of the three do I choose and then what?
How do I get fsck to run?

---

### Post by rubbsdecvik on 2007-02-23
Good question!

First I have to make sure that I say I used the Desktop version of the LiveCD.

Ok... I'll try to give a step by step on the process I used.

First, I loaded the LiveCD and selected the install/start from CD option (it sounds like you did this).

Second... Instead of clicking on the Installer, I went to:

System->Administration->QtParted.

From there I could see my harddrive and the free space.

I selected "resize partition" and just resized my partition down.  (I did this because I intended to save data to the new partition I was going to create)

Then I hit Apply changes.

In order for Qtparted to change a partition, it needs to check the File System I guess.  (which means it runs fsck).

It then ran and kicked back some errors.  I read over the error output, and found that it attempted to fix the broken blocks on my harddrive.  I figured I'd restart and try it out.

If you give me a little bit I can do a tutorial with screen shots.

Also, I'm sure there is some other way of doing this, but this is the way I figured it out.

I don't know enough about getting a harddrive to mount, so I couldn't just run an fsck from the command line.

If you want to wait like 20 more minutes I'll attempt to get some screen shots on how to do it... along with some more exact notes

~Rubbs

---

### Post by confused57 on 2007-02-23
Until  rubbsdecvik gets back, you might want to read over these instructions:
[http://www.ubuntuforums.org/showpost.php?p=2198398&postcount=2](http://www.ubuntuforums.org/showpost.php?p=2198398&postcount=2)

---

### Post by SteveHoffmanUK on 2007-02-23
Thanks, rubbs, for getting back to me and trying to help - I really appreciate it. Before you bother with screenshots, I seem to have a basic difference from your live CD:

> Second... Instead of clicking on the Installer, I went to:
System->Administration->QtParted.

Bad news: I don´t have any QtParted listed under my ¨Administration¨

I am using the Edgy desktop live CD.

---

### Post by SteveHoffmanUK on 2007-02-23
I should add that what I DO have under Administration is ¨GNOME Partition Editor¨, but that&#347; called GParted, not QtParted.

---

### Post by rubbsdecvik on 2007-02-23
That would be what I used... I'm just a dork and couldn't remember off the top of my head.

---

### Post by rubbsdecvik on 2007-02-23
Ok so here is what I did.

The problem was that before I was trying to recall what I did from memory.  I have since gone back and "recreated" what I did.

I used GNOME Partition Editor, not QtParted.

First i loaded the LiveCD (Edgy Ubuntu) and went to System-Administration-GNOME Partition Editor

I came up with the screenshot labeled : GNOMEpartition.png

Then I resized the partition to allow for more room to save my files (in case I couldn't get the fsck to work):

those steps are illustrated in shots: resize 1 2 and 3

Then I hit apply :apply.png

what that did was open another window.  It ran a fsck check and returned an error log.

It didn't end up partitioning because of the error, but the automatic fsck fixed my problems.

If it does partition actually partition the drive, and it doesn't fix your problems, then you can install the new system on the new partition, and copy your files from the old. (theoretically) 

Hopefully that helps.

~Rubbs

---

### Post by rubbsdecvik on 2007-02-23
> Then I hit apply

I should note that this time i did not hit apply, because I didn't want to change my partition (since it now works).  However, that is what I did when I was actually trying to fix the problem.

~Rubbs

---

### Post by SteveHoffmanUK on 2007-02-23
rubbs, you are NOT a beginner, you are a flippin' GENIUS!

I followed your instructions, applied the repartitioning, hit the fsck error, saved the log, read it and it seemed to have repaired the disk, so I rebooted, and - voila! - my system is back up. The only damage I can see so far is that I've lost my wallpaper, but that's no problem.

Thanks very much for all you help. I've lost the better part of the day, but at least I've restored my system.

 :) :) :) :) :)

---

### Post by rubbsdecvik on 2007-02-23
Glad to have helped!  I say I'm a beginner because I just barely am hanging on to what a lot of people say.  What I just posted is truly the most advanced thing I have ever done.  

I'm really glad to that you have it restored.  I feel like I can actually contribute now!  (does little happy dance).  

Hopefully this post helps others too.

~Rubbs

PS... if anyone is reading this and they know a better way to do it (I.E. get the disk to mount and run an fsck automatically) please post it!

---

### Post by olavjunior on 2007-03-07
Great thread! Helped alot!

I just moved my /home to a new partition, and it all worked fine. But after a reboot, I got the error 
[I]Resize inode not valid
Unexpected inconsistency[/I]

So off course I was convinced that there was something wrong with the fstab. I tried and tried, but always the error. Then I read your thread :)

When I started gpartd and tried to resize my partition, I got errors. Took a look at the log, and ubuntu had fixed alot of things. So I folloed your advice and restarted, and everything worked just fine! :)

Tanx

---

### Post by rubbsdecvik on 2007-03-07
Glad to see I helped someone else!  

Hope you have a good day!

---

### Post by matjaz_pirnovar on 2007-03-15
I had the same problem today and I followed instructions with live CD and resizing partitions.

I'm running Edgy. And I used Dapper 6.06 live CD to work with partititions. After hitting Apply it started working and after 20 min it was still working. Then I hit Cancel.

After restarting, Edgy was completely back  :-)

Looks like applying resizing partititions triggers fcsk which is the key to the solution (without actually changing them).

Thanks for tutorials :-)

Matjaz

---

### Post by rubbsdecvik on 2007-03-15
Glad to hear that it helped for you too.

I figured fsck was doing the work, but I didn't know how to do it manually.

If anyone figures it out.  I hope they let me know.

---

### Post by TeoK on 2007-10-09
> **rubbsdecvik said:**
> I fixed it.

Ran LiveCD 

Ran fsck with auto fixing and verbose mode.

Restarted... worked like a charm.

Hope this may help someone else out there.

OMG -i got the same exact error today, and i'm still lil bit lost.

Can you post more detailed steps you took to recover.?

like ..how do I start with CD, and details on "Ran fsck with auto fixing and verbose mode."

thanks !

---

### Post by rubbsdecvik on 2007-10-09
Ok... so the whole idea here is to try to run fsck on your disk but not *from* the disk.  (This is what your computer is trying to do now, and it's having problems.  So what we need is an external disk to run fsck, hence the LiveCD.) 

EDIT:  Just in case you didn't know, fsck is the disk checking utility that checks your disk for errors, however, in this case it can't fix those errors, probably because the error is in the part of the disk that fsck is running off of.

So what happened in the post is this.

I had this error with exit status 4.

I booted off a liveCD and tried to resize my partition.  when I tried this, it automatically ran fsck, and fixed my problems.

You can do the same, and if you wait until my next post I can try to tell you how (it's been a long time since I did this). 

Before I give you the exact way I did it, I'm going to do a little bit of research and see if there is a safer way to do it.

I'll get right back to you!  Don't lose hope!

---

### Post by TeoK on 2007-10-09
thanks Rubbs !

basically, i booted from CD and tried to run sudo fsck/dev/sda1 to fix my file system

but it says 'command not found'

uff..

---

### Post by rubbsdecvik on 2007-10-09
Oh... you almost had it.

try this :

```
sudo fsck -av /dev/sda1
```

the spaces and the av part are important too.

If that doesn't work try this post I made earlier.  It shows how I did it graphically.

[http://ubuntuforums.org/showpost.php?p=2200353&postcount=17]("http://ubuntuforums.org/showpost.php?p=2200353&postcount=17")

---

### Post by TeoK on 2007-10-09
> **rubbsdecvik said:**
> Oh... you almost had it.

try this :

```
sudo fsck -av /dev/sda1
```

the spaces and the av part are important too.

If that doesn't work try this post I made earlier.  It shows how I did it graphically.

[http://ubuntuforums.org/showpost.php?p=2200353&postcount=17]("http://ubuntuforums.org/showpost.php?p=2200353&postcount=17")

ouch, now I get this massive warning:

"/dev/sda1 is mounted

Warning!!! Running e2fsck on a mounted filesystem may cause SEVERE filesystem damage."

What should I do?..this is scary

---

### Post by rubbsdecvik on 2007-10-09
Ok try this...

```
sudo umount /dev/sda1
```

That should unmount your drive, and then you can do the fsck code again.

---

### Post by TeoK on 2007-10-09
done.

 then i get 
"/dev/sda1 contains a file system with errors, check forced"

and 
UNEXPECTED INCONSISTENCY; RUN fsck MANUALLY"

so how did you do the file system check with auto correction?

---

### Post by rubbsdecvik on 2007-10-09
That was supposed to be the -a part.

The way I actually ended up fixing it was by trying to resize my partition.  When GNOME Partition manager tried to repartition, it ran fsck and fixed it on it's own.

I did some research and found out that fsck -a is supposed to try to automatically fix errors.  the -v part is just to tell you what's going on.

I'm running out of ideas so try this

In the GUI go to  System -> Administration -> GNOME Partition Manager.

Then select your linux partition and hit resize.  Move it just a little bit, and then hit apply.  That way it will try to resize the partition.  It should try to fix it on it's own.

Again, I'm sorry that I don't know any other technical way... you've exhausted them with the fsck -av from the CD.

I'm hoping some real guru will contribute to this thread.

---

### Post by rubbsdecvik on 2007-10-09
PS....

After you hit apply it's going to try to resize.  It should fail and come back with error messages.  The fsck will have been run.  After that try to restart without the CD.  That is how I did it.

Again... I'm trying to do this all from memory, about something that happened 8 months ago, so I'm sorry if my info isn't 100% correct.

Let me know how it goes.

---

### Post by TeoK on 2007-10-09
yes, I just tried you partitioning method , but it doesnt work.
when GParted opens, the sda1 is automatically mounded and after "resize",  and "apply"
I get "check filesystem on /dev/sda1 for errors (if possible) fix them"

so no automatic fix here.uff

---

### Post by rubbsdecvik on 2007-10-09
Sorry to hear it didn't work out.

What you really need to do is some good fsck research.  maybe start a new thread and see if someone here knows what to do.

I'm sorry I couldn't help much.

---

### Post by ryanVickers on 2007-10-09
> **rubbsdecvik said:**
> I fixed it.

Ran LiveCD 

Ran fsck with auto fixing and verbose mode.

Restarted... worked like a charm.

Hope this may help someone else out there.

Wow, we've created one tough filesystem!  congrats to the whole ext3 team! ;)

---

### Post by TeoK on 2007-10-10
> **rubbsdecvik said:**
> Sorry to hear it didn't work out.

What you really need to do is some good fsck research.  maybe start a new thread and see if someone here knows what to do.

I'm sorry I couldn't help much.

naw, you've been much help, thanks !

finally fixed, though..with a command:


sudo e2fsck -f -y -v /dev/sda1

---

### Post by rubbsdecvik on 2007-10-10
oh good job!

I'm really going to try to remember that.  Where did you find the answer to it?  That's some amazing researching abilities!

---

### Post by TeoK on 2007-10-11
> **rubbsdecvik said:**
> oh good job!

I'm really going to try to remember that.  Where did you find the answer to it?  That's some amazing researching abilities!

Actually, this was a command listed in GParted error log, as i tried you method.
..and i turned out to be a key to the puzzle. thank again.

---

### Post by fox88 on 2007-10-21
thank you, oh lord, thank you!!

i had to use and old 6.06 live cd, since my ATI Mobile X1400 and ubuntu recent live cds don't get along, but it is working!!! YEYYY!!! :)

---

### Post by d-r-i-v-e on 2007-11-13
First of all I would like to thank you for giving so clear instructions.
It works exactly as it was expected.
Thank you very much for helping me break threw this horrible event this morning.

---

### Post by rubbsdecvik on 2007-11-13
glad to hear you made it through.  I know what it's like to have something like this happen.  It's quite a problem.

---

### Post by xaxas on 2008-01-08
YEEES :D

Dam ubuntu is 2 smart 4 me :)

Had the same problem and Didn't have to boot from live CD
I'm running Gutsy Gibbons and it tryed 2 do the fsck automaticly, after the exit status 4 and failed and said i had to do it manualy :((

I typed ```
fsck /dev/sda1
``` and bingo :D
waited 5 min and said Yes to all the "should i fix this" type of errors and now it worx :D

---

### Post by jmorales on 2008-01-19
I wish mine took only 5 minutes of answering ""should i do this" type questions. I started it last night and it was still going when i got back. Went to bed, it is still going this morning. I have typed "Y" sooooooo many times. Is this normal? I ran "fsck /dev/sda1"'

---

### Post by philinux on 2008-01-19
You can use the -y switch which will answer yes to all questions. Or is it -Y.

Not on buntu else would have done a man fsck

---

### Post by jmorales on 2008-01-19
> **philinux said:**
> You can use the -y switch which will answer yes to all questions. Or is it -Y.

Not on buntu else would have done a man fsck

was it totally noobish of me to run a man fsck? either that or i dont get it lol

---

### Post by philinux on 2008-01-19
fsck -y /dev/sdax

is what I meant but cant remember if its capital Y or not

In terminal if you type 

man Command (where command might be sudo or fsck) it will give you the command syntax.

Thats not the same a running fsck manually

---

### Post by jmorales on 2008-01-19
ah ok yeah that makes sense. sorry for the misunderstanding.

---

### Post by jmorales on 2008-01-19
running sudo e2fsck -C0 -p -f -v /dev/sda1 starts up the check and it hangs around 67% done. then i get an UNEXPECTED INCONSISTENCY; RUN fsck MANUALLY.

---

### Post by jmorales on 2008-01-19
I was in a maintenance shell, and I don't know what I did differently this time, but it worked. When I tried your suggestion to do a partition and have it auto run fsck, it just hung and I had to cancel it. so I went into the maintenance shell and did another e2fsck with all the options mentioned a page or two ago, basically the same command that the partition manager was trying to do and it worked!!! 

Thank you Rubbs for the thread and everyone else that chipped in. I know this was solved a long time ago, but its things like this that make it possible for everyone else. Thanks again. 

jaime

---

### Post by rubbsdecvik on 2008-01-29
Sorry it took so long to post back.  My grandfather was airlifted to the hospital... but I digress.

I'm glad that you figured out the problem.  It has always been my favorite thing about this site that people will help out perfect strangers for no real reason other than to just help out.

---

### Post by the_master on 2008-02-09
Rubbsdecvik i'm sorry about your grandpa.  Thanks for the the directions it helped yet another person.  Keep up the good work, you made ubuntu go round.

---

### Post by rubbsdecvik on 2008-02-09
> **the_master said:**
> Rubbsdecvik i'm sorry about your grandpa. 

My grandpa's doing better.  Thanks for the support.  

>  Thanks for the the directions it helped yet another person.  Keep up the good work, you made ubuntu go round.

I'm just one person in a large community that likes to help out, but I'm glad that something I did helped someone.

---

### Post by ru0n on 2008-04-03
> **rubbsdecvik said:**
> 
Hope this may help someone else out there.

This indeed helped someone else out here!
Thanks! ;)

---

### Post by rubbsdecvik on 2008-04-03
Good to know you could fix the problem.

---

### Post by speirint on 2008-04-27
I'm an absolute beginner as well, so I'm a bit squeamish about doing more than what I've described below:

I'm not sure what I did to get this, but I'm running gutsy as well.  I hard reset and tried booting up on several kernals and safe modes, but I couldn't escape the fsck died w/ exit status 4 business.  I typed in fsck and it prompted me with something like:

```

bash: no job control in this shell

```
and then a list of the following followed by command not found:
```

groups:command not found
lesspipe:command not found
The:command not found
dircolors:command not found
command:command not found
The:command not found

Pass1: Checking inodes, blocks, and sizes
Inode 1431222 has illegal block(s). Clear <y>?

```

The first time I actually did say yes, and it started deleting a lot of stuff and even said something about resetting my system clock.  After it prompted me to clear more things I got nervous and decided to consult the internet.

My first question is have I deleted anything important or damaged my computer? Also, if I were to type in the stuff quoted below (```
fsck /dev/sda1
```) is that relavent to me?  When I reboot, everything referred to /dev5/hda5  as the place where my problems were.


> **xaxas said:**
> YEEES :D

Dam ubuntu is 2 smart 4 me :)

Had the same problem and Didn't have to boot from live CD
I'm running Gutsy Gibbons and it tryed 2 do the fsck automaticly, after the exit status 4 and failed and said i had to do it manualy :((

I typed ```
fsck /dev/sda1
``` and bingo :D
waited 5 min and said Yes to all the "should i fix this" type of errors and now it worx :D

---

### Post by rubbsdecvik on 2008-04-28
I'm not sure... 

What happened was that some part of the hard drive got corrupted and it needed you to attempt to fix it manually.  (That was hitting yes to all the prompts business was)  

What could have happened was a corruption of some important files.  I'm unsure as to objectively test this, but it's possible. 

I need to know a little more info to try to help you out.  I'm a little fuzzy on some details.  

This is how I interpreted what happened. 

1) you received the nasty fsck died with exit status 4 message.
2) you tried to manually run fsck and fix it via hitting yes multiple times
3) you're not sure if it did anything... 

so my questions are:

Can you boot into a GUI or Recovery Mode?

if possible can you post your fstab by doing this code:
```
cat /etc/fstab
```
and then posting the results here?

These things might be able to get us a little closer to understanding exactly what is going on.  

Let me know if you need help with any of this.

---

### Post by speirint on 2008-05-10
I cannot boot into a GUI, nor can I go to the recovery mode.  The fsck business pops up with every kernal I tried booting up into, including recovery modes.  

I typed in gdm, or reboot, or restart, or shutdown, but all of the commands don't work.  I have to hard restart the computer.  I'll try entering cat/etc/fstab now.

For step 3, I know it offered to clear more illegal blocks, but since I don't know what they are/what it means, I've shied away from continuing after seeing the screen say there are illegal blocks that need to be cleared after about four times.

---

### Post by speirint on 2008-05-10
Okay, I tried
cat /etc/fstab
and the response was either no such directory existed or no such command found (I don't remember exactly which, but I believe it was the first one).

When I typed in fsck I got something along the lines of:
illegal block(s) in inode 1431222 found, clear block(s)? <y>

I input y
and then it showed a list that said:
illegal block 12 (a bunch of numbers that were probably pertinent, but I am unable to retain in my short term memory right now)  CLEARED
illegal block 13 (a bunch of numbers that were probably pertinent, but I am unable to retain in my short term memory right now)  CLEARED
And so on, all the way to illegal block 22 following the same arrangement.

I then got:
too many illegal blocks in inode 1231222

and an offer to clear more stuff.  Should I carry on with allowing it to clear blocks in inodes?  Doing a quick google search, I've come to believe that inodes are pretty important for files, and the blocks have something to do with how the operating system understands data input/output and does something with data buffers... is it bad that I've been using ubuntu for over a year and still have almost no clue as to what's going on beyond the gui?  Anyhow, for an absolute beginner, one can probably infer how this can seem a bit terrifying as I haven't reached the point of understanding enough to discern when something isn't a big deal and such.

---

### Post by rubbsdecvik on 2008-05-10
Unfortunately in a situation such as this, there is very little one can do to make sure things are going ok.  

fsch is just doing what it knows best to do, which is clearing the illegal blocks.  My guess the blocks became corrupted, by one of many possibilities, including operating system error (I hate to say it, but it's possible), user error, power failure, or some other thing I can't think of.

My suggestion is to just keep hitting clear and hope for the best.  eventually you will come to the end of the corrupted blocks and you might have something to boot off in the end.  If your data is that important, I would suggest attempting to get it off of the bad drive by using a liveCD.  The Ubuntu liveCD can do quite a bit, but for true system rescue stuff I would suggest [SysResCD]("http://www.sysresccd.org/Main_Page")(Edit: added link to sysrescd).  As for how to fix your specific problem with it, you're better off asking them in their forums, I'm not an expert by any means.  I don't mean to shove you off onto someone else, I just want to make sure you have every opportunity to get the right information rather than someone's best guess.

I'm really sorry that this has happened to you.  I hope that you would still give Ubuntu a chance after something like this, the newest versions seem to be a lot more stable.

when I had this happen to me I just hit clear to all the problems that needed fixing and I was able to boot up again.  I didn't notice anything, so you might have the same luck, but I can't promise that.

Hope I've helped in at least some small way.

---

### Post by speirint on 2008-05-12
Thanks for your suggestions, I believe it is associated with some power issues.  My computer started behaving strangely after I set it to hibernate if I wasn't attending to it for more than 15 minutes.  Hibernation worked out alright for it at first, but after about three or four times I believe something started to corrupt as it began to have shaky bootups and certain applications would begin to freeze with greater frequency.

I very much appreciate your advice and sincere efforts.  I've been using the mepis live cd or windows xp to get stuff done in the mean time, but still have the ubuntu live cd (6.10? edgy eft) a classmate gave me.  Would I be able to retrieve data through a gui on the ubuntu live cd, or will it take me through an installation process or require me to know how to do the coding (understanding sudo, bash, and grub)?

I'll start working on it a couple weeks from now.

---

### Post by rubbsdecvik on 2008-05-12
As far as getting your files off via a gui, you might want to get the newest version of Ubuntu.  Another idea is to try the SysResCD I posted about earlier.  It will boot up in command line mode, but the command: 
```
startx
```
will start the windows manager (gui).  

The SysResCD has some tools that might be able to find your files easier, but they usually are command line.  

There is probably no easy gui way to get everything down perfectly.   

I hope you have some good luck.  Keep asking questions... we might be able to help

---

