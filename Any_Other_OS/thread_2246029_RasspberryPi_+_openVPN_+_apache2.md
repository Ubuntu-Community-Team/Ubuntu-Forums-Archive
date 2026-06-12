---
title: "RasspberryPi + openVPN + apache2"
date: 2014-09-27
forum: Any Other OS
---

### Post by markeee on 2014-09-27
Hey y'all

sorry if this is posted in thr wrong place, wasn't entirely sure where to post!!!
I got myself a raspberry pi a few weeks back and went about setting it up as a small home server for http (apache2) VPN (openVPN) and an ftpd

At the time this was more for a bit of fun and a project than anything of any real use; however a few weeks after I got it, I got the chance to move abroad for 6months minimum, maybe longer if i like it

fast forward and I agree to go to Gibraltar (right at the bottom of Spain) - so i thought perfect, I'll use my openVPN whilst there and use my apache server to host files id like to be able to download form place to place and to be able to mess about with coding etc (php and stuff) (vpn was mainly so my IP would show as a UK IP allowing me to still use on demand services such as 4od and bbc iplayer) which geoblock based on ip address

anyway, it's all working..kind of I haven't got internet at the flat im at yet so I've been going to mcdonalds..buying some garbage and hooking my laptop up to their wifi..connected to my VPN and it all worked fin (albeit slowly!) showed me as coming from the UK as intended

however the apache web server isnt working ..or rather it isn't reachable on the external IP

the pi has an ip of 192.168.0.9 , apache on port 80/sshd on 22 VPN on 1194 and I've forwarded ALL of these ports from the router to the pi , and the VPN can be accessed remotely as can SSHD, but I can only connect to apache using 192.168.0.9 and not [http://frogs.zapto.org](http://frogs.zapto.org) (the dynamic dns hostname linked to my ip)

Really not sure what's causing it, if you try ssh to frogs.zapto.org you'll get a response and the same with VPN but try connecting to the web server..and nothing
I logged into the router once connected to the VPN and all the ports are still showing as being forwarded from the router -> pi so i cant see why the httpd cant be accessed remotely and everything else can!!
any ideas/suggestions would be greatly appreciated!!

No firewall rules present, only ones to forward VPN traffic, 

thanks

---

