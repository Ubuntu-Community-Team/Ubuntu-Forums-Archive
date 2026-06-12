---
title: "I'm a noob/wheres my shutdown gone!"
date: 2007-03-09
forum: Absolute Beginner Talk
---

### Post by gamer91 on 2007-03-09
Hi, as you may have guessed I'm new, currently running edgy and loving it so (dual boot with xp, ftw).
When I click the shutdown icon (top right) i do not get the shutdown or restart option, what has gone wrong?

I have tryed to download drivers for my graphics card but I don't know what to do with the *.run file

p.s. whats with the coffee beans ^^^

---

### Post by Aberrix on 2007-03-09
have you tried automatix for your video card drivers? 100x easier.

---

### Post by ComplexNumber on 2007-03-09
> **gamer91 said:**
> Hi, as you may have guessed I'm new, currently running edgy and loving it so (dual boot with xp, ftw).
When I click the shutdown icon (top right) i do not get the shutdown or restart option, what has gone wrong?

I have tryed to download drivers for my graphics card but I don't know what to do with the *.run file

p.s. whats with the coffee beans ^^^
it appears that gdm is not running. when you logged in, was it a text console?


the beans are nothing more than post count.

---

### Post by jhenager on 2007-03-09
Try doing CTRL+ALT+Backspace to restart X. 

What - you a tea drinker or something?

---

### Post by gamer91 on 2007-03-09
> **jhenager said:**
> Try doing CTRL+ALT+Backspace to restart X. 

What - you a tea drinker or something?

well yes, but anyways, when I click the icon i just get options like log out, hibernate, suspend etc. but shutdown is missing.

---

### Post by gamer91 on 2007-03-09
> **ComplexNumber said:**
> it appears that gdm is not running. when you logged in, was it a text console?

I was using the blue swirl theme - could it be to do with this?

---

### Post by kanha on 2007-03-09
> **gamer91 said:**
> I was using the blue swirl theme - could it be to do with this?

that blueswirl theme have some bugs
I also faced problem.then after 1 or 2 install was able to log back and then changed that screen

---

### Post by King Donko on 2007-03-09
Sorry, I didn't see the rest of your message. I'm new here myself.

---

### Post by gamer91 on 2007-03-10
I have removed blue swirl although still have the same problem - any help?

---

### Post by Famicommie on 2007-03-10
I can't offer you the precise solution that you're seeking, but ever since I installed Beryl I lost those buttons and have discovered a few workarounds. My favorite is shutting down/restarting through the terminal.

To shutdown, open up a terminal and type:
```
sudo shutdown -h now
```

To restart:
```
sudo shutdown -r now
```

For more info, open a terminal and type:
```
info shutdown
```

If you don't know how to read an info file, then open up a terminal and type
```
info info
```
to take a quick tutorial.

---

### Post by derrick81787 on 2007-03-10
Are you possibly using Xgl and Compiz? When I ran Dapper with Xgl and Compiz, I had this exact same problem and never did know what to do about it. I'm running Beryl AIGLX on edgy right now though, and I no longer have this problem.

---

### Post by enopepsoo on 2007-03-10
> **gamer91 said:**
> well yes, but anyways, when I click the icon i just get options like log out, hibernate, suspend etc. but shutdown is missing.

you should try coffee, it is a lot better than tea.:guitar:

---

