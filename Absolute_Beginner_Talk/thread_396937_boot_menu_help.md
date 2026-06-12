---
title: "boot menu help"
date: 2007-03-30
forum: Absolute Beginner Talk
---

### Post by googanhiem on 2007-03-30
Okay,

so i'm trying to set up a dual boot on my old comp

I started by installing xubuntu, played with it for a couple months and really liked it

Then installed windows xp, (just cause)

I used my live cd to get the grub back

then i added this code to the end of menu.lst

```
title		Microsoft Windows
root		(hd0,1)
savedefault
makeactive
chainloader	+1
```


Note: I used (hd0,1) cause its on my second partition, xubuntu's on my first.

Now whenever I click on this Microsoft Windows option, it just quickly flashes black.

Does this mean my MBR is messed? I ran a fixboot on my windows recovery cd to no avail.

Any help would be great!

---

### Post by nixclusive on 2007-03-30
While at the grub menu, enter 'c' for the command line. enter those commands and check the error reported. This much should be enough at the command line:
```
root		(hd0,1)
makeactive
chainloader	+1
```

---

### Post by confused57 on 2007-03-30
nixclusive is right, you could take out the "savedefault", something similar to this:

```
title		Microsoft Windows
rootnoverify	(hd0,1)
makeactive
chainloader	+1
```

---

### Post by googanhiem on 2007-03-30
Thanks for you input.  but I ran those commands, and there was no error report, It just goes

```
grub>root (hd0,1)

grub>makeactive

grub>chainloader +1

grub>
```

as if i have to put in another command

---

### Post by googanhiem on 2007-03-30
also, I was able to run the 

```
boot (0,1)
```

command and start windows from the Grub command-line, so i know that partition still works. Is there any command similar to this that I can add to menu.lst without some kernel error.

---

### Post by dstew on 2007-03-30
You might need to remap your windows partition to grub's hd0. To do this, use the map command on the grub command line or in the menu list before you start the boot sequence:

grub> map (hd0) (hd1)
grub> map (hd1) (hd0)
     
See this in the grub manual:
[http://www.gnu.org/software/grub/manual/html_node/map.html](http://www.gnu.org/software/grub/manual/html_node/map.html)

EDIT: Actually, this advice is wrong. It applies only when windows is on a different disk. Sorry if I confused anyone.

---

### Post by googanhiem on 2007-03-30
Okay, by far the dumbest mistake i've made in months. I capitalized chainloader, thus grub didn't understand the command. Anyways thanks everyone for your help!

---

### Post by confused57 on 2007-03-30
> **googanhiem said:**
> Okay, by far the dumbest mistake i've made in months. I capitalized chainloader, thus grub didn't understand the command. Anyways thanks everyone for your help!
Happens to all of us at one time or another...glad you got it working.  That's why I like to see someone I'm helping "copy & paste" entries or command results, rather than retyping or paraphrasing...sure makes it easier to spot a possible problem.

---

