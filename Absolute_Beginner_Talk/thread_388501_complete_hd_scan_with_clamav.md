---
title: "complete hd scan with clamav?"
date: 2007-03-19
forum: Absolute Beginner Talk
---

### Post by darkeale on 2007-03-19
does anyone know a way to run a complete hard disk scan using clamav. i use the command clamscan -r but this seems to only scan the home folder. any ideas?

thanks

alex

---

### Post by annda on 2007-03-19
what about sudo clamscan ? that way the program should be able to access files that do not belong to you as a specific user - by running with administrator privileges. it should help.

---

### Post by darkeale on 2007-03-19
no that still appears to just do the home folder aswell. thanks for your help anyway tho. any other ideas?

---

### Post by freebird54 on 2007-03-19
I am wondering why you would want to scan the whole drive.  Windows files are only likely to be found under /home somewhere.  Is that not the purpose of clamav- scanning for Windows problems, so you don't forward them?

Windows malware can't run on Linux without a LOT of trouble being taken by the user (installing them in wine perhaps?)

Just wondering.... :)

---

### Post by darkeale on 2007-03-19
> **freebird54 said:**
> I am wondering why you would want to scan the whole drive.  Windows files are only likely to be found under /home somewhere.  Is that not the purpose of clamav- scanning for Windows problems, so you don't forward them?

Windows malware can't run on Linux without a LOT of trouble being taken by the user (installing them in wine perhaps?)

Just wondering.... :)

ah i see. i thought it would be like windows where things can hide anywhere but thinking about it i guess your right. thats the point of me having linux. in that case it doesnt matter then. thanks all

---

