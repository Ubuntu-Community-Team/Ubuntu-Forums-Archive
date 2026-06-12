---
title: "Can't get to Google"
date: 2007-12-13
forum: Absolute Beginner Talk
---

### Post by Gambini on 2007-12-13
Just last night I could get on to Google, but today it won't connect. I'm using Ubuntu 7.10 Gusty and Firefox, but it won't go to it in Opera either. It is the same for Newegg.com, but I can get to most other sites. I booted into my windows partition, and it worked there, so I have no idea what to do. Any suggestions?

---

### Post by Rocket2DMn on 2007-12-13
Sounds like it could be a DNS issue.  Go to System->Administration->Network and click the DNS tab.  These should be compatible with your internet provider which you need to look up online (maybe at another search engine like yahoo), but you can also try third party DNS servers
For now you can also access google by using their IP as the URL - 72.14.207.99

---

### Post by wormser on 2007-12-13
It does sound like it could be a DNS problem.  If you can get to google with 72.14.207.99 in Firefox then it would confirm it.  Here are a third parties DNS server you can use.  

4.2.2.2
4.2.2.1

If you cannot get to google via the IP address then something else is going on.

---

### Post by Gambini on 2007-12-13
Ah, I have the worst of luck,: Yahoo doesn't work. Neither does MSN or Webcrawler (I think that's it). 

If it was a DNS issue, would it not affect all of the websites? I tried to get to Google through the IP and it didn't work, so should I still try those DNS servers?


School is so worthless; I spent quite a bit of money on a couple of tests to get certified for networking, and I can't troubleshoot a network problem. All I can say is "lol".

:lolflag:

---

### Post by Teknyk on 2007-12-13
Next step is to try and ping and trace to google I would say.
If you can't ping it see where the trace dies.

*edit*
I just realized you said it does work from your windows partition so I am guessing your ping will fail and a trace wont make more than the first hop

---

