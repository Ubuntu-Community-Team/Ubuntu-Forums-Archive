---
title: "Upon resume from hibernation screen remains black."
date: 2007-09-20
forum: Absolute Beginner Talk
---

### Post by abhiroopb on 2007-09-20
I have read some of the other threads regarding the screen blanking issue. Unfortunately nothing has worked for me.

Using the uswsup I have managed to get hibernate and suspend working. It even worked at one time. Now unfortunately for some reason when it resumes from hibernation I just get a black screen. I know things are still running as I hear pidgin beeping, and the disk activity led is on, yet the screen is black with the mouse pointer on screen.

I have a HP dv5242ea
nvidia geforce go 7400 256mb
1gb ram

I am using beryl. This may be a problem but it is quite useful and I don't want to sacrifice it. I have disabled the sync to VBlank command as well. 

Its strange as it worked fine a little while back and then suddenly its not working. The change happened without me changing any other settings!

Any thoughts?

---

### Post by mridkash on 2007-09-20
Happens with my pc too!

I have nvidia graphics and compiz fusion installed. upon resume from hibernate the screen goes blank with the mouse showing and i have to hit ctrl-alt-backsp to restart the enviornment.

Just because of that reason, I've disabled power management, which is bad!

---

### Post by abhiroopb on 2007-09-20
Used the following:

this one goes in /etc/acpi/suspend.d/25-beryl-suspend.sh
Code:

#!/bin/bash
# /etc/acpi/suspend.d/25-beryl-suspend.sh

pids=""
for pid in `pidof /usr/bin/beryl-manager`
do
ps -o comm= --ppid $pid | grep -q '^beryl$'
if (($? == 0)); then
pids="$pid $pids"
kill -USR2 $pid
fi
done
export BERYLMGRPIDS="$pids"

and this one goes into /etc/acpi/resume.d/99-beryl-resume.sh
Code:

#!/bin/bash
# /etc/acpi/resume.d/99-beryl-resume.sh

for pid in $BERYLMGRPIDS
do
(sleep 10 && kill -USR2 $pid)&
done

Works great now. But its still a LOT slower than windows hibernate, but that isn't such a big deal for me.

---

### Post by nickzeff on 2007-09-24
YESS!!!! Thank you SO much!

This just fixed my Dell D820 suspend problems after months of frustration!

Huge thanks!

---

### Post by PantsMan on 2008-04-03
Just to add to the knowledge, I was having similar issues on my HP Pavilion DV5120EU (ATI Radeon Xpress 200M) in Heron Beta with Compiz; I copied abhiroopb's scripts and now with some modifications it all works fine:

*/etc/acpi/suspend.d/25-compiz-suspend.sh*
```
#!/bin/bash
# /etc/acpi/suspend.d/25-compiz-suspend.sh

pids=""
for pid in `pidof /bin/sh`
do
ps -o comm= --ppid $pid | grep -q '^compiz.real$'
if (($? == 0)); then
pids="$pid $pids"
kill -HUP $pid
fi
done
declare -x COMPIZPIDS="$pids"

```

*/etc/acpi/resume.d/25-compiz-resume.sh*
```
#!/bin/bash
# /etc/acpi/resume.d/25-compiz-resume.sh

for pid in $COMPIZPIDS
do
(sleep 10 && kill -HUP $pid) &
done

```

---

