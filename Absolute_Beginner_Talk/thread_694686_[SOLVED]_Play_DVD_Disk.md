---
title: "[SOLVED] Play DVD Disk"
date: 2008-02-12
forum: Absolute Beginner Talk
---

### Post by Hoom@n on 2008-02-12
Hello!
I wanna play a dvd disk but I get this: "Totem cannot play this type of media (DVD) because it does not have the appropriate plugins to be able to read from the disc./Please install the necessary plugins and restart Totem to be able to play this media./More information about media plugins" What should I do?
(I can play it in winxp or my home dvdplayer)
Thanks.

---

### Post by taurus on 2008-02-12
[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

---

### Post by Hoom@n on 2008-02-12
Thanks, but I couldn't get what should I do. Should I install "sudo wget [http://www.medibuntu.org/sources.list.d/gutsy.list](http://www.medibuntu.org/sources.list.d/gutsy.list) -O /etc/apt/sources.list.d/medibuntu.list" or? Please help more clear!

---

### Post by ghantoos on 2008-02-12
You can try this:
[http://ubuntuguide.org/wiki/Ubuntu:Gutsy#How_To_Add_DVD_Playback_Capability](http://ubuntuguide.org/wiki/Ubuntu:Gutsy#How_To_Add_DVD_Playback_Capability)

Hope this helps,

Cheers,

---

### Post by CJ56 on 2008-02-12
Open the terminal - it's in Applications> Accessories

Copy the long command on the medibuntu web page beginning 'sudo wget...' Make sure you copy the command that corresponds to your version of Ubuntu

Paste it into the terminal and hit return

If it asks for your password, type it in the terminal - if you don't see any characters, don't worry. Just type the password carefully then hit return. The terminal does the rest

Close the terminal , go to System> Administration> Synaptic Package Manager

Press the Reload button on the Package Manager to check that your repositories are up-to-date

Search for libdvdcss2

Install it if it's not in there

Close Synaptic & try your DVD player again....

Hope this works... 8)

---

### Post by stchman on 2008-02-12
> **Hoom@n said:**
> Hello!
I wanna play a dvd disk but I get this: "Totem cannot play this type of media (DVD) because it does not have the appropriate plugins to be able to read from the disc./Please install the necessary plugins and restart Totem to be able to play this media./More information about media plugins" What should I do?
(I can play it in winxp or my home dvdplayer)
Thanks.

I have a tutorial.

[http://www.stchman.com/dvd_rip.html](http://www.stchman.com/dvd_rip.html)

---

### Post by ExpatPaul on 2008-02-12
> **Hoom@n said:**
> Hello!
I wanna play a dvd disk but I get this: "Totem cannot play this type of media (DVD) because it does not have the appropriate plugins to be able to read from the disc./Please install the necessary plugins and restart Totem to be able to play this media./More information about media plugins" What should I do?
(I can play it in winxp or my home dvdplayer)
Thanks.

I had this issue a while ago. 

Check this: [https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs](https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs)

And try this:

```
sudo apt-get install libdvdread3 libxine1-ffmpeg totem-xine
sudo /usr/share/doc/libdvdread3/install-css.sh
```

---

### Post by Hoom@n on 2008-02-12
Thanks alot for all the helps. Post #7 solved everything. And also I gonna read the guide from post #6.
Thanks alot for help!

---

