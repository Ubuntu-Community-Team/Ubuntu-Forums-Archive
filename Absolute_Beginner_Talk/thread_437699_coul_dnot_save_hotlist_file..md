---
title: "coul dnot save hotlist file.  ?????"
date: 2007-05-09
forum: Absolute Beginner Talk
---

### Post by beanco on 2007-05-09
so, in addition to the other problems I am having today with Ubuntu I got htis msg with my opera email client


could not save hotlist file.

/home/robi/.opera6.adr 

what the heck does that mean?

I now cannot even access the opera email client..

robi

---

### Post by kidders on 2007-05-10
Hi there,

My guess would be that you're either out of disk space, or you've denied yourself access to (at least parts of) your own home directory.

---

### Post by beanco on 2007-05-10
agian as a neophyte I am not sure how to check disk space or to see if I have denied myself access..

what should I do to check?


thanks


robi

---

### Post by kidders on 2007-05-10
> **beanco said:**
> I am not sure how to check disk space or to see if I have denied myself access.

You can get an idea of how much disk space you're using with **df**

The output of **ls -l /home/robi/.opera6.adr** (assuming the file exists) will show you what access privileges you have for that file. **ls -ld ~** will do the same for your home directory.

My suggestions are little more than shots in the dark, but they should give you someplace to start. :-)

---

### Post by beanco on 2007-05-10
Kidders.

thanks for the info... but I am havine even more serious pobls a tthe moment


see:

[http://ubuntuforums.org/showthread.php?p=2626766](http://ubuntuforums.org/showthread.php?p=2626766)

soon as I get that issue fixed I will try your solutions.

thanks

robi

---

### Post by kidders on 2007-05-10
My suggestions were aimed at identifying the problem ... not solving it, I'm afraid.

My guess is that both threads are related, in that you may have somehow managed to mangle your home directory. I suspect you have simply locked yourself out of it, which is what I was trying to establish.

Hopefully, once your other thread is solved, this problem will go away.

---

### Post by beanco on 2007-05-11
i hope so too...

if you have nay idea on the other thread, let me know.

thanks

robi

---

### Post by kidders on 2007-05-11
Hmm... the posts over there seem to suggest exactly what I would have suggested, if my theory about your home directory turned out to be true. There are two phrases that jumped out at me as worrying though...
[LIST]
[*]so i just used mc and deleted several files
[*]ld.sobject ;libjvm.so' from LD_PRELOAD cannot be preloaded:ignored
[/LIST]
I'm not sure what "mc" is, but your post sort of seemed to suggest that you might have deleted random things by accident.

The second error is a problem with your Java virtual machine, involving system libraries that are either missing, or inappropriate for your system.

Anyhow, one thing at a time! Have you corrected the permissions problems in your home directory? Making sure you have the appropriate access to your own data is important.

---

### Post by beanco on 2007-05-11
hi,

mc  is midnight comander... i used it to delet a few flims that were on teh hard drive as one thread suggested there maybe a lack of space... i was just freeing things up...

as for the premissions problems i have not been able to get it done.

when i typed in 

```
sudo chown -R robi:robi
```

I got the error: chown missing operand after 'robi:robi'

and I have no idea what operand means...


robi

---

### Post by kidders on 2007-05-11
Yeah, that's a bit obscure! "Operand" is a mathematical term for something an operator ... well ... operates on. Basically you forgot to tell **chmod** what to change the permissions _of_.

You probably intended something like **chown -R robi:robi *** or **chown -R robi:robi ~**. Whatever you do though, don't hit enter until you're **sure** the command will do what you want it to do. It can be extremely damaging, when mis-applied.

I hope that helps.

---

### Post by beanco on 2007-05-11
Kidders I just used what was written in the post here... i did not think that iwould have to to it what to change etc.

but that was not the problem though...

turns otu there was a damgaed file.. the sys op where i teach is happy that I am now a linux user and helped me... 


thanks everybody here!!!!


robi

---

### Post by kidders on 2007-05-11
Glad you solved your problem. :-) Sorry we all jumped to the wrong conclusion!

---

### Post by beanco on 2007-05-11
well as alays the help was much appreciated!!!!!

Mauzi suggested I upgrade to feisty... I am going to look into that later on.

robi

---

