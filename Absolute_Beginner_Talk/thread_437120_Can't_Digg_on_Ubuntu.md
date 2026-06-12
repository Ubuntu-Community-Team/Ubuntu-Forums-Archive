---
title: "Can't Digg on Ubuntu"
date: 2007-05-08
forum: Absolute Beginner Talk
---

### Post by getaboat on 2007-05-08
Firefox on Dapper and Fiesty never load the page. They used to. I've tried not loading images in digg (as per these forums - and cleared cache - no joy)

On IE and Firefox on W98 through the same router - OK.

Oddly traceroute on both Linux boxes never get there - not making the last hurdle. tracert on W98 shows the same route but makes the last hurdle. 

I'm not aware of the firewall blocking anything - but I'm not aware of it running - especially on Feisty. The W98 box runs ZoneAlarm which can be quite twitchy.

Any pointers welcome.

---

### Post by Acglaphotis on 2007-05-08
Did you try another browser? It could be firefox.

-Acgla

---

### Post by starcraft.man on 2007-05-08
> **Acglaphotis said:**
> Did you try another browser? It could be firefox.

-Acgla

LOL, it most certainly is NOT Firefox. Firefox is the majority browser on Digg and most other tech websites. It is most definitely either the way you have configured your network, or some setting in firefox. Let me recommend a quick diagnostic, run this in a terminal:

```
sudo aptitude install epiphany-browser
```

Then open epiphany and direct it to Digg. If digg works, its likely your firefox set up, and I would like to know all your extensions installed ... if it doesn't work either, its something independent of your browser and its likely the network or another system local setting.

PS: I view and Vote on Digg almost daily.

---

### Post by Acglaphotis on 2007-05-08
> **starcraft.man said:**
> LOL, it most certainly is NOT Firefox. Firefox is the majority browser on Digg and most other tech websites. It is most definitely either the way you have configured your network, or some setting in firefox. Let me recommend a quick diagnostic, run this in a terminal:

```
sudo aptitude install epiphany-browser
```

Then open epiphany and direct it to Digg. If digg works, its likely your firefox set up, and I would like to know all your extensions installed ... if it doesn't work either, its something independent of your browser and its likely the network or another system local setting.

PS: I view and Vote on Digg almost daily.



I meant  **his** firefox. A corrupt file or setting.

-Acgla

---

### Post by getaboat on 2007-05-08
Thanks for the replies.

I downloaded epiphany (neat browser!) and it didn't do digg. But I didn't think it would.

As in my original post it's OK on my W98 box with IE and Firefox through the same router. Extensions might be a clue - I'll remove them next. Fiesty has Stumble and Unplug, Dapper has shed-loads, W98 has none.

The only other thing I have done recently (because of CUPS) is go to fixed IP (on the home network) rather than DHCP (W98 included).

Traceroute (after my ISP) output below:
 5  ge2-2.fr1.lon.llnw.net (193.203.5.68)  37.061 ms  28.017 ms  28.861 ms
 6  tge7-4.fr3.lon.llnw.net (69.28.171.137)  33.136 ms  25.093 ms  34.030 ms
 7  tge7-2.fr3.lga.llnw.net (69.28.171.125)  93.844 ms  90.071 ms  113.807 ms
 8  ge2-1.fr3.ord.llnw.net (69.28.171.193)  117.025 ms  124.949 ms  117.055 ms
 9  ge1-3.fr4.sjc.llnw.net (69.28.171.66)  171.863 ms  180.078 ms  174.975 ms
10  ve5.fr3.sjc.llnw.net (69.28.171.209)  169.927 ms  173.896 ms  170.939 ms
11  * * *

on W98 tracert shows the next step as 

digg.ve707.fr3.sjc.llnw.net - then digg.com

---

### Post by getaboat on 2007-05-08
Removed all Firefox extensions - no difference - had to put Stumble  back otherwise I might have to try and pass the time more productively. I'm going to try and dig deeper down the firewall route - if some one can point be to where the default logs will be. Thanks.

---

### Post by Ptero-4 on 2007-05-10
Ask your ISP if they know what linux is. If they do ask them if they support it. If they say that they don´t, then your ISP is the problem (I say that b/c the site fails under linux in every browser but works right in every browser under windoze). If they say they don´t know what is linux then they´re not the problem themselves, but there might be trap code in the router.

---

### Post by getaboat on 2007-05-10
Utterly bonkers. We lost our internet connection for a while today. When it came back it seemed slightly faster and straight to digg.

---

### Post by starcraft.man on 2007-05-10
> **getaboat said:**
> Utterly bonkers. We lost our internet connection for a while today. When it came back it seemed slightly faster and straight to digg.

Oh so it works? Guess your ISP changed something, good for ya. Have a nice time then with Ubuntu and Digg too :)

---

