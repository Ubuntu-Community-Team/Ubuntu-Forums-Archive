---
title: "xserver has crashed!! please help!!"
date: 2007-03-06
forum: Absolute Beginner Talk
---

### Post by the_nomad on 2007-03-06
i have lately installed the nvidia driver... ok everything had been good with one exception: screen had started to freeze, everything i could make was to move the mouse; i reviewed the articles about installing the nvidia driver and i found in problems section about my problem and how to solve it; ok so, i did what i had to do but still, same problem; everything i was actually alowed to do was to reset the computer, though i knew that's gonna be very bad and very soon!! and i was right! here we get to my problem: when i boot into linux, it loads all those necessary programs or whatever they are (those one shown below that ubuntu logo) and when tries to load that login screen i get an error that says that is likely that xserver isn't set up correctly.

i tried through
```
sudo dpkg-reconfigure xserver-xorg
```, i went through all those setups but still, the same problem with xserver! so, PLEASE if you can tell what the problem would be and how do i solve it i'd be very very thankful!


thanx in advance.

---

### Post by r4ik on 2007-03-06
press Control-Alt-F1 and try

sudo dpkg-reconfigure xserver-xorg

Follow the defaults,

Set you're video driver to nv

finish with,

sudo /etc/init.d/gdm start

---

### Post by the_nomad on 2007-03-07
ok, so i've done everything you said and in the end when i try to start gdm i get 
```
starting gnome display manager...          fail
```

---

### Post by the_nomad on 2007-03-07
anybody? please?

---

### Post by the_nomad on 2007-03-08
ok it finally worked :) thanx.. i thought i'll have to reinstall it :)

---

### Post by fairmeadow on 2007-03-08
What did you do to make it work?   I have the same problem.

regards
Bob

---

### Post by tjk on 2007-03-08
I have just posted a new thread similar to this problem, so if you would describe your solution it may help me with my predicament.

---

