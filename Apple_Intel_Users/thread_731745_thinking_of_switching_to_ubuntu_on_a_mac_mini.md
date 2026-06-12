---
title: "thinking of switching to ubuntu on a mac mini"
date: 2008-03-22
forum: Apple Intel Users
---

### Post by kanpachi on 2008-03-22
hey , i've been using ubuntu for awhile , but recently i got myself a mac mini, just cuz of it's small size and convience, and i'm thinking of installing ubuntu on it instead of leopard.
like i've said earlier, i'm very famillar with ubuntu as i've used it on my previous pc, but i'm a newbie to mac , i tried installing feisty, but it won't boot, and gutsy is a bit of a mess, so i'd rather wait for hardy.
when i did have gutsy installed , the remote would show me a pop up window i can change the volume up and down but infact, it wouldn't change the volume at all! so it puzzled me a bit , i was wondering if this works in hardy. i prefer ubuntu by a long shot since it has support for flac which i can't use on a mac, and i love to rip my music in flac format, pulus i'm not so fond of the os x looks.
i was just wondering , do you guys recommend using ubuntu on a mac mini ? does it work well? i mean mac os is built for this hardware, so will ubuntu work as good with it as it should?

---

### Post by mrsteveman1 on 2008-03-22
Ubuntu should work just fine, Mac hardware sets things up so that non-efi operating systems can boot and run normally. Just make sure the firmware on the mac is updated.

Flac seems to work in osx:

[http://earpick.wordpress.com/2007/06/11/how-to-play-flac-in-itunes-on-mac/]("http://earpick.wordpress.com/2007/06/11/how-to-play-flac-in-itunes-on-mac/")

[http://xiph.org/quicktime/]("http://xiph.org/quicktime/")

[http://code.google.com/p/flacforitunes/downloads/list]("http://code.google.com/p/flacforitunes/downloads/list")

---

### Post by cyberdork33 on 2008-03-22
Ubuntu works very well on a Mac Mini.

---

### Post by entangled on 2008-03-23
I've been running ubuntu on my Intel Mac mini Core Solo since I bought it.
I ended up dual booting MacOSX through rEFIt. The grub bootloader also boots SUSE 10.3 further into my disk. SUSE 10.3 is very good and might have the edge for hardware detection and driver installation.

With Feisty most of it worked but I had poor wireless performance (happens in OSX too) and no suspend-to-RAM-resume.
Gutsy could suspend-to-RAM but never woke up.
Hardy now suspends-to-RAM and resumes. This is probably due to the 2.6.23 kernel because SUSE 10.3 has the 2.6.22 kernel and cannot do Suspend.
Wireless is no better - I advise wired operation whatever OS is used.
As for other capabilities:
- Gnome 2.22 looks similar to previous and works well. SUSE 10.3 offers bits of KDE 4 which is interesting, but definitely unfinished. 
- Bluetooth can be made to work for mouse and keyboard. SUSE 10.3 works out of the box.
- I can drive a Epson DX3800 MFP and a Epson 2580 scanner, not quite doing film scanning because xsane backend can't do it and the iscan option won't install. Again SUSE 10.3 will set up drivers and run the film scanner properly.
- I like Firefox 3. Usual plugins seem to work.
- Windows network browsing is good (as it always has been).
- I experiment with Windows Server 2003 in virtualbox. Seems at least as good as Vmware.
- Sound seems to work reliably - it used to be intermittent.

So I certainly think ubuntu works on MacMini but you might find that SUSE 10.3 works better!

---

