---
title: "RealPlayer Installation Problem"
date: 2007-05-10
forum: Absolute Beginner Talk
---

### Post by bprof on 2007-05-10
Hi

I have tried to install real player on Ubuntu 7.04 but I failed to do so here is what I tried:

I tried this first:

[HTML]sudo aptitude install realplay[/HTML]

Couldn't find any package matching "realplay".  However, the following
packages contain "realplay" in their description:
  kmplayer-konq-plugins 

I tried

It said Couldn't find any package matching "".

So I download RealPlayer for Linux and used the following commands:

```
chmod +x RealPlayer10GOLD.bin
sudo ./RealPlayer10GOLD.bin
```

Everything went fine, I found a short cut for RealPlayer under Applications but it gives me an error message couldn't find realplayer

I tried from the command line by typing 

```
./realplayer
```

it gave me this error 

```
Segmentation fault (core dumped)
```

Could you please help?

Thank you,

---

### Post by kragen on 2007-05-10
Just to check - are you running the 32 bit or the 64 bit version of ubuntu?

---

### Post by bprof on 2007-05-10
> **kragen said:**
> Just to check - are you running the 32 bit or the 64 bit version of ubuntu?

32 bit

---

### Post by kragen on 2007-05-10
In that case .deb files should be available. If you cant find it under synaptic then make sure you have all the extra repositories enabled (multiverse etc...), or try here:

[https://help.ubuntu.com/community/RealplayerInstallationMethods?action=show&redirect=RealPlayerInstallationMethods#head-952f28daf565230d2827780b6cf3f7d31e116299](https://help.ubuntu.com/community/RealplayerInstallationMethods?action=show&redirect=RealPlayerInstallationMethods#head-952f28daf565230d2827780b6cf3f7d31e116299)

I'm sorry I cant test to make sure it works myself because I'm running 64 bit ubuntu (hence why I asked - I had massive problems installing realplayer because there are no 64 bit debs available).

---

### Post by Najand on 2007-05-10
where did you install your realplayer? And did you do it using root previlages (sudo command)?

---

### Post by Najand on 2007-05-10
> **kragen said:**
> In that case .deb files should be available. If you cant find it under synaptic then make sure you have all the extra repositories enabled (multiverse etc...), or try here:

[https://help.ubuntu.com/community/RealplayerInstallationMethods?action=show&redirect=RealPlayerInstallationMethods#head-952f28daf565230d2827780b6cf3f7d31e116299](https://help.ubuntu.com/community/RealplayerInstallationMethods?action=show&redirect=RealPlayerInstallationMethods#head-952f28daf565230d2827780b6cf3f7d31e116299)

I'm sorry I cant test to make sure it works myself because I'm running 64 bit ubuntu (hence why I asked - I had massive problems installing realplayer because there are no 64 bit debs available).

Realplayer is not included in the repositories. There is its alternative (Helix Media Player) in the multiverse repository, though.

---

### Post by bprof on 2007-05-10
Thank you guys,

kragen, I didn't find realplayer in repo.

Najand, I installed it in /opt/RealPlayer using sudo.

---

