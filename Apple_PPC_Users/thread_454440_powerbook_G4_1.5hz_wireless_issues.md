---
title: "powerbook G4 1.5hz wireless issues"
date: 2007-05-25
forum: Apple PPC Users
---

### Post by tx_sumo on 2007-05-25
So I got sick of OS X for several reason and decided to back up and install Ubuntu, it was crazy easy.  Everything except, and this would be a deal breaker for me, my wireless card.  when I click on networking thingie in the top right corner it never shows any wireless access point, and I have about 9 around me. I have a fresh install and haven't added anything.  if it helps my wifi card is Broadcom 43x card.

Regards
Sumo

---

### Post by SycloneMedia on 2007-05-25
if you have feisty, then:

```
sudo aptitude update
```
```
sudo aptitude install bcm43xx-fwcutter
```

then if you're trying to connect to wpa networks, let us know for further directions after that...

---

### Post by tx_sumo on 2007-05-25
> **SycloneMedia said:**
> if you have feisty, then:

```
sudo aptitude update
```
```
sudo aptitude install bcm43xx-fwcutter
```

then if you're trying to connect to wpa networks, let us know for further directions after that...

Holy buckets it's working and better than my friends x86 Ubuntu machine! 	:guitar:

would you be kind enough to let me know what the WPA tricks are, I have friends who use WPA at their house.

Regards, 
Sumo

---

### Post by SycloneMedia on 2007-05-25
> **tx_sumo said:**
> Holy buckets it's working and better than my friends x86 Ubuntu machine! 	:guitar:

would you be kind enough to let me know what the WPA tricks are, I have friends who use WPA at their house.

Regards, 
Sumo

At the command line:

```
wpa_passphrase "(insert the name of the wireless network - in quotes if spaces between words)" (insert the password)
```

this will return the passkey (psk) to you.. copy and paste this psk into your network manager where needed for the WPA password. The network manager's don't take the regular WPA password at this time but they will take the psk.

---

