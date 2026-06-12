---
title: "Getting Programs to Install through Sudo (As Well As Wireless Card WPA thing)"
date: 2007-04-23
forum: Absolute Beginner Talk
---

### Post by DeadSuperHero on 2007-04-23
Well, I'm pretty new to Ubuntu. I don't quite know a whole lot about installation or sudo.
I've got WINE installed (and will be getting Cedega soon from my Mom)
However, I want to know: how do I go about installing Windows games through sudo? I can't seem to get WINE to use the Windows Installer (for example, I can't install Steam or Half Life 2 from their respective install programs. What commands do I use for that?)

On another note, my wireless card isn't working very well. I'm getting a signal just fine, but my home network is a WPA encryption, and I'm not very sure about how to make Ubuntu see those.
Cheers,
Mr. Psychopath.

---

### Post by Kobalt on 2007-04-23
About Wine : [https://help.ubuntu.com/community/Wine](https://help.ubuntu.com/community/Wine)

For your wireless network is suggest you try Network-Manager first : [https://help.ubuntu.com/community/WifiDocs/NetworkManager](https://help.ubuntu.com/community/WifiDocs/NetworkManager)

---

### Post by DeadSuperHero on 2007-04-23
I've got WINEto work fairly well.
However, I can't seem to tell the Network Manager to use a WPA encryption.
I tried just copying bits of a tutorial I read for WPA encryption for sudo, but everytime I type
> sudo vi /etc/wpa_supplicant.conf

I get an odd error message (will post that message later when I log back in as root.)
It basically says that "Oh, this file seems to have been messed with. You can try to 1) recover it or 2) Do something else, press ENTER or just type something to continue."

That causes the terminal to mess up, forcing me to restart the terminal.

Any ideas?

Or is there a WPA tutorial for Feisty?

---

### Post by Kobalt on 2007-04-24
Network-Manager normally support WPA out of the box, you just click your network and it detects the encryption key method, and asks for your key.

---

### Post by TRinQtown on 2007-04-24
My only option under Network Manager is WEP, there is no WPA.

---

### Post by DeadSuperHero on 2007-04-24
Yeah, it only asks for WEP.
Is there a way I can get WPA to work on it? Or will I have to dumb down the family network to WEP, and change all their Windows computers to recognize this, just so that I can use the wireless internet?

---

