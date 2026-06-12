---
title: "network help"
date: 2006-10-25
forum: Absolute Beginner Talk
---

### Post by garnetH on 2006-10-25
I need some help on setting up a network initially with an xp box and a ubuntu box and then I want to add more after that.

I am not used to using the command line, but this is what I have done and have not been able to get ubuntu to join my existing mshome network.

On ubuntu I have shared my directory, installed samba, configured eth0 and left it as DCHP without wins.

On my XP I have tried to locate the ubuntu by mapping the drive using \\ip address of my ubuntu machine\sharedfolder name

I get a log in box and type in my ubuntu login name and my ubuntu password. But the box just stays there when I press enter and that is as far as I get.

ANy help for a beginner?

Gary

---

### Post by l33tbuntuhax0r on 2006-10-25
[FONT="Fixedsys"][COLOR="Red"][SIZE="4"]y0ur 7cp/!p $74ck m4y 83 c0rrup73d.  7ry r3!n$7411!ng !7 70 $33 !f 7h47 f!x3$ 7h3 pr0813m.[/SIZE][/COLOR][/FONT]

---

### Post by dbd on 2006-10-25
This page should have all the info you need:
[https://help.ubuntu.com/community/SettingUpSamba](https://help.ubuntu.com/community/SettingUpSamba)
edit: Link changed.

After a brief look at it I think you need to run smbpasswd, but I'm not certain so if that doesn't work then have a look around that wiki page for more info.

Good luck :)

---

