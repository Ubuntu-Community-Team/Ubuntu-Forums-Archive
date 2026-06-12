---
title: "install programs outside of add/remove"
date: 2007-03-14
forum: Absolute Beginner Talk
---

### Post by travm on 2007-03-14
How do i install sotfware that i cant find in the add/remove program?  
I want to install mythtv, but im kinda confused.  I never put in a root password.  can I manually install software as a user?
I want to install mythtv, and im also kind of lost on how to install the correct drivers for my video card.  it is a voodoo 3 3500 TV.  I believe it needs a special driver, right now all i can get to work is vesa.

I believe i need to install this, but the instructions are over my head, compiling a kernel?  just for the driver? 
If anyone could help me translate that installation guide or suggest what i need to do to get my video card working properly (video in, tv-out, 3d-accel) it would be appreciated

---

### Post by aysiu on 2007-03-14
I don't know anything about your video card, but you can install MythTV through the repositories.

**Step 1**:
[Enable extra repositories](http://www.psychocats.net/ubuntu/sources)

**Step 2**: 
Paste this command in [the terminal](http://www.psychocats.net/ubuntu/terminal): ```
sudo aptitude update && sudo aptitude install mythtv
```

---

### Post by travm on 2007-03-14
ok, i think i installed mythv properly, but it doesnt work.  I guess i have some reading to do.  I do need to get the drivers figured out, so anyone who can help me with that.

---

### Post by majoridiot on 2007-03-14
this is a great place to start:

[https://help.ubuntu.com/community/MythTV](https://help.ubuntu.com/community/MythTV)

---

