---
title: "vlc crash on old powerbook g3"
date: 2011-04-19
forum: Apple Hardware Users
---

### Post by mkdahan on 2011-04-19
hello.
i installed ubuntu 10.10 on old powerbook g3 (6g hard disk, i think it lombard)m with xfce as desktop (xfce and not xubuntu wich is slower). anyway, everything works fine, but for some reson my vlc just cannot run video file. each time i play him it show a black screen and fall. i tried config his outpot video, and it still dont work, in smoe mode the audio working but the other not.
i tried another movie player, and only totem, kaffeine and xine works ok, although very slowly (the video work not smoothly). kaffeine works fine, but not enough. when i had ubuntu 8.04 in the same computer vlc was the movie player i chose and he did his job perfectly.
can anyone help me with this problem? i search in the internet answer for days, but cannot find. her's the output when i run vlc (the important line is the two in the end):

VLC media player 1.1.4 The Luggage (revision exported)
warning: your CPU has Altivec instructions, but not your operating system.
         some optimizations will be disabled unless you upgrade your OS
Blocked: call to unsetenv("DBUS_ACTIVATION_ADDRESS")
Blocked: call to unsetenv("DBUS_ACTIVATION_BUS_TYPE")
Blocked: call to setlocale(6, "")
Blocked: call to sigaction(17, 0x483b2ac4, 0x483b2a38)
Blocked: call to setlocale(6, "")
[0x108a8260] xcb_xv generic error: no available XVideo adaptor
Illegal instruction

thanks!

---

### Post by mkdahan on 2011-04-19
(sory for the double theard, my mistake. and for the bad english, it isn't my mother tongue)

---

### Post by mkdahan on 2011-04-20
the two lines in the end removed, for some reason:

[0x108a8260] xcb_xv generic error: no available XVideo adaptor
Illegal instruction

---

### Post by conal on 2011-04-20
I always have this exact problem on G3's with VLC on all recent linux disto's. I use totem with the xine-backend (totem-xine rather then totem-gstreamer) have you tried this? I find this gives me the smoothest playback (actually it plays MP4 files smoothly that wont play under OS X with vlc or anything). I use Ogle for DVD's, nothing else plays them smoothly on my 400Mhz box. Is this any help?

I don't understand why VLC gives that altivec message, as far as I know altivec wasn't implemented until the G4 processor, so there would be no point in implementing it in the OS.

---

### Post by mkdahan on 2011-04-20
thank you for the response.
i will try your recommand when it will finish install ubuntu (i have tried another                              distribution. mintppc. not so diffrent from ubuntu, although the video actualy work smother then ubuntu). anyway, do you think that changing xorg.conf is smart idea? i'm searching one compatible to my machine, bronze keyboard.
and thanks again!

---

### Post by conal on 2011-04-20
If you have video working I wouldn't mess with it providing the rosultion, colour depth and so on looks right. You cant expect the same smooth shadows and animations in the GUI as OS X - this is one of the very few things linux can't do so well.  

If things don't look right (colours etc) linuxopjemac (the guy behind MintPPC) has probably advised someone else on this forum about your ibook's xorg.conf file already, so search through.

I installed MintPPC on an eMac the other day - everything went smoothly and worked out-of-the-box. I have installed it a few times now and yes, I find video generally works better than with ubuntu on older machines - though VLC still crashes for me in the way you described.

---

### Post by markosjal on 2011-04-25
Since I just installed another distro with the same issue, can anyone with a g3 and VLC crashing confirm that mplayer crashes as well?


command line mplayer seems to give an error relating to CPU detection.

Does vlc rely on mplayer decodong? If so the problem seems to be mplayer.

FYI check out geexbox.org and post results here please. I had no lock at all with it , but may work for some.

---

### Post by barbaGNU on 2011-04-25
it's possible that some libraries are compiled with altivec code builtin.

---

