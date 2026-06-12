---
title: "Macbook Pro 8,2 (2011): Fans running high all the time"
date: 2012-09-05
forum: Apple Hardware Users
---

### Post by garthrodgers on 2012-09-05
I'm quite new to Ubuntu, though I've dabbled in the past, and decided recently to go full cold turkey and make the switch from OS X on my Macbook Pro. I've enjoyed working out all of the niggles which have inevitably come up, though one in particular has been quite tricky - the problem that most Macs seem to have with excessive heat.

I installed macfanctld as per the documentation for my macbook's model (8,2), which ran fine, although I started to get a little annoyed with the way it would quite often seem to be driving the fans at what sounded like 100%. While I was looking for a possible solution, I came across mbpfan ([http://task3.cc/projects/mbpfan/](http://task3.cc/projects/mbpfan/)), which appealed because it seemed to have been created as a direct reaction to the issue I myself had with macfanctld.

Before I go any further, I'll explain the problem I've got, and then go on to say how I got there. Basically, since installing mbpfan, my fans are running at 100% all the time. It's made my laptop very cool :P, but probably isn't doing the fans or battery life any favours, and is making a lot of noise.

So, as to how I got to this position. I installed mbpfan, following the instructions here: [http://task3.cc/projects/mbpfan/](http://task3.cc/projects/mbpfan/). Newbie that I am, I've only really installed software using apt or Ubuntu Software Centre, and don't really know much about "make", compiling and all that jazz.

I uninstalled macfanctld using 'apt-get remove' to avoid any potential conflicts with mbpfan, which was fine, and set mbpfan to run at startup, again following the instructions. However, once the process started, and now whenever it starts when I start up, the fans immediately go to 100%, and stay there.

So my question has two parts:

1. Why are the fans running like this all the time? Is it to do with sensors not reporting temperatures correctly, which causes mbpfan to tell the fans to go to 100%, or something else?
2. If there's no way around this, how can I remove software which I've not installed using apt, but have 'made'?

Sorry if this is all really obvious stuff. I'm just tearing my hair out trying to find a way through!

Thanks in advance :)

---

### Post by garthrodgers on 2012-09-05
OK, so Google turned out to be my friend for the 2nd question ;). I've removed mbpfan for the time being, and am back to using macfanctld. I think the relief of not having the constant hum of fans in the background has made me slightly more amenable to the occasional burst of high activity from macfanctld, but I'd still be interested to know if anyone has had any success with mbpfan or an alternative fan daemon to macfanctld?

---

### Post by dgraziotin on 2012-10-24
> **garthrodgers said:**
> OK, so Google turned out to be my friend for the 2nd question ;). I've removed mbpfan for the time being, and am back to using macfanctld. I think the relief of not having the constant hum of fans in the background has made me slightly more amenable to the occasional burst of high activity from macfanctld, but I'd still be interested to know if anyone has had any success with mbpfan or an alternative fan daemon to macfanctld?

Or, you could have contacted the maintainer of mbpfan, who is very happy to see his software being tested and adopted :-) 
I am developing mbpfan and testing it on different macbooks and different GNU/Linux distributions, with the help of kind volunteers.

I am planning to generate .deb packages in the future.
However, I would like first to gather some feedback from people and seing mbpfan become more useful for every other MBP models.

In particular, I am working with two kind Archlinux users to solve an [issue related to your Macbook Pro model]("https://github.com/dgraziotin/Fan-Control-Daemon/issues/24"), which looks exactly like your issue.
See the comments there if you would like to test the related experimental version. Otherwise, wait for v.1.5.0.

By the way, you can uninstall mbpfan using 
```
sudo make uninstall
```
from mbpfan sourcecode directory.

Cheers!

---

### Post by LinuxBill on 2013-01-11
This could well be the problem I currently have. I have macfanctl installed right now and the fans are going mental with no real impact. I think that im going to try and install your pacge to see if it has better perfromance.

---

