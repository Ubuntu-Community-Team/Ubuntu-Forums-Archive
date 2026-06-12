---
title: "Login problem"
date: 2007-04-07
forum: Absolute Beginner Talk
---

### Post by nxMarc on 2007-04-07
Hello, community!

I would like that we met in diferent situation, but...

I'm pretty new user of Ubuntu, and I have a problem with... well, I think it's file system.
I get login screen, but when I type my username and pass, it says "your home directory is listed as: /home/marc/ but it does not appear to exist" and asks if I want to login with the root directory as my home directory. If I select yes, it says again that my home/.dmrc file is being ignored, then that my session lasted less than 10 sec and returns me back to login screen. If i select no, same thing happens.
So, I can login only in failsafe terminal... and, as I said, I'm new linux user and I have no idea what to do. :(  

I hope somebody can help me...

---

### Post by LaurelLynn on 2007-04-07
Dear nxMarc,

I would try to reboot and select the option the says ¨Recovery¨ give it your original password.  If it takes you to a prompt ¨#¨ enter ¨adduser  letmein¨.  Fill in the entries and use a new password. You may be able to login with that name and password.

If not it´s just possible you have /home set to a partition that isn´t there. Do ¨ls /home¨.  If you get an error message, I would start a new thread ¨Missing home partition on install¨.

Laurel Lynn

---

### Post by nxMarc on 2007-04-07
Thank you for your reply.

I can't find no Recovery option... :(

/home directory is here. But it seems like /home/marc isn't.

---

### Post by LaurelLynn on 2007-04-07
When I say ¨Recovery¨, I mean I can´t remember what it is called, and I would have to reboot my computer to get the exact name (something I would prefer not doing).

When the system boots up most people get a GRUB menu of boot options.  One of those leads to a command line only login ( the word recovery or restore or repair should be in it).

Depending on how Grub is configured you may not get the menu, but just a prompt that reads ¨boot:¨ for a few seconds, then flashes by.  Try entering ¨single¨ at the prompt.  If that doesn´t work try ¨init=1¨.

One of those should get you to a command prompt were you can run ¨adduser¨.

Laurel Lynn

---

### Post by ComplexNumber on 2007-04-07
> **nxMarc said:**
> Hello, community!

I would like that we met in diferent situation, but...

I'm pretty new user of Ubuntu, and I have a problem with... well, I think it's file system.
I get login screen, but when I type my username and pass, it says "your home directory is listed as: /home/marc/ but it does not appear to exist" and asks if I want to login with the root directory as my home directory. If I select yes, it says again that my home/.dmrc file is being ignored, then that my session lasted less than 10 sec and returns me back to login screen. If i select no, same thing happens.
So, I can login only in failsafe terminal... and, as I said, I'm new linux user and I have no idea what to do. :(  

