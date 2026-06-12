---
title: "Shutdown button locks computer"
date: 2008-01-11
forum: Absolute Beginner Talk
---

### Post by lobo-tuerto on 2008-01-11
Hello guys,


I have a dual screen system at home, and I'm having some problems, If I press the shutdown button on my first screen the shutdown dialog will show, not so in the second screen. If I press the shutdown button in my second screen, I'm not able to click anything in both windows.

I remember it was working before, but I messed with the "Remember currently running applications" (or something like that), and with the "Automatically remember applications when leaving the session", it was duplicating processes when I started my session.

So I deleted the "session" file in ~/.gnome2

And it seems like everything reverted back to normal, except for that little detail.



After reading the forums a bit, I realized that the system isn't truly hanging up, what happens is that the shutdown dialog isn't showing, but it IS there, invisible.
I know this because if I press the "ESC" key I'm able to continue working in the graphical environment.

I have Compiz Fusion and Emerald installed.

Any ideas about this bug?

Any help will be hugely appreciated.



Regards,
Adrián.

---

### Post by nikoPSK on 2008-01-11
please tell me if this locks your pc as well:

```
sudo shutdown -h now
```

---

### Post by lobo-tuerto on 2008-01-11
No it doesn't lock up the computer.

In my post I said it wasn't really locking it up, it was more like the logout or shutdown window was invisible.

And that command just shutted down my computer.

Any ideas?

---

### Post by nikoPSK on 2008-01-11
> **lobo-tuerto said:**
> No it doesn't lock up the computer.

In my post I said it wasn't really locking it up, it was more like the logout or shutdown window was invisible.

And that command just shutted down my computer.

Any ideas?

well, Sorry, can't help anymore. I was just finding out if it was hardware related. 

Best Regards,
nikoPSK

---

