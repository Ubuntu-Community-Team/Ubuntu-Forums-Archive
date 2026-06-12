---
title: "Real Player is REALLY annoying!"
date: 2006-09-08
forum: Absolute Beginner Talk
---

### Post by ross22 on 2006-09-08
Hi,

I like to listen to BBC radio "listen again" more or less everyday.  Unfortunately, realplayer 10 doesn't seem to work on my machine with ubuntu (or pclinuxos and suse).  The stream plays but the controls become unresponsive almost immediately.  I've tried using alternatives such as mplayer and gxine; both work but unfortunately not very well.  This is probably due to the fact that I live in China and my connection can be fast and intermittantly slow (I believe this is due to the great firewall of China as it seems to make no difference even when I use the internet at my friends home, university, internet cafe etc).  Realplayer works better as when the connection becomes slower it automatically switches to lower quality broadcast whereas mplayer and gxine do not (I can only listen for a very short time until the audio stops to rebuffer); Is there any way to configure them differently?
In PClinuxos I installed realplayer 8 which worked perfectly for the radio; unfortunately I can't seem to install it on ubuntu.  Synaptics tells me "depends xlibs but not installable".  I've tried to install the rpm after using the alien command - it installs but I cannot get realplayer to load.  I've also tried to install the .bin file, again I'm told "error while loading shared libraries: libXm.so.2: cannot open shared object file".
I've searched the repsoitories but cannot find the library, any idea where I can find it?

Sorry for the very long explainatio; I've been trying hard to fix this on my own!

Thanks in advance for any help
Ross

---

### Post by xyz on 2006-09-08
**navneeth** had the same problem so I hope you'll be able to solve yours by clicking....
[http://www.ubuntuforums.org/showthread.php?t=250416](http://www.ubuntuforums.org/showthread.php?t=250416)

Let us know...

---

### Post by ross22 on 2006-09-08
Hi xyz,

thanks for the quick reply, I read through the link earlier but it doesn't cover my problem as although I can install and use the players (realplayer10, mplayer) they don't work very well.  real10 works best although the controls become unresponsive (the station keeps playing however).  I don't know why realplayer becomes unresponsive, my gf has another laptop running ubuntu with real player 10 working fine, hers is less powerful than mine though!  I have a compaqv2000, 1.6ghz, 786mbRAM but realplayer always becomes unresponsive after a few minutes on suse, pclinuxos and now ubuntu. on my gf's 1.5ghz acer laptop with 512mb RAM it works fine (in ubuntu suse and pclos which ive installed at different times).

In pclos i found that realplayer8 worked fine; but i can't install on ubuntu due to a missing library that I can't find.

I would prefer to use anything other than realplayer if I could configure it to not rebuffer every five seconds and instead play at a lower quality.

Thanks again for any help
Ross

---

### Post by xyz on 2006-09-08
Did you enable DMA?
[https://help.ubuntu.com/community/DMA](https://help.ubuntu.com/community/DMA)

You do have all the required codecs installed?
And if, as you say "would prefer to use anything other than realplayer", why not do what navneeth did in the thread I suggested to you?

---

### Post by ross22 on 2006-09-08
Hi xyz,

DMA is enabled; also I did what you said and installed mplayer plugin for firefox.  It works - but it doesnt work very well for me because it always plays at full quality 44000khz whereas realplayer varies depending on your connection speed.  When I use realplayer 10 for the today program the stream plays for the full 3 hours without having to rebuffer (the quality of the audio goes up and down), however with the mplayer plugin it rebuffers every minute or so and is always playing with full quality which is really annoying.

I'd really like to sort this out as at the moment the only reason I have to boot windows is to use realplayer for the radio.
thanks
Ross

---

### Post by xyz on 2006-09-08
Could you please give the link to what you're trying to listen to?
Thanks.

---

### Post by ross22 on 2006-09-08
here is a link for 'today' on friday:

[http://www.bbc.co.uk/radio/aod/shows/rpms/radio4/today_fri.ram](http://www.bbc.co.uk/radio/aod/shows/rpms/radio4/today_fri.ram)

mplayer is playing for me now - and rebufferring every 5 seconds or so I estimate

Im off to bed now; thanks for your help

ross

---

### Post by xyz on 2006-09-08
OK ross22...good night! Will check in later and try your link!
Here it is only 4:15 PM!!

BBC works fine for me...so far!

---