I hope somebody can help me...
i had that error once. it turned out to be incorrect permissions/ownership on either my home directory or the root file system.
as LaurelLynn suggests, select "failsafe" at the boot menu (or choose failsafe at the login prompt after you've booted up in normal mode). then after you've logged in(you will be asked to log in as root user), navigate to root(ie /) by typing in 'cd /'. then type in:
**ls -l **(note: this says "minus el". ie lower case "L").

---

### Post by nxMarc on 2007-04-07
Sorry, I wasn't even thinking on GRUB... yes, it is there, recovery mode.
I've succesfully added new user, but now in my partitions list / and /home are here, but not recongnized (no device, no size..., just mount points) :confused:

---

### Post by LaurelLynn on 2007-04-07
Dear nxMarc,

Try posting the results of:

cat /etc/fstab

Mount problems can often be traced to an error in one of the listings.

Laurel Lynn

---

### Post by ComplexNumber on 2007-04-07
> **LaurelLynn said:**
> Dear nxMarc,

Try posting the results of:

cat /etc/fstab

Mount problems can often be traced to an error in one of the listings.

Laurel Lynn
its not a problem with fstab. the OP mentions this, which gives the cause of the problem away:
> it says again that my home/.dmrc file is being ignoredits a problem with permissions/ownership.


[http://ubuntuforums.org/showthread.php?t=179122&page=2&highlight=dmrc](http://ubuntuforums.org/showthread.php?t=179122&page=2&highlight=dmrc)
[http://ubuntuforums.org/showthread.php?t=153553&highlight=dmrc](http://ubuntuforums.org/showthread.php?t=153553&highlight=dmrc)

---

### Post by LaurelLynn on 2007-04-07
Dear ComplexNumber,

I was just thinking that mount permissions superceed shell permissions, so an error durring mount could also cause the permissions to default to where even root has less than full access.

Laurel Lynn

---

### Post by ComplexNumber on 2007-04-07
> **LaurelLynn said:**
> Dear ComplexNumber,

I was just thinking that mount permissions superceed shell permissions, so an error durring mount could also cause the permissions to default to where even root has less than full access.

Laurel Lynn
yes, you are correct in your reasoning :).   its only because i've been down this route before that i know how to solve it. many people end up believing that its a problem with the permissions of the /home/<username>/.dmrc file, but thats incorrect, and the cause of the problem is nothing to do with that file.

well, i think the OP should try all suggested possibilities.

---

### Post by nxMarc on 2007-04-07
Anyway, cat /etc/fstab says:

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda4
UUID=19f848dc-9693-41d7-8d4c-b6ef3fbc4890 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda2
UUID=8853d528-14a8-42c5-9f93-2df8a2e75dfc /home           ext3    defaults        0       2
# /dev/sda1
UUID=3b645a9e-74d5-4efc-8e90-b69140132d69 /torrents       ext3    defaults        0       2
# /dev/sda3
UUID=5b3e2ab7-cc59-4a9c-a06a-54b54e49d6cf none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto     0       0
```

It's definately something wrong here.

---

### Post by LaurelLynn on 2007-04-07
Thanks ComplexNumber,

I apreciate the info.:) 

Laurel Lynn

---

### Post by LaurelLynn on 2007-04-07
I´ve seen an fstab like that before, with similar problems.

If your still listening ComplexNumber, could you please take the time to explain to me how new users are ending up with UUID entries in their fstab, instead of the usual ¨/dev¨ names? It  really stuck me as rather odd, not necessarily wrong but odd, and I was hoping someone could explain it.

Laurel Lynn

---

### Post by ComplexNumber on 2007-04-07
> If your still listening ComplexNumber, could you please take the time to explain to me how new users are ending up with UUID entries in their fstab,its meant to be like that. here's mine:

> # /etc/fstab: static file system information.
#
#  -- This file has been automaticly generated by ntfs-config -- 
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>

proc /proc proc defaults 0 0
# Entry for /dev/hda6 :
UUID=d6b42216-3c81-45bb-9cf3-f70631d8b2fd / ext3 defaults,errors=remount-ro 0 1
# Entry for /dev/hda3 :
UUID=b36543bc-7792-4369-a39f-ca225fa269ea /home ext3 defaults 0 2
# Entry for /dev/hda1 :
UUID=6010B50710B4E566 /media/hda1 ntfs-3g defaults,locale=en_GB.UTF-8 0 1
# Entry for /dev/hda5 :
UUID=110252f4-7e71-4123-8cbc-0fe7dd1a458e none swap sw 0 0
/dev/hdc /media/cdrom0 udf,iso9660 user,noauto 0 0
/dev/hdd /media/cdrom1 udf,iso9660 user,noauto 0 0
/dev/ /media/floppy0 auto rw,user,noauto 0 0each entry was preceded by the UUID number when i first installed - it doesn't change. the UUID is just a unique identifier for the partitions.

---

### Post by LaurelLynn on 2007-04-07
Thanks Complex Number,

I´ve only seen it rarely in Unix or other Linux distros. Good luck nxMarc, ComplexNumber has much greater Ubuntu wisdom than I, I leave you in his competent hands.

Laurel Lynn ):P

---

### Post by ComplexNumber on 2007-04-07
> **LaurelLynn said:**
> Thanks Complex Number,

I´ve only seen it rarely in Unix or other Linux distros. Good luck nxMarc, ComplexNumber has much greater Ubuntu wisdom than I, I leave you in his competent hands.

Laurel Lynn ):P
no, don't do that. your help for nxMarc is _equally_ worthy.

---

### Post by LaurelLynn on 2007-04-07
Sorry Complex Number, I didn´t mean I leaving the forum and will never try to help anyone again.

It´s just that I ran out of ideas on this one, and the last time I saw  something like this before I failed to come up with a solution.  What I meant is I´ll just kibitz to see how it turns out, I have decades of Unix experience, but only a few weeks Ubuntu experience.

Laurel Lynn

---

### Post by ComplexNumber on 2007-04-07
i know you didn't mean that :lolflag:. if you have decades of unix experience, then i'm leaving this problem to you :D.  i'm still relatively a noob.  
the way i see it, all help is welcome help.

---

### Post by Ptero-4 on 2007-04-07
Don`t worry Laurel. Ubuntu is in the end just another UNIX.

---

### Post by LaurelLynn on 2007-04-07
Ah, but it isn´t BSD, Ptero-4 ( spent most of my time on IRIX, ohhh so long ago). 

That´s why some things look a little odd to me at times. I´ll still help whenever I see something I recognize, but Ubuntu specific problems will still be completely new to me (especially since I´m still running Dapper).

I think we may have scared off nxMarc, are you still here?

Laurel Lynn;)

---

### Post by ComplexNumber on 2007-04-07
**LaurelLynn**
sorry, what i meant before was that i thought that you were saying that you're going to leave this problem to me. 

i think that if you have lots of unix experience, then that will, after a short while, translate itself to having lots of experience of linux. the underlying theory is basically the same.  the vast majority of people don't have your level of unix experience and the unix filesystem, and i think thats really valuable. thats not exactly something that can be learnt overnight, but takes years.

hopefully the OP comes back and tries out all the suggestions.

---

### Post by LaurelLynn on 2007-04-07
Well boys, I really am out of time for now.

Thanks for your kind words ComplexNumber!!!

nxMarc, if you are still checking back here, I have one parting piece of wisdom that might help.

Us Unix/Linux dinosaurs are used to working with servers catering to other users, so we hate to have to reboot, and we hate to touch existing data.

That causes us to dig our heels in and wrestle with a problem far longer than sometimes we should.

For a single user Desktop system, with all your data backed up. Sometimes the old Windows reinstall everything from scratch is the easiest solution (the problem there, is that they now seem to think that´s the only solution).

If it´s a fresh install, starting over from scratch may fix the problem, or try a different version (dapper 6.06LTS seem very stable and will still be supported for some time. I still use it)

I have this thread bookmarked, and will check back later.

Laurel Lynn ):P

