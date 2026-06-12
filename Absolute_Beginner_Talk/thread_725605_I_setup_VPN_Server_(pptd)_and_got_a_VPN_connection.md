---
title: "I setup VPN Server (pptd) and got a VPN connection -- now ...."
date: 2008-03-15
forum: Absolute Beginner Talk
---

### Post by cwmoser on 2008-03-15
I setup VPN Server (pptd) on my home Ubuntu PC workstation and I was able to established a VPN connection.

I VPN'ed remotely using an XP client and was able to mount a drive on on my Ubuntu PC. .. i.e.
   net use J: \\192.168.1.77\public

It was kinda cool being able to access files this way.

But, I was not able from the remote location to ping any PC on my home network except for the Ubuntu PC.  I could ping 192.168.1.77, the Ubuntu PC, but no other device.

I guess I need some clarification on how to use VPN.  If I had a Windows XP Pro PC on my home network, should I have been able to remote desktop to it like you can when you VPN into a network running Server 2003?  Is there further configurations I need to make to pptpd?

Carl

---

### Post by gordintoronto on 2008-03-16
VPN provides access to your server via a long wire instead of a short one.  By itself, it doesn't include remote desktop.

All the best,
Gord

P.S. If you're the Carl Moser who wrote an assembler for the PET about 400 years ago, THANKS!

---

### Post by cwmoser on 2008-03-17
Once the VPN is established, I can ping the Server -- but no other device.
I can run TightVNC to 192.168.1.xx and get on the desktop of the Server.
Still TightVNC is slow and I like NXServer much better as it is much faster.

Is there a way to establish a VPN so that all the devices on the remote network are accessible?


Carl

---

### Post by farahbod on 2008-03-24
Carl I think you have to make further configurations on ubuntu box to go out of the box.

If you can do anything with ubuntu box but cant see other machines on the LAN then ubuntu box must act as a router in order to deliver your packets from the PPP connection to other boxes on wired network!

Execute the following command while you logged in the ubuntu from the Xp and let us know the result:

sudo route

---

### Post by daflame on 2008-03-25
Just use hamachi instead.  You can have near local access with a different IP address for each machine and it works on linux and windows.  It is also MUCH MORE SECURE.  It uses openssl tunneling technology with public/private keys.

---

### Post by cwmoser on 2008-03-27
I ran the route command and got this:

   IP                    GATEWAY         GenMask             
192.168.0.0             *              255.255.255.0           eth0
192.168.0.50           *              255.255.255.255       ppp0
default               192.168.0.1   0.0.0.0                       eth0


The Ubuntu PPTP server is 192.168.0.202 and the dynamic IP assigned to me when I VPN'ed in is .50.

I can ping 192.168.0.202 and .50.  I cannot ping other devices such as my Windows XP PC (192.168.0.215) or my router (192.168.0.1)

Any help is appreciated.

Thanks

Carl

---

### Post by cwmoser on 2008-03-27
The reason why I need a solution is so that once I setup the VPN connection, I would like to remote desktop to one of a number of PC's.  With the current configuration, I can only remote into the Ubuntu PC running the PPTP server.

Carl

---

### Post by cwmoser on 2008-03-27
Another thing I thought of is that I have my router set to Port Forward port 1723 to my Ubuntu computer (192.168.0.202) -- where the PPTP server software runs on.

Would that have something to do with it?

Carl

---

### Post by farahbod on 2008-03-28
1. You have a private lan in your home.
Consider we have 192.168.0.0/24 network for that.
Host      |    IP
-----------------------------
Router     |  192.168.0.1
Ubuntu |  192.168.0.202
XP1             |  192.168.0.215
XP2             |  192.168.0.216

in the pptpd configuration, you should have proxyarp enabled. Place this in /etc/pptpd.conf or /etc/ppp/options.pptpd:

```
proxyarp
```

Also localip and remoteip tags must look like this:
```

localip 192.168.0.202
remoteip 192.168.0.11-100
```

which means when you connect through the vpn, your computer will be assigned an IP address between 192.168.0.11 and 192.168.0.100.

Now restart the pptpd server. Connect to ubuntu and ping 192.168.0.215.
Considering it replys from ubuntu server itself, you should now be able to ping it from your vpn client too.

2. If you can connect to the ubuntu vpn server, there is no need for any change on the router!

---

### Post by cwmoser on 2008-03-28
I inserted proxyarp in /etc/pptpd.conf  and  in  /etc/ppp/pptp.options

I also have:

localip 192.168.0.202
remoteip 192.168.0.50-51


Then I restarted pptpd via /etc/init.d/pptpd

