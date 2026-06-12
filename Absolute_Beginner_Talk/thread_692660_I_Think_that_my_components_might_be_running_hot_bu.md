---
title: "I Think that my components might be running hot but I can't tell"
date: 2008-02-10
forum: Absolute Beginner Talk
---

### Post by XVII on 2008-02-10
When I put
```
sensors
```
into the terminal, this is what I get:
```
lm78-i2c-1-28
Adapter: SMBus nForce2 adapter at f800
VCore 1:   +2.32 V  (min =  +0.00 V, max =  +3.49 V)   
VCore 2:   +2.93 V  (min =  +0.70 V, max =  +1.04 V)   ALARM
+3.3V:     +3.31 V  (min =  +2.06 V, max =  +0.06 V)   ALARM
+5V:       +5.56 V  (min =  +0.00 V, max =  +0.00 V)   ALARM
+12V:      +9.06 V  (min =  +0.06 V, max =  +0.12 V)   ALARM
-12V:     -10.90 V  (min =  -8.23 V, max =  -2.45 V)   ALARM
-5V:       -5.47 V  (min =  -1.59 V, max =  -3.30 V)   ALARM
fan1:        0 RPM  (min = 675000 RPM, div = 2)          ALARM
fan2:        0 RPM  (min = 168750 RPM, div = 8)          ALARM
fan3:        0 RPM  (min = 675000 RPM, div = 2)          ALARM
temp:      -65.0°C  (high =    +0°C, hyst =  +127°C)   ALARM
vid:       +3.00 V
alarms:   Board temperature input (LM75)               ALARM
alarms:   Chassis intrusion detection                  ALARM

w83627dhg-isa-0290
Adapter: ISA adapter
VCore:     +1.17 V  (min =  +0.00 V, max =  +1.74 V) 
in1:       +9.66 V  (min =  +2.32 V, max =  +3.43 V) ALARM
AVCC:      +3.31 V  (min =  +2.06 V, max =  +0.06 V) ALARM
3VCC:      +3.31 V  (min =  +0.00 V, max =  +0.00 V) ALARM
in4:       +1.19 V  (min =  +0.01 V, max =  +0.02 V) ALARM
in5:       +1.57 V  (min =  +0.35 V, max =  +1.18 V) ALARM
in6:       +5.81 V  (min =  +3.51 V, max =  +1.69 V) ALARM
VSB:       +3.31 V  (min =  +0.64 V, max =  +1.09 V) ALARM
VBAT:      +2.98 V  (min =  +1.15 V, max =  +0.03 V) ALARM
Case Fan:    0 RPM  (min = 21093 RPM, div = 64) ALARM
CPU Fan:     0 RPM  (min = 10546 RPM, div = 128) ALARM
Aux Fan:     0 RPM  (min = 21093 RPM, div = 64) ALARM
fan4:        0 RPM  (min = 10546 RPM, div = 128) ALARM
fan5:        0 RPM  (min = 42187 RPM, div = 32) ALARM
Sys Temp:    -65°C  (high =    +0°C, hyst =  +127°C)  
CPU Temp:  +21.0°C  (high = +127.0°C, hyst =  +0.0°C)   ALARM
AUX Temp:  -65.0°C  (high = +127.0°C, hyst =  +0.0°C)  

coretemp-isa-0000
Adapter: ISA adapter
Core 0:       +8°C  (high =   +85°C)                   

coretemp-isa-0001
Adapter: ISA adapter
Core 1:      +12°C  (high =   +85°C)
```

What are all of those alarms for and should I worry about them?

---

### Post by tyggna1 on 2008-02-10
Everything looks like it's running fine--and that it's not running very much.  I don't know what the Alarm means--as I've never used the sensors program--but the only one I'd worry about is the + and - 12 volt readouts--those seem to be a little low.

Lack of use could account for that--but it could also be a power-supply problem.  Rev up some devices that use the 12V connectors and then run the sensors to see if they're giving enough juice.

(Hint: There's a 12V connector to your RAM and north-bridge)

---

### Post by tyggna1 on 2008-02-10
To help you make more sense--this is what I gathered:

The parenthesis tell you what is normal usage.  The first term is the current usage.  As long as no component is running above 60-70C, then it's running fine.  Some processors (like you're GPU) can run much hotter than that (120s in your case).

