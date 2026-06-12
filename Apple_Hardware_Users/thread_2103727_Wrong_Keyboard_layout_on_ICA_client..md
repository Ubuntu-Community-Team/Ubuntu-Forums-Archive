---
title: "Wrong Keyboard layout on ICA client."
date: 2013-01-11
forum: Apple Hardware Users
---

### Post by Knightwise on 2013-01-11
Hey Guys

I'm a little bit of a cross platform geek who likes to "slide" from OS to OS. At the moment I'm running Ubuntu 12.10 on my 11.6 inch Macbook air. I have a French Macintosh keyboard (azerty) that works perfectly on Ubuntu.

At work we use a Citrix server to connect to a Windows environment. I wanted to start bringing my own laptop to work and use linux, and just accces the Citrix server with an ICA client.

I followed this great howto : [https://help.ubuntu.com/community/CitrixICAClientHowTo](https://help.ubuntu.com/community/CitrixICAClientHowTo) to get that done.

The problem I have now is that the keyboard layout is completely fracked up when I log into Citrix. My question is : Does anybody know how to fix this ? 

I opened up the wfclient.ini file and when it comes to keyboard here is what it states : 

KeyboardLayout = (User Profile)
KeyboardMappingFile = automatic.kbd
KeyboardDescription = Automatic (User Profile)
KeyboardType=(Default)

Now : Does anybody know what I need to fill in to override these settings  ? Obviously the default settings don't work, So i'll have to fill something in manually but aside from "French Macintosh" I have no clue what to fill in.

---

### Post by Knightwise on 2013-01-11
Managed to fix it. 
I just had to type FRENCH behind the first line of the config file 

keyboardlayout = FRENCH

):P):P):P):P):P):P

---

### Post by Knightwise on 2013-01-11
Here is the article on how I did it (complete with links) [http://knightwise.com/how-about-a-citrix-session-in-ubuntu-on-a-macbook-air/](http://knightwise.com/how-about-a-citrix-session-in-ubuntu-on-a-macbook-air/)

---

