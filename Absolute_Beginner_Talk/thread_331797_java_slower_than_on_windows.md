---
title: "java slower than on windows ???"
date: 2007-01-05
forum: Absolute Beginner Talk
---

### Post by Sasa_Ivanovic on 2007-01-05
I have made a game in Java recently. it's called "plazma" the problem is that it's much slower in Ubuntu than on Windows. And also sound i a bit buggy. This might be only mine problem since i haven't installed sound drivers, but sound works ok. should i install them ?
I'm using JRE 5.0 on both platforms.

The diffrence in speed (using same resolutions) is as follows
Ubuntu : 28 FPS
Windows : 100 FPS

If you have both windows and ubuntu could you test the game on your cpu ? please ...
[http://www1.webng.com/sasaivanovic/]("http://www1.webng.com/sasaivanovic/")
i would really appreciate it if you could report back with FPS count.

---

### Post by Sasa_Ivanovic on 2007-01-05
Common, why are you ignoring me ?

---

### Post by oyvindaa on 2007-01-05
I'd help you out if I had Windows. I'm sure someone will help you soon.

---

### Post by kavon89 on 2007-01-05
I'd love to test it, i'm a java coder myself 8) 

I have windows right now and i'll test it when I get home. My windows machine can two instances of runescape on low detail with minimal lag (I have the micro, so its easy to do 2 runescape accounts at once ;) ). Next off i'm getting my laptop tonight and I shuold have linux fully working and everything I want installed by saturday.

e-mail me if you want: [email]kavon89@gmail.com[/email]

I'll tell ya right now that I know on Mac OS X, the JVM is a little slower than windows. On Mac the hardware diffrence is sort of understandable (powerpc) but on linux there shuld not be... again i've tried runescape on an hp computer, p4, only 256mb ram, intel intergreated gfx, off of the Knoppix 4 live CD. So memory was VERY tight and ruenscape ran on low detail pretty well, it was playable. I'll test it out but check your code.

---

### Post by Sasa_Ivanovic on 2007-01-05
ok, thanks.

---

### Post by MkfIbK7a on 2007-01-05
ok i tried it and here are my results (by the way nice game)

ubuntu = 4fps extremely slow
windows = 100 to 130fps

not sure what the problem is though because all other java programs i have run much faster

---

### Post by livingtarget on 2007-01-05
With the sound off (it shutters and lags up the balls) and the music on I get around about 90fps most of the time.

Do you know if you have glx enabled? If you type glxinfo in the console you'll see a big blurb of text, if it says Direct Rendering: YES than you do (if I remember correctly).

Rather annoying thing is that the ball can be out of view in the opponents goal area and it just needs a little flick but you cant see it any more. May need a little tweak. Also anti aliasing is misspelled I think. 

All in all quite a funny game.

---

### Post by MkfIbK7a on 2007-01-05
i dont have glx enabled do you know how to enable it

---

### Post by Sasa_Ivanovic on 2007-01-05
No it isn't enabled, how should i do this ?

---

### Post by Sasa_Ivanovic on 2007-01-05
> **wert613 said:**
> ok i tried it and here are my results (by the way nice game)

thanks

---

### Post by jimbo2150 on 2007-01-05
> **wert613 said:**
> i dont have glx enabled do you know how to enable it

Don't really play games very much on Linux (or anymore for that matter).

I still use Windows at work. My opinion is not an actual test, just a visual estimation of speed between Windows and Linux.

As for java applets in websites (using Firefox) they seem to load in the same ammount of time overall.

Programs like Azureus that run on Java seem to run much faster though, and take up less memory than they do in Windows. I suppose I could attribute the memory issue with Linux being able to handle memory more efficiently than Windows.

---

### Post by livingtarget on 2007-01-05
Do you have an nvidia card? There's a lot of tutorials on how to change to the 'nvidia' driver, but in a nutshell:

sudo apt-get install nvidia-glx

You may already have that package.

gksudo gedit /etc/X11/xorg.conf

Find the following section, may look slightly different:

Section "Device"
    Identifier     "NVIDIA Corporation NV34 [GeForce FX 5200]"
    Driver         "nv"
EndSection

Change the text "nv" to "nvidia". Save and close the text editor. Cross your fingers and press CTRL+ALT+BACKSPACE and you should have glx. If you get stuck in terminal mode after restarting, revert the changes. Be careful actually if this is the first time doing this. If you need a texteditor in the command line try the nano command.

Of course if you have ati I don't really know, just search for ati in the search box and it should point you in the right direction.

---

### Post by MkfIbK7a on 2007-01-05
i have nvidia and i did all this a long time ago mybe my card doesnt support glx?

elsa tnt2 vanta

its supported by the nvidia legacy drivers

---

### Post by livingtarget on 2007-01-05
hmmz now I dunno, but if your fps is higher on windows there's a good indication it may be your video rendering.

