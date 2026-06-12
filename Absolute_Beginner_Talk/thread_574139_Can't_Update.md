---
title: "Can't Update"
date: 2007-10-12
forum: Absolute Beginner Talk
---

### Post by RichPicker on 2007-10-12
I have kept Update Manager turned OFF, because in the past, some  updates have caused problems with my sound card. I would rather refuse the  updates, instead of asking for help all the time about the sound card.  But now my laptop won't play movies. It needs plugins, etc. It is
 out-of-date.

When I try to run Update Manger, I get this:

-----------------------------------------------------------------------------------------------
A unresolvable problem occurred while initializing the package  information.

Please report this bug against the 'update-manager' package and include
 the following error message:

'E:Dynamic MMap ran out of room, E:Error occurred while processing
 kde4utils (NewVersion1), E:Problem with MergeList
 /var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_feisty-backports_universe_binary-i386_Packages,
 E:The package lists or status file could not be parsed or opened.'
--------------------------------------------------------------------------------------------------

What should I do?
Thank you.

---

### Post by Kingsley on 2007-10-12
You should run an update.

---

### Post by RichPicker on 2007-10-12
In the terminal I enter this;

sudo apt-get update

And I get this:

. . . . 
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) feisty/non-free Sources
Fetched 195B in 3s (64B/s)
Reading package lists... Error!
E: Dynamic MMap ran out of room
E: Error occurred while processing kde4sdk (NewVersion1)
E: Problem with MergeList /var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_feisty-backports_universe_binary-i386_Packages
E: The package lists or status file could not be parsed or opened.
rich@rich-laptop:~$

---

### Post by Ink-Jet on 2007-10-12
Try ```
sudo apt-get upgrade
```

---

### Post by RichPicker on 2007-10-12
It returns the same error message.

---

### Post by RichPicker on 2007-10-12
Bump...

---

### Post by RichPicker on 2007-10-13
I increased the apt-get cache, which allowed me to run sudo apt-get upgrade. But now my sound card is dead again. The sudo /etc/modprobe.d/alsa-base file still contains the needed line of text. 

Anyone else have this problem with the Dell laptop? Any ideas?

I had everything running fine for all summer. But now it's unhappy again.

Help will be appreciated.

I need to get the alsa drivers again after this upgrade? I'll try that.

---

### Post by RichPicker on 2007-10-13
I increased the cache size of apt-get. This allowed me to run sudo apt-get upgrade.
But now my sound card is dead again. The necessary line of text in the modprobe.d/alsa-base file is still there.
Not sure what to do, or what changed? Everything has been running fine for a few months.
I had the update mgr turned off, in an attempt to avoid having to rebuild the system again. 
Any permanent solutions to this constant sound card problem? I don't want to re-install Windows. Can I change the sound card to one that is more compatible with Linux?
It's a Dell Laptop with a Sigmatel STAC90 card.
Thanks.

---

### Post by RichPicker on 2007-10-13
Okay....
I've reloaded all the necessary ALSA files, libs, etc. and the sound works great again ! ! 
I loaded another library that I needed for the movie players, and the movies play great ! ! 

But why did I have to increase the cache size of apt-get.conf?
Is this something that needs to be purged occasionally like a temp directory? Or have I done something wrong with my machine that caused it to need more cache? Have I created a problem by increasing the cache? What is the maximum size? I'm just asking generally if I've screwed up?

And... The movie players have worked for quite a while. Why today did I have to download another library? 

The puzzle endures. :-)

Thanks for your help.

---

