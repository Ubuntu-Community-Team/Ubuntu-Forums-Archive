---
title: "Cube Rotation - Gone"
date: 2007-10-20
forum: Absolute Beginner Talk
---

### Post by mikex on 2007-10-20
Searched but no help so far -

Had cube rotation working under Beryl, Ubuntu upgraded this morning to new version and now Cube won't rotate. I have all Compiz stuff installed. Linux has again proven I am an idiot, so can anyone tell me how to get my Cube rotation to work again?

How many desk tops do I set (H,V, etc)

How do I get the cube to rotate like I had it before, where I simply pressed the middle mouse button on the desktop and it went into cube mode. 

:confused:

---

### Post by 505 on 2007-10-20
Does it rotate when you press the switcher at the bottom of your screen. If not, do the following.
1. Press alt+F2 and type 'metacity --replace'
2. Right clich the desktop switcher, choose preferences, and set the number of desktops to 1
3. Press alt+F2 and type 'compiz --replace'

You should now see four desktop again, and the cube should work.

---

### Post by Paqman on 2007-10-20
> **mikex said:**
> Linux has again proven I am an idiot

Don't be so hard on yourself, your question is [very common](http://compiz.org/FAQ/Users#Why_can.27t_I_get_the_cube_rotation_to_work.3F)

---

### Post by mikex on 2007-10-20
> **505 said:**
> Does it rotate when you press the switcher at the bottom of your screen. If not, do the following.
1. Press alt+F2 and type 'metacity --replace'
2. Right clich the desktop switcher, choose preferences, and set the number of desktops to 1
3. Press alt+F2 and type 'compiz --replace'

You should now see four desktop again, and the cube should work.

Wow - amazing! I have no idea how you know these things, but thanks it seems to have worked.

Q: Why didn't the upgrade set those commands like you just told me?

---

### Post by Wiebelhaus on 2007-10-20
> **505 said:**
> Does it rotate when you press the switcher at the bottom of your screen. If not, do the following.
1. Press alt+F2 and type 'metacity --replace'
2. Right clich the desktop switcher, choose preferences, and set the number of desktops to 1
3. Press alt+F2 and type 'compiz --replace'

You should now see four desktop again, and the cube should work.

hella sweet , I'm not going to try it because I like the sliding effect , but this will help allot of people who do desire the cube.

---

### Post by mikex on 2007-10-20
In the CompizConfig settings manager, what are the Horizontal, vertical, and Number of Desktops sliders for?

---

### Post by kubuntuuser on 2007-10-20
Hi Guys. 
The same has happened to me. I upgraded from feisty to gusty and had cube rotation working with beryl-manager. 

I've tried the method above and it still doesnt work. Instead of seeing 4 desktops I only see 1. 

Anyone got any suggestions? Thanks in advance.

---

