---
title: "Intel 3945abg Flakey"
date: 2008-04-15
forum: Absolute Beginner Talk
---

### Post by neurostu on 2008-04-15
I currently have intel 3945 wireless and it is really flake


Has anyone with this adapter been able to overcome how flakey it is in linux?

---

### Post by Seisen on 2008-04-15
which version of Ubuntu are you using and what version of the intel 3945 do you have?

```
lspci
```

---

### Post by Golem XIV on 2008-04-15
I have this card on a Vostro 1400 laptop.  In Gutsy I had to replace network-manager with Wicd and it worked.  In Hardy beta it "just worked".

---

### Post by neurostu on 2008-04-15
Seisen:
I'm running Gutsy:

```

$lspci | grep 3945
03:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG Network Connection (rev 02)

```

I previously had tried installing Wicd but it gave me some errors about needing to remove network manager first, and I was a little hesitant to take the plunge and possibly end up losing my internet  connection all together.

---

### Post by Golem XIV on 2008-04-15
> **neurostu said:**
> Seisen:
I'm running Gutsy:

```

$lspci | grep 3945
03:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG Network Connection (rev 02)

```

I previously had tried installing Wicd but it gave me some errors about needing to remove network manager first, and I was a little hesitant to take the plunge and possibly end up losing my internet  connection all together.

What happens is that Wicd will uninstall the packages "network-manager" and "network-manager-gnome".  The trick is to have them in your apt cache, so you can reinstall them via apt-get or Synaptic even if Wicd screws up and you lose internet connectivity.

Open a terminal and type
```
ls /var/cache/apt/archives | grep network
```
you should see something like ```

network-manager_0.6.6-0ubuntu5_amd64.deb
network-manager-gnome_0.6.6-0ubuntu2_amd64.deb
```
The version numbers may be different since I am using Hardy beta 64 bit.

If you have these two packages, then if Wicd fails to work you can reinstall network manager with
```
sudo apt-get install network-manager network-manager-gnome
```
even if you don't have a connection.  It will uninstall Wicd and install the stock network manager back.

---

### Post by neurostu on 2008-04-15
So it looks like I don't have them in my cache.
```

slayton@stockton-mini:~$ ls /var/cache/apt/archives/ | grep network
slayton@stockton-mini:~$ 

```

how can I get them in my cache?

---

### Post by Golem XIV on 2008-04-15
There is a "download only" option in apt-get (I think it's the -d switch)

You can also download them from [here]("http://packages.ubuntu.com/gutsy/network-manager") and [here]("http://packages.ubuntu.com/search?searchon=names&keywords=network-manager-gnome") (for Gutsy).  Then either copy them to the apt cache or install them by double-clicking the DEB file (in this case you may have to uninstall wicd manually first).

---

### Post by neurostu on 2008-04-15
So I took the plunge and installed Wicd, I'll report back in a few weeks with how it is working out.

---

### Post by starcannon on 2008-04-15
I have Intel 3945abg on this HP Pavilion dv2000, and on my moms Dell 1420n, both running Ubuntu 7.10, wifi works out of the box, rock solid. I never get unexpectedly dumped, I can access wep, wpa, wpa I and II enterprise, leap, peap, msvchap, etc... etc... all from default wireless nm-applet.

I think you have some sort of settings issue, the hardware is very compatible.

---

### Post by neurostu on 2008-04-19
So i changed to Wicd and I'm still having the same issues with my wireless. I think it has to do with the intel drivers and Hardy should overcome most of those issues.

---

### Post by neurostu on 2008-04-22
If I restore the gnome-network-manager how do I get it to start up automatically again?

---

### Post by Blingin2Mingin on 2008-04-26
I have a Dell Inspiron 9400 with an Intel wireless 3945abg card.
This worked perfectly until I upgraded to Hardy on Saturday Morning.
I was left with no connection and no led.

Firstly I upgraded the iwl driver.

Please ensure Hardy-Backports are enabled under Software Sources.

Then open a terminal.

```
sudo apt-get install linux-backports-modules-hardy-generic
```



The led now worked, but connecting to any WEP or WPA encrypted network didn't.

Spent the best part of 4 hours searching for an answer nothing seemed to work. (Had to use wired connection)

So I took the plunge and ditched Network Manager and installed Wicd and Bingo! it worked. In fact it works so well I won't be going back when this bug is finally fixed.

The following line requires adding to the 3rd party software repositories.

```
deb http://apt.wicd.net hardy extras
```

wicd site is here:

[HTML]http://wicd.sourceforge.net/[/HTML]


Hope this is some use to someone.

---

### Post by neurostu on 2008-04-26
I just switched to Hardy Heron, I'll report back on the wireless issues.

---

### Post by Joeb454 on 2008-04-26
I have the same Wireless chipset, the Intel 3945abg :) I have to say that for me it's always worked flawlessly out-the-box with Ubuntu (7.10 and 8.04)

Does it actually find wireless networks?

---

### Post by neurostu on 2008-04-26
I did a fresh install of Hardy and the wireless adapter is working great. 

On another note, I presonally wasn't very happy with wicd.

---

### Post by jkilgrow on 2008-05-03
I'm running a Dell XPS 1730 with an Intel/PRO Wireless 3945ABG card. Heron is the first Linux distro run on this box. Ok....Heron is the first Linux distro I've ever run.

Anyway, my wireless card did not work at first. I found a post explaining how to, basically, remove all of the Heron stuff and go back to Gibbon so that I could get my wireless card working.

Well, after doing that, NOTHING worked! So I undid what I did in the instructions and, VIOLA!! Suddenly my card is working! Yay me!

So, if anyone is interested, let me know and I'll dig up the forum post for ya.

---

