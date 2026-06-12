---
title: "Frustrations using ubuntu on many networks"
date: 2006-08-10
forum: Absolute Beginner Talk
---

### Post by moaxey on 2006-08-10
loving ubuntu, i change networks (every day more than once) there must be other people with similar problems...

[LIST]
[*]sending mail (need to change smtp servers per locations)
[*]changing proxy servers (so many different places, so boring)
[*]synaptic through proxy servers (http authentication not supported)
[/LIST]

I've been searching the web for weeks re need to manually reconfigure my sending mail options every time i change networks. I cannot do this 100% accurate, and I frequently end up with my mail disappearing forever into black holes if i have the wrong settings in the wrong contexts. 

This is a big problem for me. It never used to happen when I was on mac.

i'm sure postfix must be the answer, but the configuration guides are impossible for me to understand, and none look at my problem directly. Been searching/experimenting for weeks on this one cant work it out. Flaky communications are costing me work and respect.

And then there's proxy servers, need different ones in different places... and i can probaly write a script to quit all my network applications, replace text in configuration files... (mostly mozilla, network proxy and synaptic) but it seems so messy, surely theres a really smart way... like being able to tell where i am from network tools, and adjusting settings appropriately.

and the proxy situation for synaptic is almost impossible for me. I have been able to do updates by putting my proxy authentication in the url, but the network fascists at my institution have made it impossible to authenticate that way. Why not just use network proxy which has the option to store the username password?

Thats not ubuntu's fault but theirs, must hav m$ shares as they dont support linux and would prefer me to not use it on their network.

There must be many other people with experiences like these?

---

### Post by timhaughton on 2006-08-10
I'm out and about a lot on client site with my Ubuntu laptop. Like you, I don't enjoy having to change my proxy settings all the time, here's what I do.

Back at the office, I run an OpenSSH server.

When I'm on site, I ssh back to base instructing ssh to act as a socks proxy server, like so.

ssh -D 8080 [email]mylogin@myIPAddress.com[/email]

Then login over ssh like normal. Now I have a local Socks proxy running on port 8080.

I install tsocks on my laptop, and configure it to use my local socks proxy. Now once the secure tunnel is up, all I need to do is run...

tsocks evolution&

And evolution's network traffic is transparently intercepted and routed back to my office. This works for Firefox, GAIM etc. I don't need to change any settings in any of my client software, because it's just like being in the office from their perspective.

Incidentally, this is a really useful thing to do if you're on an unencrypted WiFi hotspot because all of your traffic is encrypted.

To check, if you go to [www.whatismyip.com](www.whatismyip.com) you should see your home/office IP address.

Regards,

Tim

---

### Post by moaxey on 2006-08-13
Hey thanks,

although i'm still battling to get it going, i'm sure i will get there eventually...

just working on getting it going between computers at home network, before dealing with proxies and network address translation issues.

So can I clarify your method:

[INDENT]When I'm on site, I ssh back to base instructing ssh to act as a socks proxy server, like so.

ssh -D 8080 [email]mylogin@myIPAddress.com[/email]
[/INDENT]
do you mean when you are off site you ssh first to start socks server on base?
[INDENT]
Then login over ssh like normal. Now I have a local Socks proxy running on port 8080.

[/INDENT]
from the laptop to the base, socks proxy running on base, not laptop?
[INDENT]

I install tsocks on my laptop, and configure it to use my local socks proxy. Now once the secure tunnel is up, all I need to do is run...

tsocks evolution&

[/INDENT]

at home, can ssh to another computer at home, and tsocks to it. It is pretty slow old machine and anything I do in that context times out. Get these error messages from evolution

Error while performing operation.
Welcome response error: Transport endpoint is not connected

Error while Fetching Mail.
Failed to read a valid greeting from POP server mail.***.net

both computers can do internet separately.

---

