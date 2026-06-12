---
title: "Getting Ubuntu Online"
date: 2007-10-06
forum: Absolute Beginner Talk
---

### Post by oscarthefish on 2007-10-06
I have just successfully installed 'Ubuntu 7.04' on my spare computer. I would like to get online but i haven't a clue and was hoping for some help. 

I already have a computer online using a Netgear 'DG834G'  modem router and running Widows Vista. But how can i get my spare computer online that is running (Ubuntu) as well sharing if possible the same internet connection.

Or failing that could i just remove the Ethernet cable from the computer running Windows Vista and connect it to my spare computer running Ubuntu and get online?

Thanks in advance for any and all help

---

### Post by hey_mrs_tee on 2007-10-06
hi there,

i've just recrently installed Ubuntu 7.04 feisty Fawn, and encountered the same problem as yours. 

Try clicking your network connections tab on the top right corner of your monitor screen ie, static config tab and see whether your connection is set to Automatic in properties.

or try 

```
Sudo ethtool eth0
```

and post output here ;) cheers

---

### Post by candtalan on 2007-10-06
> **oscarthefish said:**
> I have just successfully installed 'Ubuntu 7.04' on my spare computer. I would like to get online but i haven't a clue and was hoping for some help. 
I already have a computer online using a Netgear 'DG834G'  modem router and running Widows Vista. But how can i get my spare computer online that is running (Ubuntu) as well sharing if possible the same internet connection.
Or failing that could i just remove the Ethernet cable from the computer running Windows Vista and connect it to my spare computer running Ubuntu and get online?
Thanks in advance for any and all help

The Netgear 'DG834G' seems to be both wireless and wired, with four sockets (ports) for the wired connections. I guess one is already used to take ethernet from the router to your vista PC at present? 

For a wired connection all you need to do is take another cable from a port on the router to the network port socket on the spare PC. You could use the cable from the vista pc temporarily, no problem, the router will not care.

With a wired connection you should find that the network card in the spare PC is recognised automatically and will probably pick up an IP address from the router at boot up, automatically, and you will be on the internet no problem.

Wired connections are easy :-) I prefer them. You can hang a lot more PCs onto your router just by taking one cable to a 'Switch' and that gives you a bunch more ports for more PCs - or more switches! My house is full of them. :-)
'switch' example:
Edimax 8 Port 10/100Mbps Switch
[http://www.dabs.com/ProductView.aspx?Quicklinx=4MX1&CategorySelectedId=11176&PageMode=1&NavigationKey=11176,4294960498,4294960497,41770000&InMerch=1](http://www.dabs.com/ProductView.aspx?Quicklinx=4MX1&CategorySelectedId=11176&PageMode=1&NavigationKey=11176,4294960498,4294960497,41770000&InMerch=1)

An aside comment: It sounds as if you may not be using wireless just now, it might be a good idea to disable or turn off the wireless function if you are not using it - others in the neighborhood might be tempted to mess with using it.

---

### Post by oscarthefish on 2007-10-06
As i have a spare ethernet cable i can just connect it to the computer and the Netgear "DG834G" modem/router and i will be able to access the internet using both computers? Thanks folks!

---

### Post by Sef on 2007-10-06
> As i have a spare ethernet cable i can just connect it to the computer and the Netgear "DG834G" modem/router and i will be able to access the internet using both computers? 

Yes.  that's what I do.

---

