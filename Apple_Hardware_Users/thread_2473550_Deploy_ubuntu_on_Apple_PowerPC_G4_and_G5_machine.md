---
title: "Deploy ubuntu on Apple PowerPC G4 and G5 machine"
date: 2022-04-07
forum: Apple Hardware Users
---

### Post by vintageapple on 2022-04-07
My aim is to extend the lifecycle of 'vintage' Apple machines with PowerPC processor (G4 and G5). I tried several releases (12.04.4 and newer) with no success. I would like to give these old machines a second life by offering access to the modern internet (https sites). Who can help? Thanks.

---

### Post by guiverc on 2022-04-07
PPC is a dropped architecture, with 14.04 LTS being the last release of Ubuntu with full support, and flavors provided support with releases for 16.04 LTS. Both Ubuntu 14.04 LTS and flavors of 16.04 LTS reached EOL on April-2019.

From 14.04 support was added for PPC64EL and is now the only supported architecture ([https://wiki.ubuntu.com/ppc64el](https://wiki.ubuntu.com/ppc64el)) though it'll be of no use to you.

Refer [https://help.ubuntu.com/lts/installation-guide/powerpc/ch02s01.html](https://help.ubuntu.com/lts/installation-guide/powerpc/ch02s01.html) for supported architectures for Ubuntu 18.04 LTS (bionic).

FYI:  *ppc64el* is a *supported architecture; but apple has never made a machine capable of running it as they moved to intel instead.*

---

### Post by vintageapple on 2022-04-07
Thanks for your response. Does it mean that you recommend not to deploy 14.04 because of the EOL? Or just take the risk?

---

### Post by ronsking on 2022-04-07
You might check out MintPPC:


[https://www.u58733p55594.web0093.zxcs-klant.nl/]("https://www.u58733p55594.web0093.zxcs-klant.nl/")

---

### Post by QIII on 2022-04-07
Moved to Apple Hardware Users.

For the sake of everyone else, please do not install an unsupported release of any OS, even Ubuntu, on a machine that will connect to the internet.  Doing so will expose an unprotected machine to compromise and that endangers us all.

---

### Post by guiverc on 2022-04-07
Ubuntu 14.04 LTS is fine if your machine is going to be **used offline**.

In your initial post you mention "*modern internet*"  which cannot ***safely*** be provided with an **EOL** OS.

Whilst I'm a Debian user, I have no experience & have not kept up with Debian's support of the ***ppc*** architecture, nor any other OS. 

I considered installing Ubuntu long ago on the one old powerpc mac I have, but the device is *old & slow* & performs worse than 32-bit IBM laptops I have thus it made little sense, so I kept the apple OS9 on it & keep it just to play some old games on it on rare occasion.

---

### Post by TheFu on 2022-04-07
> **vintageapple said:**
> Thanks for your response. Does it mean that you recommend not to deploy 14.04 because of the EOL? Or just take the risk?

NEVER run an EoL OS if you plan to use it on a network.
A few other distros probably support the PPC version your system have.  Debian might. [https://www.debian.org/ports/powerpc/inst/install](https://www.debian.org/ports/powerpc/inst/install)

Debian is likely the most mainstream release with the widest HW support.  There may be specialty releases created by Linux+Apple nerds that could be worth checking out.

But Ubuntu ain't the droid you seek anymore.

---

