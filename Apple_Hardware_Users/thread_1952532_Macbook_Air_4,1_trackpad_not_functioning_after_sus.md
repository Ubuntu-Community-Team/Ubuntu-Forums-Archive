---
title: "Macbook Air 4,1 trackpad not functioning after suspend"
date: 2012-04-04
forum: Apple Hardware Users
---

### Post by Kallun on 2012-04-04
Hello! :)

I got a Macbook Air 4,1 yesterday, I have 12.04 (64bit) running on it.

I have an issue with the trackpad. It functions absolutely flawlessly, apart from when the machine wakes from suspend.

Upon waking from suspend (suspend2RAM) I am unable to move the cursor... unless I click down and try and move it.

So, after waking, it doesn't respond to touch unless I'm actually pressing down on the pad so it's clicked in.

Anyone have any ideas on how I can fix this? Perhaps a script that re-launches the mouse input daemon after waking from suspend as a work around?

**EDIT** **FIX**

See my second post for a workaround :)

---

### Post by mr_manny on 2012-04-04
same here :(

found this bug link:
[https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-input-synaptics/+bug/970574](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-input-synaptics/+bug/970574)


will test reloading module later today...

---

### Post by Kallun on 2012-04-05
> **mr_manny said:**
> same here :(

found this bug link:
[https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-input-synaptics/+bug/970574](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-input-synaptics/+bug/970574)


will test reloading module later today...

Ah, well at least that's something!

Cheers for the reply :D Let me know

**EDIT** **FIX**

Okay, I've fixed it by reloading the module from suspend with a script called by pm-utils :D

See instructions below:

su to switch to root

Then:

```
cd  /etc/pm/sleep.d/
```

Then:

```
touch 99mouse-pad
```

Then use nano on the new file:

```
nano 99mouse-pad
```

Paste in the below:

```
#!/bin/bash
case $1 in
   hibernate)

       ;;
   suspend)

       ;;
   thaw)
       rmmod bcm5974; modprobe bcm5974
       ;;
   resume)
       rmmod bcm5974; modprobe bcm5974
       ;;
   *)
       ;;
esac

```

Then make it executable with:
```
chmod a+x 99mouse-pad
```

Then test it out! :D Works fine for me

---

### Post by dark_harmonics on 2012-04-05
This is a great solution for this problem and should be posted to the macbook Air 4,x configuration wiki.

---

### Post by Kallun on 2012-04-05
> **dark_harmonics said:**
> This is a great solution for this problem and should be posted to the macbook Air 4,x configuration wiki.

Wow, thanks! :D

How can we go about getting it there?

---

### Post by alx80 on 2012-04-08
I've just come across the same problem with my Macbook6,1 . Adding

[FONT="Courier New"]SUSPEND_MODULES="bcm5974"[/FONT]

to 

[FONT="Courier New"]/usr/lib/pm-utils/defaults[/FONT]

solved the issue for me.

My 2 cents

---

### Post by jackley on 2012-04-08
This worked perfectly. Definitely should be on the wiki. Thanks a lot!


Jim

---

### Post by lunar cranium on 2012-04-09
brilliant. thanks!

---

### Post by cyberco on 2012-04-10
Fixes the problem on a Macbook Air 3,2 as well.



> **alx80 said:**
> I've just come across the same problem with my Macbook6,1 . Adding

[FONT="Courier New"]SUSPEND_MODULES="bcm5974"[/FONT]

to 

[FONT="Courier New"]/usr/lib/pm-utils/defaults[/FONT]

solved the issue for me.

My 2 cents

---

### Post by ryanhellyer on 2012-04-14
Thanks very much for the fix. I was kinda frazzled for a few minutes there trying to figure out why my Mac had frozen. Then realised it was just the trackpad which had stopped responding. Was stoked to find this forum thread and relatively simple solution.

---

### Post by Kallun on 2012-04-16
Good stuff! Glad this has helped you guys :)

---

### Post by mistadman on 2012-08-08
New Macbook Air 5,2 here, and this process helped a great deal with my mouse not working correctly after resuming from a suspend.

On Ubuntu 12.04 LTS, I:

    Created the file: **/etc/pm/config.d/macbook_fix**, and added the line:

    ```

        SUSPEND_SUSPEND="bcm5974"
    
```


And now my Macbook Air: i7 2.0Ghz, 8GB RAM, 256GB SSD, is working beautifully with Ubuntu 12.04 LTS full install (No OSX)!

---

