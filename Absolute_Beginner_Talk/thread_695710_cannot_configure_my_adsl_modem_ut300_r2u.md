---
title: "cannot configure my adsl modem ut300 r2u"
date: 2008-02-13
forum: Absolute Beginner Talk
---

### Post by coolnik6 on 2008-02-13
plzz help me
im using Ubuntu 6.10 along with windows xp
my isp is working fine on xp with ut 300 r2u modem

but in ubuntu
when i try this coomand
sudo pppoeconf
it says find 1 ehtrnet device eth0
then it times out n say cant find the access concentrator

i have set my ip address to -192.168.1.4
subnet mask- 255.255.255.0
default gateway 192.168.1.1

i even try to get to the admin page of my router
by typying this line in firefox
[http://192.168.1.1](http://192.168.1.1)
but it says page cannot be diplayed
but when i ping my IP address
ir gives me replies
pllz help me
my lan card is of 10mbps
its family fast ethernet
driver version - 5.398.613.2003
one more thing which i noticed
is even when i remove my lan cable from port it still says i found ether net devices n all that stuff n the end result is same
so the result is same wheather i plug the cale or not
soo where is the problem?????

---

### Post by max renn on 2008-02-13
I found this for you:

[http://ubuntuforums.org/showthread.php?t=159039](http://ubuntuforums.org/showthread.php?t=159039)

[http://broadbandforum.in/bsnl-dataone-broadband/8334-need-help-port-forwarding-via-netgear-wireless-rtr-ut-300r2u/](http://broadbandforum.in/bsnl-dataone-broadband/8334-need-help-port-forwarding-via-netgear-wireless-rtr-ut-300r2u/)

I find stuff in ubuntuforums using Google that I cannot find using the forums search.  Weird.

I don't know the router you have, but you should verify all of the settings in router from windows and compare to linux.  Also can try DHCP from router in linux and verify the ips then.  Respond if you need more :)

---

