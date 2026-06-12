---
title: "Wireless Internet not Working..."
date: 2006-09-30
forum: Absolute Beginner Talk
---

### Post by coolbian57 on 2006-09-30
My wireless internet connection is still not working!

I have tried everything, and i have had a lot of success so far, but this last step has me confused.

I have set up everything correctly, my Wirless USB adapter is perfectly recognized, i average aboout 95% wireless avaliablility (or whatever its called), and i have my DHCP set up so i know im getting the right DNS and IP.  I also have 4 different WEP keys and have tried each one in Hexidecimal and AASCII format.

But still, when i open up firefox, and type in google, it sais server not found.

What did i forget to do?  Is it a router problem possibly?

ARGHH](*,) ](*,) ](*,) 

Please help.  (Iv'e been working on this for 4 days now)

---

### Post by Josh1 on 2006-09-30
So you can access your router?

---

### Post by theknave on 2006-09-30
In the terminal, type in the command "route". Does that give you any output numbers? Or just a few headings?

---

### Post by coolbian57 on 2006-09-30
As far as i can tell, yes.  But lately i am getting the feeling that it could be a router issue.

When I did the Iwconfig wlan0 code in the terminal, for the ESSID it just said "".  Normally there would be something in between the " and the other ".  But i know i configured it correctly, i have it set to have an ESSID on the Network Adminstrative thing.  And i have it set to the correct one.

(In fact, now that i think about it, it automaticlly recognized my ESSID and i never had to enter it.)

I tried the add ESSID code thing ( i can't remember what the exact code was, sorry) in the terminal, but it replied that I could not do that, something about not enough privilages.  I didn't think that it would matter too much, so i kinda forgot about that. But if that is my problem please tell me.

---

### Post by theknave on 2006-09-30
If you wanted wireless internet, you don't need to look at lwconfig, but rather you should be using iwconfig, if I'm not wrong. Give that a go and see what it says.

---

### Post by coolbian57 on 2006-09-30
Yea i was using IWconfig.  

For the Route command, it just had a bunch oif headers  i saw no numbers at all for any of the data.

So this is an issue, how do i fix it?  Will i need to manually enter my DNS and IP and whatnot?

---

### Post by theknave on 2006-09-30
Okay, well if you're not getting any numbers out of 'route' (for example, my output looks like this:

```
brett@Brett:~$ route
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.0.0     *               255.255.255.0   U     0      0        0 wlan0
default         192.168.0.1     0.0.0.0         UG    0      0        0 wlan0
brett@Brett:~$ 
```, and this is your goal)

Have you got any WEP or other security enabled? I suggest you disable it - I had WEP enabled and couldn't get my wireless working unitl I disabled it. You always want to start with the simplest system and work up. You can enable it later.

---

### Post by coolbian57 on 2006-09-30
> **theknave said:**
> Okay, well if you're not getting any numbers out of 'route' (for example, my output looks like this:

```
brett@Brett:~$ route
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.0.0     *               255.255.255.0   U     0      0        0 wlan0
default         192.168.0.1     0.0.0.0         UG    0      0        0 wlan0
brett@Brett:~$ 
```, and this is your goal)

Have you got any WEP or other security enabled? I suggest you disable it - I had WEP enabled and couldn't get my wireless working unitl I disabled it. You always want to start with the simplest system and work up. You can enable it later.

Yes i have WEP enabled and i think it may be my issue.  I've narrowed it down to either a Router, DNS, or WEP key problem.  

So how do i disable my WEP?  I know that is a supremely newb question, but seriously.  I don't know how.

---

### Post by theknave on 2006-09-30
Hey, bud, I didn't know how to do it either before I got setting up my wireless connection.

What you need to do is go into a Windows partition (or, more efficiently, another computer that does have internet support), and find out your router I.P. address. Then you want to type that in to the URL bar of your favourite browser, and type in the username and password (for me, the username is "admin" and there is no password). Then you want to find the section on "security", and from the drop-down menu, select "none".

Remember to configure your ubuntu connection settings accordingly.

---

### Post by coolbian57 on 2006-09-30
But, how do i figure out my routers IP adress.

---

### Post by coolbian57 on 2006-09-30
How can i figure out what my routers IP adress is?

---

### Post by coolbian57 on 2006-09-30
If anybody knows the Internal IP adress for a Motorola SBG940 wireless router, please tell.

Heh, thats a hopeless cause.

---

