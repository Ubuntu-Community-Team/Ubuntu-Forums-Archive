---
title: "Wine windows rdp client"
date: 2008-04-10
forum: Absolute Beginner Talk
---

### Post by TechDragon on 2008-04-10
I installed wine and downloaded the rdp client from windows but when I try to install it says it is already installed.  I can't find it anywhere though.  

Help please?

---

### Post by DianeHelen on 2008-04-10
Id be most curious to follow your progress with this lil adventure. The RDP client for a windows XP box, is JUST what I am looking for.

What IS WINE?  and with thei rdp client, should you techincally be able to open a remote desktop session from an Ubunto box to an XP one that has Remote Desktop enabled?

I'll be watching thread for answers.

---

### Post by bodhi.zazen on 2008-04-10
You do not need to do any of that, I don't think.

Ubuntu comes with a client already installed.

Applications -> Internet -> Terminal Server Client

[http://mixeduperic.com/index.php?option=com_content&task=view&id=70&Itemid=46](http://mixeduperic.com/index.php?option=com_content&task=view&id=70&Itemid=46)

---

### Post by Rocket2DMn on 2008-04-10
> **bodhi.zazen said:**
> You do not need to do any of that, I don't think.

Ubuntu comes with a client already installed.

Applications -> Internet -> Terminal Server Client

[http://mixeduperic.com/index.php?option=com_content&task=view&id=70&Itemid=46](http://mixeduperic.com/index.php?option=com_content&task=view&id=70&Itemid=46)

+1
You can load rdp files into the Terminal Server Client as well.  I suggest specifying screen resolution on the second tab (Display) to something a little smaller than your full scree resolution so you can move the mouse out of the remote machine window, otherwise it will fill up your whole screen, and I haven't figured out how to get out of that without killing the remote connection.

---

### Post by DianeHelen on 2008-04-10
That seemingly would work over an internal network, but how would you get that to work across the internet. When I travel Im not on my network. Currently I use the remote client to log in via my home IP (and custom port) to get to my windows desktop.

Is there a way I could do taht with the RDP client thru the Terminal SErver?

Id be soooo utterly happy if that was possible!

---

### Post by Rocket2DMn on 2008-04-10
> **DianeHelen said:**
> That seemingly would work over an internal network, but how would you get that to work across the internet. When I travel Im not on my network. Currently I use the remote client to log in via my home IP (and custom port) to get to my windows desktop.

Is there a way I could do taht with the RDP client thru the Terminal SErver?

Id be soooo utterly happy if that was possible!

It works over the internet, you would have to forward the ports through your router to the server computer (I'm don't know off the top of my head which port(s) is/are used).  If you are generating rdp files, you will need to configure them to use public IPs instead of internal LAN IPs.  Otherwise just manually enter the details into Terminal Server Client.  This also requires you to know your home's public IP - see [http://www.whatismyip.com/](http://www.whatismyip.com/)
You may also look into dyndns - [http://www.dyndns.com/](http://www.dyndns.com/) so you can get an easy to remember name rather than a raw IP.  Some routers can auto-updated with dyndns, and there are scripts you can put on computers to auto-update as well.

---

### Post by DianeHelen on 2008-04-10
Hmmm ok maybe getting close here

I have a static(public) IP , I know it, I RDP to that IP and just add a custom port to it, when I log in from my XP laptop

so, HOW and where to I establish this on the Ubunto box?

The XP box is all set thru the router and then thru the standard port for it, that the router reroutes to the custom port

If you would like to be my NEW best friend, PM me, and I will return an AIM or Yahoo messenger S/N and you can walk me thru it, just cuz you are soooo nice, and sooo smart, and Im so needy :)


But if not, any help or direction you can spare, would also be truly appreciated


:)
Diane

---

### Post by Rocket2DMn on 2008-04-10
> **DianeHelen said:**
> Hmmm ok maybe getting close here

I have a static(public) IP , I know it, I RDP to that IP and just add a custom port to it, when I log in from my XP laptop

so, HOW and where to I establish this on the Ubunto box?

The XP box is all set thru the router and then thru the standard port for it, that the router reroutes to the custom port

If you would like to be my NEW best friend, PM me, and I will return an AIM or Yahoo messenger S/N and you can walk me thru it, just cuz you are soooo nice, and sooo smart, and Im so needy :)


But if not, any help or direction you can spare, would also be truly appreciated


:)
Diane

Hehe, well let's just deal with the problem here on the forums.  To connect to your windows box that has the remote desktop connection already setup, you can open Terminal Server Client on your Ubuntu machine from Applications->Internet->Terminal Server Client
Where it says Computer, you should be able to type in your public IP.  Protocol should be RDP.  Then you can type in the username and password.  I'm not sure domain or hostname are required since you are direct connecting to the box.
If you are using something other than the default port, the Computer section may need to look like 
```
ip:port
```
 although I've never tried not using a standard port, most of the time when I use RDP connections I am given an rdp file to use, which has all the information in it.
That should be all you have to do.

---

### Post by bodhi.zazen on 2008-04-10
> **DianeHelen said:**
> Hmmm ok maybe getting close here

I have a static(public) IP , I know it, I RDP to that IP and just add a custom port to it, when I log in from my XP laptop

so, HOW and where to I establish this on the Ubunto box?

The XP box is all set thru the router and then thru the standard port for it, that the router reroutes to the custom port

If you would like to be my NEW best friend, PM me, and I will return an AIM or Yahoo messenger S/N and you can walk me thru it, just cuz you are soooo nice, and sooo smart, and Im so needy :)


But if not, any help or direction you can spare, would also be truly appreciated


:)
Diane

Start terminal server client

Enter the hostname or ipaddress

Leave protocol at "RDP"

click connect

[http://www.watchingthenet.com/how-to-connect-to-a-windows-terminal-server-from-ubuntu.html](http://www.watchingthenet.com/how-to-connect-to-a-windows-terminal-server-from-ubuntu.html)

Enter windows log in name and password.

---

### Post by DianeHelen on 2008-04-10
Well I JUST got back HERE to give the GOOD news, and odly the answer I came up with, is in fact the VERY answer you just posted..

WHAT I was doing wrongly duhhhh , was entiering my computer NAME, and that is why I was saying, it would not work over the internet. When you said earlierm, about the public IP, a light went on in my lil pea brain, and I JUST went back to teh U box, and , well
long story short, I used my public ip  then a colon, then the      port and THAT was the trick!


YAYYYYYYYYYYYYYYYYYYYY

WORKS like a charm, and WAY faster than gotomypc

bit by inch , piece by piece, Im forging the way to leave Windows closed, at least when I travel. 


So THANK you SOOO much for turning the lights on..

---

### Post by bodhi.zazen on 2008-04-10
You can do it by hostname, but you need a public hostname

You can get one at [DynDNS](http://www.dyndns.com/) or similar.

Your hostname (or computer name) == private IP (from your router)

DynDNS name == Public IP , from your IP provider


So to use RDP on your LAN, use your computer name or private IP (192.168.1.x )

To RDP over the internet, use you DynDNS name or public IP

---

