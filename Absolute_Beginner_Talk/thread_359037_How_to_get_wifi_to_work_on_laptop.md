---
title: "How to get wifi to work on laptop"
date: 2007-02-11
forum: Absolute Beginner Talk
---

### Post by Onecat on 2007-02-11
I got ubuntu to boot from HD but I can't get my wifi set up. I am on a toshiba satellite laptop. Any suggestions? Thanks.

---

### Post by jolger on 2007-02-11
okay i had the same problem on my laptop, heres what i did:

assuming that your wireless card is eth1 else its probably eth0.
commands:
> 
in the top panel on the right hand there is the "network manager" i suppose,
go there and select your wifi card, next write the details of the network you want to connect to E.G. network name, network key.

#next i started a console
  ifconfig
#look for your IP and so on, if it isnt there try:
  sudo ifdown eth1
  sudo ifup eth1

#now you should be ready to go
#next thing i did (to see most web pages)
  sudo gedit /etc/modprobe.d/aliases
#find the line where it says:
  alias net-pf-10 ipv6
#replace it with
  alias net-pf-10 off
#save and exit
#restart computer


this is basically what i did to make it work. hope this helps...

/Jolger

---