### Post by coolbian57 on 2006-09-30
Does anybody know how I could find out my routers internal IP adress?

---

### Post by oyvindaa on 2006-09-30
> **coolbian57 said:**
> Does anybody know how I could find out my routers internal IP adress?

[http://192.168.100.1](http://192.168.100.1)

or

[http://192.168.10.1](http://192.168.10.1)

Unless I misunderstood your question..

---

### Post by mojojo on 2006-09-30
I'm having the same problem.  I think the IP address in in your documentation for th router.  I'm checking on mine now and I'll let you know!  I have Linksys WP300N - what's yours?

---

### Post by coolbian57 on 2006-09-30
Hey everybody thank you so much for your support.

I FINALLY GOT MY INTERNET SET UP AFTER 4 DAYS!!!

Turns out it WAS a problem with the WEP encryption key.  I had to go into my router on my Windows partition and edit some things on there.  

Thanks all for the support. 

I WOULD NOT have done this without you guys.

---

### Post by theknave on 2006-09-30
Sorry, bud, I got distracted. I'm not sure, I think the router's IP address is standard for each type of router.

---

### Post by mojojo on 2006-09-30
coolbian57, don't leave me.  Tell me what you did on the windows side.  PLEASE!!

---

### Post by mojojo on 2006-09-30
Well, I'm off to the XP side to disable WEP.   If anyone is still listening, I'll brb!!

---

### Post by soleil on 2006-09-30
I'd like to chime in here since I am having the same problem under slightly different cirumstances.  My wireless card is fully recognized, and on my university's campus wireless network it works just fine.  However, at home, and at various hotspots around town, it produces the same error discussed above.  Data is moving--I can see it in the wireless status dialog--but I can't resolve any domain names, either with firefox, ping, or anything else.  My home network does not have a WEP key.  Instead, my roomate who runs the router added my laptop to his list of allowed machines, which caused two tings: the wireless on the WinXP side of my laptop started working, and the Ubuntu side started getting a signal but not resolving. So, now where do we go?  I have it set to use DHCP, so I haven't entered any DNS IPs or anything.

-s

---

### Post by ttoes on 2006-10-02
Motorola's IP addresses are 192.168.100.1 or 192.168.10.1, <admin> as username and <motorola> (no <chevrons>) as the factory default password.
Linksys router address is (usually) 192.168.1.1, from the factory with no user name and <admin> as the password.
DLink uses 192.168.0.1, <admin> as the username and no password
But you need to be connected, preferably by wire connection, to access any of these or change them.

I also have had no success with WEP encryption and Ubuntu (or Suse 10.1). Unsecured, no problem at all--except that I'm unsecured. My WEP setup works fine with Windows XP. I've tried many times now to no avail. Does anyone have a foolproof way to get WEP encryption working with Ubuntu?

---

### Post by ttoes on 2006-10-03
WEP working!
With Ubuntu Network Administation tool only the first key (choice of 4 keys) works.
Now I have to find a way to enable better encryption (WPA)

---

### Post by Mimsy on 2006-12-21
If you did find a way, would you mind letting me know? I just set up a Motorola SBG940 at home, and Ubuntu just won't play nice with it. No connection whatsoever, in other words. The modem is not even deteced and recognised.

/Mimsy

---

### Post by jbutler12 on 2006-12-21
Mimsy, if your card is not naturally detected by Ubuntu and / or there is no linux driver issued by motorola for it, you have to use ndiswrapper to "wrap" the windows driver and get it to work on your system.

See [http://czarism.com/easy-peasy-wireless-w-ubuntu-debian-linux](http://czarism.com/easy-peasy-wireless-w-ubuntu-debian-linux) for step-by-step instructions.  (make sure you have the ubuntu CD so you can install ndiswrapper-utils off of it in Synaptic).
-John

---

### Post by Mimsy on 2006-12-21
The card works without problems. It shows as "activated" in the Network Manager GUI. The laptop just can't seem to find our wireless network.

/Mimsy

---

### Post by jimrz on 2006-12-21
> **coolbian57 said:**
> But, how do i figure out my routers IP adress.

Check the user man that came with the router, it will tell you the default IP to it. If you no longer have it, go to the manufactures website where you should be able to find supprt info listing it.

Also, and I know this sounds way too simple, but check in network and see what DNS servers it is looking for. All of the Ubuntu "live" cd's I have tried and (I think) even some of the installs did not have correct DNS targets by default, had to delete (if any were even listed) and manually enter correct ones.

---

