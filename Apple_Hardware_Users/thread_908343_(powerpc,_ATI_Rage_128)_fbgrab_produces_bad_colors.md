---
title: "(powerpc, ATI Rage 128) fbgrab produces bad colors"
date: 2008-09-02
forum: Apple Hardware Users
---

### Post by paul_mcl on 2008-09-02
I'm using CLI almost for anything (okay, links2 -g isn't CLI). And to make screenshots somebody recommended me 'fbgrab'. But this small (1 source file, as I saw) utility produces distorted colors (in both 16 and 32 bit modes) or even anything in grayscale (when capturing terminal screens). Does anybody have a solution?

---

### Post by paul_mcl on 2008-09-03
Blue & White G3 / ATI Rage Orion... Same thing (screenshot attached). Hard-coded color conversion tables in fbgrab? Can anybody suggest a correct table(s)?

---

### Post by wodim on 2008-09-12
I can suggest that it is endianess problem. You can to do the following to test it:
1. Change to 32-bit mode (use fbset, for example).
2. ```
cp /dev/fb0 dump
```
3. Convert this dump file so each 32-bit number in it, for example $12345678, becomes $78563412 and so on (for more information, visit [http://en.wikipedia.org/wiki/Endianness](http://en.wikipedia.org/wiki/Endianness)).
4. ```
fbgrab -w 1024(replace with your screen's width) -h 768 -b 32 -f dump fb.png
```
5. ```
fbi fb.png
``` to see the result.

---

### Post by paul_mcl on 2008-09-13
> I can suggest that it is endianess problem.
> You can to do the following to test it:
> ...

No, it is not. I checked it even before my post #2 in this thread. Almost nothing changes by swapping bytes. But anyway, thanks for response.
Linux -on- Apple PPC Mac users, I just can't be the only one with this problem (as I saw, all of three [different!] macintoshes shows color distortion). But I can't find any information on that, google doesn't know it too. Can't understand...

---

