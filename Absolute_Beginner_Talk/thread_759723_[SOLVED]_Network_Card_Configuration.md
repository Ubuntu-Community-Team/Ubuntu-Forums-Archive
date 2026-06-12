---
title: "[SOLVED] Network Card Configuration"
date: 2008-04-19
forum: Absolute Beginner Talk
---

### Post by Dumpy Dumpster on 2008-04-19
Frustration!!
I have installed 'Configure Network Card' and a Realtek 8139 is in place.  When I go to 'Configure Network card' a message appears saying 'sudo first'   What do I sudo?
Am I very naive, but surely if someone takes the trouble to write such a tip, why cannot they just say what to do?
Thanks for any help - I certainly need it

---

### Post by anjilslaire on 2008-04-19
when you are prompted for sudo, give it your password

---

### Post by Dumpy Dumpster on 2008-04-19
Thanks anjilslaire, it really is simple when explained.  I will give it a go after supper!

---

### Post by Dumpy Dumpster on 2008-04-19
Sorry, but the previous reply simply does not work.
The window I referred to does not have a facility to type into.
So I go to terminal, type in 'sudo' and it basically says - so what!
What I ask is simply how top connect a Livebox ethernet to Ubuntu (and please no comments on the quality of Livebox - it comes with the deal I have)  
I surely cannot be the first to try this but getting information is becoming a real hassle.

---

### Post by ugm6hr on 2008-04-19
I'm not quite sure exactly what you are trying to achieve.

You have a wired ethernet connection, right?

Not sure what Livebox is - perhaps you could elucidate...

What is your networking setup?

It would be helpful to confirm that the ethernet driver is installed:

```
lshw -C network
```

The more information you give, the more likely we are likely to be abke to help.

---

