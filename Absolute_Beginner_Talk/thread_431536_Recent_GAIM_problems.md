---
title: "Recent GAIM problems?"
date: 2007-05-03
forum: Absolute Beginner Talk
---

### Post by Catfish81 on 2007-05-03
Hi this is not entirely Ubuntu related, but my cousin and I run PCs side-by-side  and about 2 days ago both of our GAIM clients connecting to MSN stopped logging in. Has anyone else had this issue recently? I've checked the GAIM website forums but there's no mention of problems on there.

---

### Post by kgriffin on 2007-05-03
No problems with it recently here.

---

### Post by jkblacker on 2007-05-03
Me neither I'm afraid!

---

### Post by wataboutbob on 2007-05-03
I've had this problem for the last 2 weeks... both GAIM and Kopete as I'd installed it to check if GAIM was the issue. Haven't bothered trying to fix it as most chats for me are now through google chat anyway.

---

### Post by Sef on 2007-05-03
You could download Amsn via Add/Remove or Synaptic.  It is an Amsn clone.

---

### Post by gerrymoth on 2007-05-03
> **Catfish81 said:**
> Hi this is not entirely Ubuntu related, but my cousin and I run PCs side-by-side  and about 2 days ago both of our GAIM clients connecting to MSN stopped logging in. Has anyone else had this issue recently? I've checked the GAIM website forums but there's no mention of problems on there.

I've had the same problem Monday and Tuesday of this week. I have AIM/Yahoo/MSN setup in Gaim and the AIM & Yahoo logged in okay, but the MSN never. If I disabled and enabled MSN it started to work again.

Check last night and its working fine again. Might just be a problem with the connection to MSN, I know my old WinXP MSN used to be a bit flacky every so often.

---

### Post by metaphor- on 2007-05-03
ive been running windows live messenger and gaim on two seperate computers and I can from experience say that the MSN network crashes, MANY A TIME! ive had to do some odd things to get it working, even reinstalling.  Its microsoft, the ford tempo of the computer world..

---

### Post by 3rdalbum on 2007-05-03
What version of Gaim are you running?

Users of Gaim 2 beta 4 have recently been complaining about crashes while using the MSN service. AMSN doesn't want to connect on my computer, and Kopete from Dapper seems to have problems. In one instance, my Kopete crashed at the exact same time as the person who I was talking to had their Kopete crash.

Happily, you can compile the latest Gaim beta (now called Pidgin 2 beta 7), and this will fix the crashing problems. It may also fix your login problems.

---

### Post by jvc26 on 2007-05-03
No issues here I'm afraid - I have had it disconnect me from time to time, but I think thats just due to the general issues with MSN seemingly to not be 100% stable all the time.
Il

---

### Post by UltimaDude on 2007-05-03
No problems since I started using Ubuntu

WLM always had problems though.

---

### Post by InuyashaDuelist on 2007-05-03
Get the latest version, and if it's still going on after that... are you sure you're using the right password?

---

### Post by Catfish81 on 2007-05-04
I've updated GAIM to v 2.0.0beta6 and the same thing occurs.
I installed AMSN also and it too fails to connect.
I thought maybe my router was stopping it (since it's happening on both PCs) and added a port range entry for it but that doesnt help either.

I've tried pinging the messenger.hotmail.com server and I can't ping it. This is consistent with the error messages as they say that it "can't connect". But why can't I see the servers if everyone else in the world can? The rest of the internet works perfectly for me.

I'll try removing the profiles and re-adding them. Yahoo in GAIM works fines as well. This is starting to tick me off.

PS: Also now tried changing proxy settings etc. in the profile options, no go. Keeps saying "Unable to connect" which I guess means "can't contact the server". I also get this error: "Connection error from Notification server: Reading error"

---

### Post by brodiepearce on 2007-05-11
I'm having a similar issue with Gaim Beta6, for some reason it just doesn't automatically connect when I start it.  I just says "Available waiting for network", and I have to select offline then available again for it to actually start the connection process.

---

### Post by Sloddy Shipper on 2007-05-13
hi, gaim has gone wrong for me the past two days. I can log in ok and see contacts status and they can see me online but i can't send/receive messages. I get 'messages cannot be sent because the user is offline' even though i can see they are online.

If I run gaim from a terminal i get the following output

libnm_glib_nm_state_cb: dbus returned an error.
  (org.freedesktop.DBus.Error.ServiceUnknown) The name org.freedesktop.NetworkManager was not provided by any .service files

Anyone shed some light on what this means?. I did uninstall network manager a while back but gaim has worked normally since then.

---

### Post by Catfish81 on 2007-05-17
GAIM (and MSN in general) suddenly came good for me.

Just an issue with useless M$ software?

---

