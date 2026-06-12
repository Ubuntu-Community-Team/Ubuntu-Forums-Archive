---
title: "New Linux user with a few problems"
date: 2006-02-05
forum: Absolute Beginner Talk
---

### Post by Mors_sum on 2006-02-05
I just got Ubuntu 5.10 to duel boot with XP, and after my first impressions I now intend to use Linux for just about everything except gaming, but I have had two major problems.

The first isn't so bad; I just can't seem to find a driver for my modem for any version of linux. I use a "D-1156IVT1", with a Riptide chipset. After several hours in google, I can find no driver for it; does one even exist?

The second problem is a bit worse. I have some large NTFS partitions for media, but when I try to access those from Linux I am told I "Do not have the permissions neccisary to view [this partition]". After reading a stack of help files, I decided to log on as root; however by default it seem you can't do that when Linux loads. So I went to the "Login Setup" or something in administrative tools, howver, once I click on it and enter my password, it closes itself, and I see nothing in logs. Furthermore my friend told me that I needed to install a package to view NTFS partitions, but the package installer does the same thing (refuses to open). It now seems that nearly all the programs in "administrative options" and several others are doing this, despite the fact that I installed Linux less than 12 hours ago, and I'm sure I can't have damaged it THAT badly so quickly.
Is this common? Does anyone have a solution or an idea as to why this happened? I would really appreciate any help.

---

### Post by RaiSuli on 2006-02-05
This link will help you with mounting Windows partitions:

[http://www.psychocats.net/linux/mountwindows.php](http://www.psychocats.net/linux/mountwindows.php)

---

### Post by Mors_sum on 2006-02-05
Thanks, that would solve my problem about not being able to read it, but does anyone have any idea why the programs stopped working?
And I saw something on that page that said NTFS was read only in Ubuntu; is that true, or is there a way around that?

---

### Post by Mors_sum on 2006-02-05
Is it normal for Ubuntu to have problems like this? Would a reinstall fix it? (I haven't had it installed for long enough to set anything up, so a reinstall is not too much of a hastle).

---

### Post by annsachd on 2006-02-06
From what I understand, you don't want to write to NTFS partitions from Linux. It's problematic at best. You can read from them fine.

Get yourself a cheap external modem that isn't a Winmodem (software) and you should have an easier time of getting dialup to work. I had an old Supra Express lying around that plugs in with a serial cable. It was easy to setup and get online.

---

### Post by Mors_sum on 2006-02-06
Thanks, I was considering getting an external modem before because they are just so much easier to get to work regardless of your OS.
The thing is, I'll be storing all my media (music, movies) on my large NTFS partitions, and if I then rip or download media in Linux I will want to store it with the rest. That's my only reason for wanting to write from Linux to NTFS.
As for the Ubuntu programs refusing to open.....I think I will just reinstall it and hope that fixes it.

---

### Post by Madpilot on 2006-02-06
Also, regarding your problems with root: use "sudo" in front of commands when you need to run them as root, and use your own user password when it asks for one.

Ubuntu, unlike some other versions of Linux, does not have a usable root account by default.

Get all the details here: [https://wiki.ubuntu.com/RootSudo](https://wiki.ubuntu.com/RootSudo)

---

