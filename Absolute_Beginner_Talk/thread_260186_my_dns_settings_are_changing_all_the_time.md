---
title: "my dns settings are changing all the time"
date: 2006-09-18
forum: Absolute Beginner Talk
---

### Post by pedrotuga on 2006-09-18
I am using daper and i was having troubles connecting my computer to the internnet at home.

At my university i caonnect it without any trouble, but at home... despite being using DHCP i still have to set my ips' dns server manualy.
but... after a while it changes itself fot some 162.somethin.0.1... i cant understabd what can be causing this... what da heck can it be?

---

### Post by LotsOfPhil on 2006-09-18
So you know the DNS server you want to use, you put it in, and then after a little while it stops working?

Can you check what is in /etc/resolv.conf when it works and when it doesn't?

---

### Post by pedrotuga on 2006-09-18
> **LotsOfPhil said:**
> So you know the DNS server you want to use, you put it in, and then after a little while it stops working?

Can you check what is in /etc/resolv.conf when it works and when it doesn't?

not exactly... the thing is that it changes the dns server by itself, i dont know why... but when i go and check... there is the old 168.somthing.0.1 instead of the dns i defined... i dont get it.... why da heck does it changes itself???

---

### Post by skymt on 2006-09-18
Here's the fix. Run "gksudo gedit /etc/dhcp3/dhclient.conf". Look for the bit that looks like this:```
request subnet-mask, broadcast-address, time-offset, routers,
	domain-name, domain-name-servers, host-name,
	netbios-name-servers, netbios-scope;

```Remove domain-name-servers, so it looks something like this:```
request subnet-mask, broadcast-address, time-offset, routers,
	domain-name, host-name,
	netbios-name-servers, netbios-scope;
```That should fix it.
EDIT: Or, if your router supports it, enter the DNS servers into your router.

---

### Post by LotsOfPhil on 2006-09-18
> **pedrotuga said:**
> not exactly... the thing is that it changes the dns server by itself, i dont know why... but when i go and check... there is the old 168.somthing.0.1 instead of the dns i defined... i dont get it.... why da heck does it changes itself???

This may work. Put the following line in the /etc/dhcp3/dhclient.conf file.

prepend domain-name-servers 162.something.0.1;

Replace the 162.x.x.x with what your DNS is.

I think this is happening because whenever your box asks for an some info (because it is using DHCP) it overwrites /etc/resolv.conf. Both my solution and the other guys are trying to get it to remember/not overwrite the proper DNS info.

---

### Post by pedrotuga on 2006-09-19
> **LotsOfPhil said:**
> This may work. Put the following line in the /etc/dhcp3/dhclient.conf file.

prepend domain-name-servers 162.something.0.1;

Replace the 162.x.x.x with what your DNS is.

I think this is happening because whenever your box asks for an some info (because it is using DHCP) it overwrites /etc/resolv.conf. Both my solution and the other guys are trying to get it to remember/not overwrite the proper DNS info.

unfortunatly noone of those worked :(
the 162.x.x.x was not specified anywhere, anddoing the

  and removing "domain-name-servers" from dhclient.conf didnt work :(

if i go on system>administration>networking i have a location that i defined... the problem is... after one minute i go there againand my location is not selected anymore and there is tha same old 162.x.x.x dns... its anoying.

---

### Post by LotsOfPhil on 2006-09-19
> **pedrotuga said:**
> I am using daper and i was having troubles connecting my computer to the internnet at home.

At my university i caonnect it without any trouble, but at home... despite being using DHCP i still have to set my ips' dns server manualy.
but... after a while it changes itself fot some 162.somethin.0.1... i cant understabd what can be causing this... what da heck can it be?
You said you have to enter the DNS manually. Whatever the DNS that works for you is, put that after "prepend domain-name-servers". Remember the semicolon at the end. I thought that the 162.x.x.x was the valid DNS, not the broken one it changes itself too.

---

### Post by pedrotuga on 2006-09-19
> **LotsOfPhil said:**
> You said you have to enter the DNS manually. Whatever the DNS that works for you is, put that after "prepend domain-name-servers". Remember the semicolon at the end. I thought that the 162.x.x.x was the valid DNS, not the broken one it changes itself too.

this is very stupid... but i dunno so i should ask...

all those lines start with a #, doesnt that means they are commented? should i uncomment them?

---

### Post by LotsOfPhil on 2006-09-19
Yes. You need to uncomment the prepend line. I hope it works *fingers crossed*

---

### Post by pedrotuga on 2006-09-19
lets chek it out ;)

---

### Post by pedrotuga on 2006-09-19
damn... it didnt work :(

---

### Post by testube_babies on 2006-09-19
For some reason, Ubuntu rewrites /etc/resolv.conf frequently even if you have it set to read-only.  Here's what I've done to keep my system from rewriting it:

1) Set up your networking so that it is the way you want it.  Open up resolv.conf to make sure it's right.

2) Close resolv.conf and enter this command in a terminal to make the file immutable: ```
sudo chattr +i /etc/resolv.conf
```

All better!  But if you want to connect to another network or change your network settings you are going to need to undo what you just did by reentering the command using the flag '-i' instead of '+i'

---

### Post by pedrotuga on 2006-09-19
ok... maybe it worked the solution pointed by lotsofphil

so far its working fine for a while...
i guess if i use curl, wget or something like that it will xcrew it up.. lets wait and see

thx to everybody

---

