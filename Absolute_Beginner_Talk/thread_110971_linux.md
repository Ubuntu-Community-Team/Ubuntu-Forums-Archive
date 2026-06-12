---
title: "linux"
date: 2006-01-01
forum: Absolute Beginner Talk
---

### Post by richard willacy on 2006-01-01
has anybody know where on bt broadband i can get some help in installing this linksys modem/router, i 
have done what everybody says but all i get is this dialout thing which takes me to the gate way and i have done all this right, and all the lights are lite up on modem/router, now if i can go out to gateway then i must be doing somthing right, but it still does not let me out using bt broadband, i have been doing this sudo thing 
but that only tells me my ip address and mask numbers,is it possable to get this thing working with just linux and not windows, how to configer this modem/router for linux, hope biscbrit has had a good holiday over here in rainy uk,

---

### Post by Jimmey on 2006-01-01
I've a wireless Linksys router/wireless card, and all I needed to do to get them working in Ubuntu was to go to
System > Administration > Networking.
I clicked on the "Wireless Connection", and clicked "Properties".
Then, I clicked "Enable this connection".
Then, to finish the job, just complete the next few sections (IP assignment etc. ). 
Or, it's possible to finish it by typing 
```
sudo ifup ra0
```
In the terminal, assuming that your network device is ra0.

---

### Post by richard willacy on 2006-01-01
thanks jimmey for the thread and somthing happend but i still have trouble getting out, i went into terminal client but get abit lost in what i have to put into the fields, some i know but there is two i dont know like
domain>client host server, what do i do about  this, i have bt broadband

in terminal it says etho

---

### Post by Jimmey on 2006-01-01
Ah - In that case, in Network Settings, click on the "Ethernet connection", and enable that. Then, in the terminal type

```
sudo ifup eth0
```

Hope it works.

---

### Post by richard willacy on 2006-01-01
in terminal no it did not work, but the erthnet thing did work and is very active, i have enabled this device >configerations set to dhcp is this ok or not,
and i still cant get going

---

### Post by richard willacy on 2006-01-01
sombodys just told me to ping somthing but how do i do this ping thing:confused:

---

### Post by Jimmey on 2006-01-01
DHCP is probably right then - That just means that the router assigns the IP address, not you.

If the device is active, then maybe you just need to make sure it's the default - Under 'Network Settings', change the 'Default gateway device' to 'eth0'.

And just incase - When you type eht0 in the terminal, that's a zero, not an 'o'.

Edit -

To ping, type in the terminal 'ping', followed by the address of the computer you want to ping. This address could be your router, which is usually 192.168.1.1, in which case you'd type

```
ping 192.168.1.1
```
or
```
ping localost
```

Or, you could ping google. It's what I do.

```
ping google.com
```

---

### Post by richard willacy on 2006-01-01
typed this sudo ping 192.168.1.1 and all these numbers came up, well at least it works but nothing els worked, and when i typed this sudo 192.168.1.1 this 64bytes came up

---

### Post by richard willacy on 2006-01-01
been thinking of this voyager 105 adsl modem usb, that i have got, if im using erthnet i dont realy need 
this voyager do i, so will this erthnet work if i get this btbroadband stuff of my pc,because every time i go
out this bt phone thing keeps poping up, what do you think

---

### Post by Jimmey on 2006-01-01
Not to say that you don't, but I didn't need any software on Ubuntu to get my Linksys working. It doesn't really matter what ISP you have, what matters is the hardware.

I checked ping myself, and like you said, a whole bunch of number came up.  I knew what it was doing - It just wasn't very helpful.

So, you still can't connect to the internet? 

If it's wireless, type in the terminal 
```
 iwconfig 
```
and post the results.
If not, type 
```
ifconfig
```
and post the results.

There's probably a simple enough solution to this problem, that we're missing.

---

### Post by richard willacy on 2006-01-01
ok jimmey this is what i get.

iwconfig io no wirerless>etho no wireless>sito no wireless
ifconfig and this lot came up 

etho linkcap erthnet >internet address>192.168.1.64
bcast >192.168.1.255
mask>255.255.255.0

lo or io
internet address> 127.0.0.1
mask> 255.0.0.0. hope you make sence of this :confused:

---

### Post by Jimmey on 2006-01-01
Yeah - It says that the eth0 interface has a network address - I can't see why you can't get the internet :S

Make sure that in the 'Network Settings' that eth0 is the default gateway device, and that it's enabled, AND activated.

Is there any special kind of message that happens when you try to run an internet application, like firefox?

---

### Post by richard willacy on 2006-01-01
i will have another look adn thanks jimmey

---

### Post by Jimmey on 2006-01-01
It's no problem - I want 5 cups :P

I'm beginning to run out of ideas - Hope it works!

---

### Post by richard willacy on 2006-01-01
default gate way device is wtho,
when you go into the gereral in network setting,there is this name called host name and 
in the fiels is this name ubuntubreezy and there is this other name and its called domain and there is sod all 
in this,

when you go into host theres this brown bar thing, and there is 8 diverent rows of diverent numbers
and theres this number 86.129.38.161.me to going for pint of beer

---

### Post by Jimmey on 2006-01-01
Yeah, it's the same for me too, and I am posting using the internet. I REALLY can't see what's wrong - Sorry :(

---

### Post by richard willacy on 2006-01-01
got it working jimmey and there is these 3 tv screens but the only trouble is that im out onto the web but i cant seem to get anything but this white screen. which says somthing about not being able to dial out or somthing,butit works on windows but have not tried it on linux, i know it works because you can see the thing working at the right side of the computer screen and there this thing called settings with diverent stuff in,which one do i select from the list

---

