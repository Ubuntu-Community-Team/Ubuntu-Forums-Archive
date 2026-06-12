---
title: "Getting an NTL ethernet internet connection working?"
date: 2006-09-24
forum: Absolute Beginner Talk
---

### Post by njparton on 2006-09-24
Hi,

I ran Ubuntu initially from the live CD and everything worked fine. I had sound and an internet connection - perfect! I'm running a system using an nforce4 motherboard.

I've now installed Ubuntu properly and I can't seem to get my NTL cable internet working which is strange as under the live CD everything was fine.

The NIC has been detected correctly and set as eth0 and DHCP looks to be setup correctly - what else do I need to look at?

Thanks

---

### Post by nts on 2006-09-24
can you ping from the router?

---

### Post by nts on 2006-09-24
> **nts said:**
> can you ping from the router?

sorry, can you even ping the router...?

---

### Post by njparton on 2006-09-24
I don't use a router just straight ethernet cable to the cable box (which I guess acts as a kind of router?).

What would be it's IP address? I can't ping a website such as bbc.co.uk, already tried that.

---

### Post by nts on 2006-09-24
I'm pretty sure NTl give out routers or at least cable modems, does the box have a model number/manufacturer? 

(Just trying to find out exactly what setup you have there, to narrow the problem down)

---

### Post by DroobieAtYamba on 2006-09-24
I can't help but I have exactly the same problem and if I don't get some constructive help about it I'll scrap this Ubuntu and go back to Xandros oce 3.02

---

### Post by nts on 2006-09-24
> **DroobieAtYamba said:**
> I can't help but I have exactly the same problem and if I don't get some constructive help about it I'll scrap this Ubuntu and go back to Xandros oce 3.02

Maybe you could shed some light on the equipment that NTL issue?

---

### Post by DroobieAtYamba on 2006-09-24
> **DroobieAtYamba said:**
> I can't help but I have exactly the same problem and if I don't get some constructive help about it I'll scrap this Ubuntu and go back to Xandros oce 3.02
forgot to put this in original post except I am using a netcom dsl modem via ethernet0 but same result

---

### Post by lcarsdata on 2006-09-24
I have ntl and am just using a cable modem with both ethernet and USB output, some lights on the front but no buttons. It does come with some software, however the software is for macs and windows only. I use Windows for the net anyway.

---

### Post by nts on 2006-09-24
Log into the config page for the modem and note down the DNS resolver addresses - then enter these in the resolve.conf file.

---

### Post by DroobieAtYamba on 2006-09-24
Shouldn't make a difference Xandros oce 3.02 (another linux distro) works staight out of the box, with both my modem and ethernet

---

### Post by nts on 2006-09-24
sorry, resolve.conf is normally found in /etc/

---

### Post by nts on 2006-09-24
Well, 

I just found this with a quick Google search - seems to fix the problem

[http://66.102.9.104/search?q=cache:QsAG2xYOwMMJ:lists.slug.org.au/archives/slug/2005/06/msg00156.html+netcom+dsl+modem+with+ubuntu&hl=en&gl=uk&ct=clnk&cd=1](http://66.102.9.104/search?q=cache:QsAG2xYOwMMJ:lists.slug.org.au/archives/slug/2005/06/msg00156.html+netcom+dsl+modem+with+ubuntu&hl=en&gl=uk&ct=clnk&cd=1)

---

### Post by nts on 2006-09-24
You basically need to make sure that all network functions such as DHCP are all enabled in the modem/router and turned off in Ubuntu - could be a conflict issue

---

### Post by njparton on 2006-09-24
I think the router must be embedded in the cable box.

When setting up via windows you have to run start.ntl from a browser to register your PC with the cable box to get an internet connection.

I was surprised I didnt have to do that with the live CD to achieve an internet connection.

Anyway, whats the standard IP address of a router or a loopback IP that I can try?

---

### Post by xpod on 2006-09-24
I use ntl but its an "ambit" cable modem they gave me and it alls works with either ethernet or usb...

---

### Post by nts on 2006-09-24
I work for an ISP *most* routers are 192.168.1.1, but some use different addresses...

Could you use ifconfig to find the gateway address?

---

### Post by njparton on 2006-09-24
There are 2 gateway addresses in there already.

I'll try copying the one from windows now (swapping back and for at the moment :( ).

---

### Post by njparton on 2006-09-24
Well this is very strange. I tried pinging 192.168.1.1 - nothing.

I then went into the network properties and there are 2 DNS servers automatically entered: 194.168.4.100 and 194.168.8.100. I tried pinging the first one which was successful and then fired up firefox and now it works!

I wonder if I'll have to do this every time or if the "fix" will be permanent?

---

### Post by nts on 2006-09-24
Those are NTL DNS resolvers... like i said earlier, you should check that those are either setup in your resolve.conf file - the software that you get with Windows probably adds this in windows automatically.

---

