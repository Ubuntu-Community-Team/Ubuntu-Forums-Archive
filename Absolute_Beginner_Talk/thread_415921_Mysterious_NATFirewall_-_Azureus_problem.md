---
title: "Mysterious NAT/Firewall - Azureus problem"
date: 2007-04-20
forum: Absolute Beginner Talk
---

### Post by arsadogi on 2007-04-20
Ok here it is my story.I am connected to internet with a router(Fritz box) and apt-get_ed azureus.when i tried to download smth with it i  faced this message."

[COLOR="Red"]UPnP:Mapping 'incoming Peer Data Port  (UDP/"port number"' failed
UPnP:Mapping 'incoming Peer Data Port  (TCP"port number"' failed

[/COLOR]

So my torrent tracker is down and i can't download.(In a decent speed)
I searched previous posted threads in the forum and i figured out that i have
NAT/firewall problem.I forward the port in my router and i downloaded firestarter and in the Policy tag i add a rule 
Service=bittorrent
Port="port that uses azureus"
  i checked in azureus at
Tools > NAT/Firewall test.
Testing Potr: "bla bla lba" OK

i retart Azureus and there is the damned message again ->>
[COLOR="Red"]UPnP:Mapping 'incoming Peer Data Port  (UDP/"port number"' failed
UPnP:Mapping 'incoming Peer Data Port  (TCP"port number"' failed

[/COLOR]

I simply can't figure it out...:confused:

---

### Post by PurplePenguin on 2007-04-20
Shouldn't you turn off UPnP if you're opening up your own ports?

---

### Post by arsadogi on 2007-04-20
First of all what is UPnp at all.And if i need to turn it off how can i do it?

---

### Post by arsadogi on 2007-04-21
Ok i fixed it.I turned off the UPnP from Tools>Options>Plugins.i found i useful link  [here]("http://www.azureuswiki.com/index.php/NAT_problem")

---

### Post by PurplePenguin on 2007-04-21
Is it working better now?

---

### Post by arsadogi on 2007-04-23
yeah but then i encounterned another error. this time [COLOR="Red"]disk read error[/COLOR] i searched the forum about this and i found out that gij (i think) the JRE open source cantidate
is bugged so  i configured the built in bittorrent and it's working great so i choose to keep it simple.

---

### Post by Thangalin on 2007-04-24
Remove GIJ and install Sun's JVM.

It seems GIJ, which is the Java Virtual Machine installed by Feisty, cannot handle the connection load required for Azureus to perform properly.

1. sudo apt-get remove gij
2. rm /usr/bin/java
3. Download Sun's JVM ([http://java.sun.com);](http://java.sun.com);) try "Java Runtime Environment (JRE) 6u1"
4. Install Sun's JVM into /opt/jdk1.6.0
5. Set your PATH to include /opt/jdk1.6.0/bin
6. Close your shell window.
7. Open a new shell window.
8. Run Azureus.
9. Help -> About
10. You should see "Java 1.6.0" in the "System" pane.
11. Enjoy faster download speeds!

---

### Post by daverave999 on 2007-04-25
How would one go about performing 4 and 5 please?

---

