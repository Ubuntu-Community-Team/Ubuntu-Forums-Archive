---
title: "CapsLock key doen't work in Ubuntu 7.04"
date: 2007-05-13
forum: Absolute Beginner Talk
---

### Post by abcuser on 2007-05-13
Hi,
I have installed Ubuntu 7.04, but I have recognized that CapsLock does not respond. I have two disk one with Windows and one of Ubuntu, but on Windows CapsLock works fine, so my keyboard is not broken. Any idea what to check?
Thanks,
Abcuser

---

### Post by jkblacker on 2007-05-13
System->Preferences->Keyboard.  Check layouts first, then Layout options. See anything looking dodgy?

---

### Post by mejy on 2007-05-13
Also, what output does 'xev | grep keycode' give if you then hover over the window and press yoru capslock key?

---

### Post by abcuser on 2007-05-14
@mejy output is:
    state 0x0, keycode 66 (keysym 0xfe08, ISO_Next_Group), same_screen YES,
    state 0x0, keycode 66 (keysym 0xfe08, ISO_Next_Group), same_screen YES,

---

