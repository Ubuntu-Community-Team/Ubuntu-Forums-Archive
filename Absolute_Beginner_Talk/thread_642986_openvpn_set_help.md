---
title: "openvpn set help"
date: 2007-12-17
forum: Absolute Beginner Talk
---

### Post by sloop on 2007-12-17
Hi to everybody.I must set open-vpn network on my workplace.My boss wants me to show open-vpn connection between two PC's.They are on the same LAN segment.This is for no practical use, he just want me to do it.On the two PC's running ubuntu.I read common howto for openvpn but still don't figure out everything. Where must I paste keys to the client PC - to some new directory ? In server.conf is determine as open-vpn server 10.8.0.0  Should I change it or it has nothing to do with the LAN segment which is 192.168.0.0?

---

### Post by sloop on 2007-12-18
Pleace, my friends - answer me. It is important to me.

---

### Post by HermanAB on 2007-12-18
Take two PCs and a cross-over cable.  Then Google for a few howtos.

Cheers,

Herman

---

### Post by sloop on 2007-12-19
I did that already but thanks for your answer.

---

### Post by bunnynuts on 2007-12-27
To clarify, you are running 2 machines both with some version of ubuntu and one of them has been set up as the server, and you want to connect the other machine to the machine running as the server through the vpn...and there are no windows machines involved. Is that correct? Also, it appears they are both behind the same router. 

To answer your first question see if this URL is of any help:
[http://www.zeroshell.net/eng/openvpn-client/#OpenVPN-GUI-Linux](http://www.zeroshell.net/eng/openvpn-client/#OpenVPN-GUI-Linux)

As to our second question, you do not need to change the ip that will be used to connect through the vpn to the same one that is assigned by the router. So there is no need to change the 10.8.0.0 ip, however, be sure that the client configuration file and the server configuration file match in regards to this ip. 

Also, I have something of a 'how to' on setting up the server side of the openvpn on the forums somewhere though I did not start the post. I'm not sure it will be of help. 

Finally, I'm not sure how this will work for your setup, but if you were to try to connect to the vpn server from a machine that is not behind the router, you would need to setup port forwarding on the router itself. I'm fairly certain (though not 100% sure) that you will need to do so even when both machines are behind the router.

---

