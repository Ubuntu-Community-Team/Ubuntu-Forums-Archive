---
title: "dmesg | tail gives the following errors, why? ATI driver, from ATI"
date: 2006-10-02
forum: Absolute Beginner Talk
---

### Post by stoer on 2006-10-02
Hi all,
in another thread i posted the result of dmesg | tail 

See the following code output.


```
[17182442.856000] [fglrx:firegl_rmmap] *ERROR* map 0xf6c9b650 still in use (map_count=1)
[17182442.856000] [fglrx:firegl_free_buffer_queue] *ERROR* buffer qeue 0xf6c9b640 still mapped
[17182442.856000] [fglrx:firegl_rmmap] *ERROR* map 0xf6c9b650 still in use (map_count=1)
[17182442.856000] [fglrx:firegl_free_buffer_queue] *ERROR* buffer qeue 0xf6c9b640 still mapped
[17182442.856000] [fglrx:firegl_rmmap] *ERROR* map 0xdfb91b50 still in use (map_count=1)
[17182442.856000] [fglrx:firegl_free_buffer_queue] *ERROR* buffer qeue 0xdfb91b40 still mapped
[17182442.856000] [fglrx:firegl_rmmap] *ERROR* map 0xdfb91b50 still in use (map_count=1)
[17182442.856000] [fglrx:firegl_free_buffer_queue] *ERROR* buffer qeue 0xdfb91b40 still mapped
[17182442.856000] [fglrx:firegl_rmmap] *ERROR* map 0xf6c9b650 still in use (map_count=1)
[17182442.856000] [fglrx:firegl_free_buffer_queue] *ERROR* buffer qeue 0xf6c9b640 still mapped
steve@laptop:~$ dmesg | tail
[17182442.856000] [fglrx:firegl_rmmap] *ERROR* map 0xf6c9b650 still in use (map_count=1)
[17182442.856000] [fglrx:firegl_free_buffer_queue] *ERROR* buffer qeue 0xf6c9b640 still mapped
[17182442.856000] [fglrx:firegl_rmmap] *ERROR* map 0xf6c9b650 still in use (map_count=1)
[17182442.856000] [fglrx:firegl_free_buffer_queue] *ERROR* buffer qeue 0xf6c9b640 still mapped
[17182442.856000] [fglrx:firegl_rmmap] *ERROR* map 0xdfb91b50 still in use (map_count=1)
[17182442.856000] [fglrx:firegl_free_buffer_queue] *ERROR* buffer qeue 0xdfb91b40 still mapped
[17182442.856000] [fglrx:firegl_rmmap] *ERROR* map 0xdfb91b50 still in use (map_count=1)
[17182442.856000] [fglrx:firegl_free_buffer_queue] *ERROR* buffer qeue 0xdfb91b40 still mapped
[17182442.856000] [fglrx:firegl_rmmap] *ERROR* map 0xf6c9b650 still in use (map_count=1)
[17182442.856000] [fglrx:firegl_free_buffer_queue] *ERROR* buffer qeue 0xf6c9b640 still mapped
```

fglrxinfo
display: :0.0 screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: MOBILITY RADEON 9700 Generic
OpenGL version string: 2.0.5946 (8.27.10)

 glxinfo | grep

(this used to give me a 3d rendering yes or no - now all i get is an error message refering me on to 'Grep --help'.


Only issue i've noticed is Firefox tends to freeze up an aweful lot since the last update, usually on "flash" related sites and sometimes it just "ups and closes", on an apparently "flash free" site.

Seeing as my graphics seem otherwise to be working fine ( i do stress "seem to be"), i'm a total novice here, i'm unsure about what i need to do, if anything.
Any wise words would be greatly appreciated.
Cheers in advance.

---

### Post by llamakc on 2006-10-02
You have to grep for something.

 glxinfo | grep "render"

Or something to that effect.

I'm not using the fglrx driver right now so I'm not sure. Is the kernel loading agpgart? Shouldn't you use the fglrx one instead?

---

### Post by stoer on 2006-10-02
Ah -
 glxinfo | grep rendering
direct rendering: Yes

Sorry, forget to add "rendering"

Like i say, everything appears to work, just the reported errors that are making me uncomfortable, that and the strange behaviour of firefox coupled to the fact that i don't know if the 2 things are related or not?

Again, like i say, everything appears to work fine.  Games work, 3d works everything appears to be going well, apart from firefox (something i can live with, my son can always use windows for Flash games).

---

