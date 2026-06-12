---
title: "network manager gutsy - im sorry for being so stupid"
date: 2007-10-18
forum: Absolute Beginner Talk
---

### Post by teh'p3nsi0n3r on 2007-10-18
me being rather silly have managed to use "add/remove" to remove the network manager front end applet, ive barely had any sleep thats my excuse :lolflag: seriously i was waiting up for gusty release last night and had no sleep. :)

being serious though, the network manager applet was only showing "old wireless spots" i dont know why but i was in the car (not driving of course) and my laptop picked up other spots as we were passing (i was not attempting to connect to these btw), i got into uni to go and access the wireless and it wasnt showing/updating the access points, it was still showing the ones from the hotspots that were sohwing the car as if they were cached.

spoke to a fellow student (who also uses ubuntu) advised me to remove the network manager and reinstall it, and again this where the stupid part comes in .... i ran add/remove without thinking, removing the network manager and relised i had no net connection and cannot reinstall it :lolflag: is there anyway i can get it back? the only way i can think of just now is to use my wired access point at home? and run add/remove again, or is there a way i can get a .deb file of the network manager and reinstall it on my laptop? :KS

---

### Post by teh'p3nsi0n3r on 2007-10-18
:)bump

---

### Post by kazamx on 2007-10-18
I have had a look around online and can't find a .deb for network manager. I found some tar.gz version, but assume you wouldn't know what to do with them (I don't) 

I think your best option is going to be to wait until you get home and use your wired connection. As you mentioned it I am guessing that you can get that all set up. 

I am sure someone else could tell you how to work around the problem, but I guess it maybe complex. If you can wait until you get home maybe that would be best. 

As always I admit I am a noob and any advice offered should be taken knowing that

Good Luck

---

### Post by teh'p3nsi0n3r on 2007-10-18
> **kazamx said:**
> I have had a look around online and can't find a .deb for network manager. I found some tar.gz version, but assume you wouldn't know what to do with them (I don't) 

I think your best option is going to be to wait until you get home and use your wired connection. As you mentioned it I am guessing that you can get that all set up. 

I am sure someone else could tell you how to work around the problem, but I guess it maybe complex. If you can wait until you get home maybe that would be best. 

As always I admit I am a noob and any advice offered should be taken knowing that

Good Luck


i will probably just wait till i get home for a wired connection :) thanks though for your help, its apreciated :)

---

### Post by tact on 2007-10-18
sorry I cannot be of more specific help as I dont know the commands myself.  But surely someone can help you to manually bring up a network interface and get connected without network manager.

perhaps post again with the topic "how do I bring up a network interface manually - I deleted network manager accidently"    -  that might get more people looking in and offering advice

Can you get any ideas from entering the below in a terminal?
```
ifconfig --help
```

For wireless try 
```
iwconfig
```

In the help/options you may figure out how to bring up wifi and get connected.

---

### Post by teh'p3nsi0n3r on 2007-10-21
oops...i forgot about this thread, i fixed the issue when i got home, you were right my wired connection was fine, i did not need the network manager, i reinstalled the "nm-applet" frontend, and this fixed the wireless issue, i can now use wireless again.
thanks for all the help.:)

---

