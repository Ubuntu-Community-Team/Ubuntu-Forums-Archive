---
title: "need a bit of help"
date: 2007-04-09
forum: Absolute Beginner Talk
---

### Post by jrcullen007 on 2007-04-09
i just got ubuntu and installed it at a friends and it worked fine. but now its at home i have gotten a bit of a problem. it starts loading unbuntu fine then when it gets to the sign in page all it say on my monitor is out of range. my friend told me this is because my resolution is too high. he then told me to try out on here to get help for it sorta the old motto teach a man to fish. anyways he said to use the live disk and set up the hard drive on it and change the settings for res that way. i need a little bit of help any one know how to do this let me know need kinda step by step instructions thanks

---

### Post by heimo on 2007-04-09
Hit ctrl+alt+F1 to get to a virtual console (command line interface), log in, shut down gdm:
```
sudo /etc/init.d/gdm stop
```

Run dpkg-reconfigure using these instructions:
[https://help.ubuntu.com/community/FixVideoResolutionHowto](https://help.ubuntu.com/community/FixVideoResolutionHowto)

Restart gdm:
```
sudo /etc/init.d/gdm start
```

Not working? Repeat. :)

---

### Post by jrcullen007 on 2007-04-09
still didn't work tried all of them just came up saying command not found its ubuntu 6.10 does that mean i have to do something different i am soo lost

---

### Post by meborc on 2007-04-09
command not found means you have made a spelling error :)

just try to run ```
sudo dpkg-reconfigure xserver-xorg
```
keep the default answers to the ones you are not sure of... 

try again with correct commands... spelling with CAPS does not work!

---

### Post by wj32 on 2007-04-09
Which command isn't found?

BTW: no need for the crying icon, we're here to help :)

---

### Post by jrcullen007 on 2007-04-09
i tired that and i had my spelling right but still didn't work

---

### Post by jrcullen007 on 2007-04-09
any of the xorg ones can't be found

---

### Post by jrcullen007 on 2007-04-09
shutting down the gdm works fine but all the other command lines i got off here just are not working

---

### Post by wj32 on 2007-04-09
Huh? That's a bit weird. Try and post the exact error message when you get the error.

---

### Post by jvc26 on 2007-04-09
Right, when you boot up and it starts saying out of range, CTRL+ALT+F1 will drop you into a text console. Can you get the:
```

sudo dpkg-reconfigure xserver-xorg

```
To work from there? I'm not sure why it can't find the command.
Il

---

