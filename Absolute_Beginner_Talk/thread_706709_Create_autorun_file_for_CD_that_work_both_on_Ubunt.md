---
title: "Create autorun file for CD that work both on Ubuntu and Windows?"
date: 2008-02-24
forum: Absolute Beginner Talk
---

### Post by vavroom on 2008-02-24
I am creating a CD that will be distributed to several people.  I have no way of knowing if the people getting the CD will be on Windows, *nix or Mac.  I only need a particular HTML file to open in the default browser when the CD is inserted in the drive.

I've been able to create an autorun.inf for the CD to run in windows, that was quite straightforward.

[code]
[autorun]
ShellExecute=index.html
icon=icon.ico
[code]

Now, how do I make it happen if the user puts the CD in a Ubuntu/*nix box?  Obviously, I'd love to know on Mac as well, but this ain't the place to ask about macs ;)

Thanks for any ideas or assistance.

---

### Post by doorknob60 on 2008-02-24
Hmm, I don't know if it's possible in Ubuntu for it to do that. Not sure about Mac.

---

### Post by vavroom on 2008-02-24
Surely it's possible to get a particular file or program to play once you insert a CD in the drive?

---

