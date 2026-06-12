---
title: "Bluetooth: cannot browse phone in Gutsy"
date: 2008-02-24
forum: Absolute Beginner Talk
---

### Post by Majiq on 2008-02-24
People seem to have found a solution to my problem, but no one seems to be saying anything about it. This is the thing: I'm on my second installation of Ubuntu because I got another external and wanted to run Ubuntu off of my new external. Trying to set up the bluetooth to link to my phone, though, would not work. It worked on my first installation, but I can't stick to that one because it's on an external hard drive that requires power. 
Does someone know the answer to the problem for the following error message that comes up when trying to access a cell phone via the bluetooth browse device menu?

"
Couldn't display "obex://[mac address]".
Check if the service is available.
"

I have bluez-utils, bluez-gnome, and gnome-vfs-obexftp installed already. I know it's not a phone issue because it worked in my first installation. What happens is that the connection dialog pops up on my phone for about a half a second and then disappears and then the above message comes up on my computer.

All help appreciated.

---

### Post by RudolfMDLT on 2008-02-24
Hi,

Could you please try using the KDE bluetooth utilities. I have been working with Ubuntu's bluetooth for about 2 years now and the Gnome guys are years behind KDE.

In synaptic, install the "kde bluetooth" packadge. The download might be a big one as you may need to download core kde files to make it work.

Once the install is done, in gnome, under Applications -> Internet, you should find "kbtobexclient". This will then allow you to send and receive files.

Also, KDE's version of Nautilus, called Konqurer supports browseing of bluetooth devices nativly.

Post back if you have any problems,

Cheers,

Rudolf

---

### Post by pat_can_vault on 2008-02-25
Thanks for the help, but I am still experiencing problems. I was able to send files TO and FROM my LG Chocolate I think KG800i on Windows and Mac, and browse devices on both. (The Windows was on the same laptop - Toshiba Satellite - I was able to get the built-in bluetooth working using omnibook.) I don't understand how to use the ktbobexclient either.

Some more help?

ps. when trying to send things to my Mobile using the ktbobexclient It says there is an error. it sends OK using the gnome client.:)

---

### Post by MarilenCorciovei on 2008-02-28
I managed to browse my sony ericsson k550i using the information from [this page]("http://www.len.ro/work/tools/ubuntu-gutsy-on-a-dell-latitude-d820/k550i-sync/view")

---

