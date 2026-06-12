---
title: "I want to download the non-live cd edtion"
date: 2006-11-04
forum: Absolute Beginner Talk
---

### Post by tbluhp on 2006-11-04
I need the ppc version of the install cd not the live cd.

---

### Post by Ecthelion on 2006-11-04
Does that exist? Except for Xubuntu then?

Why not just installing with the live cd?

---

### Post by Narzuhl on 2006-11-04
Is there not an alternitive CD version? I think i saw it on the Ubuntu downloads page.

---

### Post by tbluhp on 2006-11-04
I tryed but it did not partion my external or my internal drive correctly I chose the option to have it use the lot of freespace but when installing it said I had no boot strip or something.

---

### Post by Ecthelion on 2006-11-04
> no boot strip or something.

Not really clear...

Did you try to install again doing the partition manually?

If you need help with that, just tell us how your disk is and how you want it to be... :-)

Or post a screen shot....

---

### Post by tbluhp on 2006-11-04
> **Ecthelion said:**
> Not really clear...

Did you try to install again doing the partition manually?

If you need help with that, just tell us how your disk is and how you want it to be... :-)

Or post a screen shot....
ah thank you

My hd is firewire and my computer has mac os x and want to duelboot it. Eaither install it on external or internal.

My exteranal already has 2 partions that are for my mac.

the error read no /boot or something I cannot remember it was last night.

Please help me try to figure all this out.

