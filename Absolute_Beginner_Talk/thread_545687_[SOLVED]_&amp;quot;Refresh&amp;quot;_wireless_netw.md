---
title: "[SOLVED] &amp;quot;Refresh&amp;quot; wireless network?"
date: 2007-09-07
forum: Absolute Beginner Talk
---

### Post by dwiedenfeld on 2007-09-07
How do I "refresh" my wireless network connection?

If my wireless gateway goes down or is turned off (I don't leave it running all of the time) when I boot Feisty, when the wireless doesn't come up, Feisty doesn't seem to "find" it. That is, I can get no connection. (In other words, if the wireless gateway is on when I boot up, it works fine. It's just that the wireless has to be on first.)

I've found two solutions, but both are pretty slack:
1. Reboot. Then Feisty finds the wireless connection and it works fine,
2. Go into "Network" and de-select the wireless connection, select a wired connection (there's no wired connection so it obviously doesn't work), save it, then open it again, de-select the (non-functioning) wired connection and choose the wireless one again, and save it again. Then it seems to re-detect the wireless connection and it works fine.

But both of these are less than satisfactory.

Is there some easy command that will just "repair" or "re-detect" the wireless connection?

---

### Post by robtg on 2007-09-07
Are you sure it's not finding your connection?  I have an issue where I don't always pick up a DHCP address on my wireless NIC and the symptom is that I can't connect to anything.

The next time this happens, open a terminal and type **sudo dhclient**

This will attempt to acquire a new DHCP address for your PC.  

I'm not sure why I have to do this (about 60% of the time) but it always works.

-Rob

---

### Post by dwiedenfeld on 2007-09-07
I don't know, but your suggestion sounds good--I'll try it. I suspect that it's probably something that's pretty easy, but being a total newbie to Linux, I don't know it.

---

### Post by cubeist on 2007-09-07
what works for me is right-clicking on the network icon (in the menubar) and turning off wireless, then I wait a couple minutes and turn it back on... works about 60 -70% of the time... the rest of the time I have to reboot... I will also try the dhclient thing to see if it works for me!

---

### Post by dwiedenfeld on 2007-09-10
OK, I've tried both of these suggestions (above) and neither works. DHclient tells me that no DHCP licenses are available, and it's "sleeping." Disabling networking and enabling it doesn't do anything. My previous two solutions (re-booting and de-selecting then re-selecting wireless networking) both still work.

Any other suggestions from anyone? I appreciate it,

---

### Post by chrome307 on 2007-09-10
Have you tried using WiFi Radar??

---

### Post by dwiedenfeld on 2007-09-10
No, didn't know it existed. I see it's available in Synaptic and has a web page--I'll go look. Thanks.

---

### Post by dwiedenfeld on 2007-09-10
Ok, that didn't work, either. Maybe it's my unfamiliarity with Wi-Fi Radar. When it was connected I could disconnect, but when I tried to re-connect (after having entered the profile and WEP key), it said it could get no IP address. Maybe the profile I entered was not right, but I did all I know. (One thing is that it doesn't actually say anything about WEP...).

---

### Post by chrome307 on 2007-09-10
When you logged in did you save this information ?

Also when you enter your login details are you sure your entering them in the right format eg Hex/Decimal etc ??

If you've logged in earlier, your simply just missing a step ..... your 99% there already!!

BTW You can drag your 'preferred' connection to the top of the list and rearrange them in any particular order.

---

### Post by UbuntuniX on 2007-09-10
Can't you just click the nm-applet button, then click the current connection?

---

### Post by asmoore82 on 2007-09-10
> **dwiedenfeld said:**
> How do I "refresh" my wireless network connection?

```
~$ sudo /etc/init.d/networking restart
```

will restart the neworking subsystem ... you could create an **alias** so you don't have to
type or tab complete all that everytime ...

```
~$ echo 'alias wiifresh='\''sudo /etc/init.d/networking restart'\' >>~/.bashrc
~$ source ~/.bashrc
```

from then on, the new alias command **wiifresh** will do the same as typing it all out.

---

### Post by dwiedenfeld on 2007-09-10
> **UbuntuniX said:**
> Can't you just click the nm-applet button, then click the current connection?

No, that doesn't work.

---

### Post by dwiedenfeld on 2007-09-10
> **asmoore82 said:**
> ```
~$ sudo /etc/init.d/networking restart
```

will restart the neworking subsystem ... 


This looks like maybe what I was looking for. I'll try it next.

---

### Post by dwiedenfeld on 2007-09-11
> **dwiedenfeld said:**
> 

Code:
~$ sudo /etc/init.d/networking restart

This looks like maybe what I was looking for. I'll try it next.

Yes--worked! That's what I was looking for, I think.

---

### Post by asmoore82 on 2007-09-11
> **dwiedenfeld said:**
> Yes--worked! That's what I was looking for, I think.

My Dlink router and IBM T42 can take 2~3 "refreshes" to pick up after a "location" switch;
but it always works on the first shot with a reboot :-/ ...

I'm almost getting into the habit of
```
~$ sudo /etc/init.d/networking stop
```
Then switching location with the GUI, then
```
~$ sudo /etc/init.d/networking start
```

Sometimes I wonder why the GUI doesn't do all this in the background for me;
but I remember that it's never a problem on Ethernet, just WiFi.

---

