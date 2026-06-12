---
title: "Keyboard Layout Problems"
date: 2006-07-02
forum: Apple PPC Users
---

### Post by coalquay404 on 2006-07-02
Hi,

I'm running Dapper on an iBook G4 and everything seems to be going swimmingly. However, I'm having difficulty figuring out how to change the keyboard layout to my satisfaction. For example, I use LaTeX an awful lot and would like to swap around the '\' and '/' keys. Also, I'd like to figure out a way to swap the CTRL and Apple keys. Does anybody have any hints on how to do this?

Thanks.

---

### Post by coalquay404 on 2006-07-03
Surely somebody has come across this problem before?

---

### Post by coalquay404 on 2006-07-05
Anybody?

---

### Post by chasisaac on 2006-07-06
Okay hints only 

```
 
Mapping your Apple Key to act as Alt and more:
sudo vi $HOME/.xmodmap (might create a new file, thats ok) and add:

keycode 115 = Alt_L Meta_L
add mod1 = Alt_L Meta_L
keycode 101 = F1
keycode 212 = F2
keycode 160 = F3
keycode 174 = F4
keycode 176 = F5
keycode 214 = F7
keycode 215 = F8
keycode 216 = F9
keycode 217 = F10

```

This is taken from: [http://bin-false.org/?p=17](http://bin-false.org/?p=17)

I have not tried this yet . . . it is on my list of things to do. 

ci

---

### Post by coalquay404 on 2006-07-07
Excellent. Thanks.

---

