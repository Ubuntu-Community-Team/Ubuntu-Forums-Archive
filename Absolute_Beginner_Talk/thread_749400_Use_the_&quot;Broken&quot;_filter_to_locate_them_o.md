---
title: "Use the &quot;Broken&quot; filter to locate them ok where do i find this?"
date: 2008-04-08
forum: Absolute Beginner Talk
---

### Post by wawadave on 2008-04-08
You have 2 broken packages on your system!

Use the "Broken" filter to locate them.

Where do i find this broken filter?
once found any thing special i should know on its use?
thx!!

---

### Post by dje on 2008-04-08
Hi wawadave,

I just had this problem, doing this fixed it:
1. Download [http://archive.ubuntu.com/ubuntu/pool/main/l/launchpad-integration/liblaunchpad-integration1_0.1.18_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/l/launchpad-integration/liblaunchpad-integration1_0.1.18_i386.deb)
2. Open up a terminal and copy/paste the following:
3. ```
cd /path/to/deb
```
Where /path/to/deb is the path to where you downloaded the deb file
4. ```
 sudo dpkg --force-overwrite -i liblaunchpad-integration1_0.1.18_i386.deb
```
5. ```
sudo apt-get -f install
```
6. ```
sudo apt-get update
```
And you should be good to go

source:
[https://bugs.launchpad.net/ubuntu/+s...on/+bug/213863](https://bugs.launchpad.net/ubuntu/+s...on/+bug/213863)

This is what you get if you use hardy heron before release, if you are a new user?? i would suggest against it

hope that helps
dje

---

### Post by mikeyphi on 2008-04-08
> **wawadave said:**
> You have 2 broken packages on your system!

Use the "Broken" filter to locate them.

Where do i find this broken filter?
once found any thing special i should know on its use?
thx!!

Synaptic - Custom filter - Broken

---

### Post by sisco311 on 2008-04-08
In Synaptic Package Manager click the Custom Filters button (bottom left of the window) and select the Broken option from the list (left side of the window)

---

### Post by dje on 2008-04-08
@ last two replies

This is a hardy specific problem, I tried what you described but it doesn't work. You have to go through what I described in the first reply ;)

dje

---

### Post by wawadave on 2008-04-08
OK thank you for this grate info!
I will start on this as soon as current updating finishes!
Had found my way to synaptic and had clicked on filters but it had not yet opened any thing when i tried manually searching. Was close but not quite there!

---

### Post by qamelian on 2008-04-08
> **dje said:**
> @ last two replies

This is a hardy specific problem, I tried what you described but it doesn't work. You have to go through what I described in the first reply ;)

dje
It depends on what caused the broken packages. I've used the broken filter in Synaptic to fix broken packages in Hardy a couple of times already without any problem at all.

---

### Post by dje on 2008-04-08
@qamelian

Yes but i assume he is talking about the packages which broke today (something to do with launchapad integration), i tried to fix with the broken filters but it doesn't work (these specific broken packages). You need to follow my instructions outlined in the first reply

dje

---

### Post by forrestcupp on 2008-04-08
Also, until the April 24th release, you are supposed to post Hardy specific problems in the [Hardy Heron Development Forum](http://ubuntuforums.org/forumdisplay.php?f=305).

---

### Post by qamelian on 2008-04-08
> **dje said:**
> @qamelian

Yes but i assume he is talking about the packages which broke today (something to do with launchapad integration), i tried to fix with the broken filters but it doesn't work (these specific broken packages). You need to follow my instructions outlined in the first reply

dje
Ah, fair enough. Since no specifics were given I assumed we were talking normal circumstances.

---

### Post by wawadave on 2008-04-08
"This is what you get if you use hardy heron before release, if you are a new user?? i would suggest against it"

Yes i could have just stayed with current stable release.
With every thing functioning smoothly.  But what would i learn or then need to learn.

This release is teaching me much and more quickly then i would have!!

dje your links do not work.

---

### Post by wawadave on 2008-04-08
seems last update cured the problem. as synaptic shows no broken now.

---

### Post by bratliff on 2008-04-10
Thanks, but tried that. I eliminated the broken files, but it the package manager tell me there is broken files still, but does not show any with the broken filter.
Bratliff
The broken filter is inder package manager/settings/filter.


> **wawadave said:**
> You have 2 broken packages on your system!

Use the "Broken" filter to locate them.

Where do i find this broken filter?
once found any thing special i should know on its use?
thx!!

---