---

### Post by jerryrw on 2007-04-07
I agree we dinosaurs will often go way too far just to not have to put that cd back into the drive, I think it's a throwback to installing off tape and disks(I just missed out on punchcards).

But,  For the original problem I would also like to see an fdisk -l, or did I miss it?

I have been using Linux for quite some time and am new to Ubuntu and I'm finding that %90 of the bang my head into the keys problems are permission problems.  I would think that if it is a perm prob that going into single user mode and then creating a new user, and then adding that user to the admin group should fix it.  there are details in the install guide under chroot or installing from an existing distro.

---

### Post by LaurelLynn on 2007-04-07
I´m back again! But just for a minute.

jerryrw, I was unfortunate enough to catch the tail end of cards in high school ( whoa to the girl who  drops her homework assignment).

I saw a problem early this week where someone unable to login could get to a root prompt, but could not run any commands. Any attempt failed do to lack of permision.  I have seen that before in Unix with mount problems, because the bootloader goes straight to the partition for the command shell, but the command shell has very few commands of it´s own.  Mostly it just runs files from the various bin directories on root. Which it can´t do without read access to the drive.

In that case even single user mode doesn´t change anything. When you get to a command prompt you think that at least /root must be mounted, but that isn´t necessarily true. Instead what you get is a steady stream of ¨permision denied¨ messages.

