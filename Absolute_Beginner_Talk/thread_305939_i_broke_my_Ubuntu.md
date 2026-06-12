---
title: "i broke my Ubuntu"
date: 2006-11-24
forum: Absolute Beginner Talk
---

### Post by wallacek on 2006-11-24
OK. I think I really screwed it up, and the problem is I was doing (as usual, you'd think I'd have learned by now) 2 or 3 things at once. Trying to update Firefox using that nice shell script. Trying to download and burn Gparted. mounting my windows partition so I could see those files.  (I am really new at this.) 
Ok. so now, nothing in the 'administration' works. it all says "error" in a little blue box in the middle of the screen but won't tell me what KIND of error. firefox won't open. terminal won't open. something else tells me I don't have permission to write to this filesystem. In restarting, i noticed that several things failed that don't usually fail- didn't note all of them, but one was unmounting drives.
what did I do? any ideas? Is it totally FUBAR?  :-? 
thanks. <sigh>
karinne

---

### Post by dogon on 2006-11-24
Very little information here.

But ehm, how is the diskspace on your drives?

What you did should not kill anything. But it could fill up the drives. Linux gets very very flakey when the drives are full, random errors completely unrelated to what you were doing.

It drove me mad in the past, I even reinstalled systems that on second thoughts just needed some breathing space.

---

### Post by rlozano on 2006-11-24
maybe you can try sudo aptitude install -f, to remove unfinished installation then follow it by sudo aptitude update.

it may help you, but no guarantee. 

but if you still noticed things failed at startup, then i suggest to make a clean install again. if you have important data already, you may want to back it up first.

---

### Post by wallacek on 2006-11-24
It's definitely screwed up. I rebooted, got ALL kinds of failure notices, multiply defined blocks, inode #xxxx = 1, when should =2...like 25,000 different errors. OK. Luckily, I had very little data on the Ubuntu partition of the hdd. XP is still fine, defragged this sector again, no problems.  So I am going to do a fresh install.  I could use a walk-through. The only things I did that could have screwed things up were using PartitionMagic (Norton) from XP partition to try to resize both NTFS and ext3 partition, which gave me errors even before I knew I had problems in my ubuntu (which was working fine before.) Errors had to do with some errors in my ext2 filesystem (which I don't have, I have NTFS, logical (Linux swap), and ext3.  
So- to do a fresh install, Just reinstall the ubuntu liveCD? I am assuming it will know that there is already an install in place, etc. 
I am going to Google and thread search now for re-install ubuntu issues, but if there are any heads-up, it would be nice to hear about them.
Thanks for your help. 
karinne

---

### Post by rlozano on 2006-11-24
> So- to do a fresh install, Just reinstall the ubuntu liveCD? I am assuming it will know that there is already an install in place, etc.
I am going to Google and thread search now for re-install ubuntu issues, but if there are any heads-up, it would be nice to hear about them.
Thanks for your help.
karinne

yes. and please read this nice guide from aysiu before proceeding with your re-installation.

[http://www.psychocats.net/ubuntu/index](http://www.psychocats.net/ubuntu/index)

hope this helps...

---

