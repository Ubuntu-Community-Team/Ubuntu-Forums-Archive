---
title: "Static IP address"
date: 2007-06-08
forum: Absolute Beginner Talk
---

### Post by pardesi on 2007-06-08
how to set an static IP address i have a DHCP now

---

### Post by brim4brim on 2007-06-08
We don't your network setup.  Please post details of what model of router or other you are using and what Wireless card is in your computer if you know.

---

### Post by Seisen on 2007-06-08
Go to System>Administration>Network. Then click on your connection and properties. After that click the block next to configuration and select static ip. There you will need to enter you static ip address, subnet and gateway address. after doing that click okay. If you have router you will have to configure it to allow static ip addresses. If you have just a cable modem with a Dynamic Ip address then you can't use a static ip.

---

### Post by HereInOz on 2007-06-08
You may also need to go to the DNS tab in Network and enter the DNS addresses which will be given to you by your ISP.  If you don't do this, you may find that you have internet connectivity, but you just can't access any web sites.  You need the DNS addresses to resolve domain names into IP addresses, otherwise the domain names are meaningless.

---

### Post by pardesi on 2007-06-08
i use a cable modem but how do i know whether it's dynamic or static:(

---

### Post by dptxp on 2007-06-08
Many ISPs do not give static IP address. 
They thus use less no. of IP address than their subscribers.

---

### Post by djgrandmarquis on 2007-06-08
> **pardesi said:**
> how do i know whether it's dynamic or static

Static IP's are generally for business-class connections and they are significantly more expensive than dynamic IP service. If you didn't pay for a static IP, then your connection is most likely dynamic.

---

### Post by pardesi on 2007-06-08
i think i have a dynamic adress and i am not able to view pages though the computer writes  i am connected

---

### Post by fastpakr on 2007-06-08
What's the output of the ifconfig command for you?

---

### Post by pardesi on 2007-06-08
here's the link that contains the output in .odt format
[http://ubuntuforums.org/attachment.php?attachmentid=34657&d=1181248407](http://ubuntuforums.org/attachment.php?attachmentid=34657&d=1181248407)

---

### Post by hyper_ch on 2007-06-08
well, your cable provider should have given details on your access... whether you have to set some settings on the cable modem... what you have to do to get online... if you have static/dynamic ip....

---

### Post by pardesi on 2007-06-08
well everything was ok till 2 days back  i was acessing the net properly but now it shows i am connected but the FF won't open any page and i would be sitting there like a dumb....

---

### Post by hyper_ch on 2007-06-08
hmmm, are you sure your internet connection (cable modem --> outside world) is working? It may not be a problem between your ocmputer and the cable modem...

Normally if everything is ok you should have a steady green light with "ready" labelled.... or something similar... you may want to check that....

---

### Post by pardesi on 2007-06-08
yes that' ok that's why i am able to acess the net via XP

---

### Post by hyper_ch on 2007-06-08
ups... I didn't read that...

Once you are in xp open a command shell:

Start --> Run --> cmd --> [enter]

and then type:

```

ipconfig /all

```

or

```

ipconfig -all

```
(not sure anymore which one of those works...

Post the output here...

Then also in ubuntu open a terminal and do the:

```

ifconfig

```

and if you have wireless do also:

```

iwconfig

```

---

### Post by pardesi on 2007-06-08
ifconfig output  gave [http://ubuntuforums.org/attachment.php?attachmentid=34657&d=1181248407](http://ubuntuforums.org/attachment.php?attachmentid=34657&d=1181248407)
```
Microsoft Windows XP [Version 5.1.2600]
(C) Copyright 1985-2001 Microsoft Corp.

C:\Documents and Settings\Vasudevan>ipconfig/all

Windows IP Configuration

        Host Name . . . . . . . . . . . . : vasudevan-b6067
        Primary Dns Suffix  . . . . . . . :
        Node Type . . . . . . . . . . . . : Unknown
        IP Routing Enabled. . . . . . . . : No
        WINS Proxy Enabled. . . . . . . . : No

Ethernet adapter Local Area Connection:

        Connection-specific DNS Suffix  . :
        Description . . . . . . . . . . . : Realtek RTL8139 Family PCI Fast Ethe
rnet NIC
        Physical Address. . . . . . . . . : 00-19-21-54-C6-18
        Dhcp Enabled. . . . . . . . . . . : Yes
        Autoconfiguration Enabled . . . . : Yes
        IP Address. . . . . . . . . . . . :***.***.***.**
        Subnet Mask . . . . . . . . . . . : **.**.***
        Default Gateway . . . . . . . . . :***.***.***
        DHCP Server . . . . . . . . . . . :****.***
        DNS Servers . . . . . . . . . . . : ***.***
                                            ***.***.**
                                          *.***.**
        Lease Obtained. . . . . . . . . . : Friday, June 08, 2007 11:12:48 PM
        Lease Expires . . . . . . . . . . : Saturday, June 09, 2007 2:12:48 AM

C:\Documents and Settings\Vasudevan>
```

---

### Post by hyper_ch on 2007-06-08
well, windows is using DHCP.... 

so set in Ubuntu also the network settings to DHCP....

you shouldn't be required to change anything...

---

### Post by pardesi on 2007-06-08
yes i set it in DHCP in the network adminstration...
when i connect to FF no results...

---

### Post by hyper_ch on 2007-06-08
well, does an error message appear or do you just don't get any results?

If no error message is appearing, then you may want to turn IPv6 off

---

### Post by pardesi on 2007-06-08
no no kind of error message appears and how to turn IPv6 off.

---

### Post by pardesi on 2007-06-08
thanks it's finally connected .....this message is from fiesty not XP:p

---

### Post by hyper_ch on 2007-06-08
Was it due to IPv6?

---

### Post by khardbored on 2007-06-08
How DO you disable ipv6?

---

### Post by hyper_ch on 2007-06-08
by searching this forum ;)

---

### Post by nickpaton on 2007-06-08
Or trying [this]("http://ubuntuforums.org/showthread.php?t=87798") link!

---

### Post by pardesi on 2007-06-08
yes it was due to !Pv6 and yes i got that from the link above the post .
just edit the bad_lst in /etc/modprobe.d by writing 
```
alias net-pf-10 off
```
and rebooting :p

---

