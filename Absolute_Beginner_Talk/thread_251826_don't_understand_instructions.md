---
title: "don't understand instructions"
date: 2006-09-05
forum: Absolute Beginner Talk
---

### Post by crunchystrike on 2006-09-05
ok, i have read the instructions at [http://www.linux-gamers.net/modules/wiwimod/index.php?page=HOWTO+Steam&back=HOWTO+INDEX+Wine+Games](http://www.linux-gamers.net/modules/wiwimod/index.php?page=HOWTO+Steam&back=HOWTO+INDEX+Wine+Games)

ok, on the part that tells me: Now run wine without any parameters. When wine is run for the first time, it creates all necessary directories, including your fake C: drive, which is per default located in ~/.wine/drive_c.

how do i run wine without any parameters, and where is .wine/drive_c. located after i run it?

thanks

---

### Post by meng on 2006-09-06
Go to the terminal
wine
That's how to invoke wine without parameters

~ is a shortcut for your home directory, e.g. /home/crunchystrike
so ~/.wine is really /home/crunchystrike/.wine
it is a hidden directory because of the leading .
so you won't see it if you simply
ls
but you will see it if you
ls -a

Similarly, you won't see it in Nautilus unless you enable See Hidden Files (Ctrl-H)

---

### Post by orb9220 on 2006-09-06
To configure wine in term or alt-f2 amd type winecfg
To install as an example dvdshrink in term type  sudo wine dvdshrink32.exe
which would start the installer for dvdshrink.

---

