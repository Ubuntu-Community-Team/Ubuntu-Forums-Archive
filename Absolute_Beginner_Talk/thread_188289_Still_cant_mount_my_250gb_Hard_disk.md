---
title: "Still cant mount my 250gb Hard disk"
date: 2006-06-03
forum: Absolute Beginner Talk
---

### Post by aktiwers on 2006-06-03
This is really killing me!

I have made 2 posts about this problem, but never got it solved. Im real thankful for all the help, and hope I can get it solved this time.

In this other thread I was told to check out dmegs, and I now see there is a problem. But what? and how do I fix it?

```
aktiwers@ubuntu:~$ dmesg
eue 0xdf415960 still mapped
[4318763.056000] [fglrx:firegl_rmmap] *ERROR* map 0xdf415a70 still in use (map_c ount=1)
[4318763.056000] [fglrx:firegl_free_buffer_queue] *ERROR* buffer qeue 0xdf415a60  still mapped
[4318763.056000] [fglrx:firegl_rmmap] *ERROR* map 0xdf415a70 still in use (map_c ount=1)
[4318763.056000] [fglrx:firegl_free_buffer_queue] *ERROR* buffer qeue 0xdf415a60  still mapped
[4318763.056000] [fglrx:firegl_rmmap] *ERROR* map 0xdf415970 still in use (map_c ount=1)
[4318763.056000] [fglrx:firegl_free_buffer_queue] *ERROR* buffer qeue 0xdf415960  still mapped
[4318763.056000] [fglrx:firegl_rmmap] *ERROR* map 0xdf415970 still in use (map_c ount=1)
[4318763.056000] [fglrx:firegl_free_buffer_queue] *ERROR* buffer qeue 0xdf415960  still mapped
[4318763.056000] [fglrx:firegl_rmmap] *ERROR* map 0xdf415a70 still in use (map_c ount=1)
[4318763.056000] [fglrx:firegl_free_buffer_queue] *ERROR* buffer qeue 0xdf415a60  still mapped
[4318763.057000] [fglrx:firegl_rmmap] *ERROR* map 0xdf415a70 still in use (map_c ount=1)
[4318763.057000] [fglrx:firegl_free_buffer_queue] *ERROR* buffer qeue 0xdf415a60  still mapped
[4318763.067000] [fglrx:firegl_rmmap] *ERROR* map 0xdf415970 still in use (map_c ount=1)
[4318763.067000] [fglrx:firegl_free_buffer_queue] *ERROR* buffer qeue 0xdf415960  still mapped
[4318763.067000] [fglrx:firegl_rmmap] *ERROR* map 0xdf415970 still in use (map_c ount=1)
[4318763.067000] [fglrx:firegl_free_buffer_queue] *ERROR* buffer qeue 0xdf415960  still mapped
[4318763.067000] [fglrx:firegl_rmmap] *ERROR* map 0xdf415a70 still in use (map_c ount=1)
[4318763.067000] [fglrx:firegl_free_buffer_queue] *ERROR* buffer qeue 0xdf415a60  still mapped
[4318763.067000] [fglrx:firegl_rmmap] *ERROR* map 0xdf415a70 still in use (map_c ount=1)
[4318763.067000] [fglrx:firegl_free_buffer_queue] *ERROR* buffer qeue 0xdf415a60  still mapped
[4318763.067000] [fglrx:firegl_rmmap] *ERROR* map 0xdf415970 still in use (map_c ount=1)
[4318763.067000] [fglrx:firegl_free_buffer_queue] *ERROR* buffer qeue 0xdf415960  still mapped
[4318763.072000] [fglrx:firegl_rmmap] *ERROR* map 0xdf415970 still in use (map_c ount=1)
[4318763.072000] [fglrx:firegl_free_buffer_queue] *ERROR* buffer qeue 0xdf415960  still mapped
[4318763.072000] [fglrx:firegl_rmmap] *ERROR* map 0xdf415a70 still in use (map_c ount=1)
[4318763.072000] [fglrx:firegl_free_buffer_queue] *ERROR* buffer qeue 0xdf415a60  still mapped
[4318763.075000] [fglrx:firegl_rmmap] *ERROR* map 0xdf415a70 still in use (map_c ount=1)
[4318763.075000] [fglrx:firegl_free_buffer_queue] *ERROR* buffer qeue 0xdf415a60  still mapped
[4318763.075000] [fglrx:firegl_rmmap] *ERROR* map 0xdf415970 still in use (map_c ount=1)
[4318763.075000] [fglrx:firegl_free_buffer_queue] *ERROR* buffer qeue 0xdf415960  still mapped
[4318763.076000] [fglrx:firegl_rmmap] *ERROR* map 0xdf415970 still in use (map_c ount=1)
[4318763.076000] [fglrx:firegl_free_buffer_queue] *ERROR* buffer qeue 0xdf415960  still mapped
[4318763.076000] [fglrx:firegl_rmmap] *ERROR* map 0xdf415a70 still in use (map_c ount=1)
[4318763.076000] [fglrx:firegl_free_buffer_queue] *ERROR* buffer qeue 0xdf415a60  still mapped
[4318763.098000] [fglrx:firegl_rmmap] *ERROR* map 0xdf415a70 still in use (map_c ount=1)
[4318763.098000] [fglrx:firegl_free_buffer_queue] *ERROR* buffer qeue 0xdf415a60  still mapped
[4318763.098000] [fglrx:firegl_rmmap] *ERROR* map 0xdf415970 still in use (map_c ount=1)
[4318763.098000] [fglrx:firegl_free_buffer_queue] *ERROR* buffer qeue 0xdf415960  still mapped
[4318763.245000] [fglrx:firegl_rmmap] *ERROR* map 0xdf415970 still in use (map_c ount=1)
[4318763.245000] [fglrx:firegl_free_buffer_queue] *ERROR* buffer qeue 0xdf415960  still mapped
[4318763.245000] [fglrx:firegl_rmmap] *ERROR* map 0xdf415a70 still in use (map_c ount=1)
[4318763.245000] [fglrx:firegl_free_buffer_queue] *ERROR* buffer qeue 0xdf415a60  still mapped
[4318763.245000] [fglrx:firegl_rmmap] *ERROR* map 0xdf415a70 still in use (map_c ount=1)
[4318763.245000] [fglrx:firegl_free_buffer_queue] *ERROR* buffer qeue 0xdf415a60  still mapped
[4318763.246000] [fglrx:firegl_rmmap] *ERROR* map 0xdf415970 still in use (map_c ount=1)
[4318763.246000] [fglrx:firegl_free_buffer_queue] *ERROR* buffer qeue 0xdf415960  still mapped
[4318763.246000] [fglrx:firegl_rmmap] *ERROR* map 0xdf415970 still in use (map_c ount=1)
[4318763.246000] [fglrx:firegl_free_buffer_queue] *ERROR* buffer qeue 0xdf415960  still mapped
[4318763.246000] [fglrx:firegl_rmmap] *ERROR* map 0xdf415a70 still in use (map_c ount=1)
[4318763.246000] [fglrx:firegl_free_buffer_queue] *ERROR* buffer qeue 0xdf415a60  still mapped
[4318763.246000] [fglrx:firegl_rmmap] *ERROR* map 0xdf415a70 still in use (map_c ount=1)
[4318763.246000] [fglrx:firegl_free_buffer_queue] *ERROR* buffer qeue 0xdf415a60  still mapped
[4318763.247000] [fglrx:firegl_rmmap] *ERROR* map 0xdf415970 still in use (map_c ount=1)
[4318763.247000] [fglrx:firegl_free_buffer_queue] *ERROR* buffer qeue 0xdf415960  still mapped
[4318763.287000] [fglrx:firegl_rmmap] *ERROR* map 0xdf415970 still in use (map_c ount=1)
[4318763.287000] [fglrx:firegl_free_buffer_queue] *ERROR* buffer qeue 0xdf415960  still mapped
[4318763.288000] [fglrx:firegl_rmmap] *ERROR* map 0xdf415a70 still in use (map_c ount=1)
[4318763.288000] [fglrx:firegl_free_buffer_queue] *ERROR* buffer qeue 0xdf415a60  still mapped
[4318763.288000] [fglrx:firegl_rmmap] *ERROR* map 0xdf415a70 still in use (map_c ount=1)
[4318763.288000] [fglrx:firegl_free_buffer_queue] *ERROR* buffer qeue 0xdf415a60  still mapped
[4318763.288000] [fglrx:firegl_rmmap] *ERROR* map 0xdf415970 still in use (map_c ount=1)
[4318763.288000] [fglrx:firegl_free_buffer_queue] *ERROR* buffer qeue 0xdf415960  still mapped
[4318763.289000] [fglrx:firegl_rmmap] *ERROR* map 0xdf415970 still in use (map_c ount=1)
[4318763.289000] [fglrx:firegl_free_buffer_queue] *ERROR* buffer qeue 0xdf415960  still mapped
[4318763.289000] [fglrx:firegl_rmmap] *ERROR* map 0xdf415a70 still in use (map_c ount=1)
[4318763.289000] [fglrx:firegl_free_buffer_queue] *ERROR* buffer qeue 0xdf415a60  still mapped
[4318763.289000] [fglrx:firegl_rmmap] *ERROR* map 0xdf415a70 still in use (map_c ount=1)
[4318763.289000] [fglrx:firegl_free_buffer_queue] *ERROR* buffer qeue 0xdf415a60  still mapped
[4318763.289000] [fglrx:firegl_rmmap] *ERROR* map 0xdf415970 still in use (map_c ount=1)
[4318763.289000] [fglrx:firegl_free_buffer_queue] *ERROR* buffer qeue 0xdf415960  still mapped
[4318763.364000] [fglrx:firegl_rmmap] *ERROR* map 0xdf415970 still in use (map_c ount=1)
[4318763.364000] [fglrx:firegl_free_buffer_queue] *ERROR* buffer qeue 0xdf415960  still mapped
[4318763.365000] [fglrx:firegl_rmmap] *ERROR* map 0xdf415a70 still in use (map_c ount=1)
[4318763.365000] [fglrx:firegl_free_buffer_queue] *ERROR* buffer qeue 0xdf415a60  still mapped
[4318763.369000] [fglrx:firegl_rmmap] *ERROR* map 0xdf415a70 still in use (map_c ount=1)
[4318763.369000] [fglrx:firegl_free_buffer_queue] *ERROR* buffer qeue 0xdf415a60  still mapped
[4318763.369000] [fglrx:firegl_rmmap] *ERROR* map 0xdf415970 still in use (map_c ount=1)
[4318763.369000] [fglrx:firegl_free_buffer_queue] *ERROR* buffer qeue 0xdf415960  still mapped
[4318763.370000] [fglrx:firegl_rmmap] *ERROR* map 0xdf415970 still in use (map_c ount=1)
[4318763.370000] [fglrx:firegl_free_buffer_queue] *ERROR* buffer qeue 0xdf415960  still mapped
[4318763.371000] [fglrx:firegl_rmmap] *ERROR* map 0xdf415a70 still in use (map_c ount=1)
[4318763.371000] [fglrx:firegl_free_buffer_queue] *ERROR* buffer qeue 0xdf415a60  still mapped
[4318763.372000] [fglrx:firegl_rmmap] *ERROR* map 0xdf415a70 still in use (map_c ount=1)
[4318763.372000] [fglrx:firegl_free_buffer_queue] *ERROR* buffer qeue 0xdf415a60  still mapped
[4318763.372000] [fglrx:firegl_rmmap] *ERROR* map 0xdf415970 still in use (map_c ount=1)
[4318763.372000] [fglrx:firegl_free_buffer_queue] *ERROR* buffer qeue 0xdf415960  still mapped
[4318763.379000] [fglrx:firegl_rmmap] *ERROR* map 0xdf415970 still in use (map_c ount=1)
[4318763.379000] [fglrx:firegl_free_buffer_queue] *ERROR* buffer qeue 0xdf415960  still mapped
[4318763.379000] [fglrx:firegl_rmmap] *ERROR* map 0xdf415a70 still in use (map_c ount=1)
[4318763.379000] [fglrx:firegl_free_buffer_queue] *ERROR* buffer qeue 0xdf415a60  still mapped
[4318763.389000] [fglrx:firegl_rmmap] *ERROR* map 0xdf415a70 still in use (map_c ount=1)
[4318763.389000] [fglrx:firegl_free_buffer_queue] *ERROR* buffer qeue 0xdf415a60  still mapped
[4318763.389000] [fglrx:firegl_rmmap] *ERROR* map 0xdf415970 still in use (map_c ount=1)
[4318763.389000] [fglrx:firegl_free_buffer_queue] *ERROR* buffer qeue 0xdf415960  still mapped
[4318763.869000] [fglrx:firegl_rmmap] *ERROR* map 0xdf415970 still in use (map_c ount=1)
[4318763.869000] [fglrx:firegl_free_buffer_queue] *ERROR* buffer qeue 0xdf415960  still mapped
[4318763.869000] [fglrx:firegl_rmmap] *ERROR* map 0xdf415a70 still in use (map_c ount=1)
[4318763.869000] [fglrx:firegl_free_buffer_queue] *ERROR* buffer qeue 0xdf415a60  still mapped
[4318764.139000] [fglrx:firegl_rmmap] *ERROR* map 0xdf415a70 still in use (map_c ount=1)
[4318764.139000] [fglrx:firegl_free_buffer_queue] *ERROR* buffer qeue 0xdf415a60  still mapped
[4318764.139000] [fglrx:firegl_rmmap] *ERROR* map 0xdf415970 still in use (map_c ount=1)
[4318764.139000] [fglrx:firegl_free_buffer_queue] *ERROR* buffer qeue 0xdf415960  still mapped
[4318764.477000] [fglrx:firegl_rmmap] *ERROR* map 0xdf415970 still in use (map_c ount=1)
[4318764.477000] [fglrx:firegl_free_buffer_queue] *ERROR* buffer qeue 0xdf415960  still mapped
[4318764.477000] [fglrx:firegl_rmmap] *ERROR* map 0xdf415a70 still in use (map_c ount=1)
[4318764.477000] [fglrx:firegl_free_buffer_queue] *ERROR* buffer qeue 0xdf415a60  still mapped
[4318765.086000] [fglrx:firegl_rmmap] *ERROR* map 0xdf415a70 still in use (map_c ount=1)
[4318765.086000] [fglrx:firegl_free_buffer_queue] *ERROR* buffer qeue 0xdf415a60  still mapped
[4318765.086000] [fglrx:firegl_rmmap] *ERROR* map 0xdf415970 still in use (map_c ount=1)
[4318765.086000] [fglrx:firegl_free_buffer_queue] *ERROR* buffer qeue 0xdf415960  still mapped
[4318765.089000] [fglrx:firegl_rmmap] *ERROR* map 0xdf415970 still in use (map_c ount=1)
[4318765.089000] [fglrx:firegl_free_buffer_queue] *ERROR* buffer qeue 0xdf415960  still mapped
[4318765.089000] [fglrx:firegl_rmmap] *ERROR* map 0xdf415a70 still in use (map_c ount=1)
[4318765.089000] [fglrx:firegl_free_buffer_queue] *ERROR* buffer qeue 0xdf415a60  still mapped
[4318765.100000] [fglrx:firegl_rmmap] *ERROR* map 0xdf415a70 still in use (map_c ount=1)
[4318765.100000] [fglrx:firegl_free_buffer_queue] *ERROR* buffer qeue 0xdf415a60  still mapped
[4318765.100000] [fglrx:firegl_rmmap] *ERROR* map 0xdf415970 still in use (map_c ount=1)
[4318765.100000] [fglrx:firegl_free_buffer_queue] *ERROR* buffer qeue 0xdf415960  still mapped
[4318765.103000] [fglrx:firegl_rmmap] *ERROR* map 0xdf415970 still in use (map_c ount=1)
[4318765.103000] [fglrx:firegl_free_buffer_queue] *ERROR* buffer qeue 0xdf415960  still mapped
[4318765.103000] [fglrx:firegl_rmmap] *ERROR* map 0xdf415a70 still in use (map_c ount=1)
[4318765.103000] [fglrx:firegl_free_buffer_queue] *ERROR* buffer qeue 0xdf415a60  still mapped
[4318765.174000] [fglrx:firegl_rmmap] *ERROR* map 0xdf415a70 still in use (map_c ount=1)
[4318765.174000] [fglrx:firegl_free_buffer_queue] *ERROR* buffer qeue 0xdf415a60  still mapped
[4318765.174000] [fglrx:firegl_rmmap] *ERROR* map 0xdf415970 still in use (map_c ount=1)
[4318765.174000] [fglrx:firegl_free_buffer_queue] *ERROR* buffer qeue 0xdf415960  still mapped
[4318765.175000] [fglrx:firegl_rmmap] *ERROR* map 0xdf415970 still in use (map_c ount=1)
[4318765.175000] [fglrx:firegl_free_buffer_queue] *ERROR* buffer qeue 0xdf415960  still mapped
[4318765.175000] [fglrx:firegl_rmmap] *ERROR* map 0xdf415a70 still in use (map_c ount=1)
[4318765.175000] [fglrx:firegl_free_buffer_queue] *ERROR* buffer qeue 0xdf415a60  still mapped
[4318765.175000] [fglrx:firegl_rmmap] *ERROR* map 0xdf415a70 still in use (map_c ount=1)
[4318765.175000] [fglrx:firegl_free_buffer_queue] *ERROR* buffer qeue 0xdf415a60  still mapped
[4318765.175000] [fglrx:firegl_rmmap] *ERROR* map 0xdf415970 still in use (map_c ount=1)
[4318765.175000] [fglrx:firegl_free_buffer_queue] *ERROR* buffer qeue 0xdf415960  still mapped
[4318765.176000] [fglrx:firegl_rmmap] *ERROR* map 0xdf415970 still in use (map_c ount=1)
[4318765.176000] [fglrx:firegl_free_buffer_queue] *ERROR* buffer qeue 0xdf415960  still mapped
[4318765.176000] [fglrx:firegl_rmmap] *ERROR* map 0xdf415a70 still in use (map_c ount=1)
[4318765.176000] [fglrx:firegl_free_buffer_queue] *ERROR* buffer qeue 0xdf415a60  still mapped
[4318765.177000] [fglrx:firegl_rmmap] *ERROR* map 0xdf415a70 still in use (map_c ount=1)
[4318765.177000] [fglrx:firegl_free_buffer_queue] *ERROR* buffer qeue 0xdf415a60  still mapped
[4318765.177000] [fglrx:firegl_rmmap] *ERROR* map 0xdf415970 still in use (map_c ount=1)
[4318765.177000] [fglrx:firegl_free_buffer_queue] *ERROR* buffer qeue 0xdf415960  still mapped
[4318765.177000] [fglrx:firegl_rmmap] *ERROR* map 0xdf415970 still in use (map_c ount=1)
[4318765.177000] [fglrx:firegl_free_buffer_queue] *ERROR* buffer qeue 0xdf415960  still mapped
[4318765.177000] [fglrx:firegl_rmmap] *ERROR* map 0xdf415a70 still in use (map_c ount=1)
[4318765.177000] [fglrx:firegl_free_buffer_queue] *ERROR* buffer qeue 0xdf415a60  still mapped
[4318765.190000] [fglrx:firegl_rmmap] *ERROR* map 0xdf415a70 still in use (map_c ount=1)
[4318765.190000] [fglrx:firegl_free_buffer_queue] *ERROR* buffer qeue 0xdf415a60  still mapped
[4318765.190000] [fglrx:firegl_rmmap] *ERROR* map 0xdf415970 still in use (map_c ount=1)
[4318765.190000] [fglrx:firegl_free_buffer_queue] *ERROR* buffer qeue 0xdf415960  still mapped
[4318765.191000] [fglrx:firegl_rmmap] *ERROR* map 0xdf415970 still in use (map_c ount=1)
[4318765.191000] [fglrx:firegl_free_buffer_queue] *ERROR* buffer qeue 0xdf415960  still mapped
[4318765.191000] [fglrx:firegl_rmmap] *ERROR* map 0xdf415a70 still in use (map_c ount=1)
[4318765.191000] [fglrx:firegl_free_buffer_queue] *ERROR* buffer qeue 0xdf415a60  still mapped
[4318765.192000] [fglrx:firegl_rmmap] *ERROR* map 0xdf415a70 still in use (map_c ount=1)
[4318765.192000] [fglrx:firegl_free_buffer_queue] *ERROR* buffer qeue 0xdf415a60  still mapped
[4318765.192000] [fglrx:firegl_rmmap] *ERROR* map 0xdf415970 still in use (map_c ount=1)
[4318765.192000] [fglrx:firegl_free_buffer_queue] *ERROR* buffer qeue 0xdf415960  still mapped
[4318765.196000] [fglrx:firegl_rmmap] *ERROR* map 0xdf415970 still in use (map_c ount=1)
[4318765.196000] [fglrx:firegl_free_buffer_queue] *ERROR* buffer qeue 0xdf415960  still mapped
[4318765.196000] [fglrx:firegl_rmmap] *ERROR* map 0xdf415a70 still in use (map_c ount=1)
[4318765.196000] [fglrx:firegl_free_buffer_queue] *ERROR* buffer qeue 0xdf415a60  still mapped
[4318765.197000] [fglrx:firegl_rmmap] *ERROR* map 0xdf415a70 still in use (map_c ount=1)
[4318765.197000] [fglrx:firegl_free_buffer_queue] *ERROR* buffer qeue 0xdf415a60  still mapped
[4318765.197000] [fglrx:firegl_rmmap] *ERROR* map 0xdf415970 still in use (map_c ount=1)
[4318765.197000] [fglrx:firegl_free_buffer_queue] *ERROR* buffer qeue 0xdf415960  still mapped
[4318765.197000] [fglrx:firegl_rmmap] *ERROR* map 0xdf415970 still in use (map_c ount=1)
[4318765.197000] [fglrx:firegl_free_buffer_queue] *ERROR* buffer qeue 0xdf415960  still mapped
[4318765.198000] [fglrx:firegl_rmmap] *ERROR* map 0xdf415a70 still in use (map_c ount=1)
[4318765.198000] [fglrx:firegl_free_buffer_queue] *ERROR* buffer qeue 0xdf415a60  still mapped
[4318765.198000] [fglrx:firegl_rmmap] *ERROR* map 0xdf415a70 still in use (map_c ount=1)
[4318765.198000] [fglrx:firegl_free_buffer_queue] *ERROR* buffer qeue 0xdf415a60  still mapped
[4318765.198000] [fglrx:firegl_rmmap] *ERROR* map 0xdf415970 still in use (map_c ount=1)
[4318765.198000] [fglrx:firegl_free_buffer_queue] *ERROR* buffer qeue 0xdf415960  still mapped
aktiwers@ubuntu:~$
``` 
Here is a link to my earlyer thread.
[http://www.ubuntuforums.org/showthread.php?t=173066]("http://www.ubuntuforums.org/showthread.php?t=173066")

I kind of gave up back there, but now I really want to watch some of my movies.
Also please view the screenshot I uploaded.

Any help on getting my Hardisc mounted, will be very appriciated!

Thanks alot for taking the time to read.

---

### Post by u.b.u.n.t.u on 2006-06-03
Hi,

I recently added a 2nd HDD for storage.

[http://www.ubuntuforums.org/showthread.php?t=187339](http://www.ubuntuforums.org/showthread.php?t=187339)

Maybe something there is of use to you. 

Cheers.

---

### Post by aktiwers on 2006-06-03
[quote=u.b.u.n.t.u]Hi,

I recently added a 2nd HDD for storage.

[http://www.ubuntuforums.org/showthread.php?t=187339]("http://www.ubuntuforums.org/showthread.php?t=187339")

Maybe something there is of use to you. 

Cheers.[/quote] 
Thanks, I did actually follow that thread (its good), but as you see on my earlyer threat, I have already tried that. Its like the HD is mounted, but not accessable?

Thanks a lot for you reply.

Any other suggestions?

---

### Post by u.b.u.n.t.u on 2006-06-03
[QUOTE=aktiwers]Thanks, I did actually follow that threat (its good), but as you see on my earlyer threat, I have already tried that. Its like the HD is mounted, but not accessable?

Thanks a lot for you reply.

Any other suggestions?[/QUOTE]

Sorry aktiwers but,

thread (this is what we have here at the board, forum)
[http://dictionary.reference.com/search?q=thread](http://dictionary.reference.com/search?q=thread)

threat (this is something else :shock: )
[http://dictionary.reference.com/search?q=threat](http://dictionary.reference.com/search?q=threat)

It is easiest for me, so I will ask.

1. What file system do you have on that HDD?

2. Is it empty or full?

3. Is it brand new, never used before?

---

### Post by aktiwers on 2006-06-03
Hehe thanks for pointing that out! Offcause I ment thread and not threat. English is not my first langues, so sorry for any typos.

1) Its NTFS, and it worked fine on Ubuntu 5.10 with the defualt kernel.
2) Its not empty, its almost full. I think it has 10 - 15gb Free.
3) Nope not brand new, but like 10 months old.

Thanks a lot :)

EDIT: Fixed the typos for you ;)

