---
title: "Ati accelerated restricted driver ATI radeon 9550"
date: 2008-01-21
forum: Absolute Beginner Talk
---

### Post by strang3r on 2008-01-21
Hi everyone,
i am still new to linux (but i am loving it so far) and am having a problem with my ATI radeon 9550 256 mb graphics card. I am currently running ubuntu 7.10 on my computer and am trying to enable compiz fusion. it registers my card but it shows in restricted drivers ATI accelerated graphics driver when i try to enable it, it says xorg-driver-fglrx is not enabled. ive tried fixing broken packages in synaptic  package manager only to find nothing is supposedly broken. on top of that i cant find compizconfig thing in synaptic package manager (am i supposed to be connected to internet to get it?). so seriously folks any help would be hot.

---

### Post by ikex on 2008-01-21
lol same card as me, after all the trouble  i went to to get compiz working flawlessly im making sure my next card is an NVIDIA.

first double check its not loaded
```

lsmod | grep fglrx

```

then check dmesg to why it isnt loaded
```

dmesg | grep fglrx

```

paste results?

---

### Post by strang3r on 2008-01-21
im sorry do i do that in the terminal?

---

### Post by strang3r on 2008-01-21
please keep in mind im really new to this you will have to walk me through this

---

### Post by ikex on 2008-01-21
yeah in terminal ^^,
and copy and paste the replies here

---

### Post by strang3r on 2008-01-21
its not giving me anything. am i supposed to be connected online? (im using my macbook cause my pc does not having internet on it) but anyways nothing in the terminal happened.

---

### Post by strang3r on 2008-01-21
perhaps this would go faster if someone could I-M me. pm me if you can.

---

### Post by strang3r on 2008-01-21
please any help would be great

---

### Post by strang3r on 2008-01-21
help! PLEASE HELP

---

### Post by strang3r on 2008-01-21
i need real help look ive tried everything i could

---

### Post by ikex on 2008-01-21
> **strang3r said:**
> help! PLEASE HELP

open up a terminal,
type 
```

sudo bash
[enter your password]
lsmod | grep ati
lsmod | grep radeon
lsmod | grep fglrx
dmesg | grep fglrx

```

i guess?

---

### Post by strang3r on 2008-01-21
lsmod | grep ati
cpufreq_conservative    8072  0
lsmod | grep radeon
radeon                           125472  2
drm                                  83348  3 radeon
lsmod | grep fglrx (nothing happens)
dmesg | grep fglrx (nothing happens)

i typed this in manually so spacing can be off at times

---

### Post by ikex on 2008-01-21
try sudo apt-get install xorg-driver-fglrx

---

### Post by strang3r on 2008-01-21
you mentioned that an nvidia card would be your next buy i have a nvidia geforce fx 5200 lying around. would i be better off if i just put that in instead.

---

### Post by RebounD11 on 2008-01-21
no, if you get your current card working at its full capacity it totally surpasses the FX5200.

---

### Post by strang3r on 2008-01-21
Reading package lists... done
building dependency tree
reading state information... done
E: Couldn't find package xorg-driver-fglrx

---

### Post by strang3r on 2008-01-21
now what any ideas?

---

### Post by kelvin spratt on 2008-01-21
The easiest way is to download Envy [http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)
  It will download the latest ATI drivers from their site and install them with a couple of clicks. that will give the ATI Catilist drivers alla windows. But the linux versions and then you can use compiz. you might need to enable the Compiz manager etc in Synaptic or the terminal. The drivers work OK.

---

### Post by strang3r on 2008-01-21
problem my compy's not on internet my macbook is. is there any way i can get what i need on my macbook and simply transfer it to my ubuntu desktop? if not perhaps you guys can recommend a better more compatable videocard?

---

### Post by strang3r on 2008-01-21
i downloaded it on my macbook anyways in case i can transfer it

---

### Post by strang3r on 2008-01-21
any1 there

---

### Post by oodledoodle on 2008-01-21
is there any way of getting your pc online? reason i say is that ubuntu doesn't come with the ati drivers pre-loaded because of licensing issues, so the best way to install them (as a newbie to ubuntu) is to be online really and go from there.

---

### Post by strang3r on 2008-01-21
well that all depends if it can read my linksys wireless internet usb adapter. can it?

---

### Post by oodledoodle on 2008-01-21
the best way to find out is to try! i've heard some linksys work out of the box and some don't. 

as for the ati card, follow **method two** from this guide [http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide)
 report back any problems you have and i'll try and help :)

---

### Post by strang3r on 2008-01-22
thanks guys but for the time being my wireless adapter usb is MIA. till then apparently im SOL so until then i'll try other methods.

---

### Post by strang3r on 2008-01-25
> **oodledoodle said:**
> the best way to find out is to try! i've heard some linksys work out of the box and some don't. 

as for the ati card, follow **method two** from this guide [http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide)
 report back any problems you have and i'll try and help :)

it mentions of a download directory. where is that?

---

