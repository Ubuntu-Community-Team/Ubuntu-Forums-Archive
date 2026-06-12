---
title: "flash player"
date: 2007-06-16
forum: Absolute Beginner Talk
---

### Post by gprok on 2007-06-16
I am following all the steps to install flash in ubuntu and nothing work, i am doing exactly what's in the instruction on the adobe site.....some help would greatly appreciate. TIA !!!

Gprok

---

### Post by starcraft.man on 2007-06-16
> **gprok said:**
> I am following all the steps to install flash in ubuntu and nothing work, i am doing exactly what's in the instruction on the adobe site.....some help would greatly appreciate. TIA !!!

Gprok

Open any terminal (Applications > Accessories > Terminal) and paste this in:

```
sudo aptitude install flashplugin-nonfree
```

Then restart firefox and it should be in. There isn't any need to use adobe's site... You can confirm its installed by putting "about:plugins" (damn thing, not a smiley its : and p) in the url of firefox.

Thats it.

---

### Post by gprok on 2007-06-16
thanks soooooooo much, works a charm, im new to linux ( not at computer though) and this linux community ir probably the best thing on this planet.....

since im here i got another question: i have ubuntu installed now in dual boot with XP....but i wanna try ubuntu studio, can i just install it over the existing linux installation so its gonna sqeeze it ??? or create another partition and have both ubt and ubuntu studio in there ??

Gprok

---

### Post by starcraft.man on 2007-06-16
> **gprok said:**
> thanks soooooooo much, works a charm, im new to linux ( not at computer though) and this linux community ir probably the best thing on this planet.....

since im here i got another question: i have ubuntu installed now in dual boot with XP....but i wanna try ubuntu studio, can i just install it over the existing linux installation so its gonna sqeeze it ??? or create another partition and have both ubt and ubuntu studio in there ??

Gprok

Ok since your just starting out, these resources will help learning:

[Ubuntuguide]("http://ubuntuguide.org/wiki/Ubuntu:Feisty") site and [psychocats]("http://www.psychocats.net/ubuntu/") for General basics. [LinuxCommand]("http://www.linuxcommand.org/") for learning the CLI/Terminal. [Ubuntu Wiki]("https://wiki.ubuntu.com/") for advanced and specific questions (also forums of course) [Linux app finder]("http://linuxappfinder.com/") for finding programs and applications that suit your needs.

As for ubuntu studio, yes, you can it directly over Feisty with no trouble. [Here.]("http://ubuntustudio.org/downloads")

Follow the instructions in the studio repo section (scroll down) and pick the packages you want (if you don't want the theme for instance and just the packages and kernel, only pick those...)

---

