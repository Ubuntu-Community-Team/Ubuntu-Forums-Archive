---
title: "Wired Network Connection"
date: 2007-04-25
forum: Absolute Beginner Talk
---

### Post by bruce50 on 2007-04-25
Every time I start or restart, I have to click to 'Wired Network' option to select my network card.  Is there some way to make this automatic?

---

### Post by leibowitz on 2007-04-25
No.

I mean the solution is to click on the network manager icon (top right) and just select "configure manually". Then configure your network and it will work at every boot.

Automatic configuration is more for people connecting to many different connection on the same day. At least that's what I think.

---

### Post by zvacet on 2007-04-25
Like leibowitz sed select "configure manually".That will take you to the network settings,and then
highlight your modem>properties>choose type of connection(dhcp or static)>close.In the DNS tab you will see address.Replace it with your nameservers>close.
```
sudo pppoeconf
```

---

### Post by bruce50 on 2007-04-25
thanks but I already tried that a few times.  I find it hard to believe that every time I start ubuntu, I will have to manually select the only network card I have in my system.

---

### Post by leibowitz on 2007-04-25
You don't have to select the card.

You have to go to manually configure the card. That's something you do one time. Be sure to disable the "roaming" profile (or something called like this).

Just go to System menu, Administration, Network.

Click on the card, properties, Activate this card.

And you can still delete Network manager if you want. But try with it first. You can do it!

---

### Post by bruce50 on 2007-04-25
ok here's what I did

System > Administration > Network > keyed in password the Network settings windows appears, there is a checkmark in the box to the left of 'Wired connection" it's address is DHCP.  I click on Wired connection to highlight it and click on 'Properties'  In the Properties window enable roaming is unchecked  and configuration is set to DHCP.  click OK, Click Close and restart computer.  When the desltop returns, the Network Manager shows 2 computers, one with a red exclamation point.  Highlighting the icon shows "No network connection" as before.  Clicking on the icon brings up a small window with two choices, 1. Wired network (with an empty option circle next to it) and 2. Manual configuration.

I plan to run this computer without a monitor and connect to it from a other computers using VNC,  obviously, that will not work if I have to 'activate' the wired network card every time I reboot.

What am I doing wrong?

---

### Post by leibowitz on 2007-04-25
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/network-manager/+bug/82927](https://bugs.launchpad.net/network-manager/+bug/82927) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				Even if the icon says "No network connection", please try to see if you have one. Here what you did is tell to NM that he won't handle your connection anymore.

So he think nothing is connected. But you are. Try to ping anything, before clicking on that NM of hell.
That's why I just un-install this network manager if I don't need it. And it's way better without it.

Again, please check yourself if you have a connection and don't trust what NM says. If you don't have one, then un-install this piece of s**t.

---

### Post by speeddemon8803 on 2007-04-25
uninstall what exactly?

Were not uninstalling nuthin here...were gonna make this work...if thats the last thing we do.

---

### Post by bruce50 on 2007-04-25
When NM says there is no network connection, it is correct.  Firefox unable to connect to websites, ping unable to find my gateway router.  I looked at the bug thread you referenced and didn't see a resolution (for me, at least).  If NM were to be uninstalled, how would I configure my network card?  This is my first day with Linux so go easy on me.  I just want the computer to be automatically connected to my network upon startup.

Thanks for all the help so far.

---

### Post by medad on 2007-04-25
You might want to unplug both the router and the modem to see if that might be causing the problem.  Give it about 10 seconds and then plug them back in.  I had a similar problem last, but it was with Windows XP,

---

### Post by bruce50 on 2007-04-25
thanks medad but I don't think the problem lies with the router/modem.  One of the tests I did earlier was pinging the dhcp assigned address with a persistant ping (-t switch) before, during and after restarting.  responses stopped as expected with the system was rebooting.  They restarted only after manually clicking on the 'wired network' option as I mentioned above.

---

### Post by medad on 2007-04-25
Sorry that I wasn't any help.  The first thing I always do when my system acts weird or in this case loses it's internet connection is check the cables, turn off the computer completely and restart and do the same with the modem and router.  That usually fixes my problem (This is on my Ubuntu system).

---

### Post by bruce50 on 2007-04-25
Impatience got the best of me.  I uninstalled NetworkManager, rebooted and the network connection was there as it should be.  I'm slightly curious as to way NM wasn't working but at least I automatically have a connection

---

### Post by Mell0s on 2007-06-04
Thanks bruce50! I was looking for this for a long time too and i couldn't find it anywhere. But i do hope that it has no bad consequences that NM is uninstalled.

Anyway, thanks a lot!

---

### Post by Vaidya on 2007-07-27
Hi Bruce.

Thanks for this thread.

I have been trying unsuccesfully to get this done myself.

I have tried ppoeconf 

Tried reading through huge number of posts and googled away

In fact, I have managed to get most of my issues resolved by reading the excellent posts in the forums (including some which state that removing NM breaks the desktop etc)

AND rants on why ppl like me (ADSL router) should just reconfigure the router to just (duh forgot...) but to just work directly with the internet or something.

I AM going to take that stupid NM off and take my chances again.

And ya, the bug report is there all right, so I am just waiting for this to be fixed...

Whew...

But, yes, I did get rid of XP and am on Feisty full time now and having a good ride!

Thanks again.

---

