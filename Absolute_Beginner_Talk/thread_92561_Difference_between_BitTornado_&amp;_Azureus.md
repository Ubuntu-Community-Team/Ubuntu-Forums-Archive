---
title: "Difference between BitTornado &amp; Azureus"
date: 2005-11-19
forum: Absolute Beginner Talk
---

### Post by goyan on 2005-11-19
Hi all,

I have tried to use both BitTornado and Azureus on Ubuntu. I live in university's hall of residence, so all the ports are blocked.... When I use Azureus, the upload is poor, v.poor. However, once I started to use BitTornado, I some times gets over 2MB/s upload rate! What is the difference between these bittorrent clients?

Is there a multi-torrent version (like Azureus) of BitTornado?

Thank you for your time.

Goyan

---

### Post by bionnaki on 2005-11-19
this is copied from another forum

> 
Some ISP's like Optonline and many universities try to limit torrenting. Some just block ports, some use filters and traffic shaping, some (at least Optonline) detect the moment when you switch from leeching to seeding and disrupt the connection. Here are some tricks and clients you can try.



Blocked ports

First of all, don't use the default ports, they are often blocked. You also shouldn't use a port that is used by any known trojan. Pick a random port (or a small, perhaps 20 or so port range if your client uses a port range) from between 40000 and 60000, and make sure it isn't blacklisted.



Traffic shaping

These tricks are known to fool at least some filters:


BitTornado 0.3.12
When set to super seed, it somehow hides some information.


BitComet 0.60
This version has an option to encrypt headers, so that the traffic doesn't resemble bittorrent so much.

Go to 'Preferences' -> 'Advanced' -> 'Connection' and set 'Protocol Header Encrypt' to 'always'



Lazy bitfield

At least Azureus and µTorrent support an option called lazy bitfield. When torrent switches from leeching to seeding, the client sends a specific bitfield information. At least Optonline detects this info, and sends spoofed packets to both peers causing the clients to terminate the connection. When lazy bitfield is turned on, the client sends altered info.

µTorrent has an easy setting to turn it on, Azureus has to be started with a command line parameter. This is done differently in windows and OS X, for linux take a look at this.


µTorrent

Go to 'Preferences' -> 'Advanced options' and set 'peer.lazy_bitfield' to true, save and restart µTorrent


Azureus (windows)

You can create a bat file that starts azureus when executed. Go to the directory where azureus is installed
(for example c:\program files\azureus) and create a new text document. Paste this line into it:

start javaw -Dazureus.lazy.bitfield=1 -classpath Azureus2.jar;swt.jar;systray4j.jar org.gudy.azureus2.ui.swt.Main

Save the document, and change the file ending to .bat (for example the file could be called Azureus.bat). It has to be in the same directory with Azureus2.jar, but you can make shortcuts to the bat if you want. Start Azureus by executing the bat.


Azureus (OS X)

For OS X, you have to edit a file inside the azureus package. Go to Applications, and find Azureus (or where ever you installed the package to).

Hold ctrl and click on Azureus (or with second mouse button if you have one). It should pop up a menu. Select "Show package contents". Then go to a folder named 'Contents'. In there you should see azureus again. Do the same, select "Show package contents." Again, go to 'Contents'. Now you should see a file named 'Info.plist' there. Open it with any text editor, text edit will do fine.

Now, look for a line that has

-Xms16m -Xmx128m -Djava.library.path=$JAVAROOT/dll

on it. Change that part to

-Xms16m -Xmx128m -Djava.library.path=$JAVAROOT/dll -Dazureus.lazy.bitfield=1

Save the file and start Azureus normally.


maybe it'll help.

---

