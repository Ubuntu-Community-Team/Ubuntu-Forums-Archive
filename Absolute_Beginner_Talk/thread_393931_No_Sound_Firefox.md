---
title: "No Sound Firefox"
date: 2007-03-26
forum: Absolute Beginner Talk
---

### Post by mikaelsnavy on 2007-03-26
Hello,
I have no sound for flash stuff in firefox! I have the latest flash. I downloaded aoss and edited "/etc/firefox/firefoxrc". Sound works in all my other apps. Any ideas?
Thanks,
Mikael

---

### Post by caish5 on 2007-04-08
I have this problem too.

Does anyone have a solution yet?

---

### Post by r00tintheb0x on 2007-04-08
Flash like youtube video flash?

---

### Post by kvarley on 2007-04-08
1. Update your flash player (linux version is avaliable!) 
2. Check your sound card settings, 
3. It may be that your sound card needs the driver installing or is not compatible with        [INDENT]Ubuntu.[/INDENT]

Try those and then post another message if they don't work and I will have a deeper look into it for you.

-Vitium-

---

### Post by caish5 on 2007-04-08
I'm using feisty so i assume that i have the latest flash, i just downloaded it through firefox. 

The sound works fine and in 5.1 for all other apps. Of interest the master volume has no effect on my system, only front, centre, rear etc.

---

### Post by caish5 on 2007-04-08
OK I've narrowed it down a bit. The problem is with my .asoundrc file.

I usually use this...

```

 pcm.!default {
type route
slave.pcm surround51
slave.channels 6
ttable.0.0 1
ttable.1.1 1
ttable.0.2 1
ttable.1.2 -1
ttable.0.3 1
ttable.1.3 -1
ttable.0.4 0.5
ttable.1.4 0.5
ttable.0.5 0.5
ttable.1.5 0.5
} 

```

Which gives a rough approximation of surround sound from stereo sources. With this i get no firefox sound at all.

Now if im use this which i found in a firefox sound thread...

```

 pcm.!default {
type plug
slave.pcm "dmix"
} 

```

I get firefox sound and all is well but i lose my surround effect..

Do you have any idea how to combine the two into one uber asoundrc?

Thanks 
Andy

---

