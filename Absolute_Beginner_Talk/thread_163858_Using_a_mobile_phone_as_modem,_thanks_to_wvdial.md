---
title: "Using a mobile phone as modem, thanks to wvdial"
date: 2006-04-21
forum: Absolute Beginner Talk
---

### Post by gr0kzer0 on 2006-04-21
This isn't a howto, as I haven't got this down pat yet - for a start I'm having to run wvdial to maintain connection as root, which is _not_ advisable. But I'll try and sort that out. In the meantime, if anyone else wants to try this, I connected my moble phone (Nokia 3220) to my laptop with a USB-Serial data cable, then ran wvdialconf. This detected my phone as a modem! I then edited my /etc/wvdial.conf file so it looked like this:

[Dialer Defaults]
Modem = /dev/ttyUSB0
Baud = 230400
Init1 = ATZ
Init2 = ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
ISDN = 0
Modem Type = Analog Modem
Phone = *99#
Username = A
Password = B
New PPD = yes
Stupid Mode = 1

Then I ran wvdial in a console, switched to gnome and started firefox. And here I am!

Read the wvdial man pages before you try this. I'll try to write a better guide once I've sorted out the permissions stuff etc, but you need to know wvdial anyway so you can get your wvdial.conf file right for you.

---

### Post by catlett on 2006-04-21
Just curious. Do you have dial-up internet sevice? Is this why this works? You connect to your cell phone and it dials the internet service number and connects the computer to the service? 
Or are you getting into a wireless service somehow or some other service? I guess I'm asking, is this only a way to replace a modem that is used for dial up service? Will it connect any computer or  it won't connect a computer without an internet service provider?
Either way it's pretty resourcefull, I'd say it gets the "Macgiver" award of the month.

---

### Post by gr0kzer0 on 2006-04-21
>Just curious. Do you have dial-up internet sevice? Is this why this works? You connect to your cell phone and it dials the internet service number and connects the computer to the service?
Or are you getting into a wireless service somehow or some other service? I guess I'm asking, is this only a way to replace a modem that is used for dial up service? Will it connect any computer or it won't connect a computer without an internet service provider?

I don't have dial-up, no. I have a gsm mobile phone, and my mobile service includes gprs connection and unlimited data transfer for a fixed fee. I think all gsm service includes gprs, it's used for multi-media messages and wap, but you can use it to get on the internet too. DNS etc is all dealt with by the mobile netwok. Instead of dialling a normal phone number to get connection, I dial *99# (some networks may be different).

Be aware: my costs are fixed, as I have unlimited data transfer for a fixed fee. But a lot of mobile agreements charge per MB of data transferred, so you'd have to watch your browsing.

I think this is, in a way, better than wi-fi, as I can now surf the internet from anywhere with mobile signal - not tied to wi-fi hot-spots.

---

### Post by catlett on 2006-04-21
I understand now. That's ingenious. What gave you the idea? I didn't even grasp it when you said it, never mind come up with the thought. I'll have to try and see if I can get that working. I was about to pay for another internet service (wifi) but why not use my cell phone internet service?! That's great. Finally a break on internet.
I'm sure everyone else is in the same boat. I have broadband at home and 4 cell phones (for the family) all with internet access. I was about to get Verizon wireless broadband (It's a wifi service but supposedly they are going to have nationwide {US} service and high download rates) for a laptop. We have a plan at work.
But screw that now. I'll be on the lookout for your how-to.

---

### Post by gr0kzer0 on 2006-04-21
>What gave you the idea?

It was Pawel, one of the developers of gnokii, who gave me the clue. Gnokii is an app for linking mobile phones to computer to transfer data back and forth. On the gnokii-users mailing list I asked Pawel if it was possible to use gnokii so I could use my phone as a modem. He replied that I didn't need gnokii to do that, just use the phone. I couldn't really go into it with him on the list as it was off-topic and he's a busy guy, but it made me think. Then, I read about wvdial while trying to compile a driver for my laptop's built-in winmodem... I wondered if its modem detection would find my phone... so I tried it and it worked! I haven't got it all perfect yet, but at least it works.

---

### Post by gr0kzer0 on 2006-04-21
Something I'd find interesting/useful while I'm messing with this is an indication of connection speed. I'm using Firefox as my browser. When you're downloading something with Firefox, it tells you the download speed. Is there a way of getting Firefox to show you the connection speed while you're browsing?

---

### Post by catlett on 2006-04-21
The closest thing I could find was the extension "Fasterfox". It had some tweaks and could prefetch files etc. But I don't know if you can get the data out of it. I think the extension does klnow it. I have it installed on my firefox and when you go to another link fasterfox keeps a time record in seconds. I don't know if it is tracking download speed as well or just the time in seconds but it might be worth a little research. There may have been another extension (there have been so many since that competition).  I didn't see any but I also didn't get through them all.

---

### Post by gr0kzer0 on 2006-04-22
Wow. I just did an update with Synaptic over the mobile link and watched the download speed display. It was up and down constantly, anywhere from 1000 to 8000 B per sec. At one point it jumped to 19K per sec, for a few seconds. Not the fastest, most consistent of links. But if you have a UMTS phone (known in UK as 3G) the rates are _much_ faster.

---

### Post by airtonix on 2006-05-12
Oh yeah ..I also did this ...but on windows.....with a three phone...

although they say its a 56kbps modem...what they dont say is that the gprs gets you some fast downloads....i remeber once i got 100k/s. but it is pricey ....vodafone australia sell monthly accounts of 500 mb quotas or you can opt for their pcmia gprs device for direct connect to your laptop for a bit more.

---

