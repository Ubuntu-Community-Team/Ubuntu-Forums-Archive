---
title: "OK, my dad is hesitant to instal ubuntu on his  win 98 tower . . .V. . ."
date: 2007-07-04
forum: Absolute Beginner Talk
---

### Post by ~~Tito~~ on 2007-07-04
and I would like to know if it can install programs that run for windows like The Watchtower Library? And can it play games well. Like The Sims 2, and is there a plug in that allows it to run active x because I need it to run a certain website. :p

PS: The live cd runs on the computer faster than windows. No mouse studdering or anything.

---

### Post by Vajra Vrtti on 2007-07-04
> I would like to know if it can install programs that run for windows like The Watchtower Library?

Some Windows programs can run under a product named **Wine**. It is possible to install *The Watchtower Library* under Wine, but it is not easy.

> And can it play games well. Like The Sims 2

The same is valid for games. Some can be executed under Wine but many can't. I doubt *The Sims* will work. Many people dual boot Linux and Windows. I only use Windows only for games. That said, there are many games that run natively in Linux.

> and is there a plug in that allows it to run active x

As far as I know, there is no Active X support in Linux (thanks God!).

---

### Post by lisati on 2007-07-04
And some Windows stuff has Linux versions e.g. Open Office, AVG Antivirus,.......

---

### Post by ~~Tito~~ on 2007-07-04
I'm asking is there because i really need active x to run a website called mlxchange a real estate website, do you think there is a Linux version of Netscape?

---

### Post by Vajra Vrtti on 2007-07-04
Yes, Netsacape has a Linux version.

---

### Post by ~~Tito~~ on 2007-07-04
Active x support?

---

### Post by Malibu Illusion on 2007-07-04
You can install Internet Explorer under Linux, execute it using WINE and install some required .dll files to enable Active X support in that browser.  

A quick web search for "activex linux" will show you this information.

---

### Post by Surkow on 2007-07-04
> **~~Tito~~ said:**
> Active x support?
It's a lot of effort...but [here]("http://www.gagme.com/greg/linux/activex-linux.php") is a guide to make it work. And Netscape in Ubuntu does not support the engine of Internet Explorer.

---

### Post by ~~Tito~~ on 2007-07-04
> **Malibu Illusion said:**
> You can install Internet Explorer under Linux, execute it using WINE and install some required .dll files to enable Active X support in that browser.  

A quick web search for "activex linux" will show you this information.

So i will have to get them from the ie folder?

---

### Post by Malibu Illusion on 2007-07-04
Plz read the page:

[http://www.gagme.com/greg/linux/activex-linux.php](http://www.gagme.com/greg/linux/activex-linux.php)

---

### Post by ~~Tito~~ on 2007-07-04
Excelent thanks, What about exe cd's like the watchtower library cd i have?

---

### Post by Malibu Illusion on 2007-07-04
Once you have installed WINE, you can run things such as setup.exe from the CD by issuing:

```
wine /media/cdrom0/setup.exe
```

Or something along those lines.  This will initiate the installation.

I have taken the liberty of checking the WINE application database for you, you'll find the application's page [here](http://appdb.winehq.org/appview.php?iAppId=1485) detailing how it runs, and what doesn't run.  I suggest checking any native Windows application that you're thinking about running under WINE against that database to see other people's experiences.  Click the version numbers on the left to be taken to pages with more detailed info.

Take care.

---

### Post by ~~Tito~~ on 2007-07-04
Excellent thanks. :KS:KS:KS:KS:KS

---

### Post by Surkow on 2007-07-04
> **Malibu Illusion said:**
> Plz read the page:

[http://www.gagme.com/greg/linux/activex-linux.php](http://www.gagme.com/greg/linux/activex-linux.php)

...The exact same link I posted 20min earlier.

---

### Post by ~~Tito~~ on 2007-07-04
So sorry I didn't see that.
:(

---

### Post by Malibu Illusion on 2007-07-04
**@Surkow**: And that's the exact same link that appears first in Google when you insert the search terms that I posted up even earlier, which I was staring right at at the time. =P

You shouldn't have to do someone's homework for them in its entirety; it's often better to gently encourage them to research the information themselves. ;)

---

### Post by ~~Tito~~ on 2007-07-05
What other things that I will need to run some windows programs?

---

### Post by Hallvor on 2007-07-05
Luck ;)

---

### Post by splintercellguy on 2007-07-05
I doubt your machine could handle it, but you could run Windows in a VM.

---

### Post by lisati on 2007-07-05
> **Hallvor said:**
> Luck ;)

:popcorn:

---

### Post by ~~Tito~~ on 2007-07-05
Any other essential programs, not having to do with windows?

---

