---
title: "Separate Documents vs Home Partition"
date: 2006-07-24
forum: Absolute Beginner Talk
---

### Post by confused57 on 2006-07-24
I've always seen it suggested to have a separate "home" partition, so that reinstalling the OS would not delete important files that someone has saved.
Just recently read a post suggesting it's actually better to keep /home with the root partition, but have a separate partition, guess you can call it anything, but "Documents" would indicate saved files.  I guess you just set up a mount point for the partition and save files to it, rather than to a separate home?
It's my understanding that a separate "home" partition would contain old configuration files that may conflict with a new install, especially an upgrade.

It appears to me that  a separate "Documents" partition would be the way to go.

---

### Post by userundefine on 2006-07-24
Eh, it's up to you if you want to reconfigure all your programs.  If you decide to switch from one distro to another, are you going to wait 3 months when the program versions will be beyond what your configuration files are, or are you going to change over immediately and likely have the same versions?  I've never seen a "compatibility" problem with config files between different programs that dump settings into /home (as opposed to something like php).

You could move all "personal" files off to another mount point/partition if you want, but it's a waste if it's not another harddrive.  It's not like they're more secure, or safer.  /home is where the heart is.

---

### Post by tzulberti on 2006-07-24
In the case of an upgrade, the old configure files would be used, so the best thing is to have a diferent document partion.

---

### Post by aysiu on 2006-07-24
I used to have a separate /home partition, and I got annoyed with it after a while, for the reasons you guessed. With a newer version of Ubuntu, the configuration may be a little off--a blank icon, for example. Your system will still be functional... but possibly a little bit weird.

Also, if you have any themes installed and such, you don't really get to experience the default installation at all. Now... you may not *want* to experience the default. But, for me, part of the joy of installing a new release is installing it--seeing how it performs by default. I can always tweak it later, and it doesn't take me long.

But I do have a separate documents partition for music, photos, and other personal files.

---

### Post by confused57 on 2006-07-24
> **aysiu said:**
> I used to have a separate /home partition, and I got annoyed with it after a while, for the reasons you guessed. With a newer version of Ubuntu, the configuration may be a little off--a blank icon, for example. Your system will still be functional... but possibly a little bit weird.

Also, if you have any themes installed and such, you don't really get to experience the default installation at all. Now... you may not *want* to experience the default. But, for me, part of the joy of installing a new release is installing it--seeing how it performs by default. I can always tweak it later, and it doesn't take me long.

But I do have a separate documents partition for music, photos, and other personal files.

Thanks aysiu, that answers my question & what I had sort of concluded, just wanted to get someone else's opinion.

---

### Post by nalmeth on 2006-07-24
Yeah, seperate Media partition is the way I go about things.

Call it paranoia, but when I reinstall my system (for my own reasons, not because I was forced to), I don't like the thought of holding my old /home. 

Yes, reconfiguration is a chore, especially since I rarely use the default for any of my favorite apps or DE's, but it's just peace of mind for me.

---

### Post by FrinkTheBrave on 2008-02-26
A bit of clarification then, if you wouldn't mind:
I am from a windows background and new to linux. I have a separate disk (called MY Data) for my documents/photos etc.
In /Home/Username are several folders: Desktop and Documents I understand. I guess Pictures, Music and Videos are like Documents, but what about Examples, File, Public and Templates?
Do they have special meaning?

When I do a Save in a newly created presentation it defaults to /Home/Username/Documents but really I want it to default to MY Data (or MY Data/Documents). Can I do that?
I don't really want two Documents folders, /Home/Username/Documents and MY Data/Documents.

Thanks,

- Frink

---

### Post by timbounceback on 2008-02-26
> **FrinkTheBrave said:**
> A bit of clarification then, if you wouldn't mind:
I am from a windows background and new to linux. I have a separate disk (called MY Data) for my documents/photos etc.
In /Home/Username are several folders: Desktop and Documents I understand. I guess Pictures, Music and Videos are like Documents, but what about Examples, File, Public and Templates?
Do they have special meaning?

When I do a Save in a newly created presentation it defaults to /Home/Username/Documents but really I want it to default to MY Data (or MY Data/Documents). Can I do that?
I don't really want two Documents folders, /Home/Username/Documents and MY Data/Documents.

Thanks,

- Frink
Templates is a folder that you can put, well, templates in, so when you right click, and select create file, you can create it from a template you put in there.

---

