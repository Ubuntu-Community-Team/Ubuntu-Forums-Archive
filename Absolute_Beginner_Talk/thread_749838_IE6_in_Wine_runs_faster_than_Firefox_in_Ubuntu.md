---
title: "IE6 in Wine runs faster than Firefox in Ubuntu"
date: 2008-04-08
forum: Absolute Beginner Talk
---

### Post by SlappyPappy on 2008-04-08
What is up with that?

Also, the fonts look much better in IE6 than Firefox in Ubuntu.

Man, I've got some work to do to get Firefox to look better. Tired of the jagged font look.

---

### Post by Crafty Kisses on 2008-04-08
> **SlappyPappy said:**
> What is up with that?

Also, the fonts look much better in IE6 than Firefox in Ubuntu.

Man, I've got some work to do to get Firefox to look better. Tired of the jagged font look.

I don't have any problems with Firefox.

---

### Post by JoshuaRL on 2008-04-08
It will probably depend on how you have your install set up and how many add-ons you have.  Firefox can become really bloated if you let it, but it can be fast and quick if you pay attention to that too.

Plus, Firefox is at least one generation better than IE6.  So it has a lot more support and features.  It's the reason IE7 has tabs, RSS, and a lot of other stuff.  I made a small super simple browser in VB once that kicked the pants off of IE6.  But then again, it probably wasn't secure in the least either.

---

### Post by Crafty Kisses on 2008-04-08
Yeah, if you want speed, I'd suggest you get Swiftfox.

---

### Post by vexorian on 2008-04-08
* Get Firefox 3 beta 5.

* Set the firefox font to bitstream sans vera.
* Disallow web pages from changing the font.

Get used to the new font (it is hard initially, but once you get used to it you'll notice it is much better than whatever MS font and aliasing IE uses.

If even firefox 3 beta is slow to you, disable compiz.

---

### Post by SlappyPappy on 2008-04-08
Thanks for the tips lads. Can't wait to put them to use.

---

### Post by ramjet_1953 on 2008-04-08
Here are a few tips to speed-up Firefox.

1. Disable ipv6
To do this, simply create a file [COLOR="Blue"]/etc/modprobe.d/bad-list[/COLOR]
Put this line in the file: [COLOR="Blue"]alias net-pf-10 off[/COLOR]
Save the file
NOTE: You will need to do this using the [COLOR="Blue"]sudo[/COLOR] command

2. Open Firefox and type this in the search bar: [COLOR="Blue"]about:config[/COLOR]
a. Find the setting [COLOR="Blue"]network.http.pipelining[/COLOR] Set the default to to [COLOR="Blue"]True[/COLOR]
b. Find the setting [COLOR="Blue"]network.http.proxy.proxy.pipelining[/COLOR] Set the default to [COLOR="Blue"]True.[/COLOR]
c. Find the setting [COLOR="Blue"]network.http.pipelining.maxrequests[/COLOR] Set default to [COLOR="Blue"]40[/COLOR].
d. Restart

3. Change the DNS server settings in your router to OpenDNS
First record the two sets of addresses before changing them, for backup.
Replace the address with these:
[COLOR="Blue"]208.67.222.222
208.67.220.220[/COLOR]
Re-start your router and system

Enjoy!

Regards,
Roger 8)

---

