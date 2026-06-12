---
title: "Read access to hfsplus for regular users ( I do NOT want/need write access)"
date: 2012-01-17
forum: Apple Hardware Users
---

### Post by Linforcer on 2012-01-17
Hey guys,

I tried googling this, but all I find is guides for getting read/write access..

All I want is normal users to have read access to all the files on the mac partition, so I can read my music library. right now, when I mount the partition the root user can get in there, but my normal user can't go deeper than my home directory.

Also I would like to know what the right fstab setup is for automatically mounting it that way. Can anyone help me with this?

---

### Post by coffeecat on 2012-01-18
Is this on your Mac Mini?

Anyway, you would need to set access/read permissions for "others" in the MacOS GUI for the folders and contents you want access to from Ubuntu. If you want help with this, I'll boot into my MacMini to remind myself of exactly how this is done. It's not difficult. You can even use a chmod command from the Mac terminal if you're feeling adventurous!

However, you say:

> All I want is normal users to have read access to all the files on the mac partition

All? I hope you mean all in your Mac home, not all files. You don't want to be changing permissions on system files. 

As far as an fstab line is concerned, I don't know. Mount the Mac partition from the GUI and then post the contents of /etc/mtab. That will give us a lead.

---

### Post by Linforcer on 2012-01-18
Well, I don't really care. I assumed Linux doesn't necessarily know what my system files are on Mac OS, but yeah, ok, all I really need is for my user and maybe one more to have access to stuff beneath my home dir, ore really ONLY the Music dir.

If I want to access files I don't mind being root, I just don't care for starting my music player as root, obviously.

Anyway I thought I tried what you told me to do on my girlfriend's system (A macbook) but I guess I didn't do it quite right. (I think I used "sharing" in the system prefs to indeed make the directory readable for all others.

Anyway I'll have a look and use chmod anyway and report back.

And yes, this is all on a Mac Mini

---

### Post by coffeecat on 2012-01-18
> **Linforcer said:**
> Well, I don't really care. I assumed Linux doesn't necessarily know what my system files are on Mac OS, but yeah, ok, all I really need is for my user and maybe one more to have access to stuff beneath my home dir, ore really ONLY the Music dir.

An important point this. If you change permissions of files in any folders except your Mac home folder you will break the operating system, just as you would in Ubuntu. The Mac GUI probably wouldn't let you anyway, but be careful with that chmod command. It is possible to do serious damage with it outside of the home folder.

> **Linforcer said:**
> Anyway I thought I tried what you told me to do on my girlfriend's system (A macbook) but I guess I didn't do it quite right. (I think I used "sharing" in the system prefs to indeed make the directory readable for all others.

Sharing is not the way to effect this, because you are directly accessing your Mac files by mounting the partition.

For the record, this is what you do in the Mac GUI. Open your home folder and right-click on any sub-folder that you are having problems accessing from Ubuntu. Click on "Get Info". In the info window that opens, unlock it by double-clicking on the padlock bottom right - you will be prompted for your password. Where it says "everyone No access", change that to either Read only or Read & Write by clicking on "No access". It doesn't matter which because you won't be able to write from Ubuntu anyway.

The only way you will be able to write to Mac folders from Ubuntu is by setting up sharing, but sharing involves both operating systems running and connected on the network, so that you would need Mac on one machine and Ubuntu on another.

---

### Post by Linforcer on 2012-01-18
I did as you said even though it was already set to Everyone : read access, and then clicked Apply to enclosed" as seen in this[ image]("http://img843.imageshack.us/img843/5471/screenshot20120118at809.png").

It does not seem to change anything in linux, I can still only access this folder and everything in it as root.

P.S. Despite the fact that it's called "file sharing" it looks like it serves the same purpose. (compare right window in image with left)

P.P.S Here is an [image]("http://img268.imageshack.us/img268/1124/snapshot1xz.png") of what kubuntu thinks about all of this.

---

### Post by Lars Noodén on 2012-01-18
My solution was to [change the user id](http://osxdaily.com/2009/02/19/mac-os-x-change-your-user-id/) on the OS X parition to match the Linux partition.  Also part of that solution has been to store all my data, including music, in a Linux partition/layout (but in HFS+).  Then I create symlinks on the OS X partition to the appropriate point on the Linux partition.  It's fiddly but I have everthing working and even my bookmark files are in sync that way.

---

### Post by Linforcer on 2012-01-18
Now that is just darn silly. I'd sooner start my media player as root or make an exFAT partition for my library to live in, but both of those (and your solution seem ridiculous.

Can't I do it the other way around? change my user id in linux, or add a user in Mac OS and give it used id 1000 and give that access to the files I want access to? (can you set the user id of a user in mac?)


(Also in case anyone noticed in the screenshots, in one I change permissions for one folder deeper than I try to access in the other, I did see that, and did the same to the correct folder with no difference)

---

### Post by Lars Noodén on 2012-01-18
Yes, if you follow the link in my previous post, it goes to a page on setting the UID in OS X.  There is also a way via the GUI, but it's much more complex.

As you suggest it is also possible to go the other way, to set the Linux UID after the OS X account.  That works too.  However, for me, the Linux side of things is my baseline.  I choose that way because I can just grab and go when I need to and know where everything is.  If you are more used to OS X than Linux then it might be the other way around for you.

We are talking about just a single account, right?  Or did you want all the music from all the accounts to be available?  If that is the case, then you need to mess with group settings.

---

