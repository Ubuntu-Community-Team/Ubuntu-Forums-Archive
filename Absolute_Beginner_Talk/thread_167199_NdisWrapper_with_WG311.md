---
title: "NdisWrapper with WG311"
date: 2006-04-27
forum: Absolute Beginner Talk
---

### Post by deadlycow21 on 2006-04-27
I have been searching around everywhere for a way to get this to work. I have a wg311 and, i can't get it to work very well in windows (my current OS)... I was thinking that maybe ndiswrapper would help me with this... I am going to switch over to ubuntu soon but, i cant get internet from in my room so, i have put ndiswrapper on my jump drive. ](*,) 

what should i do to install this... i was thinking this would be easy because i could just go: ```

apt-get install ndiswrapper.deb 
``` but, what do i do to install this without internet access? do i need to still use the drivers on my cd or is there a way to just use ndiswrapper to use my internet card.... You guys are my last hope on this....:-k

---

### Post by deadlycow21 on 2006-04-28
[QUOTE=deadlycow21]I have been searching around everywhere for a way to get this to work. I have a wg311 and, i can't get it to work very well in windows (my current OS)... I was thinking that maybe ndiswrapper would help me with this... I am going to switch over to ubuntu soon but, i cant get internet from in my room so, i have put ndiswrapper on my jump drive. ](*,) 

what should i do to install this... i was thinking this would be easy because i could just go: ```

apt-get install ndiswrapper.deb 
``` but, what do i do to install this without internet access? do i need to still use the drivers on my cd or is there a way to just use ndiswrapper to use my internet card.... You guys are my last hope on this....:-k[/QUOTE]

i really need an answer.... [bump]

---

### Post by erik_boi on 2006-04-28
to install a .deb that you have downloaded...

```

sudo dpkg -i name.deb

```

That should however be on the ubuntu cd and you could just install it how you normally would from synaptic or the command line (I think).

-Erik

edit: it looks like your card may be supported and ndiswrapper wouldn't be needed, but it also looks like there are a couple of versions so check out

[https://wiki.ubuntu.com/HardwareSupportComponentsWirelessNetworkCards?highlight=%28wireless%29]("https://wiki.ubuntu.com/HardwareSupportComponentsWirelessNetworkCards?highlight=%28wireless%29")

---

### Post by deadlycow21 on 2006-04-28
Thank you very much! i will try this.

---

### Post by deadlycow21 on 2006-04-28
[QUOTE=erik_boi]to install a .deb that you have downloaded...

```

sudo dpkg -i name.deb

```

That should however be on the ubuntu cd and you could just install it how you normally would from synaptic or the command line (I think).

-Erik

edit: it looks like your card may be supported and ndiswrapper wouldn't be needed, but it also looks like there are a couple of versions so check out

[https://wiki.ubuntu.com/HardwareSupportComponentsWirelessNetworkCards?highlight=%28wireless%29]("https://wiki.ubuntu.com/HardwareSupportComponentsWirelessNetworkCards?highlight=%28wireless%29")[/QUOTE]


looks like only version 2 works... i have version 3 :( which would explain why it is not working, btw, i am making my own driver (so far i have taken out all the LED stuff and am hoping that this MAY be the reason it is freezing up...

---

### Post by deadlycow21 on 2006-04-29
[QUOTE=deadlycow21]looks like only version 2 works... i have version 3 :( which would explain why it is not working, btw, i am making my own driver (so far i have taken out all the LED stuff and am hoping that this MAY be the reason it is freezing up...[/QUOTE]

worked for 10 hours so far... this looks like my solution.

---

