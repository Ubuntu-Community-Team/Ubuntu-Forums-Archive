---
title: "bcm43xx-fwcutter isnt working??"
date: 2006-08-10
forum: Absolute Beginner Talk
---

### Post by WalmartSniperLX on 2006-08-10
I have a broadcom chipset wireless pci card (microsoft). I tried the instructions on using this utility with drivers given. The page i used is here: [http://ubuntuforums.org/showthread.php?t=185174](http://ubuntuforums.org/showthread.php?t=185174)


Basically I have network manager running and its not picking up any wireless network (the light isnt even on either). What can i do to fix this?? please help!! :confused: :( :?:

---

### Post by Jjohn on 2006-08-10
Hi Walmart,
          I am having the same problems the only thing I know is that you need to uninstall "wifi radar" if you have it that is as it causes a problem.
         Please keep the thread up to date and if you get a fix off forum please include it here so that I can find out what you did...
Regards    John:cool:

---

### Post by WalmartSniperLX on 2006-08-10
> **Jjohn said:**
> Hi Walmart,
          I am having the same problems the only thing I know is that you need to uninstall "wifi radar" if you have it that is as it causes a problem.
         Please keep the thread up to date and if you get a fix off forum please include it here so that I can find out what you did...
Regards    John:cool:

Ok ill investigate on this. Ill be happy to post post anything important. :D

---

### Post by WalmartSniperLX on 2006-08-11
Alright. Initially i didnt have wifi radar but i installed it to see what i could get out of it. I didn't get anything, but that wasn't anything unexpected since my wireless card light is still off. :S

---

### Post by tdwester on 2006-08-11
What is the chipset of your card?Is it a 4306 or 4318?

---

### Post by WalmartSniperLX on 2006-08-11
> **tdwester said:**
> What is the chipset of your card?Is it a 4306 or 4318?

Im not sure all i know is :

Network controller: Broadcom Corporation BCM43xG 802.11b/g (rev 02)

:S

---

### Post by tdwester on 2006-08-11
Copy and paste this.


> lspci | grep Broadcom\ Corporation

Then post the results.

---

### Post by WalmartSniperLX on 2006-08-11
0000:00:0d.0 Network controller: Broadcom Corporation BCM43xG 802.11b/g (rev 02)

---

### Post by tdwester on 2006-08-11
Give this how to a try I belive it is a 4318 like mine and this worked for me.

[http://www.ubuntuforums.org/showthread.php?t=197102&highlight=broadcom+4318](http://www.ubuntuforums.org/showthread.php?t=197102&highlight=broadcom+4318)

---

### Post by WalmartSniperLX on 2006-08-11
> **tdwester said:**
> Give this how to a try I belive it is a 4318 like mine and this worked for me.

[http://www.ubuntuforums.org/showthread.php?t=197102&highlight=broadcom+4318](http://www.ubuntuforums.org/showthread.php?t=197102&highlight=broadcom+4318)

Ok thanks ill give that a try now :D

---

### Post by tdwester on 2006-08-11
Let me know if it works.

---

### Post by WalmartSniperLX on 2006-08-11
:S  i dont think it worked :(

---

### Post by tdwester on 2006-08-11
Did you re-boot?

---

### Post by WalmartSniperLX on 2006-08-11
yeah I just did. 

Just to make sure Im looking at the right things, after I follow the instructions I should be able to have the wireless network options in network manager?

---

### Post by tdwester on 2006-08-11
I had to go into network in the under system and  switch from etho 0 to etho 1.

---

### Post by WalmartSniperLX on 2006-08-11
> **tdwester said:**
> I had to go into network in the under system and  switch from etho 0 to etho 1.

when I did that I enabled etho 1 (the wireless) but nothing changed. After closing it, I re-open it to check to see if the changes were correct but it re-disables etho1. Am I doing something wrong? :?:


EDIT: Woah now its not even detecting my wireless adaptor anymore :S Hold on Ill do what i can to see whats going on

---

### Post by tdwester on 2006-08-11
Sorry but that is all that I have.
  ok. I will wait.

---

### Post by WalmartSniperLX on 2006-08-11
> **tdwester said:**
> Sorry but that is all that I have.

its ok. Thanks for the help :D

---

### Post by Jjohn on 2006-08-11
Thanks Tdwester,
               I will give that a try also. I have the same wifi setup...:D
Regards   John

---

