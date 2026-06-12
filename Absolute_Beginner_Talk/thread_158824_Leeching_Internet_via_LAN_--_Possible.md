---
title: "Leeching Internet via LAN -- Possible?"
date: 2006-04-11
forum: Absolute Beginner Talk
---

### Post by UnknownVariable on 2006-04-11
The only thing that was keeping me from installing Linux on my desktop was the fact that I knew I wouldn't be able to connect to the internet, as I was connecting via a Dell Wireless Card to my Dell router, and there was no Linux-capable drivers for that from what I've seen.

So I came up with an idea. What if I were to connect to the internet using my laptop (with Windows XP), connect both my laptop and desktop with a Cat 5 (ethernet) cable, and share the internet connection?

Well, first, I'm not sure if that's even possible. Is it? And if it is, how would I go about doing so? I've tried clicking around in some of the Network areas on Linux, but I'm not exactly sure what I'm doing, and most things are disabled as it is.

I've checked the wiki, and it just noted I should check my router's documentation for connecting, but that would be if I was directly connecting to the router, which I'm not.

Does anybody have any suggestions for me? Thanks. :)

---

### Post by 5-HT on 2006-04-11
Does the router have ports for a direct connection?

If so, easiest thing would be to just run a direct link from the router to the desktop.
As long as the desktop's NIC is recognized, you'll have no problem.

You could do a connection sharing, but it's more involved and would also require a direct connection to the desktop (but from the laptop instead of the router) anyway. If you were to do this, you'd have to enable internet connection sharing on the windows laptop (there's a wizard for it somewhere in a menu). I'd only consider doing this myself if I couldn't connect the desktop directly to the router.


There may be a chance at getting Ubuntu to recognize your wireless card in the desktop though. There are many threads on how to get wireless, that wasn't working out of the box, working on Ubuntu using a wrapper for the windows drivers. I don't like wireless myself, so I couldn't really help you there.

HTH

---

### Post by UnknownVariable on 2006-04-11
Oh, forgot to mention. I do already have both computers connected with a cat 5 cable. My father is rather lax at running a wire from the basement up to my room for me to direct connect to the router, which is why I'm trying to go this second route-- at least for the time being.

After I finish the windows internet sharing, would I have to do anything else on the Linux end?

I'm going to skip the wireless card route if at all possible. Too much hassle, I think. 

Thanks for the help! :****D

---

### Post by 5-HT on 2006-04-11
If you're going that route, I think something like this should do it*:

i) Set up internet connection sharing on the windows box
   -It'll most likely have to be a static address for the  NIC  
   -Something like IP = 192.168.0.1 , netmask = 255.255.255.0

ii) Configuring Ubuntu with a static IP**.
    System > Administration > Networking > Ethernet Connection > Properties
    Set it for something like IP = 192.168.0.2 , netmask = 255.255.255.0
    You may also need to set the DNS to the LAN IP of the windows box


*You may need a crossover ethernet cable for this (basically the wires at one end are reversed).  This is usually only needed for older NICs as most newer ones do the switching themselves. So try it out with what you have now, and if need be either make (google search should turn up a lot of guides, it's really straightforward) or buy a crossover cable.

**You may need to tell windows the IP of the other computer when you go through the wizard (haven't done it myself).



HTH

---

### Post by UnknownVariable on 2006-04-15
Whoops. I had a bit of a downtime from the internet for a few days. Sorry 'bout that. Anyhow~

There seems to be a few problems so far... First, when I run the Internet Connection Sharing Wizard on Windows, it's trying to set up a home network, and also says that the Wizard must be run on all other computers that will be part of the network*. 

And next, I'm not able to access Administration > Networking on Ubuntu. The menu is there, but when I click on Networking, nothing at all happens. 


* I understand you might not be able to help with this part. I'm still fiddling around with it to see if I can help myself as well. :****D

Thanks for the help so far. It's been appreciated greatly.

---

### Post by 5-HT on 2006-04-15
[quote=UnknownVariable] I'm not able to access Administration > Networking on Ubuntu. The menu is there, but when I click on Networking, nothing at all happens. [/quote] 
What about trying it from the command line ```
 network-admin 
``` 
If that doesn't work, can you start any of the administration utilities in that menu? 
Can you start synaptic from the menu?
 Can you use sudo from the terminal (say 'sudo ls')?

If you cannot do any of the above, it looks like your user may not have sudo permissions. 
Here's a link that walks you through how to enable your user to use sudo: [http://www.ubuntuforums.org/showpost.php?p=901128&postcount=4]("http://www.ubuntuforums.org/showpost.php?p=901128&postcount=4")

[quote=UnknownVariable] when I run the Internet Connection Sharing Wizard on Windows, it's trying to set up a home network, and also says that the Wizard must be run on all other computers that will be part of the network*. 

* I understand you might not be able to help with this part. I'm still fiddling around with it to see if I can help myself as well. :D [/quote] 
I havn't done this myself, but maybe the wizard just says that to make it easy to configure the other computers. 
If you can get into network-admin, you would be doing this manually so there would really be no need for the wizard.

Does it look like the ICS has been setup for the laptop? If the wizard completed successfully, it may work so long as you can manually input the required settings in Ubuntu. 

Someone else with actual experience of doing this may be able to help you much better for this one though.

HTH

---

### Post by matthew on 2006-04-15
I'm moving at the moment so I won't be able to do tech support for this, but take a look at my how to on the wiki with a link back to the forum thread where I first posted it and see if you are able to figure out how to modify it for your uses...it isn't too hard, but if you're new at it you may have to read it a few times to feel comfortable.

[https://wiki.ubuntu.com/forum/hardware/UseWirelessLaptopAsAnInternetAccessPoint](https://wiki.ubuntu.com/forum/hardware/UseWirelessLaptopAsAnInternetAccessPoint)

---

### Post by trent dillman on 2006-04-15
I've set this up before. Ignore the M$ crap about other computers.

---

