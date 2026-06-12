---
title: "firefox closing when uploading to revver?"
date: 2007-06-14
forum: Absolute Beginner Talk
---

### Post by tdrusk on 2007-06-14
I just made this video to show what happens
[http://blip.tv/file/265498](http://blip.tv/file/265498)

A couple of other programs have been doing that to me. I don't know why. Does it have to do with a process using up too much memory?

---

### Post by FuturePilot on 2007-06-14
Launch Firefox from the terminal and see if/what errors it gives when it crashes.

---

### Post by tdrusk on 2007-06-14
> **FuturePilot said:**
> Launch Firefox from the terminal and see if/what errors it gives when it crashes.
I got when going to revver and uploading.
Segmentation fault (core dumped)

it just did it without me being at revver.

---

### Post by FuturePilot on 2007-06-14
I would also try and see if you can reproduce the problem on the live CD. If it doesn't do it with the live CD something is probably corrupted or something. You could try reinstalling it and deleting your ~/.mozilla-firefox profile in your Home directory. It's hidden so you have to make the hidden files visible.

---

### Post by tdrusk on 2007-06-14
I just did a complete removal and reinstall. It still does it.

---

### Post by tdrusk on 2007-06-14
I just changed Ubuntus. I went from Feisty to Dapper and it is still happening.

---

