---
title: "Two programs not working correctly."
date: 2007-10-07
forum: Absolute Beginner Talk
---

### Post by jeff4760 on 2007-10-07
Amarok and X Sensors are not working with my Ubuntu install.  Amarok was included in the cd I burned and I installed X Sensors using synaptic.  When I open Amarok it freezes and I have to force close it using the "terminate" command.  X Senors shows nothing.  No CPU, memory, temp, etc. readings.  Just a blank page.  Does anyone know why this might be so, or good programs to try in replacement of those?

I do have an X- Fi card, with no updated driver yet, that might be the problem of the Amarok program.  My MOBO is a Gigabyte 965P- DS3- not sure if that is problematic with sensor reading in Linux or not.

Thanks

---

### Post by deadgobby on 2007-10-07
run amarok in the terminal and see if any error messages appear.

---

### Post by jeff4760 on 2007-10-07
Ok, well I am glad that I just found out about 5 minutes ago what the terminal window actually is.  Here is the error message:

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
Amarok: [Loader] Starting amarokapp..
Amarok: [Loader] Don't run gdb, valgrind, etc. against this binary! Use amarokapp.
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
kdecore (KAction): WARNING: KAction::insertKAccel( kaccel = 0x78cc20 ): KAccel object already contains an action name "play_pause"
QLayout "unnamed" added to QVBox "unnamed", which already has a layout
kdecore (KAction): WARNING: KAction::insertKAccel( kaccel = 0x78cc20 ): KAccel object already contains an action name "play_pause"
QLayout: Adding KToolBar/mainToolBar (child of QVBox/unnamed) to layout for PlaylistWindow/PlaylistWindow
Amarok: [Loader] amarokapp probably crashed!

I keep seeing bad device, so maybe that is the X-Fi card.  I have another thread where I am asking some very Newbie instructions on how to get that driver installed.  Could that be it?

UPDATE: on X Sensors.  I followed a walkthrough for sudo sensors-detect, and Kunbuntu does detect my sensors, but X Sensors still does not work.  Here is the terminal reading:

it8718-isa-0290
Adapter: ISA adapter
in0:       +1.30 V  (min =  +0.00 V, max =  +4.08 V)
in1:       +1.79 V  (min =  +0.00 V, max =  +4.08 V)
in2:       +3.38 V  (min =  +0.00 V, max =  +4.08 V)
in3:       +2.93 V  (min =  +0.00 V, max =  +4.08 V)
in4:       +0.61 V  (min =  +0.00 V, max =  +4.08 V)
in5:       +0.00 V  (min =  +0.00 V, max =  +4.08 V)   ALARM
in6:       +1.25 V  (min =  +0.00 V, max =  +4.08 V)
in7:       +3.02 V  (min =  +0.00 V, max =  +4.08 V)
in8:       +4.08 V
fan1:        0 RPM  (min =    0 RPM)
fan2:        0 RPM  (min =    0 RPM)
fan3:     1979 RPM  (min =   10 RPM)
temp1:       +38°C  (low  =  +127°C, high =  +127°C)   sensor = thermistor
temp2:       +29°C  (low  =  +127°C, high =   +60°C)   sensor = diode
temp3:        -2°C  (low  =  +127°C, high =  +127°C)   sensor = thermistor
vid:      +1.088 V

I see alarm at in5.  Is that anything to worry about?  NOTE: I have thought for some time that one on my sensors was faulty.

---

### Post by jeff4760 on 2007-10-08
That same error message for Amarok shows after I remove the X-Fi card and boot up with the audio line-in plugged into my motherboard audio.  That just is confusing to me.  I would have posted the error message but I crashed Linux trying to update the drivers for my nvidia card.

Any clues anyone?

---

### Post by jeff4760 on 2007-10-09
I fixed the Linux crash but cannot get the sound to work under Linux whatsoever.   I am running the 64 bit version on a Gigabyte 965p-DS3 motherboard.  Does anyone have any suggestions?

---

### Post by HousieMousie2 on 2008-01-29
Might not be anything more than Amarok...

Every time I load Amarok after a start-up, I have to make it try to play a song (which it won't) then I terminate the program, and restart Amarok, after which it will work just fine, but if I don't make it lock itself up first then simply restarting the program will do nothing to help me.

I am looking for a solution and will post back here if I find one.

---

