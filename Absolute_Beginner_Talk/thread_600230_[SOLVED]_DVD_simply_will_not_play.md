---
title: "[SOLVED] DVD simply will not play"
date: 2007-11-02
forum: Absolute Beginner Talk
---

### Post by doctorbighands on 2007-11-02
I'm at a dead end here. Once again, I'm extremely frustrated with something that seems like it should be painfully simple.

I have enabled the Medibuntu repository.

I have the latest versions of libdvdcss2, all the gstreamer codecs, and the win32 codecs.

I have attempted to use Totem with both backends. Neither one will play movies.

I have attempted to use VLC. It flashes a "play" window for just a split second, then does nothing. It won't play.

What on earth am I missing here?

---

### Post by Supergoo on 2007-11-02
Can you tell us what hardware you are running also how much Ram is in the system, also does it give any error messages you can think of ?  Lets see if we can ot figure this thing out.




Supergoo :)

---

### Post by doctorbighands on 2007-11-02
Thank you.

I'm running a laptop with a Pentium M (Centrino) processor @2.1 GHz (about), 1.5GB RAM. Everything else is OEM, and I don't know specs on things like the video card.

I know that isn't much...

---

### Post by Maestro23 on 2007-11-02
> **doctorbighands said:**
> Thank you.

I'm running a laptop with a Pentium M (Centrino) processor @2.1 GHz (about), 1.5GB RAM. Everything else is OEM, and I don't know specs on things like the video card.

I know that isn't much...

And is this a burned DVD you made your self? Store-bought, etc...

---

### Post by shad0w_walker on 2007-11-02
Is it safe to assume these are official, encrypted dvds? If so have you tried running this command from a terminal?

```
sudo /usr/share/doc/libdvdread3/install-css.sh
```

It will hopefully setup the decoders properly for encrypted dvds and get you sorted out.

---

### Post by RomeReactor on 2007-11-02
Hi. Are you using desktop effects? Make sure you have either the **gstreamer0.10-fmpeg** or **libxine1-ffmpeg** package installed, depending on which backend Totem is currently using (though for DVD playback, you should probably use totem-xine.

To find out which video card you have, go to the "Graphics Card" tab in "System->Administration->Screens and Graphics".

---

### Post by Supergoo on 2007-11-02
doctorbighands, ok this a start I would use the command,shad0w_walker suggested, I do not know how confortable you are with the command line, just know its nothing to be scared of. Open you term window and the easy way to make sure you get the command right is to do a highlight of the command and copy it, then you should be able to paste it right into the term window, it will most likely ask for your password just enter it and see what happens. I am sure we can figure this out. You going to do great.:)

---

### Post by doctorbighands on 2007-11-02
> **shad0w_walker said:**
> Is it safe to assume these are official, encrypted dvds? If so have you tried running this command from a terminal?

```
sudo /usr/share/doc/libdvdread3/install-css.sh
```

It will hopefully setup the decoders properly for encrypted dvds and get you sorted out.

This is a Netflix DVD - just a plain, old encrypted thing.

I tried the command above. Now (when in Totem) it plays the audio, but the video shows up as this weird fuzzy bar. Imagine a 1-inch-wide by 4-inch-tall ultrasound image, and you'll see what I see.

I tried punching in
```
sudo apt-get install libxine1-ffmpeg
```
and the terminal says, "couldn't find package libxine1-ffmpeg".

Apparently I'm running an Intel 915 graphics card. The driver is set to "intel - experimental modesetting driver for l...".

Supergoo, you're a REALLY nice person. :)

EDIT: I tried to downgrade my desktop effects (I even thought to do it before you folks suggested it! I'm proud of myself for anticipating something correctly!) from the high setting to the medium one, and it didn't seem to do anything for me.

---

### Post by Maestro23 on 2007-11-02
> **doctorbighands said:**
> This is a Netflix DVD - just a plain, old encrypted thing.

I tried the command above. Now (when in Totem) it plays the audio, but the video shows up as this weird fuzzy bar. Imagine a 1-inch-wide by 4-inch-tall ultrasound image, and you'll see what I see.

I tried punching in
```
sudo apt-get install libxine1-ffmpeg
```
and the terminal says, "couldn't find package libxine1-ffmpeg".

Apparently I'm running an Intel 915 graphics card. The driver is set to "intel - experimental modesetting driver for l...".

Supergoo, you're a REALLY nice person. :)

EDIT: I tried to downgrade my desktop effects (I even thought to do it before you folks suggested it! I'm proud of myself for anticipating something correctly!) from the high setting to the medium one, and it didn't seem to do anything for me.

Try turning Desktop Effect completely off.

---

### Post by doctorbighands on 2007-11-02
> **Maestro23 said:**
> Try turning Desktop Effect completely off.

Tried, and it didn't help. :(

---

### Post by doctorbighands on 2007-11-02
UPDATE:

All of a sudden, VLC has decided it wants to play the movie for me. Totem's still useless, but VLC seems to work. I even moved my desktop effects settings around, and VLC works with any of them.

I don't get it

I'm happy to have this problem solved, but I don't get it!

Once again, thank you all SOOOO much for your kindness and assistance.

---

### Post by Supergoo on 2007-11-02
Hmmm, 
hey Doc when you open your package manageer and scroll all the way to the bottom, do you see something called Free and Non Free, the non free if you click it should show you have the codecs installed, you using the 32bit version of ubuntu or the 64 ? I know I am asking alot of questions here, just trying to get some ideas.. off all the fustrating things in ubuntu , I always find getting DVD to play the one I always have to work the hardest on, so I know it can be fustration, my desktop can tell you about all the head banging I have done LOL

---

### Post by Supergoo on 2007-11-02
Woot Congrads , Way to go... Nice work :popcorn:

---

