---
title: "Uninstalling software that is compiled from source..."
date: 2006-04-30
forum: Absolute Beginner Talk
---

### Post by PerpsTherapy on 2006-04-30
Greetings to all.

Just wondering if anyone could tell me how to uninstall software that has been compiled from source. I've installed wxGTK 2.6.3 from source code, but it's causing problems with amule 2.1.1 (amule won't start, it returns "amule: error while loading shared libraries: libwx_gtk2_adv-2.6.so.0: cannot open shared object file: No such file or directory"), so I wanted to uninstall it. What terminal commands are used to achieve this??

Many thanks,

- PerpsTherapy

P.S I searched the forums for information on how to uninstall software on ubuntu, but the threads I found all related to using aptitude or synaptic to uninstall software.

---

### Post by mostwanted on 2006-04-30
[QUOTE=PerpsTherapy]Greetings to all.

Just wondering if anyone could tell me how to uninstall software that has been compiled from source. I've installed wxGTK 2.6.3 from source code, but it's causing problems with amule 2.1.1 (amule won't start, it returns "amule: error while loading shared libraries: libwx_gtk2_adv-2.6.so.0: cannot open shared object file: No such file or directory"), so I wanted to uninstall it. What terminal commands are used to achieve this??

Many thanks,

- PerpsTherapy

P.S I searched the forums for information on how to uninstall software on ubuntu, but the threads I found all related to using aptitude or synaptic to uninstall software.[/QUOTE]

Go to the directory where you extracted the source file to. Run the command:

```
sudo make uninstall
```

Then reinstall amule.

---

### Post by PerpsTherapy on 2006-04-30
Thanks for the reply mostwanted.

I tried what you suggested, but the following was returned:

make: *** No rule to make target `uninstall'.  Stop.

Any ideas??

Thanks,

- PerpsTherapy

---

### Post by syg00 on 2006-04-30
Unfortunately depends on the author.
Check for a readme or some-such; should tell you.
Else check the Makefile - usually reasonably straightforward to work out if it has an uninstall. Have a look for "clean".

---

### Post by PerpsTherapy on 2006-04-30
Thanks for the reply syg00.

Checked out Makefile.in, and there seemed to be instructions there for uninstall and clean as well, but attempting make uninstall or make clean fails with the afore mentioned error.

---

### Post by gingermark on 2006-04-30
In the future, you might want to consider checkinstall.

Instead of typing 'sudo make install' you would type 'sudo checkinstall -D' and a .deb file is created, which makes later removal very easy.

'sudo apt-get install checkinstall' to install it.

---

### Post by cwaldbieser on 2006-04-30
[QUOTE=gingermark]In the future, you might want to consider checkinstall.

Instead of typing 'sudo make install' you would type 'sudo checkinstall -D' and a .deb file is created, which makes later removal very easy.

'sudo apt-get install checkinstall' to install it.[/QUOTE]
If you re-install your package this way, it should put the files in the same place, but then you will be able to uninstall them with synaptic.

---

### Post by xenmax on 2006-04-30
[QUOTE=PerpsTherapy]Checked out Makefile.in, and there seemed to be instructions there for uninstall and clean as well, but attempting make uninstall or make clean fails with the afore mentioned error.[/quote]
Is that "Makefile" or "Makefile.in" ?
If it is "Makefile.in", then you have to do ```
make -f Makefile.in uninstall
``` as make only picks up by default files named GNUmakefile or makefile or Makefile. Anything else and you have to explicitly mention using -f option.
Hope this helps.

---

