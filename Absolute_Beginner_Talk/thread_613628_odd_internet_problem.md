---
title: "odd internet problem"
date: 2007-11-15
forum: Absolute Beginner Talk
---

### Post by kleo skywalker on 2007-11-15
I use an ADSL modem which connects to my computer through its ethernet port. I turn off the modem at night and turn it back on in the morning. 
Things were fine till I was using Feisty, but since I switched to Gutsy, I can't connect to the internet for a long time (like an hour) after I turn on the modem. I can ping, but webpages don't open.
Why could this be happening and how do I fix it? It is a really annoying problem.
Thanks.
P.S.: Please do not post arbit search results - if I had found a solution in existing threads, I would not have posted.

---

### Post by Znort_Ubern00b on 2007-11-15
Do a search of threads/forums as i think this has been commented on elsewhere.

---

### Post by kleo skywalker on 2007-11-15
> **Znort_Ubern00b said:**
> Do a search of threads/forums as i think this has been commented on elsewhere.

That might be, but I couldn't find anything relevant when I searched. So I posted afresh hoping for a solution specific to my problem.

---

### Post by SpiritIsReality on 2007-11-15
[http://www.google.ca/search?hl=en&q=site%3Aubuntuforums.org+gutsy+slow&btnG=Google+Search&meta=](http://www.google.ca/search?hl=en&q=site%3Aubuntuforums.org+gutsy+slow&btnG=Google+Search&meta=)
[http://www.google.ca/search?hl=en&q=site%3Aubuntuforums.org+gutsy+%22internet+connection%22&btnG=Google+Search&meta=](http://www.google.ca/search?hl=en&q=site%3Aubuntuforums.org+gutsy+%22internet+connection%22&btnG=Google+Search&meta=)
[http://www.google.ca/search?hl=en&q=ubuntu+gutsy+slow+to+reach+internet+%22router+problems%22&btnG=Google+Search&meta=](http://www.google.ca/search?hl=en&q=ubuntu+gutsy+slow+to+reach+internet+%22router+problems%22&btnG=Google+Search&meta=)
[http://www.google.com/cse?cx=002165917076592449621%3Ay8jmiivon3o&q=gutsy+adsl+modem+problems&sa=Search&cof=FORID%3A1](http://www.google.com/cse?cx=002165917076592449621%3Ay8jmiivon3o&q=gutsy+adsl+modem+problems&sa=Search&cof=FORID%3A1)

---

### Post by Mud.Knee.Havoc on 2007-11-15
A couple of the links posted might lead you in the right direction (although start from the last one and go backwards - the first one - googling "gutsy" and "slow" doesn't find a thing related to your problem).

When you say you can ping, are you referring to trying to ping [www.google.com](www.google.com) or the ip address?  If you can only ping ip addresses, but not domain names, I'd change your DNS servers (System->Administration->Network) to use OpenDNS (their nameservers are 208.67.222.222 and 208.67.220.220).  You might want to do this anyway, they provide some decent services as well as traditional DNS.

And when you do figure out your problem, please come back here and make a note of how you got through it... the next person with this problem will be happy that you did! :)

---

### Post by kleo skywalker on 2007-11-15
I think the DNS servers etc are entered correctly. As I said, it's not that I can't connect to the internet at all. The problem is that when I turn on my modem, I can't connect to the internet right away -  I have to wait for like an hour. After that, I can connect to the internet normally.
By ping, I mean using the ping tool under System-->Administration-->Network tools. I use the numbers given to me by my ISP provider - one to check if the modem is working, and one for their server.
As far as the search results go, I (obviously) searched for solutions to this problem before posting. I didn't find any relevant to my specific problem (or close) so I asked here.

---

### Post by bigken on 2007-11-15
disable ipv6 in the browser type about:config in the search filter type ipv6 changer the value from true to fales 

hope this helps

---

### Post by kleo skywalker on 2007-11-15
> **bigken said:**
> disable ipv6 in the browser type about:config in the search filter type ipv6 changer the value from true to fales 

The value is already false.

---

### Post by louieb on 2007-11-15
Hum adsl modem turned off. Then after turning back on can only ping but browser does not display a web page.  What have you tried in order to fix it? anything?  Sounds like a slow connection. a couple of things:
Have you disabled IPv6? [http://louboldt.com/ilinuxmisc.htm#ipv6](http://louboldt.com/ilinuxmisc.htm#ipv6) 

My dsl provider suggest keeping the modem on in order to optimize service. But haven't noticed that it makes much difference.

BTW: theres another way to disable IPv6 in Gutsy.

---

### Post by sailor2001 on 2007-11-15
check with your isp.. it looks like the modem is searching for the correct mac address for you. My isp said it could take up to 4 hours to recycle mac addresses.. Why are you turning the modem off? other than for storms.

---

### Post by kleo skywalker on 2007-11-15
> **louieb said:**
> Hum adsl modem turned off. Then after turning back on can only ping but browser does not display a web page.  What have you tried in order to fix it? anything?  Sounds like a slow connection. a couple of things:
Have you disabled IPv6? [http://louboldt.com/ilinuxmisc.htm#ipv6](http://louboldt.com/ilinuxmisc.htm#ipv6) If not you need to work on your search skills. 
My dsl provider suggest keeping the modem on in order to optimize service. But haven't noticed that it makes much difference.

Isn't the absolute beginner forum a place to help people who are new to ubuntu and linux, and maybe even computers? So if you have a possible solution to someone's problem and you post it, that's very kind of you but if not, then please leave out comments about people's computing abilities and searching skills - they are not your concern and they are not the measure of anything.

ipv6 is already disabled. I haven't tried anything to fix it, because I don't know what the problem or the solution is - that is why I'm on this forum asking for help.
I don't know if it's a "slow connection" because once connected it is not slow at all. It is normal for the connection to take a couple of minutes to start after I turn on the modem, but almost an hour is too much. Moreover, this wasn't happening when I was using Feisty.

---

### Post by kleo skywalker on 2007-11-15
> **sailor2001 said:**
> check with your isp.. it looks like the modem is searching for the correct mac address for you. My isp said it could take up to 4 hours to recycle mac addresses.. Why are you turning the modem off? other than for storms.

What are mac addresses? (I don't know if this information is relevant, I'm on manual network configuration, and set to Static IP.)

---

### Post by bigken on 2007-11-15
ok give it try with ipv6 as true also try to manually set your dns servers in the router


this is what I would try ipv6 false set router for dhcp go to adsl providers web site and find out what there
dns is and manually set it in the router

---

### Post by philinux on 2007-11-15
The ipv6 setting in about:config should be set to true to disable it.

It's worth a shot as it's easily changed.

---

### Post by kleo skywalker on 2007-11-15
I'm not making much headway with the suggestions posted so far. I hope there are solutions other than just keeping the modem on!
bigken, when you say manually change the dns, do you mean the settings on the network tool on the top right panel?
philinux, I changed ipv6 to true but couldn't figure out how to disable it.
What is the actual point of doing that? I mean, what are the possible reasons behind this problem?

---

### Post by louieb on 2007-11-15
> **kleo skywalker said:**
> Isn't the absolute beginner forum a place to help .... but if not, then please leave out comments about people's computing abilities and searching skills - they are not your concern and they are not the measure of anything....ipv6 is already disabled. ..
:lolflag:I got a big mouth I need it so my foot will fit.  This dog will bite.

Since disabling IPv6 hasn't helped. Have you ruled out out that your modem or network card isn't broke? See if another computer has the same problem or If you dual boot does windows work right away? Maybe the modem or your network card is going out and only functions correctly after warming up.

---

### Post by bigken on 2007-11-15
If I were you I would ditch the modem and buy a modem/router much easier and more reliable plus they very easy to setup 

also what is the make of the modem and who is your broadband provider ?

if you go to system administration there is a network icon from here you can set your dns ect

---

### Post by SpiritIsReality on 2007-11-15
> **kleo skywalker said:**
> Isn't the absolute beginner forum a place to help people who are new to ubuntu and linux, and maybe even computers? So if you have a possible solution to someone's problem and you post it, that's very kind of you but if not, then please leave out comments about people's computing abilities and searching skills - they are not your concern and they are not the measure of anything.

ipv6 is already disabled. I haven't tried anything to fix it, because I don't know what the problem or the solution is - that is why I'm on this forum asking for help.
I don't know if it's a "slow connection" because once connected it is not slow at all. It is normal for the connection to take a couple of minutes to start after I turn on the modem, but almost an hour is too much. Moreover, this wasn't happening when I was using Feisty.
tx that's what I want to bve when I grow up. A googler., a searcher, and hopefully sometimes a finder. or a fireman. or a firefighter. firemen are in town . firefighters aren't, when they're workin. off duty , that's a different story.
gone to google.com learnin the hard way.

---

