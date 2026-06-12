---
title: "No internet after installation..."
date: 2006-07-28
forum: Absolute Beginner Talk
---

### Post by Aurdal on 2006-07-28
Hey, I convinced one of my friends to give a shot at linux. So, he booted up the Live CD and installed. After he had rebooted into his new installation he had no internet, even though he did when he ran the live CD. I think he said he couldn't connect to the rest of the network either.

He has a ASUS k8n-e deluxe mother board with an integrated ethernet card.

---

### Post by %hMa@?b&lt;C on 2006-07-28
you can try
```
sudo pppoeconf
```
in terminal

---

### Post by Aurdal on 2006-07-28
He connects trough a router so I don't think  that's the answer really.

Sorry for not mentioning that.

---

### Post by Aurdal on 2006-07-28
Anyone?

---

### Post by davebgimp on 2006-07-28
Was he plugged into an ethernet cable during the installation? If not, I'd recommend reinstalling with an ethernet cable attached. If you were relying on a wireless card, that might have been the trouble. Usually, I have to install with an actual wired ethernet connection and then once all is groovy, take on wireless.

---

### Post by Aurdal on 2006-08-06
I was talking him trough it on GAIM while he did it, so yeah, he was connected. And yes it was with a cable.

---

### Post by davebgimp on 2006-08-07
> **Aurdal said:**
> I was talking him trough it on GAIM while he did it, so yeah, he was connected. And yes it was with a cable.

How exactly were you talking with him through GAIM while he was running the installation?

---

### Post by eXisor on 2006-08-07
I'd put $5 he's running two drivers for his network card, dfme & tulip. If he types 'lsmod' in a terminal, he should see both listed.
If he does, tell him to:

```
sudo gedit /etc/modprobe.d/blacklist
```

and then to add tulip to the bottom. After a reboot he should be good to go.

---

### Post by Aurdal on 2006-08-09
> **davebgimp said:**
> How exactly were you talking with him through GAIM while he was running the installation?

You haven't tried installing the 6,06 version from scratch, have you?

eXisor, I'll ask him to do that, thanks.

---

