---
title: "Slow Internet?"
date: 2006-09-17
forum: Absolute Beginner Talk
---

### Post by thomasaaron on 2006-09-17
OK, folks. I took the leap -- in a BIG way.

Not only did I install Ubuntu, but I totally erased Windows wile trying to do a dual boot setup. Anyway, no sense whining over that now. I'm an Ubuntu person whether I want to be or not!

Everything is doing well, and I'm figuring it out.

But my internet connection is quite a bit slower than it was with Mozilla on Windows.

There is a chance that it is just the internet in the building that I'm in.

Do you know if there is maybe some way of telling if it is because of Ubuntu? Or if there is anything I can do to speed it up.

I'm talking about 45 seconds to load up Yahoo.com, as opposed to about 5 seconds when I was using Windows.

It is an ethernet, DHCP connection. I'm using an ACER Aspire 3000 laptop. Generally, it's a pretty quick computer.

You guys'll be seeing a lot more of me around here, I suspect.

Best,
Tom

---

### Post by gauntalus on 2006-09-17
Are you connecting via a wireless or a wired connection?  A lot of wireless cards still have major issues operating in Linux.  If this is the case, try a wired connection and see if you get better results.

If you are already using a wired connection, you probably want to make sure you have the latest driver for your LAN card.

---

### Post by xpod on 2006-09-17
Hi mate and welcome to THE machine:biggrin: 
Sorry to hear about your windows install......PITY:-\" 

Not too sure about your speed issues but you could try swiftfox, although thats not really tackling the cause i suppose.
Im sure someone will point you in the right direction.
Good luck and have fun.....now that your free=D>

---

### Post by tribaal on 2006-09-17
Tell firefox not to use IPv6:

- type in "about:conf" in the url bar
- in the filter field that appears, type in "ipv6"
- double click the only line left, so that it now says "true" in bold

Restart firefox.

Hope this helps :)

- trib'

---

### Post by octothorp on 2006-09-17
I had a problem where Ubuntu was slow to resolve domain names and that caused everything network related to be very slow. The fix I found for that was to edit /etc/resolv.conf and put entries for my DNS servers in there.

---

### Post by thomasaaron on 2006-09-17
> **tribaal said:**
> Tell firefox not to use IPv6:

- type in "about:conf" in the url bar

- trib'

Do you mean the URL bar at the top of Firefox, where you type in where you want to browse to?

When I type it in there, nothing happens.

I'm not sure what the URL bar is, if that is not it.

Best,
Tom

---

### Post by k9brand on 2006-09-17
I think he meant

```
about:config
```

---

### Post by thomasaaron on 2006-09-17
YES!

That made a WORLD of difference.

Thanks a lot, guys.

Best,
Tom

---

### Post by mongooseman1128 on 2006-09-17
WOW... I couldn't get any pages to display at all, I could ping, tracert, and do every other trick I could think of from windows but mozilla wouldn't work at all. as soon as I deactivate ipv6, my internet was up and running. This is also pretty cool, because I've been a windows user for a long time and I'm incredibly proficient with it and I could never find forums half as helpful as this one.

---