Your CPU is running at 21C, which is perfect.

I'm guessing that the alarms mean that you've reached a new "historic" high. . .but, that's just a guess.

---

### Post by XVII on 2008-02-10
I was just making sure, I though everything was fine; thanks for reaffirming my thoughts.  The reason it might be running low i that I have a monster 100% copper overclocker's fan and I'm not overclocking.

---

### Post by dcstar on 2008-02-10
> **XVII said:**
> When I put
```
sensors
```
into the terminal, this is what I get:
..........
What are all of those alarms for and should I worry about them?

Those numbers are all over the place and should not be trusted (negative temperatures!), you should run **sensors-detect** again and see if things make more sense.

---

### Post by XVII on 2008-02-10
> **dcstar said:**
> Those numbers are all over the place and should not be trusted (negative temperatures!), you should run **sensors-detect** again and see if things make more sense.

Okay.  I did sensors-detect again and this is the output of sensors now:
```
lm78-i2c-1-28
Adapter: SMBus nForce2 adapter at f800
VCore 1:   +2.34 V  (min =  +0.00 V, max =  +3.49 V)   
VCore 2:   +2.93 V  (min =  +0.70 V, max =  +1.04 V)   ALARM
+3.3V:     +3.31 V  (min =  +2.58 V, max =  +0.06 V)   ALARM
+5V:       +5.56 V  (min =  +0.00 V, max =  +0.00 V)   ALARM
+12V:      +9.06 V  (min =  +0.18 V, max =  +4.01 V)   ALARM
-12V:     -10.90 V  (min =  -8.23 V, max =  -2.45 V)   ALARM
-5V:       -5.47 V  (min =  -1.59 V, max =  -3.30 V)   ALARM
fan1:        0 RPM  (min = 7336 RPM, div = 8)          ALARM
fan2:        0 RPM  (min = 13775 RPM, div = 2)          ALARM
fan3:        0 RPM  (min = 16463 RPM, div = 2)          ALARM
temp:      -65.0°C  (high =    +0°C, hyst =  +127°C)   ALARM
vid:       +3.00 V
alarms:   Board temperature input (LM75)               ALARM
alarms:   Chassis intrusion detection                  ALARM

w83627dhg-isa-0290
Adapter: ISA adapter
VCore:     +1.17 V  (min =  +0.00 V, max =  +1.74 V) 
in1:       +9.66 V  (min =  +2.32 V, max =  +3.43 V) ALARM
AVCC:      +3.31 V  (min =  +2.58 V, max =  +0.06 V) ALARM
3VCC:      +3.31 V  (min =  +0.00 V, max =  +0.00 V) ALARM
in4:       +1.19 V  (min =  +0.02 V, max =  +0.53 V) ALARM
in5:       +1.57 V  (min =  +0.35 V, max =  +1.18 V) ALARM
in6:       +5.81 V  (min =  +3.51 V, max =  +1.69 V) ALARM
VSB:       +3.31 V  (min =  +0.64 V, max =  +1.09 V) ALARM
VBAT:      +2.99 V  (min =  +1.15 V, max =  +0.03 V) ALARM
Case Fan:    0 RPM  (min = 7670 RPM, div = 16) ALARM
CPU Fan:     0 RPM  (min =  878 RPM, div = 64) ALARM
Aux Fan:     0 RPM  (min = 4218 RPM, div = 16) ALARM
fan4:        0 RPM  (min = 5273 RPM, div = 64) ALARM
fan5:        0 RPM  (min = 10546 RPM, div = 8) ALARM
Sys Temp:    -65°C  (high =    +0°C, hyst =  +127°C)  
CPU Temp:  +20.0°C  (high = +127.0°C, hyst =  +0.0°C)   ALARM
AUX Temp:  -65.0°C  (high = +127.0°C, hyst =  +0.0°C)  

coretemp-isa-0000
Adapter: ISA adapter
Core 0:       +7°C  (high =   +85°C)                   

coretemp-isa-0001
Adapter: ISA adapter
Core 1:      +11°C  (high =   +85°C)  
```

---

