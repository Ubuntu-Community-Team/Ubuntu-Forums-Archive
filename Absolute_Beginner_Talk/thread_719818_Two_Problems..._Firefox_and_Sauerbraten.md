---
title: "Two Problems... Firefox and Sauerbraten"
date: 2008-03-09
forum: Absolute Beginner Talk
---

### Post by DaMann on 2008-03-09
Hello, I have had Firefox crashing on me at random times, that's about all I know about that problem.

The other problem is Sauerbraten won't start right. When I type in the start command it opens up a screen I can see some stuff for a second then it closes. I checked the terminal after that and I see this.

```
Using home directory: /home/curtis/.sauerbraten
init: sdl
init: enet
init: video: mode
init: video: misc
init: gl
Renderer: GeForce 8800 GTS 512/PCI/SSE2 (NVIDIA Corporation)
Driver: 1.2 (2.1.2 NVIDIA 169.12)
WARNING: No vertex_buffer_object extension! (geometry heavy maps will be SLOW)
WARNING: No occlusion query support! (large maps may be SLOW)
Rendering using the OpenGL 1.5 assembly shader path.
WARNING: No texture rectangle support. (no full screen shaders)
init: console
init: gl: effects
init: world
init: sound
init: cfg
Could not set gamma (card/driver doesn't support it?)
sdl: Gamma correction not supported on this visual
init: localconnect
init: mainloop
read map packages/base/metl4.ogz (0.0 seconds)
Mining Station by metlslime
X Error of failed request:  BadLength (poly request too large or internal Xlib length error)
  Major opcode of failed request:  148 (GLX)
  Minor opcode of failed request:  2 (X_GLXRenderLarge)
  Serial number of failed request:  2343
  Current serial number in output stream:  2345

```

Any idea?

Thanks,
-DaMann

---

### Post by imanoob on 2008-03-09
Firefox could be crashing because of a heavy page loading, and I can't help you with your other problem sorry.

---

### Post by DaMann on 2008-03-09
> **imanoob said:**
> Firefox could be crashing because of a heavy page loading, and I can't help you with your other problem sorry.

Just wondering... are their any rules against bumps? If so tell me because I am doing one now.

---

### Post by hhhhhx on 2008-03-09
> **DaMann said:**
> Just wondering... are their any rules against bumps? If so tell me because I am doing one now.
one a day is polite :)

also you can try firefox 3 beta 3, it works alot better on my com

---

### Post by hhhhhx on 2008-03-09
also for saurtouban, 1:  is your grafics cards driver correctly installed?
                 2: are you running it with way too high settings or resoloution?

---

### Post by DaMann on 2008-03-09
> **xhhux said:**
> also for saurtouban, 1:  is your grafics cards driver correctly installed?
                 2: are you running it with way too high settings or resoloution?

Well I played Nexuiz a few minuts ago so I'm assuming the drivers are correctly installed. These would have to also be the default settings in the game because I haven't gotten to change the settings at all yet.

---

### Post by hhhhhx on 2008-03-09
hmmm.. are you using i386 or x86_64

---

### Post by DaMann on 2008-03-09
> **xhhux said:**
> hmmm.. are you using i386 or x86_64

Well I'm assuming that's processor right? If so I am using an Intel Conroe E6850.. I am not sure if that answers your question at all.

---

### Post by hhhhhx on 2008-03-09
> **DaMann said:**
> Well I'm assuming that's processor right? If so I am using an Intel Conroe E6850.. I am not sure if that answers your question at all.
not really, e6850 can be either, i have the same one :)

basically are u using 32bit or 64bit?

---

### Post by DaMann on 2008-03-09
> **xhhux said:**
> not really, e6850 can be either, i have the same one :)

basically are u using 32bit or 64bit?

Ohhh... I am using 62 bit =D

---

### Post by hhhhhx on 2008-03-09
> **DaMann said:**
> Ohhh... I am using 62 bit =D
well thats great, cuz now i might have a solution to your problem.

the game is for i386, but according to another thread you can make it work if you install the SDL libs from the i386 repository :)
EDIT: dont do that yet, i think theres something else...

EDIT 2: this should tell you what you need to do:  [http://gaming.gwos.org/doku.php/guides:64bit:sauerbraten](http://gaming.gwos.org/doku.php/guides:64bit:sauerbraten)

---

### Post by DaMann on 2008-03-09
> **xhhux said:**
> well thats great, cuz now i might have a solution to your problem.

the game is for i386, but according to another thread you can make it work if you install the SDL libs from the i386 repository :)
EDIT: dont do that yet, i think theres something else...

EDIT 2: this should tell you what you need to do:  [http://gaming.gwos.org/doku.php/guides:64bit:sauerbraten](http://gaming.gwos.org/doku.php/guides:64bit:sauerbraten)

Alright so uninstall it then do what that guide says?

---

### Post by hhhhhx on 2008-03-09
> **DaMann said:**
> Alright so uninstall it then do what that guide says?
looks like it :)

---

### Post by DaMann on 2008-03-09
> **xhhux said:**
> looks like it :)

Went through all of that and it didn't work... It still just goes to the starting screen then stops....  I have a feeling I did something wrong though....

---

### Post by DaMann on 2008-03-10
Daily bump =D!

Does anyone else have some new ideas?

---

