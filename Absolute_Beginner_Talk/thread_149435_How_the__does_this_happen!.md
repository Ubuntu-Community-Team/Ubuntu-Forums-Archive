---
title: "How the **** does this happen?!?"
date: 2006-03-23
forum: Absolute Beginner Talk
---

### Post by Papa-san on 2006-03-23
```
john@laptop:~$ sudo modprobe -r bcmwl5 FATAL: Module bcmwl5 not found.
john@laptop:~$ sudo modprobe -r bcmwl5a FATAL: Module bcmwl5a not found.
john@laptop:~$ sudo ndiswrapper -i ~/Desktop/bcmwl5.inf bcmwl5 is already installed. Use -e to remove it
john@laptop:~$ sudo modprobe -r bcmwl5a.inf
FATAL: Module bcmwl5a.inf not found.
john@laptop:~$ sudo modprobe -r bcmwl5.inf
FATAL: Module bcmwl5.inf not found.
john@laptop:~$ sudo ndiswrapper -i ~/Desktop/bcmwl5.inf
bcmwl5 is already installed. Use -e to remove it
john@laptop:~$ sudo modprobe -r bcmwl5.inf
FATAL: Module bcmwl5.inf not found.
john@laptop:~$ sudo ndiswrapper -i ~/Desktop/bcmwl5.inf
bcmwl5 is already installed. Use -e to remove it

```

---

### Post by Papa-san on 2006-03-23
I obviously cannot understand the way the modules and drivers work together...

This error (perceived error?) has been plaguing me since day one...:
```

john@laptop:~$ sudo modprobe -r bcmwl5.inf
FATAL: Module bcmwl5.inf not found.
john@laptop:~$ sudo ndiswrapper -i ~/Desktop/bcmwl5.inf
bcmwl5 is already installed. Use -e to remove it
```
Like it is telling me it is there, but it is not there, at the same time... Am I thinking wrong again, and this isn't the case or what?

I'm gonna die of old age before I get my wireless working!

---

### Post by conbrio on 2006-03-23
Hey there, 

I am a n00b but maybe I can help with your wireless problem seeing as I had a very similar problem.

first 
> sudo apt-get install ndiswrapper-utils
wget [http://christer.homeip.net/bcmwl5.inf](http://christer.homeip.net/bcmwl5.inf)
wget [http://christer.homeip.net/bcmwl5.sys](http://christer.homeip.net/bcmwl5.sys)
sudo ndiswrapper -i bcmwl5.inf
sudo ndiswrapper -l (thats L)

Then lets try and get rid of the old drivers by and try the new one by 
sudo ndiswrapper -e bcmwl5
sudo ndiswrapper -i bcmwl5.inf

see if that helps

---

