---
title: "How to isolate networking slowness?"
date: 2006-11-14
forum: Absolute Beginner Talk
---

### Post by jingo811 on 2006-11-14
Hi ever since I started using Ubuntu surfing on my main bookmarks seems very slow.  Now what 1,2,3 step-by-step procedure can I do in order to find out where the problem lies?
How do I know if it's because of Ubuntu, my router, my wire or my ISP that's the problem maker? :-k

---

### Post by featherking on 2006-11-14
you could try running a traceroute and look at the times for each hop. 

Go to System > Admin > Network Tools. Then go to the TraceRoute tab, enter the url that you want to test, hit trace and let it finish.

The first hop should be your computer to your router(if you have one) if that is really slow then you know its a local speed issue. if its really slow anywhere else it could be an isp issue, if the website fails to load completly its probably a webserver issue

Also, try running a test(download and upload) at [http://www.testmy.net]("http://www.testmy.net") to see if you are getting average speeds for your ISP. (Test results are compared to other results from your same ISP if available)

---

### Post by featherking on 2006-11-14
Also,

If only your bookmarks seem slow, it could be too large of a cache configured in your web browser. If they get too big they bog things down instead of help

---

### Post by steve.horsley on 2006-11-14
One thing thast used to be mentioned a lot here was disabling IPv6 in firefox. Some people claimed great improvements this way. Enter the address **about:config** into the address bar, search for **ipv6** adn double-click the entry to set disabled to true.

It's worth a try.

---

### Post by jingo811 on 2006-11-14
Well now after 6 hours or so when I startup my PC, browsing the Internet seems as quick as I'm used to again.
So it must've been my ISP having some technical problems, the local newspapers have complained about them for some month now.
Or it's because Firefox emptied it's cache tonight.

Either way tnx for all your valuable tips and tricks.  They'll come in handy at a later time when I learn how to play with Ubuntu server :KS

...crap now it starts to slow down again guess I'll have to do the bug tracing after all.

---

