---
title: "[SOLVED] MIgration XP to Feisty Fawn"
date: 2007-05-02
forum: Absolute Beginner Talk
---

### Post by coolbrook on 2007-05-02
Will the installation be intuitive and search my "C:" drive for media so that I don't lose images and music or will it just be looking for the My Documents/My Music Folders?  I'll back up as much as I can anyway.

---

### Post by starcraft.man on 2007-05-02
I haven't had any personal experience with the migration manager but I don't think it actually imports images and media... I think its mostly for wallpaper, favorites, bookmarks, contacts and a few other preference things. Best suggestion would be to simply do a dual boot until you are able to get all your media off the XP partition. Easy way to do that is to make 3 paritions with the installer.

1) **/** (root), 6-8 GB, Primary, Ext3 format

2) **swap file**, 2-3 GB, logical, swap-file format

3) **/home** (home directory), X GB, logical, Ext3 format 

X is whatever is left over after 1 and 2, you can use gparted to resize your ntfs XP partition but don't shrink it to less than the data on your drive else you will be in serious trouble.

After that, grub should detect XP and install it in your boot menu. Then you can use any method of your choice to swap it over. Make sure you like Ubuntu before you switch, I've heard plenty of upset stories about problems when completely moving >.>

---

### Post by andrewPCT on 2007-05-02
It looks in the default directory for documents (generally My Documents) and transfers everything.  Also, it will only work if you are setting up a dual boot system.

---

### Post by starcraft.man on 2007-05-02
> **andrewPCT said:**
> It looks in the default directory for documents (generally My Documents) and transfers everything.  Also, it will only work if you are setting up a dual boot system.

Really darn, I didn't know that... is this a live CD feature only? Oh well, doesn't matter... I had it all on my seperate USB drive, but still nice to know for future.

---

### Post by coolbrook on 2007-05-02
Thanks guys!  I'll be abandoning Windows on one system and trying to get it to boot like it used to on another

---

### Post by starcraft.man on 2007-05-02
> **coolbrook said:**
> Thanks guys!  I'll be abandoning Windows on one system and trying to get it to boot like it used to on another

No problem coolbrook, have fun with Ubuntu and stop by anytime :)

---