### Post by Dr Small on 2007-12-13
First install traceroute (I don't remember ever having to do this on dapper... but oh well.)
```
sudo apt-get install traceroute
```

And then find where the traceroute fails (if it does) as from Teknyk's suggestion:
```
traceroute google.com
```

---

### Post by Gambini on 2007-12-13
Copy and Paste from terminal for Google:

```
gambini@ubuntu:~$ traceroute google.com
traceroute to google.com (72.14.207.99), 30 hops max, 40 byte packets
 1  * * *
 2  * * *
 3  * * *
 4  * * *
 5  * * *
 6  * * *
 7  * * *
 8  * * *
 9  * * *
10  * * *
11  * * *
12  * * *
13  * * *
14  * * *
15  * * *
16  * * *
17  * * *
18  * * *
19  * * *
20  * * *
21  * * *
22  * * *
23  * * *
24  * * *
25  * * *
26  * * *
27  * * *
28  * * *
29  * * *
30  * * *

```
...not looking too promising.

For comparison, c&p to ubuntuforums.org:
```
gambini@ubuntu:~$ traceroute ubuntuforums.org
traceroute to ubuntuforums.org (91.189.94.186), 30 hops max, 40 byte packets
 1  73.12.179.1 (73.12.179.1)  17.458 ms  29.693 ms  32.304 ms
 2  ge-2-21-ur01.west.tn.knox.comcast.net (63.86.137.49)  34.859 ms  37.433 ms  40.085 ms
 3  te-3-3-ar01.sharpsridge.tn.knox.comcast.net (63.86.136.9)  42.299 ms  43.032 ms  44.707 ms
 4  12.118.120.101 (12.118.120.101)  46.053 ms  47.208 ms  50.587 ms
 5  tbr1.attga.ip.att.net (12.123.20.178)  52.628 ms  53.837 ms  55.791 ms
 6  12.122.96.5 (12.122.96.5)  58.420 ms  15.886 ms  25.230 ms
 7  192.205.34.58 (192.205.34.58)  27.793 ms  30.391 ms  33.400 ms
 8  ae-31-55.ebr1.Atlanta2.Level3.net (4.68.103.158)  40.100 ms  42.795 ms  43.876 ms
 9  ae-68.ebr3.Atlanta2.Level3.net (4.69.134.50)  45.732 ms  46.801 ms  48.077 ms
10  ae-2.ebr1.Washington1.Level3.net (4.69.132.86)  69.760 ms  70.828 ms  71.895 ms
11  ae-81-81.csw3.Washington1.Level3.net (4.69.134.138)  72.964 ms ae-91-91.csw4.Washington1.Level3.net (4.69.134.142)  87.136 ms ae-61-61.csw1.Washington1.Level3.net (4.69.134.130)  85.988 ms
12  ae-72-72.ebr2.Washington1.Level3.net (4.69.134.149)  63.058 ms ae-82-82.ebr2.Washington1.Level3.net (4.69.134.153)  35.610 ms ae-72-72.ebr2.Washington1.Level3.net (4.69.134.149)  36.365 ms
13  ae-5.ebr2.Paris1.Level3.net (4.69.132.114)  133.954 ms  135.032 ms  136.363 ms
14  ae-1-100.ebr1.Paris1.Level3.net (4.69.133.81)  129.340 ms  148.308 ms  149.386 ms
15  ae-2.ebr1.London2.Level3.net (4.69.133.94)  142.120 ms  156.474 ms  157.558 ms
16  ae-16-51.car2.London2.Level3.net (4.68.117.16)  150.377 ms ae-16-55.car2.London2.Level3.net (4.68.117.144)  146.929 ms ae-16-53.car2.London2.Level3.net (4.68.117.80)  152.204 ms
17  195.50.121.2 (195.50.121.2)  153.267 ms  154.393 ms  124.565 ms
18  gw0-0-gr.canonical.com (91.189.88.10)  122.618 ms  122.017 ms  126.012 ms
19  * * *
20  * * *
21  * * *
22  * * *
23  * * *
24  * * *
25  * * *
26  * * *
27  * * *
28  * * *
29  * * *
30  * * *

```
...looks a little bit more promising.

It seems a request doesn't even leave my computer for Google. What should I do now?

---

### Post by Rocket2DMn on 2007-12-13
Definitely sounds like DNS.  Try the DNS servers wormser suggested.  The only other thing it could be is your ISP.

---

### Post by Teknyk on 2007-12-13
His machine resolved it correctly when he traced to it so I doubt it is a DNS issue.
I would be willing to bet a trace to Googles IP would yield the same results.

Maybe try one of Googles other IPs? like 64.233.167.104

---

### Post by Rocket2DMn on 2007-12-13
It's not that his connection to his ISP server is broken (though it could be if he is just accessing local dns storage at his router for these other sites), but his DNS may have bad information stored.
Resetting the router might be enlightening.

---

### Post by Teknyk on 2007-12-13
I don't think he has a router based on his first hop being a public gateway address for comcast when he traced to the forums.

---

### Post by Gambini on 2007-12-13
Tried both of the DNS servers, but they didn't work. Do you think that Comcast is kicking my internet in the rear for being on Linux? Can Comcast even do that? (physically and legally)

I've also tried to use the static IP where I have all of my ports forwarded (not sure how that would help, but worth a try) as well as the DHCP and neither worked. Hopefully it will be resolved like it came on, and be gone by tomorrow. I'll also see what the difference is between my Windows DNS/Host/whatnot and what they are on Linux. If that doesn't work, then I'll call Comcast and see what's up.

Thanks for the help, and continue to pump out the ideas as I'm willing to try most anything.


EDIT: and as I was about to post, I saw 2 more posts! Woohoo!

Google's 2nd IP didn't work either, and I'm about to go reset my router.

EDIT2: Ya, I'm on a laptop and I use a wireless router.

---

### Post by Dr Small on 2007-12-13
No, I don't think comcast could do that. They just provide the service, I don't think they could restrict it per OS.

---

### Post by Teknyk on 2007-12-13
well that is wierd. (to me at least) I wonder why his router didn't show as a first hop on the trace to the forums.

---

### Post by Teknyk on 2007-12-13
> **Dr Small said:**
> No, I don't think comcast could do that. They just provide the service, I don't think they could restrict it per OS.

Not by OS but by protocol they can.

Google sandvines.

*edit*
now I want to know what resetting the router does.

---

### Post by Gambini on 2007-12-13
Resetting router didn't work either (unplugged for 2 minutes or so). If it means anything, I'm using a Netgear wireless router and haven't ever had trouble until today.

---

### Post by Rocket2DMn on 2007-12-13
I would have to suggest that you just leave the problem be for a day or so - I predict it will go away.  If you still have the problem after that, come back and we'll see if we can idea-up anything new for ya.

---

### Post by Teknyk on 2007-12-13
I have two other questions...

did you restart your laptop and modem also?

and for giggles what happens if you bypass your router?

---

### Post by Dr Small on 2007-12-13
[quote=Rocket2DMn]I would have to suggest that you just leave the problem be for a day or so - I predict it will go away. If you still have the problem after that, come back and we'll see if we can idea-up anything new for ya.[/quote]

"*Once you eliminate the impossible, whatever remains, no matter how improbable, must be the truth.*" :D

---

### Post by Gambini on 2007-12-13
Yes, I've restarted my laptop a couple of times (actually the first thing I did) and unplugged the modem as well for about 2 minutes.

And how do I go about bypassing the router?

---

### Post by Dr Small on 2007-12-13
> **Teknyk said:**
> I have two other questions...

did you restart your laptop and modem also?

and for giggles what happens if you bypass your router?
You could try bypassing the router and see what happens.

---

### Post by Gambini on 2007-12-13
and just in case you jumped to the 3rd page: How do I bypass the router? (I'd use google for this usually, but it seems as though I can't! :lolflag:)

---

### Post by Teknyk on 2007-12-13
I am assuming cable modem here based on you being with comcast.

power down modem and laptop.
run cat 5 from modem to laptop.
power up modem.
then power up laptop.

---

### Post by Dr Small on 2007-12-13
Lol. How are you connect to your router ? Wireless or ethernet ?
Either or, you need to plug the ethernet cable coming from your modem into your system, which will completely bypass the router.

Dr Small

---

### Post by Gambini on 2007-12-13
Arrg, I swear that I'm half-retarded sometimes. I didn't realize that the cable going from the modem to the router was ethernet.](*,) I'll post back with the results in about 10 minutes.

---

### Post by Gambini on 2007-12-13
Bypassing the router didn't get me to Google, and traceroute outputs are basically the same at the beginning, so I don't think I need to repost them.

So now, unless someone else has another idea, I'll leave it alone until tomorrow and frollock off to Windows land for a day. I'd like to thank you guys sincerely for all of your help, hopefully It'll work itself out.

---

### Post by Dr Small on 2007-12-13
Since it is still doing it, it is a DNS problem on your ISP's end. There is nothing you can do about it. Just give it time, and hopefully it should sort out all on it's own. If it doesn't I would be calling my ISP on the phone and get it sorted out.

Dr Small

---

