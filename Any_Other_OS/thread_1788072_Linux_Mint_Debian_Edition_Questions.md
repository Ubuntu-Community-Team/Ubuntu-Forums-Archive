---
title: "Linux Mint Debian Edition Questions"
date: 2011-06-22
forum: Any Other OS
---

### Post by slooksterpsv on 2011-06-22
Now I know some of these questions will be like duh, but still I just want more of a confirmation for what I'm asking if I'm right or an addendum to what's wrong with my statements.

1. My hardware works better under LMDE (specifically I don't have to patch my sound) because the kernel isn't modified, it's pretty much a direct compile from kernel.org with minor changes for it to work under Debian? - This I get the feeling I'm wrong in stating.

2. Besides having to reconfigure VirtualBox for kernel updates, are there any other pieces of software that you can think of where I'd have to reconfigure for kernel updates? I know VBox cause of it's DKMS that builds from the kernel.

3. Why is LMDE faster? Why is Debian faster than Ubuntu or Linux Mint? I mean there's nothing missing, at least that I've found, in fact I feel I have more. All my software works, great. I just don't understand if they're pretty much the same, but ones a freeze and ones a constant update, why one is faster. I would think the constantly updated one would be more apt to slow downs. What do they do different?

Is anyone else running LMDE (I've got mine on a 60GB partition sharing with Ubuntu)? If so how are you liking it? This is like the best thing I've done is try it out. It tells me I like constant updates more than install for a new version.

---

### Post by NightwishFan on 2011-06-22
> 1. My hardware works better under LMDE (specifically I don't have to patch my sound) because the kernel isn't modified, it's pretty much a direct compile from kernel.org with minor changes for it to work under Debian? - This I get the feeling I'm wrong in stating.
Debian patches the kernel - however it is configured as much as possible like the upstream source.
[http://wiki.debian.org/DebianKernel](http://wiki.debian.org/DebianKernel)

> 2. Besides having to reconfigure VirtualBox for kernel updates, are there any other pieces of software that you can think of where I'd have to reconfigure for kernel updates? I know VBox cause of it's DKMS that builds from the kernel.
Nvidia drivers and virtualbox are all I have ever used. That and the occasional newer version of alsa. (I backport myself)

> 3. Why is LMDE faster? Why is Debian faster than Ubuntu or Linux Mint? I mean there's nothing missing, at least that I've found, in fact I feel I have more. All my software works, great. I just don't understand if they're pretty much the same, but ones a freeze and ones a constant update, why one is faster. I would think the constantly updated one would be more apt to slow downs. What do they do different?
It is a minor note that Debian packages are configured without hardening for a small performance benefit. Say 1-3% on 32-bit and negligible at all on 64-bit. I think certain packages (like Midori/Mupen64) are hardened though. From my experience this "faster" people speak of is negligible and not always true. I tend to see it to mean 'responsive'. Perhaps the packages and kernel are just configured more conservatively and less experimentally. Also note that even packages in Debian Unstable have to be deemed release quality as once they hit there they are intended to eventually be actually used after enough testing of them is done.

> Is anyone else running LMDE (I've got mine on a 60GB partition sharing with Ubuntu)? If so how are you liking it? This is like the best thing I've done is try it out. It tells me I like constant updates more than install for a new version.
No, but I use standard Debian. Since they share repositories I highly doubt there is much difference. I might give LMDE a try just so I can see why people use it instead of just Debian. (nothing so far has convinced me to try it for real). I tried another 'fully compatible' Debian fork called Mepis and it really felt like 'just Debian'. That is a good thing though since they do not pointlessly change what already works.

Edit: Well Debian based systems are fantastic at doing upgrades (even while you are working). Upgrading Debian Stable or Ubuntu LTS every 2-3 years does not trouble me much. At least I know the same software will be available the whole support life. With a rolling type software might just vanish one day.

---

### Post by slooksterpsv on 2011-06-22
I like LMDE cause it's well... small. I don't like downloading HUGE DVD images or 6 CD images. Even with the netboot install I'd have to download and install every time. With LMDE it's preconfigured to a small low-endish DVD size. Other than that, it has the Software Manager (like Ubuntu software Center) which I do enjoy using over Synaptic.

---

### Post by NightwishFan on 2011-06-22
> **slooksterpsv said:**
> I like LMDE cause it's well... small. I don't like downloading HUGE DVD images or 6 CD images. Even with the netboot install I'd have to download and install every time. With LMDE it's preconfigured to a small low-endish DVD size. Other than that, it has the Software Manager (like Ubuntu software Center) which I do enjoy using over Synaptic.

Debian has a very very nice live dvd image for gnome. It is 1.1gb and has everything you can think of including most codecs. I also downloaded and burned the multi-arch dvd of Squeeze (you can buy it also (a debian developer burns and sells them for basically the cost of shipping, if your net is slow). It has most of Gnome, KDE, XFCE, LXDE, as well as some server packages for 32 and 64 bit + source code. It is lacking network-manager-gnome oddly enough. It has network-manager-kde and wicd though. But Debian doesn't need a network-manager to connect to a wired connection, so you aren't up a creek.

The many CDs of Debian are a convenience not a necessity. If you so wanted you could certainly download the whole repository but you only need CD1 to install a working system. They have CDs for KDE, XFCE, LXDE, and a standard server system as well. You only need the one to install and a net connection to get the (probably 100mb) rest.

Edit: I will try LMDE in a VM though. I am very curious how it works. I might even start recommending it here or there if it is nice.
Edit Edit: Debian has the software center by default in Squeeze.

---

### Post by slooksterpsv on 2011-06-22
> **NightwishFan said:**
> Debian has a very very nice live dvd image for gnome. It is 1.1gb and has everything you can think of including most codecs. I also downloaded and burned the multi-arch dvd of Squeeze (you can buy it also (a debian developer burns and sells them for basically the cost of shipping, if your net is slow). It has most of Gnome, KDE, XFCE, LXDE, as well as some server packages for 32 and 64 bit + source code. It is lacking network-manager-gnome oddly enough. It has network-manager-kde and wicd though. But Debian doesn't need a network-manager to connect to a wired connection, so you aren't up a creek.

The many CDs of Debian are a convenience not a necessity. If you so wanted you could certainly download the whole repository but you only need CD1 to install a working system. They have CDs for KDE, XFCE, LXDE, and a standard server system as well. You only need the one to install and a net connection to get the (probably 100mb) rest.

Edit: I will try LMDE in a VM though. I am very curious how it works. I might even start recommending it here or there if it is nice.
Edit Edit: Debian has the software center by default in Squeeze.

Wow I didn't know that about Debian, may start going squeezy now ;).
I'm loving it cause I love to be on the latest kernels, where possible. They had an update for 2.6.39-2 today, so I'm using that. Plus GIMP is updated, LibreOffice is only 3.3.3, no 3.4 yet though, which is weird to me. (Granted nothings ever going to be perfectly up to date).

All in all I'm very happy, it's quick, it works, its not tempting me to reformat to get the latest and greatest, it's actually making me want to stick with it.

I'll check out Debian a bit more then, I have a 1/2 MB/s connection but its still slow to me, when downloading large ISOs ;). I know people are still on dial-up and would kill to have a 5192Kb/s download. So yeah knowing the software center is in there =D.

---

### Post by NightwishFan on 2011-06-22
Yes, I do not dislike Ubuntu or anything but Debian 6 impressed me enough to switch. :) A lot of the negatives said of Debian are really either out of date or flat out wrong. (such as hard to use, out of date software etc) The only issues I have with Debian are that at times a user might just not know how to install or set it up. Someone pointed out to me that an average user would likely not set it up themselves any way. (And also the live cd is fully ready to go if you install using it so I can just point them there)

As LMDE is compatible with Debian most tutorials go for either.

---

### Post by BrokenKingpin on 2011-06-22
I ran LMDE for about a month on my desktop. I liked it because it was fast, and a rolling release.

Unfortunately I had a few issues with it. First, there is over a gig of updates to do after install. Normally I wouldn't care, but it asked me about 5 questions about updating configuration where I had no idea what it was talking about. They should update the ISOs.

After using it for about a month an update broke my ability to navigate to samba shares (Gnome would just lock up). I searched for an answer but could not find a solution.

One additional issue I see is where are they going with Gnome... to Gnome 3? Alliteratively, there is an XFCE version, but it is still on version 4.6, and seems to use the same amount of ram as the Gnome version, if not more. I would like to see it with Xfce 4.8, and not overly bloated.

It is an interesting project and will continue to follow it, but it is not for me at this point.

---

### Post by NightwishFan on 2011-06-22
Installing LMDE now. So far.. The fonts and icons look great. The installer was kind of annoying to select my time zone. It also takes very long to install.

---

### Post by Rubi1200 on 2011-06-22
These are my experiences with LMDE thus far:

1. very fast to install on my system; it only took 10 minutes

2. nice theme and icons, default applications etc.

3. reasonably configurable

4. I have had issues with updates. Nothing that could be considered a deal breaker but certainly somewhat more awkward than I would have liked 

In general, I would say that more work needs to be put into this distro but that it definitely has the potential to shine.

---

### Post by 4Orbs on 2011-06-22
> It tells me I like constant updates more than install for a new version.
Rolling release - I thought I would like it, but decided I don't like it. Too many updates every week for things that are already working well.

Mint tools - All the Mint goodies are nice, but they focus on activities that I've already learned to do in a different way, so they have little importance to me. But they are probably a good idea for newcomers.

Mint configuration - This is the best part of Mint from my perspective. All the restricted codecs and extras come pre-installed making this the most instantly full-featured distro available. It's something I appreciate even though not really necessary. Mint adds some nice little surprises in other places also... the red background in the file manager when using it as root is one example.

---

### Post by Roasted on 2011-06-22
> **BrokenKingpin said:**
> 

One additional issue I see is where are they going with Gnome... to Gnome 3? 

Wait, what? Linux Mint DE is going to Gnome 3? When is this

EDIT - Ahh, you were asking a question. I took "are they" for "they are". I also took Gnome 3 for assuming it's Gnome Shell...

I know Linux Mint is moving to Gnome 3, but they're not using Unity or Mint, they're using their own current interface, but it'll just be on Gnome 3 instead. I would assume Mint DE would follow suit. Being a Gnome Shell fan, I'm trying to figure out when that will take place so I can just apt-get gnome-shell and have my rig where I want it. I know 11.10 is getting Gnome 3, so I assume GS will just be an apt-get away there, but I was curious/hoping some other .deb distro would get it sooner, so I've had my eye on Mint DE...

---

### Post by slooksterpsv on 2011-06-22
Well it uses GDM3 for its DM; but most the apps look like Gtk2.

One main big issue that I always have to fix with Linux mint is the Google search CSE. I hate hate hate hate hate hate custom search experiences on Google. It's too limiting. I need regular Google (easy fix though).

Other than that I like the constant updates. I like having the latest and greatest. If it breaks, I know how to fix it =D

---

### Post by Roasted on 2011-06-22
> **slooksterpsv said:**
> Well it uses GDM3 for its DM; but most the apps look like Gtk2.

One main big issue that I always have to fix with Linux mint is the Google search CSE. I hate hate hate hate hate hate custom search experiences on Google. It's too limiting. I need regular Google (easy fix though).

Other than that I like the constant updates. I like having the latest and greatest. If it breaks, I know how to fix it =D

Stupid question. Does GDM3 = Gnome 3? Is that to say Mint DE is based on Gnome 3? I thought for sure it wasn't... now I'm just a smidgen confused...

---

### Post by NightwishFan on 2011-06-22
GDM 3 is the name of the debian package for the new 'list' gdm. It will use GTK3 in Wheezy eventually but for now it doesn't.

---

### Post by cbowman57 on 2011-08-03
You know you don't have to update Debian or LMDE. :)  When you get it the way you want it just freeze it there.

---

