---
title: "Live-cd not booting!"
date: 2006-06-11
forum: Absolute Beginner Talk
---

### Post by mkolby on 2006-06-11
Well, as the title says, my Live-CD doesn't boot on restart. Am I supposed to do something for it to boot? I was under the impression that it happened automatically.

This is my second Live-CD, the first one didn't work either.

Hopefully it's just me, I want the Ubuntu experience!! :D 

Mads Kolby
Copenhagen

---

### Post by Klaidas on 2006-06-11
Make sure that you set CD-ROM as your first device to boot.
Make sure md5sums match

By the way, do you get any error while trying to boot?

---

### Post by XxNightfirexX on 2006-06-11
A little more info is needed to help you properly.

1) Have you made sure your iso was burned as an image and not as a file?
    To check that, simply put your cd in, and explore it. If it shows only the iso file, then it was burned as a file and not as an image, and therefore won't work.

2) Is your cd-rom set as your main boot device in Bios? If not, you need to change that or you'll continue to boot of your hd.

3) Have you used the checksum to make sure you got a complete/good copy of the iso file?

Now, even if all of these are done correctly, that still doesn't guarentee your cd will boot. It's possible you're getting a bad burn. The best bet, after checking these (if things still don't work), is to re-burn the iso image at the slowest burn speed you can, that minimizes any risk of coruption during the burn process.

---

### Post by mkolby on 2006-06-11
Thanks. It worked after I changed the bios setup. All I need know is for my wireless connection to work, and I might actually consider switching to Ubuntu instead of windows.

---

