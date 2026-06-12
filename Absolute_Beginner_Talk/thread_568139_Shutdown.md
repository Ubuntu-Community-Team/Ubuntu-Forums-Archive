---
title: "Shutdown"
date: 2007-10-05
forum: Absolute Beginner Talk
---

### Post by Darkblizz on 2007-10-05
When i shutdown my computer it just freezes at the shutdown screen in Ubuntu any clue on how to fix this problem?  Restart works startup works fine just the shut down process gets the last of the bar when shutting down and freezes!

---

### Post by sumguy231 on 2007-10-05
It sounds like ACPI support is not working for your computer. How old is it? If it is prior to 2000, you might try the acpi=force boot option to force it to work:
[https://wiki.ubuntu.com/BootOptions?highlight=%28boot%29%7C%28option%29](https://wiki.ubuntu.com/BootOptions?highlight=%28boot%29%7C%28option%29)

Also check your bios settings and make sure ACPI is enabled, and if your BIOS has an "OS Type" option, try changing it from Windows to Other.

Even if you don't get it working, at that point you should be able to safely press the power button to turn it off. It's like the "It's now safe to turn off your computer" screen in Win95.

---

### Post by Darkblizz on 2007-10-05
No the computer is rather new only about 2 years id say.  I dunno whats the matter and i dont get a screen that says its say to turn it off lol

---

### Post by Darkblizz on 2007-10-05
It was on and there is no option for os type

---

