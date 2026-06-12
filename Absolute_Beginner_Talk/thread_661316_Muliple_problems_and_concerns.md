---
title: "Muliple problems and concerns"
date: 2008-01-07
forum: Absolute Beginner Talk
---

### Post by Ramrod_The_Wizard on 2008-01-07
With gutsy now being the standard for the ubuntu community I decided that I should update from fiesty, but I'm worried about corruption or loss of data.   The quickguide says to backup my files, but I don't have ready access to an external hard drive.  Normally I wouldn't be concerned, but I have recently gotten quite a large amount of movies and videos and I want to avoid losing them at all costs.  What should I do to keep up to date but still ensure my files are fine? Or is it not worth upgrading due to the circumstances?

My second problem is fairly minor.  I've been using Deluge Bittorent client for the past few weeks after becoming annoyed with the excess resource usage of Azureus, but today it hasn't been opening properly.  After rebooting the problem persists and I'm not really knowledgeable to diagnose the problem effectively.  Is this a common error and how should I fix it?  If this problem persists, are there any good alternatives (not including utorrent via wine) or should I return to Azureus?

I'll be back in about an hour, gotta go on a bike ride.
Thanks in advance :)

---

### Post by bodhi.zazen on 2008-01-07
For your data problem, either make a separate /home or a /data partition.

[http://ubuntu.wordpress.com/2006/01/29/move-home-to-its-own-partition/](http://ubuntu.wordpress.com/2006/01/29/move-home-to-its-own-partition/)

That way when you upgrade or install , just do not format your /home or /data

========

For deluge, launch it from a terminal and see if there is an error message.

As an alternate, look at rtorrent :

[http://kmandla.wordpress.com/2007/05/02/howto-use-rtorrent-like-a-pro/](http://kmandla.wordpress.com/2007/05/02/howto-use-rtorrent-like-a-pro/)

---

### Post by RomeReactor on 2008-01-07
Hi. It's not necessary to upgrade to Gutsy right away; you can do that later, when you're able to backup your files. That's not saying you'll forcibly encounter problems while upgrading, but it's better to be prepared in case it *does* happen--especially if you have a large amount of files and no backups. Feisty will still update regularly, for the time being.

As for Deluge, try running it from a terminal:
```
deluge
```
and please post any error messages you get there.

---

### Post by Ramrod_The_Wizard on 2008-01-07
no existing Deluge session
deluge_core; using libtorrent 0.11.0.0. Compiled with NDEBUG value: 1
Applying preferences
Raising error: 
deluge_core; using libtorrent 0.11.0.0. Compiled with NDEBUG value: 1
terminate called after throwing an instance of 'boost::filesystem::filesystem_error'
  what():  boost::filesystem::default_name_check: default name check already set
Aborted (core dumped)


That's what came up after I tried to open deluge in terminal.  Well, I don't know much about terminal (a problem which needs to be solved) I can see that it is indeed an error in startup, though I don't really understand why.

Thanks for the advice on the upgrading problem.  Depending on how much money I have free I might just pick up a solid external HDD, though nothing huge like a terabyte.

---

### Post by bodhi.zazen on 2008-01-07
See if this thread helps : [http://ubuntuforums.org/showthread.php?t=383420](http://ubuntuforums.org/showthread.php?t=383420)

---

### Post by Faud on 2008-01-07
> **Ramrod_The_Wizard said:**
> 
 Depending on how much money I have free I might just pick up a solid external HDD, though nothing huge like a terabyte.

No need for a seperate HD if you want. You can make your /home its own partition that way if you do an update and it messes other stuff up, the data in your /home is safe beacuse you havent touched that partition.

---

### Post by Ramrod_The_Wizard on 2008-01-07
> **bodhi.zazen said:**
> See if this thread helps : [http://ubuntuforums.org/showthread.php?t=383420](http://ubuntuforums.org/showthread.php?t=383420)

It was a great help, thanks alot!

---

