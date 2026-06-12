---
title: "Help, im about to install ubuntu"
date: 2008-03-11
forum: Absolute Beginner Talk
---

### Post by Toolpeth on 2008-03-11
ok, basically i've decided to install ubuntu using dual boot alongside xp coz i wanna taste test first. 
just need to know when the partition option comes up in the installation process will that have a "create partition" option? or will i have to have partitions ready?
thx.
Also before i install i only have 192mb of ram, not the 256 they say it requires. Will this make it impossible/horrible coz i would like to watch videos on my voodoo3, (yes, i know) XP is a **** head with this.
It was awsome on 98, but you guys already know how much of a cunt bill gates is.

---

### Post by shedokan on 2008-03-11
first of all I'm glad your'e trying ubuntu.
:popcorn:
now for your questions, ubuntu installation has a couple of options involving partitions:
you can choose for it to auto create the partitions or you can manually create them with the installation wizard.

and sorry I don't know how will it work with 192mb of ram...

---

### Post by firestormx37 on 2008-03-11
With 192 MB of memory, you may want to consider trying Xubuntu instead.

As far as partitions, the installation will give you the option to resize an existing partition.  However, you should back up any important data from window in case something goes wrong.  The other option is to plan out before you start and have the partitions ready.  You can do this with GParted on the live cd or through the manual option during installation.  Again make sure you backup important files before doing anything with partitions.  If you are not familiar with the partitions that you will need, then I recommend using the automated option.

---

### Post by meindian523 on 2008-03-11
But the completely automatic would just format your entire disk.Use the Guided Partitioning option.

---

### Post by Arkenzor on 2008-03-11
I second choosing using [Xubuntu](http://www.xubuntu.org/), it's an Ubuntu "flavor" using the Xfce Desktop Environment, which is much lighter than Ubuntu's default Gnome environment.

(Just to make things clear, Ubuntu, Kubuntu and Xubuntu are basically the same OS. They simply come with different preinstalled programs)


According to the Xubuntu website you precisely need 192 minimum RAM for the installation (the installation only, day-to-day use is lighter and you can use a swap partition). So you should barely make it, but in case it doesn't work try using the Alternate CD instead. It allows you to install Xubuntu through the command-line and therefore needs much less resources, though it may be a bit harder to use.

---

### Post by firestormx37 on 2008-03-11
Yes, I'm sorry if the wording was confusing. When I said use the automatic option, I meant using the Guided Partitioning that resizes an existing partion, as opposed to using the manual option.  Thanks meindian523 for catching that.

---

### Post by meindian523 on 2008-03-11
[http://psychocats.net/ubuntu/installing](http://psychocats.net/ubuntu/installing)


That tutorial should help.

@firestorm

I thought you might have made precisely that kind of mistake too,I've never seen anybody recommending the complete format and install option.:)

---

### Post by sandysandy on 2008-03-11
here are some links to dual booting:-

[http://users.bigpond.net.au/hermanzone/](http://users.bigpond.net.au/hermanzone/)

[http://apcmag.com/5459/dualboot_ubuntu_and_windows_xp](http://apcmag.com/5459/dualboot_ubuntu_and_windows_xp)

it may be better to have partitions ready. 

if partitions are not ready be careful when using guided option (during installation) in which u can shrink existing windows partition. BACK UP data and de-fragment ur windows drive before starting.

regards

---

### Post by aysiu on 2008-03-11
With only 192 MB of RAM, you should definitely use the Alternate CD, in which case the Psychocats tutorial is not going to work for you. You should use this instead:
[http://users.bigpond.net.au/hermanzone](http://users.bigpond.net.au/hermanzone)

---

### Post by meindian523 on 2008-03-11
aysiu:

Will he need the Alternate CD even if he's using Xubuntu?

---

### Post by Sokraates on 2008-03-11
Welcome to Linuxland.

Like the previous writers I would urge you to try Xubuntu instead of another *buntu variant. 192MB will guarantee a frustratingly slow desktop experience (OpenOffice alone will kill your poor machine).

Before partitioning I would advise you to first defragment you Windows drive(s) to make more room, if necessary. Before all this I would recommend to back up all your valuable data. Just in case. How many GB does your harddrive have, if I may ask?

The partitioner on the live CD will then easily allow you to create all the necessary partitions. You can resize the Windows partition and if I recall correctly there is even an option to use all the free space on the disk. 

Regarding your video card, it should suffice for basic video playing. My parants have an old Riva TNT2 which also works splendidly.

Good luck and have fun.

---

### Post by aysiu on 2008-03-11
> **meindian523 said:**
> aysiu:

Will he need the Alternate CD even if he's using Xubuntu?
Yes, since the combination of the live session *and* the Ubiquity installer will be too much for 192 MB of RAM to handle. I've even seen cases where it's too much for 256 MB to handle. To be on the same side, the Alternate CD is the way to go.

---

### Post by meindian523 on 2008-03-11
> **aysiu said:**
> Yes, since the combination of the live session *and* the Ubiquity installer will be too much for 192 MB of RAM to handle. I've even seen cases where it's too much for 256 MB to handle. To be on the same side, the Alternate CD is the way to go.

Hmmm,thanks for that info.

---

### Post by Het Irv on 2008-03-11
Would that also be true with 8.04 since there is an option to install directly?

---

### Post by aysiu on 2008-03-11
> **Het Irv said:**
> Would that also be true with 8.04 since there is an option to install directly?
I don't know, but 8.04 hasn't yet been released, and I wouldn't encourage a new user to start with an alpha version of Ubuntu.

---

### Post by sandysandy on 2008-03-11
> **Het Irv said:**
> Would that also be true with 8.04 since there is an option to install directly?

what does í[COLOR="Blue"]nstall directly[/COLOR]' mean. does it mean u can install directly from the web.

thanks

---

### Post by aysiu on 2008-03-11
> **sandysandy said:**
> what does í[COLOR="Blue"]nstall directly[/COLOR]' mean. does it mean u can install directly from the web.

thanks
It means you don't have to run the live session *and* the installer at the same time--you can run only the installer.

I believe what you're talking about is a netinstall, something close to which can be achieved if you start with a barebones installation and then fetch the rest of the software packages off the internet.

---

### Post by vikasmk on 2008-03-11
with only 192 MB of ram you better try xubuntu that too with an alternate installer.
 all the best ..........

---

### Post by Het Irv on 2008-03-11
> **aysiu said:**
> I don't know, but 8.04 hasn't yet been released, and I wouldn't encourage a new user to start with an alpha version of Ubuntu.

No, I wasn't recommending that (sorry should have been more clear).  That was a question I had that was partially on topic.  I am trying it now in VirtualBox w/192mb.

---

### Post by Arkenzor on 2008-03-11
What about we stop the information flood while the OP still has a chance of finding what he/she was looking for? :p

---

### Post by twright on 2008-03-11
maybe even try flubuntu, it's even lighter :)

alternative install will probably be required but if you just run wubi.exe from the cd that is fast and easy

---

