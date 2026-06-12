---
title: "Getting CPU usage"
date: 2006-12-01
forum: Absolute Beginner Talk
---

### Post by meniscus on 2006-12-01
Someone told me the following line to get the CPU temperature from the hardware monitoring command "sensors"

```
sensors | perl -ne 'if ( /CPU Temp:\s*\+(\d+)/ ) { print $1 . "\n"; }'

```



Im trying to get the the command line to show me just the CPU usage from the command "top" 





```
top | perl ...............
```


 
I dont know what the code given to me means so cant modify it. Can anyone explain?

---

### Post by lloyd_b on 2006-12-01
I have no clue as to the perl, but:

top -n 1 | grep "Cpu"

Will produce a line like the following:

Cpu(s): 20.1%us,  1.1%sy,  0.1%ni, 76.3%id,  2.2%wa,  0.2%hi,  0.0%si,  0.0%st

Is this what you're looking for?

An explanation of the command:

top -n 1 = "Run the command top, but stop after one pass"
| = "Pipe output from preceeding command to trailing command"
grep "Cpu" = Only display lines containing the string "Cpu"

Lloyd B.

---

### Post by meniscus on 2006-12-01
> top -n 1 | grep "Cpu"

Will produce a line like the following:

Cpu(s): 20.1%us, 1.1%sy, 0.1%ni, 76.3%id, 2.2%wa, 0.2%hi, 0.0%si, 0.0%st

Thanks for those explanations.




Is there any way tou can modify the command to return just the values themselves? 

something like

```
top -n 1 | grep "Cpu" ...whatever
``` (to get just the user percentage)(us%)

and it ll return just the value "20.1" to the terminal?

---

### Post by lloyd_b on 2006-12-01
This is getting tricky.  A couple of issues pop up.

1.  By default, top's output includes "escape sequences" (hidden sequences that control things like bold, reverse video, cursor positioning, etc).  This is a minor issue - these codes can be eliminated by using top's "-b" option.
 
2.  When you run "top -n 1", the values you get for Cpu usage ARE THE VALUES SINCE THE LAST REBOOT.  Only on the second and later passes do you get a good snapshot of what the system is doing at the moment.

The second problem is trouble - it means calling top with a "-n 2" option, and then finding a way to ignore the first "Cpu" line.

Why exactly are you trying to get this number?  This isn't an idle question - If I (and the rest of the folks on the forum) understand what the final objective is, we may be able to spot an easier-to-accomplish method to get there....

It may turn out that this is easier to accomplish via Perl (about which I know very little.)

Okay - Here's a command:

```
top -b -n 2 | grep "Cpu" | tr '\n' '+' | cut -d '+' -f2 | cut -b 8-12
```

English translation:

"Run top in batch mode, 2 passes"
"Pipe to grep, searching for "Cpu""
"Pipe to "tr", translating newlines to plus signs"
"Pipe to "cut", returning everything after the first plus sign"
"Pipe to "cut", return the eighth through twelfth characters"

This works, but it's a little convoluted for my taste....

BTW: If you want to better understand things like "grep", "tr", and "cut", in a terminal window you can type "man {command}" and get the manual page for that command.

Lloyd B.

---

### Post by meniscus on 2006-12-01
I want the number to write my own systems monitor.

I was doing tutorials but was told the best way to learn to is start a project for myself!

---

### Post by meniscus on 2006-12-01
Ohh! Thanks very much for those explanations.Very much appreciated.

---

### Post by lloyd_b on 2006-12-01
> I want the number to write my own systems monitor.

I was doing tutorials but was told the best way to learn to is start a project for myself! 

Some info that may be of use to you - the CPU information from "top" (as well as pretty much every system monitor on a Linux system) comes from the information in the file "/proc/stat". 

You can "cat /proc/stat" to obtain this information, but it is NOT intended to be easily read by a person - it's formatted to make it easy for a program to parse.

For more info regarding this, look at "man proc" - it has the details.

Lloyd B.

---

### Post by meniscus on 2006-12-05
thanks

---

