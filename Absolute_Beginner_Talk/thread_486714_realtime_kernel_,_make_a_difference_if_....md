---
title: "realtime kernel , make a difference if ..."
date: 2007-06-28
forum: Absolute Beginner Talk
---

### Post by firedancer on 2007-06-28
will installing/using the realtime kernel help 

i 'm into recording, i need to upgrade my pc , but rite now i can't 

so , i can record a track in audacity , but trying the next would make it jump, having problems with other words 

i record realtime no midi , so ...


tried with dyne , but similar problem 

i'm trying to get a m-audio 66 too, mine just is not good enough 



rite now i have a intel desktop with celeron which ofcourse is not recommended
but how can i record realtime , say three tracks behind each other  , or do i need to wait until santa comes and give me duo 2 core and the maudio 66 


ppppfffffff:cry:

---

### Post by Seisen on 2007-06-28
What do you mean by realtime kernel?

---

### Post by firedancer on 2007-06-28
i hav the low-latency kernel now , but if i'm not mistaking i read about a realtime kernel it's only if you do music/audio recordings




maybe i should psot the Q somwhere else , but once one was removed when i posted it in the multimedia production section

---

### Post by Seisen on 2007-06-28
I think this what you are talking about

[http://ubuntuforums.org/showthread.php?t=441366]("http://ubuntuforums.org/showthread.php?t=441366")

See you learn something new every day.

You can try it, personally I have never tried so I don't know how well it works.

---

### Post by firedancer on 2007-06-28
yes, 


but i don't wanna try it , i wanna know if it would make a difference , 


or maybe i should just do , 

i'm happy now with my sys after a month of tuff learning , but my musical inspirations kind of go to waste .... so that's why the Question


is there a ubuntu studio forum ? maybe i can ask there

---

### Post by firedancer on 2007-06-28
my 45 line is line is wrong       deb-src should be the 46 line 

> deb [http://www.texware.it/ubuntu](http://www.texware.it/ubuntu) feisty/ deb-src [http://www.texware.it/ubuntu](http://www.texware.it/ubuntu) feisty/


so i can't update from their repo and install the realtime


but how do i edit this as root , cause i can't login my root account anymore 

so i have to edit  and save it from terminal after crlt+alt+F1 , but how ?

---

### Post by firedancer on 2007-06-28
anyway:(

---

### Post by Seisen on 2007-06-28
> **firedancer said:**
> my 45 line is line is wrong       deb-src should be the 46 line 




so i can't update from their repo and install the realtime


but how do i edit this as root , cause i can't login my root account anymore 

so i have to edit  and save it from terminal after crlt+alt+F1 , but how ?

Go into the terminal and put this in

```
gksudo gedit /etc/apt/sources.list
```
there you can edit your source list.

---

### Post by firedancer on 2007-06-28
can't even acces  it with gksudo 

saw and update and can't update

i messed up

---

### Post by Seisen on 2007-06-28
try vim 

```
sudo vim /etc/apt/soruces.list
```

```
Shift+I 
```will let you write to the file[/CODE]

when your done editing the file
```
:wq
``` will save the file and close it out

then do the 
```
sudo apt-get update
```

---

### Post by firedancer on 2007-06-28
thanx alot ;)

---

### Post by Seisen on 2007-06-28
I am assuming it work this time.

---

### Post by firedancer on 2007-06-28
love you guys /gals :D

yes, yes, yes


still have to try wether it will make a difference in my situations , but at least i can try that now ,

---