---

### Post by CompShrink on 2006-06-03
Ok, so the error messages from dmesg are about your video card. Sorry to let you know more bad news... I don't know what that error is, and if you think the video is OK for what you do with it (as in, as long as you don't game or work on 3d modeling, etc) I would leave the video errors alone.

It still gives you the same error when you try to mount?

There is a folder in /media named wd250 right? There has to be a normal, regular directory to mount to. Try the simpliest possible:

sudo mount -t ntfs /dev/sdb5 /media/wd250 

and tell us the error, again, please.

---

### Post by u.b.u.n.t.u on 2006-06-04
aktiwers I know very little about linux, but, 

```
error: device /dev/sdb5/ is not removable
error: could not execute pmount
```

it would seem that ubuntu is not reading the device as removable and therefore a pmount (whatever that is) couldn't occur.

The fstab determines the status of a HDD doesn't it? Is that correct? (just guessing here). Perhaps something in there isn't right.

Also the System/Administrator/Disks ... Partitions/Access path may be useful to check out.

Can you install this HDD at all? Like any other means? A matter of trial and error, though someone here may hopefully give you a quick answer.

---

### Post by aktiwers on 2006-06-04
Okey thats bad news, that the dmegs is more errors.
Well I will look to that later, all games (also 3D) runs fine and I have no problem.