So that is why I was thinking this case might be a mount problem not a permission problem. 

Ubuntu is different from BSD Unix though, and ComplexNumber, who has a lot of beans, has seen permission problems stemming from the configuration files in /home. If he has seen it a lot, it is probably the source of most problems.

I myself would like to see the error logs since mount problems don´t print messages on the screen, they fail back to a reduced permission set, usually read only.  That is actually a troubleshooting feature, because your supposed to be able to read the drive, even if the error prevents you from writing. Sometimes the problem prevents even reading though.

All of which becomes mute, because most new people will have staggered off like deer caught in head-lights long before you can tell them to upload the error logs from a non-readable drive.

I guess the point I´m trying to make, is: Be aware that drive problems sometimes show up as permision problems in Linux/Unix.

Laurel Lynn

---

### Post by ComplexNumber on 2007-04-07
> and ComplexNumber, who has a lot of beans
the number of beans means absolutely and literally nothing other than number of posts :). honestly, please don't go down the route of thinking that beans equals experience. its simply not true. i have lots of beans, but i'm still a dum-dum ;)

i may have seen and encountered this problem before, but my knowledge of this particular problem doesn't show the extent of my linux knowledge. most of linux/unix is still a mystery to me. for example, you mention about the error logs. but when it comes to error logs, i really wouldn't have a single clue.

---

### Post by LaurelLynn on 2007-04-07
Dear ComplexNumber,

Don´t look now, but the forum has you listed as ¨Staff¨

I suppose it depends on wheither they are asking beans, or telling beans.  I would say the person with the most asking beans probably has the most experience. Nothing like slamming into a brick wall a few times to teach you never to do it again.

I spent six years administering SGI Workstations and servers in the 90s. But at most it was a half dozen unix system with maybe twice as many connected PCs (which weren´t mine) and X-terminals (which were).

Thing is with an IRIX system you add Unix to the Mac like all components from one source.  You end up with systems that just  keep on going like energizer bunnies. I was like the guys in the old Maytag commercials (only better looking).  You had to actually work at crashing them. It only happened when I wrote software to interface directly with the drivers. I locked up or crashed the graphics system a few times, with programming errors or recursive scripts. But I would log in from the next system over, and the problem was easy to solve.

Mostly I just swapped back up tapes, and fixed my own screw ups. Engineers running  bleeding edge (at the time) experimental realtime aps, and the os never seemed to even hiccup it was mostlyboring.

Which was good because I was really supposed to be a Software Engineer.

I will say that I go back to the BPC era (Before PCs). But now I´m just inflating my ego, and showing my age, so I´ll stop.

Laurel Lynn

---

### Post by ComplexNumber on 2007-04-07
i guess i'm a member of staff because some other mods may have found me to be helpful, i guess. i don't think its much to do with experience. one can be helpful without being knowledgable.

---

### Post by LaurelLynn on 2007-04-07
Your way too modest ComplexNumber.

In the computer world you can always find hoards who will look at you and see a god.

Then there are always hoards who you will look at and feel like you were born yeasterday.

Laurel Lynn

---

### Post by LaurelLynn on 2007-04-07
Oh, I almost forgot ComplexNumber,

Most of the logs are in the   /var/logs   Folder tree.  There are quite a few things logged, startup, shutdown, samba errors, X errors....

Traditionally logs were spread around all over the system.  I don´t see boot or shutdown logs (possibly somewhere in /boot, but a quick peek didn´t show them). 

¨syslog¨, ¨auth¨, and ¨Xorg.o.log¨ are useful ones. They tell you system errors, who has been trying to log in, and graphics errors.

Laurel Lynn

---

### Post by ComplexNumber on 2007-04-07
getting to know the /var directory better is something that i want to look into sometime. apart from having the odd peep in there for curiosity's sake, i've never really had any reason to go in there. if i were a sys admin or  if i run a server, things would be very different. but for the average desktop user, there's usually not much need to go in there.

