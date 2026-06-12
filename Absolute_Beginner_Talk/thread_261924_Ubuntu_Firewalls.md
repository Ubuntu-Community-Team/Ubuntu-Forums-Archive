---
title: "Ubuntu Firewalls"
date: 2006-09-20
forum: Absolute Beginner Talk
---

### Post by CombatGod on 2006-09-20
I'm looking for a firewall which has active logging and I can see all IP addresses accessing the server ports. 

Right now I have Lokkit and it's nice but I'm looking something that I can actively monitor and have logs of activity. Is there anything out there like that?

---

### Post by Bugsly on 2006-09-20
I've been reading about Firestarter firewall. I believe it has the features you're looking for. I'm trying to download and install it. I can't find the download. This is the Ubuntu begginers page and that represents the extent of my Linux knowledge. Please post back if you find a Firestarter download. I'll so the same.

---

### Post by wieman01 on 2006-09-20
**Firestarter** is certainly a good option. Have been using it for a while and it has logging function to various degrees. It fairly reliable and easy to configure. 

You find **Firestarter** in the repositories, there is no need to download & compile to. Let us know if you have problems installing or configuring it. We can help.

---

### Post by CombatGod on 2006-09-20
I just opened up Synaptic and looking for it right now, thanks.

I'll let ya know how it works.

---

### Post by jISh on 2006-09-20
sudo apt-get install firestarter

It just configures the firewall you already have by default, iptables.

---

### Post by CombatGod on 2006-09-20
Thank you so much. I just installed it. Opened up inbound port 80 and my server is set.

This is everything I was looking for. I greatly appreciate it.

---

### Post by wieman01 on 2006-09-20
Just one thing to bear in mind: If you have troubles connection to you router after the installation, you need to open "inbound" and "outbound" for DHCP. 

Firestarter can be quite a trap... Some networking application may refuse to work unless you open up the corresponding ports. Don't forget that. I keep falling into the same trap again & again.

---

### Post by Bugsly on 2006-09-21
Okay, for us beginners; System/Aministration/Synaptic Package Manager.
I did a search for Firestarter. Then looked under "Settings" to find "Repositories", Selected the first Ubuntu repository and clicked "Add".
Went back to the Synaptic and clicked reload. Ubuntu went and found Firestarter. Downloaded it. Follow the path and install it. Nice. This is my first evening with Ubuntu. I'm also toying with Xandros. I'm liking the world of Linux. Thanks for the help people. 'Til we meet again.

---

### Post by CombatGod on 2006-09-21
I just set the the Outbound Policy to Permissive by Default. I monitor my server every day so I can block any outbound ports which have too much activity. It also makes it easier since I dont' have to consistantly open all the ports.

Just out of curiousity is there a Win32 version of Firestarter?

I've tried so many Win32 firewalls and they have all been garbage. This is by far the best.

---

### Post by wieman01 on 2006-09-21
Not sure about a Win32 version... But another comment: Set your policy to restrictive and allow only those ports that you really need. But I am saying this without know what your purpose is. Just a thought from a security-nerd and paranoid. :-)

---

### Post by elpuerco on 2006-09-21
wieman01,  I am unable to get out onto the internet in a browser whilst connected to eth0 on my laptop when here at work.

At home on eth1 I have free access.

Work supplied me with proxy detail and the said I should be able to get out but I cant.  I can ping hosts local to me and elsewhere in our organisation.

I see you mention inbound and outbound for DHCP?  I know squat of firewalls etc so am lost and cautious about what I turn off and on.

Can you advise?

---

### Post by wieman01 on 2006-09-21
Hey Mate, 

Sure, no problem. 2 things you need to do:

1. Fire up Firestarter and go to Edit->Preferences->"(Firewall)Network Settings" and change "Detected devices" from "eth1" to "eth0" [COLOR="Blue"](screenshot 1)[/COLOR].
2. Add a new rule for **both** "ingoing" and "outgoing" traffic under tab "Policy". Select "Allow service"->Name "DHCP", then hit add [COLOR="Blue"](screenshot 2)[/COLOR].

So you will have 2 more rules. Don't forget to reconfigure "Preferences" when you connect via "eth1". But you get the idea, right?

---

### Post by hkgonra on 2006-09-21
Just a suggestion but I prefer to keep my servers as servers and have a seperate hardware firewall. There are SEVERAL good ones to choose from. I use ipcop, it can be run on old hardware, ( think that old p233 you have in the closet ) and does a good job with it. That way it sets right after your modem and takes care of everything from the outside, it also solves several of the other problems being discussed above about other network services not working.

---

### Post by wieman01 on 2006-09-21
> **hkgonra said:**
> Just a suggestion but I prefer to keep my servers as servers and have a seperate hardware firewall. There are SEVERAL good ones to choose from. I use ipcop, it can be run on old hardware, ( think that old p233 you have in the closet ) and does a good job with it. That way it sets right after your modem and takes care of everything from the outside, it also solves several of the other problems being discussed above about other network services not working.
Good point. For mobile computers this is hardly possible but for a home network this is certainly the best option. I prefer hardware firewalls as well (using a router to achieve that) but since I need to travel quite a bit, a reliable local software firewall is a must... I hook up to lots of wireless networks in China. Crazy stuff going on there. :-)

Appreciate the comment though.

---

### Post by elpuerco on 2006-09-21
Hi,  I am going to try what you suggest re configuring FF thanks:D 

Just to confirm this will FF know which network device to use so when at work eth0 will kick in and when at home eth1?

Or will I have to keep manually swapping??

Thnx ;)

---

### Post by b_martinez on 2006-09-21
For  a decent Win32 firewall, go to simtel.net and download the SPF5.6 (Sygate personal firewall version 5.6). It's free, but you do have to register it.
hth
Bill

---

### Post by elpuerco on 2006-09-21
As I am at work I want to test the firestarter DHCP thing.

However I dont have firestarter on my laptop yet and cannot access web whilst at work.

Can someone point me to the latest version download that is not through adept/synaptic please?

Thnx

---

### Post by bobpur on 2006-09-21
If you've downloaded Automatix, you'll find firestarter in there. Automatix used to be in the Third party section in the forums startup page but I see it has been moved. I'm sure you can still find it somewhere, though.

---

### Post by wieman01 on 2006-09-21
I have attached the Firestart Debian file. Just remove ".zip" suffix by renaming the file and you can install it like any other Debian file. I can not upload *.deb files so I had to rename it in the first place.

I think you have to change Firestarter's devices manually. As far as I know there is no way to have Firestarter recognize the change by default.

---

