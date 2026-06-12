---
title: "Opening a Multi-part RAR file"
date: 2007-06-01
forum: Absolute Beginner Talk
---

### Post by cong06 on 2007-06-01
I have acquired a multi-part RAR Archive file, and I want to extract it.

It appears File-roller [doesn't handle Mult-part files.]("https://bugs.launchpad.net/fileroller/+bug/59448") Unfortunately that link didn't tell me how to approach it.

Another post mentioned [combining the files]("http://ubuntuforums.org/showthread.php?t=202396"). I don't know much about RAR files in general though. It's the kind that has a RAR file, and then R01 to a R56 files. Which ones do I combine? And then which one can I open to extract? Or is there a better way?

List of files, for clarification:
```

htd-tray.r00  htd-tray.r12  htd-tray.r24  htd-tray.r36  htd-tray.r48
htd-tray.r01  htd-tray.r13  htd-tray.r25  htd-tray.r37  htd-tray.r49
htd-tray.r02  htd-tray.r14  htd-tray.r26  htd-tray.r38  htd-tray.r50
htd-tray.r03  htd-tray.r15  htd-tray.r27  htd-tray.r39  htd-tray.r51
htd-tray.r04  htd-tray.r16  htd-tray.r28  htd-tray.r40  htd-tray.r52
htd-tray.r05  htd-tray.r17  htd-tray.r29  htd-tray.r41  htd-tray.r53
htd-tray.r06  htd-tray.r18  htd-tray.r30  htd-tray.r42  htd-tray.r54
htd-tray.r07  htd-tray.r19  htd-tray.r31  htd-tray.r43  htd-tray.rar
htd-tray.r08  htd-tray.r20  htd-tray.r32  htd-tray.r44
htd-tray.r09  htd-tray.r21  htd-tray.r33  htd-tray.r45
htd-tray.r10  htd-tray.r22  htd-tray.r34  htd-tray.r46
htd-tray.r11  htd-tray.r23  htd-tray.r35  htd-tray.r47
```

(There are links up there...preview isn't showing them for me and has me worried)

---

### Post by pbw on 2007-06-01
If it's media, simply extract the main one htd-tray.rar (the only one that's .rar). sudo apt-get install vlc, and away you go, just play the file that's extracted with vlc.

Even if it's not media, I'm pretty sure rest will auto extract as part of the master rar.

-- pbw

---

### Post by cong06 on 2007-06-01
The problem, like I attempted to point out in my first post, is that the file won't extract with File-Roller, simply because it's connected to a multi-part file.

I got this message when I right clicked on htd-tray.rar and chose "Extract here":
```

**Could not Open "htd-tray.rar"**
Archive type not supported

```

Whenever I try to do anything with the file(specifically htd-tray.rar) resembling extracting it or viewing it's contents File-Roller activates and attempts to take over (just like I'd want 7-zip to do in Windows, or WinRar...if I chose to use that...) and then throws that error.

So I refer everyone back to my previous question:

> **cong06 said:**
> Which ones do I combine? And then which one can I open to extract? Or is there a better way?

[SIZE="1"]btw. VLC doesn't install that easy.....[/SIZE]

---

### Post by pbw on 2007-06-01
I don't use file roller, i use ark and it handles multi rars fine, maybe try that if file roller's being a pain. I assume you've installed unrar of course.

How isn't installing vlc that easy? It's sitting in universe.

$ apt-cache search vlc | grep multimedia
libvlc0 - multimedia player and streamer library
mozilla-plugin-vlc - multimedia plugin for web browsers based on VLC
vlc - multimedia player and streamer
vlc-nox - multimedia player and streamer (without X support)

-- pbw

---

### Post by srt4play on 2007-06-01
File roller works perfectly fine for what you want to do, in fact I just used it yesterday to do this exact thing.

The problem is that file roller cannot handle .rar files by default.  Solve this by installing the package "unrar" in Synaptic.  Then right-click the first file (htd-tray.r00 EDIT: just noticed you had a htd-tray.rar file, that probably is the one you need to extract) and choose open with Archive Manager.

---

### Post by pbw on 2007-06-01
*nod at srt4play* That's what i was trying to suggest as well, i didn't really think file roller would be unable to handle it, but as i don't use it i couldnt say. I just assumed he had installed the unrar package, since he said he already looked for help on it prior to posting.

---

### Post by Inxsible on 2007-06-01
you can also install rar instead of unrar...They both do the exact same thing, although they seem antonyms of each other :)

---

### Post by meng on 2007-06-01
I can confirm that multi-part RAR unarchiving works for me. I installed BOTH unrar and unrar-nonfree (on Dapper).

---

### Post by cong06 on 2007-06-01
> **pbw said:**
> *nod at srt4play* That's what i was trying to suggest as well, i didn't really think file roller would be unable to handle it, but as i don't use it i couldnt say. I just assumed he had installed the unrar package, since he said he already looked for help on it prior to posting.

well, I had looked, but as usual I apparently didn't look deep enough or long enough.
thanks and sorry for any miscommunication.

[SIZE="1"]as far as VLC went, I had to add an extra repository...I think anyway maybe I'm confused. :D oh well.;)[/SIZE]

---

### Post by pbw on 2007-06-01
that's cool, glad it got sorted :)

---

### Post by srt4play on 2007-06-01
So did you successfully extract your rar file?

---

### Post by cong06 on 2007-06-02
I did. thanks.

---

