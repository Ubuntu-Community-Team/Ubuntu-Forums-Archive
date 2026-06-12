---
title: "Internet on Ubuntu"
date: 2007-04-15
forum: Absolute Beginner Talk
---

### Post by captabec on 2007-04-15
Well i recently installed Ubuntu onto one of my older computers, and I want to start using the internet. But when i plugged in one of my routers the internet light wont come on. I didn't install the program for the router because i cant find the cd, so i thought that was the problem. So i got another router(its a wireless), I then proceeded to put in the cd and tried to load the setup but it wont load it. I do have a working Ethernet card and phone jack, so do you know how i could get the router/internet to work.

P.S. I have a working router set up on a computer downstairs running Xp, and whenever i try to run on the first router(on my Ubuntu comp) the internet light turns off downstairs. Am i not aloud to have 2 router running at the same time?
Edit/Delete Message

---

### Post by Seisen on 2007-04-15
How many DSL/Cable modems do you have?

---

### Post by captabec on 2007-04-15
I have 3 now but only one set up on another computer. I am trying to set one up on my Ubuntu comp, so then i will have 2 running DSL.

---

### Post by Seisen on 2007-04-15
What is the name of the dsl modem you are trying to get to work on Ubuntu?

---

### Post by scrooge_74 on 2007-04-15
> **captabec said:**
> Well i recently installed Ubuntu onto one of my older computers, and I want to start using the internet. But when i plugged in one of my routers the internet light wont come on. I didn't install the program for the router because i cant find the cd, so i thought that was the problem. So i got another router(its a wireless), I then proceeded to put in the cd and tried to load the setup but it wont load it. I do have a working Ethernet card and phone jack, so do you know how i could get the router/internet to work.

P.S. I have a working router set up on a computer downstairs running Xp, and whenever i try to run on the first router(on my Ubuntu comp) the internet light turns off downstairs. Am i not aloud to have 2 router running at the same time?
Edit/Delete Message

For proper help you should give more details.  

Are you using a USB router?  If you are using wireless, what brand is the card on your PC?

More info, faster help

---

### Post by captabec on 2007-04-15
I am using a Ethernet connection. And the regular router, not the wireless, is a Westell Model 6100. Note i do not have the cd for this router, although i do not think it would load on Ubuntu.

---

### Post by scrooge_74 on 2007-04-15
If the router plugs to the ethernet port you should not need to use any CD, if it is a config tool  you could use the XP sytem.

Also no need to make two threads  [http://ubuntuforums.org/showthread.php?t=410516](http://ubuntuforums.org/showthread.php?t=410516)

---

### Post by Seisen on 2007-04-15
Try doing this in the terminal and see what happens.

```
sudo pppoeconf
```

---

### Post by captabec on 2007-04-15
Well the internet light never comes on until about 10 min later when it goes red. I didn't think i needed the cd but for some reason it wont work. Sorry for double posts i am new on this forum.

---

### Post by captabec on 2007-04-15
How do i type in the password after i type in the command (sorry I'm new). And another thing every time i try to start up the router it turns off my internet light on my router downstairs.

---

### Post by Seisen on 2007-04-15
Just type in your password like you would type anything else and hit enter when you are done. It just doesn't show up on the screen.

---

### Post by captabec on 2007-04-15
And the password is my password to log in?

---

### Post by Seisen on 2007-04-15
Yes also sudo does is give your super user privleges.

---

### Post by captabec on 2007-04-15
Then what do i do?

---

### Post by bobplano on 2007-04-15
i assume you need to tell us if it did anything and post the output here. also look for errors if there are any

---

### Post by Seisen on 2007-04-15
Did you select you network card and did it find your modem

---

### Post by captabec on 2007-04-15
It had a loading screen and it said: Looking for pppoe access concentrator on eth0. Then it said: Sorry i scanned interface but the access concentrator did not respond. check network and modem cables.Another reaon for scan failure may be another pppoe process that controls the modem.

---

### Post by Seisen on 2007-04-15
Do you happen to have Verizon Wireless as an ISP.  I found a link that might help you. 
[http://members.verizon.net/~res08lyg/6100.htm]("http://members.verizon.net/~res08lyg/6100.htm")

---

### Post by captabec on 2007-04-15
Actually i think i might, hold on.

---

### Post by captabec on 2007-04-15
When it wants me to go to private lan connection it asks me for a password that i don't know.

---

### Post by Seisen on 2007-04-15
Are you using the website I gave if and if you are which step are you on?

---

### Post by captabec on 2007-04-15
I am using the website and I'm on step 7.

---

### Post by Seisen on 2007-04-15
Have you put anything in for the password, the default should be "password"

---

### Post by captabec on 2007-04-15
I know ive been here before to set up something for Utorrent, and i don't remember changing the password.

---

### Post by captabec on 2007-04-15
Do you know of any way for me to find out my admin name and  password

---

### Post by Seisen on 2007-04-15
If you still can't access it still you can reset the modem to default by holding down the reset button  on the back of the modem.

---

