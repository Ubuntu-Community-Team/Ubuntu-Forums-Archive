---
title: "Where should I install Java plugins?"
date: 2007-09-25
forum: Absolute Beginner Talk
---

### Post by Sarteck on 2007-09-25
My Mom finally started going back to college, and one of the courses she is taking is a Math class.  A good deal of the work for this class is done online through this thing called "ALEKS", and requires their Java plugin to be installed.

Now, I am using Kubuntu Feisty on an AMD64, and I read that using the Blackdown plugin is the only way I'll be using a 64-bit Java Virtual Machine, so I installed it, tested it, and it works fine.  I e-mailed these ALEKS people to find out what I would have to do to get their plugin working, and they directed me to a page that said to get the jar file (aleksPack10.jar) and put it in my "Java VM lib/ext" directory.

I've been looking for it (using "whereis java" and looking in subdirectories), and tried a few various things (creating a lib/ext directory, etc.), but it hasn't worked.  Where should I be putting this jar file so that FireFox recognises it as a plugin when using Blackdown Java?

---

### Post by reckless2k2 on 2007-09-25
[http://easylinux.info/wiki/Ubuntu:Feisty#Browser_plug-ins](http://easylinux.info/wiki/Ubuntu:Feisty#Browser_plug-ins)

---

### Post by Sarteck on 2007-09-25
You misunderstand...  The Java plugin itself is already isntalled and working.  It's the ALEKS plugin I need to place in the "Java VM lib/ext" directory and get working.

---

### Post by Sarteck on 2007-09-25
The page the ALEKS guy pointed me to was this:

[ALEKS Plugin](http://www.aleks.com/downloads/linux_jvm)

---

### Post by RomeReactor on 2007-09-25
Hi. Enter the following in a terminal:
```
locate /lib/ext/
```
and post that here.

---

### Post by Sarteck on 2007-09-25
Thanks!  That's what I was looking for.  The directory was "**/usr/lib/j2se/1.4/jre/lib/ext**"

And the plugin is now working after a FireFox restart. ^_^  Thanks again, Mom will be thrilled!

---

### Post by Samanathon on 2008-04-09
Thanks a lot! That's exactly what I was looking for!

---

