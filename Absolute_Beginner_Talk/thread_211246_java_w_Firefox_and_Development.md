---
title: "java w/ Firefox and Development"
date: 2006-07-08
forum: Absolute Beginner Talk
---

### Post by cjnkns on 2006-07-08
Hi all!

I recently insatlled Ubuntu and so far love it. I am very happy with the easy installation of most packages linux has come a long way IMHO...

Anyway, I have just used the synaptic(sp) package manger to install java jdk/jre and it does not seem to be working with firefox as the plugin should be? I am sure there is some documentation somewhere I missed or just overlooked. 

Also, if someone would be kind enough to tell me how to use the jdk that I just downloaded for developement purposes? (can i use the typical linux PATH changes on ubuntu also?)
Typically when I installed java I would put it in /usr/local but using synaptic I am not sure where it's located... is this default location ok?

Thank you all!

Hopefully I can keep Winders off my laptop for a while!

---

### Post by Max Luebbe on 2006-07-08
What jdk did you install and how did you install it?

---

### Post by cjnkns on 2006-07-08
I installed java 5 and I used the synaptic package manager...

---

### Post by Max Luebbe on 2006-07-08
The sun jvm or the gcj?

---

### Post by cjnkns on 2006-07-08
Well it's funny you mention that. I found a gcj folder and the newly (i think) insalled java directory in a directory together..

---

### Post by cjnkns on 2006-07-08
I did a locate javac and I find that I have java-1.4.2-gcj-4.1.4.2.0 and a java-1.5.0-sun-1.5.0.06 directories both in the 
/usr/lib/jvm directory....

---

### Post by Max Luebbe on 2006-07-08
<personalbias>
Being a java developer myself, I am not a fan at all of the gcj, and prefer the sun implementaation hands-down. I also feel it should be possible  to get a machine set up without the gcj being hardwired into all sorts of places i don't want it to be no matter what I set my defaults to.
</personalbias>

Your jvms should be found in /usr/lib/jvm

I've never had a problem with java and firefox... I'm looking into that right now.

PATH usually works great.

I reccommend you give Eclipse a try for doing java development, I'm hooked.
The trick is to get it set up not using gcj so performance isnt godawful.

---

### Post by cjnkns on 2006-07-08
Ubuntu is unfamilar territory to me as I guess is to be expected since I am poisting to the "Absolute Beginner" forum. 

Anywho,
 Is it "ok" that my java sun resides in /usr/lib/jvm directory? or being on a linux machine does it make more sense to move it to another place? Does this even matter?

---

### Post by Max Luebbe on 2006-07-08
leave it there.

sudo update-alternatives --config java

run this and set your default java implementation.

---

### Post by cjnkns on 2006-07-08
I found the docs for 
sudo update-alternatives --config java
and ran it for javac and other(s) javaxx also so that seems to be in order. It just seems strange to havea the jdk under a director that says its a jvm... ah well 

I really appreciate your help thatnk you very much!

---

