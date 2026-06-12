---
title: "[SOLVED] ubuntu takes over"
date: 2008-01-31
forum: Absolute Beginner Talk
---

### Post by captkit on 2008-01-31
By takes over, I mean that, when I boot from a shut down computer, Ubuntu loads by default. I am running a dual boot, dual hard drive machine with XP  on the master and ubuntu on the secondary slave. Mucha as I like Ubuntu, I want the machine to boot into Xp by default. When I go into the setup screen (which makes me nervous) and get boot priority to boot the secondary drive I get a message that there is no OS on that drive in spite of having installed it there. My wife wants XP when she turns on the computer. She will not select it from a list and she's mad. I need help. Is anybody out there?

---

### Post by jordanmthomas on 2008-01-31
Can you post this file?
```
/boot/grub/menu.lst
```

Basically what you'll want to do is change the line that says
```
default 0
``` to 
```
default someothernumber
```

To get the right number, count (start at 0) the number of options you have in your grub menu when you first boot up.  Replace the 0 with the number That windows shows up in the list.

For example, if Windows is the third item, you'd put 2 as the default.

If you need help, just post your file here and we can help.

---

### Post by captkit on 2008-01-31
That was a quick reply--thanks. I think I get the drift of your instructions. I have zero experience with command lines and don't know how to post a file if I can find it. Here's my level of experience:
"If I press Enter when the little flashing thingie in the upper left hand corner that looks like a dash and comes on just before  the list of available OS's comes on will I be able to enter GRUB and reconfigure the order in which the OS's load?" Incidently I am using v7.10 not 6-06 and I don't know why my bean count (0?) is hidden.

---

### Post by Vadi on 2008-01-31
Nono, there's an easier way.

Install StartUp Manager ([click]("http://getdeb.net/search.php?keywords=startup%20manager")). Go to System - Administration, StartUp Manager, and change the default boot setting to windows xp or "last used". And you're done.

---

### Post by captkit on 2008-02-01
Thank you, Vadi. That did it.

---

### Post by Crafty Kisses on 2008-02-01
> **Vadi said:**
> Nono, there's an easier way.

Install StartUp Manager ([click]("http://getdeb.net/search.php?keywords=startup%20manager")). Go to System - Administration, StartUp Manager, and change the default boot setting to windows xp or "last used". And you're done.

That's the easiest.

---

### Post by Vadi on 2008-02-01
> **captkit said:**
> Thank you, Vadi. That did it.

Click on "Thread Tools" on top, and select "Mark thread as solved" to help out others later, thanks.

---

