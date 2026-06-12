---
title: "problem on gusty"
date: 2007-12-14
forum: Absolute Beginner Talk
---

### Post by nnamdi on 2007-12-14
hello all
when i click on my power button i dont find the shutdown and restart button which makes me always hibernate all the time how do i fix this

---

### Post by L Campbell on 2007-12-14
> **nnamdi said:**
> hello all
when i click on my power button i dont find the shutdown and restart button which makes me always hibernate all the time how do i fix this

If you mean that the button is hidden away in the top, right corner, you might be able to change your screen resolution and make it appear.

System  -  Preferences  -  Screen Resolution.

---

### Post by elliotjreed on 2007-12-14
Go to Sysetm > Preferences > Power Management (or Control centre > Power Management)

And on the second tab, you should be able to select what the power-off button does!



If you mean the power-button as in, the Ubuntu one on the screen, I have no idea where they gone.

But you could just type:

```
sudo shutdown h- now
```

... or replace 'now' with the number of minutes until you want shutdown. Eg:

```
sudo shutdown -h 10
```

---

