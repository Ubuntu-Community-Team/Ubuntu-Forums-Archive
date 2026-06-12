---
title: "Getting Azareus to work"
date: 2006-11-18
forum: Absolute Beginner Talk
---

### Post by Felix Jay on 2006-11-18
Just trying for the first time ver to dl a torrent on a linux system and if this works then it's goodbye windows forever! 

However, I open a torrent in azareus and nothing happens! It's permanently waiting for a "handshake". Now I know that I am probably doing something stupid. 


Edit - in fact it's just told me I need to have port 16568 UDP open if I'm on a modem/ router (Which I Am Netgear DG632). How would I do this?? 

As ever any help much appreciated - I'm learning a lot! :mrgreen:

---

### Post by aidanr on 2006-11-18
[http://www.portforward.com/english/routers/port_forwarding/Netgear/DG632/Azureus.htm](http://www.portforward.com/english/routers/port_forwarding/Netgear/DG632/Azureus.htm)

you may also need to open that port in iptables, use firestarter for this, you can get that through add/remove programs

---

### Post by nickpaton on 2006-11-18
Love this router - 

And a great HOWTO as well, so thanks for that, Aidenr - will get bookmarked.

RE the static IP, this can be done via the router by getting it to assign a permanent address.

Off the top of the old head:


LAN IP Setup > Address Reservation > Add

In new Address Reservation Window, you should see your Linux PC listed with an IP address against it.  Note that number for Azureus.
Click to put a dot in the left hand bullet box; Click on Add.

This takes you back to the previous LAN IP window, and you will now see your Linux PC listed under Address Reservation.

Click on APPLY (don't forget!)

And click on LOGOUT in bottom LH panel.

You now have a static IP address for your Linux PC.

Reboot the Pc.

---

### Post by Felix Jay on 2006-11-19
Cheers chaps

I followed that as closely as I could and it's downloading anyway! 

My only concern is this afternoon my upload seemsway more than my download but I guess that happens.....

---

### Post by nickpaton on 2006-11-19
You may find uploading to be faster than downloading, especially if there are not too many seeders.
What happens is that initially you start downloading and get a few 100's Kb's of data.
At that point you will have them available to upload.
Then the other downloaders will grab what they can from you and kill your download speed.
One thing you may want to look at is to limit your upload speed.  This is because you have a set amount of bandwidth, and you don't want the upload to take all of it.
For example - I have a 1Mb ADSL connection.  Maximum download with no uploads is around 130Kb/s; Maximum upload with no downloading is around 35kb/s.

So if you are uploading 20kb/s, then the max download is only going to be around 70kb/s.

What I do is to limit my upload speed to 10kb/s and this allows me to get the download and then up the upload speed to seed out to others.

I'm not sure where in Az this setting is precisely but it's in Tools / Config section somewhere.  You may need to set it, close Az and then  restart it again.

Firewall settings - I find that it's best to disable iptables / Firestarter.  If you now have Firestarter installed, just go and disable it.
If you don't have it, disable iptables in a terminal:

```
sudo /etc/init.d/firewall stop
```

The Netgear firewall is fine as it is so you are still well protected.

To restart iptables:

```
sudo /etc/init.d/firewall restart
```

I've always found that you get a hugely better performance increase, probably due to not having the ports open in it. (I need to look into that for myself!!)

---

### Post by Felix Jay on 2006-11-19
Hey Nick, 

I have firestarter but I hadn't configured it and my downloads now seem fine! 

Cheers mate for the advice........

---

