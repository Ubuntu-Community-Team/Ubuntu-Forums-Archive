---
title: "Setting Ubuntu up as a (bandwidth shaping) server for Windows computers"
date: 2006-03-27
forum: Absolute Beginner Talk
---

### Post by smallsaul on 2006-03-27
hello!

OK, we have:

4 computers running XP
1 computer running linux (ubuntu)
1 network switch
1 cable modem

we'd like to set the ubuntu computer up as a pure server routing the bandwidth from the cable modem to the 4 computers around the house.

1) is this possible?
2) is it easy?
3) do we need any special "bandwidth shaping" software to do this? bearing in mind we want to give people "dedicated" bandwidth (lots of us use downloading programs that eat up the low upload speed and make it unfair on others when downloading. and it also causes our cheap (belkin) router to crash and needs to be reset. 
we have a 10 meg download, but only 384k upload,
4) do we need any other equipment? (we have 2 network cards on the linux machine)

5) could you helpful people point us in the right direction? websites? free software? etc etc?

thank you thank you thank you.
thanks

---

### Post by nanotube on 2006-03-28
1) is this possible?
yes

2) is it easy?
if you dont know much about networking, maybe not so easy. but you should be able to find tutorials online about setting up a linux router.

3) do we need any special "bandwidth shaping" software to do this? bearing in mind we want to give people "dedicated" bandwidth (lots of us use downloading programs that eat up the low upload speed and make it unfair on others when downloading. and it also causes our cheap (belkin) router to crash and needs to be reset. 
we have a 10 meg download, but only 384k upload,

if your only concern is the upload of a couple machines dedicated to filesharing, its probably easiest to just set upload limits in the filesharing software you use (eg, any bittorrent client worth its salt has that capability). if that does not sound like a good option, you could look into tcng for traffic shaping ([http://tcng.sourceforge.net/)](http://tcng.sourceforge.net/)), but it is not easy to set up.

4) do we need any other equipment? (we have 2 network cards on the linux machine)

no, you do not need any extra equipment. in fact, if you decide not to do traffic shaping at the router, and have the "downloader" computers limit their own uploads, you do not even need the linux router - you could just keep using your belkin router (unless its just a switch, in which case you might have to invest like $20 to get a cheapo router).

5) could you helpful people point us in the right direction? websites? free software? etc etc?

a google search for "linux router" or "iptables router linux" should turn up quite a few tutorials on that. if you do decide to do traffic shaping with tcng (though there are probably other tools out there too), then that tcng website would be a good start, though a google search for 'tcng howto' or 'tcng tutorial' might turn up some good stuff, too. 

have fun. :)

---

### Post by ubuntuuser on 2006-03-28
You maybe want to use IPCop instead of ubuntu for this. [http://ipcop.org/]("http://ipcop.org/")
It is a complete Linux Firewall Distribution, and also capable of traffic shaping. They have a VMware image for download, so you can have a look at it.

---

