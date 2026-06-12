---
title: "no sound for online videos"
date: 2007-12-04
forum: Absolute Beginner Talk
---

### Post by ubunter1 on 2007-12-04
hi im having a problem playing sound with online videos only.if ive a video or music on my computer the sound works fine, also internet music streams work great as well.ive just installed a newish sound card to bypass my sis integrated one because i only recieved sound from one speaker,now it works fine except for the online videos,bbc,hgtv,youtube  etc.i see the video but no sound.is it a driver issue?, or a flash issue?. i looked at the other threads and tried some of the suggestions including reinstalling codecs and the medibuntu repos and flash sound debs, but to no avail.can anyone help?,thanks for your time.

---

### Post by Sef on 2007-12-05
1) What browser are you using?

2) What are your system specs?

3) What version of Ubuntu are you using?

---

### Post by ubunter1 on 2007-12-05
> **Sef said:**
> 1) What browser are you using?

2) What are your system specs?

3) What version of Ubuntu are you using?
sorry for the lack of info.
firefox, latest.
amd athlon 2600xp,motherboard and soundcard is different from original,its some asrock . ram 510. 160gb hd.i think.es1370 audio pci(ensonic audio pci).

ubuntu 7.10 gutsy.

is there a way to code it in the terminal to give a more detailed list of my specs?.
thanks.

---

### Post by aarong on 2007-12-07
i am also having the same problem, and cant find help anywhere

im running firefox 2, with all of my udates taken care of

i have en external sound card which works for all sound other than in firefox

---

### Post by ubunter1 on 2007-12-11
im also starting to get all these boxes instead of text in firefox,and it crashes alot when trying to view video.any ideas?:(

---

### Post by ubunter1 on 2007-12-12
hi,im getting more firefox crashes especially with video,but sometimes i can play the video but the sound will not work still. i also need to force quit the browser and go into the processes page and quit the firefox bin file,to restart the browser.:confused:

---

### Post by ubunter1 on 2007-12-14
would there be any other forums or places i can get info about solving this issue?.i realize people cant answer every thread as this board moves really fast.thanks.

---

### Post by adzik on 2007-12-17
Don't know the answer to your issue, but you should also try [http://www.linuxquestions.org](http://www.linuxquestions.org) (general gnu/linux forums)
and definitely check out the debian forums, as Ubuntu is a debian derived distro.
[http://forums.debian.net](http://forums.debian.net)

Cheers!

---

### Post by ellenhidemi on 2007-12-18
Try to open Firefox as a root (sudo firefox). If the sound works fine, search for .macromedia hidden directory in your "home", delete it and try again (not as a root).

---

### Post by ubunter1 on 2007-12-19
i will try those now,thank you both for the responces,i really want to fix this.
i also got this from the terminal while running sudo firefox and trying to open a video from you tube-
    6903100/6903113.stm?bw=bb&mp=wm&asb=1&news=1&bbcws=1'
** Message: Failed to open DBUS session: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.
** Message: totemPlugin dtor [0x991a588]
** Message: NP_Shutdown
** Message: NP_Initialize
** Message: NP_Initialize succeeded
** Message: totemPlugin ctor [0x9a02a08]
** Message: Init mimetype 'application/x-mplayer2' mode 1
** Message: Base URI is 'http://news.bbc.co.uk/player/nol/newsid_6900000/newsid_6903100/6903113.stm?bw=bb&mp=wm&asb=1&news=1&bbcws=1'
** Message: Failed to open DBUS session: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.
** Message: totemPlugin dtor [0x9a02a08]

so it did not play sound from thsites i tried while sudoing it,

---

