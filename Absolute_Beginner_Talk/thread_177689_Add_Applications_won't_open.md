---
title: "Add Applications won't open"
date: 2006-05-16
forum: Absolute Beginner Talk
---

### Post by joshbax on 2006-05-16
Hey All, I am a linux n00b, and a ubuntu n00b, but enjoying it so far compared to other distro's.

Anyway, I have installed it all fine, and am now logged in. But I need to use a Belkin PCI wifi card to access the internet. How could I get ubuntu to recognise it exists/even getting it working? Basically, where can I find drivers?

And also a major problem; add applications and synaptic package manager won't open, which from what i have researched may be able to help me. I just click them and then nothing.

Any help much appreciated! Thanks,

Josh

---

### Post by brettr on 2006-05-16
I am not sure about your wireless, but you don't have to use the Synaptic GUI thing. you can open up a terminal and use

```
sudo apt-get install <PackageName
```

to install stuff. To search i think this might work

```
sudo apt-cache search <search parameters>
```

anyways just a quick thought.

---

### Post by Jagot on 2006-05-16
Take a look at Belkin's site for drivers.  You may need to install Ndiswrapper to install some Windows drivers.  Have a look at this site also to see if your specific card is mentioned:

[https://wiki.ubuntu.com/HardwareSupportComponentsWirelessNetworkCards](https://wiki.ubuntu.com/HardwareSupportComponentsWirelessNetworkCards)

---

### Post by joshbax on 2006-05-16
ok thanks pple.

don't you have to be connected to the internet for apt-get to work?

---

### Post by bluevoodoo1 on 2006-05-16
[QUOTE=joshbax]don't you have to be connected to the internet for apt-get to work?[/QUOTE]

Yes.

---

### Post by joshbax on 2006-05-16
yer. i cant get online. thats my problem. i can move it downstairs to be able to get a cat-5 connection. but can i not do it from my lappy up here with the pc next to me?

also, system>administration>networking doesn't open either. it goes thru the motions on loading, but then stops. and has a normal blank screen.

---

