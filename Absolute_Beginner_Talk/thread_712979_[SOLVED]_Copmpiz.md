---
title: "[SOLVED] Copmpiz ??"
date: 2008-03-02
forum: Absolute Beginner Talk
---

### Post by jbalazs on 2008-03-02
I have set up compiz but wen I try to turn  it on I get this

[IMG]http://i5.photobucket.com/albums/y176/foxhunter2/Screenshot.png[/IMG]

---

### Post by northern lights on 2008-03-02
Can you post the output of ```
lspci -v | grep VGA
``` Thank you.

By the way, compiz is running on your comp already...

---

### Post by jan quark on 2008-03-02
what is your graphic card?

please post the results of these terminal commands to detect your graphic card
```

lspci
```
```

sudo lshw -C display
```

if you have an Ati card try the following:
```

sudo apt-get install xserver-xgl
```

and then change to xclient session during the login

---

### Post by jbalazs on 2008-03-02
foxhunter@foxhunter-laptop:~$ lspci -v | grep VGA
01:05.0 VGA compatible controller: ATI Technologies Inc Radeon XPRESS 200M 5955 (PCIE) (prog-if 00 [VGA])
foxhunter@foxhunter-laptop:~$

---

### Post by northern lights on 2008-03-02
> **jan quark said:**
> 
```

sudo apt-get install xserver-xgl
```

and then change to xclient session during the login

Try Jan's suggestion.
Otherwise, check [https://answers.launchpad.net/ubuntu/+question/12823]("https://answers.launchpad.net/ubuntu/+question/12823")
[http://https://answers.launchpad.net/ubuntu/+faq/17]("http://https://answers.launchpad.net/ubuntu/+faq/17")

---

### Post by owbizi on 2008-03-02
What's your graphics card, please? And did you successful enabled it before?

edit: woops, too late, hah... anyway, I have a X1300 and didn't have to install xserver-xgl, only the drivers on ATI's website.

---

### Post by jbalazs on 2008-03-02
Thanks guys it's working now this command did it

sudo apt-get install xserver-xgl

---

