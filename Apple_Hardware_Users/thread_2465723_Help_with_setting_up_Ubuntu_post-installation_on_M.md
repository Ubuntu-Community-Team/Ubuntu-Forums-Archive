---
title: "Help with setting up Ubuntu post-installation on MacBook Air 2020"
date: 2021-08-09
forum: Apple Hardware Users
---

### Post by firelad97 on 2021-08-09
Hello, hope you had a good time/day/week. If I can spare a bit of your time here, that will be greatly appreciated.

So, I have issues that needs fixing right away. I tried to troubleshoot as much as I could (apt-get, software store, software updater). I am connected to internet by tethering USB with my Samsung.

I need to see if I can get drivers for WiFi card, Bluetooth card, keyboard, and trackpad. They currently do not work or are not present. The MacBook model is Intel-based 2020 Air. I am currently using the external mouse and virtual keyboard, but not in long run. This “external mouse” is actually Steam controller.

Respond and I will do my best to answer any questions you may have for me. Thanks!

- Ama

---

### Post by guiverc on 2021-08-09
You haven't provided any release details.  

Main Ubuntu releases use the *year.month* format which is a pretty good indicator of the age of the software stack (LTS releases have two stack choices though but are still behind). For newer hardware you really need a newer OS, but you've provided no details of what you're trying to use (you've installed).

---

### Post by scorp123 on 2021-08-09
What MacBook model number is that? And does it have an Intel CPU or one of the newer Apple "M1" CPU's?
Most MacBooks that came out after 2016 are known to be problematic when it comes to Linux support.
The reason being the "T2" security chip that will prevent Linux from functioning on such MacBooks.

See here:
[https://discussions.apple.com/thread/251260029]("https://discussions.apple.com/thread/251260029")

See here for a compatibility chart:
[https://github.com/Dunedan/mbp-2016-linux]("https://github.com/Dunedan/mbp-2016-linux")

---

### Post by firelad97 on 2021-08-10
> **guiverc said:**
> You haven't provided any release details.
Apologies. I was in a bit of rush I forgot to add that. I am on 20.04 LTS. I might also should mention that I started over and installed rEFInd before reinstalling Ubuntu (or should I say Ubuntu Bungie this time around?) and either way, issues still present. I will try updating from LTS to latest version (21.04) on current installation.

> **scorp123 said:**
> What MacBook model number is that?
I believe I already mentioned that it is Intel-based MacBook Air 2020, or more specifically, “The MacBook model is 2020 Intel-based Air.” Also yes I am aware about issues with M1 Macs. I can guarantee that I am not using an M1 MacBook Air. I can look up the serial number for this MacBook if you so desire. And thank you, I will check those links out.

However, y’all should also know that other than missing drivers, everything works perfectly with the exception of fatal error “grub install…” during installation which I already fixed on my own with research.

EDIT: Checked those two links out. Unfortunately they didn’t help… 1) The first link is related to Secure Boot, which newer Macs with T2 have, and I already disabled Secure Boot prior to installation. No issues. 2) That link is only for MacBook Pro models, nothing on Air models.

EDIT2: My apologies—the first link also mentioned kernel. I will see what I can do about it. Thanks again.

EDIT3: I upgraded to 21.04. Still nothing. Updating kernel seems to be related to updating the OS version, so I’m not sure what else to do.

---

### Post by gsahli on 2021-08-10
Have you been able to find out the wifi chip it uses? I "think" it's Broadcom B43xx. Start here:
[https://askubuntu.com/questions/55868/installing-broadcom-wireless-drivers](https://askubuntu.com/questions/55868/installing-broadcom-wireless-drivers)

---

### Post by scorp123 on 2021-08-10
> **firelad97 said:**
>  I believe I already mentioned that it is Intel-based MacBook Air 2020, or more specifically, “The MacBook model is 2020 Intel-based Air.” 

You still have not provided a detailed model number. Since I have to assume you completely removed Mac OS X and *"About this Mac > System Report"* is no longer available you will have to find out via the Linux terminal.

```
sudo dmidecode -s system-product-name
```

Result should be the exact model number, e.g. something like (... examples taken from my own Macs ... )

```
MacBook4,1
MacBookPro5,4
MacBookPro11,5
```

Knowing the exact model number would allow us to look up what hardware and what chipsets are built into it and if there are any specific steps needed to get this to work.

---

### Post by firelad97 on 2021-08-10
> **scorp123 said:**
> You still have not provided a detailed model number. Since I have to assume you completely removed Mac OS X and *"About this Mac > System Report"* is no longer available you will have to find out via the Linux terminal.
You seem to misunderstood me. I can still access macOS (I need it for Recovery OS in the case anything happens, plus it is no longer called Max OS X). I did say I can check for you. And either way, I am sorry if I hadn’t made it clear. I had been feeling very sick lately, and that’s not an excuse I’m going to use on this. I just wanted to let you know.

MacBook Air (Retina, 13-inch, 2020)
MacBookAir9,1

I apologize again. Thank you so much for taking your time to help me.

---

### Post by scorp123 on 2021-08-11
> **firelad97 said:**
> MacBookAir9,1

This thread over at the Linux Mint forum suggests that this model of MacBook Air is not going to work with Linux at this time:

[https://forums.linuxmint.com/viewtopic.php?t=343632]("https://forums.linuxmint.com/viewtopic.php?t=343632")

Since Linux Mint is based on Ubuntu, I'd say it's safe to assume that the observations made with Linux Mint also apply to Ubuntu in this case. And as I already previously wrote, the likely culprit is Apple's T2 chip that is blocking Linux from functioning. Quote from the thread above:

> I found a few other posts like this one on the apple community that basically suggest that newer hardware like my 2020 MacBook Air with **T2 chip** are just not yet supported by any current linux kernels.

They also link back to a discussion on an Apple forum that basically says the same thing:
[https://discussions.apple.com/thread/251260029]("https://discussions.apple.com/thread/251260029")

> Currently you cannot easily install Linux onto an Apple computer which uses the T2 security chip because the Linux Kernel with the T2 support is not included in any of the currently released distributions as a default kernel.

Now, I realise that the thread on the Linux Mint forum is from earlier this year, and the thread on the Apple forum is a little more than one year old. Things might have progressed since then.

It might thus be possible that newer versions of the Linux kernel might work better than what gets shipped with Linux Mint or Ubuntu. Therefore it might be worth it if you try out other distributions that are a bit more on the *"bleeding edge"* side of things. 

In no particular order:

[LIST]
[*]Ubuntu 21.10, once it is released (coming soonish in just a couple of months)
[*]Fedora Linux, [https://getfedora.org/en/workstation/download/]("https://getfedora.org/en/workstation/download/")
[*]openSUSE Tumbleweed, [https://get.opensuse.org/tumbleweed/#download]("https://get.opensuse.org/tumbleweed/#download")
[*]Debian Sid, [https://wiki.debian.org/DebianUnstable]("https://wiki.debian.org/DebianUnstable")
[/LIST]

Good luck.

---

### Post by firelad97 on 2021-08-11
> **scorp123 said:**
> …
Good luck.
Thanks so much. That’s actually very helpful. I’ll see what I can do about testing on the bleeding edge side. I will update this thread once I made some successful progresses.

---

### Post by firelad97 on 2021-08-13
I’ve kinda given up on this. Nothing works and it’s really tiring to try setting this up. I’ll be better off getting my own custom built PC and stick with bootcamp on Macs. Not to mention other complications going on in my life.

This thread can be closed.

---

### Post by expobill on 2021-09-15
dont feel bad, Firelady
i spent all yesterday trying to install Unbuntu on a macbook air 3,1 and never got past the white to orange dots
i even dusted off a cd player/burner and tried to install via a dvd.
at least you had some success installing the OS.

---

### Post by cybersecuritykid on 2021-12-21
I have the 2020 macbook air, intel. I cant even get it to boot from the usb drive. I disabled the security chip but it still wont boot from the usb, just goes straight into mac os.

---

### Post by makouser on 2021-12-23
FWIW I thought I'd add my experience.

I have a *Macbook Air* 2017 7,2 which I bought thinking 'well I can always load linux if I can't get on with macos'. I have been using Ubuntu for well over 10 years so was a little nervous.

Anyway, as the frustrations of the Apple straight jacket, ebb & flow, I have repeatedly got close to installing but cringe at the potential mine field that I'd be getting into. I have booted from USB without issue ( except the WIFI which is OK provided you can get an internet connection - I use my phone). Performance, mouse, screen all seem OK.

My only worry is battery life. There's so much info saying it will be worse. Having said that I find it gets worse with each OS upgrade anyway. No scientific basis for this just a feeling. 

I'm sure at some time I will take the leap.

---

