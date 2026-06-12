---
title: "[SOLVED] ATI again"
date: 2007-08-09
forum: Absolute Beginner Talk
---

### Post by ravendiana on 2007-08-09
Ok I'm completely new to this...

I'm tring to run NWN on my machine, did all the linux updates and it's mostly in there except the graphics won't run, so  yeah graphics card. On a fun side note HIS does not seem to belive my particular video card exisitis in the firstplace

Anyway, I read the sicky about ATI cards, and I have no idea what I just read.  I think it was basically telling me to get a new set of drivers and install them, but I couldn't figure out Where I was suppose to get those drivers and It looked like I needed to emulate windows at some point to get them installed?

could someone provide a slightly more absolute beginner version of the instructions?

thanks

Diana

---

### Post by splintercellguy on 2007-08-09
Try Envy, it also works for ATI: [http://www.albertomilone.com/nvidia_scripts1.html](http://www.albertomilone.com/nvidia_scripts1.html)

---

### Post by overdrank on 2007-08-09
> **ravendiana said:**
> Ok I'm completely new to this...

I'm tring to run NWN on my machine, did all the linux updates and it's mostly in there except the graphics won't run, so  yeah graphics card. On a fun side note HIS does not seem to belive my particular video card exisitis in the firstplace

Anyway, I read the sicky about ATI cards, and I have no idea what I just read.  I think it was basically telling me to get a new set of drivers and install them, but I couldn't figure out Where I was suppose to get those drivers and It looked like I needed to emulate windows at some point to get them installed?

could someone provide a slightly more absolute beginner version of the instructions?

thanks

Diana

HI and welcome
Then instruction are meant to be used in the terminal located under applications, accessories, terminal. Here is a link to help with the command line ( also known as terminal)
[http://doc.gwos.org/index.php/CommandLineBeginners](http://doc.gwos.org/index.php/CommandLineBeginners)

---

### Post by Hospadar on 2007-08-09
The easiest way to get your drivers working I have always found is with envy.  You should read up on command line stuff a little first just so you are comfortable with what's going on and have a little better idea how things are happening.

The best way to use envy is to use the text interface, that way it can restart your xserver (the thing that handles in and output, so that you can use the drivers after you install them)

you'll want to go to a text terminal with ctrl-alt-F1 (you can get back to the gui with ctrl-alt-F7) then login to it with your normal info.  than install envy with apt ```
sudo apt-get install envy
```
the sudo part allows you access to system files, so you will need to use it for administrative tasks.  just use your user password when it asks for one.

Then, run envy with ```
sudo envy -t
``` and you will get a little interface that is pretty straightforeward, have it install the ati drivers for you, and let it edit the config file and restart the xserver.  ideally, this will be all you need to do. However, if the xserver does not start up, you will need to remove those drivers and try something else.

to remove them, get back to the text terminal with ctrl-alt-F1 (if you arn't already there) and do another ```
sudo envy -t
``` and use the dialog to remove your ati drivers, let it edit your config file and restart the xserver.

write down whatever error messages you get if it doesn't work so we can try to fix it.

---

### Post by igknighted on 2007-08-09
What ATI card do you have before you go on a wild goose chase for drivers...

If it is anything other than a new HD card or an x1*** card, you might be better served with the OSS drivers rather than FGLRX.

---

### Post by ravendiana on 2007-08-10
my card is an HIS ATI radeon x1600pro pciexpress card, which HIS calims doesn't exisit.  what I'm confused about in the instructions is that they frequently tell me to run programs without telling me if I <u>Have</u> those programs or <u>where</u> to get them if I don't..Do I need to get this envy thing or do I have it?.

If I've got it right...

Once I have envy and put it in my main directory, then I follow the instructions as provided, but how do I know if I have it?

err  I tried to download envy and It wolt let me :: Error dependancy not satisfiable: modual-assisatant

Diana

---

### Post by ravendiana on 2007-08-14
envy never did work, I found something on the Neverwinter nights linux froum that did, but I don't remeber what it was now,  sorry  I should be here for others  :(

---

### Post by misfitpierce on 2007-08-14
I've had it where Envy didn't work the first time then I just hit install ATI driver again and it reconfiged xorg again and restarted and fglrxinfo pulled up and said it worked.

---

### Post by ravendiana on 2007-08-14
it wasn't that envy wouldn't work to find the driver it was that envy wouldn't install at all

---

### Post by tadada on 2007-08-14
you could try the restricted driver if you havn't already (go to system>admin>restricted driver manager and enable the ATI one (though there might be a problem because I am pretty sure it detects your card and choses the correct restricted driver but it is worth a try (I tun ATI raedon x1300 PRO fine 3-D games and all using the restricted I belive it is called FGLRX))

---

