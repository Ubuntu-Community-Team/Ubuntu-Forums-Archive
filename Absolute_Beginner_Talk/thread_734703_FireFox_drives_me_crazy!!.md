---
title: "FireFox drives me crazy!!"
date: 2008-03-25
forum: Absolute Beginner Talk
---

### Post by angel_zone on 2008-03-25
Firefox in my ubuntu is really (i mean it!!:mad:)slow,it could took over 15 minutes to open a web page and this is'n the end after that NOTHING appears!!just blank page this makes me really mad becouse in windows every thing is normal for the same pages i tried to access from ubuntu so any ideas becouz i really hate to get back to windows

---

### Post by scragar on 2008-03-25
try downloading opera, or using konqueror, both are very fast in comparison, alternativly you can try firefox 3(beta's only just yet, but they are still almost completely bug free, and any help finding new bug's is always appreciated).

---

### Post by angel_zone on 2008-03-25
> **scragar said:**
> try downloading opera, or using konqueror, both are very fast in comparison, alternativly you can try firefox 3(beta's only just yet, but they are still almost completely bug free, and any help finding new bug's is always appreciated).

O.K i forgot!! i had installed opera too but the proplem is the same:mad: besides i'm not one of opera's fan i used to like firefox very much but now!!!!!!!

---

### Post by JonathanRRogers on 2008-03-25
> **angel_zone said:**
> Firefox in my ubuntu is really (i mean it!!:mad:)slow,it could took over 15 minutes to open a web page and this is'n the end after that NOTHING appears!!just blank page this makes me really mad becouse in windows every thing is normal for the same pages i tried to access from ubuntu so any ideas becouz i really hate to get back to windows

So, is Firefox slow, or did the web page not load at all? If it's the latter, it's probably not a problem with Firefox, but with more general network configuration. That seems to be confirmed by the fact that "the proplem is the same" in Opera. Can you load any web pages? Is a network interface connected? Can you access any Internet services at all?

---

### Post by awiggin on 2008-03-25
I am having the same problem.  I have something of a connection, because firefox does say "waiting for <website>" and a little (very little) comes up - like one or two words, or just a button, or the icon for the website.  

Plus, I occasionally get a weather update on my weather applet that is accurate.

But functionally, i have no connection.

If you get this fixed, I want to know how.

(NOTE:  I already disabled the ipv6.  It didn't work.  Something is wrong with how I have my wireless internet configured.  Also, this all worked fine a couple days ago on Feisty, before I upgraded to gutsy.)

---

### Post by angel_zone on 2008-03-25
> **JonathanRRogers said:**
> So, is Firefox slow, or did the web page not load at all? If it's the latter, it's probably not a problem with Firefox, but with more general network configuration. That seems to be confirmed by the fact that "the proplem is the same" in Opera. Can you load any web pages? Is a network interface connected? Can you access any Internet services at all?

yes i can!! i'm using pidgin and it connect fast and fine and i had just downloaded kopete but i did that within the command sudo apt-get install not from add/remove list and when i tried to add any thing it asks me to reload then downloading file stuck at file 9 of 18???????

---

### Post by angel_zone on 2008-03-25
and there is another thing when i lost connection firefox tells me that there is a proplem loading the pag or can not establish a connection but never blank

---

### Post by Cresho on 2008-03-25
sounds like hardware and connection issues or even connectivity issue from your isp.  I have no problems at all.  Good Luck!

---

### Post by angel_zone on 2008-03-25
> **Cresho said:**
> sounds like hardware and connection issues or even connectivity issue from your isp.  I have no problems at all.  Good Luck!

well i do'n think it is ahardware proplem i should say i had installed ubuntu befor but aftrer while i uninstalled it then reinstall:)and that proplem was not there

---

### Post by zabien1970 on 2008-03-25
How are you connected? My wireless connection gives me problems constantly but a hard connection works great

---

### Post by angel_zone on 2008-03-25
> **zabien1970 said:**
> How are you connected? My wireless connection gives me problems constantly but a hard connection works great

no i don't have wireless i had wired connection via LAN

---

### Post by ContraWars on 2008-03-25
Problem possibly with the DNS setup?

I'm a noob when it comes to how linux works, but I used to be a windows vista tech support rep, so pardon my poisoned ignorance when I ask how does linux handle a process like the hosts file?

Perhaps going into about:config and making a few adjustments would fix the responsiveness of FF.

---

### Post by Cresho on 2008-03-25
I was going to add configuration as well.  I recently Tossed my wifi router due to problems with my ubuntu...so I thought.  I tossed it because I was unable to modify any settings in my router in either firefox or internet explorer.  I purchased a new router and now everything and my connection works fine....no more dropped signal.  Another time, I lost connection and called tech support from charter.  The tech guy was going to send someone over and I told him I had tons of expirience.  So we talked things over and checked the decible and figured out that there was not enough signal....I said ill fix the problem.  Anyway, I changed a spliter that was hanging around outside (was rusted) and that solved my problem.

I would have you call your isp and do a signel strength check.  I didnt read back and can't remember if you stated "your windows works better" but if it does, disregard this post. :lolflag:

---

### Post by Cerny on 2008-03-25
One you think you might want to do is if it is a router problem, which is sounds like, is upgrade the firmware on the router. Also it could be network manager that could be giving you problems on your connection. Try some other connections like wifi-radar or something similiar.

---

### Post by Driftwood 420 on 2008-03-25
Hello all first post here...Just getting started after a long love affair with OSX.  So far so good.  
I found this to be problem for me as well.  i am not sure what version of ubuntu i am running but this worked for me...  I hope it helps, found it is a search of “firefox slow”


________________________________________
“Have you disabled ipv6 in firefox? Usually a good pace to start. To do so, type "about:config" in the firefox location bar. In the filter box type "ipv6". Then, set disableIPv6 to "true". 

HTH

Cheers, Rick”

---

### Post by easyease on 2008-03-25
i bet its a firefox extension screwing things up, try disabling them all one by one to find the culpret.

---

### Post by warrior24 on 2008-03-25
I am having similar problems 
[http://ubuntuforums.org/showthread.php?t=730560](http://ubuntuforums.org/showthread.php?t=730560)

---

### Post by mike555 on 2008-03-25
You might try different DNS numbers ... like   ...
   208.67.222.222     or   208.67.220.220

---

### Post by funrider on 2008-03-25
try to ping some website to see if there be any connection lag

eg ping ubuntuforums.org

---

### Post by JonathanRRogers on 2008-03-26
So, what about other web browsers, like Konqueror?

---

### Post by warrior24 on 2008-03-27
I tried different ones with no luck

---

### Post by prshah on 2008-03-27
> **angel_zone said:**
> Firefox in my ubuntu is really (i mean it!!:mad:)slow,it could took over 15 minutes to open a web page and this is'n the end after that NOTHING appears!!just blank page this makes me really mad becouse in windows every thing is normal for the same pages i tried to access from ubuntu so any ideas becouz i really hate to get back to windows

I had the same problem, try [http://ubuntuforums.org/showthread.php?t=718709&highlight=prshah+lynx+firefox](http://ubuntuforums.org/showthread.php?t=718709&highlight=prshah+lynx+firefox)

Hope it helps!

---

