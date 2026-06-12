---
title: "can anyone here help me with Debian ppc?"
date: 2011-04-26
forum: Any Other OS
---

### Post by cain071546 on 2011-04-26
i installed Debian ppc base from the netinstall cd on a imac g3
i then installed xorg and xfce 
after logging in i installed synaptic,Vlc,Openoffice,terminator,iceweasel, and menu = so that i could open synaptic and software sorces from the xfce menu  =)

VLC wont play most=90% of .mp3s and wont play any mp4,ogg,avi.wmv or anything else ive thrown at it
it seems to play some .wav files but not others, even from the same album.

so i open vlc in terminal so i can see wye its crashing

tara@dhcppc24:~$ vlc

VLC media player 1.1.3 The Luggage (revision exported)
warning: your CPU has Altivec instructions, but not your operating system.
         some optimizations will be disabled unless you upgrade your OS
Blocked: call to unsetenv("DBUS_ACTIVATION_ADDRESS")
Blocked: call to unsetenv("DBUS_ACTIVATION_BUS_TYPE")
Warning: call to signal(13, 0x1)
[0x1078d900] main libvlc: Running vlc with the default interface. Use 'cvlc' to use vlc without interface.
Blocked: call to setlocale(6, "")
Blocked: call to sigaction(17, 0x48323a48, 0x48323ad4)
Warning: call to rand()
Warning: call to rand()
Warning: call to rand()
Warning: call to rand()
Warning: call to rand()

*(here is were i tried to open a .mp3)*

Blocked: call to setenv("_PX_CONFIG_ORDER", "", 1)
Warning: call to signal(13, 0x1)
Illegal instruction
tara@dhcppc24:~$ 

am i missing codecs?
i posted in Debian forum but Never got a single reply =(

---

### Post by Sef on 2011-04-26
Moved to other o/s talk.

---

### Post by mips on 2011-04-27
Maybe have a look at [http://ubuntuforums.org/showthread.php?t=1533344](http://ubuntuforums.org/showthread.php?t=1533344) seems the issue is PPC related.

---

