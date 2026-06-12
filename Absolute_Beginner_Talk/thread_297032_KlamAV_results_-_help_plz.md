---
title: "KlamAV results - help plz"
date: 2006-11-10
forum: Absolute Beginner Talk
---

### Post by spamzilla on 2006-11-10
So I ran a virus scan just for the hell of it. I know it's pretty hard to get viruses on Ubuntu, but since I own a website and receive random emails regularly, I figured it's best to be safe then sorry! So anyway, I ran the scan and, KlamAV found 15 viruses/problems, all with the status of "loose." What does this mean and what should I do to these files?

Thanks in advanced :)

Here's an image of the offending files:

---

### Post by johnnymac on 2006-11-10
Don't think it's a virus - I think it's a clamAV setting.  More than likely your clamAV setting has a specific file size allowed for *.zip and *.gzip files.  I'd look at the man pages for clamAV to get the exact location and how to modify.  As for the other file (the test file) it's going to pick that up as a virus because that's what it does...displays as a virus for testing.

---

### Post by spamzilla on 2006-11-10
I figured that they weren't viruses, and I found the settings about the zip sizes. Thanks for replying :P

---

