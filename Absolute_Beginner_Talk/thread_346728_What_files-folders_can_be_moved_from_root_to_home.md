---
title: "What files-folders can be moved from /root to /home"
date: 2007-01-26
forum: Absolute Beginner Talk
---

### Post by randiroo76073 on 2007-01-26
I'm interested in moving files/folders from /root to /home partition so as to keep my root partition as small as possible for imaging to dvd.  I'm currently running Ubuntu dapper[6.06 LTS] w/ gnome, kde, xfce + desktops.  Its not a matter of hdd space[I've got plenty], it's that my /root keeps growing.  I know, I know, quit installing so much stuff, but I'm having to much fun to do that :)  So what files/folders can be moved w/o causing Ubuntu to go wonky & is there a tutorial that will guide the way?  In 98se I had a prgm that would change all reg entries, but in Ubuntu I don't mind doing CLI cause it's more logical than windoz.
TIAFAI

---

### Post by lamego on 2007-01-26
> keep my root partition as small as possible for imaging to dvd If you have a big /home why just you don't use the /home for that instead ?

---

### Post by hyper_ch on 2007-01-26
well, you could try moving /root to /home/root and then make a symlink that points /root to /home/root... not sure if that works but I don't see why it shouldnt...

e.g.

```

sudo ln -s /home/root /root

```

---

### Post by Bachstelze on 2007-01-26
I think there's a slight confusion here. /root is *not* the root filesystem, it's the home folder of user root and since the root user is never used in Ubuntu, there should be close to nothing in there. The root filesystem is / and if things are kept there, it's for a reason so there's nothing you can move to your home folder that is not already in there.

---

### Post by lamego on 2007-01-26
> The root filesystem is / and if things are kept there, it's for a reason so there's nothing you can move to your home folder that is not already in there.
Actually you can, as long you create the proper symlinks, the fact is, you shouldn't, because you loose your system organization and you may get into troubles later because if forget about that move.

---

### Post by randiroo76073 on 2007-01-28
Thanks for all replies, thats kinda what I was thinking[HymnToLife] but wanted to get some other thoughts before making any moves.

---

### Post by steve.horsley on 2007-01-28
You need to be very careful. When booting, the system first mount the root / partition, and only later on after doing a lot of scripted work does it go to /etc/fstab to find what other partitions to mount. Moving the wrong thing to the /home partiton and symlinking it may well leave the system unable to boot in a chicken-and-egg lockout. Certainly don't move /bin or /etc or /boot.

---

### Post by randiroo76073 on 2007-01-29
Thanks for added info Steve, LOL, after experiencing windows & crashing it big time a bunch I'm cautious about what I move where :)  Better to ask than have to reinstall.

---

### Post by randiroo76073 on 2007-02-02
Well, I did find 1 I could move sucessfully, moved my "mnt" to /home & edited fstab accordingly :)

---

### Post by Tomosaur on 2007-02-02
I don't understand the rationale behind this. You're not saving any space by moving stuff from root  to home, and nothing 'new' should be appearing in the root directory anyway (so long as you're just installing 'normal' stuff). Your root folder (/), should look roughly like this:
```

tom@tom-desktop:/$ ls
bin    dev   initrd          lib         mnt   root  sys  var
boot   etc   initrd.img      lost+found  opt   sbin  tmp  vmlinuz
cdrom  home  initrd.img.old  media       proc  srv   usr  vmlinuz.old

```

If you're finding extra stuff in there, like programs or whatever, then you're doing something wrong.

---

### Post by randiroo76073 on 2007-02-02
Thats what mine looks like minus the mnt, what your not thinking of is I have seperate partitions for / & /home, so yes, I did gain something, / is smaller by .5gb

---

### Post by rccharles on 2007-02-02
> **randiroo76073 said:**
> I'm interested in moving files/folders from /root to /home partition so as to keep my root partition as small as possible for imaging to dvd.  I'm currently running Ubuntu dapper[6.06 LTS] w/ gnome, kde, xfce + desktops.  Its not a matter of hdd space[I've got plenty], it's that my /root keeps growing.  I know, I know, quit installing so much stuff, but I'm having to much fun to do that :)  So what files/folders can be moved w/o causing Ubuntu to go wonky & is there a tutorial that will guide the way?  In 98se I had a prgm that would change all reg entries, but in Ubuntu I don't mind doing CLI cause it's more logical than windoz.
TIAFAI

I believe that /var and /usr are often put in separate partitions.

Perhaps a google search would reveal how the experts partition a large system.

Robert

---

### Post by randiroo76073 on 2007-02-03
Thanks for the tip rccharles, have done google, but couldn't find one that fit me, altho did find some interesting ones :)

---

### Post by rccharles on 2007-02-03
> **randiroo76073 said:**
> I'm interested in moving files/folders from /root to /home partition so as to keep my root partition as small as possible for imaging to dvd.  I'm currently running Ubuntu dapper[6.06 LTS] w/ gnome, kde, xfce + desktops.  Its not a matter of hdd space[I've got plenty], it's that my /root keeps growing.  I know, I know, quit installing so much stuff, but I'm having to much fun to do that :)  So what files/folders can be moved w/o causing Ubuntu to go wonky & is there a tutorial that will guide the way?  In 98se I had a prgm that would change all reg entries, but in Ubuntu I don't mind doing CLI cause it's more logical than windoz.
TIAFAI

I run across this book at Border's book store.  It has a section on backup.  See:

Linux Administration Handbook (2nd Edition) (Paperback)
by Evi Nemeth, Garth Snyder, Trent R. Hein 

[http://www.amazon.com/Linux-Administration-Handbook-2nd-Nemeth/dp/0131480049/sr=8-1/qid=1170543604/ref=sr_1_1/102-5343521-3571365?ie=UTF8&s=books](http://www.amazon.com/Linux-Administration-Handbook-2nd-Nemeth/dp/0131480049/sr=8-1/qid=1170543604/ref=sr_1_1/102-5343521-3571365?ie=UTF8&s=books)


Some folks backup up /home but not the stuff in / because you can restore this stuff.  I did read somewhere where you can get a list of all the packages you downloaded and ask that these file be restored.

You do not need to backup /dev nor /proc because these are memory only file systems.

Robert

---

