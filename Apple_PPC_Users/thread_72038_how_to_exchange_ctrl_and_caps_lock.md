---
title: "how to exchange ctrl and caps lock"
date: 2005-10-05
forum: Apple PPC Users
---

### Post by craks on 2005-10-05
i want to exchange the ctrl and caps_lock's positions, so i do the followings:
cat .Xmodmap_ctrl_caps
remove Lock = Caps_Lock
remove Control = Control_L
keysym Control_L = Caps_Lock
keysym Caps_Lock = Control_L
add Control = Control_L
add Lock = Caps_Lock

add add 
xmodmap .Xmodmap_ctrl_caps in the .xinitrc

but the result is ctrl becomes caps_lock, but caps_lock is nothing.

anything i am wrong?

---

### Post by open_flax on 2005-10-05
hello 
you can use the comand showkey. infact this prog show a keycode onput in kernel and you know a number of keycode so you can change.
:)

---

### Post by craks on 2005-10-05
if i use showkey, it give me two code for one key, for example:
ctrl_l: 0x12 0x9d, what's meaning?

---

### Post by open_flax on 2005-10-05
you use a option -m 
# showkey -m

you have only number 29 when press and relase. you can see a man page where you fond other options.
:)

---

### Post by craks on 2005-10-05
nothing when i press ctrl & caps_lock:(

---

