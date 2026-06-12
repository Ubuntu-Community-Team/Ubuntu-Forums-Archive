---
title: "error message about missing library. what should i do?"
date: 2007-06-05
forum: Absolute Beginner Talk
---

### Post by legolas_w on 2007-06-05
Hi
thank you for reading my post
What should i do to resolve this error
```

./setup: error while loading shared libraries: libstdc++-libc6.2-2.so.3: cannot open shared object file: No such file or directory

```

I faced it when i tried to install an application and I have ubuntu 7.04.

Thanks

---

### Post by annda on 2007-06-05
both libstdc and libc are in the repositories. go to synaptic, do a quick search and install them.

p.s. is the application you are trying to install not in the repositories as well?

---

### Post by PetePete on 2007-06-05
you could try
sudo apt-get install cruft

according to packages.ubuntu.org that contains the library you require.

what are you trying to install, is there not a .deb for it?

---

### Post by legolas_w on 2007-06-05
Hi
Thank you for help.
I install them and now here is content of /lib and /usr/lib folder
my setup does not works yet.

```


:/lib$ ls libc* libst*
ls: libst*: No such file or directory
libc-2.5.so     libcfont.so.0.0.0  libcom_err.so.2.1    libcrypt.so.1
libcap.so.1     libcidn-2.5.so     libconsole.so.0      libc.so.6
libcap.so.1.10  libcidn.so.1       libconsole.so.0.0.0  libctutils.so.0
libcfont.so.0   libcom_err.so.2    libcrypt-2.5.so      libctutils.so.0.0.0


```

```

:/usr/lib$ ls libc* libst*
libcaca.so.0                     libcroco-0.6.so.3.0.1
libcaca.so.0.99.0                libcrypto++5.2.so.0
libcairo.so.2                    libcrypto++5.2.so.0.0.0
libcairo.so.2.11.1               libcrypto.so.0.9.8
libcamel-1.2.so.10               libcrypto.so.4
libcamel-1.2.so.10.0.0           libcrypto.so.6
libcamel-provider-1.2.so.10      libcspi.so.0
libcamel-provider-1.2.so.10.0.0  libcspi.so.0.10.11
libcdaudio.so.1                  libcucul.so.0
libcdaudio.so.1.0.0              libcucul.so.0.99.0
libcdda_interface.so.0           libcupsimage.so.2
libcdda_interface.so.0.10.0      libcups.so.2
libcdda_paranoia.so.0            libcurl-gnutls.so.3
libcdda_paranoia.so.0.10.0       libcurl-gnutls.so.3.0.0
libcddb-slave2.so.0              libcurl.so.3
libcddb-slave2.so.0.0.0          libcurl.so.3.0.0
libcdio.so.6                     libstartup-notification-1.so.0
libcdio.so.6.0.1                 libstartup-notification-1.so.0.0.0
libchm.so.1                      libstdc++.so.5
libchm.so.1.0.0                  libstdc++.so.5.0.7
libcompface.so.1                 libstdc++.so.6
libcompface.so.1.0.0             libstdc++.so.6.0.8
libconnectionmanager.so.0        libstlport.so.5.1
libconnectionmanager.so.0.0.0    libstlport.so.5.1.0
libcroco-0.6.so.3

```

---

