---
title: "Installed Ubuntu today"
date: 2006-01-19
forum: Absolute Beginner Talk
---

### Post by Anti-Establishment on 2006-01-19
Need help fast, i'm tired and can't understand how I install new programmes.

I particularly want amsn messenger and FrostWire, but can't for the life of me figure out how to install them. When I download them, they never open, if I save them to the desktop, where do I go from there?

---

### Post by zAo on 2006-01-19
Read this first. When "universe" is enabled, you can install amsn.
> [https://wiki.ubuntu.com/SynapticHowto?highlight=%28synaptic%29](https://wiki.ubuntu.com/SynapticHowto?highlight=%28synaptic%29)

---

### Post by Anti-Establishment on 2006-01-19
Sweet thanks.

---

### Post by cjm5229 on 2006-01-19
Another thing to try is Automatix. go to customization tips and tricks (Ubuntu forums) you will find the howto right on top. Works like a charm.

---

### Post by hen3rz on 2006-01-19
Hello,

You can find a tutorial on installing programs in ubuntu here:
[http://www.psychocats.net/linux/installingsoftware.php]("http://www.psychocats.net/linux/installingsoftware.php")

To install FrostWire you can check out this HowTo:
[http://www.ubuntuforums.org/showthread.php?t=105169&highlight=frostwire]("http://www.ubuntuforums.org/showthread.php?t=105169&highlight=frostwire")

I used it and had no problems. I would recommend the Lazy way by Aeon17x.

To install amsn you can try this howto:
[http://www.ubuntuforums.org/showthread.php?t=87001&highlight=howto+amsn]("http://www.ubuntuforums.org/showthread.php?t=87001&highlight=howto+amsn")

I haven't tried this howto yet as I use Gaim as my msn client but Im sure it will work fine.

---

### Post by Anti-Establishment on 2006-01-20
> I used it and had no problems. I would recommend the Lazy way by Aeon17x.

Thanks. but I don't understand this:[QUOTE=Aeon17x]For the lazy, here's something a bit shorter - 

0.) If you haven't installed Java, do it now [[http://www.ubuntuforums.org/showthread.php?t=76702&highlight=java]("http://www.ubuntuforums.org/showthread.php?t=76702&highlight=java")]. FrostWire needs it to operate.
1.) Install the alien package through Synaptic or the terminal -
```
sudo apt-get install alien
```
2.) Go to the FrostWire [download page]("http://www.frostwire.com/index.php?title=FrostWire:Download") in the FrostWire wiki and download the RPM package. Alternatively, you can enter this in the terminal - 
```
wget -c http://voxel.dl.sourceforge.net/sourceforge/frostwire/FrostWire-4.10.0-1.i586.rpm
```
3.) Now go to the folder where you downloaded the RPM, and use alien to install it directly.
```
sudo alien -i FrostWire-4.10.0-1.i586.rpm
```
4.) If you did it right, you should see FrostWire at Applications > Internet.

That's it. Frostwire is based on the LimeWire code; it does everything LimeWire Pro does, except FrostWire is totally free and wouldn't be restricted in the future. :)[/QUOTE]

What is the alien package? And where do I add those codes in the synaptic?

---

### Post by bartbes on 2006-01-20
what don't you understand?

---

### Post by Anti-Establishment on 2006-01-20
[QUOTE=bartbes]what don't you understand?[/QUOTE]
What is an alien package? Where is it?

---

### Post by jon_z on 2006-01-20
an easier alternative might be to visit the automatix link in my signature beneath my post...type the commands into an open terminal..   Automatix will isntall frostwire painlessly.

---

### Post by carlosqueso on 2006-01-20
the alien package converts .rpm files which Ubuntu doesn't like to .deb files which it will eat happily.  To get it, type.  ```
sudo apt-get install alien
``` to install it.  Then follow the rest of the directions in that howto.  Just type what it says in the code blocks into a terminal, not synaptic.  To get a terminal, go to Aplications->Accesories->terminal (I think).  Then type the commands there.

---

### Post by Anti-Establishment on 2006-01-20
Automatix is my new God, Hail Automatix.

Thank you all very much.

---

### Post by Burning Bronx on 2006-01-20
[QUOTE=Anti-Establishment]Automatix is my new God, Hail Automatix.

Thank you all very much.[/QUOTE]

The official statement about automatix from the Ubuntu support channel

[quote=ubotu]somebody said automatix was messy, breaks all sorts of security guidelines, and is not open to improvement. In short: DO NOT USE IT![/quote]

I have found this statement to be entirely true. Automatix "may" work but eventually it'll mess you up. I suggest you do some reading at the above mentioned links. It will be a lot more educational and a lot safer for your system.

---