Everytime I try to mount they way you say CompShrink I get this Too busy messege.

```
aktiwers@ubuntu:~$ sudo mount -t ntfs /dev/sdb5 /media/wd250
Password:
mount: /dev/sdb5 already mounted or /media/wd250 busy
aktiwers@ubuntu:~$

```

u.b.u.n.t.u - Thanks, Im gonna look one more time in Fstab to see if anythings wrong.

Thanks a lot so fare guys, hope to see some more suggestions.

---

### Post by CompShrink on 2006-06-05
Just so you don't go looking at something irrelavent: pmount is (to my understanding) what is used on removable media: cameras, usb flash memory sticks, CDs etc. When you use nautilus to try and open a memory device that isn't mounted, but is listed, it assumes it's removable. Otherwise it wouldn't be unmounted and listed.

That is usually true, but not in your case, correct?

---

### Post by hotstovejer on 2006-06-05
I'm getting the exact same thing. I have a 200gig drive that says that it's mounted, but I can't see anything on, cause it can't pmount it.

Here's what my dmesg looks like.

```
[4294667.296000] Linux version 2.6.15-23-k7 (buildd@rothera) (gcc version 4.0.3 (Ubuntu 4.0.3-1ubuntu5)) #1 SMP PREEMPT Tue May 23 14:20:54 UTC 2006
[4294667.296000] BIOS-provided physical RAM map:
[4294667.296000]  BIOS-e820: 0000000000000000 - 000000000009fc00 (usable)
[4294667.296000]  BIOS-e820: 000000000009fc00 - 00000000000a0000 (reserved)
[4294667.296000]  BIOS-e820: 00000000000f0000 - 0000000000100000 (reserved)
[4294667.296000]  BIOS-e820: 0000000000100000 - 000000003fff0000 (usable)
[4294667.296000]  BIOS-e820: 000000003fff0000 - 000000003fff8000 (ACPI data)
[4294667.296000]  BIOS-e820: 000000003fff8000 - 0000000040000000 (ACPI NVS)
[4294667.296000]  BIOS-e820: 00000000fec00000 - 00000000fec01000 (reserved)
[4294667.296000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
[4294667.296000]  BIOS-e820: 00000000fff80000 - 0000000100000000 (reserved)
[4294667.296000] 127MB HIGHMEM available.
[4294667.296000] 896MB LOWMEM available.
[4294667.296000] found SMP MP-table at 000fb940
[4294667.296000] On node 0 totalpages: 262128
[4294667.296000]   DMA zone: 4096 pages, LIFO batch:0
[4294667.296000]   DMA32 zone: 0 pages, LIFO batch:0
[4294667.296000]   Normal zone: 225280 pages, LIFO batch:31
[4294667.296000]   HighMem zone: 32752 pages, LIFO batch:7
[4294667.296000] DMI 2.3 present.
[4294667.296000] ACPI: RSDP (v000 AMI                                   ) @ 0x000fa900
[4294667.296000] ACPI: RSDT (v001 AMIINT VIA_K7   0x00000010 MSFT 0x00000097) @ 0x3fff0000
[4294667.296000] ACPI: FADT (v001 AMIINT VIA_K7   0x00000011 MSFT 0x00000097) @ 0x3fff0030
[4294667.296000] ACPI: MADT (v001 AMIINT VIA_K7   0x00000009 MSFT 0x00000097) @ 0x3fff00c0
[4294667.296000] ACPI: DSDT (v001    VIA   VIA_K7 0x00001000 MSFT 0x0100000d) @ 0x00000000
[4294667.296000] ACPI: PM-Timer IO Port: 0x808
[4294667.296000] ACPI: Local APIC address 0xfee00000
[4294667.296000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
[4294667.296000] Processor #0 6:6 APIC version 16
[4294667.296000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
[4294667.296000] IOAPIC[0]: apic_id 2, version 2, address 0xfec00000, GSI 0-23
[4294667.296000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[4294667.296000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 low level)
[4294667.296000] ACPI: IRQ0 used by override.
[4294667.296000] ACPI: IRQ2 used by override.
[4294667.296000] ACPI: IRQ9 used by override.
[4294667.296000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[4294667.296000] Using ACPI (MADT) for SMP configuration information
[4294667.296000] Allocating PCI resources starting at 50000000 (gap: 40000000:bec00000)
[4294667.296000] Built 1 zonelists
[4294667.296000] Kernel command line: root=/dev/hda1 ro quiet splash
[4294667.296000] mapped APIC to ffffd000 (fee00000)
[4294667.296000] mapped IOAPIC to ffffc000 (fec00000)
[4294667.296000] Initializing CPU#0
[4294667.296000] PID hash table entries: 4096 (order: 12, 65536 bytes)
[4294667.296000] Detected 1150.680 MHz processor.
[4294667.296000] Using pmtmr for high-res timesource
[4294667.296000] Console: colour VGA+ 80x25
[4294669.743000] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[4294669.745000] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[4294669.804000] Memory: 1027216k/1048512k available (2094k kernel code, 20556k reserved, 597k data, 332k init, 131008k highmem)
[4294669.804000] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[4294669.864000] Calibrating delay using timer specific routine.. 2301.97 BogoMIPS (lpj=1150985)
[4294669.864000] Security Framework v1.0.0 initialized
[4294669.864000] SELinux:  Disabled at boot.
[4294669.864000] Mount-cache hash table entries: 512
[4294669.864000] CPU: After generic identify, caps: 0383fbff c1c3fbff 00000000 00000000 00000000 00000000 00000000
[4294669.864000] CPU: After vendor identify, caps: 0383fbff c1c3fbff 00000000 00000000 00000000 00000000 00000000
[4294669.864000] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
[4294669.864000] CPU: L2 Cache: 256K (64 bytes/line)
[4294669.864000] CPU: After all inits, caps: 0383fbff c1c3fbff 00000000 00000020 00000000 00000000 00000000
[4294669.864000] mtrr: v2.0 (20020519)
[4294669.864000] Enabling fast FPU save and restore... done.
[4294669.864000] Enabling unmasked SIMD FPU exception support... done.
[4294669.864000] Checking 'hlt' instruction... OK.
[4294669.868000] SMP alternatives: switching to UP code
[4294669.868000] checking if image is initramfs... it is
[4294670.790000] Freeing initrd memory: 6758k freed
[4294670.806000] ACPI: Looking for DSDT ... not found!
[4294670.809000] CPU0: AMD Athlon(tm) Processor stepping 02
[4294670.810000] Total of 1 processors activated (2301.97 BogoMIPS).
[4294670.810000] ENABLING IO-APIC IRQs
[4294670.810000] ..TIMER: vector=0x31 apic1=0 pin1=2 apic2=-1 pin2=-1
[4294670.921000] Brought up 1 CPUs
[4294670.921000] NET: Registered protocol family 16
[4294670.921000] EISA bus registered
[4294670.921000] ACPI: bus type pci registered
[4294670.922000] PCI: PCI BIOS revision 2.10 entry at 0xfdaf1, last bus=1
[4294670.922000] PCI: Using configuration type 1
[4294670.923000] ACPI: Subsystem revision 20051216
[4294670.930000] ACPI: Interpreter enabled
[4294670.930000] ACPI: Using IOAPIC for interrupt routing
[4294670.930000] ACPI: PCI Root Bridge [PCI0] (0000:00)
[4294670.930000] PCI: Probing PCI hardware (bus 00)
[4294670.936000] Boot video device is 0000:01:00.0
[4294670.936000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[4294670.976000] ACPI: Power Resource [URP1] (off)
[4294670.976000] ACPI: Power Resource [URP2] (off)
[4294670.976000] ACPI: Power Resource [FDDP] (off)
[4294670.976000] ACPI: Power Resource [LPTP] (off)
[4294670.979000] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 10 *11 12 14 15)
[4294670.979000] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 6 7 *10 11 12 14 15)
[4294670.980000] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 6 7 10 11 *12 14 15)
[4294670.980000] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 *5 6 7 10 11 12 14 15)
[4294670.980000] Linux Plug and Play Support v0.97 (c) Adam Belay
[4294670.980000] pnp: PnP ACPI init
[4294670.986000] pnp: PnP ACPI: found 9 devices
[4294670.986000] PnPBIOS: Disabled by ACPI PNP
[4294670.986000] PCI: Using ACPI for IRQ routing
[4294670.986000] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[4294670.989000] PCI: Bridge: 0000:00:01.0
[4294670.989000]   IO window: disabled.
[4294670.989000]   MEM window: dde00000-dfefffff
[4294670.989000]   PREFETCH window: bdc00000-ddcfffff
[4294670.989000] PCI: Setting latency timer of device 0000:00:01.0 to 64
[4294670.990000] audit: initializing netlink socket (disabled)
[4294670.990000] audit(1149432859.988:1): initialized
[4294670.990000] highmem bounce pool size: 64 pages
[4294670.990000] VFS: Disk quotas dquot_6.5.1
[4294670.990000] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[4294670.990000] Initializing Cryptographic API
[4294670.991000] io scheduler noop registered
[4294670.991000] io scheduler anticipatory registered
[4294670.991000] io scheduler deadline registered
[4294670.991000] io scheduler cfq registered
[4294670.991000] isapnp: Scanning for PnP cards...
[4294671.348000] isapnp: No Plug & Play device found
[4294671.370000] Real Time Clock Driver v1.12
[4294671.371000] PNP: PS/2 Controller [PNP0303:PS2K] at 0x60,0x64 irq 1
[4294671.371000] PNP: PS/2 controller doesn't have AUX irq; using default 12
[4294671.371000] serio: i8042 AUX port at 0x60,0x64 irq 12
[4294671.371000] serio: i8042 KBD port at 0x60,0x64 irq 1
[4294671.371000] Serial: 8250/16550 driver $Revision: 1.90 $ 48 ports, IRQ sharing enabled
[4294671.371000] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[4294671.371000] serial8250: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[4294671.374000] 00:01: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[4294671.374000] 00:02: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[4294671.375000] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[4294671.375000] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[4294671.375000] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
[4294671.376000] mice: PS/2 mouse device common for all mice
[4294671.376000] EISA: Probing bus 0 at eisa.0
[4294671.376000] EISA: Detected 0 cards.
[4294671.376000] NET: Registered protocol family 2
[4294671.385000] IP route cache hash table entries: 65536 (order: 6, 262144 bytes)
[4294671.385000] TCP established hash table entries: 262144 (order: 9, 3145728 bytes)
[4294671.394000] TCP bind hash table entries: 65536 (order: 7, 786432 bytes)
[4294671.396000] TCP: Hash tables configured (established 262144 bind 65536)
[4294671.396000] TCP reno registered
[4294671.397000] TCP bic registered
[4294671.397000] NET: Registered protocol family 1
[4294671.397000] NET: Registered protocol family 8
[4294671.397000] NET: Registered protocol family 20
[4294671.397000] Using IPI No-Shortcut mode
[4294671.397000] ACPI wakeup devices:
[4294671.397000] PCI0 UAR1 USB1 USB2 USB3 EHCI  USB USBA  AC9  MC9 SLPB
[4294671.397000] ACPI: (supports S0 S1 S4 S5)
[4294671.397000] Freeing unused kernel memory: 332k freed
[4294671.423000] input: AT Translated Set 2 keyboard as /class/input/input0
[4294671.479000] vga16fb: initializing
[4294671.479000] vga16fb: mapped to 0xc00a0000
[4294671.609000] Console: switching to colour frame buffer device 80x25
[4294671.609000] fb0: VGA16 VGA frame buffer device
[4294672.727000] Capability LSM initialized
[4294672.786000] ACPI: Processor [CPU1] (supports 16 throttling states)
[4294673.679000] VP_IDE: IDE controller at PCI slot 0000:00:11.1
[4294673.679000] ACPI: PCI Interrupt 0000:00:11.1[A]: no GSI
[4294673.679000] PCI: Via IRQ fixup for 0000:00:11.1, from 255 to 15
[4294673.679000] VP_IDE: chipset revision 6
[4294673.679000] VP_IDE: not 100% native mode: will probe irqs later
[4294673.679000] VP_IDE: VIA vt8233a (rev 00) IDE UDMA133 controller on pci0000:00:11.1
[4294673.679000]     ide0: BM-DMA at 0xfc00-0xfc07, BIOS settings: hda:DMA, hdb:DMA
[4294673.679000]     ide1: BM-DMA at 0xfc08-0xfc0f, BIOS settings: hdc:DMA, hdd:DMA
[4294673.679000] Probing IDE interface ide0...
[4294674.067000] hda: WDC WD205BA, ATA DISK drive
[4294674.323000] hdb: WDC WD2000JB-00GVA0, ATA DISK drive
[4294674.378000] ide0 at 0x1f0-0x1f7,0x3f6 on irq 14
[4294674.411000] Probing IDE interface ide1...
[4294675.206000] hdc: TDK CDRW4800B, ATAPI CD/DVD-ROM drive
[4294675.920000] hdd: SAMSUNG DVD-ROM SD-616T, ATAPI CD/DVD-ROM drive
[4294675.975000] ide1 at 0x170-0x177,0x376 on irq 15
[4294675.990000] hda: max request size: 128KiB
[4294676.017000] hda: 40088160 sectors (20525 MB) w/2048KiB Cache, CHS=39770/16/63, UDMA(66)
[4294676.017000] hda: cache flushes not supported
[4294676.018000]  hda: hda1 hda2 < hda5 hda6 > hda3
[4294676.062000] hdb: max request size: 1024KiB
[4294676.063000] hdb: 390721968 sectors (200049 MB) w/8192KiB Cache, CHS=24321/255/63, UDMA(100)
[4294676.065000] hdb: cache flushes supported
[4294676.065000]  hdb:<6>hdc: ATAPI 48X CD-ROM CD-R/RW drive, 2048kB Cache, UDMA(33)
[4294676.069000] Uniform CD-ROM driver Revision: 3.20
[4294676.077000]  hdb1
[4294676.109000] hdd: ATAPI 48X DVD-ROM drive, 512kB Cache, UDMA(33)
[4294676.589000] usbcore: registered new driver usbfs
[4294676.589000] usbcore: registered new driver hub
[4294676.592000] USB Universal Host Controller Interface driver v2.3
[4294676.593000] ACPI: PCI Interrupt 0000:00:06.0[A] -> GSI 17 (level, low) -> IRQ 169
[4294676.593000] PCI: Via IRQ fixup for 0000:00:06.0, from 10 to 9
[4294676.593000] uhci_hcd 0000:00:06.0: UHCI Host Controller
[4294676.595000] uhci_hcd 0000:00:06.0: new USB bus registered, assigned bus number 1
[4294676.595000] uhci_hcd 0000:00:06.0: irq 169, io base 0x0000e800
[4294676.598000] hub 1-0:1.0: USB hub found
[4294676.598000] hub 1-0:1.0: 2 ports detected
[4294676.670000] ohci_hcd: 2005 April 22 USB 1.1 'Open' Host Controller (OHCI) Driver (PCI)
[4294676.700000] ACPI: PCI Interrupt 0000:00:11.2[D] -> GSI 21 (level, low) -> IRQ 177
[4294676.700000] PCI: Via IRQ fixup for 0000:00:11.2, from 5 to 1
[4294676.700000] uhci_hcd 0000:00:11.2: UHCI Host Controller
[4294676.700000] uhci_hcd 0000:00:11.2: new USB bus registered, assigned bus number 2
[4294676.700000] uhci_hcd 0000:00:11.2: irq 177, io base 0x0000d800
[4294676.700000] hub 2-0:1.0: USB hub found
[4294676.700000] hub 2-0:1.0: 2 ports detected
[4294676.701000] ACPI: PCI Interrupt 0000:00:0b.0[A] -> GSI 18 (level, low) -> IRQ 185
[4294676.701000] ohci_hcd 0000:00:0b.0: OHCI Host Controller
[4294676.703000] ieee1394: Initialized config rom entry `ip1394'
[4294676.706000] ohci1394: $Rev: 1313 $ Ben Collins <bcollins@debian.org>
[4294676.706000] ACPI: PCI Interrupt 0000:00:08.2[B] -> GSI 16 (level, low) -> IRQ 193
[4294676.758000] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[193]  MMIO=[dffff000-dffff7ff]  Max Packet=[2048]
[4294676.802000] ACPI: PCI Interrupt 0000:00:11.3[D] -> GSI 21 (level, low) -> IRQ 177
[4294676.802000] PCI: Via IRQ fixup for 0000:00:11.3, from 5 to 1
[4294676.802000] uhci_hcd 0000:00:11.3: UHCI Host Controller
[4294676.802000] uhci_hcd 0000:00:11.3: new USB bus registered, assigned bus number 3
[4294676.802000] uhci_hcd 0000:00:11.3: irq 177, io base 0x0000dc00
[4294676.803000] hub 3-0:1.0: USB hub found
[4294676.803000] hub 3-0:1.0: 2 ports detected
[4294676.908000] ohci_hcd 0000:00:0b.0: new USB bus registered, assigned bus number 4
[4294676.908000] ohci_hcd 0000:00:0b.0: irq 185, io mem 0xdfffd000
[4294677.113000] usb 2-1: new full speed USB device using uhci_hcd and address 2[4294677.470000] hub 4-0:1.0: USB hub found
[4294677.470000] hub 4-0:1.0: 3 ports detected
[4294677.498000] SCSI subsystem initialized
[4294677.502000] Initializing USB Mass Storage driver...
[4294677.661000] usb 3-2: new low speed USB device using uhci_hcd and address 2
[4294677.982000] ACPI: PCI Interrupt 0000:00:0b.1[B] -> GSI 19 (level, low) -> IRQ 201
[4294677.982000] ohci_hcd 0000:00:0b.1: OHCI Host Controller
[4294677.982000] ohci_hcd 0000:00:0b.1: new USB bus registered, assigned bus number 5
[4294677.982000] ohci_hcd 0000:00:0b.1: irq 201, io mem 0xdfffe000
[4294677.983000] scsi0 : SCSI emulation for USB Mass Storage devices
[4294677.983000] usb-storage: device found at 2
[4294677.983000] usb-storage: waiting for device to settle before scanning
[4294677.983000] usbcore: registered new driver usb-storage
[4294677.983000] USB Mass Storage support registered.
[4294677.985000] usbcore: registered new driver hiddev
[4294678.007000] input: Logitech USB-PS/2 Optical Mouse as /class/input/input1
[4294678.008000] input: USB HID v1.10 Mouse [Logitech USB-PS/2 Optical Mouse] on usb-0000:00:11.3-2
[4294678.008000] usbcore: registered new driver usbhid
[4294678.008000] drivers/usb/input/hid-core.c: v2.6:USB HID core driver
[4294678.018000] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[00023c003102509d][4294678.544000] hub 5-0:1.0: USB hub found
[4294678.544000] hub 5-0:1.0: 2 ports detected
[4294679.059000] ACPI: PCI Interrupt 0000:00:0b.2[C] -> GSI 16 (level, low) -> IRQ 193
[4294679.059000] ehci_hcd 0000:00:0b.2: EHCI Host Controller
[4294679.081000] ehci_hcd 0000:00:0b.2: new USB bus registered, assigned bus number 6
[4294679.081000] ehci_hcd 0000:00:0b.2: irq 193, io mem 0xdffffb00
[4294679.081000] ehci_hcd 0000:00:0b.2: USB 2.0 started, EHCI 0.95, driver 10 Dec 2004
[4294679.081000] hub 6-0:1.0: USB hub found
[4294679.081000] hub 6-0:1.0: 5 ports detected
[4294679.299000] Attempting manual resume
[4294682.988000]   Vendor: HDS72258  Model: 0VLAT20           Rev: V32O
[4294682.988000]   Type:   Direct-Access                      ANSI SCSI revision: 02
[4294682.988000] usb-storage: device scan complete
[4294691.025000] Driver 'sd' needs updating - please use bus_type methods
[4294691.031000] SCSI device sda: 160836480 512-byte hdwr sectors (82348 MB)
[4294691.031000] sda: assuming drive cache: write through
[4294691.034000] ts: Compaq touchscreen protocol output
[4294691.051000] SCSI device sda: 160836480 512-byte hdwr sectors (82348 MB)
[4294691.051000] sda: assuming drive cache: write through
[4294691.051000]  sda: sda1
[4294691.070000] sd 0:0:0:0: Attached scsi disk sda
[4294691.144000] sd 0:0:0:0: Attached scsi generic sg0 type 0
[4294694.137000] Linux agpgart interface v0.101 (c) Dave Jones
[4294694.148000] agpgart: Detected VIA KT266/KY266x/KT333 chipset
[4294694.159000] agpgart: AGP aperture is 128M @ 0xe0000000
[4294694.422000] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[4294694.429000] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[4294694.474000] Linux Tulip driver version 1.1.13 (December 15, 2004)
[4294694.474000] ACPI: PCI Interrupt 0000:00:07.0[A] -> GSI 18 (level, low) -> IRQ 185
[4294694.475000] tulip0:  MII transceiver #1 config 1000 status 786d advertising 01e1.
[4294694.479000] eth0: ADMtek Comet rev 17 at 0001e400, 00:50:BF:1E:93:C4, IRQ 185.
[4294694.663000] gameport: EMU10K1 is pci0000:00:08.1/gameport0, io 0xec00, speed 1193kHz
[4294695.177000] nvidia: module license 'NVIDIA' taints kernel.
[4294695.184000] ACPI: PCI Interrupt 0000:01:00.0[A] -> GSI 16 (level, low) -> IRQ 193
[4294695.185000] NVRM: loading NVIDIA Linux x86 Kernel Module  1.0-8762  Mon May 15 13:06:38 PDT 2006
[4294695.494000] irda_init()
[4294695.494000] NET: Registered protocol family 23
[4294695.563000] ACPI: PCI Interrupt 0000:00:08.0[A] -> GSI 19 (level, low) -> IRQ 201
[4294695.838000] parport: PnPBIOS parport detected.
[4294695.838000] parport0: PC-style at 0x378 (0x778), irq 7, dma 3 [PCSPP,TRISTATE,COMPAT,EPP,ECP,DMA]
[4294695.846000] input: PC Speaker as /class/input/input2
[4294695.882000] Floppy drive(s): fd0 is 1.44M
[4294695.897000] FDC 0 is a post-1991 82077
[4294698.056000] lp0: using parport0 (interrupt-driven).
[4294698.107000] NET: Registered protocol family 17
[4294698.119000] sbp2: $Rev: 1306 $ Ben Collins <bcollins@debian.org>
[4294698.119000] ieee1394: sbp2: Driver forced to serialize I/O (serialize_io=1)[4294698.119000] ieee1394: sbp2: Try serialize_io=0 for better performance
[4294698.348000] Adding 851404k swap on /dev/hda5.  Priority:-1 extents:1 across:851404k
[4294698.757000] md: md driver 0.90.3 MAX_MD_DEVS=256, MD_SB_DISKS=27
[4294698.757000] md: bitmap version 4.39
[4294699.510000] device-mapper: 4.4.0-ioctl (2005-01-12) initialised: dm-devel@redhat.com
[4294699.922000] NET: Registered protocol family 10
[4294699.922000] lo: Disabled Privacy Extensions
[4294699.923000] IPv6 over IPv4 tunneling driver
[4294700.004000] cdrom: open failed.
[4294700.067000] 0000:00:07.0: tulip_stop_rxtx() failed (CSR5 0xfc664010 CSR6 0xff972117)
[4294700.067000] eth0: Setting full-duplex based on MII#1 link partner capability of 45e1.
[4294700.372000] cdrom: open failed.
[4294700.381000] cdrom: open failed.
[4294701.103000] FAT: bogus number of reserved sectors
[4294701.103000] VFS: Can't find a valid FAT filesystem on dev sda1.
[4294707.379000] ACPI: Power Button (FF) [PWRF]
[4294707.379000] ACPI: Power Button (CM) [PWRB]
[4294707.379000] ACPI: Sleep Button (CM) [SLPB]
[4294707.543000] ibm_acpi: ec object not found
[4294707.577000] pcc_acpi: loading...
[4294710.333000] eth0: no IPv6 routers present
[4294713.249000] ppdev: user-space parallel port driver
[4294713.662000] agpgart: Found an AGP 2.0 compliant device at 0000:00:00.0.
[4294713.662000] agpgart: Putting AGP V2 device at 0000:00:00.0 into 4x mode
[4294713.662000] agpgart: Putting AGP V2 device at 0000:01:00.0 into 4x mode
[4294714.619000] apm: BIOS version 1.2 Flags 0x03 (Driver version 1.16ac)
[4294714.619000] apm: overridden by ACPI.
[4294721.584000] Bluetooth: Core ver 2.8
[4294721.584000] NET: Registered protocol family 31
[4294721.584000] Bluetooth: HCI device and connection manager initialized
[4294721.584000] Bluetooth: HCI socket layer initialized
[4294721.624000] Bluetooth: L2CAP ver 2.8
[4294721.624000] Bluetooth: L2CAP socket layer initialized
[4294721.630000] Bluetooth: RFCOMM socket layer initialized
[4294721.630000] Bluetooth: RFCOMM TTY layer initialized
[4294721.630000] Bluetooth: RFCOMM ver 1.7
[4294838.526000] NTFS driver 2.1.25 [Flags: R/O MODULE].
[4294838.783000] NTFS volume version 3.1.
[4312363.991000] agpgart: Found an AGP 2.0 compliant device at 0000:00:00.0.
[4312363.991000] agpgart: Putting AGP V2 device at 0000:00:00.0 into 4x mode
[4312363.992000] agpgart: Putting AGP V2 device at 0000:01:00.0 into 4x mode
[4329904.728000] SysRq : HELP : loglevel0-8 reBoot tErm Full kIll saK showMem Nice powerOff showPc unRaw Sync showTasks Unmount
[4329904.757000] SysRq : HELP : loglevel0-8 reBoot tErm Full kIll saK showMem Nice powerOff showPc unRaw Sync showTasks Unmount
[4329904.787000] SysRq : HELP : loglevel0-8 reBoot tErm Full kIll saK showMem Nice powerOff showPc unRaw Sync showTasks Unmount
[4329906.584000] agpgart: Found an AGP 2.0 compliant device at 0000:00:00.0.
[4329906.585000] agpgart: Putting AGP V2 device at 0000:00:00.0 into 4x mode
[4329906.585000] agpgart: Putting AGP V2 device at 0000:01:00.0 into 4x mode
[4341173.618000] NTFS volume version 3.1.
[4372899.343000] NTFS-fs error (device hdb1): ntfs_ucstonls(): Unicode name contains characters that cannot be converted to character set cp437.  You might want to try to use the mount option nls=utf8.
[4372899.343000] NTFS-fs warning (device hdb1): ntfs_filldir(): Skipping unrepresentable inode 0x2ead.

