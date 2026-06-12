---
title: "How do I access my FAT32 partition"
date: 2007-06-15
forum: Absolute Beginner Talk
---

### Post by ~sparkles~ on 2007-06-15
Hi there,

I'm having a lot of trouble working out how to mount my FAT32 partition in Kubuntu. I need help with a guide or directions etc.

Here is my set up.
sudo fdisk -l
```
   8        1154     9213277+   7  HPFS/NTFS
/dev/sda3            1155        7792    53319735    f  W95 Ext'd (LBA)
/dev/sda4            7793        9729    15558952+  83  Linux
/dev/sda5            1155        7701    52588746    b  W95 FAT32
/dev/sda6            7702        7792      730926   82  Linux swap / Solaris

```

:)

---

### Post by orb9220 on 2007-06-15
Post your fstab

open terminal and: **gedit /etc/ftab** copy and paste back here.

---

### Post by ~sparkles~ on 2007-06-18
```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda4
UUID=9f186a36-e890-4979-89bf-06c40697af70 /               ext3    defaults,erro$
# /dev/sda6
UUID=85933306-9b4c-43c1-a17d-70cf3f149068 none            swap    sw           $
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto     0       0
```

---

### Post by bodhi.zazen on 2007-06-18
This is the classic link : [http://www.psychocats.net/ubuntu/mountwindows](http://www.psychocats.net/ubuntu/mountwindows)

---

### Post by swoll1980 on 2007-06-18
Did you try offering it some food?:D

---

### Post by ~sparkles~ on 2007-06-18
> **bodhi.zazen said:**
> This is the classic link : [http://www.psychocats.net/ubuntu/mountwindows](http://www.psychocats.net/ubuntu/mountwindows)

I've already been there... couldn't get things to work... I've spent 3 days searching guides etc but there hasn't been anything that works... am I missing something obvious?

---

### Post by bodhi.zazen on 2007-06-18
LOL

You can mount it with :

```
mkdir /media/fat
sudo mount /dev/sda5 /media/fat -o umask=000
```

And if you like, add this to fstab :

> /dev/sda5 /media/fat vfat auto,users,umask=000  0  0

[list][*]You can use any mount point you like such as /media/share or /media/windows or /media/music or ...[/list]

---

### Post by gn2 on 2007-06-18
> **~sparkles~ said:**
>  am I missing something obvious?

Possibly. There's a utility available through Automatix which will automatically mount and make Fat32 and NTFS partitions writeable.

It's listed in the "Miscellaneous" category in Automatix, once you've got that installed.

Lots of other good stuff can be added with Automatix as well.

[www.getautomatix.com](www.getautomatix.com)

Doubtless someone will be posting soon giving dire warnings of how bad Automatix is, and how it's unsupported, not part of Ubuntu blah, blah, blah.

You can safely ignore such BS.

---

### Post by bodhi.zazen on 2007-06-18
> **gn2 said:**
> Possibly. There's a utility available through Automatix which will automatically mount and make Fat32 and NTFS partitions writeable.

It's listed in the "Miscellaneous" category in Automatix, once you've got that installed.

Lots of other good stuff can be added with Automatix as well.

[www.getautomatix.com](www.getautomatix.com)

Doubtless someone will be posting soon giving dire warnings of how bad Automatix is, and how it's unsupported, not part of Ubuntu blah, blah, blah.

You can safely ignore such BS.

LOL

The utility you are talking about is called "ntfs-config"

You do not need automatix to install it:

[Ntfs-config](http://doc.gwos.org/index.php/Ntfs-config)

_Note_: And yes, it is true what you say about automatix. It is an official part of Ubuntu and is is not supported on these forums, they have their own forums if you would like. If it breaks your system, well you have been warned ...

---

### Post by gn2 on 2007-06-18
> **bodhi.zazen said:**
> LOL

The utility you are talking about is called "ntfs-config"

You do not need automatix to install it:

[Ntfs-config](http://doc.gwos.org/index.php/Ntfs-config)

_Note_: And yes, it is true what you say about automatix. It is an official part of Ubuntu and is is not supported on these forums, they have their own forums if you would like. If it breaks your system, well you have been warned ...

I have checked my markings in Synaptic. Interestingly, "ntfs-config" isn't installed, but "ntfs-3g" and "libntfs-3g0" are.

My intention in pointing the OP to Automatix was that he was struggling with the more traditional methods to get a Fat32 partition mounted.

Using the Automatix tool achieves this without ever having to stare a terminal in the face.
You don't even have to use a terminal to install Automatix these days. Ahhh progress.

Point-and-click does the trick! :-)

---

### Post by ~sparkles~ on 2007-06-18
Yay! I was missing something obvious... use CAPITAL Y to save fstab.

Nonetheless I didn't have the commands sorted as nicely as you peeps advised.

Your advice has been brilliant. Mwah! :)

Thank you:D

---

### Post by bodhi.zazen on 2007-06-18
> **gn2 said:**
> I have checked my markings in Synaptic. Interestingly, "ntfs-config" isn't installed, but "ntfs-3g" and "libntfs-3g0" are.

My intention in pointing the OP to Automatix was that he was struggling with the more traditional methods to get a Fat32 partition mounted.

Using the Automatix tool achieves this without ever having to stare a terminal in the face.
You don't even have to use a terminal to install Automatix these days. Ahhh progress.

Point-and-click does the trick! :-)

So we meet again ....

Good to see you gn2, I am pleased to see you are still trying to help. I love your insights as you come from a different background as I and it is always nice to see there is a third way to skin a cat.

When you are guiding new users, please consider this.

1. It is always best to stay with the official repositories whenever you can for obvious reasons. Yes there are problems with this I know ...

2. When advising the use of third party projects :[list][*]Know and advise the risks (security, system breakage, upgrading, etc). None of these issues are unique to automatix.[*]So if you advise automatix, best guide the user to thier forums. That is where they will get the best and most up to date support.[*]You will go against the grain less if you advise the "Ubuntu way". There are plenty of awesome 3rd party projects, like Mint, Mepis, automatix, etc. BUT they are they are exactly that, 3rd party.
[*]So if you do advise automatix :[list][*]Know and advise the risks.[*]Know that system breakage *HAS* occurred with automatix, partially because automatix is a large and complex system.[*]Ask yourself how you would feel if my advice broke your system, ? A friendly warning is best.[/list][/list]

As an example : There was a time when upgrading X caused general system breakage (it happens, and if I recall you were here then). The Ubuntu forums was a source of information and resolution of the issue.

So, when (I use when rather then if because, like X with Ubuntu it is going to happen from time to time with something as complex as automatix) then, like the ubuntu forums , the automatic forums are the best source of information. Obviously this gets the information back to the automatix maintainers and a fix from the automatic maintainers back to the automatix users quickly and efficiently.

So what is the point of all this ranting ? If you like automatix and would like to advise it, no problem. Obviously there are many users who enjoy automatix. Just understand the complexity and risks of 3rd party projects. Like any OS, windows for example, 3rd party software is often not supported (try calling Microsoft for support of your favorite non-microsoft game for example). Similar situation with Ubuntnu/automatix.

BUT, as you know, there are enough flame wars with ubuntu/automatix so lets not feed the flames, that is counter productive to both ubuntu and automatix.

---

### Post by gn2 on 2007-06-18
> **bodhi.zazen said:**
> there are enough flame wars with ubuntu/automatix so lets not feed the flames, that is counter productive to both ubuntu and automatix.

Must have missed that, I've been away for a bit.....

You're quite right about warning of the potential dangers of using Automatix.

Where I live generally we experience fewer dire warnings on things  as our society is much less litigious.

You still prefer Grapes>Merlot to Apples or Oranges?

---

### Post by drowner on 2007-06-18
Since Feisty i really see no need for automatix.

FLAME ON!

---

### Post by bodhi.zazen on 2007-06-18
> **drowner said:**
> Since Feisty i really see no need for automatix.

FLAME ON!

+1 Gutsy :twisted:

[list][*]Expect some breakage[/list]

-1 Flames :(

Please just advise on the proper way to maintain a system without the flames.

---

