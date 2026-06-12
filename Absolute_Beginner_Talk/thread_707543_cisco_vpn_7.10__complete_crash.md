---
title: "cisco vpn 7.10  complete crash"
date: 2008-02-25
forum: Absolute Beginner Talk
---

### Post by parmdeep on 2008-02-25
hello guys i have a serious problem, everytime i use cisco vpn client my system crashes, i can not move the mouse, i can not do anything except hard reboot. it doesnt crash if it the tunnel is idle, but will crash as soon as traffic hits it. 

i am using roamnet to connect to my uni's wireless, the way i installed it;

i downloaded the tar, unziped it, installed it via ./vpn_install
once it was installed i imported a cert, root.pcf via  cisco_cert_mgr -R -op import
after this i imported roamnet.pcf to the profiles folder
then i run the connection using /etc/init.d/vpnclient_init start
vpnclient connect roamnet,

after this it asks for my username and password, it does connect i do see the correct information, but as soon as i try to use the connection i get a crash, this is a serious problem the onli reason i brought this laptop was for uni work and the thought of going back to windows because of such a small problem makes me cry inside. i really hope there is a fix for this, i have read a few tutorials and not one mentions using 2 .pcf files. can vpnc be configured like this? is there a fix for cisco client? (is it this problem onli on 7.10 is hardy alpha better, beg to think any other distro? i really do enjoy using ubuntu and just as i seem to be getting my hands around this beast we call ubuntu it throws me  off the saddle :(

---

### Post by parmdeep on 2008-02-26
humpty bumpty

---

### Post by cyburdine on 2008-03-31
I too have noticed this problem.  I am running 7.10 on a dell d630 everything works great, however when I connect with the VPN client via wireless the machine completely halts within 2-5 minutes.  The interesting thing to note is that this does not happen when I plugin with a network cable.  

My guess is that this is a conflict with the wireless network driver and the vpn client.  I am curious to know if anyone has tried an older version of the cisco client.

---

