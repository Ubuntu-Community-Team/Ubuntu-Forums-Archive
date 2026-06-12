---
title: "A particular program from a CD, need rather urgently to install..."
date: 2007-05-05
forum: Absolute Beginner Talk
---

### Post by Eoghanalbar on 2007-05-05
I have a CD with a very useful program for preparing for a calculus exam, and it would be REALLY nice to have it, soon, but all Xubuntu sees on the disk are some .mov files.

I'm an absolute Linux noob, period. Just switched old laptop from windows ME to Xubuntu (finally figured out that I had to use the alternate install).

This is now the only OS on the machine.

I don't know where to start.  "Show Hidden Files" doesn't help.

---

### Post by aysiu on 2007-05-05
What's the name of the program?

And is it a Windows-only program?

---

### Post by Ptero-4 on 2007-05-05
You should see an exe file in the CD, otherwise, I don´t know what kind of software it can be.

---

### Post by Eoghanalbar on 2007-05-05
I think the official name is "AP CD".

I don't know what it is. I'm pretty sure a friend of mine who knows linux and stuff has got it on (I think) Kororaa. But then he might have some program to emulate windows or something?

---

### Post by aysiu on 2007-05-05
It may not work. Not all Windows programs can work in Ubuntu, but you can try Wine:
[http://www.psychocats.net/ubuntu/wine](http://www.psychocats.net/ubuntu/wine)

---

### Post by Eoghanalbar on 2007-05-05
I go Applications>Accesories>Terminal and the screen turns to some funny verticle multicolored stripes, goes black, and the xubuntu login screen comes back.

I don't even know how to start getting this WINE thing.

---

### Post by jfinkels on 2007-05-05
Is there an executable file on the disc? That's what you should be looking for. If there is, you may be able to run it by installing wine and typing:
```
wine /path/to/file.exe
```

---

### Post by jfinkels on 2007-05-05
> **Eoghanalbar said:**
> I go Applications>Accesories>Terminal and the screen turns to some funny verticle multicolored stripes, goes black, and the xubuntu login screen comes back.

I don't even know how to start getting this WINE thing.

Uh oh, you might want to get that sorted out before trying to install wine...

AP tests coming up soon? :D

---

### Post by Eoghanalbar on 2007-05-05
I think I may have gotten around the terminal problem (at least partly) by using the Application>System>Add/Remove thing.

Do I have to type that "wine /path/to/file.exe"into the terminal? Is that "file" a wildcard, or do I actually have to know what to call it? Can I USE a wildcard?

I live in Canada, and the damn tests are set to the US schedule, which means we have to take them before we can finish the course on a normal schedule. *Whine*

---

### Post by Eoghanalbar on 2007-05-05
Wow, talk about stupidity plus. I can't believe I missed reading that as "path to file". Ugh.

Still, do I need the terminal for that?

---

### Post by jfinkels on 2007-05-05
Yes you need the terminal.

Take a look at aysiu's site (posted above) before doing anything.

Once you have installed wine, you will want to run the executable file. Where I wrote "/path/to/file.exe", I meant to determine the ACTUAL path to the file (if it's on the cdrom it might be something like "/media/cdrom/filename.exe" where "filename.exe" is the actual name of the executable file. You can see what files are on your cd by typing the following command:
```

ls /media/cdrom/

```
)

In fact, why don't you post here the output of this command.
```

ls /media/cdrom

```

---

### Post by Eoghanalbar on 2007-05-05
Yes, I hope you noticed that I made a post just before you said that. That way I don't have to feel like a COMPLETE moron.

Anyway, I don't know how to take your advice if I can't use the terminal, but I did a forum search and found some post about the exact same problem.

[http://ubuntuforums.org/showthread.php?t=433345&highlight=terminal+crash](http://ubuntuforums.org/showthread.php?t=433345&highlight=terminal+crash)

I followed Pox's instructions and the following mess is what I got:

```
/etc/gdm/PreSession/Default: Registering your session with wtmp and utmp
/etc/gdm/PreSession/Default: running: /usr/X11R6/bin/sessreg -a -w /var/log/wtmp -u /var/run/utmp -x "/var/lib/gdm/:0.Xservers" -h "" -l ":0" "o"
/etc/gdm/Xsession: Beginning session setup...
/usr/bin/startxfce4: X server already running on display :0
** Message: Querying Xkb extension
** Message: Xkb extension found
** Message: This build doesn't include support for XF86Misc extension
** Message: Querying Xkb extension
** Message: Xkb extension found
Warning:          No symbols defined for <SYRQ> (keycode 92)
Warning:          No symbols defined for <II65> (keycode 101)
Warning:          No symbols defined for <BRK> (keycode 114)
Warning:          No symbols defined for <FK13> (keycode 118)
Warning:          No symbols defined for <FK14> (keycode 119)
Warning:          No symbols defined for <FK15> (keycode 120)
Warning:          No symbols defined for <FK16> (keycode 121)
Warning:          No symbols defined for <FK17> (keycode 122)
Warning:          No symbols defined for <KPDC> (keycode 123)
Warning:          No symbols defined for <XFER> (keycode 129)
Warning:          No symbols defined for <I02> (keycode 130)
Warning:          No symbols defined for <NFER> (keycode 131)
Warning:          No symbols defined for <I04> (keycode 132)
Warning:          No symbols defined for <AE13> (keycode 133)
Warning:          No symbols defined for <I06> (keycode 134)
Warning:          No symbols defined for <I07> (keycode 135)
Warning:          No symbols defined for <I08> (keycode 136)
Warning:          No symbols defined for <I09> (keycode 137)
Warning:          No symbols defined for <I0A> (keycode 138)
Warning:          No symbols defined for <I0B> (keycode 139)
Warning:          No symbols defined for <I0C> (keycode 140)
Warning:          No symbols defined for <I0D> (keycode 141)
Warning:          No symbols defined for <I0E> (keycode 142)
Warning:          No symbols defined for <I0F> (keycode 143)
Warning:          No symbols defined for <I10> (keycode 144)
Warning:          No symbols defined for <I11> (keycode 145)
Warning:          No symbols defined for <I12> (keycode 146)
Warning:          No symbols defined for <I13> (keycode 147)
Warning:          No symbols defined for <I14> (keycode 148)
Warning:          No symbols defined for <I15> (keycode 149)
Warning:          No symbols defined for <I16> (keycode 150)
Warning:          No symbols defined for <I17> (keycode 151)
Warning:          No symbols defined for <I18> (keycode 152)
Warning:          No symbols defined for <I19> (keycode 153)
Warning:          No symbols defined for <I1A> (keycode 154)
Warning:          No symbols defined for <I1B> (keycode 155)
Warning:          No symbols defined for <K59> (keycode 157)
Warning:          No symbols defined for <I1E> (keycode 158)
Warning:          No symbols defined for <I1F> (keycode 159)
Warning:          No symbols defined for <I20> (keycode 160)
Warning:          No symbols defined for <I21> (keycode 161)
Warning:          No symbols defined for <I22> (keycode 162)
Warning:          No symbols defined for <I23> (keycode 163)
Warning:          No symbols defined for <I24> (keycode 164)
Warning:          No symbols defined for <I25> (keycode 165)
Warning:          No symbols defined for <I26> (keycode 166)
Warning:          No symbols defined for <I27> (keycode 167)
Warning:          No symbols defined for <I28> (keycode 168)
Warning:          No symbols defined for <I29> (keycode 169)
Warning:          No symbols defined for <K5A> (keycode 170)
Warning:          No symbols defined for <I2B> (keycode 171)
Warning:          No symbols defined for <I2C> (keycode 172)
Warning:          No symbols defined for <I2D> (keycode 173)
Warning:          No symbols defined for <I2E> (keycode 174)
Warning:          No symbols defined for <I2F> (keycode 175)
Warning:          No symbols defined for <I30> (keycode 176)
Warning:          No symbols defined for <I31> (keycode 177)
Warning:          No symbols defined for <I32> (keycode 178)
Warning:          No symbols defined for <I33> (keycode 179)
Warning:          No symbols defined for <I34> (keycode 180)
Warning:          No symbols defined for <K5B> (keycode 181)
Warning:          No symbols defined for <K5D> (keycode 182)
Warning:          No symbols defined for <K5E> (keycode 183)
Warning:          No symbols defined for <K5F> (keycode 184)
Warning:          No symbols defined for <I39> (keycode 185)
Warning:          No symbols defined for <I3A> (keycode 186)
Warning:          No symbols defined for <I3B> (keycode 187)
Warning:          No symbols defined for <I3C> (keycode 188)
Warning:          No symbols defined for <K62> (keycode 189)
Warning:          No symbols defined for <K63> (keycode 190)
Warning:          No symbols defined for <K64> (keycode 191)
Warning:          No symbols defined for <K65> (keycode 192)
Warning:          No symbols defined for <K66> (keycode 193)
Warning:          No symbols defined for <I42> (keycode 194)
Warning:          No symbols defined for <I43> (keycode 195)
Warning:          No symbols defined for <I44> (keycode 196)
Warning:          No symbols defined for <I45> (keycode 197)
Warning:          No symbols defined for <K67> (keycode 198)
Warning:          No symbols defined for <K68> (keycode 199)
Warning:          No symbols defined for <K69> (keycode 200)
Warning:          No symbols defined for <K6A> (keycode 201)
Warning:          No symbols defined for <I4A> (keycode 202)
Warning:          No symbols defined for <K6B> (keycode 203)
Warning:          No symbols defined for <K6C> (keycode 204)
Warning:          No symbols defined for <K6D> (keycode 205)
Warning:          No symbols defined for <K6E> (keycode 206)
Warning:          No symbols defined for <K6F> (keycode 207)
Warning:          No symbols defined for <HKTG> (keycode 208)
Warning:          No symbols defined for <K71> (keycode 209)
Warning:          No symbols defined for <K72> (keycode 210)
Warning:          No symbols defined for <AB11> (keycode 211)
Warning:          No symbols defined for <I54> (keycode 212)
Warning:          No symbols defined for <I55> (keycode 213)
Warning:          No symbols defined for <I56> (keycode 214)
Warning:          No symbols defined for <I57> (keycode 215)
Warning:          No symbols defined for <I58> (keycode 216)
Warning:          No symbols defined for <I59> (keycode 217)
Warning:          No symbols defined for <I5A> (keycode 218)
Warning:          No symbols defined for <K74> (keycode 219)
Warning:          No symbols defined for <K75> (keycode 220)
Warning:          No symbols defined for <K76> (keycode 221)
Warning:          No symbols defined for <I5E> (keycode 222)
Warning:          No symbols defined for <I5F> (keycode 223)
Warning:          No symbols defined for <I60> (keycode 224)
Warning:          No symbols defined for <I61> (keycode 225)
Warning:          No symbols defined for <I62> (keycode 226)
Warning:          No symbols defined for <I63> (keycode 227)
Warning:          No symbols defined for <I64> (keycode 228)
Warning:          No symbols defined for <I65> (keycode 229)
Warning:          No symbols defined for <I66> (keycode 230)
Warning:          No symbols defined for <I67> (keycode 231)
Warning:          No symbols defined for <I68> (keycode 232)
Warning:          No symbols defined for <I69> (keycode 233)
Warning:          No symbols defined for <I6A> (keycode 234)
Warning:          No symbols defined for <I6B> (keycode 235)
Warning:          No symbols defined for <I6C> (keycode 236)
Warning:          No symbols defined for <I6D> (keycode 237)
Warning:          No symbols defined for <I6E> (keycode 238)
Warning:          No symbols defined for <I6F> (keycode 239)
Warning:          No symbols defined for <I70> (keycode 240)
Warning:          No symbols defined for <I71> (keycode 241)
Warning:          No symbols defined for <I72> (keycode 242)
Warning:          No symbols defined for <I73> (keycode 243)
Warning:          No symbols defined for <I74> (keycode 244)
Warning:          No symbols defined for <I75> (keycode 245)
Warning:          No symbols defined for <I76> (keycode 246)
Warning:          No symbols defined for <I77> (keycode 247)
Warning:          No symbols defined for <I78> (keycode 248)
Warning:          No symbols defined for <I79> (keycode 249)
Warning:          No symbols defined for <I7A> (keycode 250)
Warning:          No symbols defined for <I7B> (keycode 251)
Warning:          No symbols defined for <I7C> (keycode 252)
Warning:          No symbols defined for <I7D> (keycode 253)
Warning:          No symbols defined for <I7E> (keycode 254)
Warning:          No symbols defined for <I7F> (keycode 255)
ERROR: ld.so: object 'libjvm.so' from LD_PRELOAD cannot be preloaded: ignored.
ERROR: ld.so: object 'libawt.so' from LD_PRELOAD cannot be preloaded: ignored.
X Error: BadDevice, invalid or uninitialized input device 167
  Major opcode:  144
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 167
  Major opcode:  144
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
xscreensaver: 17:40:29: 0: unrecognised ClientMessage "_NET_ACTIVE_WINDOW" received
xscreensaver: 17:40:29: 0: for window 0x1000003 (Thunar / Thunar)
```

---

### Post by jfinkels on 2007-05-06
you can run terminal commands that don't require a GUI by pressing <Ctrl>+<Alt>+<F1> (or F2, or F3...etc up to F6) to go to your "tty1" terminal. You can get back to the graphical environment by pressing ctrl+alt+F7. Login there and enter commands that you need to enter. For example, if you want to install a different terminal emulator because xfce4term causes crashage, ctrl+alt+f1 then type:
```

sudo aptitude install rxvt
```
Then go back to the graphical environment by pressing ctrl+alt+F7. Press alt+F2 to open the "Run Application" dialog. Type "xterm" (which is another terminal emulator which comes with all Ubuntus) or the now-installed "rxvt" and see if that works. If they don't crash, then use those. Let us know how this goes.

---

### Post by Eoghanalbar on 2007-05-06
The problem is that ctrl+alt+F1 causes crashage.

By the way, I finally got a hold of my friend, and he sent me the files and I can open them with WINE now.

Thank you all very much for your help anyway. I'll have to fix this terminal problem eventually, but right now I've gotta go deal with other priorities, obviously.

One  Fitzy_oz thinks it might have something to do with non-standard buttons on the keyboard, if you're interested.

---

### Post by bobplano on 2007-05-06
for fixing that terminal you could try using synaptic and getting something like konsole or just another terminal and seeing if that works

---

### Post by jfinkels on 2007-05-06
> **bobplano said:**
> for fixing that terminal you could try using synaptic and getting something like konsole or just another terminal and seeing if that works

As I suggested above.

> **Eoghanalbar said:**
> The problem is that ctrl+alt+F1 causes crashage.


Ah, you only told us that xfce4term caused a crash. Have you tried the program "xterm"? Press <Alt>+<F2> to open the "Run Application" dialog, and then type "xterm".

---

### Post by bobplano on 2007-05-06
sorry. i must've read right over it.
EDIT: there it is. i didn't know rxvt was a terminal

---

### Post by jfinkels on 2007-05-06
> **bobplano said:**
> sorry. i must've read right over it.
EDIT: there it is. i didn't know rxvt was a terminal

It's cool, didn't mean to be...brusque. We're all on the same team here. :)

The point of that post was for me to describe how to use the tty1 terminal to install software. All Ubuntus come with xterm, so there's really no need to install another terminal. :P

---

### Post by Eoghanalbar on 2007-05-09
Okay, thanks, and sorry for my slowness. 
"xterm" in alt-F2 works, so long as I don't check the "run in terminal" box. The window that comes up, I assume that's the fully functional terminal for all purposes.

So all good, then?

---

### Post by jfinkels on 2007-05-09
> **Eoghanalbar said:**
> Okay, thanks, and sorry for my slowness. 
"xterm" in alt-F2 works, so long as I don't check the "run in terminal" box. The window that comes up, I assume that's the fully functional terminal for all purposes.

So all good, then?

You don't have to check the "run in terminal" option because xterm IS a terminal! More accurately a 'terminal emulator', as are gnome-terminal, konsole, xfce4term, rxvt, etc. You shouldn't lose any functionality by using xterm over xfce4term. A terminal emulator is just a program that allows you to interact with the shell (on Ubuntu, the Bourne Again Shell, or "bash"), and the shell is a program that let's you interact with your system, i.e. giving commands to run programs. All the terminal emulators you're going to find around here are going to implement bash.

Let us know if you need anything else!

---