seems like the OP's thread has been hijacked :D. maybe i should split part of the thread off into its own thread called 'Various musings about unix/linux and the world of IT'. i guess i can always do that later.

---

### Post by antoz on 2007-04-08
nxmark I had a similar problem plus a few others if you want to check it out it may be usefull

[http://ubuntuforums.org/showthread.php?t=394394](http://ubuntuforums.org/showthread.php?t=394394)

---

### Post by LaurelLynn on 2007-04-08
That is it antoz!

I just new it was a mount problem\\:D/   I´m going to bookmark that post.

I didn´t like the use of UUID because one small typo would be almost impossible to find. I tried to walk someone else through something similar, but he said it didn´t work (possiblly a comunication misunderstanding along the way - english was not his native tongue).

nxMarc if you come back  follow that link and do what confused57 suggest on page 3.

I could kiss you antoz!!!:)

---

### Post by ComplexNumber on 2007-04-08
**LaurelLynn**
i bet you thats not the solution ;). in fact, its not even close.

---

### Post by LaurelLynn on 2007-04-08
Dear ComplexNumber,

You must be keeping secrets from us.  antoz seems to say he could log in **after** he changed the fstab entries.

I admit I got a little over jazzed because that matched my original hypothesis ( ergo it must be right, because the universe revolves around me).

All kidding aside, you sound pretty confident that something else is going on. I´m just dying to know why?

Laurel Lynn

---

### Post by antoz on 2007-04-08
thanks for the kiss

My fstab was nonexistant confused57 created it for me all I did is delete everything that was in there and pasted what he had in his post. AND IT WORKED not sure if it will work for anybody else but it certainly taught me a few things along the way. It is still working I am writing this in Ubuntu by the way. Cheers,A

---

### Post by Mellon on 2007-04-08
nxMarc you can try changing owner of home directory, it works to me.

in terminal type

sudo chmod 777 -r /home

dont remember if its -r or -R , anyway dont do this in /

---

### Post by LaurelLynn on 2007-04-08
-R  Mellon I just  checked the --help

---

### Post by antoz on 2007-04-08
Not sure but I think the UUID lines in fstab are for Edgy and Feisty I am using Dapper

---

### Post by ComplexNumber on 2007-04-08
>  All kidding aside, you sound pretty confident that something else is going on. I´m just dying to know why?there are several reasons:
1) i've had exactly the same problem before.
2) others had the same problem as the OP has solved it in exactly the same way. i gave 2 of threads earlier on (see post  8). there are many more. 
3) the error that the OP stated in his first post (ie "your home directory is listed as: /home/marc/ but it does not appear to exist") is  a permission error.

[here]("http://ubuntuforums.org/showthread.php?t=371052") is another one that is exactly the same as the OP's problem

btw antoz said he could boot up after he changed fstab. the OP has no problem with booting up, he has a problem with logging in.

---

### Post by antoz on 2007-04-08
just want to make a few things clear:
I could boot after editing the menu lst **BUT** could then not log inn and had exaclly the same message as nxMark describes about home directory etc... that is why I replied to his thread.

---

### Post by ComplexNumber on 2007-04-08
> **antoz said:**
> just want to make a few things clear:
I could boot after editing the menu lst **BUT** could then not log inn and had exaclly the same message as nxMark describes about home directory etc... that is why I replied to his thread.
i've had a look through both of your threads, but i can't seem to see anywhere where the dmrc file is mentioned in your problem. can you point it out to me please?

---

### Post by LaurelLynn on 2007-04-08
Hmmm,

I had a different impression antoz because when I followed that thread I read :

¨Thanks a lot confused this absolutely did the trick, I was able to **log in** for the first time¨

