---
title: "[SOLVED] Start aMule (or any program) when screensaver starts???"
date: 2007-07-11
forum: Absolute Beginner Talk
---

### Post by sad_iq on 2007-07-11
Ok...I would like to know if there's a way to start aMule (or Amarok...etc.) when the screensaver starts...I can't use cron(can I??)...and I can't find any info here...so posting a thread is my only option!!!

---

### Post by sad_iq on 2007-07-12
Anyone???

---

### Post by mpeters on 2007-07-12
It's a bit quick and dirty, but paste the following into a file and save it as something like /home/sad_iq/bin/screenwatch.py. 

```

#!/usr/bin/python

import os
import time

RUNME = "aMule"
ARGS = ""

screensaver_started = 0
running = 0

while 1:
	active = 0
	out = ""
	pid = 0

	if screensaver_started == 0:
		# Don't do anything if the screensaver isn't running
		s = os.popen("pidof gnome-screensaver")
		spid = s.read()
		s.close()
		if len(spid) > 0:
			screensaver_started = 1
	else:
		h = os.popen("gnome-screensaver-command -q", "r")
		out = h.read()
		active = out.find("inactive")
		h.close()

		if active < 0 and running == 0:
			os.system("%s %s &" % (RUNME, ARGS))
			running = 1
		elif active > 0 and running == 1:
			os.system("pkill %s" % RUNME)
			running = 0
	time.sleep(5)

```

As this is a Python script, make sure the indentation is the same as it is here after you have pasted it.

Edit the values RUNME to reflect the command you want to run and ARGS for any arguments you want to pass the command. eg if you want to run 
```
xmms foobar.mp3
```

edit the file to read:

```

RUNME = "xmms"
ARGS = "foobar.mp3"

```

leave ARGS blank if you wish. 

Make the script executable:

```
chmod 750 /home/sad_iq/bin/screenwatch.py
```

You can test the script by running it from a command line and then starting up the screensaver manually:

```

/home/sad_iq/bin/screenwatch.py
gnome-screensaver-command -a

```

(I put a delay of 5 seconds before your program executes or shuts down after starting or stopping the screensaver.)

Now set the script to run when you log in by adding it to your startup session via System -> Preferences -> Sessions. 

Enjoy.

---

### Post by sad_iq on 2007-07-12
Hey...Finally ...someone answered...Thanks...only a little problem...I use Kubuntu...so I think that gnome-screensaver isn't available (don't know if installing it will make it the default screensaver app in kubuntu)...so..all I have to do is find the replacement...and to test your script :) ...Hopefully it works!!! Great Job Anyway!!!

---

### Post by mpeters on 2007-07-12
> **sad_iq said:**
> Hey...Finally ...someone answered...Thanks...only a little problem...I use Kubuntu...so I think that gnome-screensaver isn't available (don't know if installing it will make it the default screensaver app in kubuntu)...so..all I have to do is find the replacement...and to test your script :) ...Hopefully it works!!! Great Job Anyway!!!

Ah! Didn't notice you were using Kubuntu. I'm not sure what KDE uses for a screensaver. You could try installing gnome-screensaver but I'm not sure how that would work....

Whilst checking to see if I could find what KDE uses I discovered you can do this very easily with xscreensaver if you're using that, or are willing to switch. The man page even provides an example Perl script. From the xscreensaver-command man page:

```

#!/usr/bin/perl

my $blanked = 0;
open (IN, "xscreensaver-command -watch |");
while (<IN>) {
    if (m/^(BLANK|LOCK)/) {
        if (!$blanked) {
            system "sound-off";
            $blanked = 1;
        }
    } elsif (m/^UNBLANK/) {
        system "sound-on";
        $blanked = 0;
    }
}

```

replace *system "sound-off";* and *system "sound-on";* with the commands to run when the screensaver starts and stops respectively. This script also assumes you've set the screen to blank out though.

Set the script up to run the same as I explained for mine.

---

### Post by sad_iq on 2007-07-13
Ok...Works great...better than I expected...(the xscreensaver that is)...and it doesn't have to be a blank screen...amule now starts when the screensaver activates :). Just replaced ```
if (m/^(BLANK|LOCK)/) {
        if (!$blanked) {
            **system "sound-off";**
            $blanked = 1;
        }
``` with ```
if (m/^(BLANK|LOCK)/) {
        if (!$blanked) {
            **system "amule";**
            $blanked = 1;
        }
``` 

Thanks again...Great job!!!

---

