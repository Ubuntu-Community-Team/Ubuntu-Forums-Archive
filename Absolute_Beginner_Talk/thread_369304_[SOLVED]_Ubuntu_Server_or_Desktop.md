---
title: "[SOLVED] Ubuntu Server or Desktop ?"
date: 2007-02-24
forum: Absolute Beginner Talk
---

### Post by ashmew2 on 2007-02-24
Hi every1 , i have been playing Counter Strike 1.6 (non-steam) for some time now. I usually host dedicated servers on my Ubuntu Desktop machine (and i play from the same machine), but there is the common complain about lag. So is there a way that I could install the Ubuntu Server and run a dedicated server on it and run Counter Strike also ?
and Btw , will the Ubuntu server provide a boost to the cs server or not ? 

Thanks!!!

---

### Post by Muzik83 on 2007-02-24
Hey

If the lag is caused by your computer being "Too busy" (while playing, flip to a terminal and do an uptime or top, and look at the load average... if its more than 2-3 then it probably is that your computer is "too busy" to handle requests), then hosting the CS server on a _second machine_ would be beneficial.

If you are talking about getting rid of ubuntu desktop (as in not getting a second machine), and installing ubuntu server and playing CS on the server, there will be no difference.  Ubuntu server is exactly the same underlying Linux, but instead of "Gnome" and "The Gimp" and other desktop applications you have "Apache" and "MySQL", and a bunch of other server applications.

So if you were to take Ubuntu Server, and install Gnome and all the desktop apps, you would have essentially the same machine as if you were to take Desktop and install a bunch of server apps.

---

### Post by ashmew2 on 2007-02-25
hmm , so that wudnt make any difference , will it. ?
Btw , any ways i can cut off the lag to some extent />?

---

### Post by ashmew2 on 2007-02-27
bump

---

### Post by compmodder26 on 2007-02-27
> **Muzik83 said:**
> Hey

If the lag is caused by your computer being "Too busy" (while playing, flip to a terminal and do an uptime or top, and look at the load average... if its more than 2-3 then it probably is that your computer is "too busy" to handle requests), then hosting the CS server on a _second machine_ would be beneficial.

If you are talking about getting rid of ubuntu desktop (as in not getting a second machine), and installing ubuntu server and playing CS on the server, there will be no difference.  Ubuntu server is exactly the same underlying Linux, but instead of "Gnome" and "The Gimp" and other desktop applications you have "Apache" and "MySQL", and a bunch of other server applications.

So if you were to take Ubuntu Server, and install Gnome and all the desktop apps, you would have essentially the same machine as if you were to take Desktop and install a bunch of server apps.

While most of what you say is correct, you seemed to omit the fact that removing all the gui apps will DRASTICALLY reduce the load on the server.  And Apache and MySQL aren't on there by default.  You can choose that option if you like.

I'm not a gamer so I don't know about the CS server.  But if the server is a gui application then you'll need Ubuntu Desktop.

---

### Post by ashmew2 on 2007-03-15
nah the server is command line . there's an executable hlds_run which runs the server when given appropriate commands...so shud i install ubuntu server ?

---

### Post by ashmew2 on 2007-03-15
And btw , ive been using Edgy Eft and whenever i play CS with Cedega or wine , the CPU usage goes up2 100% , maybe that has something to do with lag ?

---

### Post by lamalex on 2007-03-15
you should never be playing on the same machine you are hosting on. I'm an avid cser and ubuntu server works great with ubuntu server, all you need is an old pc if its just you and a few friends laning. If your server is public you probably a) dont want to host it out of your house and b) will need a better machine. so yeah, using server will drastically increase performance but if youre going to use server then you're going to need to use a seperate computer since CS isnt CLI based.

ps do the new ads in 1.6 piss you the hell off? I was playing last night and  getting so mad watching intel billboard on aztec.

---

### Post by ashmew2 on 2007-03-15
lol..thanks for the info , but i got only one machine at home with  asucky 256 kbps connection..i make 10 player servers...i was thinking that if i installed ubuntu server and then only installed essential things that wud run the server as well as client on the same machine...that wud make a difference ?

btw , i dont get ne ads in cs 1.6..ol..

---

### Post by lamalex on 2007-03-15
Well if youre going to be using ubuntu as your main computer, install the desktop version and then do server. That's going to be the best way for you.

As for ads, do you not get them on your home server or on pub servers or both? Theyre part of 1.6 now so you really should be getting them. They are only built into a few maps though (aztec is one, i think dust has them too but idk) and when you view scores there is one, and when you are dead there is one.

---

### Post by rayofash on 2007-03-15
Where'd you get a non-steam version of CS1.6? Isn't Won.net dead?

Also, your slow connection is playing a major role in the lag.

---

### Post by lamalex on 2007-03-15
There are a few non-steam servers left. That's why he's not getting ads, I didn't notice that part.

---

### Post by rayofash on 2007-03-15
> **Iamalex said:**
> There are a few non-steam servers left. That's why he's not getting ads, I didn't notice that part.

It's possible to host Steam servers with HLDS right?

---

### Post by ashmew2 on 2007-03-16
Acctually i always host a non steam server cuz 99% of my friends use non steam copies of 1.6....
And so....what i understood is , that there is quite nothing can be done ?

---

### Post by pppetter on 2007-03-18
Well, if you have a computer laying around, then go ahead and install ubuntu server and HLDS. But I don't know how to make it a non-steam server though. There's one important thing, don't use the  server kernel, use the desktop kernel. The kernel server has very low timer, which is bad for FPS intensive games. If you have a computer with a good processor, consider compiling a custom kernel and raise the timer even more, like 500 or maybe even 1000 if you have a REALLY GOOD processor. 

But I really think that your internet connection will cause you some severe lag problems.

---

