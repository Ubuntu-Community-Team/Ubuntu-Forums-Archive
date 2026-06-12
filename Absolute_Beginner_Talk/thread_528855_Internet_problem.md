---
title: "Internet problem"
date: 2007-08-18
forum: Absolute Beginner Talk
---

### Post by sandeep37 on 2007-08-18
I have IP address and subnet mask and gateway address and i am entering this value and this value are saved there, i also tried DCHP ,but still i am not  able to connect to the internet plz some one help me. I am using 7.04

---

### Post by Warren Watts on 2007-08-18
Can you be more specific?

What sort of connection to you have to the internet?
Cable?
DSL?
Dialup?

---

### Post by pbwalker on 2007-08-18
Sandeep37,

We'll need more information than this...are you behind a DHCP Server (Wi-Fi Router, ISP, etc.)?

When you enter your IP, if you run an ifconfig, do you see it in there?

have you tried running dhclient eth# yet? (the # refers to whatever your network interface is...eth0, eth1, etc.)

---

### Post by sandeep37 on 2007-08-18
i am using cable and i have IP,SUBNET and gateway address

---

### Post by pbwalker on 2007-08-18
So you have a static IP address?

Can you run 'ifconfig' and post it here please? Thanks!

---

### Post by sandeep37 on 2007-08-18
this is the output . Plz help me

---

### Post by pbwalker on 2007-08-18
Ok...that is a NATd IP Address, so I assume you are behind some type of Firewall or Router (be it wireless, etc.)

This is not a direct connection to the internet (cable modem) right?

---

### Post by sandeep37 on 2007-08-18
I dont have any modem with me . I just have a cable( through LAN)

---

### Post by pbwalker on 2007-08-18
Ok...Does that patch cable plug into the wall or a device?

Anyways, remove those static entries you put in and run dhclient eth0 (you'll need root access, so you may have to run 'sudo dhclient eth0')

Post your output here...

---

### Post by sandeep37 on 2007-08-18
i will plug the cable into the LAN port

---

### Post by pbwalker on 2007-08-18
This seems to be getting more confusing than it needs to...

This is at home correct?

What type of connection do you physically plug your computer into?

Who is your ISP?

Are you trying to give the IP that you have on your windows box?

---

### Post by sandeep37 on 2007-08-21
I am using cable internet connection which i will plug into LAN port and i have ID ,SUBNET,gateway address . I gave this address in the networking by selecting static IP . I am able to connect to net through XP.I dont have any modem with me i will just plug the cable in the LAN port . I am using local cable connection . I also tried the following things . Some one plz helps me

---

### Post by ElidS on 2007-08-22
Any suggestions as to how resolve Sandy's issue? 

I have the EXACT same situation.
Cable ISP, no firewall, other PCs with XP connect just fine so it is not a connectivity issue, the Ubuntu pc seems to 'network' when physically connected (the double monitor icon on the top right hand corner appears to have a connection) but I'm unable to access the net. 

On a side note trying to capture a screen shot will not save it directly on to a floppy, and one can not capture the image and paste it onto Gimp to save it with that. This I can figure out later though.

---

