---
title: "xubuntu network problem"
date: 2007-01-19
forum: Absolute Beginner Talk
---

### Post by Ian Swain on 2007-01-19
I think I have searched thoroughly for any references to this problem, so please let me off lightly if it has been covered somewhere in the mass of threads....

I've just installed Xubuntu 6.06 on a Toshiba 440cdt laptop - P1 223MHz - and despite it's 3com Megahertz PCMIA network card being detected during the instalation (and the dongle and hub LEDs also lighting during instalation) I have no sign of a network upon first boot: no eth0 offered to me when I look in 'network-admin', no LEDs lit. 
During boot up I saw "PCMIA not present" scroll past. To me it seems as if the machine has forgotten that it detected the network card during the instalation.
When I did a Ubuntu install on another machine a while back it all just worked straight off, giving me a false sense of security, so I  need a few hints, preferably fairly idiot proof stuff! 
The hardware is all OK, as I have had the laptop networked successfully while running DSL and W98 on the laptop, using all the same cables and hub.
3COM LAN Card is Model 3CCFE574BT

Thanks in anticipation....

---

### Post by slipperhead on 2007-01-19
i had this problem a while ago. i had to add xubuntu live cd as a repository(as network was ok on live cd)
then used synaptic to get pcmcia services(cant remember exact package,just search for pcmcia)

i had to untick all the other repos(settings in synaptic) to make it use the cd then put it back to normal after.
this worked for me. hope it helps you.

edit. there is also a link to download pcmcia services if i can find it for you.
also, if you used the alternate cd and your net card was ok during installation you might be able to use that as a repository too.

---

### Post by slipperhead on 2007-01-19
[http://security.ubuntu.com/ubuntu/pool/main/p/pcmcia-cs/](http://security.ubuntu.com/ubuntu/pool/main/p/pcmcia-cs/) 

this is a list of all the pcmcia-cs.

the 4th one from the bottom of the list is the one i used (i think) i386 version.)

---

### Post by Ian Swain on 2007-01-20
Thanks slipperhead, I'll persue those ideas. I did use the Alternate CD, having failed to get the Live to intall - not enough RAM - so both CDs are to hand.

---

### Post by Ian Swain on 2007-01-20
Ah... I have pcmcia cs services installed already. 4th up the list ties in with what is installed. What do I check out next? On searching for 'PCMCIA' in synaptic I seem to have the full set.

---

### Post by slipperhead on 2007-01-20
where you see pcmcia in synaptic, are the checkboxes green(for installed)?
if not ,install the pcmcia_cs.
my expertise doesnt go so far other than i installed the package and everything worked.
maybe someone else can jump in with more advice.
you could try sudo modprobe (the name of your net card) in the terminal and see what it returns

---

### Post by slipperhead on 2007-01-20
also, if you are seeing 'pcmcia not present' when booting, this would suggest that it is not installed. so try installing it anyway and the other packages, pcmcia_utils etc just incase.

---

### Post by Ian Swain on 2007-01-20
Yes, everything PCMCIA in synaptic is checked, with the exception of wlan. Thanks for your help, I've at least eliminated one possibility. Time for terminal I guess.

---

