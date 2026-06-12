---
title: "how to connect to router"
date: 2008-02-22
forum: Absolute Beginner Talk
---

### Post by chaparrazo on 2008-02-22
Hello, 

Just installed an intel nic in my ubuntu 7.10 box (PIII) and tried to connect to my linksys cabled router wrt54g. I guess I have to configure the nic or add a driver? Like a stupid noob trying to cross over from windoze, i guesss i expected it to just work. ;) 

Have been reading posts looking for help but can't seem to find the right answer. 

help, please! 

Thanks

---

### Post by chaparrazo on 2008-02-22
ok, guess i'll try a fresh install. that worked last time nobody answered me too.

---

### Post by Sir_Sid on 2008-02-22
What nic are you using? In most cases Ubuntu should be able to detect it immediately unless its one that is not supported.

---

### Post by chaparrazo on 2008-02-22
Intel 701738-002 with an sl2p4 chip on it. 

Thanks

---

### Post by chaparrazo on 2008-02-22
I'm looking for compatibility lists to check, anyone know where? 

When i did the first install there was no nic in this box. I plugged it in and prayed and guess i'm not righteous. If it's compatible, then it should see it and configure everything without my having to do any config? 

i just bought the card at free geek and assumed it would work. 

thanks for any tips or suggestions . . .

---

### Post by spiderbatdad on 2008-02-22
try running depmod -a in a terminal and then look at sudo lshw -C net

---

### Post by superprash2003 on 2008-02-22
go to system->administration->network tools... if you see eth0 or eth1 etc.. that means your LAN card has been detected.. i think the problem is that your eth0 or eth1 is not set to DHCP.. your router maybe trying to give you an ip but your computer is not accepting.. so go to the eth0 or eth1 properties and select DHCP

---

### Post by chaparrazo on 2008-02-22
tried those commands and is said could not open and listed nothing for the second.

then in system admin net tools, there's nothing about eth. should it be listed there under protocols? there are two in the list: ipv4 and ipv6. after network device it has loopback interface (lo)

what next? 

thanks!

---

### Post by spiderbatdad on 2008-02-22
could you post the results of ```
ifconfig
iwconfig
```

---

### Post by kaginken on 2008-02-22
You may also want to grep your /var/log/dmesg file

cat /var/log/dmesg | grep eth0

or

tail -n 200 /var/log/dmesg | less  
and just scroll thru the last 200 lines of it

That's your hardware log, and it will show any errors that may be occuring.  

Hope that helps!

---

### Post by chaparrazo on 2008-02-22
ok

don't have a way to copy and paste the listings. 

ifconfig shows link encap local loopback
inet addr
inet6 addr
up loopback running
rx packets: all 0
tx packets all 0
0 collisions (obviously) 
rx bytes 0

iwconfig says: 
lo      no wireless extensions
 

the other commands said nothing about eth

thanks!

---

### Post by spiderbatdad on 2008-02-22
would be nice if you could see if your nic is detected. You may have made a mistake the first time you tried this command, so, if you want, try again, exactly like this:```
sudo lshw -C net
```
You are looking for a wireless interface.

---

### Post by superprash2003 on 2008-02-23
since u cannot see any eth0 or eth1.. ubuntu has not recognized your LAN card.. if its an onboard LAN card then u need ot search for drivers.. if its a PCI then first check if its insert properly..!!

---

### Post by chaparrazo on 2008-02-23
tried it again. it lists things on the same line and then they disappear. 

just to be sure, this is not a wireless card i'm trying to install. it's just a plain old nic for a wired connection to my router. 

thanks

---

### Post by chaparrazo on 2008-02-23
superprash, 

it's a card. i opened the box about a half hour ago to check. it's in there good and the connect, 100 and act lights are on. the light on the router is lit too.

---

### Post by kaginken on 2008-02-23
If a reboot doesn't solve the problem ( a cold reboot, power the machine completely off), then I'd try installing that NIC on a different PCI slot if you have another available on your motherboard.  Could be a bad pci slot.  

Alternatively, just try reseating it in the pci slot, press very hard, make sure it's seated in there firmly.

---

### Post by chaparrazo on 2008-02-23
ok, it's in another slot, lights are on on the card, activity light flashing, but no connections. 

other ideas?

---

### Post by kaginken on 2008-02-23
Yea - boot up on your ubuntu live cd, see if THAT sees the NIC.  If so you could always
*gasp* 
reinstall ubuntu  :D

---

### Post by spiderbatdad on 2008-02-23
i believe you need to manually insert the module for the card with ```
modprobe card
``` where card might be e100, for example. What type of nic is this, maybe we can find the appropriate module.

---

### Post by kaginken on 2008-02-23
think the command would be modprobe  :D

---

### Post by spiderbatdad on 2008-02-23
:oops:

---

### Post by chaparrazo on 2008-02-23
ha ha

well, at least we're all having fun . . . 

the card is Intel 701738-002 with an sl2p4 chip on it.

---

### Post by chaparrazo on 2008-02-23
just tried live CD and (drumroll please) . . . 

nope. time for a fresh install? or how do I do the modprobe?

---

### Post by spiderbatdad on 2008-02-23
```
modprobe 701738-002
```

---

### Post by spiderbatdad on 2008-02-23
but if the driver is not existing that wouldn't work. You may need the intel pro/100 driver.[http://www.gtlib.gatech.edu/pub/suse/people/kgw/7.0/e100-v1.3.20/Readme_e100-1.3.20.txt](http://www.gtlib.gatech.edu/pub/suse/people/kgw/7.0/e100-v1.3.20/Readme_e100-1.3.20.txt)
If your re-installing doesn't do the trick.   first try```
modprobe e100
```

---

### Post by kaginken on 2008-02-23
If at first you don't succeed...well, so much for skydiving.

I agree with the above...that nic just ain't supported out of the box sounds like.

You can verify, check the supported drivers list, see if it's listed.  

Sorry I couldn't be any more help.  Best of luck!

---

### Post by chaparrazo on 2008-02-23
well, crapola! did a fresh install and it still doesn't connect or show any evidence of a card. 

i'm going to bed.

---

### Post by chaparrazo on 2008-02-23
where is the supported drivers list? i was looking earlier and couldn't find it. 

thanks

---

### Post by Yoke &amp; Chung on 2008-02-23
If the card is not detected on LiveCD, you really have to search Google whether the card is supported or any work around on Ubuntu/ Linux. 

If it does not have a Linux driver, and you absolutely have to use the card, try ndiswrapper. It is usually used for installing Windows wireless card driver onto Linux but is known to work with some other devices.

Good luck!

---

### Post by superprash2003 on 2008-02-23
if nothing works.. how about another LAN card :D.. dont think it would cost more than 7$

---

### Post by kaginken on 2008-02-23
Yea, might be best to get a new NIC, their real cheap on ebay or tigerdirect, etc.

I can't easily find the supported drivers list either - found a couple different lists, one for wireless nics, one for dell laptops...both in the wiki.  Try searching the wiki for your exact model.

---