### Post by kidders on 2007-05-11
Sounds good. :-) Be sure your existing installation is in good working order first though. Unexpected weirdness could cause an upgrade to fail.

---

### Post by beanco on 2007-05-14
more silly opera probs

> OpenFile r+ failed, file: (/home/robi/.opera/mail/store/account1/2007/05/14/5053.mbs). Total: 178


what that mean????

thanks

robi

---

### Post by kidders on 2007-05-14
Again, that looks like it could be permissions-related, although corruption (as caused your previous issues) could also be to blame. Just be aware that the problematic file is an email cache ... if there is a chance it contains something important (eg if you're not using IMAP), you should back up your entire .opera directory immediately, just in case something bad happens.

Since it looks as though you are running into the same sort of problem over and over, there are a few possibilities that are worth mentioning, most of which I'm sure you already know...

[LIST]
[*]Failing to cleanly dismount filesystems causes corruption.
[*]Altering file access permissions without a good understanding of the potential impact is a bad idea.
[/LIST](As I said, I'm sure you already know these)[LIST]
[*]Your root (or /home) filesystem may be damaged -- I would strongly suggest checking it.
[*]If Opera is crashing, that would also explain this particular issue.
[*]Your hard disk may be damaged. Your system logs will tell you if that's the case. (There would be long lists of I/O errors in them.)
[*]Opera may have a bug in it. It might be worth taking a quick look through Opera's forums for similar issues. I find this unlikely though ... Opera 9 has had a number of revisions, so you would expect most bugs to be fixed.
[/LIST]
Out of interest, what type of filesystem is your /home stored on?

I'm pretty anxious to sort this out for you ASAP ... there is no point in using a computer (or operating system) that you can't trust to store your files properly!

---

### Post by beanco on 2007-05-14
Hi Kidders,

>   Again, that looks like it could be permissions-related, although corruption (as caused your previous issues) could also be to blame. Just be aware that the problematic file is an email cache ... if there is a chance it contains something important (eg if you're not using IMAP), you should back up your entire .opera directory immediately, just in case something bad happens.

What is IMAP? I will look into it... I will also make a copy of the .opera directory, 


> 

[*]Failing to cleanly dismount filesystems causes corruption.
[*]Altering file access permissions without a good understanding of the potential impact is a bad idea.


well, how does one know if he is dismounting cleanly or not? 

I have not really altered any permissions... because I do not clearly udnerstand what it is.. I get the basic concepts.. jut cannot remmeber how to do it... when , why,, why not do it...

There are 5 persons with log ons to this computer.

I would like to be the overall super user, tha tis have rights to everything.

The kids should only be able to read, write, execute files in their own spaces and not have access to anything else... 


> [QUOTE][/LIST](As I said, I'm sure you already know these)[LIST]
[*]Your root (or /home) filesystem may be damaged -- I would strongly suggest checking it.

how is it done?


> If Opera is crashing, that would also explain this particular issue.

Opera is not crashing per se... it just has that mail issue. at least so far that is all I have seen...

> Your hard disk may be damaged. Your system logs will tell you if that's the case. (There would be long lists of I/O errors in them.)

I will look into it,,, just have to search the forum to find out how this is done..


> Opera may have a bug in it. It might be worth taking a quick look through Opera's forums for similar issues. I find this unlikely though ... Opera 9 has had a number of revisions, so you would expect most bugs to be fixed.


I doubt it is a bug...




> Out of interest, what type of filesystem is your /home stored on?

I have no idea!



> I'm pretty anxious to sort this out for you ASAP ... there is no point in using a computer (or operating system) that you can't trust to store your files properly!

so am I and again, thanks for all the help!!!!

robi

---

### Post by kidders on 2007-05-14
> **beanco said:**
> What is IMAP?IMAP is a mail protocol that normally retains copies of your email on the remote server ... in which case, you could probably just delete the faulty Opera caches and reload all your mail from your mail server (like you could do with cached web pages).

On the other hand, if your .opera directory contains the only copy of your mail, it would be important to make a backup now, just in case something you do (or something I suggest!) makes the damage worse.

> **beanco said:**
> how does one know if he is dismounting cleanly or not?Usually, remembering to shut down your computer properly is all you need to do. As you may know, not shutting down correctly can cause damage.

> **beanco said:**
> I have not really altered any permissions.Damn. That would have been the easiest problem to solve! :-( Hehe.

Can I ask you to post the results of executing the following, just to rule out some possibilities:
[LIST]
[*]ls -ld ~/.opera
[*]ls -l ~/.opera/mail/store/account1/2007/05/14/5053.mbs
[*]mount
[*]grep -i "i\/o" /var/log/syslog
[/LIST]

I would also be happy to examine your mail caches for any obvious errors, if you were to package them up with something like **sudo tar -cjf ~/opera_settings.tar.bz2 ~/.opera** and PM me the result. _Doing so would reveal private information_ though, so you may prefer not to.

> **beanco said:**
> how is it done? [SIZE="1"][Filesystem check][/SIZE]I'll be able to tell you that after your next post. It involves running a program called **fsck**, but it **_requires_** that the filesystem being scanned be dismounted at the time ... so you may need help. Your next post should also tell us whether there is any physical damage on your hard disk (the "grep" command I mentioned *should* pick up on error reports).

> **beanco said:**
> I doubt it is a bug.So do I. All the same, I wanted my list of possible causes to be as complete as possible.

> **beanco said:**
> There are 5 persons with log ons to this computer.

I would like to be the overall super user, tha tis have rights to everything.Linux prefers not to work this way. The "super user" is almost never a real person, since using that account would:
[LIST]
[*]Allow the user to make mistakes that could seriously damage the system.
[*]Give a malicious program or virus infecting the account uncontrolled access to the entire computer.
[/LIST]
Instead, certain users are granted the right to temporarily slip in and out of the super user account (called "root") by being given access to a command called **sudo**. That way, any user who wants to act as root gets a chance to stop and think about what they're doing, before it happens. By default, Ubuntu grants all members of the "admin" user group access to **sudo**, so I would suggest adding yourself, and removing everyone else.

In day to day operation, all users (including you) would then be subject to the same access restrictions, designed to keep your PC safe from harm. Any time you want to do something that requires elevated privileges, you can simply precede the command with the word "sudo". _It is very important never to log into your computer as root_, unless you know what you're doing.

> **beanco said:**
> thanks for all the help!!!!No problem. :-)

---

### Post by beanco on 2007-05-14
kidders..

thanks for teh offers and the info

as for sudo. i am the only one that uses it.... the kids have no idea what it is

but as a back up I could remove them... possible in the systems/administration/users-groups?


fsck I have used.. every 30 shout downs i have to run it.... the kids simply do not use the computer if they get that msg saying that it needs to be run.

I will get back to you later

My wife is out of town and I am on kid duty for the week... it is dinner time here.

robi

edited to add IMAP:

I just checked opera... and when i hit the IMAP option it wanted me to first set up an account.. gues that means I ahve not been using IMAP of yet.

---

### Post by beanco on 2007-05-14
Kidders,

for you reading pleasure while I make/adminster/eat dinner


robi@robi:~$ ls -ld ~/.opera
drwx------ 11 robi robi 4096 2007-05-14 18:28 /home/robi/.opera
robi@robi:~$ ls -l ~/.opera/mail/store/account1/2007/05/14/5053.mbs
-rw-r--r-- 1 robi root 11715 2007-05-14 14:13 /home/robi/.opera/mail/store/account1/2007/05/14/5053.mbs
robi@robi:~$ mount
/dev/hda1 on / type ext3 (rw,errors=remount-ro)
proc on /proc type proc (rw)
/sys on /sys type sysfs (rw)
varrun on /var/run type tmpfs (rw)
varlock on /var/lock type tmpfs (rw)
procbususb on /proc/bus/usb type usbfs (rw)
udev on /dev type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
devshm on /dev/shm type tmpfs (rw)
lrm on /lib/modules/2.6.15-28-386/volatile type tmpfs (rw)
/dev/hdc on /media/cdrom0 type iso9660 (ro,noexec,nosuid,nodev,user=robi)
/dev/sda1 on /media/UDISK 2.0 type vfat (rw,nosuid,nodev,quiet,shortname=mixed,uid=1000,gid=0,umask=077,iocharset=utf8)
robi@robi:~$ grep -i "i\/o" /var/log/syslog
May 14 18:16:38 localhost kernel: [17179569.184000] Enabling APIC mode:  Flat. Using 1 I/O APICs
May 14 18:16:38 localhost kernel: [17179573.952000] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
May 14 18:16:38 localhost kernel: [17179573.956000] 00:06: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A

exciting stuff this linux is...

robi

---

### Post by beanco on 2007-05-14
> **kidders said:**
> I

I would also be happy to examine your mail caches for any obvious errors, if you were to package them up with something like **sudo tar -cjf ~/opera_settings.tar.bz2 ~/.opera** and PM me the result. _Doing so would reveal private information_ though, so you may prefer not to.


I got this

> tar: Removing leading `/' from member names

now if I only knew what memer names are I would remove the  `/' from it


robi

---

### Post by Ptero-4 on 2007-05-14
From what I see you don´t have hard disk problems and your filesystem is ext3 (which is a good thing since this one tends to be reliable as long as you remember to shutdown properly (System>Logoff... and then press the shut down button in the dialog).

---

### Post by kidders on 2007-05-14
> **Ptero-4 said:**
> From what I see you don´t have hard disk problems and your filesystem is ext3 (which is a good thing since this one tends to be reliable as long as you remember to shutdown properly (System>Logoff... and then press the shut down button in the dialog).I agree. If there was any kind of physical problem, your system logs would be littered with hundreds of ugly complaints

> **beanco said:**
> tar: Removing leading `/' from member namesThat's just an informational message.



> **beanco said:**
> for you reading pleasure while I make/adminster/eat dinner:lolflag:

> **beanco said:**
> ```
robi@robi:~$ ls -l ~/.opera/mail/store/account1/2007/05/14/5053.mbs
-rw-r--r-- 1 robi root 11715 2007-05-14 14:13 /home/robi/.opera/mail/store/account1/2007/05/14/5053.mbs
```That's curious. Do you run Opera as root?

> **beanco said:**
> ```
robi@robi:~$ mount
/dev/hda1 on / type ext3 (rw,errors=remount-ro)
```Thanks for that. I basically wanted to be sure you weren't using an odd filesystem in your /home. If you wanted to, you could boot your computer off a CD and run **sudo fsck.ext3 /dev/hda1** to check for corruption, but I would be surprised if you found any problems, to be honest. (As you mentioned, your system does that automatically every so often anyway.)

---

### Post by beanco on 2007-05-14
nice to know my file system is a stable one...


> **kidders said:**
> ...
That's curious. Do you run Opera as root?



i have no idea!

if it is importan than I can check...

robi

---

### Post by kidders on 2007-05-14
It *could* be important ... I'm not sure. The reason I ask is that running applications as root can cause odd behaviour (and is usually regarded as the most reliable way of asking for trouble ... and getting it!) It looks as though your mail caches may involve the root user in some way.

Having said that, I don't _see_ any particular problem, but I thought I'd ask the question anyway. I don't know enough about how Opera handles mail.

Anyhow, I would suggest doing the following. If it makes any difference, then I might be on to something. If not, I'll have to think about it some more.

**sudo chown -R robi:robi /home/robi/.opera**

If you still have no joy, try...

[B]sudo chmod -R 644 /home/robi/.opera
sudo chmod -R +X  /home/robi/.opera
[/B]
These commands will force any wayward ownerships & permissions back into line.

If you still have no luck, I would suggest removing your Opera preferences and recreating them ...

**mv ~/.opera ~/dot_opera**

Opera will then revert to its default configuration, and you can re-import your bookmarks, mail, etc. The trouble with this (assuming it fixes everything) is that we won't have found out what caused the problem in the first place, so there's no way to be sure it won't happen again. :-(

**Edit:**
> nice to know my file system is a stable one.Yeah, the Extended filesystem is pretty old, and is a solid, general purpose filesystem that is well trusted.

**Edit:**
> Do you run Opera as root?Another way of asking the question is...
[LIST]
[*] Have you ever logged in to your graphical environment as root, and opened opera?
[*] Have you ever launched **sudo opera** or similar?[/LIST]

---

### Post by beanco on 2007-05-15
[QUOTE
Another way of asking the question is...
[LIST]
[*] Have you ever logged in to your graphical environment as root, and opened opera?
[*] Have you ever launched **sudo opera** or similar?[/LIST][/QUOTE]


Not that I know of... can it be checked?

I have opened opera interminal but not as root... just as plain old user robi


I will try the chown ocmmands you suggest....

as to

 I> f you still have no luck, I would suggest removing your Opera preferences and recreating them ...

mv ~/.opera ~/dot_opera

Uh, ok... what is MV???? and how will I recreat the preferences? Just go to opera, tools. prefs?

robi

---

### Post by kidders on 2007-05-15
[LEFT]mv = move

(It'd have the same effect as erasing your Opera settings, except that you could presumably reimport them all again. Irritating, but having Opera rewrite everything from scratch really ought to fix *any* problem!
[/LEFT]

---

### Post by beanco on 2007-05-15
that is what i thought...

then i looked it up and foudn that i ws correct.. mv = move


> sudo chown -R robi:robi /home/robi/.opera


i will try it when i get back home.

if that and the other ideas fail i will try the mv one

if I do move them and have to creat the opera prefs manually. is that done like i ask, ie. opera/preferences...
thnks


robi

---

### Post by kidders on 2007-05-15
I presume so ... you may want to check you can do everything you'll need to, before you try.

---

### Post by beanco on 2007-05-15
> **kidders said:**
> I presume so ... you may want to check you can do everything you'll need to, before you try.

what?


BTW i tired the  

>  sudo chown -R robi:robi /home/robi/.opera

and got this

> robi@robi:~$

robi

---

### Post by kidders on 2007-05-15
> **beanco said:**
> what?I just meant that *after* getting Opera to create you a fresh ~/.opera directory would be the wrong time to discover you weren't able to re-import all your settings!

> **beanco said:**
> BTW i tired the```
[SIZE=2]sudo chown -R robi:robi /home/robi/.opera[/SIZE]
```and got this```
robi@robi:~$
```Perfect. (No errors = good?)

---

### Post by beanco on 2007-05-16
opera seems to be working fine now...

any tests you would suggest I run?

robi

---

### Post by kidders on 2007-05-16
Not really. What did you have to do to get Opera to cooperate?

---

### Post by beanco on 2007-05-16
All I did was run this

> sudo chown -R robi:robi /home/robi/.opera

and everything seems to be working... at least I can see all my msgs and I do not get those error msgs I was getting earlier!

thanks

robi

---

### Post by kidders on 2007-05-16
Hmm... In that case, file access permissions *were* the problem. You may have done one of the following at some point...
[LIST]
[*]Launched Opera using **sudo**.
[*]Copied some of your Opera preferences around, as root.
[*]Accidentally set a new owner for some of your files.[/LIST]Hopefully, you won't have any more trouble. :-)

---

### Post by beanco on 2007-05-16
or maybe i did all of the above adn did not even know it..

but maybe the kids did it without knowing...

thanks for all the help!!


robi

---

### Post by kidders on 2007-05-16
No problem. :-)

---

### Post by beanco on 2007-05-17
kidders, sorry to bother you. check out the new post on the beginners forum i made under beanco... it is quite urgent.

and doesn't this forum have som kind of private msging syste?

robi

---

### Post by beanco on 2007-05-29
It has started again

I got some error msg but did not have time to deal with it. logged off, and left.

when i logged back on later and fired up Opera i got the 

> could not save hotlist file

error msg!!!!

now I have no mail panel in Opera...

I think maybe it is time to just give up on Opera...

robi

---

### Post by kidders on 2007-05-29
Hmm... It's at least remotely possible that there's a bug in Opera (although personally, I've never encountered anything like what you've described). Have you checked with their support people?

The trouble is, you see, that if the problem is being caused by something *you're* doing (rather than something Opera is up to), you'll probably encounter this issue no matter what web browser you use. :-(

[COLOR=Silver][[SIZE=1]*[UAResolved]*[/SIZE]]("http://ubuntuforums.org/showthread.php?t=377083")[/COLOR]

---

### Post by beanco on 2007-05-30
Kiders, I will be posting over at the Opera forum later on.

There will be a lull in the computer usage here for a while. this means that I will be the only one using it and can see what happens.

| have no idea what I could have done.

|I open and close programs in the normal manner. I do not mess round with permissions.

I do not change any prgm files.

At least I do not do this stuff on purpose.

I tend to have a ton of tabs open, but I doubt that is the issue.

Robi

---