Still, when I VPN in, I can only ping and connect to the 192.168.0.202 PC.  The other PC's on my network are not accessible via the VPN.

Any insight is appreciated.

Carl

---

### Post by farahbod on 2008-03-28
Did you enable packet forwarding on the ubuntu machine?
run this:
```
echo 1 > /proc/sys/net/ipv4/ip_forward
```

run this on ubuntu server just for testing purpose:

```
iptables -F
```

run this from client:

```
tracert 192.168.0.215
```

---

### Post by BDNiner on 2008-03-28
So you want to VPN to your ubuntu machine and have it act as a hardware VPN. You would have to add a second network card to the computer and then connect a switch to that port and all the other computers will then connect to this switch. you would also have to setup DHCP on the ubuntu box so it hands out the IPs to the other computers.

I feel there are some problems with your setup. Once you connect to the VPN, you should be able to VNC to your ubuntu box and then be able to access the other computers. That is if you can access them while actually sitting infront of the computer. The VPN connection terminates at your ubuntu box therefore you can't see anything beyond that on your network. I only know a little about this since i have a hardware VPN to connect to work from home, so it handles all of this for me. Also you need to look up routing since your other computers will try to connect the your remote machine (the one you are VPNing from) through the internet instead on back through the VPN (which would make it slow) since they don't know that the VPN exists since it terminates at your ubuntu box. 

some clever routing should help you. good luck.

---

### Post by farahbod on 2008-03-28
> **BDNiner said:**
> So you want to VPN to your ubuntu machine and have it act as a hardware VPN. You would have to add a second network card to the computer and then connect a switch to that port and all the other computers will then connect to this switch. you would also have to setup DHCP on the ubuntu box so it hands out the IPs to the other computers.

I feel there are some problems with your setup. Once you connect to the VPN, you should be able to VNC to your ubuntu box and then be able to access the other computers. That is if you can access them while actually sitting infront of the computer. The VPN connection terminates at your ubuntu box therefore you can't see anything beyond that on your network. I only know a little about this since i have a hardware VPN to connect to work from home, so it handles all of this for me. Also you need to look up routing since your other computers will try to connect the your remote machine (the one you are VPNing from) through the internet instead on back through the VPN (which would make it slow) since they don't know that the VPN exists since it terminates at your ubuntu box. 

some clever routing should help you. good luck.

He runs other machines virtually on the ubuntu server, and i think he does not want to use a hardware vpn.
Even if he eventually decides to buy a hardware vpn, still we can work on this! ;-)

---

### Post by Dabbill on 2008-03-28
To do what your wanting to do with your computer you would need a hardware VPN device, or a router that has VPN abilities. Software VPN will not work as far as i know. My buddy and i have a VPN setup. We use the linksys open source routers. We installed linux firmware on them with VPN support to get our VPN to work. Now we have 2 networks across down that act as 1 Local area network. Its a little slow accessing the computers at his house due to the bandwitch limits of our comcast cable connections, but works wonderfully.

---

### Post by cwmoser on 2008-03-28
Now its working.  I think when farahbod suggested this that got it working:

Did you enable packet forwarding on the ubuntu machine?
run this:

Code:
echo 1 > /proc/sys/net/ipv4/ip_forward


Now, I can ping all my computers via the VPN.  How about a DNS?  Instead of:

ping 192.168.0.215

can I:

ping XPLab1

Thanks for the all this help.

Carl

---

### Post by BDNiner on 2008-03-28
glad to see you got it working. I did not know that the other computers were virtual machines.

---

### Post by farahbod on 2008-03-28
:)
This means that you did not enable packet forwarding!
To enable this forever(after any restart) open /etc/sysctl.conf and uncomment this line:
```
#net.ipv4.conf.default.forwarding=1
```
save & exit.

You can install BIND or use another method! BIND installatoin is much more better, however BIND can not resolve netbios names. I think Samba is able to act as WINS server.
Also if you always connect from one PC you can locally define name/ip address pairs.

On windows XP goto Start\Run and copy/paste this command:
```
notepad %systemroot%\system32\drivers\etc\hosts
```
add this line at the end of the file:
```
192.168.0.215 XPLab1
```
Save & exit.

You're welcome!

---

### Post by ryazkhan on 2008-03-28
I have slightly different problem. I loose internet after connecting to vpn at ubuntu box. Any idea how you will fix that, because sound like you are not having this pro and your vpn is working fine.
Any help would be appreciated 
Thanks in advance

---

### Post by farahbod on 2008-03-29
ryazkhan, do you use xp vpn client?
Windows xp vpn client will change default routes through the tunnel.
Try to set proper routes manually.

---

