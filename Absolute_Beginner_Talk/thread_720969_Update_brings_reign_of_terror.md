---
title: "Update brings reign of terror"
date: 2008-03-10
forum: Absolute Beginner Talk
---

### Post by dwilson08 on 2008-03-10
So, I decided to do a harmless little update last night. Bad call. I've had problems in the past with updates telling me they can only do partial upgrades, then magically just working one day. As was the case with this update. It said I needed something like 350Mb between over 1000 files, it sounded like a major distribution upgrade, which is weird because I have the latest distribution. Anyways, so after downloading all of that, it attempts to upgrade things, then gives me some wicked error saying that I don't have permissions or there's a problem with the server or something. I didn't understand. Whatever the case it tells me I need to restart. I do. Then comes the problems. It tells me its got some kinda problem with the Human theme (Which I wasn't using at the time) And now all the files are missing from my desktop. I tried to upgrade the files again, which it attempted then failed and said "Problem upgrading from Hardy to Gutsy" or some backwards stuff like that. Now I am throughly confused. It wouldn't allow me to open anything related to OpenOffice this morning (When I needed it) and it's becoming a bit of a nuisance. If anyone can offer any help it would be greatly appreciated, I'm not educated enough to solve my own problems. I'm back to Vista for the time being. Thanks for reading this novel.

---

### Post by Nameless_one on 2008-03-10
The fact that you're having so many problems with updates sounds curious. I am tempted to say you're doing something wrong :) What did you update? Are automatic updates enabled? 

And if nothing works, do you have a seperate home partition so you can reinstall Gutsy without losing your files? :)

---

### Post by forrestcupp on 2008-03-10
It sounds like you did an apt-get upgrade instead of an apt-get update.  You unintentionally upgraded to an alpha of Hardy.  I really don't know if it's possible to go back.  You may have to reinstall.

---

### Post by angry_johnnie on 2008-03-11
350 Megs is an awful lotta updates!  Did you have pre-released and unsupported updates enabled?  Most of the times an update has killed my system,  it's been related to that.  So I've just settled for security and recommended updates only.  I may not have the latest and greatest, but it's very stable. As forrestcupp said, you may have to reinstall.  But, if you feel like you *must*  have all the updates available, at least read the descriptions.  Sometimes it's just better to chicken out! :-)

---

### Post by dwilson08 on 2008-03-16
Well as it ends up It looks like Ive got some kind of bleeding edge version here, grub says I have the (development branch) which certainly can't be good for me. Also If I try to update it tells me "A Upgrade from 'hardy' to 'gutsy' is not supoprted with this tool" [sic] Which not only sounds like it was written by a grade four, but also confuses me. Does anyone else have some ideas here? I'd rather not reinstall everything, it's been hard to get everything the way it currently is (HP laptops don't seem to take ubuntu easily, Ive had a lot of problems that I've fixed)

---

### Post by Jerry N on 2008-03-16
You didn't mention what version of Ubuntu you have installed on your computer.

Jerry

---

### Post by dwilson08 on 2008-03-19
Well before all this happened I had Gutsy (7.10) Now, I'm not too sure.

---

### Post by Oldsoldier2003 on 2008-03-19
> **dwilson08 said:**
> Well before all this happened I had Gutsy (7.10) Now, I'm not too sure.

if grub is telling you you have a development branch, then you are now runny Hardy Alpha 6. Unfortunately you cannot revert to gutsy from hardy so you will have to reinstall or tough it out for a couple weeks.

---

