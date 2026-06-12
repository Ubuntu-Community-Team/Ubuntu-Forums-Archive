---
title: "Installing libdvdcss"
date: 2007-03-03
forum: Absolute Beginner Talk
---

### Post by rath3r on 2007-03-03
I'm looking for help installing libdvdcss in order to play dvds the only thread which i came across was found at.

[http://ubuntuforums.org/showthread.php?p=1139971](http://ubuntuforums.org/showthread.php?p=1139971)

This thread gave the following command as a possible solution, install libdvdcss2

[FONT="Courier New"]sudo /usr/share/doc/libdvdread3/examples/install-css.sh
[/FONT]
after typing this into the terminal it tells me

[FONT="Courier New"]sudo: /usr/share/doc/libdvdread3/examples/install-css.sh: command not found[/FONT]

which confuses me. This has not given me the ability to play dvds. The thread also refers to other solutions but of the two one produced the same result as above and the other was a bad link.

Is there anyone out there who can help me get around this. I know or at least hope it is only a matter of installing libdvdcss. I have found 

libdvdcss-1.2.8-1.fr.i386.rpm 

but this seems to have been a none ubuntu version, and is not recognised. I hope, as was the reply to my last query, that it will just involve using an autopackage. But to tell the truth I don't know what to do.

---

### Post by taurus on 2007-03-03
Here's a guide.

[https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs](https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs)

---

### Post by AndyCooll on 2007-03-03
Ubuntu uses the deb format, rpm's are used by Fedora Core etc.

Anyway, copy and paste the following two lines and that should do it:

```
wget -c http://medibuntu.sos-sts.com/repo/pool/edgy/free/i386/libdvdcss2_1.2.9-2medibuntu2_i386.deb
sudo dpkg -i libdvdcss2_1.2.9-2medibuntu2_i386.deb
```

:cool:

---

### Post by Bachstelze on 2007-03-03
Another option is to compile libdvdcss from source. It's very easy and could give you a first sight on how things work :)

---

### Post by RomeReactor on 2007-03-03
Hi rath3r. The command you posted was meant for Dapper; for Edgy, it's

```
sudo /usr/share/doc/libdvdread3/install-css.sh
```

**without** the "examples" part. Here's a good [guide]("http://ubuntuguide.org/wiki/Ubuntu:Edgy#How_to_install_DVD_playback_capability").

---

### Post by rath3r on 2007-03-03
I don't know if any of the people who replied to this thread will ever read this but thank you dvds are now playing. 

Lots still to learn but i know I can rely on you guys.

Thanks

especially RomeReactor it was your advice which finally got things going.

thanks again

---

