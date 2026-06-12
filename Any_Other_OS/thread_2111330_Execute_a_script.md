---
title: "Execute a script"
date: 2013-02-01
forum: Any Other OS
---

### Post by guyfromfl on 2013-02-01
I am trying to figure out what this script is, and run it on Linux Mint LMDE.

The company I am working for is thinking about buying this sound board, and it comes with a "Linux App" tested on Ubuntu 12.04. The only thing in the archive is a file called XControl.

When I extract it, it has the little purple icon with gears that I thought meant executable.

I Tried to chmod +X it, double click it, ./XControl, sh and bash (just to try) etc etc but it does nothing!

Here is a link to the download page, I am including the link so you don't think I'm up to something strange. I am trying to run the 5th download "XControl Linux App"
[http://www.behringer.com/EN/products/X32.aspx](http://www.behringer.com/EN/products/X32.aspx)

The documentation doesn't explain anything

---

### Post by zealibib slaughter on 2013-02-01
for me it brings up a control board. i downloaded it and double clicked it.

---

### Post by guyfromfl on 2013-02-01
weird.

I guess its a compatibility issue on Linux Mint.

My laptop is running 12.04 so I'll give it a shot when I get home.

I just wanted to make sure that I was doing it right...

Thanks!

---

### Post by srekcahrai on 2013-02-01
As my experience, execute permission (chmod +x or double clicking) doesn't work if the file is located in NTFS system. So, where does your script locate?

---

### Post by xenopeek on 2013-02-01
The XControl file extracts with executable permissions. Double-clicking the extracted XControl file runs perfectly fine on Linux Mint 14, and throws up a control board window. The problem is probably you are missing libraries or have the wrong versions on LMDE. Figure that out.

Here is a dump of "ldd XControl" on my system. Run that on LMDE for your download as well, and hopefully you can figure out which libraries you are missing or have the wrong version for.
```
    linux-gate.so.1 =>  (0xf7778000)
    libX11.so.6 => /usr/lib/i386-linux-gnu/libX11.so.6 (0xf7624000)
    libXext.so.6 => /usr/lib/i386-linux-gnu/libXext.so.6 (0xf7612000)
    libdl.so.2 => /lib/i386-linux-gnu/libdl.so.2 (0xf760c000)
    libfreetype.so.6 => /usr/lib/i386-linux-gnu/libfreetype.so.6 (0xf7572000)
    libpthread.so.0 => /lib/i386-linux-gnu/libpthread.so.0 (0xf7557000)
    librt.so.1 => /lib/i386-linux-gnu/librt.so.1 (0xf754e000)
    libstdc++.so.6 => /usr/lib/i386-linux-gnu/libstdc++.so.6 (0xf7465000)
    libm.so.6 => /lib/i386-linux-gnu/libm.so.6 (0xf7438000)
    libgcc_s.so.1 => /lib/i386-linux-gnu/libgcc_s.so.1 (0xf741a000)
    libc.so.6 => /lib/i386-linux-gnu/libc.so.6 (0xf7270000)
    libxcb.so.1 => /usr/lib/i386-linux-gnu/libxcb.so.1 (0xf724e000)
    /lib/ld-linux.so.2 (0xf7779000)
    libz.so.1 => /lib/i386-linux-gnu/libz.so.1 (0xf7235000)
    libXau.so.6 => /usr/lib/i386-linux-gnu/libXau.so.6 (0xf7230000)
    libXdmcp.so.6 => /usr/lib/i386-linux-gnu/libXdmcp.so.6 (0xf7229000)

```Edit: and as you can see in the above this is a 32-bit program. So if you are running LMDE 64-bit make sure you have ia32-libs-multiarch installed.

---

