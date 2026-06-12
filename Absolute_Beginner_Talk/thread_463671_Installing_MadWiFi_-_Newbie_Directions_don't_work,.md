---
title: "Installing MadWiFi - Newbie Directions don't work, as usual"
date: 2007-06-03
forum: Absolute Beginner Talk
---

### Post by Brightbelt on 2007-06-03
I'm on Ubuntu Studio with a Gateway M675x laptop. I'm installing MadWiFi to work as a driver for a new Wna-2330 wireless G card Adaptor. 

(Optional reading: My Rant: None of these newbie directions work!! I'm about to wrap it up with Ubuntu Linux. When things work, they work. And either they work or they don't. It really is that cut and dry most of the time. Configuring is a nightmare and rarely goes the way directions say they will. Do Linux developers think everyone is a programmer or has coding abilities? 
......OK, Sorry about the rant, but I needed to. Here goes...)

I'm following the newbie directions from [http://madwifi.org](http://madwifi.org)  to install MadWiFi. I downloaded it and unpacked it on my desktop.

When I do these: 

ifconfig ath0 down
ifconfig wifi0 down

I get 

'ERROR while getting interface flags: no such device'

Next, when enter the scripts directory (Cd scripts), I'm supposed to do this:

./madwifi-unload.bash

But then I get back 'No such file or directory'. And the NEXT line I'm supposed to enter is VERY unclear...

./find-madwifi-modules.sh $ (uname -r) cd ..

Am I supposed to make up a name for the 'uname' thing? Is it supposed to be in parentheses? Is cd at the end really part of this command? (I've never seen a 'cd' at the end, but I'm new...) Are the DOTS supposed to be there?!! 

Ok, so assuming, there's nothing there because I get errors anyway, when I try to install, it tells me there are old modules that I should remove !!!!! (What was i just trying to do?!!)

Also, when I go ahead and run the install and it gives me the options to remove old modules by pressing 'r', when I do, it tells me "FATAL: wlan is in use." So how do I turn that off? 

I appreciate any help and concrete specifics...Sorry to rant, but this install blocks me at EVERY turn.

Many Thanks, Frank B.

---

### Post by Brightbelt on 2007-06-03
In my ranting I forgot to add these time-savers:

- I'm already using 'sudo' in my commands. 
- I've also tried doing a 'complete removal' of MadWiFi in the Synaptic package Manager as a way of getting rid of old modules

Thanks, Frank B.

---

