---
title: "Bellsouth and Ubuntu"
date: 2008-04-18
forum: Absolute Beginner Talk
---

### Post by bingo1978 on 2008-04-18
I am new to Ubuntu. I am tired of Windows viruses and software prices. I like it so far. I am unable to get my Bellsouth wireless to work. Is there something I am missing? I can connect fine with a wired connection, but no go on wireless. My drivers are working, but it will not let me connect. It wants a password that I have never needed with Windows. Sorry for all the questions, but I am trying to learn.

---

### Post by ACMarina on 2008-04-18
Well, if you're getting to the point where it's asking for a password, that's a step in the right direction..

What kind of password does it want, specifically, does it say?

---

### Post by bingo1978 on 2008-04-18
It wants a 128 hexadecimal encryption password. Where is that? Is there a way around it? I am completely new to Ubuntu and I am just now figuring out how to use it, so forgive my ignorance.

---

### Post by Dekafox on 2008-04-18
Sounds like WEP or WPA got turned on. (I always forget which is which) While connected wired to it, try going to the config webpage for your router/modem and take a look aorund, see if there's an option stating that.  You should be able to change it, and I'd reccommend that over turning it off, as it makes it at least a little more secure.  Turning off Broadcast would be even better for security, but could be problematic depending on how you set your computers to connect to it.

---

### Post by ACMarina on 2008-04-18
Let me stab at this - 

You have Bellsouth DSL??

And it's hooked to a wireless router??

You will probably need to wire connect to your router to find out what your password is.  It may have automatically set it up with Windows, so you just never had to write it down or even know what it is.

---

### Post by bingo1978 on 2008-04-18
Dekafox- I don't know how to do that. In Windows or Ubantu? I am running both OS on my computer. I was spoiled by Windows and I am still baffled by the command prompts used by Linux based systems.


AC-Correct and correct. I found it on my roomate's computer. I put it in on mine and it says "not found". What sould it be set as? I tried setting it as an open connection, I tried everything I can think of. Is there a file I need to load or am I missing something? Thank you for helping.

---

### Post by Yellowdog428 on 2008-04-18
the first logical step is asking what type of router you are using.  

can you get to the settings page?  If so make sure you find the Key, or turn off the security and see if you can connect to it.  If you can connect to it without the security turned on then turn it back on and either use the same key and enter it when prompted or keep it open but understand what an open connection means and if it is a good Idea for you.

good luck

---

### Post by bingo1978 on 2008-04-18
Westell 9596. I can see the wireless signal on my connection, but can not access it. Where would I find the settings page?

---

### Post by bingo1978 on 2008-04-20
Something weird. It connects fine with my Gateway laptop, but not my Dell. I have done nothing to the settings. They both have exactly the same settings.The Gateway has an external card and no Windows OS. The Dell hasan internal card and still has Windows on a partitioned section of the hard drive.

---

### Post by perlluver on 2008-04-20
Usually you can get into the router with 192.168.2.1 or 192.168.1.1, then it will ask you for your username and password.  Unless someone changed them they are pretty standard, admin as user and router as password or vice versa.  Then you should be able to get to the wireless security.

---

### Post by bingo1978 on 2008-04-20
I must sound like a complete idiot, but where do I put in the IP address? I can hold my own on Windows. but I have literally had Ubuntu for 4 days. My router settings should be the default settings. I installed it and I am sure I kept it simple.

---

### Post by perlluver on 2008-04-20
Type the ip address into firefox, unless you mean another ip address?

---

### Post by bingo1978 on 2008-04-21
I did that and nothing happened. Itried my computer at a friend's house and the wireless didn't work there either. It didn't even detect a wireless network. I intalled the drivers that were restricted before I even posted. It seems that my wireless card is not working properly. Is there a way to test it? It seems like this is the next logical step.

---

### Post by russo.mic on 2008-04-21
So, what probably happened is that Bell South included some install CD, which actually just put this password info in windows, so you wouldn't have to do it, which is why it's working with all of your other computers.  

The Router holds this password, almost certanily, and the best thing you can do is to download the manual for the model you have, and look up how to access the menu in it.  You will probably have to get a cable, plug into the router, and as they've said before, type [http://(the](http://(the) router gateway) which will be some number.  192.168.2.1, or 192.168.20.1, or something like that.  It's different for some routers.  

That will allow you to reset the password, or extract the password, or something. 

Good Luck!

Russo

---

### Post by bingo1978 on 2008-04-22
Did as you suggested. I retrieved the password and put it in when Ubuntu requested the network key. It kept showing me that it was "waiting for network key from wireless network". Then the screen requesting the password came back.

---

### Post by bingo1978 on 2008-04-22
Ok, turned off the password protection and it works now. Thanks! The only other problem is the connection speed. It is slooooooow. Itis about the speed of dial-up. Any idea?

---