```


Hopefully, that's somewhat helpful. I can see that I would need to change the mount option to nsl=utf8, but I have no idea how to do that.

---

### Post by richbarna on 2006-06-05
How about aysiu's guide ?
[http://www.psychocats.net/ubuntu/mountwindows.php]("http://www.psychocats.net/ubuntu/mountwindows.php")

---

### Post by aktiwers on 2006-06-05
[quote=richbarna]How about aysiu's guide ?
[http://www.psychocats.net/ubuntu/mountwindows.php]("http://www.psychocats.net/ubuntu/mountwindows.php")[/quote]

Thanks, but this still doesnt work for me.

No matter what I do, I always come back the the error message:
> 
mount: /dev/sdb5 already mounted or /media/250gb busy

I tried to unmount it 10 times, and remount.. but I always get that message.

Any ideas how to get pasts this?

---

### Post by u.b.u.n.t.u on 2006-06-05
aktiwers  hang in there!

Can you test your HDD on another ubuntu box?

Do you have another HDD to test on your ubuntu?

It took me over a week to learn how to add a storage HDD. That was a Seagate 160GB. I formated it to ext3. Then mounted it in /media/storage. It works like a dream. I used Disk Manager, Gparted, and fstab variously to achieve this.

Oh and I learned it all with the help of our ubuntu community here.

:-D

---

### Post by u.b.u.n.t.u on 2006-06-05
aktiwers can you please post your fstab here?

---

### Post by aktiwers on 2006-06-05
[quote=u.b.u.n.t.u]aktiwers can you please post your fstab here?[/quote]

Thanks

Here it is:

> # /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/sda2       /               ext3    defaults,errors=remount-ro 0       1
/dev/sda1       /media/sda1     ext3    defaults        0       2
/dev/sda5       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdd        /media/cdrom1   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0
/dev/sdc        /media/usb0     auto    rw,user,noauto  0       0
/dev/sdb5       /250gb ntfs nls=utf8,umask=0222 0 0

The last line is the harddisc im having trouble with.  And I just added that line again, using aysiu's guide.

I think it, that I have another 150gb harddisc that I could mount just fine. and my Sda1 also got mounted fine!

On Breezy, I installed the newest Kernel, and then I couldnt access my sdb5 harddrisc anymore. And now its impossible for me to mount and umount it!

I keep getting this error I posted above.

 			 				 mount: /dev/sdb5 already mounted or /media/250gb busy

And it doesnt matter if I use the  /media/250gb folder.. any other folder will produce the same error with the .. what ever folder I choose.

Thanks a lot for the help so fare. I hope we can get this solved. Tell me if I need to post more information please.

---

### Post by aktiwers on 2006-06-05
** Bump **

---

### Post by anaconda on 2006-06-05
can you access your sdb5 from windows? I mean is it working properly anywhere?

OR 

can knoppix LiveCD autodetect and automount it? Where does knoppix mount it?

OR

Is it a SATA drive? or IDE?  if it is IDE then it is /dev/hdX not /dev/sdX

Just my 5 cents...

---

### Post by aktiwers on 2006-06-05
Thanks Anaconda.

1) I dont have Windows, but when I had, Yes it worked fine!
2) Yes I have booted manytimes with Knoppix, and it has always been automounted. I have never checked where it gets mounted? Tell me if this info is needed, then I will check.
3) Its SATA drive.

Thanks.

Any suggestions?

---

### Post by anaconda on 2006-06-05
1. Your disk could be corrupted. can you try it in another machine. or if it works with knoppix? Does it still work in knoppix?

2. Yes it could help. Knoppix is based on debian like ubuntu, and it mounts the drives the same way to same places. exept knoppix mounts them to /mnt/sdaX instead of /media/sdaX. 
anyway, whenever I have had problems, I have looked where/how knoppix mounts them (if it can) and copied from there.. You can check knoppix fstab-file if it handles your drive differently etc.. or if it mounts your SATA drive to /mnt/sdd5 instead of sdb5 etc.. it can be really helpful.

---

### Post by CompShrink on 2006-06-05
[QUOTE=hotstovejer]I'm getting the exact same thing. I have a 200gig drive that says that it's mounted, but I can't see anything on, cause it can't pmount it.

Here's what my dmesg looks like.
*Clipped*

Hopefully, that's somewhat helpful. I can see that I would need to change the mount option to nsl=utf8, but I have no idea how to do that.[/QUOTE]
Ok, in a terminal, type in:

gksudo gedit /etc/fstab

go down to the line that looks something like
/dev/hdb1 /media/SOMETHING ntfs defaults 0 0

If there's something other than defaults before the 0 0, leave it and add ,nls=utf8 with no space in betweeen. If there's just default, then delete default and write in nls=utf8

Then, in the terminal again, try:

sudo umount /dev/hdb1
sudo mount -a

Tell me if that works or not.

And aktiwers, I agree with what anaconda said, try copying the line from knoppix.

---

### Post by aktiwers on 2006-06-05
Thanks for the tip..  it says:

/dev/sdb5       /250gb ntfs nls=utf8,umask=0222 0 0

should I remove umask then?

I will check to see if I can find my knoppix CD, then I will give the info from that.

Thanks a lot so fare! Other suggestions are still welcome.

---

### Post by u.b.u.n.t.u on 2006-06-05
```
/dev/sdb5 /250gb ntfs nls=utf8,umask=0222 0 0 
```

My 160GB HDD was also NTFS. It had all of my data on it. I was unable to mount it and therefore threw it in an XP box, networked, transfered the data to my ubuntu HDD, then out of the XP box and into the ubuntu box, ext3 it, mounted it no problem. All working grand now.

So the short of the long is, I could not mount my 160GB HDD as it was, NTFS.

Also, all of my data was date corrupted. All the dates became 2 January 2007!!! Unbelievable! Thankfully however I have DVD backups. So I STRONGLY recommend that you do a DVD backup too.

With all my files being 2 January 2007, they are rendered largely useless. I will need copy everything over from DVD now and hope the time warp date change doesn't happen again.

---

### Post by catlett on 2006-06-05
Hey Aktiwers,
Since you have nothing to loose do you want to try one more thing? 
First make a new directory in /media ```
sudo mkdir /media/250gb
``` Next replace your current /etc/fstab entry with this one 
```
/dev/sdb5  /media/250gb  ntfs ro,auto,user,exec  0  0
```
Restart and see what happens. Just so you know. I'm making the point in media because it wil put an icon on the desktop. ntfs is obviously the file system. And I'm putting in exact comands instead of defaults. They are ro = read only (because it is ntfs), auto = automatically mount on startup, user = user and not just root can access it, exec = enables you to execute binaries from that file, 0  0 = the first is the dump option and the second is the filesystem check option.
Can't hurt but might help.

---

### Post by MetalMusicAddict on 2006-06-05
I was gonna post the same thing catlett. I dont think the drive likes being **/250gb**. I think thats gonna work.

---

### Post by hotstovejer on 2006-06-05
I THINK I may have found out what needed to be found out!

When I was getting that stupid pmount error, I was beatin my head against a wall. Then, I remembered that this wasn't winblows, and I knew that there had to be SOME file referencing that.

So I was pokin thru my etc dir, and found a file called pmount.allow. Thought that might provide some help.

Here is what I found.```
# /etc/pmount.allow
# pmount will allow users to additionally mount all devices that are
# listed here.
```

So I listed my drive, and VIOLA! It worked! 

Now I just need to know how to get it to write... but I assume that's a permissions issue.

Hope this helps!

Jeremy

---

### Post by anaconda on 2006-06-06
can you post the output of

sfdisk -l  /dev/sdb

It will print the partition table of your 250GB-disk

If you dont have sfdisk installed install it using eg. synaptic..

Sometimes windows can make corrupted or nonstandard partition table, which can work in windows, but not in ubuntu.

I once had a USB-stick, which worked in windows, but its partition table was wery strange to say the least. After fixing it started to work in linux too..

---

### Post by aktiwers on 2006-06-06
Hi again!

Wow, thanks a lot for all the replys! I just found my Knoppix CD and again this Hard disc got automounted fine! Here is the Fstab from Knoppix:

> /proc      /proc       proc   defaults            0 0
/sys       /sys        sysfs  noauto              0 0
/dev/pts   /dev/pts    devpts mode=0622           0 0
/dev/fd0   /mnt/auto/floppy auto   user,noauto,exec,umask=000    0 0
/dev/cdrom /mnt/auto/cdrom  auto   user,noauto,exec,ro 0 0
/dev/cdrom1 /mnt/auto/cdrom1  auto   users,noauto,exec,ro 0 0
# Added by KNOPPIX
/dev/sda1 /mnt/sda1 ext3 noauto,users,exec 0 0
# Added by KNOPPIX
/dev/sda2 /mnt/sda2 ext3 noauto,users,exec 0 0
# Added by KNOPPIX
/dev/sda5 none swap defaults 0 0
# Added by KNOPPIX
** /dev/sdb5 /mnt/sdb5 ntfs noauto,users,exec,ro,umask=000,uid=knoppix,gid=knoppix 0 0** 
> Hey Aktiwers,
Since you have nothing to loose do you want to try one more thing? 
First make a new directory in /media      Code:
     [LEFT]sudo mkdir /media/250gb[/LEFT]
  
 Next replace your current /etc/fstab entry with this one 
     Code:
     [LEFT]/dev/sdb5  /media/250gb  ntfs ro,auto,user,exec  0  0[/LEFT]
  
 Restart and see what happens. Just so you know. I'm making the point in media because it wil put an icon on the desktop. ntfs is obviously the file system. And I'm putting in exact comands instead of defaults. They are ro = read only (because it is ntfs), auto = automatically mount on startup, user = user and not just root can access it, exec = enables you to execute binaries from that file, 0 0 = the first is the dump option and the second is the filesystem check option.
Can't hurt but might help. 
I also tried this, but sadly it didnt work either. Thanks for the suggestion.
 
> can you post the output of

sfdisk -l  /dev/sdb

It will print the partition table of your 250GB-disk
 
It looks like this:

> aktiwers@ubuntu:~$ sfdisk -l /dev/sdb
/dev/sdb: Permission denied

sfdisk: cannot open /dev/sdb for reading
aktiwers@ubuntu:~$ sudo sfdisk -l /dev/sdb
Password:

Disk /dev/sdb: 30401 cylinders, 255 heads, 63 sectors/track
Units = cylinders of 8225280 bytes, blocks of 1024 bytes, counting from 0

   Device Boot Start     End   #cyls    #blocks   Id  System
/dev/sdb1          1   30400   30400  244188000    f  W95 Ext'd (LBA)
/dev/sdb2          0       -       0          0    0  Empty
/dev/sdb3          0       -       0          0    0  Empty
/dev/sdb4          0       -       0          0    0  Empty
/dev/sdb5          1+  30400   30400- 244187968+   7  HPFS/NTFS
aktiwers@ubuntu:~$
 
Okay, this is all. But the Hard drive is still not mounted. **Hotstovejer **could you be a little more specific about what you did? 

Thanks all so fare!

---

### Post by hotstovejer on 2006-06-06
Sure. It was all kinda easy, once I stopped smacking my head against the wall ](*,) 

You can do it either via Gnome, or the terminal, but I am going to list how I did it thru the terminal

When I tried to open the file with sudo via Gnome, it kinda hung, so do it this way.
```
sudo gedit /etc/pmount.allow
```

Then, you will see what I posted earlier. Just add your device in there, such as /dev/hdb1 (insert your own device name), save the file, and then ```
sudo mount -a
```

After that, everything should be cool.

Jeremy

---

### Post by aktiwers on 2006-06-06
[quote=hotstovejer]Sure. It was all kinda easy, once I stopped smacking my head against the wall ](*,) 

You can do it either via Gnome, or the terminal, but I am going to list how I did it thru the terminal

When I tried to open the file with sudo via Gnome, it kinda hung, so do it this way.
```
sudo gedit /etc/pmount.allow
``` 
Then, you will see what I posted earlier. Just add your device in there, such as /dev/hdb1 (insert your own device name), save the file, and then ```
sudo mount -a
``` 
After that, everything should be cool.

Jeremy[/quote]

Okey thanks, I just tried it, but sadly still got the same error message.

> aktiwers@ubuntu:~$ sudo gedit /etc/pmount.allow
Password:
aktiwers@ubuntu:~$ sudo mount -a
mount: /dev/sdb5 already mounted or /media/250gb busy
aktiwers@ubuntu:~$


Any other suggestions? Please have a look at my newest post above.

Thanks

---

### Post by u.b.u.n.t.u on 2006-06-06
This may well be a bug. Just an idea.

edit below:

aktiwers does your HDD have to be NTFS? Are you able to backup your data to DVD, then check it is all safe, then format to ext3 and try again? That is what I had to do. Perhaps the problem is with the file system being NTFS?

---

### Post by aktiwers on 2006-06-06
I know NTFS is a bad filesystem, atleast for Linux. My problem is that I dont have any place to back this up. Dont even have a DVD burner.

It just, it worked on my fresh installed Breezy, only after installing a new kernel messed it up. So I hoped after a apt-get dist-upgrade to dapper, would make it easyer. But im having the exact same problem as I had after installing the new kernel (on Breezy).
Strange, Im I really the only one who ever got this error?
** mount: /dev/sdb5 already mounted or /media/250gb busy**

Or is there a Usual way to fix it? No one has any idea what to do? I hope I dont have to reinstall Dapper from scrats, as everything else here is running like a dream!

Any Help will be very appriciated! And thanks alot so fare. :)

---

### Post by Phasmagon on 2006-06-06
[QUOTE=aktiwers]Thanks Anaconda.

1) I dont have Windows, but when I had, Yes it worked fine!
2) Yes I have booted manytimes with Knoppix, and it has always been automounted. I have never checked where it gets mounted? Tell me if this info is needed, then I will check.
3) Its SATA drive.

Thanks.

Any suggestions?[/QUOTE]
In your other post you state that you use a custom kernel. It is possible that you have not configured it correctly? Did you try to use the latest stable kernel available in the repos?

---

### Post by catlett on 2006-06-06
I found this in a CentOS mailing thread. He had the same error as you "tried to mount and it said mount was busy". He finaly replied and said he fixed it. This is what he said. It is beyond me, but hopefully Azz or someone like him will no what they are talkiong about. And hopefully it isn't CentOS specific and it will work with Ubuntu.
> I ran dmsetup remove_all then it mounted.

how can I disable dmsetup at boot?
It came from this thread [http://lists.centos.org/pipermail/centos/2006-February/060989.html](http://lists.centos.org/pipermail/centos/2006-February/060989.html)

For the heck of it can you run > mount and see what the output is. I'm curious if it says anything about sdb5 since it comes up busy.


P.S. I ran dmsetup  man and got this. There is alot more to the man but just to give an idea.
> 
DESCRIPTION
       dmsetup manages logical devices  that  use  the  device-mapper  driver.
       Devices are created by loading a table that specifies a target for each
       sector (512 bytes) in the logical device.

       The first argument to dmsetup is a command.  The second argument is the
       logical device name or uuid.

       Invoking the command as devmap_name is equivalent to
       dmsetup info -c --noheadings -j major -m minor.


---

### Post by catlett on 2006-06-06
I had an idea while we see if someone understands dmsetup better. How about you setup /etc/fstab with the noauto function. This will keep it from being mounted on startup. Then give the comand to mount it and see what happens. Hopefully noauto will keep away the "busy" error you keep getting.
So change your /etc/fstab one last time to this entry
```
/dev/sdb5  /media/250gb  ntfs ro,noauto,user,exec  0  0
```
Then restart and when you get back to the desktop enter this in the terminal.
```
sudo mount /dev/sdb5 -t ntfs /media/250gb
``` This manually mounts the partition for one session. My main reason for trying this is to see if making the /etc/fstab value "noauto" will keep the partition unmounted and therefore it won't be busy when you give the mount command .
If this has an error I don't know what to say:!:  Is it a dapper bug? My final suggestion would be to try the Dapper Live cd instead of Knoppix. Then see if Daper Live could mount it. If your lucky and it does, copy the dapper live /etc/fstab and try it in dapper regular. Good luck.

---

### Post by aktiwers on 2006-06-06
> aktiwers@ubuntu:~$ mount
/dev/sda2 on / type ext3 (rw,errors=remount-ro)
proc on /proc type proc (rw)
/sys on /sys type sysfs (rw)
varrun on /var/run type tmpfs (rw)
varlock on /var/lock type tmpfs (rw)
procbususb on /proc/bus/usb type usbfs (rw)
udev on /dev type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
devshm on /dev/shm type tmpfs (rw)
/dev/sda1 on /media/sda1 type ext3 (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw)
aktiwers@ubuntu:~$

There goes the output of mount.

Thanks Catlett, im gonna try what you just suggested in you last post. Hopefully someone will understand the stuff from CentOS, and explain what thats all about, because I dont really get it either :D

Im gonna try what you said about the noauto now, and will report back.

Thanks alot for all this help! Hope we get it solved :)

---

### Post by aktiwers on 2006-06-06
> aktiwers@ubuntu:~$ sudo mount /dev/sdb5 -t ntfs /media/250gb
Password:
mount: /dev/sdb5 already mounted or /media/250gb busy
aktiwers@ubuntu:~$ u:~$
bash: u:~$: command not found
aktiwers@ubuntu:~$ sudo mount /dev/sdb5 -t ntfs /media/wd250GB
mount: /dev/sdb5 already mounted or /media/wd250GB busy
aktiwers@ubuntu:~$

Sadly it didnt work, also tryid with another folder I created in there (wd250GB), just to make sure its not the folder that is messed up.

Hmm..  Hope someone knows about that CentOS stuff, that might work.

Thanks so fare :)

---

### Post by catlett on 2006-06-06
[QUOTE=aktiwers]Sadly it didnt work, also tryid with another folder I created in there (wd250GB), just to make sure its not the folder that is messed up.

Hmm..  Hope someone knows about that CentOS stuff, that might work.

Thanks so fare :)[/QUOTE]
I'm stumped Aktiwers.:confused: :mad: :???: :-s I don't know what else to do. There is something more going on but I don't know what. All things being normal the mounting should have worked.
If I get a handle on the CentOS thread I'll post. Until then good luck and I hope someone pops up who understands dmsetup.

---

### Post by aktiwers on 2006-06-06
[quote=catlett]I'm stumped Aktiwers.:confused: :mad: :???: :-s I don't know what else to do. There is something more going on but I don't know what. All things being normal the mounting should have worked.
If I get a handle on the CentOS thread I'll post. Until then good luck and I hope someone pops up who understands dmsetup.[/quote]

Thanks alot Catlett! You have been a great help, lets see of someone else can break this thing. Im lost ](*,)

Anyone else has an idea?

---

### Post by u.b.u.n.t.u on 2006-06-06
Can you use a live CD to facilitate the transfer of your data over to your ubuntu HDD? (Check the dates are correct - see my earlier post in your thread). Then when all is safe just format your HDD to ext3?

Perhaps now would be a good time to consider alternative methods?

---

### Post by CompShrink on 2006-06-06
u.b.u.n.t.u, it sounds like he doesn't have enough unused disk space to move stuff off the NTFS drive.

The knoppix line has nothing special. Just to be sure,  could you try typing umask in a terminal and tell me what number it gives you?

---

### Post by aktiwers on 2006-06-06
Yes Compshrink you are right, I dont have anywhere to take the back up.. (its almost 230gb).

> aktiwers@ubuntu:~$ umask
0022
aktiwers@ubuntu:~$


This is what it says?

Thanks a lot all for not giving up on me :)

---

### Post by u.b.u.n.t.u on 2006-06-06
[QUOTE=aktiwers]Yes Compshrink you are right, I dont have anywhere to take the back up.. (its almost 230gb).



This is what it says?

Thanks a lot all for not giving up on me :)[/QUOTE]

Playing with 230GB of data is a big ask. DVDs are 4.7GB so that rules that out. My data on my 160GB HDD fitted on 2 4.7GB DVDs. It was made easier by me deleting over 90% of all my Windows applications.

The problem I had with my 160GB HDD was that ubuntu couldn't read the NTFS even though it was mounted (correctly I think).

There are a number of solutions but none really "easy".

1. wait and hope a solution presents itself so that you can mount your HDD as you intend.

2. format the file system to something else with the data maintained and try that, eg  FAT32 or even ext3 depending on the software (needs XP)

3 a XP box (maybe a friends), attach your 250GB HDD on their machine, network to your ubuntu, buy yourself another 250GB HDD or larger format to ext3 and transfer your data over. (You need to buy another HDD $)

4 install 5.10 and see if that works and then do an internal upgrade to 6.10 (you may need to download 1GB of data or more)

5 review what you have on your 250GB HDD and delete till you can burn such on DVD, 20 DVDs will give you about 90GB+ of data. (You will need a DVD burner and DVDs, again $). DVD burners are not that expensive.

Just some ideas aktiwers for you to consider. I hope you can find a solution but there will come a point in time when you may have to weigh the alternatives.

There are other lateral ideas from others that may be of use to you too.

---

### Post by aktiwers on 2006-06-06
Thanks a lot for you suggestions U.b.u.n.t.u
The problem is that I dont have a DVD burner, dont have DVD cd's and dont have that kind of money.

I think the trick with a friend could do it, but its just sad if there isnt anyway to get around this. I also do this to learn. I think the easyst way to fix this would be a reinstall, but that I really would like to avoid that, as my system is running perfect exactly as I want, accept for this issue.

Will wait a little, and hopefully some guru reads this thread, and has a solution for me :)

But again, thanks a lot for all the help so fare!

---

### Post by u.b.u.n.t.u on 2006-06-06
[QUOTE=aktiwers]Will wait a little, and hopefully some guru reads this thread, and has a solution for me :)[/QUOTE]

Fair enough aktiwers, but just with regards to the "guru" reference, some have already posted here in your thread. All the best with this - maybe "another" guru in this community has an idea lol. :-k

(I suspect it may be a bug of sorts).

---

### Post by anaconda on 2006-06-07
The partition table seems to be OK! (not corrupted))
but I have never partitioned a hard drive, so that it contais no primary partitions.. only 1 extended partition with 1 logical drive...
If I want only 1 partition I always make it a primary one.

It shouldn't be a problem. But has anyone used a hd with no primary partitions succesfully  with ubuntu? It would be interesting to know.

Interesting that knoppix mounted it without problems! That proves that the drive isn't broken. Did you try using the line from knoppix fstab-file (modifying it for ubuntu, no user named knoppix etc.) 
You could try to replace your USB-mounting files (dont know which) from knoppix (it should be compatible.. both are debian based)
but it would be even better, if it works with ubuntu LiveCD

If all else fails, You can probably get it to work by repartitioning (and formatting) it with ubuntu. But I understand, it is not an option cause you cant bacup it anywhere...

I dont think the problem is that your disk is NTFS instead of ext3, because linux can mount ntfs drives without problems. So reformatting it to be ext3 probably wont help. Repartitioning in ubuntu propably would solve the problem. 

It can be done without risking the files in your drive. With sfdisk you could modify your partition table to contain just 1 primary partition which would have exactly the same start and end points as your current partition. IF the start and end poits are exactly the same than they were, then you wouldn't have to format your drive after repartitioning.

And if it wont work, you can get the old extended partition back, by changing the partition settings again with sfdisk, to be exactly as they were. ( it is good to have the outpu of "sfdisk -l /dev/sdb" saved somewhere. it contains all info needed to make changes back, or repairing corrupted partitiontable)

It would be really nice to be able to backup everything before doing anything........ But you would be modifying only the partition-table not touching the files. Partition table is in first 512bytes of the hard-disk. More exactly bytes 488-512 if I remember correctly.. So it should be enough to bacup the first 512bytes. For example with dd in knoppix. And if the cahges don't help you could jus copy the old table back..

---

### Post by Casey_Switzer on 2006-06-07
I'm getting a similar error when I click on my 250g WD HDD (I have two, but am currently only using one) in the file manager:

Unable to mount the selected volume.
error: device /dev/sdc1 is not removable

error: could not execute pmount

Here is my fdisk:

```

