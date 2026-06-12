---
title: "Can you interpret this &quot;.xsession-errors&quot; log?"
date: 2007-05-05
forum: Absolute Beginner Talk
---

### Post by Eoghanalbar on 2007-05-05
I did a search and found this this guy got the exact same problem I have with opening a terminal making the screen black and go back to the login screen:

[http://ubuntuforums.org/showthread.php?t=433345&highlight=terminal+crash](http://ubuntuforums.org/showthread.php?t=433345&highlight=terminal+crash)

I followed Pox's instructions and got the following schmozzle. Can anyone figure out what it means in terms of how to fix the problem?

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

### Post by Fitzy_oz on 2007-05-05
> **Eoghanalbar said:**
> I did a search and found this this guy got the exact same problem I have with opening a terminal making the screen black and go back to the login screen:

[http://ubuntuforums.org/showthread.php?t=433345&highlight=terminal+crash](http://ubuntuforums.org/showthread.php?t=433345&highlight=terminal+crash)

I followed Pox's instructions and got the following schmozzle. Can anyone figure out what it means in terms of how to fix the problem?

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

Is it a non-standard keyboard? Is there anything out of the ordinary, extra buttons extra functioanliy outside the standard 104 key keyboard?

---

### Post by Eoghanalbar on 2007-05-05
"Compaq" with two of those "Windows" buttons, a volume up button, a down, and a crescent moon that I assume is a sleep button.

It connects via one of those round six pin things (what do you call those?)

There are model numbers and stuff written on the back, but I'm guessing those won't be much use to you?

Oh, also, it's connected to a laptop (Dell Inspiton 2500), usurping the built in keyboard. Does that make a difference?

---

