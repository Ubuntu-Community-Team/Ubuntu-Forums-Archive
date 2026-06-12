---
title: "KDE killed my sound"
date: 2004-11-28
forum: Apple PPC Users
---

### Post by mach_zero on 2004-11-28
I successfully got KDE 3.3 up and running on my iBook G4. Everything is peachy with the exception of audio. When I was just running the default Gnome, system sounds, CD audio, MP3, everything worked. But since the KDE install I get nothing, not even under Gnome - it's completely dead. I've tried using autodetect, ALSA, OSS with no luck. Anyone else run into a similar situation? Thanks in advance for your help.

---

### Post by M-Rick on 2004-11-30
How did you get KDE running ? Synaptic always refuses to download it for me ...

---

### Post by Felix_the_Mac on 2004-11-30
[QUOTE=mach_zero]I successfully got KDE 3.3 up and running on my iBook G4. Everything is peachy with the exception of audio. When I was just running the default Gnome, system sounds, CD audio, MP3, everything worked. But since the KDE install I get nothing, not even under Gnome - it's completely dead. I've tried using autodetect, ALSA, OSS with no luck. Anyone else run into a similar situation? Thanks in advance for your help.[/QUOTE]
 
I installed YDL 4.0 with KDE and the sounds didnt work. YDL support gave me the folowing explanation (excerpt):
> 
There are two bugs with respect too sound... first KDE has an endian bug
in it's soundsystem, that we never caught until 2 weeks ago. Secondly,
OSS and ALSA have varying degrees of support. I've managed to get ALSA
working and will be writing a howto on how to update your configuration
to ALSA instead of OSS (because Alsa produced static on many systems but
that has now been resolved).

---

### Post by adamward on 2004-11-30
[QUOTE=M-Rick]How did you get KDE running ? Synaptic always refuses to download it for me ...[/QUOTE]

You have to add the universal repositories, and possibly the unstable ones as well.  From there, use apt-get install kdebase

That worked great for me and I have KDE with sound on my iBook currently.

--adam

---

### Post by M-Rick on 2004-11-30
[QUOTE=adamward]You have to add the universal repositories, and possibly the unstable ones as well.  From there, use apt-get install kdebase

That worked great for me and I have KDE with sound on my iBook currently.

--adam[/QUOTE]
I get this error message :

```
 # sudo apt-get install kdebase
E: Impossible de verrouiller /var/lib/dpkg/lock - open (11 Ressource temporairem ent non disponible)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another proc ess using it?
```

---

### Post by M-Rick on 2004-11-30
ha no it's ok, Sypnaptic was launched and I forgot ...

sorry.

---

### Post by robert on 2004-12-05
Just installed KDE via Synaptic. Now instead of the African sounding music at start up and shut down and drum beats starting applicaations and so on, I just get a horrid scratchy sound (like I did with most KDE apps on Fedora Core 2). If it wasn't for the size of the download, I'd chuck the KDE back off again.

---

### Post by jonny on 2004-12-21
Me too.  I installed KDE 3.2 from the Universe using Synaptic... and my sound died.  At full volume I get some crackly static noises, but nothing usable.

I tried some of the hints suggested elsewhere in these forums (search for KDE and sound and you'll find lots of people have the same problem) but no luck.  Tried removing KDE... and it killed the graphical login for the only administrator account on the system.

Decided to reintstall ubuntu from scratch.  Life's too short to play with configuration files for ever.

I guess I can't complain, as the Universe is clearly labelled as unsupported.  But you have been warned: KDE might murder your system.

---

### Post by Quest-Master on 2004-12-21
My speakers blew out a screaming sound so loud when I first started up KDE, ack. Scared everyone in the house.

I only did it to show my friend too. Guess what? I had to reinstall.

---

