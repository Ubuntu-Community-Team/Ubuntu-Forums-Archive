---
title: "Extracting voltage value?"
date: 2006-12-05
forum: Absolute Beginner Talk
---

### Post by meniscus on 2006-12-05
Here is the output from lm sensors

```
VCore 1:   +1.30 V  (min =  +1.12 V, max =  +1.68 V)
VCore 2:   +1.49 V  (min =  +2.16 V, max =  +2.86 V)   ALARM
+3.3V:     +3.23 V  (min =  +3.14 V, max =  +3.47 V)
+5V:       +4.92 V  (min =  +4.76 V, max =  +5.24 V)
+12V:     +12.03 V  (min = +11.39 V, max = +12.61 V)
-12V:      +0.98 V  (min =  +0.00 V, max =  +0.00 V)   ALARM
-5V:       -2.56 V  (min =  -5.26 V, max =  -4.77 V)   ALARM
Stdby:     +5.00 V  (min =  +4.76 V, max =  +5.24 V)
VBat:      +3.18 V
fan1:     2909 RPM  (min =    0 RPM, div = 16)
fan2:        0 RPM  (min =  332 RPM, div = 16)
fan3:     3443 RPM  (min =  664 RPM, div = 8)
M/B Temp:    +35°C  (low  =   +15°C, high =   +40°C)   sensor = thermistor
CPU Temp:    +42°C  (low  =   +15°C, high =   +45°C)   sensor = diode
```


The following code used in a script extracts the CPU temperature

```
my $output = `sensors`;
	my $temp;
	if ( $output =~ /CPU Temp:\s*\+(\d+)/ ) {
    	$temp = $1;
	}
```


How do i modify it to "extract VCore 1" (My attempt returns the value "1"
and leaves out the  ".49"




My attempt!

```
my $output = `sensors`;
	my $votage;
	if ( $output =~ /VCore 1:[COLOR="Red"]\s*\+(\d+)/ [/COLOR]) {
    	$voltage = $1;
	}
```



In tuth i havent a clue what the code highlighted in red does!

---

### Post by kd_pease on 2006-12-05
If you replace the (\d+) with ([\d\.]+) it should work. The reason it's not working at the moment is because \d only matches numeric digits so it doesn't match the decimal point. The [\d\.]+ part means "match one or more numeric digits or decimal points." Note that the expression I've given would also match "1.2.3" so if that's a problem for you you'll need to tweak it.

---

### Post by meniscus on 2006-12-05
Thanks very much. That worked perfectly:)

---

