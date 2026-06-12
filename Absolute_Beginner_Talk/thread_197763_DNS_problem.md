---
title: "DNS problem"
date: 2006-06-16
forum: Absolute Beginner Talk
---

### Post by MaximB on 2006-06-16
I've finally installed ubuntu 6.06
and it's great !!! a bit slow but great !!!
I have a connection problem
I've managed to connect BUT it disconnected after 10 min.
I've found the source of this problem and it was the DNS number
I've fixed it and it worked
BUT after 10 min the number changed to the default and I got no connection
I've removed the default number and typed my number and it worked
I think that ubuntu reconized my router as dns for some resion
how can I make my dns number as default so it won't change after 10 min ?

---

### Post by simone.brunozzi on 2006-06-16
Hello!

If you are able to, edit the file /etc/resolv.conf like this:

nameserver 111.111.111.111


you can use gedit.

cheers,

---

### Post by MaximB on 2006-06-16
but my dns server is diffrent and it is already listed there...
but for some resion after 10 min it changes the namber automaticly and disconnects.
by the way - is there a way to always see if i'm connected - like a micro comp in the bottem of the screen - like in windows ?

---

### Post by MaximB on 2006-06-16
sorry but I need help

---

### Post by simone.brunozzi on 2006-06-16
Are you sure that it depends on Ubuntu?

Maybe the problem is your router... are you able to safely navigate under windows on the same PC?

---

### Post by MaximB on 2006-06-16
in winxp I can connect to any site.
I need to make ubuntu NOT to change my dns server address
it changes it after 10 min to 10.0.0.138 for some resion
and I can't connect
after I change the dns address manually it connects but after 10 min it changes the dns again

---

### Post by MaximB on 2006-06-16
I still need help

---

### Post by simone.brunozzi on 2006-06-16
maxddark,
we're not here to FORCELY help you.

It is completely UNuseful to write "I still need help"... if nobody answered you, maybe you need to give more details...
Personally, I don't know what to suggest you.

You can try the IRC channels, maybe you'll find very competent people able to help you.

Cheers,

---

### Post by brentoboy on 2006-06-16
turn off dhcp (the autodetection ip feature)

chances are your dns settings are being reset by whatever pc assigned you an ip address.

use ifconfig from the command line to find out what your current ip is, and what your subnet mask is, and your default gateway.

then use the network setup area, and set those explicitly instead of setting them via dhcp.

once you stop using dhcp you wont have the dns resetting itself all the time. that's what ended up working for me

---

### Post by MaximB on 2006-06-17
I think that ubuntu thinks that my computer is a dhcp...
brentoboy - were is the network setup area ? is it in system-administrator-networking or network tools ?
and what is an explicitly ???

thanx ahead.

---

### Post by brentoboy on 2006-06-17
in a terminal window
run:
ifconfig

write down your ip, subnet, and gateway as assigned by the server

then from the menu bar
system >> Administration >> networking

select ethernet conection (or whatever it is that you are using)
click the properties button

set your ip, subnet, and gateway

click ok on th interface properties screen

then, when it closes, goto the dns settings on the network settings screen.

add the correct dns settings.
delete the ugly ones.

then, click ok on the network settings screen.

problem solved (or, at least, if you are having the problem I think you are, it will be solved)

good luck

---

### Post by MaximB on 2006-06-17
do you mean that I have to put a static ip address ?

---

### Post by brentoboy on 2006-06-17
that is exactly what I am saying.

you should put in the one that you were assigned, becuase at least it is functional on your network.

do you get an ip from a home router? or from your isp?

if it is your isp, then dont change it.
if it is your routher, then you wont end up conflicting with anything else.

when your computer requests a dynamic ip address from whatever pc it gets one from, it also gets the dns settings updated.  if you dont want to get the dns updated, you will have to stop getting an ip address from it.

---

### Post by MaximB on 2006-06-18
I'm getting my adress from my ISP.
how can I make the dns number I typed NOT to change every 10 min ?
I always getting the dns number 10.0.0.138 after the update.

---

### Post by gm__ on 2006-06-18
You have to call your ISP and ask them what dns to use.
They will tell you the ips of their DNS server.
That's what i did too.

---

### Post by MaximB on 2006-06-18
I did it
they gave me the number
I add the dns number they gave me
and the internet connection worked
but after 10 min the dns number I've typed changed.
so to be abale to connect I have to change my dns number manually every 10 min.

---

### Post by Soarer on 2006-06-18
You're still running DHCP. The IP address is given out by your router, probably an Alcatel SpeedTouch which uses 10.0.0.138, and has a Time to Live (TTL) of 600 seconds or 10 minutes. After this time it refreshes and gives you a new IP address (may actually be the same one) and updates the DNS information, overwriting the old stuff. You have not set a static IP yet, as suggested previously.

It actually SHOULD work anyway, as the router will act as a relay for DNS. What happens is the PC forwards DNS requests to the router, which it thinks is a DNS server. The router then forwards that request to your ISP's name servers. This means the ISP can change them if it needs to & you don't need to know. This is how mine is setup.

Something in the router is misconfigured, as it is not forwarding DNS requests properly. So you should set the static IP as requested. Rebooting your router MIGHT solve it, but might also cause it to stop working altogether. You can check your router's config by using your browser & typing [http://10.0.0.138](http://10.0.0.138) in the address line. Manuals for all SpeedTouches are available on line, I believe.

---

### Post by zefram on 2006-06-18
you can use the command : sudo chattr +i /etc/resolv.conf    to make the file read-only (even to the system)  ( -i to unlock).

---

### Post by MaximB on 2006-06-18
[QUOTE=zefram]you can use the command : sudo chattr +i /etc/resolv.conf    to make the file read-only (even to the system)  ( -i to unlock).[/QUOTE]

many many many thanks .... I think that you might saved my day...
I'll just have to wait and see
=D>

---

