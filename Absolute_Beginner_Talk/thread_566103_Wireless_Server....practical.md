---
title: "Wireless Server....practical??"
date: 2007-10-03
forum: Absolute Beginner Talk
---

### Post by ptrott on 2007-10-03
Hi people...be gentle...newbie in your midst:)

 I would like to set up a server in my home office, mainly to host a web site and to handle emails.
The potential problem is that the broadband connection is wireless, and to get an acceptable signal
they had to mount the microwave antenna on a shed 30 metres from the office where the PCs are located. Thus I have a wireless LAN because running a cable to the router, which is in the shed, was not practical.
My first question is, is it feasible to run the proposed server on the wireless LAN?
If not, what about cable from the 2 PCs to the server PC, (all in the office) then wireless to the router (in the shed)?

Thanks,
Phill.

(if this is do-able, i want to set up an old PC with kubuntu 6.10 & edgy as the server)

---

### Post by Jussi Kukkonen on 2007-10-03
Unless you want a very high bandwidth in the local network, the two options should be about equal... What you suggest will work (if your wireless cards connect ok to the base station),  but it's up to you if the quality is good enough for you. I assume the web site will be most difficult to get working well.

There are two separate problems here: bandwidth and latency: The latency will be a sum of the latencies on your wlan and the microwave link. Actual Bandwidth will be the minimum of wlan bandwidth and microwave bandwidth -- and the wlan bandwidth is mostly "shared": if you transfer a movie from PC to PC wirelessly, the server may have real problems putting out web pages through the same WLAN.

Email and storage are not going to hurt if your latency goes through the roof, but don't plan on playing any games over two wireless links... Hosting a website might be difficult -- it's definitely not an ideal setup for that. If this is a serious website we're talking about, I suggest 3rd party hosting...

Long story short: no way to tell without testing, but don't expect stellar performance.
Btw, I have no idea how microwave links work, but make sure the upstream bandwidth is big enough if you intend to host a website -- a consumer connection might not cut it.

---

### Post by ptrott on 2007-10-03
> **Jussi Kukkonen said:**
> Unless you want a very high bandwidth in the local network, the two options should be about equal... What you suggest will work (if your wireless cards connect ok to the base station),  but it's up to you if the quality is good enough for you. I assume the web site will be most difficult to get working well.
There are two separate problems here: bandwidth and latency: The latency will be a sum of the latencies on your wlan and the microwave link. Actual Bandwidth will be the minimum of wlan bandwidth and microwave bandwidth -- and the wlan bandwidth is mostly "shared": if you transfer a movie from PC to PC wirelessly, the server may have real problems putting out web pages through the same WLAN.

[B][I]The LAN bandwidth should not be a problem...no movies between PCs. 
The wireless connection to the router holds a pretty steady 54Mb/s and I still have the option to use higher gain antennas on the wireless cards. VOIP will be used on this router, BUT will be cabled to the router, not wireless. That however will not ease the microwave latency issue you raised I gather??
Th microwave link is supposed to support 2G/512 and I only have a 1500/256 connection. Not sure if that eases you mind any on microwave link bandwidth question ??[/I][/B]

Email and storage are not going to hurt if your latency goes through the roof, but don't plan on playing any games over two wireless links... Hosting a website might be difficult -- it's definitely not an ideal setup for that. If this is a serious website we're talking about, I suggest 3rd party hosting...

***Not looking at a 'Serious' web site. Just looking at being able to load heaps of photos on there, but there will not be much traffic. (only porn pics get serious traffic:))***

Long story short: no way to tell without testing, but don't expect stellar performance.
Btw, I have no idea how microwave links work, but make sure the upstream bandwidth is big enough if you intend to host a website -- a consumer connection might not cut it.

***I'm a bit hesitant to tackle this unless it is very likely to be a success, so I'll see what you think with the added information, and hopefully some other input from others.***

[B][I]Thanks for your input so far.
Cheers,Phill.[/I][/B]

---

### Post by hyper_ch on 2007-10-03
I don't think it would cause too much of a problem... hosting a website or emails don't generate too much traffic... you shouldn't send emails larger than 10 mb anyway... and displaying a webpage doesn't use much bandwidth...

As pointed out before, if you run p2p apps or transfer movies from/to your server then the performance for the website/email could be bogged down...

The only problem I see is that if you want to setup an email server you should get a dedicated IP address (and those aren't that cheap - at least here...)

---

### Post by Jussi Kukkonen on 2007-10-03
> The microwave link is supposed to support 2G/512 and I only have a 1500/256 connection
I assume those numbers are kilobits per second (the "2G" seems a bit odd though), The 256 kbps uplink is probably going to be your weakest link bandwidth-wise -- that's pretty slow for serving images.

If you haven't taken a look at hosted solutions, I think you should: Web hosting or a hosted (virtual) linux server are fairly affordable nowadays. This solution has it's own drawbacks, but I thought I should mention it.

---

### Post by ptrott on 2007-10-04
Thanks gents, you have given me some other choices and also some serious considerations before starting this project.

Cheers,
phill

---

### Post by dwhitney67 on 2007-10-04
Is there anything that prevents you from putting the server in the shed?  You could always connect to it (from your office) using another computer and SSH.

---

