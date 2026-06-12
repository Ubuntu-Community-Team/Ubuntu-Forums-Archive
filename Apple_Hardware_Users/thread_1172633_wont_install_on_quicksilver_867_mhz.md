---
title: "wont install on quicksilver 867 mhz"
date: 2009-05-28
forum: Apple Hardware Users
---

### Post by jdmdelsol97 on 2009-05-28
im trying to install ubuntu 9.04 on my powermac g4 quicksilver 867 mhz. i hold c down and brings up to the boot page i type live and then it says "please wait" and then "please wait" goes away and nothing happens. i type live-powerpc64 then tells me to type "mac-boot" i do it again and  i keep getting DEFAULT CATCH!code-300 i dont know what to do any ideas?

---

### Post by tiresia on 2009-05-28
You G4 is not 64bit, so don't use that option. Hit TAB at the yaboot prompt to see the different option. Most probably you have problems with the splash image. Try therefore ```
live-nosplash-powerpc
``` If you still have problem try then ```
live-nosplash-powerpc video=ofonly
```

---

### Post by jdmdelsol97 on 2009-05-28
im trying what you told me but it just kinda of stops after checking drivers or wont go past "loading, please wait"

---

### Post by jdmdelsol97 on 2009-05-29
i reset the pram and pmu and still dont know what to do...i have gotten to the point where i get the ubuntu log in and password but i dont have a user name or password, it then freezes again.

---

### Post by jdmdelsol97 on 2009-05-29
any one?

---

### Post by tiresia on 2009-05-29
error

---

### Post by jdmdelsol97 on 2009-05-29
i burned the live cd my self. I only made it to the ubuntu screen twice, three other times i had a mouse pointer. the rest of the time of typing "live-nosplash-powerpc video=ofonly" i got "loading please wait'....then the little dash at the bottom _ stops blinking and it stays there. almost every attempt i get this problem

---

### Post by tiresia on 2009-05-29
Do you get the yaboot prompt? What do you get if you hit TAB?
About your Hardware: how much RAM? Which is your grafic card?
Where did you download the LiveCD? Did you burn it correctly at lowspeed (without mounting it in MacOSX - just burning it as iso image NOT as data? )

---

### Post by jdmdelsol97 on 2009-05-29
> **tiresia said:**
> Do you get the yaboot prompt? What do you get if you hit TAB?
About your Hardware: how much RAM? Which is your grafic card?
Where did you download the LiveCD? Did you burn it correctly at lowspeed (without mounting it in MacOSX - just burning it as iso image NOT as data? )

i get the yaboot promt. if i hit tab i get live or live power pc and i cant remember the rest of the top because i cant see it.
as for hardware i have 1.12 gb of ram the original graphics card that came on it has a vga and acd. i burnt the live cd on disk utility the same way i burn all my other os discs. im assuming its the lowspeed because all of my other discs worked.

---

### Post by jdmdelsol97 on 2009-05-29
oh and i downloaded the live cd from the ubuntu website

---

### Post by tiresia on 2009-05-30
Can you switch to another console (ctrl-alt-F1). If you can do it, it means that you have problems with X. And maybe would be easier to use the alternate CD

---

### Post by jdmdelsol97 on 2009-05-30
> **tiresia said:**
> Can you switch to another console (ctrl-alt-F1). If you can do it, it means that you have problems with X. And maybe would be easier to use the alternate CD

I tried the alternate cd I made it just past the networking screen.After I didn't know what my password I told it to not set up my network at this time, the screen immediatly after that freezes at 50%

---

### Post by jdmdelsol97 on 2009-06-04
i burned a kubuntu live cd at low speed same problem

---

### Post by williwinki on 2009-07-20
I have exactly the same problem on my Quicksilver, configured almost identical to yours.  Have not seen any resolution.    Would like to know of anyone who has been successful installing 9.04 (from scratch) on a Quicksilver.

---

