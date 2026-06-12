---
title: "can't input capital letter in terminal(alt+f1)"
date: 2007-05-05
forum: Absolute Beginner Talk
---

### Post by helai on 2007-05-05
Suddently ,i found i can't inpu the capital letter in the terminal activated by ctrl+alt+f1,so it is impossible to input the command ps -A,but it is ok in the current termianl (applications-accessories-terminal),so it is strange
now i am running Ubuntu 7.04 the latest one 
who knows it?
thanks in advance!
helai
________________
thanks for yours reply,now it's ok for using SHIFT+ANY LETTER
because long befor i always simply activate the caps lock then can input capital letter in the terminal,but it's in ubuntu6.1
________________
but the way,how to edit the topic to with SOLVED attached

THANKS AGAIN!
helai

---

### Post by justinlb on 2007-05-05
I ended my session just for you so you better feel special :p. I was able to put capital letters in fine by just using the regular shift+any letter.

---

### Post by meborc on 2007-05-05
> **justinlb said:**
> I ended my session just for you so you better feel special :p. I was able to put capital letters in fine by just using the regular shift+any letter.

why would you need to end your session? ... you just need to ctrl+alt+f1... and then ctrl+alt+f7

on topic - can't reproduce your problem... it might be your keymap issue... what keyboard layout are you using?... try searching google for disabled shift key also... otherwise - i have no clue :)

---

### Post by nixclusive on 2007-05-05
strange indeed!! this may fix your problem: ```
sudo /etc/init.d/console-screen.sh restart
```Try in the F1 screen.

---

