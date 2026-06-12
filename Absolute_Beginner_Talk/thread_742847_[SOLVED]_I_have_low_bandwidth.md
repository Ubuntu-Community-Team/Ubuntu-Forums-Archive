---
title: "[SOLVED] I have low bandwidth"
date: 2008-04-02
forum: Absolute Beginner Talk
---

### Post by faytaliti on 2008-04-02
I have a 2Mbps connection but I am not getting the same speed I used to get on windows.
Also my repositories are not getting updated at all. :confused: (not even at a snail's pace !!!!!!!). 
So I thought I'd ask you guys &/or gals out there in this fast shrinking world for some help..................... please :mrgreen:

---

### Post by caravel on 2008-04-02
How are you connected to the net?  Router or modem?  If so which model of router/modem do you have?

---

### Post by mikeserv on 2008-04-02
If I understand you correctly, you're talking about the slowness of the repos specifically, right?  I fully understand, if you're using the main server, that can slow down to less than 3k a second at times, especially with this new version of Ubuntu coming out this month.  Try this:

System > Administration > Software Sources

Click on the dropdown for "Download From:" and choose "Other."  A dialog window should pop up with a myriad of selections for various servers around the world.  It may take some trial and error, but try some of the servers close to you until you find a really fast one.  Personally, I use the mirror.cpsc.ucalgary from Canada and I get between 400k and 600k a second when downloading from the repos.

-Mike

---

### Post by hyper_ch on 2008-04-02
if websites are generally slow, you may want to disable IPv6

---

### Post by faytaliti on 2008-04-02
I have already disabled ipv6 & i have a huawei quidway QA1003A router with wifi but i only use the LAN connection to go online

---

### Post by hyper_ch on 2008-04-02
so is it just teh repos that are slow or general inet traffic?

---

### Post by faytaliti on 2008-04-02
Thanks mikeserv ! That worked. I am using the server you use. But my internet connection is still slower than on windows

---

### Post by faytaliti on 2008-04-02
wait. packages are still not downloading

---

### Post by mikeserv on 2008-04-02
Well, that can take some work to figure out.  Do you still have Windows installed?  Have you tried any of the online bandwidth evaluators?  I know cnet has one that works ok...  And I think there's one at whatismyip.com.  Maybe run the same bandwidth-ometer in Windows and in Linux to verify.  It could have something to do with drivers for your NIC, but I kinda doubt it.

-Mike

---

### Post by mikeserv on 2008-04-02
Packages aren't downloading at all?  That's scary...  I can't say I understand why.  I'm really kinda new to Ubuntu myself, I've been at it for six months or more, but once I get everything working right I don't fiddle too much.  Have you added any 3rd party repos?  Go back into the Software Sources and click on the 3rd party tab and uncheck anything in there.  Then go back to the first tab and make sure all of those boxes are checked (except for the cd boxes at the bottom, make sure they're all unchecked.).

Then rinse, repeat.

-Mike

---

### Post by mikeserv on 2008-04-02
If that still doesn't work then try a different server.  I think that Canada server is a small one, sometimes it doesn't have all of the packages I want, and, seeing as how you're using Hardy Heron, I can't double-check it for you.

-Mike

---

### Post by faytaliti on 2008-04-02
No. I have this problem in my gutsy system......Anyway I only downloaded 8.04 to check it out :popcorn:

---

### Post by mikeserv on 2008-04-02
Well, I just installed a package with the Canada server and it was lightning quick.  Did you check all of your sources?

-Mike

---

### Post by faytaliti on 2008-04-02
Also, I did conduct those bandwidth tests. On vista it shows 2.02 Mbps but on Gutsy it shows a horrible 102kbps :confused:

---

### Post by TenPlus1 on 2008-04-02
Try installing the plugin FasterFox on Firefox to optimize your browser for faster browsing...  That'll definately help the web site of things...

Also, check your router and make sure the firewall isn't turned up to a high level that affects internet speeds...

Check your overall speed here: [http://www.speedtest.bbmax.co.uk/](http://www.speedtest.bbmax.co.uk/)

---

### Post by mikeserv on 2008-04-02
Wow, that totally sucks!!!  I've never heard of such a thing.  You've seriously got to get to the bottom of that situation, man.  I'm sorry that I can't help you more right now, I just wouldn't know where to start.  Do some googling.

-Mike

---

### Post by faytaliti on 2008-04-02
hey the connection works perfectly on feisty 7.04 live CD:popcorn:

---