---

### Post by MkfIbK7a on 2007-01-05
this is what i get

```
jon@albert:~$ glxinfo
name of display: :0.0
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Error: couldn't find RGB GLX visual

   visual  x  bf lv rg d st colorbuffer ax dp st accumbuffer  ms  cav
 id dep cl sp sz l  ci b ro  r  g  b  a bf th cl  r  g  b  a ns b eat
----------------------------------------------------------------------
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
0x21 24 tc  1  0  0 c  .  .  0  0  0  0  0  0  0  0  0  0  0  0 0 None
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
0x22 24 dc  1  0  0 c  .  .  0  0  0  0  0  0  0  0  0  0  0  0 0 None
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
0x23 24 tc  1  0  0 c  .  .  0  0  0  0  0  0  0  0  0  0  0  0 0 None
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
0x24 24 tc  1  0  0 c  .  .  0  0  0  0  0  0  0  0  0  0  0  0 0 None
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
0x25 24 tc  1  0  0 c  .  .  0  0  0  0  0  0  0  0  0  0  0  0 0 None
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
0x26 24 tc  1  0  0 c  .  .  0  0  0  0  0  0  0  0  0  0  0  0 0 None
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
0x27 24 tc  1  0  0 c  .  .  0  0  0  0  0  0  0  0  0  0  0  0 0 None
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
0x28 24 tc  1  0  0 c  .  .  0  0  0  0  0  0  0  0  0  0  0  0 0 None
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
0x29 24 tc  1  0  0 c  .  .  0  0  0  0  0  0  0  0  0  0  0  0 0 None
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
0x2a 24 dc  1  0  0 c  .  .  0  0  0  0  0  0  0  0  0  0  0  0 0 None
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
0x2b 24 dc  1  0  0 c  .  .  0  0  0  0  0  0  0  0  0  0  0  0 0 None
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
0x2c 24 dc  1  0  0 c  .  .  0  0  0  0  0  0  0  0  0  0  0  0 0 None
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
0x2d 24 dc  1  0  0 c  .  .  0  0  0  0  0  0  0  0  0  0  0  0 0 None
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
0x2e 24 dc  1  0  0 c  .  .  0  0  0  0  0  0  0  0  0  0  0  0 0 None
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
0x2f 24 dc  1  0  0 c  .  .  0  0  0  0  0  0  0  0  0  0  0  0 0 None
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
0x30 24 dc  1  0  0 c  .  .  0  0  0  0  0  0  0  0  0  0  0  0 0 None
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
0x80 32 tc  1  0  0 c  .  .  0  0  0  0  0  0  0  0  0  0  0  0 0 None

```

---

### Post by livingtarget on 2007-01-05
Don't really want to go too off topic on this, but ok.

In your xorg.conf, have you checked if you are loading glx? 

```
Section "Module"
    Load           "i2c"
    Load           "bitmap"
    Load           "ddc"
    Load           "extmod"
    Load           "freetype"
    Load           "glx"            <-- Add this if it's not here and remove any lines saying load "dri"
    Load           "int10"
    Load           "type1"
    Load           "vbe"
EndSection
```

---

### Post by kavon89 on 2007-01-05
I'm getting around 100fps also... however:

I tried taking a look at ur code, most of it i got but everything not syntax related seems to be in another language, the variables also are named in another language so i can't easily tell whats what. Heres what I noticed however:

1. On a 2Ghz AMD Processer, your game completely maxes out my CPU at 100%. If I lower the resolution, turn anti-aliasing, music, sound all off, and hit start so no balls are moving... I should have some sort of drop in CPU useage since I'm getting over 1,000 FPS. Somthing seems to be over using the CPU... maybe a loop gone wrong or some sort of stream of data i don't know, but theres somthing up with the high CPU useage for a 2D java applet.

2. I noticed a bug with your ball impact sound, it hangs for a second then the balls are in new positions, i think you already mentioned you know that buy just to make sure you know.

try: [http://forum.java.sun.com/index.jspa](http://forum.java.sun.com/index.jspa) There are alot of experenced people there who can help you out with CPU over use or the sound bug... or speeding up the code. 8) 

Otherwise I think its a pretty fun little game with another person.... maybe version 2 will have some AI :mrgreen:

---

### Post by Sasa_Ivanovic on 2007-01-05
All the mentioned bugs only exsist in linux. I have tested the game in windows hundreds of times... and it works fine.

There's no coding mistake, i looked it up very closely. ( the code is on Serbian, it's very nice you went into trouble of looking my messed up code... )

i have installed my GeForce 7600 GT drivers, and everything works fine.
So i gues the problem is in enabling glx direct drawing, how should i do that ?

I'm gonna run Runescape now to see if this is computer related ...

---

