---
title: "HOW TO :kad firewalled, amule, adsl modem/router"
date: 2007-06-12
forum: Absolute Beginner Talk
---

### Post by Claus7 on 2007-06-12
What we want to do :

We want to see that the amule is working fine, that means that the two arrows in the down right corner above a globe are **green**!

My version of Ubuntu is 6.06 Dapper Drake. My amule version is 2.1.3 and my modem is telindus 1133 adsl modem/router.

First of all I have to say that I downloaded amule from synaptic package manager. 
When I was trying to connect the arrows in the globe were always yellow no matter what I was trying to do. And the message of kad was :
kad : firewalled.

Searching the forums I realized that I had to do two things :
i) the first one had to do with the firewall of my computer
ii) the second one had to do with the ports of my modem.

i)SETTING YOUR FIREWALL

As far as the first is concerned, I do not know (up to now) which is the firewall I'm using. What I do know is that with firestarter (you can download it via synaptic), I can manually control the ports that they won't be hindered by the firewall itself.
So in order to allow the ports through the firewall one must declare this ports to this program. In order to do that (is very easy) you open a terminal and type the command :
```
sudo firestarter
```
and give your password

as you understand you must be root in order to do that.

Then a window will open. If you do that for the first time (at least that happened to me), I saw some messages that they were telling no folder of this or the other kind exists. The program opened very well. I ignored this messages and after the first time I never saw them again. I suppose that they vanish, because the folders in question are created after the first time you run the program.

You will see three tabs in a row. Go to the Policy tab. There go to the second "area" where it says just above Allow service.
Do a right click and select add rule. For amule you have to do this procedure three times writing in the port tab the following numbers :
4662
4665 (=4662+3, this is how I found it while searching, you have to put only the 4665)
4672

Every time you will press the add button.

Now you have configured your firewall. Open amule and see if it works. Wait at least 10 minutes in order to see whether this was the cause of having kad firewalled. If the yellow arrows remain, then you have to configure your router as well.

ii)SETTING YOUR ROUTER

Connect with your router typing in a browser the address of your router.
Give the username and the password of your router.
Then go to port forwarding (it might be on the tad advanced).
Then in the telindus modem I chose *user* and then *edit* in order to do Port Forwarding.
Then I wrote the following three times, one for every number :
Rule Name: 'type what you like'
Protocol: TCP for 4662, UDP for the other two numbers
Port Start: 4662 (and 4665, 4672 for the other two)
Port End:   4662 (and 4665, 4672 for the other two)
Port Map:  4662 (and 4665, 4672 for the other two)

As soon as I did that immediately the kad arrow turned green. For the other arrow I chose a different server Donkey Server no1 and the second arrow turned green as well. Finally I did add in the applied rules.

Even if I saved the changes I have to say that when I connected the second time I had to add again the settings in the applied rules. In any case may I have pushed only the button apply forgetting to hit save afterwards. At least the one way or the other it worked for me.

May be this is not the definite how to, yet I hope it helps. If someone has found out something different or (why not) something wrong with this how to, I will be glad to hear.

Regards!

---

### Post by Hallvor on 2007-06-14
Nice. Just a note: Some ISPs throttle the default ports of known P2P applications, so changing the standard ports may be a good idea in some cases.

---

