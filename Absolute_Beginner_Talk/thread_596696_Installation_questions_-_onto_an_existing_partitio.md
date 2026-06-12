---
title: "Installation questions - onto an existing partition"
date: 2007-10-29
forum: Absolute Beginner Talk
---

### Post by h84ll1 on 2007-10-29
Hi there,

Firstly i'm totally new to Ubuntu.
I'm wanting to install ubuntu 7.10 onto a partition i already have on my primary hardrive, to dual boot with windows xp.
Having started going through the installation on the liveCD i got confused at the partitioning section (i went into manual thinking that'd be how to choose the existing partition i wished to use) and decided against it till i know more!! :) hence i'm writing this!
Ok, the partition i want to have ubuntu on is quite large so if i need to break it up then that's fine, but i have read things about having more than 4 partitions making things get complicated! :confused:

I basically need clear instructions of how to install 7.10 on the partition i already have.  Also, what options to choose in the use menu eg file system to use.

On a side note, there was something in the manual view that said 8mb of free space, seems wasteful, can i  incorporate this into the existing partition i wish to use somehow? Or is windows actually using it!? lol.

I hope you can help,
sorry if this seems a little confused, i've read lots of posts on similar questions and i'm still baffled by it!

Thanks in advance for any help and advice! :)

---

### Post by Pumalite on 2007-10-29
These links should provide the answers to most of your questions:
[http://www.psychocats.net/ubuntu/installing](http://www.psychocats.net/ubuntu/installing)
[http://www.psychocats.net/ubuntu/partitioning](http://www.psychocats.net/ubuntu/partitioning)
[http://www.howtoforge.com/dual_boot_windows_xp_vista_ubuntu_feisty_p2?](http://www.howtoforge.com/dual_boot_windows_xp_vista_ubuntu_feisty_p2?)
If you need more help; come back.

---

### Post by mlippert on 2007-10-29
Pumalite, is psychocats.net your site? If so thanks, and I have a quick comment (followed by a request for more help if you can :-)

I followed the instructions on [http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome) to move my home directory to its own partition. The instructions were great but I ran into one small hitch, which made my first attempt not work correctly, namely that while I was running from the Live CD I didn't have permission to view the contents of several of the subdirectories (such as those under .mozilla)
if I modify the command
```
find . -depth -print0 | sudo cpio --null --sparse -pvd /new/
```
to
```
[COLOR="Red"]sudo[/COLOR] find . -depth -print0 | sudo cpio --null --sparse -pvd /new/
```

I successfully copied all the files (at least it seems fine to me now.:) )

This was in preparation for upgrading from Edgy to Gutsy. The thing is I haven't found any instructions which document the best way to do a clean re-install, which I think I have to do. You can see my post at [http://ubuntuforums.org/showpost.php?p=3653959&postcount=339](http://ubuntuforums.org/showpost.php?p=3653959&postcount=339)

Thanks,
Mike

ps sorry for hijacking the thread, I was just looking for a way to contact the owner of the psychocats site.

---

### Post by Pumalite on 2007-10-30
I'm not the owner of the site. I guess you are asking how to save before a clean install. Save /home (including 'Hidden Files') and data. Programs you have installed with apt-get or aptitude can be stored in CD's or DVD's using AptOn. Here are a couple of methods to backup and restore:
[http://users.bigpond.net.au/hermanzone/p13.htm](http://users.bigpond.net.au/hermanzone/p13.htm)
[http://www.psychocats.net/ubuntu/partimage](http://www.psychocats.net/ubuntu/partimage)

---

### Post by mlippert on 2007-10-30
> **Pumalite said:**
> Here are a couple of methods to backup and restore
Thanks, that's a pointer toward what I need, I'll check out those links.

---

### Post by aysiu on 2007-11-01
I don't think the live CD's inability to view /home/*username*/.mozilla is a typical scenario. The live CD user should be able to view the user directories of pretty much any user's folder.

I've used the find command without *sudo* and it's worked just fine. As a matter of fact, the Psychocats separate /home tutorial is really just a rehash of another tutorial. I have no idea how that find command works, only that it does work.

I would not recommend copying the /home directory using *sudo*, as I believe that will make the copied files owned by root. Not 100% sure about that.

---

### Post by mlippert on 2007-11-02
OK, I just wanted to let you know what I experienced in case you wanted to update your page.

I just checked my home directory which I did copy by using sudo on the find as well as on the cpio as above, and the files/directories are still owned by my user.

I'm fairly certain that the original command is already using sudo to copy the files, the sudo I added was only to the find command which lists them for the cpio command to copy.

Anyway, thanks again for your site, I've found (and am still finding) it very helpful as I explore Linux.

---

