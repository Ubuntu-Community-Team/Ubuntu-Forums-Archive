---
title: "Which java variation do I download from sun?"
date: 2006-12-12
forum: Absolute Beginner Talk
---

### Post by some_random_noob on 2006-12-12
[http://java.com/en/download/manual.jsp](http://java.com/en/download/manual.jsp)

- Thanks in advance :) 

... Btw I've totally nailed most of my problems today and having lots of fun :D

---

### Post by nickburns on 2006-12-12
Go to a terminal and:

sudo apt-get install sun-java5-jre

---

### Post by some_random_noob on 2006-12-12
Damn. that is not a small file! :eek: Don't they have this stuff on the install disk?

---

### Post by nickburns on 2006-12-12
I don't think so, you'll have to make a big pot of coffee and pass the time.

---

### Post by some_random_noob on 2006-12-12
This sucks, I still can't play runescape!!!! ](*,) 

Runescape is an advanced java game for those who don't know, is it just too advanced or am I doing something wrong? Any simple java applets I could test? I'm now wondering if I should download one of the other java thingys from suns website that I mentioned at the start. Help please :confused:

---

### Post by igknighted on 2006-12-12
> **some_random_noob said:**
> This sucks, I still can't play runescape!!!! ](*,) 

Runescape is an advanced java game for those who don't know, is it just too advanced or am I doing something wrong? Any simple java applets I could test? I'm now wondering if I should download one of the other java thingys from suns website that I mentioned at the start. Help please :confused:

Does it need java3d?  I think those libraries are seperate from the jre, although maybe thats just for the jdk.  try running the game from the terminal and seeing if you get any error messages that you can post here.

---

### Post by kd7swh on 2006-12-12
you can use the linux .bin file and run it in the terminal if you don't want to use synaptic

---

### Post by nickburns on 2006-12-12
You can do what kd7swh suggests, you can download the .bin file and:

sudo chmod 777 thebinfile.bin

then 

sudo ./thebinfile.bin



But I am sure you can run it with what you can get it off the repos,
what are you doing to start the program? are you starting it off of command line? what command are you using?

---

### Post by igknighted on 2006-12-12
> **some_random_noob said:**
> This sucks, I still can't play runescape!!!! ](*,) 

Runescape is an advanced java game for those who don't know, is it just too advanced or am I doing something wrong? Any simple java applets I could test? I'm now wondering if I should download one of the other java thingys from suns website that I mentioned at the start. Help please :confused:

wait... is it an online game?  You might need to install the browser plugin as well
```
sudo apt-get install sun-java5-plugin
```

Also, are you using the AMD 64 version?  There are some special steps you must take if you are.

---

### Post by some_random_noob on 2006-12-13
I tried installing another package when I got desperate shortly after posting but forgot to test it. I'm back now and the game has its own loading bar up and running so it looks like its working... if it doesn't work I'll refer to the other posts here. Looks like everything is working again :D ... thanks everyone. Ubuntu kicks ***.

---

