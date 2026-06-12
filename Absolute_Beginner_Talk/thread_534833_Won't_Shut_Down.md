---
title: "Won't Shut Down?"
date: 2007-08-25
forum: Absolute Beginner Talk
---

### Post by wuzuptravman on 2007-08-25
I am really new to Ubuntu, the first time I used it was like 3 weeks ago. Well now I have managed to get it installed on my computer and it runs much more smoothly than windows from what I've seen. But I have one problem: When I go to shut it down, It goes to a screen that looks just like the Ubuntu boot screen, except the bar is going the other way. When the bar goes completely black it just sits there, It never powers off until I hit the button. I never had to do this in Windows. PLZ help!

---

### Post by southernman on 2007-08-25
Are you using Dapper (6.06) or Feisty (7.04)?

I've never seen that with Feisty, but my Dapper server does this.

---

### Post by Majorix on 2007-08-25
I believe there most likely is an option for that in the preferences. Does it do that with every clean install? If not what I am thinking is almost for sure.

---

### Post by psycardis on 2007-08-26
Mine does the same thing, I am running fiesty. The exception being that sometimes it does not even show the loading screen just blank.

---

### Post by wuzuptravman on 2007-08-26
I'm running Feisty

---

### Post by confused57 on 2007-08-26
You could try:
```
sudo gedit /etc/modules
```

add this to the end of the file:

```
apm power_off=1
```

---

### Post by r4ik on 2007-08-26
Try,

sudo shutdown -h now

In the terminal.

---

### Post by R0B071CxN1NJ4 on 2007-08-26
ctrl + alt + backspace :)

---

### Post by por100pre1 on 2007-08-26
> **R0B071CxN1NJ4 said:**
> ctrl + alt + backspace :)

That only restarts X. To turn off:

```
sudo shutdown -h now
```

---

