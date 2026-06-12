---
title: "H-positioning problem"
date: 2008-01-02
forum: Absolute Beginner Talk
---

### Post by Walc on 2008-01-02
Hello every1

First of all, id like to say hi to this great community, i hope that with time i will serve some help as well, but first gotta get thru teh n00b period....

Im having ubuntu gutsy installed on pc since few days. Now ive noticed that when switching to ubuntu <my other os is vista>, im having issues with h-positioning. Heres the problem: in vista its set on +50 and works sweet, once i switch to ubuntu +50 isnt good anymore, i have to change it manually to +35 or sth near it. 
My graphic card is GF 7600gt, i havent updated my nvidia drivers for linux, and i dunno wheter i even should....i mean dunno if thats the issue here
so i would appreciate an advice here folks
Thx

i enabled visual effects and was asked wheter i do wanna dl the nvidia drivers, which i did. Now the problem seems to be gone too, but theres this notice that this driver<s> arent supported by ubunu...<? > Now help me out guys, where can i snatch the fully supported gf 7600gt driver?

---

### Post by jken146 on 2008-01-02
Did you enable the restricted drivers?  If you did, and that solved your problem, then don't worry about the warning.  It's just telling you that the drivers are closed source software.

---

### Post by leonidas666 on 2008-01-02
> **Walc said:**
> 
switching to ubuntu <my other os is vista>, im having issues with h-positioning. Heres the problem: in vista its set on +50 and works sweet, once i switch to ubuntu +50 isnt good anymore, i have to change it manually to +35 or sth near it. 

I guess with +50 and +35 you mean the number which is displayed on the OSD of your monitor, right? Normally, you monitor should be clever enough to realise that you are running it in two different modes. There should be some way to "save" the setting in you monitor. Start windows, adjust the monitor and use the "save" button on your monitor, and then run linux, adjust the monitor, and then again "save". Then the next time you are running either linux or windows the monitor should pick the right setting by itself. Maybe there is even a "auto mode" for adjustment, you can try to use that also. If you write what kind of monitor you have, maybe somebody who has the same model can write how to operate it in more detail.
Otherwise, you could try to set the resolution and refresh rate of your windows desktop and your linux desktop to exactly the same values. Then, with the same settings in your monitor, the picture display the same.

> **Walc said:**
> 
Now the problem seems to be gone too, but theres this notice that this driver<s> arent supported by ubunu...<? > Now help me out guys, where can i snatch the fully supported gf 7600gt driver?
That's normal, it just means that you are using the binary driver which is not open source. It's a ideological issue, you can ignore it unless you are actually having problems with your graphics card.

---

