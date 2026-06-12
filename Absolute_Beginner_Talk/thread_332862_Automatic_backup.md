---
title: "Automatic backup?"
date: 2007-01-06
forum: Absolute Beginner Talk
---

### Post by kimro on 2007-01-06
Hi there.

Is there a way to install/setup automatic incremental backup of certain folders to an external usb drive? Kinda like how Iomega or other external usb hdd unit manufacturers have software to do such but under Ubuntu... Thank you!!

---

### Post by CheshireMac on 2007-01-06
> **kimro said:**
> Hi there.

Is there a way to install/setup automatic incremental backup of certain folders to an external usb drive? Kinda like how Iomega or other external usb hdd unit manufacturers have software to do such but under Ubuntu... Thank you!!

You can script it yourself, although I'm not sure how to do it . . .but yes. There is a way to do it. Please hold for more intelligent people to answer. ~LOL~

---

### Post by kimro on 2007-01-06
I found Simple Backup (sbackup) and installed it.
I think it has all the features I need but I don't know how to set destination to my external usb hdd. 

As well, if there are better/other alternatives, I would love to hear about them.
Thanks!!

---

### Post by cult hero on 2007-01-06
Traditionally, I have scripted mine using rsync. However, I just installed Ubuntu on a machine that I want to use primarily as an automated backup server. Is there some kind of simple front end for doing incremental backups?

One of the reasons I am going with Ubuntu is, while I have a lot of the skills to do this kind of work by hand, I'm trying not to have to do it much. I used to be a Gentoo guy for crying out loud.

So, any good programs?

---

### Post by arnieboy on 2007-01-06
> **kimro said:**
> I found Simple Backup (sbackup) and installed it.
I think it has all the features I need but I don't know how to set destination to my external usb hdd. 

As well, if there are better/other alternatives, I would love to hear about them.
Thanks!!

when you plug in your external usb drive, you will see it getting automounted to a location in /media
Set that location in System --> Administration --> sbackup config--> Destination (Use custom local backup directory)

---