casey@casey-desktop:~$ sudo fdisk -l
Password:

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1           1           0    0  Empty
Partition 1 does not end on cylinder boundary.

Disk /dev/sdb: 37.0 GB, 37019566080 bytes
255 heads, 63 sectors/track, 4500 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        4314    34652173+  83  Linux
/dev/sdb2            4315        4500     1494045    5  Extended
/dev/sdb5            4315        4500     1494013+  82  Linux swap / Solaris

Disk /dev/sdc: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1       30401   244196001    c  W95 FAT32 (LBA)


```

---

### Post by CompShrink on 2006-06-08
I know it's a long thread, but as I said before, pmount is for removable media, like cameras, thumbdrives, etc. I had a partition that didn't mount with pmount but mounted fine in a terminal with the normal "sudo mount".

Casey, can you show us what your /etc/fstab file looks like?

Aktiwers, have you tried breezy? I would suggest trying an install of that, see if it reads it, and upgrade it to dapper, like u.b.u.n.t.u suggested.

Anaconda's suggestion seems promising, but I have no experience with that, and sounds dangerous...

---

### Post by ilkerka on 2006-07-08
i think it has something to do with the configuration of ubuntu's kernel(what ever that means just made it up :D ). I have the same problem. I have installed ubuntu to my second empty hdd and i cannot access to my other hdd which contains windows and my backed up data. Using knoppix i had no problem accessing to both of these drives so it has something to do with ubuntu. Hopefully someone can find a solution to this problem.
-------------------------------------------------------------------------
i opened SYSTEM->ADMINISTRATION-> DISKS and when i clicked to my first harddrive and press CHANGE i can see all my files of the unreachable HDD there. After that i tried to access to my unreachable hdd from explorer and now it says "Folder contents cannot be displayed. You do not have the permission....".

---

### Post by CompShrink on 2006-07-08
> **ilkerka said:**
> i opened SYSTEM->ADMINISTRATION-> DISKS and when i clicked to my first harddrive and press CHANGE i can see all my files of the unreachable HDD there. After that i tried to access to my unreachable hdd from explorer and now it says "Folder contents cannot be displayed. You do not have the permission....".
That means only root (the administrator account/mode) can read it.

Try opening a terminal, Applications-> Accesories-> Terminal and type in:
gksudo nautilus

And try opening your other hard disk, the "unreachable hdd." If you can, then it shouldn't be hard to get your regular user access to it also. Let us know.

---

### Post by catlett on 2006-07-08
Try to mount it manually and see what happens. I am asuming windows is on the first partition of the first hard drive. Use these commands to mount windows and put an icon for the hard drive on your desktop.
```
sudo mkdir /media/windows
```
```
sudo mount /dev/hda1 -t ntfs /media/windows
```
If everythinhg is fine an icon will appear on your desktop. Then the next step is to edit your /etc/fstab.
If this worked enter this and copy/paste the contents here (be carefull not to erase the document when you copy/paste, the document is in a state where it can be edited)```
 sudo gedit /etc/fstab
