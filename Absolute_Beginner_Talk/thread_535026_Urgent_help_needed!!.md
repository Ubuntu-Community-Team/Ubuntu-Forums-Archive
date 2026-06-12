---
title: "Urgent help needed!!"
date: 2007-08-25
forum: Absolute Beginner Talk
---

### Post by detroit/zero on 2007-08-25
I really did it this time.

I ran across some page that offered tips on how to clean up your Ubuntu system. I was moving though it and a package name GTKOrphan (or some such thing) caught my eye. "An easy way to remove orphaned packages from your system and free up space," they say. Yeah it is.

It even said on this "how-to" that the first time you run the orphan uninstaller, the list of files it finds may be quite large.

Well, I ran the thing and wasn't paying attention to what I was uninstalling. (See where this is going yet?)

Tons of stuff was wiped out. I mean **tons**. The biggest problem I am facing right now is that my GUI is history.  I have access to the command-line interface, but that's it. I'm running off the livecd right now.

I'm taking this in stride - I've been meaning to do some serious housecleaning as of late, and I guess this is a good opportunity.

I have two options, I suppose:
1. Copy all the stuff that got deleted from the livecd (don't even know where to start - the thing even erased my backup kernel)
2. Backup all the stuff I want and do a fresh install (highly time consuming and sure to kill the rest of the weekend)

I'm working towards the fresh install option already, but it's not too late to switch. The only problem I'm running into is that there's some empty space on my hard disk ([as I outlined in this post]("http://ubuntuforums.org/showthread.php?t=483344")) I've been meaning to merge into my Ubuntu partition and save a little for backup purposes in the event something like this ever happened. Only thing is, I haven't gotten around to it yet.

So, here I am on a livecd. I've resized the Ubuntu partition, but when trying to create a new partition in the rest of the unallocated space, Gparted gives me an error message about needing to create an extended partition (this is a dual-boot laptop with Vista on the other partition, plus swap space, Toshiba System Volume - all primary partitions). Creating an extended partition isn't an option in Gparted as far as I can see. How can I create my backup partition in this free space?

Also, I don't have permission to read any of the files I want to backup (basically just what's in /home/myname - program settings, saved documents and such..). How do I change this?

Thanks for any help. I'm in dire need here.

---

### Post by nonewmsgs on 2007-08-26
well i cant help with the major problem, but i can with a minor one.

sudo nautilus will open a new desktop window and you can explore your stuff and right click on drives or folders to change permissions.

---

### Post by p_quarles on 2007-08-26
I would suggest reinstalling. Not only because it's easier, but because you don't really know what that "orphan uninstaller" did to your system. The only way, at this point, to be sure that you don't have a keylogger in your root partition is to wipe the drive/partition.

For backup, there are several options. Command line would be easiest, but you can also run the Ubuntu live disk under "recovery" mode and copy stuff onto your medium of choice.

---

### Post by detroit/zero on 2007-08-26
Thanks, [nonewmsgs]("http://ubuntuforums.org/member.php?u=240189"). I guess I'm a little bit flustered.. I can't believe that didn't occur to me.

You have a good point, [p_quarles.]("http://ubuntuforums.org/member.php?u=290682") I hadn't thought of that, either. I'm assuming this program is benign; it installed through apt-get.. I suppose anything's possible, though.

In all honesty, I'll be happy just getting my FireFox Bookmarks and a few other things onto a thumb drive and I'll rebuild the rest as I go.

Thanks for the quick responses, guys. I'll let you know how it turns out.

---

### Post by p_quarles on 2007-08-26
Oh, you installed it from the repositories? I guess I was wrongly assuming that you got it from a web page. Using APT is usually pretty safe.

Before you do anything else, see if this solves your problems:
```
sudo apt-get install ubuntu-desktop
```
If you uninstalled as much as you indicated, this could take a while. :) Should fix it, though.

---

### Post by detroit/zero on 2007-08-26
OK, I'll give that a shot. I have a few operations winding down, but I haven't done anything irreversible yet.

