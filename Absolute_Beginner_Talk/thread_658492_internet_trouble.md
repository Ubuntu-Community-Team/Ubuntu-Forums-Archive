---
title: "internet trouble"
date: 2008-01-04
forum: Absolute Beginner Talk
---

### Post by nmahlman on 2008-01-04
i just got this computer for christmas... my brother built it and i have no idea how to fix it but it seems like everytime i start getting somewhere with my internet it disconnects...its wireless and its not mine its my neighbors so i dont know whats causing this

my wireless thing is edimax wireless lan pci adapter

---

### Post by bigmahlman on 2008-01-04
This is my little bro, ill try to give you all the information i know.   I dont remember what kind of card i put it but the box did say linux compatable.   The internet conects fine for a while then will suddenly just stop working.   somtimes is says it is still conected to the network.   
they are using a linksys router and buckey cable (simular to time warner)   
i was able to connect fine and stay connected from the same room with my lappy and it had 10% less connection.

he is a uber noob and i am having trouble helping him out.   

please help us try and figure this out


ps.  we do have the neighbors permision to leach the wireless.

EDIT:   he is able to stay connected with instant messanger fine all day long, but when he visits webpages it just eventualy stopls working.   

Im starting to thing it jsut might be the neighbors set up.

---

### Post by bigmahlman on 2008-01-05
should i have him reinstall firefox?

---

### Post by ugm6hr on 2008-01-05
> **bigmahlman said:**
> should i have him reinstall firefox?

Can't see that helping.

Which version of Ubuntu is this?  What encryption does the router use?  I know that the version of Network Manager in Feisty used to misbehave with WPA encryption.

The most likely reason is that the signal strength is a little weak, so it disconnects intermittently.  Pidgin can appear to remain connected even if it isn't - you won't know if it disconnects unless you are having a conversation at the time.

---

### Post by bigmahlman on 2008-01-06
> **ugm6hr said:**
> Can't see that helping.

Which version of Ubuntu is this?  What encryption does the router use?  I know that the version of Network Manager in Feisty used to misbehave with WPA encryption.

The most likely reason is that the signal strength is a little weak, so it disconnects intermittently.  Pidgin can appear to remain connected even if it isn't - you won't know if it disconnects unless you are having a conversation at the time.

gusty  no encryption

but his status never changes or anything i can see that he is online for like the 8 hours he is sleeping

i was thinking that its finding the stronger protected networks in the area and trying to connect,   its a decent connection,  my lappy and my bros macbook stay connected just fine,   and this thing has an external antenna out the window

---

### Post by ugm6hr on 2008-01-06
> **bigmahlman said:**
> gusty  no encryption

but his status never changes or anything i can see that he is online for like the 8 hours he is sleeping

i was thinking that its finding the stronger protected networks in the area and trying to connect,   its a decent connection,  my lappy and my bros macbook stay connected just fine,   and this thing has an external antenna out the window

OK. Very bizarre. Network Manager does rescan every now and then, but shouldn't disconnect while doing this (in theory).

If it looks like that is what is happening, maybe try Wicd.  See the link below.

---

