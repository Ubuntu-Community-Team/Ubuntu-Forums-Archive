---
title: "Compaq Laptop Sudden Shutdown"
date: 2007-06-19
forum: Absolute Beginner Talk
---

### Post by anonimo01 on 2007-06-19
Hi, im a noobie :D, and i installed Feisty a couple of days a go and i keep getting this sudden shutdowns, mostly clean but it goes back to code and says something about a network connection and the it just shuts down
 (sorry it's too fast to even read it). 

When i restart the system runs like nothing happened it even keeps some of the windows i had opened before the shutdown. Sometimes it happens in minutes after i boot and sometimes, like last night i watched a dvd, stayed online and downloaded more software and it didn't even peeped, feisty runned like silk...  

I watch a lot of multimedia and i have amarok installed and it's the only thing i didn't opened last night, but it did shutdown watching a video from you tube, so if anyone can help i'll appreciate it because otherwise Feisty runs flawlessly on my laptop. I don't even have problems with wifi it connects quicker than windows.

I have a Compac Presario V2069CL 
Intel Centrino 1.40GHZ, 512 Ram, 60GB, WIFI, 14.1" LCD, CD/DVD Recorder. Ohh! and i erased the windows partition (no more Windows for me, now im powered by linux jeje :p!!)

---

### Post by lazyart on 2007-06-19
are you set to hibernate after a certain amout of idle time?  processor overheating?  battery not fully charged?

---

### Post by LaRoza on 2007-06-19
Is it possible the laptop is over heating? This is a common problem with laptops.

---

### Post by dannyboy79 on 2007-06-19
can you please post anything unsual within your /var/log/syslog file? also, please inform us of what this outputs from the command line

lspci -v

also, I will need to know specifically exactly what you mean when you say, "mostly clean but it goes back to code and says something about a network connection and the it just shuts down". Like exactly what were you doing, what exactly happened step by step (example, what program you were using at the time, what happened in exact steps.) Also, have you used Automatix2 to install anything? Do you have any processes that you haev running in the background besides what the install did? Does /var/log/messages show anything helpful also? Are you running beryl or compiz, what graphics drivers are you using? We can maybe help after you answer all these questions.

---

### Post by anonimo01 on 2007-06-19
hi, thanks guys for answering so soon, im at work so i im not able to tell anything about the logs, i'll be posting them later from home. 
but the thing is it's not overheating cause like i said last night it stayed like 4 or 5 hours on and it didn't shut down, and all the setting for power manegment are set to never because i alwaus use it plugged in. 

I have automatix but the shut downs began before i had it, and as i recall must of the times it shutted down i was like watching a movie clip or listening to  a song, most of the time i had firefox running and amarok. I have beryl installed but i did that yesterday so i'm guessing that's not it. I also have opened all the windows i could to see if it was a memory fault or something but it didn't. Even with the beryl all the effects are nice and smooth. 

Also the day i installed it when i booted it for the first time it started to load then when the orange line from the load thingy  (sorry i'm not technical at all) was full it started to unload the system without doing anything else. that happened 2 times but after that it started really well, and it hasn't happened again. i don't know if that helps.

Any more info you need just ask. 
And once again thanks, you guys responded way better than any windows support i have received.

---

