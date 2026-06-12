---
title: "Torrent programs kill my wifi connection"
date: 2006-12-11
forum: Absolute Beginner Talk
---

### Post by Westies on 2006-12-11
I'm connected to a DI-524 via a DWL-G122 rev B usb Wi-Fi adapter. Whenever I use a torrent program like KTorrent or Azureus, shortly after my internet connection drops and I can no longer ping my router. Even if I shut down the torrent program, close the network connection from unchecking the box in System > Administration > Networking, waiting a moment and rechecking it, I still cannot ping the router until I reboot the computer.

---

### Post by Westies on 2006-12-11
bump

---

### Post by Westies on 2006-12-11
bump...

---

### Post by stoeptegel on 2006-12-12
You are not the only one with wifi problems, but you can try two things.

1. Lower the max connections in the BitTorrent client
2. If your /etc/resolv.conf file has dns entries pointing to your router, replace them with the real dns-server addresses of your ISP.

Btw, 32bit or 64bit OS?

PS. Please do not crosspost.

---

### Post by Chinkostu on 2006-12-12
Its a problem with the D-link router. you'll need to do a firmware update, i've read about these problems while troubleshooting a friends network

[http://support.dlink.com/default.asp?orig=1#](http://support.dlink.com/default.asp?orig=1#)

select DI and 524 in the boxes. i can't post a direct link to the page (javascripted?? no idea, i tried before)

[http://www.dlink.co.uk/?go=jN7uAYLx/oIJaWVTALoZU9f8nJUIKOZUTMyka/O31g24UoR/l7wvNJIjNqVh7jg=](http://www.dlink.co.uk/?go=jN7uAYLx/oIJaWVTALoZU9f8nJUIKOZUTMyka/O31g24UoR/l7wvNJIjNqVh7jg=)

^UK site

---

### Post by Westies on 2006-12-12
> **stoeptegel said:**
> You are not the only one with wifi problems, but you can try two things.

1. Lower the max connections in the BitTorrent client
2. If your /etc/resolv.conf file has dns entries pointing to your router, replace them with the real dns-server addresses of your ISP.

Btw, 32bit or 64bit OS?

PS. Please do not crosspost.

Sorry about the crosspost, I realize it's generally frowned upon, but this forum moves a bit quickly and after 2 bumps it didn't seem like I was going to get many results. Anyways, it's a 32bit OS. I'll check out that file shortly as I'm on my own computer at the moment and the problem is on my fathers PC.

Chinkostu: If it was an issue with the router, shouldn't the same thing happen in Windows XP? I have no problems using utorrent in XP, though perhaps Ubuntu handles things differently?

edit: Just replaced the DNS from the routers IP to the real DNS servers. Also updated the router firmware from 1.21 to 1.23. I'll make a new post to let you know how it goes.

---

### Post by Chinkostu on 2006-12-12
it works fine in XP? thats odd...its no different in how it works in Ubuntu AFAIK.

---

### Post by Westies on 2006-12-12
Still have the same problem. It lasted at least 20 mins, not sure how much longer than that (screen saver goes up after 20 mins, and I checked it earlier after it came up and it was still working. Checked it again just now, a while later and it's no longer working.) Any other ideas?

---

### Post by Westies on 2006-12-12
bump

---

### Post by stoeptegel on 2006-12-12
Since you said it worked the first 20 minutes i have another idea to try, but it is trail and error one: You could try using dnsmasq on your system as a dns proxy instead of the normal route.

This is how to configure it properly:
(it assumes you use a broadband modem/router+modem which does the login on the internet for you)
```

1. Install dnsmasq
$sudo aptitude install dnsmasq

2. configure dnsmasq
$sudo vi /etc/dnsmasq.conf
and search for "listen-address" by typing the following as soon as the editor opens:
/listen-address [enter] (line 71 probably)

Found it? Good! Go in insert mode with the i so you can start edit the file.
Now remove the # at the start of the line with delete and add the number 127.0.0.1 to the end right after the = token.
Now save the file by switching from insert mode to command mode of vi by hitting escape and giving it ":wq" (w for write, q for quit. You could also do :w enter and :q enter..)

3. configure dhclient
$sudo vi /etc/dhcp3/dhclient.conf
and search for the line with "#prepend domain-name-servers 127.0.0.1;"
Found it? remove the # at the beginning and save and exist the file.

4. add dnsmasq proxy manually to resolv.conf
$sudo vi /etc/resolv.conf
and make room on the top for a new line "nameserver 127.0.0.1"
Save file again.

5. restart dnsmasq
$sudo /etc/init.d/dnsmasq restart

Done!
```
(Credits should go to [http://ubuntu.wordpress.com/](http://ubuntu.wordpress.com/) btw)

I cannot guarantee this will fix anything, but it is worth trying i guess.

---

### Post by Westies on 2006-12-16
11 hours after trying that fix the internet is still working :)
So, either that worked, or it's because my download was capping off at about 80KB/s all night due to poor signal strength since a couple of doors were closed last night (where previously Azureus cap the download at 150 and my internet connection would max at 220). I'll open those doors and see if having it run at 150KB/s makes any difference.

Edit: Nevermind... as I just woke up, I figured it was running all night, but apparently about an hour ago my brother unplugged the USB adapter and plugged it back in because the internet wasn't working.

---

### Post by Westies on 2006-12-16
Well, it died again. Maybe it has something to do with the drivers? Perhaps I should try using the ndiswrapper? Also, the MTU wouldn't have anything to do with it, right? It's set to 1492 in the router connection settings and 1500 on the PC.

---

### Post by Westies on 2006-12-16
Probably useless info, but the Activity light and the Link light turn off when the connection dies. The usb adapter is still detected by ubuntu though. The lights also turn off when you uncheck the connection in the Sys>Admin>Networking box as well (which should come to no surprise.)

---

### Post by Westies on 2006-12-16
bump

---

### Post by Westies on 2006-12-16
](*,)

---

### Post by Westies on 2006-12-16
edit: removed unnecessary whining :P

---

### Post by Westies on 2006-12-17
I'm going to give this another bump before I give up completely... As annoying as it is, I kinda want to know how the problem should be solved.

---

### Post by stoeptegel on 2006-12-18
Sorry Westies, i only check this forum once a week or so, sometimes even less...

> 
  Well, it died again. Maybe it has something to do with the drivers? Perhaps I should try using the ndiswrapper? Also, the MTU wouldn't have anything to do with it, right? It's set to 1492 in the router connection settings and 1500 on the PC.


No that is ok, the router should take care of that. It will only use bigger packets in the inside(LAN) than in the outside(WAN), which is totally normal.

Though I do not know if this would possibly make a wireless network less stable. I guess you could try to lower that a little a see how it turns out.

You could also, as a last resort, try to disable DHT as see it that makes any difference. That dnsmask improves the stability for your wifi is interesting to know, though p2p over wireless is known to be a hassle to begin with when you use some types of routers. Look here:
[http://utorrent.com/faq.php#Modems_routers_that_are_known_to_have_problems_with_P2P](http://utorrent.com/faq.php#Modems_routers_that_are_known_to_have_problems_with_P2P)

---

### Post by IceFire on 2006-12-22
I have exactly the same problem, but I'm on a wired connection. **Any** bittorrent program will work for 1-5 minutes and kill the connection. **No** traffic will go anywhere after that. I'm using xubuntu 6.10 on a old laptop. I don't know much about linux, but I've tried to stop and restart the connection, nothing works except restarting.

---

### Post by arthur_kalm on 2007-01-05
Hi everyone,

I have the same problem and but am on wired connection (same as IceFire). This has really been bugging me for a long time. The connection cuts out at random times, sometimes working for most of the day. Anyone have any more suggestions?

---

### Post by dannyboy79 on 2007-01-05
i used to have this same problem, i have a netgear router and a motorola surf cable modem. ethernet cable (no wireless) the prpblem has to do with you flooding your upload capacity so that there is no room for any header packets. you need to set your upload limit to about 80% of your total rate. for instance, my company says I have a 5megabits download and 1.5megabits upload. now when you convert that to Kbytes that is only 640Kilobytes down and 192Kilobytes upload. well we know this is total bs, so I went to a website that tests my connection, I found out that I could download at around 350K and upload at about 75K. So what I did was take the 75K max upload rate and multiplied it by .8 (that would make 80%) and I got around 60. so now I know that when I open a couple torrent together the TOTAL between them all shouldn't be more than 60K. Does this make sence? Ever since I found this out I don't have a propblem anymore. I use bittornado for this, it's awesome. In windows I used to use Netfilter or something like that which would set and hold max limits for uploading and downloading of certain programs but when I went to linux I had to find a bittorrent client that had this incorporated. I also set my max download rate as well but I believe the upload is the most important because your cimputer needs to be able to send packet info and if it's upload limit is maxed out it can't. good luck, I hope this works for you guys as it did for me. FYI, I use Bittornado setting for slow broadband which is 13K up and I set it to 100 download limit, keeep in mind that this is PER torrent and I normally don't open more than 3 torrents at a time. max upload connections are around 4 to 6 per torrent. With these settings I have has a torrent download at 135K and when I set my upload to 60, I was able to download the torrent at around 350, the guy I was attached to must have had T1 or something, it was great. HE HE

---

### Post by NHaGa on 2007-10-31
I have this same problem with Linksys Router and USB adapter. I didn't have the problem in WinXP but had the problem in Feisty and now I have it in Gutsy. I will try to limit the upload but I think it's a still linux bug somehow.

I'll post results as soon as possible

---

### Post by NHaGa on 2007-11-13
It seems this has been solved... and it has nothing to do with upload bandwidth.
A big thanks to gb5uqx for posting a fix in this thread:

[http://ubuntuforums.org/showpost.php?p=3755385&postcount=3](http://ubuntuforums.org/showpost.php?p=3755385&postcount=3)

---

