---
title: "sorry"
date: 2008-02-24
forum: Absolute Beginner Talk
---

### Post by trgy on 2008-02-24
Thats too bad to hear. But if you think that Vista will be problem-free for its entirety, you got another thing coming,
well it s just that im used to resolve all kind of troubles with vista or other versions or windows so after whole day i just lost my temper. This will be the third time for me to instal ubuntu all over again because of that blank screen i just got. This ATI driver just won t work and it messes everything up. Or it s just hapend to bee that I m too stupid to understand all this.

---

### Post by meindian523 on 2008-02-24
Is this a rant,note to yourself or are you actually asking for some help?If asking for help,please post in --human-readable format.

---

### Post by kellemes on 2008-02-24
> **trgy said:**
> Thats too bad to hear. But if you think that Vista will be problem-free for its entirety, you got another thing coming,
well it s just that im used to resolve all kind of troubles with vista or other versions or windows so after whole day i just lost my temper. This will be the third time for me to instal ubuntu all over again because of that blank screen i just got. This ATI driver just won t work and it messes everything up. Or it s just hapend to bee that I m too stupid to understand all this.


Why do you think reinstalling Ubuntu 3 times will magically fix your problem?

Like previous poster said.. post specs and all info you can think of that may be relevant for people willing to help.

---

### Post by trgy on 2008-02-24
> **kellemes said:**
> Why do you think reinstalling Ubuntu 3 times will magically fix your problem?

Like previous poster said.. post specs and all info you can think of that may be relevant for people willing to help.

I dont think that will but each time after installing an ATI driver I get the black screen on startup and I can t do anything else

---

### Post by ugm6hr on 2008-02-24
> **trgy said:**
> I dont think that will but each time after installing an ATI driver I get the black screen on startup and I can t do anything else

Maybe you should start again.  The original post doesn't really make any sense.

Are you trying to install Ubuntu?  Which version?  On what hardware?

And do you get a blank screen from the start?  Or is after installing the "ATI driver"?  Where did you get the ATI driver from?

What ATI graphics card do you have?  The output from the following command will help identify it from within Ubuntu:
```
lshw -C display
```

---

### Post by trgy on 2008-02-24
> **ugm6hr said:**
> Maybe you should start again.  The original post doesn't really make any sense.

Are you trying to install Ubuntu?  Which version?  On what hardware?

And do you get a blank screen from the start?  Or is after installing the "ATI driver"?  Where did you get the ATI driver from?

What ATI graphics card do you have?  The output from the following command will help identify it from within Ubuntu:
```
lshw -C display
```
I get black screen after I install ATI driver. I hawe toshiba satellite A210-11c and graphic card is RADEON X1200. I goth driver from ATI download site and ubuntu is version 7,10

---

### Post by davec64 on 2008-02-24
Rather than reinstall it just sounds like your xorg.conf has incorrect settings selected for your card.
To get back to a screen with something on it, rename your xorg.conf backup to xorg.conf.

---

### Post by trgy on 2008-02-24
> **davec64 said:**
> Rather than reinstall it just sounds like your xorg.conf has incorrect settings selected for your card.
To get back to a screen with something on it, rename your xorg.conf backup to xorg.conf.

I will reinstall it again. When I install my driver it seems to be installed correctly, but in device management it says that is using some other driver. How do I rename? Sorry but I newer used linux before.

---

### Post by Crafty Kisses on 2008-02-24
> **kellemes said:**
> Why do you think reinstalling Ubuntu 3 times will magically fix your problem?

Like previous poster said.. post specs and all info you can think of that may be relevant for people willing to help.

Third time a charm.

---

### Post by trgy on 2008-02-24
> **Codename said:**
> Third time a charm.

Easy 4 U to say:confused:

---

### Post by ugm6hr on 2008-02-24
> **trgy said:**
> I get black screen after I install ATI driver. I hawe toshiba satellite A210-11c and graphic card is RADEON X1200. I goth driver from ATI download site and ubuntu is version 7,10

I would recommend you use the link below to install the latest driver - Graphics Card Driver.

Else don't bother, and just use the default driver in Ubuntu (which should work just fine).

Do you have a specific need for the latest ATI driver?

---

### Post by davec64 on 2008-02-24
If you do want to rename soemthing the way I do it is in a terminal:

cp <source folder/<source file> <destination folder>/<Destination file>

cp actually stands for copy, so in the example above you're copying a files from a source and renaming it to what you set as  your destination. If a destination file of that name exists in that location, it gets over written.

So if you did it for the backup of xorg.conf it would replace your current xorg.conf.

Hope that makes sense!  :)

---

