---
title: "DNS related slow connection"
date: 2011-06-09
forum: Any Other OS
---

### Post by mr91nk on 2011-06-09
Originally posted [here]("http://forums.linuxmint.com/viewtopic.php?f=157&t=74577").

Hi all

I know slow connection issues keep popping up on various forums every now and then, and wanted to share my most recent experience.

My connection (ISP: Comhem Sweden, 24Mbit) slowed down and pages got stuck at ”Sending request” in Chrome (11.x and 12.x) refusing to load at all, and no error messages showing. Occasionally pages would load, but incredibly slowly (several minutes for an ordinary newspaper for example)

*For those of you who doesn’t want the whole story: I finally set the IP of the secondary DNS as primary, and vice versa, in the router. Problem disappeared instantly.*

What confused me most was that the problem appeared only on one computer, a desktop AMD64 with 2GB RAM and a Belkin wifi USB dongle, running Linux Mint Debian Edition. Two notebooks (one XP and one Vista) and an Android phone (HTC Desire) was running fine all along. To start with, I tried a bunch of random actions:

[list]
[*]Clearing browser cache etc 
[*]Changing browser to Firefox 
[*]Disabling the “Predict network actions to improve page load performance” option in Chrome 
[*]Restarting the computer 
[*]Resetting the (Cisco-something) router. Also tried Changing channel on the router, trying different encryptions (WEP, WPA…) and disabling the firewall.
[*]Moving the wifi antenna in order to improve signal[/list]

Googling this issue indicates that most common suggestion regarding “slow connection” problems is that it is DNS related. I came across two rather common suggestions (neither one helped for me, but seems they help for some people):

[list]
[*]Disabling the “Predict network actions to improve page load performance” option in Chrome
[*]Adding “options single-request” to /etc/resolv.conf. I don’t fully understand what this does, but I’m sure Google will help you find out if you are interested. :)[/list]

Finally, after many hours, it hit me that perhaps pinging the DNS’ could give me some kind of idea. I started on the Vista machine, pinging both primary and secondary DNS and everything looked normal. Then I went back to the Linux computer and pinged the secondary DNS and it was fine as well. But then, to my surprise, pinging the primary DNS resulted in a 100% packet loss! I still have no idea why that is (and why it happens only on one specific computer), so I can’t say that I solved the problem, but the workaround that helped instantly was, as mentioned above, to set the secondary DNS IP as primary, and vice versa, in the router.

Any thoughts/comments on this? Similar experiences?

---

### Post by scarleo on 2011-10-31
I have the same symptom with Chromium/Chrome being ridiculously slow and just gets stuck on Sending request... And loading a page might take 2-3 MINUTES(!). However Firefox and Opera are very quick an well functioning. I did try changing DNSs but still same problem. When I ping my DNS it's responding like expected. If anyone has any thoughts on what to try or why this is happening I'd appreciate some tips. I have tried all the standard things like:

[LIST]
[*]Clearing browser cache etc
[*]Disabling the &#8220;Predict network actions to improve page load performance&#8221; option in Chrome
[*]Restarting the computer
[*]Restarting router
[*]Moving the wifi antenna in order to improve signal
[*]etc etc
[/LIST]
Thanks.

EDIT: This [http://falcon1986.wordpress.com/2010/06/01/how-to-speed-up-google-chrome-on-ubuntu/](http://falcon1986.wordpress.com/2010/06/01/how-to-speed-up-google-chrome-on-ubuntu/) seemed to have almost completely "solved" it for me, chromium is now fast.
So basically, if you see this as a workaround or a solution is up to you, what to do is: 
sudo nano /etc/nsswitch.conf

Find the line:
hosts: files mdns4_minimal [NOTFOUND=retutrn] dns mdns4
Change the order so it says:
hosts: files dns mdns4_minimal [NOTFOUND=retutrn] mdns[FONT=monospace][B]4

Ctrl+X and be done with slow Chromium!
[/B][/FONT]

---

### Post by Perfect Storm on 2011-10-31
Moved to Other OS/Distro Talk.

---

