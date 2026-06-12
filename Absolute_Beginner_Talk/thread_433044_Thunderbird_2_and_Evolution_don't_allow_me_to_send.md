---
title: "Thunderbird 2 and Evolution don't allow me to send messages"
date: 2007-05-04
forum: Absolute Beginner Talk
---

### Post by croxi on 2007-05-04
Ok, I have accepted that I have had a "broken pipe" which someone on here previously mentioned that is something to do with my DSL modem not allowing me to use Evolution or Thunderbird 2 to send and receive messages. 

My frustration is pointed to the fact that when I use Gmail on the same machine, it sends and receives mail without a problem. If I want to fix Thunderbird or Evolution, will the same settings apply or does Gmail run differently?

I tried the various sites with various kinds of fixes, even to the point of reinstalling Evolution & Thunderbird and nothing seems to have worked. Any help would be cool. 

cheers

---

### Post by nanotube on 2007-05-04
1. make sure you have the correct settings for the incoming and outgoing servers and ports
2. make sure you have the correct username/password

if that doesn't work... then, when you set up gmail, make sure to first go into your preferences and enable the pop server. after that, set it up like any old pop account. there are specific instructions for setting up gmail through pop in gmail help section.

---

### Post by croxi on 2007-05-04
my response to "...the correct settings...." would be to fire up the "brain-grinder" and stick my head in it headbutt-style. 

Sorry, but I don't know much about settings, I´ve always been just a user and not someone who messes with things I barely understand. 

What are the correct settings for these things anyway?

---

### Post by bulldog on 2007-05-04
If you want to use  POP email,you have to enter the information which was provided by your provider.
That should be  a user name and a password,and the settings for the POP-server and the Mail-server.

If you enter these items in your mail program,it should work.

---

### Post by croxi on 2007-05-04
I don't know what information you mean...

I was never provided with anything that resembled information, just the ADSL modem and a nice little $20,000 charge for replacing it for one that actually worked. 

I connected to the internet via the ADSL box and a router for my other 6 PCs 

I never had any need to go in to play with settings as I have been a user of Hotmail for quite a number of years up until this year (knowledge is a powerful thing) and only found out that there were other email providers recently, just before I broke away from MSWin. 

What I'm looking for is more detailed help if there's anyone out there that can help me.

---

### Post by amaroKer on 2007-05-04
If they're both not working, it's not their fault.  Don't bother reinstalling.  If you're using GMail, here's the settings:

1.  Go to your webmail and enable POP for all messages in your settings.  MAKE SURE you click 'Save'.

2.  Incoming Server: pop.gmail.com

3.  Encryption:  SSL

4.  Authentication:  Password

5.  Outgoing Server:  smtp.gmail.com

6.  Encryption:  SSL (checkmark the 'requires authentication' box)

7.  Authentication Type:  PLAIN

NOTE: 4 & 7 should only apply to Evolution.  Not sure about Thunderbird.

When asked for username, don't put in the '@gmail.com' part.  Just the username.  Good luck.

---

### Post by croxi on 2007-05-05
I can get onto Gmail without any problems, I just wanted to configure Thunderbird 2 and/or Evolution so that I have a choice of email servers. 

I'm able to use Gmail as I was from the start, but I wanted to make Thunderbird 2 and Evolution work because they're there and I have a mountain-climbers mentality, if its there I want to climb it. If they're there for me to use, then I want to use them. 

I also don't like things to beat me. 

I am still a little underconfident about writing things in terminal that others haven't already done, but I want to learn more about using code properly. I have high hopes that I will be able to learn something but I need more help

---

