---
title: "Ubuntu shuts down to a black screen"
date: 2007-06-23
forum: Absolute Beginner Talk
---

### Post by Dani Filth on 2007-06-23
Hello all

I'm totally new to this forum and I'm a noob to Ubuntu as well, thus, please forgive me if I'm asking at the wrong place :(

-I ordered the free CD from Ubuntu, After I got it, I installed Ubuntu on my laptop. All these things were done without any errors (as far as I can see the progress displays).

-The problem now occurs : after the first time running Ubuntu and update all the stuffs (it said that update was successful), whenever I restart the computer, everything closes, the monitor remains totally black, then, nothing happens afterwards, (the power is on, the hard disk keeps spinning...). Then I have to manually press the 'OFF' button on my computer to force it switched off, after that, switch it on again. But when I logged in, nothing states like there is any errors.

This problem keeps appearing even after several times I tried to deleted everything (after backing-up, of course) and install Ubuntu again.

Would anyone please help me to solve this problem ?
Thanks in advance :D

---

### Post by bodhi.zazen on 2007-06-23
I moved this and changed the title hoping it will get a little more visibility here :)

Please, what version of Ubuntu, and when you say update, did you update from Dapper to Edgy ?

---

### Post by Dani Filth on 2007-06-23
Thanks bodhi.zazen.
Sorry for being unclear.

My Ubuntu version is 7.04.
By saying 'update' I mean the first time when Ubuntu started, a pop-up message appeared on the screen suggested you to 'get the latest update' (or something similar).

Well, it's not really 'boots', 'closes' or 'shuts down' would be more precise word. 
In details, my problem is :
-After the first time I installed and performed the aforementioned 'update'. Everything went well at this time.
-However, the next time onwards when I clicked on the 'restart' button, everything closed, the screen flashed several times, Ubuntu logo appeared, the orange bar moved to its end. I waited for a while but the monitor remained utter black. Then I had no choice but to manually turn the computer off and turn it on again.

Only the 'restart' has error, the rest seems fine.

I hope I describe it clear enough :D

---

### Post by james1978 on 2007-06-23
hey dani   im also new to ubuntu  and would like to say   im a huge cradle fan   lol    not much help  but  thought ide say hi :p

---

### Post by bodhi.zazen on 2007-06-23
Oh, my mistake then

So it shust down to a black screen but you computer does not power down ?

I'll change the titile ...

This is not as big a problem, more or an annoyance ?

---

### Post by Regel on 2007-06-23
What's the output of
```
sudo update-java-alternatives -l
```?

---

### Post by Dani Filth on 2007-06-23
> **Regel said:**
> What's the output of
```
sudo update-java-alternatives -l
```?

Its out put is :
> alexilaiho@alexilaiho-laptop:~$ sudo update-java-alternatives -l
Password:
sudo: update-java-alternatives: command not found


---

