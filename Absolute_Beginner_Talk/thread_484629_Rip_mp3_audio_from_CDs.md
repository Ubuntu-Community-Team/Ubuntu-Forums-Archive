---
title: "Rip mp3 audio from CDs"
date: 2007-06-26
forum: Absolute Beginner Talk
---

### Post by FleetAdmiral74 on 2007-06-26
Simply...how? Normal store-bought cds mind you

---

### Post by krul on 2007-06-26
with sound juicer!

---

### Post by Inxsible on 2007-06-26
Install K3B. ```
sudo aptitude install k3b
```

Start up K3B. Navigate to Tools --> Rip Audio CD

---

### Post by FleetAdmiral74 on 2007-06-26
> **krul said:**
> with sound juicer!

I see no mp3 option...

as soon as I start ripping in k3b I get some error...

---

### Post by Inxsible on 2007-06-26
> **FleetAdmiral74 said:**
> I see no mp3 option...

In sound-juicer. Edit -->Preferences. At the bottom Output Format -- Select CD Quality MP3 (MP3 Audio)

---

### Post by forestpixie on 2007-06-26
> **FleetAdmiral74 said:**
> 
as soon as I start ripping in k3b I get some error...

you might need libk3b2-mp3 then

```
sudo apt-get install  libk3b2-mp3
```

---

### Post by FleetAdmiral74 on 2007-06-26
That lib mp3 thing is already installed.

And in Sound Juicer, mp3 is not an output option. if I go into profiles, then it is there, but if I do something like click edit on it, then I cannot close the window. Idk why the mp3 option is in the profile list, but not the output list...

---

### Post by MetalMusicAddict on 2007-06-26
See my sig for a Grip HOWTO.

---

### Post by FleetAdmiral74 on 2007-06-26
Will do.

---

### Post by odiseo77 on 2007-06-26
I do it from sound juicer and it works pretty good (it even writes metada into the tracks like tittle, artist, track number, etc). All you need is the ***gstreamer0.10-plugins-ugly***, ***gstreamer0.10-plugins-ugly-multiverse***, ***gstreamer0.8-lame*** and ***gstreamer0.8-mad*** packages installed. After you've installed these packages, restart sound juicer, go to preferences, et, voilà :)

Greetings.

---

### Post by FleetAdmiral74 on 2007-06-26
Yup, I was just looking around in Synaptic and installed a few Gstreamer things I thought might be usefull. MP3 shows up fine now, yay!

---

### Post by ricardisimo on 2007-06-26
There's a bit of a glitch in Sound Juicer, but it's no big... When you go to Edit >> Preferences >> Edit Profiles, and then select, for example, "CD Quality MP3", you'll be looking at the new dialog that pops up, but the active one is actually the previous one. You have to close that previous dialog, titled "Edit GNOME Audio Profiles" on your bottom panel. Once it's closed you can edit the MP3 dialog items.

---

### Post by Unicast on 2007-07-07
> **odiseo77 said:**
> I do it from sound juicer and it works pretty good (it even writes metada into the tracks like tittle, artist, track number, etc). All you need is the ***gstreamer0.10-plugins-ugly***, ***gstreamer0.10-plugins-ugly-multiverse***, ***gstreamer0.8-lame*** and ***gstreamer0.8-mad*** packages installed. After you've installed these packages, restart sound juicer, go to preferences, et, voilà :)

Greetings.

Just wanted to say thank you for this advice. Came across this post after having problems with Juicer. ;)

And also thanks to ricardisimo for his tip with the glitch in Juicer. ;)

---

### Post by odiseo77 on 2007-07-07
> **Unicast said:**
> Just wanted to say thank you for this advice. Came across this post after having problems with Juicer. ;)

And also thanks to ricardisimo for his tip with the glitch in Juicer. ;)

yw! Glad to help! ;)

---

