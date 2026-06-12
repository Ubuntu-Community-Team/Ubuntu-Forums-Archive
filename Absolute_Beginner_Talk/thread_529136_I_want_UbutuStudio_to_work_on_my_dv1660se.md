---
title: "I want UbutuStudio to work on my dv1660se"
date: 2007-08-18
forum: Absolute Beginner Talk
---

### Post by cyphgas on 2007-08-18
does anyone have settings for a dv1000 or dv1660se to be exact. I really want to migrate to a less power hungry audio suite. But i have seen no such tread and i have not found a thread that helps me with the loading of my graphic card. Its built in and its intel and its highly improbable that i will get a gui up so i can see what the hell im doing. thanks for some help in advance.

---

### Post by verbalshadow on 2007-08-19
In my experince Intel has good graphic driver support . This is most likely work without a hitch.

If you list the specfic graphics chips we will know for sure.
Run the command below and post the output.
It list all the PCI devices and the filters out all the non-intel stuff

```
lspci | grep intel
``` 

Let me know.

---

### Post by cyphgas on 2007-08-19
nothing happens when i use this command.

but after looking at the long list i believe it is this:

00:2.0 VGA compatible controller: intel corporation mobile 945gm/gms/940gml express integrated graphics controller (rev 3)

---

### Post by verbalshadow on 2007-08-19
oops that should have been 
```
lspci | grep Intel
```

But either way i have the same graphics card as the one you listed and it works great. Please try installing if you have not already. The only thing that i need to do was install 915resolution from the package manager to enable the wide screen support.

we'll be here if you run into issues.

---

### Post by cyphgas on 2007-08-19
sweet, i got it running. now about that i915 widescreen, how does that work?

---

### Post by verbalshadow on 2007-08-19
this we install the program.

```
sudo apt-get install 915resolution
```

After it's installed the easiest way to get it to work is to restart the machine, there is a way to start it without rebooting but i don't remember the command.

what it does it adds some values in the bios cause the graphics card doesn't put them there.

---

### Post by cyphgas on 2007-08-21
hell yes, ubuntu in its fine glory! oh yeah, do you know how to configure the audio drives. that alsa driver is crap. i have the built in conexant high definition driver that seems to have been recognized, but the audio just seems shot. is their an up to date driver.
thanks homie.

---

