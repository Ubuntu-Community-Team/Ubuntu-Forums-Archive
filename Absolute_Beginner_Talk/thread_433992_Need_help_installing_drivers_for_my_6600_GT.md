---
title: "Need help installing drivers for my 6600 GT"
date: 2007-05-05
forum: Absolute Beginner Talk
---

### Post by christarp on 2007-05-05
Okay, I need a pretty thorough walkthrough as I don't know many terminal commands.

Alright, so I have ubuntu up and running, and I wanted to get the ubuntu drivers from nvidia right?

So I click graphics driver>geforce 6 series> linux x86.

It downloads, and then when I try to run it, it comes up with either:

"nvidia-installer must be run as root" (When I type "sh NVIDIA-Linux-x86-1.0-9755-pkg1.run"

"You appear to be running an x server; please exit X before installing." (When I type "sudo sh NVIDIA-Linux-x86-1.0-9755-pkg1.run")


What's going on?

---

### Post by Bachstelze on 2007-05-05
[https://wiki.ubuntu.com/BinaryDriverHowto/Nvidia](https://wiki.ubuntu.com/BinaryDriverHowto/Nvidia)

---

### Post by starcraft.man on 2007-05-05
Ugghhh, I assume you were trying to use Nvidia installer... This may be the only place i really recommend an automatic installer, causes less problems. Long as you didn't get past the beginning install its fine. Here is [envy,]("http://www.albertomilone.com/nvidia_scripts1.html") its a neat script that will handle everything :)

Download the 0.9.2 debian installer, then run it. Then go to Applications Menu > System Tools > Envy. A dialog pops up, and pick automatically install nvdia driver. Say yes to any terminal prompts or dialogues that pop up and before you know it you got drivers :)

---

### Post by christarp on 2007-05-05
> **HymnToLife said:**
> [https://wiki.ubuntu.com/BinaryDriverHowto/Nvidia](https://wiki.ubuntu.com/BinaryDriverHowto/Nvidia)

Okay, I'm tyring to allow access to the nvidia drivers, but where it says



In the Software Preferences dialog that comes up, click the Add button.


In the Edit Repository dialog, ensure that the Restricted copyright box is checked, then press OK.


Press OK to close the Software Preferences dialog, when Synaptic asks you to reload the package database, say yes.

There is no software preferences that comes up, it's software sources, and there's no add button.

---

### Post by christarp on 2007-05-05
> **starcraft.man said:**
> Ugghhh, I assume you were trying to use Nvidia installer... This may be the only place i really recommend an automatic installer, causes less problems. Long as you didn't get past the beginning install its fine. Here is [envy,]("http://www.albertomilone.com/nvidia_scripts1.html") its a neat script that will handle everything :)

Download the 0.9.2 debian installer, then run it. Then go to Applications Menu > System Tools > Envy. A dialog pops up, and pick automatically install nvdia driver. Say yes to any terminal prompts or dialogues that pop up and before you know it you got drivers :)

Thank you!

---

### Post by starcraft.man on 2007-05-05
> **christarp said:**
> Thank you!

Your welcome, driver is one thing thats a real pain, only place I find it beneficial to use an installer. Do read up on terminal and other things though, never good to rely too much on a gui :). Ubuntu guide in my sig has more info.

---

### Post by christarp on 2007-05-05
> **starcraft.man said:**
> Your welcome, driver is one thing thats a real pain, only place I find it beneficial to use an installer. Do read up on terminal and other things though, never good to rely too much on a gui :). Ubuntu guide in my sig has more info.

Wait, One problem, when I try to open it, I get an erro:

dependency is not satisfiable: module-assistant

---

### Post by starcraft.man on 2007-05-05
> **christarp said:**
> Wait, One problem, when I try to open it, I get an erro:

dependency is not satisfiable: module-assistant

Ah! I think you need the build package, I assume you probably didn't install it after upgrading... at least I think its in there.

Open the terminal again and type this in:

```
sudo aptitude install build-essential
```

Then run the deb again, should be fixed.

If not, then run this command in terminal:

```
sudo aptitude install module-assistant
```

That should be it, good luck :)

---

