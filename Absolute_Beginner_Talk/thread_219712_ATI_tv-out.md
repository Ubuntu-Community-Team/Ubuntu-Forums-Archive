---
title: "ATI tv-out"
date: 2006-07-20
forum: Absolute Beginner Talk
---

### Post by m085 on 2006-07-20
I have an ATI Radeon 9100 IGP (Integrated graphics)
When I isntalled Ubuntu the graphics drivers were already working great, I can set my resoloution high and everything. With the Windows ATI drivers I could press Ctrl+F5 and the screen would switch to my TV. Does anyone know of a good driver that will let me clone my monitor to my TV or even just switch it? Are the drivers from the ATI website good enough? If so, how do I install a .run file?
Thank you very much for your help.

---

### Post by nalmeth on 2006-07-20
It's not at all guaranteed to work, but you could try the atitvout program. I think it will only work on certain ati cards, and only with composite video, not S-Video

You should read the [project page]("http://0pointer.de/lennart/projects/atitvout/") first, then decide if you want to try it

Applications -> Accessories --> Terminal
```
sudo apt-get update
sudo apt-get install atitvout
```
have TV plugged in
```
sudo atitvout -f detect
```
(detect TV-composite)
```
sudo atitvout -f t
```
(switch to TV)
```
sudo atitvout -f l
```
(back to LCD)

If it works you can make a keyboard shortcut for it in
SYSTEM - PREFERENCES - KEYBOARD SHORTCUTS

If it doesn't work, and your stuck somewhere between your monitor and your TV, hit CNTL-ALT-BACKSPACE to restart X.

---

### Post by m085 on 2006-07-20
thank you, another possible solution, for other people who need help:
[http://ubuntuforums.org/showthread.php?t=215763](http://ubuntuforums.org/showthread.php?t=215763)

---

### Post by da1nonlymikeo on 2006-07-20
hey im trying to do the same thing. did the atitvout program work for you?

---

### Post by m085 on 2006-07-20
ATITVOUT didn't work for me, when I go to detect the TV it says my graphics card doesn't support that function and don't complain.:D 
The how-to that I posted seemed to work. When I start my computer or shut it down, the loading screens appear on the TV, but with the wrong refresh rate so I can just barely make out that they are, in fact, the loading screens. I don't know how to switch screens using the drivers I installed in the how-to. Any help please?

---

### Post by nalmeth on 2006-07-20
Yes, atitvout worked for me.

I know one other person it worked for too.

I lucked out, because the guy who made the app, made and tested it with precisely the same built-in video card that I have :D 

You may not be so lucky, but it's probably worth a shot.

---

### Post by da1nonlymikeo on 2006-07-20
hmm yeah i checked out the site and my card (Radeon Mobility M6 LY) isent listed under the cards its made for. so i dont want to mess somthing up bigtime haha

---