```

---

### Post by ilkerka on 2006-07-08
> **CompShrink said:**
> That means only root (the administrator account/mode) can read it.

Try opening a terminal, Applications-> Accesories-> Terminal and type in:
gksudo nautilus

And try opening your other hard disk, the "unreachable hdd." If you can, then it shouldn't be hard to get your regular user access to it also. Let us know.

thnx man it does work like that. By the way when i mount the disks from Disks Manager its Access Path is "/tmp/disks-conf-sda1"

-----------------------------------------------------------------
catlet i tried the command, it says the device is already mounted. I have used this command "sudo mount /dev/evms/sda1 -t ntfs /media/windows" and windows icon did appear on my desktop. here is the file:


# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/sdb1       /               ext3    defaults,errors=remount-ro 0       1
/dev/sdb5       none            swap    sw              0       0
/dev/hdd        /media/cdrom0   udf,iso9660 user,noauto     0       0

---

### Post by catlett on 2006-07-08
For some reason your windows partition isn't in your /etc/fstab. The file /etc/fstab is the file that tells the system what to mount at startup. You need to edit the file.


> # /etc/fstab: static file system information.
#
# <file system> <mount point> <type> <options> <dump> <pass>
proc /proc proc defaults 0 0
/dev/sdb1 / ext3 defaults,errors=remount-ro 0 1
/dev/sdb5 none swap sw 0 0
/dev/hdd /media/cdrom0 udf,iso9660 user,noauto 0 0
/dev/sda1 /media/windows ntfs  defaults,nls=utf8,umask=007,gid=46 0  I am assuming windows is on sda1. If you know somethiunh I don't then add it in. I don't know what evms is when you mounted earlier. What you need to put here is what drive and partition windows is on.

To edit do these commands. The first will make a backup of the original, just in case. The second will open the file for editing
```
sudo cp /etc/fstab /etc/fstab_backup
```
```
sudo gedit /etc/fstab
```

---

### Post by ilkerka on 2006-07-08
thnx alot mate C:\ works perfectly. i have another partition sda5 so do i continue with the same process with just replacing sda1 with sda5?

---

### Post by catlett on 2006-07-08
Yes basically but the parameters may be different if it isn't ntfs. If it is ntfs you have to make a directory and then an entry
```
sudon mkdir /media/sda5
```
Then add this to your /etc/fstab
> # /etc/fstab: static file system information.
#
# <file system> <mount point> <type> <options> <dump> <pass>
proc /proc proc defaults 0 0
/dev/sdb1 / ext3 defaults,errors=remount-ro 0 1
/dev/sdb5 none swap sw 0 0
/dev/hdd /media/cdrom0 udf,iso9660 user,noauto 0 0
/dev/sda1 /media/windows ntfs defaults,nls=utf8,umask=007,gid=46 0 
/dev/sda5 /media/sda5 ntfs defaults,nls=utf8,umask=007,gid=46 0 
If you need further explanation, this is a decent guide [http://www.tuxfiles.org/linuxhelp/fstab.html](http://www.tuxfiles.org/linuxhelp/fstab.html)

---

### Post by ilkerka on 2006-07-08
thnx alot catlett and everyone, learnt alot from my problem. i hope ubuntu developers will make this operation automated when ubuntu is loading up in the future versions.

---

