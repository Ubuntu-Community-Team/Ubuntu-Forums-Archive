---
title: "[SOLVED] ./configure doesnt work... 'permission denied'"
date: 2007-10-19
forum: Absolute Beginner Talk
---

### Post by NaSiO6 on 2007-10-19
hi!

I tried './configure' ing bitsharp.(You do this to use the libraries, right?). But weirdly i get this permission denied message even though I am in the root mode. According to the instructions I do need to do this.


<Instructions>

BUILDING MONOTORRENT:
------------------------------------------------------------------------------------------------------------

MakeFiles:
To build using the makefiles, just run ./configure; make; make install from the same directory as this
README. You can alter the prefix where MonoTorrent is installed to by passing the --prefix=PATH argument to
configure.

</Instructions>

<err. message>
root@SiGreen:/home/NaSiO6/bitsharp/src# ./configure
bash: ./configure: Permission denied
</err. message>

What am i doing wrong? I even tried pasting it in usr/local directory(read it somewhere on the net).

PS:
Kindly assume that i dont know anything, because... er... well... I dont. I couldnt even build mono for that matter, so i just got it from synaptic.

---

### Post by rsambuca on 2007-10-19
First, I don't think I would be doing this as root.  It really isn't necessary until the last step, but you can use 'sudo' for this.

Also, you will have to install the 'build-essentials' package before you can compile from source code.

---

### Post by Bliepo32 on 2007-10-19
Firstly, what do you mean exactly with 'root mode'? Do you mean that you logged-in as root? Or do you mean that you used sudo?

You could try and boot in recovery mode. This will give you the possibility to become root.

---

### Post by NaSiO6 on 2007-10-19
hi!
sorry for not being descriptive.

well, i do have build-essentials package installed.
i tried it using su. and i tried ./configure when i was logged in as root in the recovery mode as well. but still it doesnt seem to work.
this might sound crazy, but is it possible that somehow './configure' on my system is 'faulty'.

btw when i tried sudo ./configure it said command not found.

thanks!

---

### Post by rsambuca on 2007-10-19
Put the file in a directory owned by a regular user, then you know you don't have to worry about weird permission problems.  Then run it from a regular terminal (ie.  non-root) and see what happens.

---

### Post by bruce89 on 2007-10-19
```
chmod +x configure
```

should fix it. This allows the script to be executed.

> /home/NaSiO6/bitsharp/src

Must be tricky typing that (NaSiO6) to log in.

---

### Post by NaSiO6 on 2007-10-20
hi!

well, it finally worked!

it was throwing permission denied error after the chmod command(but that command DID make a difference-since this time it recognized ./configure without me using su)

although i am still not sure what i did that solved the problem... but random clicking of 'apply permissions to enclosed files' and selecting 'read and write' to others did the trick.

thanks!

---

### Post by Frak on 2007-10-20
**NEVER EVER EVER EVER EVER** run **anything** as root unless you know it comes from a trusted source.

Root is a privilege, use it wisely.

Also, use sudo, not su. Sudo is safer because it's temporary.

---

