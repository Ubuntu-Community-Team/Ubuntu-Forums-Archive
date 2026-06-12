---
title: "Dapper &gt; Feisty upgrade question"
date: 2007-05-17
forum: Absolute Beginner Talk
---

### Post by topsites on 2007-05-17
Ok, I am hearing I should upgrade to Feisty...

Is there a way to do this without losing all my stuff?

---

### Post by tawniteamo on 2007-05-17
you could but it would involve upgrading to 6.10 via the alternate install cd (not desktop cd) then doing either the same with 7.04 or doing an upgrade using the update manager :) anyone correct me if I'm wrong (I'm new to this lol)

---

### Post by HereInOz on 2007-05-17
You will probably need to upgrade to Edgy first, then on to Feisty from there, unless there is a way to go direct.  There could be but I don't know of it.

To get up to Edgy first, open a terminal in Dapper and enter:
gksu "update-manager -c"
and then your password.

That will tell Dapper to seek out an upgrade, and it will, of course, find Edgy.  Run that upgrade and then you can go to Feisty from there.

On the other hand, if your /home directory is in a separate partition from the root directory, then you are able, with some care and attention, to re-format the root partition, install the software afresh, and then you will have a lovely new system which will pick up on the /home directory data and configuration.  You will need to install any non-standard software again. 

You have to be careful in the partitioning section of the install, though, to select manual partitioning and get your partitions right, or all will be lost. 

Either way, if you don't do a backup of your data before you commit, you are dicing with disaster.

---

### Post by mikewhatever on 2007-05-17
> Ok, I am hearing I should upgrade to Feisty...
That's not true. Dapper Drake is a long term release supported until the summer of 2009. I also heard it is rock solid, so if you have it working fine and configured to your liking, do reconsider upgrading.

---

### Post by shearn89 on 2007-05-17
are there any major differences between Dapper and Feisty? apart from stability issues, the odd bug fix, etc..? Does it look totally new? I'm running dapper on an old laptop, and its working fine, so i'm thinking hard about upgrading.

---

### Post by mikewhatever on 2007-05-17
I've never used Dapper, in fact started with Ubuntu from Edgy, so can't really compare. You can look at the screen shots here [http://www.thecodingstudio.com/opensource/linux/screenshots/index.php?linux_distribution_sm=Ubuntu%207.04](http://www.thecodingstudio.com/opensource/linux/screenshots/index.php?linux_distribution_sm=Ubuntu%207.04)
It still uses gnome for its desktop, Firefox for its web browser, Totem & Rythmbox, Open Office and so on. Feisty is also quite stable, and works very well in my case. I am not saying you should not upgrade, but rater that you do not have to. However if you decide to, backup everything you do not want to loose and check out here [https://help.ubuntu.com/community/UpgradeNotes](https://help.ubuntu.com/community/UpgradeNotes)

---

### Post by IainT on 2007-05-17
Have you got a separate home partition?

---

### Post by shearn89 on 2007-05-17
no, but my laptop is only really used for a bit of school work, which i can back up onto a ram pen or something...

---

### Post by topsites on 2007-05-17
gksu "update-manager -c"

works

---

### Post by louieb on 2007-05-17
For what its worth. I have Feisty and Dapper on my desktop. Because of stability problems I quite using Feisty.  Feisty has newer versions of some software, seems a little faster and x locks up every now and then. When Gutsy goes beta Feisty will be replace but for now I'm staying with Dapper. The  only reason I use Feisty on the Laptop is wireless worked out of the box and I'm to lazy to setup wireless in Dapper.

---

### Post by shearn89 on 2007-05-17
given that my laptop doesn't hold anything crucial and i can easily get back to how it was setup, i think i'll take the plunge and upgrade - if only because it'll give me the chance to learn more about ubuntu!

---