### Post by elnamo on 2008-03-29
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+source/update-manager/+bug/158175](https://bugs.launchpad.net/ubuntu/+source/update-manager/+bug/158175) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				Ok, the same problem happened to my pc. I really like the error message ""A upgrade from 'hardy' to 'gutsy' is not supoprted with this tool."", but they've fixed it. Here's the bug report & solution.

[https://bugs.launchpad.net/ubuntu/+source/update-manager/+bug/158175](https://bugs.launchpad.net/ubuntu/+source/update-manager/+bug/158175)

---

### Post by dwilson08 on 2008-03-30
Thanks for your help elnamo but as far as I can tell that bug only relates to the spelling error in the message and not so much actually fixing  the update. Do you guys think this might sort itself out when the new version comes?

---

### Post by stefangr1 on 2008-03-30
> **forrestcupp said:**
> It sounds like you did an apt-get upgrade instead of an apt-get update.  You unintentionally upgraded to an alpha of Hardy.  I really don't know if it's possible to go back.  You may have to reinstall.

Isn't apt-get update only meant to update the sources list? I always thought this didn't do anything else to the system, and that apt-get upgrade should be used to update all installed packages to the newest versions.

Is this a dangerous way to update that I shouldn't use to install updates? What then should I do instead to keep my system up to date?

I always thought that it was important to update regularly this way to keep the system up to date, and that only apt-get dist-upgrade was to be avoided for a relatively high failure chance when it replaces an older distro with a newer. Am I wrong?

---

### Post by Victormd on 2008-03-30
> **forrestcupp said:**
> It sounds like you did an apt-get upgrade instead of an apt-get update.  You unintentionally upgraded to an alpha of Hardy.  I really don't know if it's possible to go back.  You may have to reinstall.

apt-get upgrade will not upgrade to Hardy... it will only upgrade installed apps. To upgrade to hardy, you would need to type:

```
update-manager -d
```

---

### Post by elnamo on 2008-04-01
> **dwilson08 said:**
> Thanks for your help elnamo but as far as I can tell that bug only relates to the spelling error in the message and not so much actually fixing  the update. Do you guys think this might sort itself out when the new version comes?


It actually updates the update-manager package, not just the spelling error.

Here's the steps to fix the error.

Fire up Synaptic 
Find update-manager  
apply update
After applying the updates, fire up the Update Manager and voila, Hardy!



The update was stalled by the error message with the interesting spelling error, and you should select to Update the Update Manager to version 1:0.87.14

I've downloaded the whole Hardy package ( about 850MB) when an error message pops out and my system restarted. Attempts to update after that brings out the error message. After a day, I found the fix, and my system is now up to date.

---

### Post by forrestcupp on 2008-04-01
Sorry folks.  I meant
```
sudo apt-get dist-upgrade
```
Just plain upgrade is ok to do.  It's just like running the update manager from the command line.

Despite my typo, it has become evident that the OP has accidentally upgraded to Hardy.  So, yeah, I would just hang in there for a few more weeks.  Hardy is in beta now and with every update, you'll be kept up to date.  If you keep up with the updates, when the final release comes out, you will just already have it.  Hardy is the long term stable release, so if you can run it, I wouldn't mess with reinstalling Gutsy.

Make sure not to use the legacy version of Envy to install video drivers, though.  If you do, with every testing kernel update, you'll be screwed.  If you don't know what I'm talking about, you'll be ok.

---

### Post by Oldsoldier2003 on 2008-04-01
> **forrestcupp said:**
> Sorry folks.  I meant
```
sudo apt-get dist-upgrade
```
Just plain upgrade is ok to do.  It's just like running the update manager from the command line.

Despite my typo, it has become evident that the OP has accidentally upgraded to Hardy.  So, yeah, I would just hang in there for a few more weeks.  Hardy is in beta now and with every update, you'll be kept up to date.  If you keep up with the updates, when the final release comes out, you will just already have it.  Hardy is the long term stable release, so if you can run it, I wouldn't mess with reinstalling Gutsy.

Make sure not to use the legacy version of Envy to install video drivers, though.  If you do, with every testing kernel update, you'll be screwed.  If you don't know what I'm talking about, you'll be ok.

+1. Hardy is getting better and better by the day. huge amount of updates streaming down on a daily basis and overall its Fast and stable.

---

### Post by dwilson08 on 2008-04-24
Alright well not that Hardy is officially out I thought I'd give Linux another try. I ran sudo apt-get upgrade and update, while my system appears to be fully updated my problems persists. So if theres anyone out there that knows how to change from a Hardy development branch to just plain ol' gutsy your input would be appreciated. Otherwise I'm just gonna have to wipe it all and install from a cd. (one of my current problems is that i can't access any kind of file manager... when ever I open a folder it quickly closes itself)

I just ran upgrade and this came up at the end:
```
Fetched 6747B in 4m35s (24B/s)
Failed to fetch http://download.tuxfamily.org/syzygy42/dists/gutsy/avant-window-navigator/binary-amd64/Packages.gz 404 Not Found
Failed to fetch http://download.tuxfamily.org/syzygy42/dists/gutsy/avant-window-navigator/source/Sources.gz 404 Not Found
Reading package lists... Done
E: Some index files failed to download, they have been ignored, or old ones used instead.
```

I've had a problem with AWN for a while with updating and Just recently uninstalled it... so I'm not sure what I can do...

edit: It appears that file from the tux family website doesnt exists, there's only a feisty version. Hmm

---

