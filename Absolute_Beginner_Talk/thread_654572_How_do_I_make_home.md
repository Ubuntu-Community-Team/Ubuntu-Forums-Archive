---
title: "How do I make /home?"
date: 2007-12-31
forum: Absolute Beginner Talk
---

### Post by zabien1970 on 2007-12-31
I'm about to add xp to my computer so I can use my printer, it's a dell 'lexmark' that's not supported, I've read plenty that one should always backup first but I have no clue how to do this. From what I've read I should've made a home directory and am now wondering if this is possible now?
 I've made alot of changes since my original install and would like to have a backup of them.
 Also, if I can manage to do this how would I go about burning this to cd?

---

### Post by meindian523 on 2007-12-31
[http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome)

Here.

And to backup your packages,in case you haven't been regularly "apt-get cleaning" them(a good thing in this case),you can use APTonCD.(Search Synaptic)

---

### Post by LowSky on 2007-12-31
most of your original setting are in you /home folder as of now. If you want just copy the entire folder to a CD or DVD. Ubuntu repositories does have back up software availble. You could always used gparted to make a new partition, but you cannot do it while logged in. The best solution is to use an Ubuntu LiveCD and use Gparted that way. If your doing a fresh install choose manual format, and creat new partions that way (ie: /home as one partion).

---

### Post by philinux on 2007-12-31
There are two camps on this. One says its easy to back up home and reinstall. The other says having it on its own partition is better.

Anyway. Here's a link to ponder.
[http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome)

I did this and it works for me.

---

### Post by meindian523 on 2007-12-31
> **LowSky said:**
> most of your original setting are in you /home folder as of now. If you want just copy the entire folder to a DVD or DVD.</snip> 
Didn't you mean to say CD or DVD?:) ;-)

Everyone thinks the same thing.:)

---

### Post by cotcot on 2007-12-31
If you have linux installed, should have a /home folder. Maybe you mean a separate home partition ?

For backup you might read [[COLOR="Red"]backup wit TAR command[/COLOR]]("http://www.debianhelp.co.uk/tarbackup.htm") or check out the instructions from our honourable Aysiu [[COLOR="Red"]here[/COLOR]]("http://www.psychocats.net/ubuntu/partimage")
Success !

---

### Post by foolsh on 2007-12-31
most rebranded dells are lexmark 600le series
here is link to the driver for those hope you dont have to install XP
[http://downloads.lexmark.com/cgi-perl/downloads.cgi?ccs=229:1:0:390:0:0&emeaframe=&fileID=1151](http://downloads.lexmark.com/cgi-perl/downloads.cgi?ccs=229:1:0:390:0:0&emeaframe=&fileID=1151)
this work for a freind of mine.

---

### Post by LowSky on 2007-12-31
> **meindian523 said:**
> Didn't you mean to say CD or DVD?:) ;-)

Everyone thinks the same thing.:)

yup thanks i'll fix it

---

### Post by kvonb on 2007-12-31
-

---

### Post by meindian523 on 2007-12-31
Hmm,to restore Grub,you can use this: (From a Ubuntu Live CD)

[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

---

### Post by zabien1970 on 2007-12-31
> **meindian523 said:**
> [http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome)

Here.

And to backup your packages,in case you haven't been regularly "apt-get cleaning" them(a good thing in this case),you can use APTonCD.(Search Synaptic)

 Ok, Since I'm new what does apt-get cleaning' do? About to look for APTonCD.
 Also, I'm currently downloading gparted, since I can't find my live cd at the moment and have read that it's good to have it. I already downloaded it once but right clicking on it gave me no option to burn an iso, am I missing something?

---

### Post by zabien1970 on 2007-12-31
> **kvonb said:**
> erm, "adding" xp to your computer will wipe the entire disk!!

Unless you have already sorted your partitions out (and left a big one at the front of your disk for Windows), and know how to install Windows to a selected partition, be prepared to lose the lot.

The best thing to do is copy everything you don't want to lose onto a CD/DVD/other hard disk/network share first.

Oh and you will have to search for a thread on howto restore grub and keep a copy handy as Windows will overwrite the bootsector and you will not be able to boot into Linux until it is restored!

That's why I'm wondering if I can create a seperate folder/partition of my stuff (not a very technical term lol) and copy it to a cd so I can reinstall later if I wipe everything

---

### Post by meindian523 on 2007-12-31
Oh,well then there's no problem.

From the apt-get man page:

       clean
          clean clears out the local repository of retrieved package files. It
          removes everything but the lock file from /var/cache/apt/archives/
          and /var/cache/apt/archives/partial/. When APT is used as a
          dselect(8) method, clean is run automatically. Those who do not use
          dselect will likely want to run apt-get clean from time to time to
          free up disk space.

---

### Post by meindian523 on 2007-12-31
If you create a separate partition for your stuff,you don't need to back it up to removable media or a network-share,only be sure that you don't wipe the /home partition when you install.
But this applies to a Linux installation,not so sure about XP.....and if you are creating a partition just to backup to removable media,don't need to do that......you can just burn whatever is in your /home/username folder to a CD/DVD/network-share(your option),be sure to enable Hidden files(Ctrl+H) so you can save your settings too..

---

### Post by zabien1970 on 2007-12-31
> **meindian523 said:**
> If you create a separate partition for your stuff,you don't need to back it up to removable media or a network-share,only be sure that you don't wipe the /home partition when you install.
But this applies to a Linux installation,not so sure about XP.....and if you are creating a partition just to backup to removable media,don't need to do that......you can just burn whatever is in your /home/username folder to a CD/DVD/network-share(your option),be sure to enable Hidden files(Ctrl+H) so you can save your settings too..

Ok, This sounds like what I want to do, burn this info to a cd, but not only am I new to ubuntu, I'm new to computers in general and have no clue how to even attempt this

---

### Post by meindian523 on 2007-12-31
Open your /home/username folder,press Ctrl+H to show hidden files.Select All and Copy.

Go to Places>>CD/DVD creator

Paste your files and click Burn.

---

### Post by zabien1970 on 2007-12-31
Sounds simple enough, I'll try it out and post my results in a bit

---

### Post by maljaros on 2008-01-01
> **philinux said:**
> There are two camps on this. One says its easy to back up home and reinstall. The other says having it on its own partition is better.

Anyway. Here's a link to ponder.
[http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome)

I did this and it works for me.

Thanks for the useful link.  I Googled through the hda/sda thing but now have another silly newbie issue. Having three Linux distros on my hard-drive (plus Windows XP but ignore that) how do I check which distro is in what partition?
I suspect that sda2 is SuSe, sda3 is Feisty and sda4 is Gutsy - but how can i be sure?

---

### Post by maljaros on 2008-01-01
One small step forward - the headers in GRUB tell me that Feisty is sda2.  I can probably find the others by checking the GRUB boot file, but surely there is a more direct way?

---

