---
title: "Mplayer lost library?"
date: 2006-11-16
forum: Absolute Beginner Talk
---

### Post by OptimusPrime on 2006-11-16
My Mplayer doesn't open anymore.  When I try to open it with the terminal I get this:

wesley@wesley-laptop:~$ mplayer
mplayer: error while loading shared libraries: libGL.so.1: cannot open shared object file: No such file or directory
wesley@wesley-laptop:~$ gmplayer
gmplayer: error while loading shared libraries: libGL.so.1: cannot open shared object file: No such file or directory

I tried re-installing it, but I get the same error.

---

### Post by taurus on 2006-11-16
Did you happen to upgrade your Dapper recently?  Look in synaptic to see if you have libglade2-0 installed on your machine!

---

### Post by OptimusPrime on 2006-11-16
I did not upgrade dapper, and yes, I do have libglade2-0 installed.  Any other reason this wouldn't work?

---

### Post by taurus on 2006-11-16
What's the output of 

```
ldd /usr/bin/mplayer
```

---

### Post by OptimusPrime on 2006-11-16
linux-gate.so.1 =>  (0xffffe000)
        libdvdread.so.3 => /usr/lib/libdvdread.so.3 (0xb7ece000)
        libmad.so.0 => /usr/lib/libmad.so.0 (0xb7eb7000)
        libvorbis.so.0 => /usr/lib/libvorbis.so.0 (0xb7e8e000)
        libogg.so.0 => /usr/lib/libogg.so.0 (0xb7e89000)
        libdv.so.4 => /usr/lib/libdv.so.4 (0xb7e61000)
        libtheora.so.0 => /usr/lib/libtheora.so.0 (0xb7e28000)
        liblzo.so.1 => /usr/lib/liblzo.so.1 (0xb7e09000)
        libmp3lame.so.0 => /usr/lib/libmp3lame.so.0 (0xb7d67000)
        libxvidcore.so.4 => /usr/lib/libxvidcore.so.4 (0xb7c4b000)
        libpng12.so.0 => /usr/lib/libpng12.so.0 (0xb7c28000)
        libz.so.1 => /usr/lib/libz.so.1 (0xb7c14000)
        libjpeg.so.62 => /usr/lib/libjpeg.so.62 (0xb7bf5000)
        libasound.so.2 => /usr/lib/libasound.so.2 (0xb7b40000)
        libdl.so.2 => /lib/tls/i686/cmov/libdl.so.2 (0xb7b3d000)
        libpthread.so.0 => /lib/tls/i686/cmov/libpthread.so.0 (0xb7b2a000)
        libmpcdec.so.3 => /usr/lib/libmpcdec.so.3 (0xb7b1b000)
        libspeex.so.1 => /usr/lib/libspeex.so.1 (0xb7afe000)
        libfaac.so.0 => /usr/lib/libfaac.so.0 (0xb7aed000)
        libmp4v2.so.0 => /usr/lib/libmp4v2.so.0 (0xb7a50000)
        libstdc++.so.6 => /usr/lib/libstdc++.so.6 (0xb797b000)
        libfreetype.so.6 => /usr/lib/libfreetype.so.6 (0xb7911000)
        libncurses.so.5 => /lib/libncurses.so.5 (0xb78d0000)
        libcdda_interface.so.0 => /usr/lib/libcdda_interface.so.0 (0xb78bd000)
        libcdda_paranoia.so.0 => /usr/lib/libcdda_paranoia.so.0 (0xb78b5000)
        libnsl.so.1 => /lib/tls/i686/cmov/libnsl.so.1 (0xb78a0000)
        libungif.so.4 => /usr/lib/libungif.so.4 (0xb7899000)
        libsmbclient.so.0 => /usr/lib/libsmbclient.so.0 (0xb76eb000)
        libfribidi.so.0 => /usr/lib/libfribidi.so.0 (0xb76dd000)
        libfontconfig.so.1 => /usr/lib/libfontconfig.so.1 (0xb76af000)
        libgtk-x11-2.0.so.0 => /usr/lib/libgtk-x11-2.0.so.0 (0xb73da000)
        libgdk-x11-2.0.so.0 => /usr/lib/libgdk-x11-2.0.so.0 (0xb735d000)
        libatk-1.0.so.0 => /usr/lib/libatk-1.0.so.0 (0xb7344000)
        libgdk_pixbuf-2.0.so.0 => /usr/lib/libgdk_pixbuf-2.0.so.0 (0xb732e000)
        libm.so.6 => /lib/tls/i686/cmov/libm.so.6 (0xb730c000)
        libpangocairo-1.0.so.0 => /usr/lib/libpangocairo-1.0.so.0 (0xb7304000)
        libXext.so.6 => /usr/lib/libXext.so.6 (0xb72f7000)
        libXrender.so.1 => /usr/lib/libXrender.so.1 (0xb72ef000)
        libXinerama.so.1 => /usr/lib/libXinerama.so.1 (0xb72ec000)
        libXi.so.6 => /usr/lib/libXi.so.6 (0xb72e3000)
        libXrandr.so.2 => /usr/lib/libXrandr.so.2 (0xb72e0000)
        libXcursor.so.1 => /usr/lib/libXcursor.so.1 (0xb72d7000)
        libXfixes.so.3 => /usr/lib/libXfixes.so.3 (0xb72d3000)
        libpango-1.0.so.0 => /usr/lib/libpango-1.0.so.0 (0xb729b000)
        libcairo.so.2 => /usr/lib/libcairo.so.2 (0xb7255000)
        libX11.so.6 => /usr/lib/libX11.so.6 (0xb716e000)
        libgobject-2.0.so.0 => /usr/lib/libgobject-2.0.so.0 (0xb7136000)
        libgmodule-2.0.so.0 => /usr/lib/libgmodule-2.0.so.0 (0xb7133000)
        libglib-2.0.so.0 => /usr/lib/libglib-2.0.so.0 (0xb70af000)
        libaa.so.1 => /usr/lib/libaa.so.1 (0xb7095000)
        libGL.so.1 => /usr/lib/libGL.so.1 (0xb6ff5000)
        libXxf86dga.so.1 => /usr/lib/libXxf86dga.so.1 (0xb6fef000)
        libXv.so.1 => /usr/lib/libXv.so.1 (0xb6feb000)
        libXvMC.so.1 => /usr/lib/libXvMC.so.1 (0xb6fe8000)
        libXvMCW.so.1 => /usr/lib/libXvMCW.so.1 (0xb6fe3000)
        libXxf86vm.so.1 => /usr/lib/libXxf86vm.so.1 (0xb6fde000)
        libSDL-1.2.so.0 => /usr/lib/libSDL-1.2.so.0 (0xb6f56000)
        libggi.so.2 => /usr/lib/libggi.so.2 (0xb6f4a000)
        libslang.so.2 => /lib/libslang.so.2 (0xb6e8f000)
        libartsc.so.0 => /usr/lib/libartsc.so.0 (0xb6e89000)
        libgthread-2.0.so.0 => /usr/lib/libgthread-2.0.so.0 (0xb6e85000)
        libesd.so.0 => /usr/lib/libesd.so.0 (0xb6e7b000)
        libaudiofile.so.0 => /usr/lib/libaudiofile.so.0 (0xb6e5b000)
        libaudio.so.2 => /usr/lib/libaudio.so.2 (0xb6e46000)
        libXt.so.6 => /usr/lib/libXt.so.6 (0xb6df8000)
        liblirc_client.so.0 => /usr/lib/liblirc_client.so.0 (0xb6df3000)
        libgcc_s.so.1 => /lib/libgcc_s.so.1 (0xb6de9000)
        libc.so.6 => /lib/tls/i686/cmov/libc.so.6 (0xb6cba000)
        /lib/ld-linux.so.2 (0xb7efa000)
        libcrypt.so.1 => /lib/tls/i686/cmov/libcrypt.so.1 (0xb6c8c000)
        libresolv.so.2 => /lib/tls/i686/cmov/libresolv.so.2 (0xb6c79000)
        libgssapi_krb5.so.2 => /usr/lib/libgssapi_krb5.so.2 (0xb6c5d000)
        libkrb5.so.3 => /usr/lib/libkrb5.so.3 (0xb6be4000)
        libk5crypto.so.3 => /usr/lib/libk5crypto.so.3 (0xb6bc1000)
        libkrb5support.so.0 => /usr/lib/libkrb5support.so.0 (0xb6bbc000)
        libcom_err.so.2 => /lib/libcom_err.so.2 (0xb6bb8000)
        libldap_r.so.2 => /usr/lib/libldap_r.so.2 (0xb6b84000)
        liblber.so.2 => /usr/lib/liblber.so.2 (0xb6b78000)
        libexpat.so.1 => /usr/lib/libexpat.so.1 (0xb6b59000)
        libpangoft2-1.0.so.0 => /usr/lib/libpangoft2-1.0.so.0 (0xb6b35000)
        libXau.so.6 => /usr/lib/libXau.so.6 (0xb6b31000)
        libgpm.so.1 => /usr/lib/libgpm.so.1 (0xb6b2b000)
        libgii.so.0 => /usr/lib/libgii.so.0 (0xb6b24000)
        libgg.so.0 => /usr/lib/libgg.so.0 (0xb6b1b000)
        libSM.so.6 => /usr/lib/libSM.so.6 (0xb6b12000)
        libICE.so.6 => /usr/lib/libICE.so.6 (0xb6afa000)
        libsasl2.so.2 => /usr/lib/libsasl2.so.2 (0xb6ae6000)
        libgnutls.so.12 => /usr/lib/libgnutls.so.12 (0xb6a7d000)
        libtasn1.so.2 => /usr/lib/libtasn1.so.2 (0xb6a6d000)
        libgcrypt.so.11 => /usr/lib/libgcrypt.so.11 (0xb6a20000)
        libgpg-error.so.0 => /usr/lib/libgpg-error.so.0 (0xb6a1c000

---

### Post by taurus on 2006-11-16
Looks like everything is in order!  How did you install mplayer and what does your /etc/apt/sources.list look like anyway?

```
cat /etc/apt/sources.list
```

---

### Post by OptimusPrime on 2006-11-16
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper main restricted
## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper-updates main restricted
## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper universe
## Uncomment the following two lines to add software from the 'backports'
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted
# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe
deb [http://wine.budgetdedicated.com/apt](http://wine.budgetdedicated.com/apt) dapper main
## TREVINO’S FLASH REPOSITORY
# deb [http://3v1n0.tuxfamily.org](http://3v1n0.tuxfamily.org) dapper 3v1n0
deb [http://www.getautomatix.com/apt](http://www.getautomatix.com/apt) dapper main


#AUTOMATIX REPOS START

deb [http://wine.lowvoice.nl/apt](http://wine.lowvoice.nl/apt) dapper main

deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) dapper-commercial main

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-backports main restricted universe multiverse

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-updates main restricted universe multiverse

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-security main restricted universe multiverse

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) dapper main restricted universe multiverse
#AUTOMATIX REPOS END

---

### Post by OptimusPrime on 2006-11-16
Could it be a problem with my video card?  It's an ATI, and I have been trying to download drivers for it.  Maybe it lost it's ability to run due to some graphical error?

---

### Post by taurus on 2006-11-16
Did you install mplayer from Automatix2?

---

### Post by OptimusPrime on 2006-11-16
Well I'll be darned.  It works now.  I didn't do anything:-k 

Thank's for the help!

---