I managed to find the page where I got the link for that program from. [It's here.]("http://ubuntu-tutorials.blogspot.com/2007/01/cleaning-up-ubuntu-gnulinux-system.html") It wasn't installed through apt-get, it was wget a debian package. You'll see the section on GTKOrphan about 1/3 of the way down the page. I looked up the program and did a little research before I went and ran it. I guess I didn't do enough research though, particularly into "proper" usage..

It's going on 1AM here.. I may just throw in the towel for the night so I can get an early start on this in the morning.

I was thinking just now, though, that a lot of things got erased. I don't know if this program had an "undo" option or anything because it deleted itself. Go figure that one.. Also, it never asked to make any backups or anything so I assume all my stuff is history. If I'm going to have to re-install a million apps, I might as well do it on a fresh system and not try to put humpty-dumptyt back together again. I'll give that command a shot, though, and see what happens.

In any event, I'm signing off. I think I need to sleep on this one.

I'll update in the AM.

Thanks again.

---

### Post by p_quarles on 2007-08-26
Yes, get a fresh start. I've been through enough "I'm going to stay awake until I fix this even if it kills me" sessions to know that they aren't the best idea.

Since this program was apparently a .deb package, I would be pretty wary about what it's doing, unless you have really good reasons to trust the source. Of course, if *I* were going to write a spyware script, I wouldn't design it to disable the user's GUI . . . but, better safe than sorry. 

Copying important files to floppy/zipdisk/CD/external HD is really pretty easy. If you don't find a howto, ask here and someone will definitely help you. 

Best,
p_quarles

---

### Post by detroit/zero on 2007-08-26
Sorry for the delayed update, but yes, that command did restore the majority of deleted files.

I'm missing some fonts, my login window is screwed up, and I'm having some problems with dpkg and a few other things, but I'm sure I can iron it all out from here.

Thanks a million!

---

### Post by nonewmsgs on 2007-08-26
anytime mate.  :)  hopefully this update will be less troublesome.

---

### Post by Wolki on 2007-08-26
> **detroit/zero said:**
> I ran across some page that offered tips on how to clean up your Ubuntu system. I was moving though it and a package name GTKOrphan (or some such thing) caught my eye. "An easy way to remove orphaned packages from your system and free up space," they say. Yeah it is.

Don't trust automatic uninstallers and dependency cleaners, not even the one that's included in ubuntu now ("apt-get autoremove"). They tend to find stuff removable I'd rather want to keep, so always go through the things they do carefully.

But I guess you've figured this out by now. :)

Since the main problem seems to be mostly fixed by now, I'll just answer this here:

> So, here I am on a livecd. I've resized the Ubuntu partition, but when trying to create a new partition in the rest of the unallocated space, Gparted gives me an error message about needing to create an extended partition (this is a dual-boot laptop with Vista on the other partition, plus swap space, Toshiba System Volume - all primary partitions). Creating an extended partition isn't an option in Gparted as far as I can see. How can I create my backup partition in this free space?


A hard disk can only have 4 primary partitions, as you have already found out. To get more partioins on your harddrive, you need to put them as "logical drives" into a so-called "extended partition". Now, the imporant thing is that the extended partition is basically a primary partition itself, so if you already have 4 partitions, you can't create an extended partiton any more without removing one of the primary partitions first; and that there can only be one extended partition. Looking at your screenshot in the other thread, your swap is already inside an extended partition, and it's rather small. You could delete it and then make a new extended partition in the large free space, then create a logical drive for data like your /home there (and create the swap partition again). If you do this, you will probably have to edit your /etc/fstab to point your system at the new partitions.

If you have more questions about partitioning, feel free to ask. Oh, and it's best to use a livecd for making changes like this.

---

### Post by detroit/zero on 2007-08-28
Thanks for the advice, wolki.

One question, though? How do I give myself permission to read/write/execute things from my main filesystem while I'm on the live cd?

Is'nt it chmod something or another?  I looked at the help and man pages, but I'm a little unclear how to structure the command. My attempts thus far have been unsuccessful and I still can't read, archive, and copy the files to my new partition from the live cd.

Ever since the initial snafu, I've been having problems with system functionality. It works and everything,  but I have apps freezing and sometimes even X freezes and I have to do a hard reboot to regain control.. compiz is flaking out on me, nautilus windows freeze, swiftfox is barely functional.. I think I'm looking at doing that fresh install, no matter what.

I sort of go into the problems in [this post]("http://ubuntuforums.org/showthread.php?t=535428"), but it's a little obscure and hard to describe. 

It seems to me that somehow my x-cursor-themes got wiped out. For some reason, no matter what I'm trying to install or remove, I get error codes from dpkg about xcursor-themes not existing in a particular place - yet when I go look there (/etc/alternatives) the file in question is there. Apt-get install fails and installing the package from the cd fails. Most of synaptic and add/remove is non functional, but it's all inconsistent and sometimes works.

I'll still take this over windows any day, though:)

---

### Post by p_quarles on 2007-08-28
> I'll still take this over windows any day, though:smile:
Seriously? Then I guess you might not be interested in [this]("http://www.linuxgenuineadvantage.org/") :)

There's a "recover broken system" option on the live CD that you can use to get a root shell and try to fix things. That said, it looks like you're in a situation where trying to track down all the problems is going to take a lot longer than just backing up data and reinstalling Linux. 

Plus, if you don't have backups of your important files already, it's very likely that you'll some day regret that. Use this as an opportunity to buy some insurance.

---

### Post by detroit/zero on 2007-08-28
I do like the sound of that - Linux Genuine Advantage - it has a very nice ring, indeed.