I did post ealryer in the apple part of these fourms but no luck :( "crying"

---

### Post by Ecthelion on 2006-11-04
I've no experience with installing Ubuntu on an external harddrive...

If you want I can try to help you installing it on your internal hdd...

How much space do you have on your internal hdd?
And how much of free space?

> the error read no /boot or something I cannot remember it was last night

Makes me think this is a grub install problem...

Did you checked the integrity of your cd?
I've heard that can cause problems too...
the cd's have to be burned very slowly and checked for theit integrity...

---

### Post by tbluhp on 2006-11-04
> **Ecthelion said:**
> I've no experience with installing Ubuntu on an external harddrive...

If you want I can try to help you installing it on your internal hdd...

How much space do you have on your internal hdd?
And how much of free space?



Makes me think this is a grub install problem...

Did you checked the integrity of your cd?
I've heard that can cause problems too...
the cd's have to be burned very slowly and checked for theit integrity...
40GB on internal and about 18GB free

I am downloading the alternative cd like someone told me.

---

### Post by Ecthelion on 2006-11-04
If your downloading the alternate version of Ubuntu, maybe you should also look at [this]("http://users.bigpond.net.au/hermanzone/") page...


From the website:
> This website is about how to use the Ubuntu 'Dapper Drake' Alternate' Install CD, and it is in the process of being updated for 'Edgy Eft'. 

EDIT:

LOL didn't readed the last part of the phrase... still I guess that an alternate install of edgy, since it's not graphical, might look a bit like that of dapper... So you might find interesting stuff after all...

---

### Post by tbluhp on 2006-11-04
> **Ecthelion said:**
> If your downloading the alternate version of Ubuntu, maybe you should also look at [this]("http://users.bigpond.net.au/hermanzone/") page...


From the website:


EDIT:

LOL didn't readed the last part of the phrase... still I guess that an alternate install of edgy, since it's not graphical, might look a bit like that of dapper... So you might find interesting stuff after all...
hmm this seems hard. But I give it one try if nothing then I guss ubuntu for me is only useable on live cd.

---

### Post by Ecthelion on 2006-11-04
from what I know the alternate cd only uses the good 'old throughoutly tested Ubuntu installer, unlike the live installer which is a shiny Edgy thing...

So it shouldn't be hard at all...

---

### Post by tbluhp on 2006-11-04
ok, but what are the partions I need to make before i can install it?

---

### Post by Ecthelion on 2006-11-04
Well You need a root partition: that's the one with mount point /
A swap partition is also needed.

If you want, you can also create a /home partition.
That's where all your personal stuff gets in... if you have any trouble and have to reinstall, you don't loose any setting etc if you have that kind of partition.

So basically:

/          ->    ext3         -> more or less 5Gb (if you have an /home partition, otherwise as big as you want for all your linux stuff...)

/home      ->    ext3         -> as big as you want for all your personal linux stuff
swap       ->    linux swap

And, optional, you can make a fat32 partition where you can write files on from linux and from any other OS...
If you don't want a fat32 you can also install drivers on that other os that makes it possible towrite to ext3


EDIT: there's a rule about linux-swap... but i'm not sure... did it had to be twice your ram or half or your ram (the size)
Anyone who knows?

---

### Post by tbluhp on 2006-11-04
> **Ecthelion said:**
> Well You need a root partition: that's the one with mount point /
A swap partition is also needed.

If you want, you can also create a /home partition.
That's where all your personal stuff gets in... if you have any trouble and have to reinstall, you don't loose any setting etc if you have that kind of partition.

So basically:

/          ->    ext3         -> more or less 5Gb (if you have an /home partition, otherwise as big as you want for all your linux stuff...)

/home      ->    ext3         -> as big as you want for all your personal linux stuff
swap       ->    linux swap

And, optional, you can make a fat32 partition where you can write files on from linux and from any other OS...
If you don't want a fat32 you can also install drivers on that other os that makes it possible towrite to ext3


EDIT: there's a rule about linux-swap... but i'm not sure... did it had to be twice your ram or half or your ram (the size)
Anyone who knows?
what is the ext3?

When I make all these partitions were do I need to have them as my mount point?

Did you find out about linux swamp?

Also I use a mac so I already have one partion from the mac install.

---

### Post by Ecthelion on 2006-11-04
[Quote=tbluhp]
I dont get this
So basically:

/ -> ext3 -> more or less 5Gb (if you have an /home partition, otherwise as big as you want for all your linux stuff...)

/home -> ext3 -> as big as you want for all your personal linux stuff
swap -> linux swap

And, optional, you can make a fat32 partition where you can write files on from linux and from any other OS...
If you don't want a fat32 you can also install drivers on that other os that makes it possible towrite to ext3[/QUOTE]

Well.

You need a root partition: /
That is the partition where your system gets installed too. Al your system files & programs can be found on that partition. If you don't make a separated /home partition, then your home dir wil also be part of your root partition.
So if you have a serious problem and you have to reinstall, then you lose everything on your /
If your home is on it, then you lose it too.
That's why I recommend making a separated /home partion.

When you make that separated home partition, you just have to do the same as for your root partition, except that it has /home as mount point instead of just / (which is the mount point of the root partition)

So you need a / and a /home partition.
You also need a swap.

If you have 20Gb free for linux, then I would do this:
5 Gb for your / (your system files won't grow that large except if you install really a lot of stuff)
14.5 Gb for your /home
(The place where all your preferences for your programs is saved and where you can put all your other stuff: Movies, Music, etc)
And, 500Mb of swap.

You can make a bigger swap if you want, but don't make it bigger then 1Gb... It would be useless.

Does this helps?

---

### Post by tbluhp on 2006-11-04
thanks for the help I will try it out and tell you the results.

---

### Post by Ecthelion on 2006-11-04
> what is the ext3?

ext3 Is the format which is usual for linux to install too...
A bit like that NTFS is the format on which windows installs.

> When I make all these partitions were do I need to have them as my mount point?

root -> /
home -> /home
I don't remember swap having a mount point...

> Did you find out about linux swamp?

As I said, I would put it between 500Mb and 1G... depending on how much ram you have

> Also I use a mac so I already have one partion from the mac install.

That shouldn't be a problem...
Except that you'll have to resize that partition if it's taking the whole disk.
The ubuntu installer uses Gparted and can handle that.

---

### Post by tbluhp on 2006-11-04
so when makeing the partions do I make them all ext3? Also I did notice from the live cd that you can only make partions for up2 128mb?

---

### Post by tbluhp on 2006-11-04
I have 1GB of ram

---

### Post by Ecthelion on 2006-11-04
>  	so when makeing the partions do I make them all ext3?

Your /home and / are ext3
the swap it linux swap (that's also a format)

>  Also I did notice from the live cd that you can only make partions for up2 128mb?

Never heard of that... my /home is 126 Gb... So you'll have made a mistake somewhere...

> I have 1GB of ram

Well I would say 700Mb of swap will be more than enough

---

### Post by tbluhp on 2006-11-04
thanks I really appricate all the work you have given me :)

So it cannot be installed on external drive?

Also I makeing my / 3gb and /home 7gb to save room so i can install more mac stuff.

---

### Post by tbluhp on 2006-11-04
> **Ecthelion said:**
> Does that exist? Except for Xubuntu then?

Why not just installing with the live cd?

given all this info should I re-try installing from linux live cd and not the alternative.

---

### Post by Ecthelion on 2006-11-04
> So it cannot be installed on external drive?

I haven't said that...

I said that i didn't knew how to do that and that I couldn't help for an install on an external disk.

There sure are ways to do that, but you'll have to look around for it yourself.

:) 

Happy to help

---

### Post by tbluhp on 2006-11-04
What about my other post about the linux live cd?

---

### Post by Ecthelion on 2006-11-04
> given all this info should I re-try installing from linux live cd and not the alternative.
> What about my other post about the linux live cd?

You can try...

---

### Post by tbluhp on 2006-11-04
Ah it seemed to hard going to try the live cd one more time cause the text version is way hard.

---

