---
title: "SMC Fan Speed Setting"
date: 2007-04-05
forum: Apple Intel Users
---

### Post by melvis02 on 2007-04-05
Hey everyone,

I'm running feisty on my MBP with the applesmc modules loaded.  When I boot up, most times my minimum fan speeds are set properly.  However, when I suspend, the minimum speeds are reset to 1000, making my MBP go nuclear.  

I cobbled together a quick script which updates the minimum speed for the fans using zenity and gksudo.  Hopefully this will help somebody, but I'm really hoping that somebody will take a look at it and improve it, because I don't really know what I'm doing with scripts.

Just chmod +x and run, as long as you have the applesmc module loaded it *should* work.

--Trey

---

### Post by Tribe on 2007-04-05
Hi there,

Just wanted to ask round what are the minium safe maximum_speed of the fans, i got them now at 6000 and when CPUs go to max the sound is quite irritating. If i set it to 4000 can they burn or something?

Thx.

---

### Post by melvis02 on 2007-04-05
I'm not sure what a safe minimum maximum is, I've never fiddled with it, but then again I don't think my fans have ever spun up anywhere near 6000 even at maximum load.  Maybe I've messed something up with mine or my MBP revision is screwed (first batch), because my fans basically stay right at the minimum speed I set all the time.

---

### Post by voided3 on 2007-04-06
Hello, I have a 2.16ghz core duo MBP and I use the SMC fan control under OS X. I have found that a good minimum setting is 2000 (lowers the idle temp 5-10 degrees) and a good setting while under load is about 4000 (usually keeps it at or under 65 C), but if you are maxing out the CPU (like when converting audio with iTunes) I would say setting it at 5000 will keep it from "going nuclear." I run Ubuntu in VMWare Fusion on this machine too and since it has uses about 10% cpu at idle at all times when running (it's a beta version, so it has debugging permanently enabled), I set the fans at 3000 to equal out that. I don't reccommend setting them at the full 6000 because when you set the minimum at 5000, it increases the fan speed about another 350rpm because of the heat when at load (i.e. above 65 C) and I feel that setting the minimum at the fans' maximum speed might be an unnecessary strain; if i recall, the difference between 5000 and 6000rpm when under the same load was only about a 2 degree difference, if that. I also use a Targus chill mat with mine and that helps out the temps quite a bit when under load (plus it has a powered usb hub which is great since the MBP has only two usb connectors!). Good luck!

---

### Post by Tribe on 2007-04-07
Very useful post, thx.

One question: anyone knows if applesmc kernel module has got any place (config file?) where to set the different temperature ranges?

Echo'ing to /sys/devices/platform/applesmc/fan0_minimum_speed looks inneficient.

Bye.

---

