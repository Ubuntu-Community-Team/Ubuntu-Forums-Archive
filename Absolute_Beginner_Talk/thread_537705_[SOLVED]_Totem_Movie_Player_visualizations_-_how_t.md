---
title: "[SOLVED] Totem Movie Player visualizations - how to change?"
date: 2007-08-29
forum: Absolute Beginner Talk
---

### Post by qprfact on 2007-08-29
I'd liked Totem to display the cover art relating to the music track I'm playing.

Although there is a dropdown box for visualizations it doesn't have any other options and I can't see how to add any - is this possible and if so, how?!

Thanks!

---

### Post by julian67 on 2007-08-29
> **qprfact said:**
> I'd liked Totem to display the cover art relating to the music track I'm playing.

Although there is a dropdown box for visualizations it doesn't have any other options and I can't see how to add any - is this possible and if so, how?!

Thanks!

I assume you're using Gnome

You need to install the libvisual plugins. 

```
sudo apt-get install libvisual-0.4-plugins 
```

Close any gstreamer based apps (Totem, SoundJuicer, Rhythmbox etc) and delete the file /home/yourusername/.gstreamer-0.10/registry.i486.xml

Now start Totem or Rhythmbox and you'll see a few different options for visualizations. Rhythmbox can display cover art but Totem can't. Audacious is another nice audio player that will display cover art.

---

### Post by qprfact on 2007-08-29
Yep, that worked fine thanks! Shame Totem doesn't display the art, but some nice new themes there!

---

### Post by julian67 on 2007-08-29
> **qprfact said:**
> Yep, that worked fine thanks! Shame Totem doesn't display the art, but some nice new themes there!

Totem is fine as a player but you  might want to try Rhythmbox which supports the same visualisations,  will manage all your audio as a library, download and play podcasts, other features too. It works best if your audio files are properly named and tagged.

---

