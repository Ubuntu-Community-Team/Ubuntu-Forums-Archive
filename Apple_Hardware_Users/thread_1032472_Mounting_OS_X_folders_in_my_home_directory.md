---
title: "Mounting OS X folders in my home directory"
date: 2009-01-06
forum: Apple Hardware Users
---

### Post by ColBuendia71 on 2009-01-06
Hi, I'm about to order a MacBook and will be installing Intrepid alongside OS X. I would like to mount the documents folder from OS X as the documents folder in my home directory so that I can do work on current versions of documents no matter which OS I'm currently working under. I have little experience with OSX, so my question is will it play nice? Will there be permission conflicts between systems or is OS X going to complain that something else is fooling around in its directories?

---

### Post by TreeHugger52 on 2009-01-06
I doubt it. I'm running 8.10 alongside OSX on a macbook, and I am unable to work meaningfully with my OSX partition. I can SEE many of the files, but can't work with them as I would like. 

This is a nice resource for using Ubuntu on my version of the macbook (Santa Rosa). [https://help.ubuntu.com/community/MacBook_Santa_Rosa](https://help.ubuntu.com/community/MacBook_Santa_Rosa) . See the discussion about hfs+ support (or the relative lack thereof). I don't know if this applies to newer macbook chipsets.

I would love to be corrected so that I can share documents easily between the two partitions...

---

### Post by TreeHugger52 on 2009-01-06
My previous post was true two days ago before I did a full re installation of ubuntu. I can now view, open, modify, and copy documents on the OSX partition.

Great for me- sorry to leave contradictory posts.

---

### Post by ColBuendia71 on 2009-01-06
What was different on the reinstallation as opposed to the initial one? I'm confused.

---

### Post by cyberdork33 on 2009-01-06
you can, but the files there will be "owned" by the OSX user, not your Ubuntu user so there will be some permissions issues. You can get around those by changing your userid in Ubuntu.

Also, you will have to disable journaling in OSX in order to make the file system writable from Ubuntu and that is probably not something you want to do with your OSX partition.

---

### Post by ColBuendia71 on 2009-01-06
Yeah, I don't really want to disable journaling. What would you recommend then as far as keeping my documents synced between the two OS? I'm a writer and it's really important that I keep current versions of whatever I'm working on.

---

### Post by tiresia on 2009-01-06
I have a similar situation. The best solution is to create a 'third' partition, that you format as HFS+ *not Journaled*. Both System will read and write on it.
You could use FAT32, but there is a limitation of 4GB (you can't keep there a movie for example). You will find several threads about it in this forum.

You should keep in mind, that is not advisable to work on a document with different versions of the same program (as it can happen with OSX and Ubuntu). 

Anyway you have an Intel Mac, mind the number and the order of your Partitions on your computer (how many partitions do you have already?)

---

### Post by ColBuendia71 on 2009-01-07
Well, I was planning to have maybe three. (The computer is currently being shipped so I don't have it yet. I'm asking this question in advance so I can get things set up and get back to work as soon as I get it.) I was going to do just two: HFS+ for my OS X installation and then an ext3 for Ubuntu.

Could you elaborate what you mean about working with different versions of the same program? Do you mean different versions of Open Office?

Also, what would be the best way to ensure that both systems have access to my music collection?

---

### Post by Rog-Mahal on 2009-01-07
I wonder if you could use the Shared folder under Users in OS X. When I mount my OS X partition it seems to be readable, perhaps that could be a place for a read-only music collection? I'm not entirely sure about that though.

As for the different versions thing, it can sometimes be risky to switch between two versions of a program, or programs that say they are compatible. I've had some formatting issues in documents I've written with OpenOffice 3.0 on OS X and then taken over to the OpenOffice 2.4 installed with Ubuntu by default. It's not as bad as taking a .odt saved as a .doc to a Windows machine, but there are still some kinks.

---

### Post by ColBuendia71 on 2009-01-07
Well, I've been using OpenOffice 3.0 on this hardy machine via a ppa repository and it's worked fine. I'll likely do the same on the MacBook when I install Intrepid. Yeah, the music shouldn't be a problem now that you mention it since it's read only.

The primary issue for me is just being able to work on the same version of a document no matter which OS I'm booted into.

---

### Post by cyberdork33 on 2009-01-07
I have an external drive that i use for Time Machine, but I made a small FAT32 partition on it for some music / docs that I have. You can do the same thing on the internal drive.

NOTE, there is also a hidden EFI partition at the beginning of the disk, so one OSX partition and one Ubuntu partition = at least 3

---

### Post by ColBuendia71 on 2009-01-07
I have a USB drive that I considered using to keep all my documents on, but I just don't want to have to carry it around all the time since I'm on the go quite a bit. I also shy away from creating a third (fourth) partition since I'm new to the Mac world even though I read at maybe a third grade level in Ubuntu. Maybe I'll just keep all my docs in one OS and call it a day.

Or would rsync be able to do something for me in this situation?

---

### Post by cyberdork33 on 2009-01-07
> **ColBuendia71 said:**
> Or would rsync be able to do something for me in this situation?
You could probably eventually get something working, but then you have two copies of everything, and you have to make sure to sync before you work on anything. More trouble than it's worth if you ask me. Another partition is MUCH easier than all that.

---

### Post by rshnike on 2009-01-08
> **cyberdork33 said:**
> you can, but the files there will be "owned" by the OSX user, not your Ubuntu user so there will be some permissions issues. You can get around those by changing your userid in Ubuntu.


Any chance you have a link or some suggestions as to how to do this? My main partition is my Mac partition, so I really don't want to mess with any permissions whatsoever on it. If I could change things on the Ubuntu side I'd much sooner do that. As a matter of fact I want to keep things read-only to ensure that Ubuntu never changes anything whatsoever on the Mac side, so Journaling is staying on for me.

---

### Post by cyberdork33 on 2009-01-08
I've never done it, but I think you need the usermod command. Your Mac user's uid should be something like 1000 and your Ubuntu user's uid is something like 500.

---

### Post by rshnike on 2009-01-08
Well wasn't that painless...

I booted into recovery mode and did the following from a root shell:

cd /media/OSX/Users/Me
(Replace Me with your username)

ls -l

Copied the user id from there (In my case it was 501)

sudo nano /etc/passwd

changed userid to 501:501

chown -R /home/Me
(Replace Me with your username)


reboot



done. Works perfectly.

---

