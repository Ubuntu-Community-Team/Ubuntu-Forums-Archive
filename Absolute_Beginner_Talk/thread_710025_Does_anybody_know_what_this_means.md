---
title: "Does anybody know what this means?"
date: 2008-02-28
forum: Absolute Beginner Talk
---

### Post by Scut_Farkus on 2008-02-28
I get this message when trying to run Update Manager.  

[HTML]E: tzdata: subprocess post-installation script returned error exit status 9[/HTML]

Thanks!

---

### Post by JoshuaRL on 2008-02-28
Could you try from the terminal?
```

sudo apt-get update
sudo apt-get upgrade

```

And then post any errors.

---

### Post by Scut_Farkus on 2008-02-28
Thanks, I'd love to but I'm not sure how to do this if I can't see any of my icons anymore.  I rebooted to see if that might help things, but all it did was screw up my desktop.  The only thing I can see now is the standard background screen.  There are no icons to click on.

---

### Post by az on 2008-02-28
[https://help.ubuntu.com/community/FaultyHardware](https://help.ubuntu.com/community/FaultyHardware)

Can you use the live cd to check your hardware?

---

### Post by Joeb454 on 2008-02-28
Are the panels there at the top and bottom of the screen?

---

### Post by sumguy231 on 2008-02-28
Press Ctrl+Alt+F1 to get to a text-only terminal and Ctrl+Alt+F7 to get back.

---

### Post by Scut_Farkus on 2008-02-28
> **az said:**
> [https://help.ubuntu.com/community/FaultyHardware](https://help.ubuntu.com/community/FaultyHardware)

Can you use the live cd to check your hardware?

Hey!  Very cool set of tests!  Thanks very much.  I DID run MEMTEST86, but only for an hour.  I'll run it overnight just for grins.

I also ran a badblocks test and it came through just fine, but I'll see about the SMART tests, too.

---

### Post by Scut_Farkus on 2008-02-28
> **Joeb454 said:**
> Are the panels there at the top and bottom of the screen?

Nope.  No panels.  Truly...the ONLY thing I see is the background.

I DO see the panels when the system is first booting up.  When it's finished, the panels (and all associated buttons and launchers) disappear.

---

### Post by Scut_Farkus on 2008-02-28
> **sumguy231 said:**
> Press Ctrl+Alt+F1 to get to a text-only terminal and Ctrl+Alt+F7 to get back.

GAH!  I'm an idiot.  I had forgotten that simple step.  I didn't even try it yet to see if I can get to a terminal.  Thank you!

I'm also an idiot for not simply answering all these questions in one post.  Apologies for making this thread larger than it needs to be.

---

