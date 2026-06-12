---
title: "Lexmark X73 detected, but not functioning"
date: 2007-04-12
forum: Absolute Beginner Talk
---

### Post by scott5280 on 2007-04-12
Greetings all,

Linux newbie for the 2nd time.  It's been 7 years since my last attempt, and things are going much better this time.

I've searched this forum and seen several posts, but none either work or make any sense to me.  Again, a Linux newbie....

My Ubuntu install went great, and everything is working except the printer - printer is recognized, but any print job sent ends up in a "Stopped: job stopped" state.  The odd thing is that when I was running the live cd for a while before installing, I was able to print from ubuntu just fine...

Thanks for any help.

---

### Post by SanjoEel on 2007-04-12
Did you install the printer? Go to system>administration>printing and see if you need to install your printer and driver from there.

---

### Post by scott5280 on 2007-04-12
Should have mentioned that in the original post.  It is installed, and shows as 'ready'... and right now shows 1 job pending (my last attempt).

---

### Post by ramjet_1953 on 2007-04-12
Follow this link:

[http://www.linuxprinting.org/show_printer.cgi?recnum=Lexmark-X73](http://www.linuxprinting.org/show_printer.cgi?recnum=Lexmark-X73)

Hopefully it will get this Lexmark working for you.

Regards,
Roger :cool:

---

### Post by scott5280 on 2007-04-13
OK - here's a newbie question.... I need to download and install the gutenprint driver, correct?

---

### Post by scott5280 on 2007-04-14
I've downloaded the gutenprint driver, but following the steps on that site hit a wall.  The following 'alien' command isn't recognized by ubuntu:

```
sudo alien --scripts gutenprint-5.0.0.99.1-2lsb3.1.i486.rpm
```

I'm pretty sure I can't use the dpkg command on an rpm file,... so I could use some more direction.

Any ideas?

Thanks.

---

### Post by drmbogo on 2007-04-28
Just in case you're still trying...
You should already have the driver, it's just not the obvious one.
Look for one named "Lexmark z_42 CUPS + Gutenprint v5.0"
This has apparently been fixed in Feisty....

---

### Post by scott5280 on 2007-04-29
Thanks for the post.  I'm getting closer.  Set the printer up with that driver, and now when printing a test page the printer does spit out a blank sheet, which is more than it was doing before.  I welcome any other suggestions you might have.

thanks again

---

