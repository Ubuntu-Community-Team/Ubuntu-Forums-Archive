---
title: "hp dv6000z AMD, Cant Install"
date: 2007-05-01
forum: Absolute Beginner Talk
---

### Post by em11488 on 2007-05-01
I cant get any version of ubuntu working on this hunk of junk. I paid 1500 for a laptop that crashes 2x a day bc vista. For months now I've been thinking about trying Ubuntu. Only problem is that I cant the damn thing to boot up. I thought this was the most flexible distro. I cant get Ubuntu, 6.06, 6.10, or 7.04 in both 32 bit, 64 bit, and alternative versions. and Kubuntu 6.06 32 bit to boot from the liveCD. Maybe one out of 25 tries will allow me to fool around with it, but when I try to install it, it freezes. Does ubuntu hate Hp laptops with AMD cores? I want to get rid of Windows Vista. i cant go back to xp bc it deletes my cd key for xp when I upgrade to vista, I dont feel like buying a mac, and now I cant even get this OS that everyone preaches as incredibly awesome to work. 
HP DV6000z
AMD Turion 64 X2 @2.0 ghz
2 gb ram 
nvidia 7200 256 mb
120 gb hd
broadcom wireless g

any other info needed could gladly be given

hell right now my screen just went black for a minute,

Everytime start the liveCD it freezes halfway through the process of checking all  my hardware. Ive done the slow burn, ive burned the cds from 2 different computers, followed ubuntu's website directions, and ive changed the video driver **** to "vesa" instead of nv. Any help would be awesome.
I hate vista and hopefully this would free me from the grasp of M$.

---

### Post by starcraft.man on 2007-05-02
Wow, that sounds really bad... sorry for having so many problems. Just a side note, but I "think" you can downgrade your copy of Vista if you phone up microsoft and talk to the right person. I heard of two people, friend of a friends that have done so.

I can't say I've ever heard of a computer crashing with all those different versions. Can I just ask one question, do you know if your bios is Phoenix? I heard bad things about what they did, microsoft paid them to make their bios "optimized" for Vista... I hope ya don't have a comp with that...

If thats not it, do you have any more specific info on the crash? Any text pop up?

---

### Post by em11488 on 2007-05-02
next time it crashes ill write down what it says
how do I check if my bios is made by them.
I bought my laptop before vista came out, it had xp pre-installed, but I bought it during the time where a free upgrade to vista was available.
I should have just got a *snip* dell, or besides that, an intel chipset. I built my desktop with an amd core, never had one problem with it. even though intels chip was better, I stuck with my gut, and now im *snip* over. 
do you know if theres another distro that is better at adapting to my *snip* computer?

---

### Post by starcraft.man on 2007-05-02
> **em11488 said:**
> next time it crashes ill write down what it says
how do I check if my bios is made by them.
I bought my laptop before vista came out, it had xp pre-installed, but I bought it during the time where a free upgrade to vista was available.
I should have just got a *snip* dell, or besides that, an intel chipset. I built my desktop with an amd core, never had one problem with it. even though intels chip was better, I stuck with my gut, and now im *snip* over. 
do you know if theres another distro that is better at adapting to my *snip* computer?

Hey LANGUAGE! These are G forums (well, family at least, no language), calm down, I'm gonna guess since you had XP on it it wasn't a Phoenix Bios PC.

We do need to know more to help you out though, from your specs I don't see any problem. I hope someone else has an idea...

---

### Post by trjnhrse44 on 2007-05-02
using fiesty you can work around the faulty bios problem (hp bent over for microsoft) by adding the noapic command to your grub boot string.  When you insert the install cd in to your laptop and reboot, I believe the option is F6 for alternate commands.  Just add the word noapic to the end of that string.  Your dv6000 has the same bios as my dv9000 and hp has admitted that it just does not work properly, and they will not fix it.  Nice, huh?  Well I for one will buy a dell next time, Ubuntu preinstalled.

---

### Post by oilchangeguy on 2007-05-02
uh, do you still have the original restore disc(s)? or the hard drive partition with the original xp setup? if so just reload it to the way it was.

---

### Post by uzerzero on 2007-09-17
em11488: I have Ubuntu Feisty Fawn 7.04 working perfectly on my HP dv6000z. I have the exact same specs as you do except that I don't have the Nvidia 7200 video card. 

When booting off a LiveCD (32 bit is more stable than 64 bit), hit F6 then remove the dashes at the end and add the following:```
live acpi=off noapic pnp-bios=off
```
The system should boot then and allow you to install Ubuntu. After installing, you will have to edit the grub bootline to add the same options, with the exception of the live command. Once you are actually in Ubuntu, you will have to edit /boot/grub/menu.lst and add the same commands there to keep them in their permanently. Other than that, everything should work fine.

I know HP and Ubuntu don't get along, but if you give them a toy they tend to play along well ;) just keep tossing toy after toy at them until they find what they like.

---

