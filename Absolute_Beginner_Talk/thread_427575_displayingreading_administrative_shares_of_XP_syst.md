---
title: "displaying/reading administrative shares of XP system"
date: 2007-04-29
forum: Absolute Beginner Talk
---

### Post by ottawa on 2007-04-29
Hi all,

I am testing around with Ubuntu desktop 6.10, have installed smb and I can read/write shares from Ubuntu to XP or the other way around. As I would like to  manage a small mixed network (win?linux) it would be very handy for me to be able to read/write the XP/NT admin shares. Thoses are listed and shown in Ubuntu through smb, but trying to read from Ubuntu is failing in an error message saying: 

[B]The folder contents could not be displayed. 
Sorry, couldn't display the contents of C$[/B]

What do I have to do to get this content displayed and more over, even to be able to write to those folders/files ?
Any help very much welcome. Thank you.

ottawa

---

### Post by steve.horsley on 2007-04-29
Edgy had a bug with its SMB browser that may be your problem. I haven't checked Feisty for the same problem yet. But I do connect to shares, wth a command like this:
**nautilus smb://domain;administrator@1.2.3.4**
which you can put into a desktop launcher for convenience it you like. Notice the semicolon between the domain name and the user name.

---

### Post by ottawa on 2007-04-29
sorry, but that's not working here. It seems also that for this to work, one has to configure smb to use domain access rather workgroup access. I will have to test this further.
Do you know by chance if the Guest account of the xp machines has to be enabled ?

ottawa

---

