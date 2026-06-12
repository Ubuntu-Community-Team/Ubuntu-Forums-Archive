---
title: "Help me understand repositories"
date: 2007-07-08
forum: Absolute Beginner Talk
---

### Post by Protagonistics on 2007-07-08
I recently switched from feisty to dapper for stability reasons. I want all my packages from feisty on dapper-- they're all Linux so what distro I have shouldn't matter, right? That's big question #1 for me.

#2 is this: I know how to add repos. or at least I thought I did. when I "sudo gedit sources.list" in the terminal (mini question: That IS the correct terminal command, right? I AM editing the right sources.list file- there aren't more than one on my computer, right?), I get the repo sources file which I edit, adding repositories to from Trevino/Tr3vino's repo list for Dapper. I used his list for Feisty and I found many a package recommended to me on the forums. Why then, aren't some of the most basic packages not available when I look for them in Synaptic? Is Synaptic running off of a different repo source list than the Terminal? I would think not since Synaptic is just the frontend for apt-get... right?

#3 Maybe I just don't know what I am doing, but I would have thought such packages such as Songbird, k3b, DeVeDe, libc6, and automatix would have been released for Dapper (which kind of relates to question #1. If they weren't, then there must be substitutes. If they were, then I'm doing something wrong.) I'm getting awfully frustrated.


Thanks

---

### Post by eternalsword on 2007-07-08
feisty should be no less stable than dapper, so I'm not sure why you want to downgrade.  That said, to downgrade your system entirely will be very very difficult, especially if you have customized software on feisty that is not available in the dapper repositories.  To see an example of someone downgrading from edgy to dapper, you can read [http://ubuntuforums.org/showthread.php?p=1243014](http://ubuntuforums.org/showthread.php?p=1243014)  From feisty to dapper is a further jump than edgy to dapper, so problems may abound and your system may become unusable.

The way apt/dpkg is designed (basically any debian based system), upgrading is very easy, but downgrading is cumbersome.  

Some programs are only in repositories for newer ubuntu releases, though you are free to compile from source on older releases.

There is only one sources.list and synaptic uses the same listing, so if it's been updated in the terminal it will also be updated for synaptic.

Hope this helps.

(Or did you mean you reinstalled completely using dapper?  That would be the best way to downgrade.)

---

### Post by LuisAugusto on 2007-07-08
#2
You understood the concept, your new sources.list is not working because: 
What you didn't understand is the command, because it's not one, they are 2 commands there:

sudo: gives you super user privileges
gedit: text editor
-sources.list is wrong-
/etc/apt/sources.list which is the location of the file you want to edit.

#3

Yes, you are right, you understood it quite well, but probably dapper packages are out of date at side of feisty packages.

Hope this help.

---

