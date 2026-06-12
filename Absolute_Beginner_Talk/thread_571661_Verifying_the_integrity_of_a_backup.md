---
title: "Verifying the integrity of a backup"
date: 2007-10-09
forum: Absolute Beginner Talk
---

### Post by JasonBourneLinux on 2007-10-09
hello,

I was wondering if there was an app for Ubuntu or Arch or Fedora that verifies data that, for example, has been deposited onto a portable hard drive. When I say verify, I mean, compare the file on the external device with the copy on, for say a flash drive or another HD.

thanks for your help in advance

PS- Ive read other threads but when people say "verify" it doesnt seem like what im trying to get at

---

### Post by Overbyte on 2007-10-10
How about [diff]("http://en.wikipedia.org/wiki/Diff")?

You can zip/tar the data, back it up, and run a diff off the two files.
Just run the command on the terminal, I don't think you need to install anything,

---

### Post by Paqman on 2007-10-10
I suppose you could [MD5](https://help.ubuntu.com/community/HowToMD5SUM) them. That tool's built in, too.

---

