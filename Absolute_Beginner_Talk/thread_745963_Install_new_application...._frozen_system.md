---
title: "Install new application.... frozen system?"
date: 2008-04-05
forum: Absolute Beginner Talk
---

### Post by jwkungfu on 2008-04-05
Hi!
I went to the Frostwire website, downloaded (to my desktop) the Ubuntu version download.
I clicked on the install application, it installs but then feeezes up when it says that it is setting itself up? I've waited a while... nothing. I check the processor activity and it's a black screen, doesn't seem to be processing anything...?
How long should I wait for an application to set itself up?
Thanks,
john

---

### Post by ramjet_1953 on 2008-04-05
If your machine is still frozen, try the following:

1. Can you move to another desktop? If so, try to log off and back in.

2. If the system is totally frozen, do this in order:

3. cntl alt del : does this take you back to the login? If not, try this.

4. Alt SysRq + r  Wait a few seconds

5.Alt SysRq + s Wait a few seconds

6. Alt SysRq + e Wait a few seconds

7. Alt SysRq + i Wait a few seconds

8. Alt SysRq + u Wait a few seconds

9. Alt SysRq + b Wait a few seconds

The above keystrokes allow you to shut down a frozen system safely. It allows the keyboard to input data in raw mode, sync the HDD, terminate all processes, re-mount the file system in read-only mode and finally re-boot.

This is MUCH SAFER than just powering down a frozen system.

Regards,
Roger :cool:

---

### Post by jwkungfu on 2008-04-05
I first came across this problem the other day when I first downloaded the appl.
My machine isn't frozen as I am able to do other things...

I clicked on the display terminal on the install window and the message is that it is configuring.... but it seems nothing has/is...?

Are there any other appl that I could try?
Anything already in Ubuntu that I could try?
I had Nicotine that seemed to work ok?

---

### Post by Crafty Kisses on 2008-04-05
When this happens see if you can get to your Terminal and post the following output:
```
top
```

---