I've got about a 10 or 11GB partition to back my files up on, and about 20GB worth of files to back up before I get started. I'll have to make some creative use out of my and gmail account, but it shouldn't be too much of a hassle.

I'm definitely going to put it off until the weekend, though. I should be fine until then. Emphasis on the word "should".

---

### Post by Wolki on 2007-08-28
> **detroit/zero said:**
> Thanks for the advice, wolki.

One question, though? How do I give myself permission to read/write/execute things from my main filesystem while I'm on the live cd?

Is'nt it chmod something or another?  I looked at the help and man pages, but I'm a little unclear how to structure the command. My attempts thus far have been unsuccessful and I still can't read, archive, and copy the files to my new partition from the live cd.

Chmodding changes permissions. I'd advise against doing this, since you'd be changing stuff on the main system instead of on the live system.

This is one of the things where I'd say it's ok to use super-user rights. But if you want to do the copying as a user, it's ok as well. How did you mount the partition? What rights do the files have, and who do they belong to? Either what the file manager or what "ls -l" tell you.

> It seems to me that somehow my x-cursor-themes got wiped out. For some reason, no matter what I'm trying to install or remove, I get error codes from dpkg about xcursor-themes not existing in a particular place - yet when I go look there (/etc/alternatives) the file in question is there. Apt-get install fails and installing the package from the cd fails. Most of synaptic and add/remove is non functional, but it's all inconsistent and sometimes works.


I'm not sure about this, sorry. Things you could try are
"sudo update-alternatives --config x-cursor-theme", "sudo apt-get -f install", "sudo apt-get reinstall xcursor-themes". I don't have much hope though, things like this can be difficult.

---

### Post by p_quarles on 2007-08-28
> Emphasis on the word "should"
I've always considered that statement to be the fourth law of thermodynamics :)

In any case, I've found that it's pretty easy to find a deal on a big stack of recordable CDs. Backing up your data that way will definitely take more time, but it's also more reliable.

---

### Post by detroit/zero on 2007-09-04
Well, I did it.

I put Humpty Dumpty back together again, and it didn't even take a reinstall. I'm almost a little proud of myself, actually, even though this is quite a hack..

As I said, at first I lost almost all GUI functionality, but after I got it back I was having problems with Swiftfox freezing up a lot, random apps freezing and needing a Force Quit to close out (everything from gedit to Gnometris in the games menu to terminal windows), I was missing a million fonts, compiz wasn't working right, screenlets took a left turn on me.. things were ugly around here.

I focused mainly on backing things up and preparing for a new system. I used SSH to back up nearly 50GB of data to my desktop (roughly two full 24 hr days at DSL speeds.. and I was doing it in between work and play and what not..)

Then it dawned on me: This ridiculous program went through and indiscriminately deleted files.. why don't I go through and indiscriminately put them back?

First was **Add/Remove Programs**. I opened that up, uninstalled every installed app, and then re-installed them all one by one.

Second was **Automatix** - same thing. Removed each app and add-on/plugin one by one and reinstalled them.

I was still having problems at this point with my GUI freezing and my Browser crashing here and there..

So, third was **Synaptic**. 

I first went to the *Not Installed (Residual Config)* section and did a total remove of what was there. After a couple failed attempts (that ate up a couple hours total) I ended up going through all the *Not Installed (Local or Obsolete)* section and completely removing everything there, too.

Then I went into the Installed Packages section, hit *CTRL-A* to select all, marked every program/package for re-installation (which took close to a half  hour to process 1,280-something packages for re-install..) and it threw me an error code over libdvdcss (or whatever the dvd-viewing/css-decrypting lib file is). So I hit *CTRL-A* again, but deselected that one package, and let it run.

I was prompted to insert the Feisty Fawn Install CD, and it moved some files from there while downloading others from the repos.

Four-and-one-half hours later, I had my system back. Everything works as good as or better than it did before this whole nightmare began, and I must say I learned some valuable lessons about the right and wrong ways to clean a system out.

I don't know if it's an accepted/approved method, but it worked - I avoided a complete wipe and re-install, and I'm a happy camper once again.

Thanks for the help you gave me.. Couldn't have done it without you!

---

### Post by zamie on 2007-09-04
Hi there

       While I was trying to add a new user in my laptop(ubantu 7.04) I changed the mode to all of the files belongs to /home ( zamie1 and user1 ) using " chmod 644 .* " .Later on I found my self unable to login as zamie.Then again I logged in as root in to the text mode and type the following command  “chamod 777 -R /home/zamie”. Now I can login in a dektop mode but I am having two problems which are below

1. when I log in as zamie it shows me an error
   
  $HOMME ./dmrc should be owned by the user ..... use 644

2. I can not login as root from user zamie using su( from the command prompt in the ubantu desktop) 

   zamie:$ su 
   password:
   invaliad  login

Any body has any idea how to solve those problems

Thanks

Regards
zamie

---

