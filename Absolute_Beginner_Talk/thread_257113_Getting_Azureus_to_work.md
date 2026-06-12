---
title: "Getting Azureus to work"
date: 2006-09-14
forum: Absolute Beginner Talk
---

### Post by halcyon on 2006-09-14
I've never really liked Azureus to begin with, but it's the only Linux client that has header encryption (if you know another please tell me! :D).  Problem is, it runs badly.  Tabs and menus function like molasses, high CPU usage, and I can't figure out how to get the torrents I have to actually run.  It's worked fine on Windows, and there's no problems with my router, the port is open and such, yet it says there's a NAT/TCP reachability problem and that my DHT is firewalled, *even though* when I run the firewall test it says the port is open.

It also connects to trackers fine, but I can never establish any incoming or outgoing connections in the torrent.  How would I fix this?

---

### Post by Drakkor on 2006-09-14
Hi,again, halcyon 
You got firestarter up ? Under policy I got this, and it works just fine
don't know what your open ports are.

---

### Post by halcyon on 2006-09-14
I do use Firestarter, but I've tried running Azureus with a policy and without Firestarter at all, still doesn't work.

Also, another quirk is when those dialogue boxes pop up, I click Hide and the highlight border appears around it but it never depresses to close the window ever.  It's acting really weird compared to its Windows counterpart.

---

### Post by Drakkor on 2006-09-14
From what I've gathered,Ubuntu even without firestarter uses something called IP tables , whatever that is ? So everything is more or less blocked from the get-go. I have had problems with the boxes popping up,supposedly there is some .jar file that you have to update to cure this,but I have found that if you stop all torrents,and activity, and go to File>Exit and hit that a couple of times it will shutdown cleanly and when you restart it , it seems to be OK whith no boxes popping up.  Hope this helps a little, Good Luck ! :)
Edit: Ya enjoy the weirdness,lol :p

---

### Post by halcyon on 2006-09-14
From what I know, iptables is like the Windows HOSTS file, and as far as I know I haven't done anything to it, so it should let it through.

The dialogue boxes I know what's causing them haha.  It's getitng mad at me for force killing it when it won't shutdown due to aforementioned weirdness.  It's just that when they pop up I have no way of closing them and it's weird.

I'm going to try running uTorrent through WINE and see if I get the same kind of blockage.  If not, I'll probably stick with it since uTorrent is amazing.

Thanks for the effort though Drakkor :D

---

### Post by Drakkor on 2006-09-14
LOL ! "It's getitng mad at me for force killing it when it won't shutdown"
:D  Sorry I couldn't help more, Good Luck ! :KS

---