but if you are still locked out, then something else is going on.  Which would mean
ComplexNumber is right and I´m wrong (pop! There goes my inflated ego :(  ).

Laurel Lynn

---

### Post by ComplexNumber on 2007-04-08
not necessarily. lets wait for the OP to return.  it may be me who's wrong.

---

### Post by antoz on 2007-04-08
All my problems were solved after I did what confused told me to do and I haven't had a Login problem since

[http://ubuntuforums.org/showthread.php?t=396227](http://ubuntuforums.org/showthread.php?t=396227)

---

### Post by ComplexNumber on 2007-04-08
the dmrc  file isn't mentioned in your problem though.

---

### Post by antoz on 2007-04-08
Hey I am a novice when it comes to all this; just thought I could help someone with the same problem I had (and the solution that did it for me), don't even know what a DRMC file is  so I will now leave it to people who know what they are doing. Cheers, A

---

### Post by LaurelLynn on 2007-04-08
I´m not trying to accuse you of anything antoz, I just wanted clarification whether you had meant to say boot or login in the originial thread. The distinction makes a big difference, and I wanted to be clear on which one it was.

Please don´t be mad. I didn´t mean to come off that way.:(

---

### Post by antoz on 2007-04-08
It started as a boot-grub problem first (couldn't even get to the login screen)when this was fixed **It became a login issue **
It takes a lot more then that to get me mad. Have a great day or night here it is 4:24 in the afternoon.A

---

### Post by nxMarc on 2007-04-08
Sorry for being offline so long and thanks everyone for trying to help...
Looks like I've missed a lot.

I'm gonna read antoz's thread now... then I'll reply.

---

### Post by nxMarc on 2007-04-08
I've read couple of this threads, but now I'm even more confused... :confused:
This problem is similar to mine, but I realy have no idea what to do.

Anyway, UUIDs seem to be OK, just as /etc/fstab, if this helps...

I tried also booting live. There are my partitions, but they're all empty!

If there is no chance in saving files from "missing" partitions, maybe I could just start thinking about fresh install... :(

---

### Post by antoz on 2007-04-08
[http://users.bigpond.net.au/hermanzone/](http://users.bigpond.net.au/hermanzone/) 
[http://www.psychocats.net/ubuntu/](http://www.psychocats.net/ubuntu/)

I really don't know how to help you any further my problem was that the fstab was not configured obvioulsy yours is different. The above links are very helpfull.

---

### Post by ComplexNumber on 2007-04-08
**nxMarc**
the problem that you're encountering is _exactly_ the same as the one here:
[http://ubuntuforums.org/showthread.php?t=371052](http://ubuntuforums.org/showthread.php?t=371052)

---

### Post by jerryrw on 2007-04-08
It's been a busy night.  I thought I would go through a recap and my trouble shooting process on this one.

>>In OP Post #1
>>I get login screen
>>And get error "your home directory is listed as: /home/marc/ but it does not appear to exist"

Could be several things, we really need more info.  Can you get to single? Can you get /etc/fstab, fdisk -l, dmesg?

>>In OP Post #3
>>/home directory is here. But it seems like /home/marc isn't.

If this is from single user mode then this begins to rule out a 'file' permission problem as the home dir /home/marc doesn't exist so fixing permissions on .dmrc wont work and root cant see any user dirs in /home.  Another thing that noone has thought of so far is: Was /home/mark deleted?
If this is from a successful user(marc) login in 'recovery' mode then a permission prob may still be the issue.

>>In Laurel Lynn Post #7
>>cat /etc/fstab

That would be the first thig I would look at too.

>>In OP Post #11

We get the fstab:

With UUIDs removed for clarity:   [http://en.wikipedia.org/wiki/UUID](http://en.wikipedia.org/wiki/UUID)

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/sda4     /               ext3    defaults,errors=remount-ro 0       1
/dev/sda2     /home           ext3    defaults        0       2
/dev/sda1     /torrents       ext3    defaults        0       2
/dev/sda3     none            swap    sw              0       0
/dev/scd0     /media/cdrom0   udf,iso9660 user,noauto     0       0
```

Being able to get this far tells us a couple of things, most importantly that / is mounting, at least in ro mode as we can get to the /etc and /bin directories. 

First thing that I note is that this is not 'standard' for a desktop install.  Not necessarily bad but it was a custom part job.  So I would want to know if these partitions actually exist on the drive.

>>Post #20
>>Ah, but it isn´t BSD, Ptero-4 ( spent most of my time on IRIX, ohhh so long ago). 

Makes me want to go fire up that old Octane in storage :)

>>In Laurel Lynn Post #29 
>>Most of the logs are in the /var/logs

Great place to start looking but implies /var being mounted as this is in the / part according to the fstab shouldn't be a prob.
  
For this particular issue I would like to get a dmesg.

>>In Complex Number Post #33
>>i bet you thats not the solution . in fact, its not even close.

At this point I am tending to agree.  But /home being empty also suggests mounting issues.

>>In Complex Number Post #39
>>3) the error that the OP stated in his first post (ie "your home directory is listed as: /home/marc/ but it does not appear to exist") is a permission error.

Not necesarily true (but highly likely in Ubuntu).  If the /home partition is not mounting the /home partition to the /home entry in the root file system these symptoms will happen as well.  With the /home on it's own partition and the directory being totally empty strongly suggests mounting issues.

Hence the Trouble Shooting confusion.

Under a default Ubuntu install the base user is not root and cannot su directly.  And if that username cannot see the /home dir due to permission problems you get the same symptoms as a mounting issue.

Most 'old school' *nix heads will log on as root to do the real investigating. The default setup of Ubuntu makes this difficult as being in the admin group (what happend to 'wheel') only allows access to sudo and such, not direct access to root owned files.  So a sudo ls -al /  and a sudo ls -al /home  may have also been appropriate suggestions to the OP

The biggest trick in TS a Ubuntu distro is remembering to never take for granted that the user has root powers.

If you really want to see permissions issues in Ubuntu, do the chroot install from another distro.  

Alas I think the OP has gone to reinstall.  It's Been a great thread though.

---

### Post by LaurelLynn on 2007-04-08
Dear jerryrw, 

Love the recap, very concise.

One thing it reminded me of that might be of use - contrary to what I keep hearing about Ubuntu not having a root account.  A little poking around seems to indicate that it is only disabled.

¨ls /root¨  on a working Ubuntu system will even list a Desktop directory.

As near as I can tell, the ONLY thing missing with the root account is that the /etc/shadow entry has a ¨*¨ for the password. Thats a pre-GUI method of disabling a user account (after the ungreatful so and so just quit).  If that is all that was done, deleting that one character should completly restore a conventional root user (after a quick passwd, so that you don´t leave the doors wide open). Which has it´s home directory on / instead of /home.

Laurel Lynn ;)

---

### Post by jerryrw on 2007-04-08
You can enable root easily in Ubuntu with a quick  sudo passwd root and then edit the /etc/gdm/gdm.conf.  In there is a line something like EnableRootLogin=no.

I've done this on 4 machines in each of Dapper,Edgy and Feisty and it seems to work fine.  Makes Admining these things so much easier.

---

### Post by LaurelLynn on 2007-04-08
Dear jerryrw,

That will work too.

My personal solution to having to type the password again and again when modifying protected stuff, is to use Gnome.

I just added to two items to ¨System Tools¨,  ¨Filebrowser (root)¨ and ¨Terminal (root)¨. Then I added Launch Icons for them to the top panel.

To su or gksu for awhile I just double-click. ( only works when you can log in and get xstarted though)

Laurel Lynn

---

### Post by nxMarc on 2007-04-09
Hi...

Just wanted to say thanks to all of you wonderful peoples trying to solve my problem.

Unfortunately, I quited. I was trying a lot of things, but it just didn't work. Looks like my home directory was deleted (I have no idea how), and also data on my other partitions. 
Finaly, system crashed totaly and even GRUB wasn't loading anymore. 
Now I belive it could be a HD mailfunction, as there were problems with both Ubuntu and Windows reinstallation.
Anyway, now I've somehow got working OS, but I think that I'll check my HD as soon as I get.

LaurelLynn, ComplexNumber, jerryrw, antoz... Thank you.
And, anyone, don't say me ever again that Linux has bad technical support. :p

---

