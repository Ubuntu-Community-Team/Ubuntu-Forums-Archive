---
title: "Upgrading Help Please!"
date: 2007-07-30
forum: Absolute Beginner Talk
---

### Post by Katocan on 2007-07-30
I currently have ubuntu 5.10 running on my laptop and I was wondering if anyone could help me on how I would upgrade to 7.04, I downloaded 7.04 and burned it to a cd but when i tried putting it in my laptop it wont boot up so I was wondering if anyone could help me on how I could upgrade by using terminal or some other kind of method.

Thanks for any help :)

---

### Post by oilchangeguy on 2007-07-30
first, what are your computers specs?

---

### Post by misfitpierce on 2007-07-30
If it does not boot you my need to force boot to CD or you burned the ISO wrong / it messed up.

---

### Post by shearn89 on 2007-07-30
you'll have to upgrade to 6.* first - via terminal:
```

sudo apt-get update
sudo apt-get dist-upgrade

```
Then repeat... I think that should work. If not, the regular update manager should find a new distro: System -> Admin -> Update manager (or something similar)

---

### Post by Katocan on 2007-07-30
The specs on this laptop are
RAM: 256 MB
HDD: 20 Gigs
CPU: 1GHZ Mobile AMD Athlon 4

Is that of any use?

Thanks :)

---

### Post by oilchangeguy on 2007-07-30
> **shearn89 said:**
> you'll have to upgrade to 6.* first - via terminal:
```

sudo apt-get update
sudo apt-get dist-upgrade

```
Then repeat... I think that should work. If not, the regular update manager should find a new distro: System -> Admin -> Update manager (or something similar)

re-read the users first post. they have a 7.04 disc. so, there is no need to go to 6.10 first.

---

### Post by shearn89 on 2007-07-30
I can run GNOME on my laptop - 512MB, 640Mhz processor, 10Gb hd... you might be alright. If its slow or jerky, just download and install openbox, xfce, or fluxbox.

@oilchangeguy: but if the disk isn't working, and they have a decent internet connection, its not too much trouble to update in 2 steps. I had to buy a disk, as my laptop just can't deal with burnt discs (i tried about 10, 3 of which were burnt at 1x speed with perfect md5s...)

---

### Post by Katocan on 2007-07-30
> **shearn89 said:**
> you'll have to upgrade to 6.* first - via terminal:
```

sudo apt-get update
sudo apt-get dist-upgrade

```
Then repeat... I think that should work. If not, the regular update manager should find a new distro: System -> Admin -> Update manager (or something similar)

When I try and update is says that "Your distribution is no longer supported", I'm taking it that theres no other way then to try and boot from the CD?

---

### Post by diatribe on 2007-07-30
is your cd listed first to boot in your BIOS?  also if you put in the cd I think if you open synaptic you can add the files on the cd into your synaptic repo

---

### Post by diatribe on 2007-07-30
yes go to edit -> add cdrom and see if that works

---

### Post by deadgobby on 2007-07-30
You have a older version of the distro. You'll need to back up every thing that you have saved. The simple way is to fresh install feisty 7.04 and load up your save files. The long way is to upgrade to dapper, to edgy, and then to fawn. That is going to take all day and it may not even work. Sorry to be the person to give you bad news. So back up and install 7.04. 
Gobby

---

### Post by oilchangeguy on 2007-07-30
> **Katocan said:**
> The specs on this laptop are
RAM: 256 MB
HDD: 20 Gigs
CPU: 1GHZ Mobile AMD Athlon 4

Is that of any use?

Thanks :)

i'd suggest using the alt. version of 7.04. 256 is the bare min. to install, and your video card is likely eating some of that.

---

### Post by shearn89 on 2007-07-30
> **Katocan said:**
> When I try and update is says that "Your distribution is no longer supported", I'm taking it that theres no other way then to try and boot from the CD?

try going to system -> admin -> update thingy and see if that lets you?

---

### Post by shearn89 on 2007-07-30
> **deadgobby said:**
> You have a older version of the distro. You'll need to back up every thing that you have saved. The simple way is to fresh install feisty 7.04 and load up your save files. The long way is to upgrade to dapper, to edgy, and then to fawn. That is going to take all day and it may not even work. Sorry to be the person to give you bad news. So back up and install 7.04. 
Gobby

oh yeah - i forgot that 5.04 is breezy... I though you were on dapper... I'd go with this method then, as the net upgrade will take a while. Sorry oilchange - you were totally right... :redface:

---

### Post by Katocan on 2007-07-30
Thanks alot for the help everyone, I really appreciate it :)

---

### Post by sailor2001 on 2007-07-30
as oilcan mentioned, download the alt. 7.04..........remember to burn as an image iso and burn at a low speed

---

### Post by Katocan on 2007-07-30
I burned ubuntu 7.04 to CD again and this time the CD started up but when i tried to install it said.

I/O error
Error reading boot CD

and giving me the option to Reboot.

Anyone have any idea how else I could put 7.04 on my laptop

Thanks.

---

### Post by shearn89 on 2007-07-30
maybe order a free cd from canonical (mine arrived in a couple of weeks), or buy one for about £4. Do a google for "linux discs". This was the only way i could upgrade, as i'm on retricted internet, and one of the packages was liboob*, another was libsex*... Both were essential packages!

---

### Post by RedSquirrel on 2007-07-30
> **Katocan said:**
> I burned ubuntu 7.04 to CD again and this time the CD started up but when i tried to install it said.

I/O error
Error reading boot CD

and giving me the option to Reboot.

Anyone have any idea how else I could put 7.04 on my laptop

Thanks.

Did you burn the **Alternate Install CD** or the LiveCD?

The alternate install CD only requires 64 MB of RAM to install.

With only 256 MB of RAM you may want to consider Xubuntu. It would probably run better.

In any case, be sure to check the md5 sum of the download before you burn and check the integrity of the CD before you install. 

[https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)

---

