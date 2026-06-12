---
title: "XGL Help"
date: 2006-08-13
forum: Absolute Beginner Talk
---

### Post by Gonzo_PhD on 2006-08-13
I installed XGL/Compiz (I followed the instruction). When I log onto the XGL session, funny things happen. When I open applications they stick to the top tool bar and I can't move them. Another thing that happens is that everything gets really slow. What do I do?

---

### Post by MarkSheely on 2006-08-13
Hmmm....tell me more about your computer: video card, RAM, etc.  Also, what method did you use to install XGL/Compiz?

The fact that things are really slow suggests to me that the method you used for installation may not be compatible with your hardware, or that you may have missed a step in the process.....

We'll probably be able to work it out though.

--Mark

P.S. Is your PhD in Gonzoism (Hunter S. Thompson)?

---

### Post by Gonzo_PhD on 2006-08-14
I have:

1gb RAM
ATI 9800 Pro AIW
AMD Athlon XP 2000+ (If anything slowed me down it's probably this)
80gb HDD

PS
Yes it is.
"I'm a Doctor of journalism, MAN!"
lol

---

### Post by mcduck on 2006-08-14
Apps sticking to top panel sounds like you are missing window decorator (and thus can't move windows around or anything). But that's probably not the real problem but just a symptom.

Could you post a link to instructions you followed? There are so many ways run XGL/Compiz that without them it's very hard to figure what you did and went wrong..

I'm sure that you aren't having any hardware problems, and your machine is easily fast enough to run Compiz.

---

### Post by ser1alsn1per on 2006-08-14
hi i have just finnished installing everything on ubuntu including xgl this is what i did 

installed ubuntu 


type  

sudo apt-get update
sudo apt-get install linux-restricted-modules-$(uname -r) #Okay if it is already installed
sudo apt-get install xorg-driver-fglrx
sudo depmod -a
sudo aticonfig --initial
sudo aticonfig --overlay-type=Xv



then folow the 2nd howto on this site 

[http://www.compiz.net/viewtopic.php?id=389](http://www.compiz.net/viewtopic.php?id=389)


restart and it just worked 

hope it helps my ati card is a radeon 9600 but it might work  
just try it

---

### Post by Gonzo_PhD on 2006-08-14
im gonna try that. I just never did that first part, so that may be whats wrong.

btw, those where the instructions I followed.

Thanks for the help.

---

### Post by Gonzo_PhD on 2006-08-19
XGL is working great now except for one problem. I can't open the synpatic pakage manager in the XGL session. It prompts me for the password, I enter it and it won't open. I try opening it again, but it still won't open. The password is correct because it doesn't prompt me again. What could be wrong?

Thanks

---

### Post by bulldog on 2006-08-19
[http://www.ubuntuforums.org/showthread.php?t=239238](http://www.ubuntuforums.org/showthread.php?t=239238)

Read this. I think you have Quin repo enabled?
There was an update that wasn't just as good as it should be.

But there is a fix for it.

---

