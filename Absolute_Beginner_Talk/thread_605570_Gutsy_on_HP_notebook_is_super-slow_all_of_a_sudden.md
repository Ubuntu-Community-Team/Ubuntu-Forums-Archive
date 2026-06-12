---
title: "Gutsy on HP notebook is super-slow all of a sudden"
date: 2007-11-07
forum: Absolute Beginner Talk
---

### Post by CheshireMac on 2007-11-07
Hey folks. I'm running Gutsy on a HP nc8000. It's been working fine except for the few issues I had with it back when, but those issues are fixed. 
My computer is a decent machine, and still runs very nicely for a machine it's age. Well, it did run nicely until three days ago. I'm not sure what has happened to it. When I type, I can type a letter and then watchit re-type on screen. Like I'm doing right now, I've got about 15 seconds of lag time. Programss and windows are behaving strangely too. Even Gnometris is dropping the bricks slowly. ~LOL~ Can someone help with this? 
I also did a printout of 'free -m'. Here it is.
```
mac@mac1:~$ free -m
             total       used       free     shared    buffers     cached
Mem:           503        497          5          0         22        289
-/+ buffers/cache:        185        318
Swap:         1474          0       1474
```
Thanks for aany help.

---

### Post by Pumalite on 2007-11-07
You are maxed out in your memory.

---

### Post by CheshireMac on 2007-11-07
This is what I figured. I'm wondering if it's because I've got faulty memory, or if I need to strip my system down. How would I go about stripping it, too? I'd like to keep Gnome.

---

### Post by Pumalite on 2007-11-07
Can you increase you RAM? That's the best solution.

---

### Post by CheshireMac on 2007-11-07
> **Pumalite said:**
> Can you increase you RAM? That's the best solution.
~LOL~ The biggest reason I use Ubuntu is because I'm cheap. ~LOL~ That, and this is a laptop. Only so much to do. I could, but it worked fine before, so why upgrade when you can just fix?

---

### Post by anaconda on 2007-11-07
> **Pumalite said:**
> Can you increase you RAM? That's the best solution.

Hmm. interesting. With feisty 512MB was always enough, even when running windows in vmware

Does gutsy really eat THAT much more ram?

I would suggest first to close those programs that eat too much memory, and then consider if those programs are really necessary, and only then to buy more RAM if you think you still need it..

you can use eg. "top" from terminal to find out which programs use lots of ram..

---

### Post by hyper_ch on 2007-11-07
what compiz effect do you have activated? I noted a few of those are really heavy on ram.

---

### Post by CheshireMac on 2007-11-07
I've done away with Avant, Emerald, and a couple other shiny-options that I think may be better suited for my next computer. It boosted my readout to more than 100m. That's comforting. I'm wondering what I might do to slim it down some more. I have basic graphics activiated. I don't want to eat up my system with eye-candy. I don't have any widgets and I don't run anything non-default except for Azureus and that's not even on right now.
What about X-org? Is that something I'll want to keep?

---

### Post by mivo on 2007-11-07
Does **sudo top** show anything that hogs your CPU when your system is responding slowly? You can also kill Tracker, just for testing purposes, to see if there is any improvement. Your swap hasn't been touched, it seems.

Yes, you want to keep X. ;)

---

### Post by hyper_ch on 2007-11-07
or better than top is htop (IMHO)

```

sudo apt-get install htop

```

and then just run it in the terminal:
```

htop

```

---

