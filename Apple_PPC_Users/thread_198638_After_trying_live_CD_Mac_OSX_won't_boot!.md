---
title: "After trying live CD Mac OSX won't boot!"
date: 2006-06-17
forum: Apple PPC Users
---

### Post by mooreted on 2006-06-17
I tried out the Ubuntu live CD for PPC. After I got done playing around with it and rebooted, my Mac will not boot into OS X.

What do I do now?

---

### Post by tidris on 2006-06-17
What happens if you hold down the option key while booting?

---

### Post by mooreted on 2006-06-17
I get as far as the blue startup screen. The progress bar gets all the way to the end then stops. It won't boot any further. I have not tried the option key, but pressing SHIFT will not load safe mode and SHIFT+OPTION+S will not load the command-line.

Is there anyway to backup my primary HD to my secondary HD so I can reinstall OS X without losing everything?

---

### Post by mooreted on 2006-06-17
Okay, tried the option key. Nothing happend. Rather, it didn't change anything. I get to the blue screen and that's it. It won't go any further.

---

### Post by gingerbread_man on 2006-06-17
you may want to reset your NV RAM and PRAM. refer this document for detailed instructions.
[URL="http://docs.info.apple.com/article.html?artnum=2238"]http://docs.info.apple.com/article.html?artnum=2238
[/URL]

if that doesn't work. you can try to restore OS X boot settings by booting off your OS X DVD and then choosing a startup disk from the Utilities menu. I hope this helps.

you might want to try the startup disk method first since its the least destructive.

---

### Post by mooreted on 2006-06-17
Well, I did an archive and install and it looks like all my stuff is still here. Pretty tense moment.

I guess I will just have to install Ubuntu on my second hard drive to give it a real test run.

---

### Post by hotani on 2006-06-17
When I installed it on my 2nd drive it took over and now when I want to boot OS X on the primary drive I have to do the option key trick. Just FYI.

---

### Post by mooreted on 2006-06-17
Thanks, I will remember that. Now I just have to figure out how to make a partition on my second hard drive without destroying my data.

---

### Post by mooreted on 2006-06-17
Okay, I'm using parted to resize the partition. Hopefully that will give me a 30GB partition to play with Linux on. I haven't filled up my 150GB drive in a year, so I can spare the space.

Wish me luck.

Thanks for all the help.

---

