---
title: "Network Problems"
date: 2006-01-17
forum: Absolute Beginner Talk
---

### Post by fulford1968 on 2006-01-17
Hello, I am new to linux and have set up Ubuntu 5.10 on my eMac computer.
My problem is I can browse some web pages but cant use email or instant messaging such as aim. I have checked my pop settings for email and they are correct. I think it has something to do with the ports? I have set up Firestarter and given access to pop smtp etc but still cant use email or messaging. Also some web pages like Ubuntu Wiki and Hotmail login wont load. I am not sure where to start looking as this is all new to me. I have used Kubuntu on the same machine with no problems but I really love Ubuntu!
Any help to solve this would be most grateful.
Thankyou:(

---

### Post by dueY on 2006-01-17
Did they work before you installed the firewall?

---

### Post by hen3rz on 2006-01-17
You could try see if the ports for instant messaging and SMTP and POP are open on you modem and or router.

---

### Post by thomas.jreige on 2006-01-17
Have you tried to disable the firewall and connect to these pages or email servers.

Can you telnet to the pop server eg.  telnet <pop server> 110 and get a response.

---

### Post by fulford1968 on 2006-01-17
No the problem was there before I installed the firewall. Tried to telnet my pop server but it just got no response. I tried the Dapper Drake Ubuntu and it was fantastic. No network problems, everything just worked. All bar the display that is. It is set to the usual 1024-768 at 89hz but it leaves crap all over the screen and windows wont dissapear. I would use this but cant cause of the display. I tried to reconfigure the xserver but stuffed it up and ended up with a blank screen. Looks like Tiger will have to go back on my system (YUCK).
Thanks for your replies.

---

