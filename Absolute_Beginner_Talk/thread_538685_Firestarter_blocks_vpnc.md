---
title: "Firestarter blocks vpnc"
date: 2007-08-30
forum: Absolute Beginner Talk
---

### Post by Raptor45 on 2007-08-30
I set up vpnc to work, but after I installed firestarter it would still connect but the internet didn't work. Disabling firestarter lets everything work again.

How can I fix this? I dislike running without a firewall.

---

### Post by yabbies on 2007-08-30
I believe you need to open the port for vpnc. Like you would if you have a P2P client or running a remote desktop.

get either the port for vpnc or the gateway ip
start firestarter
click the policy tab
right click on the list marked Forward service and select Add rule. You will be presented with a dialog for creating a new policy rule.  When finished click the Apply Policy button to apply the changes.

Firestarter manual is found[ here]("http://www.fs-security.com/docs.php#docsdownload")

---

### Post by Pumm4 on 2007-08-30
> **Raptor45 said:**
> I set up vpnc to work, but after I installed firestarter it would still connect but the internet didn't work. Disabling firestarter lets everything work again.

How can I fix this? I dislike running without a firewall.
If the above mentioned doesen't help you I can write a small tutorial for [COLOR=black]**Lokkit**[/COLOR]; > GUI based program that helps you configure and activate a firewall on your Ubuntu system.

...it does a great job of set-ting up a basic firewall, asks the right questions, and is very easy to use) [IMG]http://www.mysmiley.net/imgs/smile/winking/winking0050.gif[/IMG]

---

### Post by grasu on 2008-02-20
The solution can be found [COLOR="Red"][here]("http://www.bradrowley.net/index.php/archives/16")[/COLOR]

---

