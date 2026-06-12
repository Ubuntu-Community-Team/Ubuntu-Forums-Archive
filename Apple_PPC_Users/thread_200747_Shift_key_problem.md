---
title: "Shift key problem"
date: 2006-06-20
forum: Apple PPC Users
---

### Post by cholguin on 2006-06-20
This is a little silly but is really bugging me. I have a Powerbook G4 867mHz, i have a normal user and made a root account that can login at the gdm login manager.

Basically the root account works perfectly on regards to the keyboard, but the user account when i am typing on the shell or anyother program were i use the keyboard shift key does not work, i try to do a shift+a to get a A and it does not type anything, but if i use caps lock and then do a shift+A to get an a it does work.

I tryed changing the layouts but it does nothing, and the funny thing is that in the root account it works great.

Please help!!!!!!!!!!

---

### Post by macheadPDX on 2006-06-21
Do you run gdesklets? I notice that when I run gdesklets my shift key won't work properly...

---

### Post by macheadPDX on 2006-06-21
Just found the solution from some post... But here is what I did... In terminal

```
gdesklets configure
```

In the resulting window change the "Key for toggling Float Mode" setting (which by default is Shift-F12) to another key.

Goodluck!

---

### Post by cholguin on 2006-06-26
Thanks for the reply, yes i am running the gdesklets, i will try it and let you know, 

Thanks and God bless

---

### Post by devoinregress on 2006-08-26
i am having the same problem. did the gdesklet config but that didn't work. might it be an issue with the mac keyboard mapping?

---

### Post by devoinregress on 2006-08-27
My bad. It was gdesklets. Editing the prefrences didn't work for me though. just got to live with out them for a while then.

---

### Post by truantology on 2006-12-23
worked like a ChArM!!! <- note the use of caps?

TY!!

---

