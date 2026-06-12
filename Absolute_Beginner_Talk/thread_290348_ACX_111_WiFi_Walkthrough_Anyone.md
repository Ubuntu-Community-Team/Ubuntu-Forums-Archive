---
title: "ACX 111 WiFi Walkthrough? Anyone"
date: 2006-11-01
forum: Absolute Beginner Talk
---

### Post by Tweedicus on 2006-11-01
Hi,

Could someone do a walk through for installation of an acx 111 wifi card. It should work on Ubuntu. 

The drivers have installed (acx_pci), they did so automatically when I installed Edgy. I believe they're native drivers to Ubuntu, no ndiswrapper was needed. The card powers on when I boot up but doesn't work. I've searched the threads, but the advice give doesn't walk in this case.

Could someone please do a step by step walk through with me please. 

Thanks

Tweed:)

---

### Post by |Syrius| on 2006-11-01
I have a D-Link G520+ and i did this way:

```
sudo mkdir /lib/firmware/your_kernel/acx/default
```

Grab your firmware from [http://www.hauke-m.de/fileadmin/acx/fw.tar.bz2]("http://www.hauke-m.de/fileadmin/acx/fw.tar.bz2")

Untar the firmware and move it to the directory created above

```
tar xvfj fw.tar.bz2
cd fw
sudo mv acx111_1.2.1.34/* /lib/firmware/your_kernel/acx/default
```

I choose acx111_1.2.1.34 because of my card chipset but you can find the correct one from the list in [http://acx100.sourceforge.net/matrix.html]("http://acx100.sourceforge.net/matrix.html")

Just restart your network, and don't forget to configure it from System->Administration->Networking

Hope that helped!!

---

### Post by Tweedicus on 2006-11-01
You know, I'm not sure what I did or how I did it, but I entered different things in /etc/somewhere, did something with firmware, renamed a couple of things, did something called modprobe, restarted my system twice, then enter a network key and I was greeted by the flashing green light on my wifi card. I'm writing this from a wifi connection and it worked.

I didn't need to download anything. It seems if you have edgy all the drivers and firmware are there, you just need to type and reconfigure a few things.

Anyhow, it works.

Thanks for replying.

---

### Post by Ksmith3637 on 2006-12-11
thats great but where did you look for them or what did you do




> **Tweedicus said:**
> You know, I'm not sure what I did or how I did it, but I entered different things in /etc/somewhere, did something with firmware, renamed a couple of things, did something called modprobe, restarted my system twice, then enter a network key and I was greeted by the flashing green light on my wifi card. I'm writing this from a wifi connection and it worked.

I didn't need to download anything. It seems if you have edgy all the drivers and firmware are there, you just need to type and reconfigure a few things.

Anyhow, it works.

Thanks for replying.

---

