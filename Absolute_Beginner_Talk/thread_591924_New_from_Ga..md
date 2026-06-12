---
title: "New from Ga."
date: 2007-10-25
forum: Absolute Beginner Talk
---

### Post by ki4dmh on 2007-10-25
I have just installed the newest ubuntu and I love it for the most part. I do have several questions to ask once I figure out where I need to ask them.
Scott

---

### Post by n3tfury on 2007-10-25
k.

---

### Post by santiagoward2000 on 2007-10-25
Welcome!!! :popcorn:
About where you should ask the questions, here's a good place for most questions, specially if you're just starting. That's why it's called "Absolute Beginner Talk".
Just ask, you'll probably get an answer... I hope...

---

### Post by por100pre1 on 2007-10-25
Welcome! You are in the right place, please don't hesitate to ask any questions.

---

### Post by ki4dmh on 2007-10-26
Well here goes then. I have several questions. Just about all of them surround my internet connection. I have dsl from my local power company. It works real well with windows xp home and xp pro as well as most other windows os.
Description of my internet connection is as follows:
#1. I have cat 5 cable running in from the phone box to a speed stream 4200 modem.
#2. From the modem into a Linksys  54 wireless G 2.4 Ghz wireless router.
#3. From the router into a built in motherboard ethernet adapter.
#4. My computer is the one that is hard wired while my sons desktop is on a Linksys wireless G adapter.
#5. I run the router and adapter in secure mode.
Both my computers are hand built by me.Computer equipment is as follows:
Computer #1. This is my machine. It is a  865 chip set ECS P4M800Pro-M478. It has 512K of memory with a Pentium 4 3.0 Gig processor. A DVD burner and a CD burner. The motherboard has a built in Ethernet adapter that I am using. It has never given any problems. Up until now I have been using XP Home for my os. This has been a rock solid set up for a very long time. I am just ready for a change.
Computer #2. It has an intel 845 chip set  intel motherboard. I forget the exact model #(sorry). It has 512K of memory with a celeron 2.4 Gig processor. It has a wireless G Linksys wireless adapter connection. His os is Windows XP Home. It is a rock solid computer that gives great service.
Now:
Question #1.  In order for Ubuntu to detect my Ethernet adapter built into my motherboard I have to boot my modem and router combo up at the same time with my computer. If for some reason I have to do a restart Ubuntu will not detect my connection. Everything has to be restarted at the same time in order for everything to work. How can I remedy this situation? I am not sure if it is my connection or my adapter that is not being detected.
Question #2. When I am using Ubuntu 7.10 my sons wireless connection is gone. When I pull up the wireless monitor system on His machine it says that the wireless adapter cannot communicate with the router. I can change back over to windows and the connection shows back up on His machine. What can I do about this? It is important that both of us have access to our machines. We are typically on our machines at the same time, otherwise this wouldn't be an issue.
I desperately want to get away from windows as much as possible. If these two issues can get worked out it will make my transition that much easier.
Question #3. The server where I get my DSL from likes for the Ethernet adapters to be configured at 10Mps instead of auto detect or 100 Mps. I have went to several internet broadband speed sites that show my connection speed is in fact faster with the 10 Mps setup. When I check the connection in Ubuntu it is configured for 100 Mps. Does this matter? How can I configure it for 10 Mps full duplex? My connection I pay for is 1500 down 384 out. What I show most of the time is 1328 or so down and 320 or so out.
Sorry for the long post but I wanted to offer as much info about my setup as I possibly could. I figure the more info the easier it would be to diagnose my problems. Thanks in advance for for knowledge and input to my issues.
Scott

---

### Post by Pinger05 on 2007-10-26
Question 1:  Ummmmmm not sure about that one.  Odd that everything has to be booted.

Question 2:  What wireless card is pre-installed on the laptop?  If it is not caught by Ubuntu you may be stuck running ndsiwrapper.  Do a search on the forum for titles carrying the name ndiswrapper for complete directions.  There are a ton of chipsets out there and most of them have step by step directions here in the forums using ndiswrapper.

Question 3:  Using Auto-Negotiate you will get 100Mbps to the Wireless Linksys 54G.  What the power company sees would come from the speed stream 4200 modem.  So I would not worry about that.

---

### Post by psycosmyth on 2007-10-26
Oh the mystical land of Ga. There are strange creatures there. 
Not as strange as the ones here in Tn though:)

Welcome!
You have many questions that I could be asking myself since I plan to make some changes that are identical. 
Don't feel afraid to ask anything here. Also hit up the other forums specific to your questions. Here however you can ask pretty much anything.

---

### Post by LowSky on 2007-10-26
question #1 Seems to be a router issue, why not try using the router in non secure mode
question #2 This makes no snece what so ever, it seems like a router issue in relation to the router seeing a linux connection..?
question #3 your modem controls your speed not you computer, the computer only talks with your router, and your router talks with your modem.

All in all I think oyu have some kind of conflict comming from your Router.

---

### Post by ki4dmh on 2007-10-26
Yea I was thinking about trying to change the firmware in my router to something that linux can recognize or vice versa which ever the case may be. Thanks for all the input.
Scott

---

