---
title: "Edgy-Eft internet connection issue"
date: 2006-12-21
forum: Absolute Beginner Talk
---

### Post by Paul_world10 on 2006-12-21
Hello there,    I have installed a copy of Edgy-Eft 6.10 on my pc.   I have come across a minor issue with my modem to internet conection. I am using a PCI  U.S. Robotics 5610B 56K modem,  It works great on Dapper Drake 6.06 LTS.   Now my issue with Edgy-Eft is that the modem  IS   recognized  in the  System-Administration-Networking as   /dev/modem now when I try to do my  Sudo pppconfig  and run modem on /dev/ttS4 save that input and run PON   'no response from modem'. Now my Plog looks like this 

root@paul-desktop:~# pon
/usr/sbin/pppd: In file /etc/ppp/peers/provider: unrecognized option '/dev/ttyS4'


root@paul-desktop:~# plog
Dec 22 02:45:27 paul-desktop pppd[10156]: In file /etc/ppp/peers/ppp0: unrecognized option '/dev/modem'
Dec 22 02:45:27 paul-desktop pppd[10167]: In file /etc/ppp/peers/ppp0: unrecognized option '/dev/modem'
Dec 22 02:45:31 paul-desktop pppd[10171]: In file /etc/ppp/peers/provider: unrecognized option '/dev/ttyS4'


under networking the modem shows up as /dev/modem  so I believe it is working under /dev/ttyS4 in my pppconfig


I am new to Ubuntu and I would appreciate your help . Thank you

---