### Post by Sasa_Ivanovic on 2007-01-05
My game is java application and not an applet ( like runescape (and i don't have firefox plugin, tryed to download it, but i need to install manualy)), can someone give me a link to a java game that's not an applet. To test this mistery.

---

### Post by mahy on 2007-01-05
Java for linux is inferior to that for windows, that's a fact. Combine this with (probably) poorly-coded software and you'll get such result. Hey! I wanna see Java 6 in ubuntu repos! ;)

---

### Post by Sasa_Ivanovic on 2007-01-05
> **mahy said:**
> Java for linux is inferior to that for windows, that's a fact. 
No it isn't it's the same on all platforms!

The basic idea is :

write once, run anywhere.
or
[b]
write once, debug anywhere.
[/b]

Damn it. Java is the best language. It's not full of **** like C++.
I used C++ for some time, until i realized it has all the bounderies from C. But no Java is pure.
It's pure, it's clean, still it has tons of depracted methods and classees. 
There's no perfect programming language, but i can imagine one :
Combination of Java design and C++ speed. Without any depracted stuff.

---

### Post by mahy on 2007-01-05
> **Sasa_Ivanovic said:**
> No it isn't it's the same on all platforms!

The basic idea is :

write once, run anywhere.
or
[b]
write once, debug anywhere.
[/b]


Write once, debug everywhere! :D 

No, sincerely, the Java Virtual Machine (the platform itself) is inferior in performance, compared to windows and solaris/sparc version. i'm an IT student and a java coder...

---

### Post by Sasa_Ivanovic on 2007-01-05
ok whatever, try it out for yourself and see where is it faster ...

```

if( System == Linux )System.beSlower();

```

---

### Post by mahy on 2007-01-05
> **Sasa_Ivanovic said:**
> ok whatever, try it out for yourself and see where is it faster ...

```

if( System == Linux )System.beSlower();

```

i don't have to, many people did it before. google for some inter-platform java benchmarking.

---

### Post by Sasa_Ivanovic on 2007-01-05
Theoreticly you don't!
My game is slower! Why!

I'm switching back to C++.

---

### Post by steve.horsley on 2007-01-05
I'm getting 95 FPS using Sun java 6 VM on a 1.7G Pentium M with 512M RAM (Dell D600 lappy). ATI graphics card and 3d acceleration.

---

### Post by Sasa_Ivanovic on 2007-01-06
I found the problem... xgl wasn't configured properly, so i reinstalled Ubuntu. Now it's running as fast as on Windows. Just that sound doesn't work. for some reason... i'll fiigure it out though.

A word of friendly advice :
**NEVER INSTALL BERYL**

---

### Post by steve.horsley on 2007-01-06
No sound problems here on java 6 JVM either. Perhaps you should try java 6 if you're not on it already. The default Ubuntu java is not Suns, and the Sun JVM in the repo is version 5. Mind you, Sun's java 5 also had working sound for me.

---

### Post by Sasa_Ivanovic on 2007-01-06
i used :
```

sudo aptitude search java

```
and i found only sun java 5 jre
where can i find java 6

ps :
i'm using sun jre 5.0, and sound doesn't play at all

---

### Post by steve.horsley on 2007-01-06
You have to download java 6 from Sun [http://java.sun.com](http://java.sun.com) and then run the self-extracting binary. But as I say, java 5 from the repos, sound worked for me on 2 separate PCs.

---

### Post by Sasa_Ivanovic on 2007-01-06
ok thanks.

maybe that's 'cause you installed sound drivers ? have you ?
i haven't, but sound works for me out of the box...

---

### Post by steve.horsley on 2007-01-06
Er, no. On one PC I had to tell it to use the soundblaster rather than the on-board sound,but that's all I did. The java sound Just Worked (TM). I would have no idea what to do if it didn't.

---

### Post by petermck on 2007-01-06
> **Sasa_Ivanovic said:**
> I found the problem... xgl wasn't configured properly, so i reinstalled Ubuntu. Now it's running as fast as on Windows. Just that sound doesn't work. for some reason... i'll fiigure it out though.

A word of friendly advice :
**NEVER INSTALL BERYL**

It sounds like 3D rendering wasn't going. What video card do you have? If its an ATI (not too new) you won't need Xgl. See [http://www.ubuntuforums.org/showthread.php?t=321766&highlight=howto+ati](http://www.ubuntuforums.org/showthread.php?t=321766&highlight=howto+ati).

---

### Post by Sasa_Ivanovic on 2007-01-07
I have GeForce 7600 GT. But that doesn't matter....

I have finaly fixed all the bugs ! It turns out i made a glich when programming the bouncing sound, sorry everyone...

In windows game worked allright 'cause i had better sound drivers there so i could play hundrets of sounds at once. So i though that this isn't my error, rather Ubuntu. I was wrong!

Well thanks everyone for all your replies.

---

