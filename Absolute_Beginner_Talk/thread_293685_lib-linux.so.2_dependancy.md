---
title: "lib-linux.so.2 dependancy"
date: 2006-11-05
forum: Absolute Beginner Talk
---

### Post by Silverfox on 2006-11-05
Howdy Folks. Like everyone else posting here, I've finally taken the plunge into Linux and decided on Ubuntu 6.06 LTS(long journey...Fortran>Basic>AmigaDOS>lost in Windoze black hole for too long>linux). Installation and configurtation went seamlessly and I've got a well configured LAMP server.

I'm trying to run an older game server (BattleField 1942) and I can't get it to run. I think I've narrowed it down to a dependancy in the bf1942 server binary on "ld-linux.so.2", which I believe is an older Glib compile library. Can I just drop the ld-linux.so.2 file into my */lib directory? Or should I look for some small utility that uses it and install it with Aptitude? Or alternatively, create a symbolic link in */lib to the latest version of said file? I'm a complete n00b with linux (learning fast though), and I'm reluctant to break my system after getting it configured the way I like. Can I experiment with these options?](*,) I've been trying to get this server program running for days (good learning experience, though), and I'm out of ideas.

Thanks in advance for any help or advice you folks can send my way!

---

### Post by po0f on 2006-11-05
Silverfox,

I can't see how your problem running bf1942 server is related to ld-linux.so.2.  All this program does is load shared libraries into memory.  Your issue is somewhere else.  If you could post errors you are getting, we might be able to get them resolved for you.

---

### Post by Silverfox on 2006-11-05
Here's what's happening, verbatim. I've solved the initial dependancy issue by installing the required library, but now it won't start because it isn't finding a lib that is actually there (a dynamic link to libncurses.so.5.5 actually. What follows is exactly what I'm getting in my terminal.

```

silver@RDES-Gamers:~/bf1942$ ls
bf1942_lnxded          bfpridaemon   fixinstall.sh  pb              readmes
bf1942_lnxded.dynamic  bfsmd         LICENSE        playermenu.con  start.sh
bf1942_lnxded.static   bfsmd.static  mods           README          UPDATE-1.61-INSTALL.txt
silver@RDES-Gamers:~/bf1942$ ./start.sh +statusMonitor 1
./start.sh: using statically linked binary
./bf1942_lnxded: error while loading shared libraries: libncurses.so.5: cannot open shared object file: No such file or directory
silver@RDES-Gamers:~/bf1942$ ldd start.sh
        not a dynamic executable
silver@RDES-Gamers:~/bf1942$ ldd bf1942_lnxded.dynamic
        linux-gate.so.1 =>  (0xffffe000)
        libdl.so.2 => /lib32/libdl.so.2 (0x55572000)
        [B]libncurses.so.5 => not found
        libstdc++.so.5 => not found[/B]
        libm.so.6 => /lib32/libm.so.6 (0x55576000)
        libgcc_s.so.1 => /usr/lib32/libgcc_s.so.1 (0x55598000)
        libpthread.so.0 => /lib32/libpthread.so.0 (0x555a3000)
        libc.so.6 => /lib32/libc.so.6 (0x555b5000)
        /lib/ld-linux.so.2 (0x55555000)
silver@RDES-Gamers:~/bf1942$ ldd bf1942_lnxded.static
        linux-gate.so.1 =>  (0xffffe000)
        libdl.so.2 => /lib32/libdl.so.2 (0x55572000)
        libm.so.6 => /lib32/libm.so.6 (0x55575000)
        **libncurses.so.5 => not found**
        libpthread.so.0 => /lib32/libpthread.so.0 (0x55598000)
        libc.so.6 => /lib32/libc.so.6 (0x555aa000)
        /lib/ld-linux.so.2 (0x55555000)
silver@RDES-Gamers:~/bf1942$ cd /lib
silver@RDES-Gamers:/lib$ ls libn*
libncurses.so.5     libnsl.so.1             libnss_files-2.3.6.so   libnss_nisplus-2.3.6.so
**libncurses.so.5.5**   libnss_compat-2.3.6.so  libnss_files.so.2       libnss_nisplus.so.2
libncursesw.so.5    libnss_compat.so.2      libnss_hesiod-2.3.6.so  libnss_nis.so.2
libncursesw.so.5.5  libnss_dns-2.3.6.so     libnss_hesiod.so.2
libnsl-2.3.6.so     libnss_dns.so.2         libnss_nis-2.3.6.so
silver@RDES-Gamers:/lib$

```

---

### Post by po0f on 2006-11-05
Silverfox,

I guess this is on a 64-bit system, huh?  You aren't making this easy for me.  ;)

What happens when you try to link libncurses.so.5 to libncurses.so?  I know it's asking for the former, but it might work.  As I hinted at above, I don't own a 64-bit system, are there any 32-bit compatibility libraries you are maybe missing, like [this one](http://packages.ubuntu.com/edgy/libs/lib32ncurses5), perhaps?

To resolve the libstdc++.so.5 error, install [this package](http://packages.ubuntu.com/edgy/base/libstdc++5):
```
$ sudo aptitude install libstdc++5
```

---

### Post by Silverfox on 2006-11-05
Oh, sorry my friend. I neglected to share that tidbit of info. Yes, it's the AMD64 package. The libstdc++5 package already is installed, but the dynamic server binary doesn't appear to need it, just the static one. 

Just added the 32 bit libraries, you're a genius. That's fixed it, the server is running as we speak. Thanks kindly for the gentle prod in the correct direction. What I'd heard about the Ubuntu community appears to be true! :cool: :D \\:D/ :biggrin: 

Thanks again!

---

