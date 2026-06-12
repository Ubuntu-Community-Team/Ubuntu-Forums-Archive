---
title: "USB external hard drive and UPS questions"
date: 2006-08-23
forum: Absolute Beginner Talk
---

### Post by arijarot on 2006-08-23
Hello,

To what type of file system should I format my external hard drive if I want to be able to read and write to it with linux but read from it with mac os x?

I just switched from m$ windows. on it, I had my UPS enabled, but when I went to the power manager in Dapper, I couldn't find it? 

Any suggestions would be much appreciated :)

A

ps what's the purpose/use of having workspaces?

---

### Post by jeremy on 2006-08-23
Your ext HD can be formatted as FAT32, then it can be read/written by linux, mac and even windows.
I have an APS UPS, and use apcupsd (from the repos), it works perfectly.

---

### Post by jeremy on 2006-08-23
By workspaces, do you mean different desktops? They are so you can have different programmes open in different desktops.

---

### Post by arijarot on 2006-08-23
> **jeremy said:**
> Your ext HD can be formatted as FAT32, then it can be read/written by linux, mac and even windows.
I have an APS UPS, and use apcupsd (from the repos), it works perfectly.

thanks, jeremy. can you defrag fat32 in linux?

i'm not sure what kind of ups i have, can the apcupsd be used as for any UPS?

---

### Post by arijarot on 2006-08-23
> **jeremy said:**
> By workspaces, do you mean different desktops? They are so you can have different programmes open in different desktops.

on the right of the bottom panel there are the four workspaces, if that's what you mean by four desktops, then, yes... why would you need different programmes open on different desktops? less clutter?

---

### Post by newlinux on 2006-08-23
Yep, less clutter. I often have tons of windows open at once, and switching from workspaces helps. Or I'll be working on something, and my wife will want to use the computer without messing with anything, so she'll just switch to a "clean" workspace.

Partition Logic can defrag FAT32. Search for it and you will find it. Some of the other partitioning tools may be able to as well.

---

### Post by arijarot on 2006-08-23
Thanks, newlinux:)

---

### Post by arijarot on 2006-08-23
Is there a command or something which will allow me to ID the type of UPS that my system has?

---

