---
title: "Get a Xorg error each time ubuntu boots"
date: 2006-11-16
forum: Absolute Beginner Talk
---

### Post by tarnation on 2006-11-16
ok, I am the same person that posted about not being able to load the live CD, and the idea of using the alternat install disc worked! and thank you to all who sujjested things, but, now I have a new problem.

Each time I boot up ubuntu, it all looks as going well, but, then I get this error that the X server(your graphical interface) could not start,

(EE) No devices detected.
Fatal server error:
no screens found

And thats what I get, I went to the Xorg wiki site, and I found the error, and it essentially said I have the wrong driver for my video card/chipset, and it tried to explain how to fix it, but I am a complete noob and couldn't for the life of me quite grasp what it is saying, so, if someone can help me, I greatly appreciate it.

Thanks!!

---

### Post by taurus on 2006-11-16
Boot into recovery mode from GRUB and at the prompt, reconfigure your X again...

```
dpkg-reconfigure -phigh xserver-xorg
```

---

### Post by tarnation on 2006-11-16
I had already seen that, but, theres one argument I did not put into my line, and i'm curious to know what it does.

I put in 
```
sudo dpkg-reconfigure xserver-xorg
```


and I'm curious to know what the 
```
-phigh
``` 
does.

I'll try it now, but I have already tried reconfiguring it, I think I did it all correct, and I still got the same error 
```
no screens found
```




EDIT* ok, I tried it, and yea, the "-phigh" helped a lot, lol, made it so i didn't have to go through all the other junk a million times. but, I tried reconfiguring it, and it didn't work, it sees my video card, the ATI Radeon RX800, and I'm pretty sure it sees my monitor, but, when I boot up ubuntu, I get the same error message :-(

---

