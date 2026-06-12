---
title: "Internet Not auto-starting anymore"
date: 2006-01-15
forum: Absolute Beginner Talk
---

### Post by rizzyc on 2006-01-15
when i installed Ubuntu LInux my router was preconfigured for my Bell sympatico internet... then one day i decided to see how i can connect w/o using my router.

I decided to run the sudo pppoeconf command and see if that would configure my internet connection... well what ended up happening was that i couldnt figure it out so i restored the changed that were made to some file it was talking about and then figured my router is easier and better anways.

Now Ubuntu doesnt automatically connect to the internet :( everytime it boots i have to go to systems > networking and activate it.. so somethign i done must have fudged it up...
i also noticed that when booting up it doesnt synchronize the clock with the ubuntu website anymore it says in red failed...

The following is the file that i backed up and then restored after i figured i must have fudged up my ineternet.
fyi. My internet is workign dandy but doesnt auto connect on start up any more :( and sometimes i think that it stops working out of the blue..
<code>
# Minimalistic default options file for DSL/PPPoE connections

noipdefault
defaultroute
replacedefaultroute
hide-password
#lcp-echo-interval 30
#lcp-echo-failure 4
noauth
persist
#mtu 1492
usepeerdns
</code>

---

