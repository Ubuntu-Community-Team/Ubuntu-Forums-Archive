---
title: "Command to set master volume to max?"
date: 2008-02-08
forum: Absolute Beginner Talk
---

### Post by disappearedng on 2008-02-08
HI everyone.
I am used to using my computer to wake me up in the morning but everynight when I sleep watching movies, I automatically mute the volume in Totem. SO is there any command where I could set the volume in Totem or the master volume so that my Kalarm can execute in the morning before the actual alarm? Any help will be appreciated.

---

### Post by Dr Small on 2008-02-08
How about:
```
amixer set PCM 100%
```

I knew I had that command somewhere ;)

---

### Post by disappearedng on 2008-02-08
Thx man
However, I still have one tiny problem,

Under "enter a script" in K alarm,
I don't know how to input multiple commands in a script.

I want to do the following:
Totem /~mysong
amixer set PCM 100%

What are the notations to set them apart and tell K alarm that these are two separate commands?

---

### Post by Dr Small on 2008-02-08
Try this:
```
amixer set PCM 100% ; totem /~mysong
```

---

### Post by emarkd on 2008-02-08
Dr Small's advice should work fine in this case, but if you're interested in learning a bit of shell scripting for future reference or if you wanted to add more functionality to your simple script you've already got started, check out this link:  [http://tldp.org/LDP/abs/html/](http://tldp.org/LDP/abs/html/)

---

### Post by Dr Small on 2008-02-08
> **emarkd said:**
> Dr Small's advice should work fine in this case, but if you're interested in learning a bit of shell scripting for future reference or if you wanted to add more functionality to your simple script you've already got started, check out this link:  [http://tldp.org/LDP/abs/html/](http://tldp.org/LDP/abs/html/)
Yeah, I had to go digging for my shell script that basically did the same thing with cronjobs ;)

---

### Post by disappearedng on 2008-02-08
Thanks a lot for the quick response: 
I have written this script but only to realize another problem:
When i sleep, I have the habit of turning the Totem volume down.
SO even if I execute my animixer to set to full, 
I still don't get much sounds coming from my Totem player.

So i looked up Totem and realize that there's a command 
"totem --volume-up"

so i began writing this:
amixer set Master 100%;
amixer set PCM 100%;
totem /media/sdb1/Songs/Rap/2Pac\ Discography\ \[2007\]/\[1998\]\ Greatest\ Hits/2Pac\ -\ 205\ -\ Changes.mp3;
totem --volume-up;
totem --volume-up;"

However, the totem --volume-up is only executed AFTER totem /~mysong. Is there anyway I can build in volume-up into my 2pac Changes while executing it? 
Thx a lot guys

---

### Post by Gen2ly on 2008-02-08
The variable can often be used in the command line as the one that directs what song is played.

---

### Post by Dr Small on 2008-02-08
Maybe this?
```
amixer set Master 100%;
amixer set PCM 100%;
totem --volume-up;
totem /media/sdb1/Songs/Rap/2Pac\ Discography\ \[2007\]/\[1998\]\ Greatest\ Hits/2Pac\ -\ 205\ -\ Changes.mp3
```

---

### Post by disappearedng on 2008-02-08
Concerning this:
"amixer set Master 100%;
amixer set PCM 100%;
totem --volume-up ;
totem /media/sdb1/Songs/Rap/2Pac\ Discography\ \[2007\]/\[1998\]\ Greatest\ Hits/2Pac\ -\ 205\ -\ Changes.mp3;"

It is not working because when totem --volume-up is applied, the Kalarm waits until totem is shut then it will procced onto playing my song. 

I thought of using 
totem /~mysong -&
totem --volume-up; 
But then the shell wouldn't even execute. What should I do?

---

### Post by macogw on 2008-02-08
why not 
```

amixer set Master 100%;
amixer set PCM 100%;
totem --volume-up /media/sdb1/Songs/Rap/2Pac\...mp3
```

---

### Post by disappearedng on 2008-02-08
Are there references where I can dig deeper into this? 
Is it possible that I write a file to be executed?

---

### Post by disappearedng on 2008-02-08
Unfortunately, 

totem --volume-up /media/sdb1/Songs/Rap/2Pac\ Discography\ \[2007\]/\[1998\]\ Greatest\ Hits/2Pac\ -\ 205\ -\ Changes.mp3 

does not work because volume-up applies only to an opened totem

---

### Post by gyterpena on 2008-03-12
I found a workaround for this. Why not have another cron job executing script at the same time as your script for totem with
sleep 10
export DISPLAY=:0
totem --volume-up
totem --volume-up

found a better solution
#!/bin/bash
export=DISPLAY:0
totem /media/STORAGE/..... 2>&1 &
sleep 2
totem --volume-up 2>&1 &
totem --volume-up 2>&1 &

---

