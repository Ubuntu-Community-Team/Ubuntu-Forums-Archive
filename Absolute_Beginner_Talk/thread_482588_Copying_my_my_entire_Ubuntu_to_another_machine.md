---
title: "Copying my my entire Ubuntu to another machine"
date: 2007-06-23
forum: Absolute Beginner Talk
---

### Post by wgw on 2007-06-23
My laptop is on its last legs. I will get another one soon. The next problem will be: how to get my files and Ubuntu setup to the new machine? 

The only thing I can think of for the moment is do a new install of Ubuntu, then reinstall every application I presently use (oof!). Then copy over my user files. 

That seems like a lot of work. I will lose all kinds of important configuration files, like Firefox passwords (though I can find the bookmark file). 

Is it possible to simply copy applications like Firefox to a new machine? (My feeling is that it can't be done). I'm assuming I can't simply make a backup of the old machine and restore to the new one because application files will be configured for the old hardware. Partition image files won't work either, for the same reasons. And of course my old machine is a dual boot...

I will probably end up doing  it all by hand, but there might be some suggestions about how to streamline the process....

Thanks!

---

### Post by BobCFC on 2007-06-23
If you press Crtl-H in your home directory or goto the View menu it will show your hidden files.  Anything that starts with a dot is the config for that application.  Try copying the .mozilla directory to the home folder on the new PC.

Unix is pretty good about keeping the app config seperate from the machine config

No guarantees though.

---

### Post by nike984 on 2007-06-23
hook up the new hard disk to the your Ubuntu Computer and 
use this command

```
cat (Original Hard disk) > (New one)
```So, for example, if the disk that Ubuntu is install is "/dev/hdb"
and the new disk that you hook up into your computer is "/dev/hdc"
Just type 

```
cat /dev/hdb > /dev/hdc
```
and this will copy everything from /dev/hdb to /dev/hdc

After that, remove the new hard disk and plug it into other machine and it will work.

---

### Post by wgw on 2007-06-24
That drive copy sounds too good to be true! Wouldn't hardware specific configuration be overwritten? (Like if the video card is  different or the wirekess.) At any rate, it is so simple, there is no reason not to try it. 

Thanks for both tips.

---

### Post by freebird54 on 2007-06-24
You are right in that it will NOT be as simple as a straight copy.  However, if you do a fresh install, add in your apps, then copy over your /home directory - the majority of application settings etc will be carried over - along with whatever data you have generated.  Good probability of success there. :)

Hope it helps...

---

### Post by ugm6hr on 2007-06-24
I've never done this - but I thought I'd give some thoughts....

Presumably if you backup your whole *home *directory (including hidden), you could just copy it onto your new hard drive *home *directory after re-installing Ubuntu on it.  That should keep all your bookmarks, passwords, settings etc, shouldn't it?

As for re-installing all your applications, assuming they are all from the repositories, you could just backup all the files in */var/cache/apt/archives/* and copy them to your new machine (in the same directory name).  Then you can just select them all from Synaptic Package manager (or use the Terminal) to install on the new machine without having to download via internet.

Perhaps someone who knows about these things could comment if this is true?

---

### Post by freebird54 on 2007-06-24
That could be a time saver too - assuming that he hasn't cleaned out the archives! 

You could say that this situation is a good reason to have a separate /home partition - then it's just a partimage away... :)

---

### Post by wgw on 2007-06-24
Yes, when I set up my new computer I am going to follow the recommended partition structure (with a separate data partition). And I should document my migration to new hardware, since I'm guessing others will have to do the same at some point.

It seems like it could be more automated, and I guess it can, except that we really don't plan for  the "next computer". For instance, there should be a way to generate a script on the old machine that will automatically install all the applications on the new machine. Right now, it looks like I will have to manually select each application, whether it archived or not.

---

### Post by nike984 on 2007-06-24
> **nike984 said:**
> hook up the new hard disk to the your Ubuntu Computer and 
use this command

```
cat (Original Hard disk) > (New one)
```So, for example, if the disk that Ubuntu is install is "/dev/hdb"
and the new disk that you hook up into your computer is "/dev/hdc"
Just type 

```
cat /dev/hdb > /dev/hdc
```and this will copy everything from /dev/hdb to /dev/hdc

After that, remove the new hard disk and plug it into other machine and it will work.

One of my friend at a computer lab usually use this method to set up the whole lab 
in the same environment; Setup 300~500 computer at a time.
Usually, most of the computer in the lab has same hardware, similar spec, 
so there was no problem. 
He even use this command to copy computers with Window XP:p

In your case, Two computers will have a different spec, so I also think that I won't
be that easy, but you can still use that command after slightly modifying the path.

---

### Post by wgw on 2007-06-25
I will probably want to modify some things on the new system anyway (configuring things differently), but it does look like the migration will not be too time consuming, even though a bit will be crafted by hand. 

Thanks for all these suggestions. I hope to post here a summary of my migration log (listing what works and what doesn't!)

---

