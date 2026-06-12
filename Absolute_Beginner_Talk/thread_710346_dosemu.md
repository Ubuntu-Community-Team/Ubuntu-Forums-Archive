---
title: "dosemu"
date: 2008-02-28
forum: Absolute Beginner Talk
---

### Post by jakl_53 on 2008-02-28
i have just installed dosemu and can run the only game i have tried so far. nothing is wrong except for the fact that its a FPS and when i turn around the cursor moves out of the window and i cant turn that way. is there anyway i can stop this from happening?

---

### Post by SOULRiDER on 2008-02-28
The program should have an option somewhere to "capture" the mouse. I havnt used dosemu, but i have used DOSBox before and as far as I can remember it does this by default.

---

### Post by jakl_53 on 2008-02-28
i dont know how to change the options though..

---

### Post by y-lee on 2008-02-28
I don't use dosemu but I found [10. The DOSEMU mouse]("http://dosemu.sourceforge.net/docs/README/1.1.3.7/mouse.html") online.

It seems there is a key press  that "when pressed with both Ctrl & Alt held down will turn on the mouse grab, which restricts the X mouse to the dosemu window, and gives dosemu complete control over it." Which key does this is  is controlled by the **$_X_mgrab_**key in the system file  **/etc/dosemu.conf**.

Read the article look at your dosemu.conf file and try to figure it out.

If ya have problems post back and if possible post the dosemu.conf file :)

---

### Post by jakl_53 on 2008-02-28
i think i know what to do to that file. but i need to save the file. but i cant do it. its says i dont have permission. how do i do it? im the only one on my computer..

"# KeySym name to activate mouse grab, ""=off. Default: "Home" (ctrl+alt+home)"
would this be the line i change? change it to on? but i need to know how to save the changes..

---

### Post by y-lee on 2008-02-28
> **jakl_53 said:**
> i think i know what to do to that file. but i need to save the file. but i cant do it. its says i dont have permission. how do i do it? im the only one on my computer..

I should have mentioned that the location of the file means it has root permissions. so

```
sudo gedit
```

Load the file make changes to it and save it, and close gedit. For safety sakes you should back it up somewhere first :)

---

### Post by y-lee on 2008-02-28
I don't use dosemu but that file should already have an entry for the **$_X_mgrab_key.**. Whatever key is specified might be easier to just use it instead of change it. :)

---

### Post by jakl_53 on 2008-02-28
thank you. i didnt even think about that. well im about to find out if it works..

---

### Post by jakl_53 on 2008-02-28
> **y-lee said:**
> I don't use dosemu but that file should already have an entry for the **$_X_mgrab_key.**. Whatever key is specified might be easier to just use it instead of change it. :)

but it seems that it is off. whouldnt i turn it on?

---

### Post by jakl_53 on 2008-02-28
well it works now. thanks a lot. now my sound doesnt work. time to find out whats wrong with that. but seriously thanks a lot.

---

### Post by y-lee on 2008-02-28
> but it seems that it is off. whouldnt i turn it on?

Does the key not work? the value there might be a number representing the key.

---

### Post by y-lee on 2008-02-28
Ok i just saw your last edit it looks like you do need to turn it on. And btw I fixed the link above, should've told me it was broke. Trying to cook as I do this. :lolflag:

---

### Post by jamillikan on 2008-03-19
Can someone resolve the issue with printing with DOSEMU 1.4 in Gutsy?  My computer has no parallel ports.  When I try to print, nothing prints.  This was no an issue with DOSEMU 1.2.2 on Feisty and Edgy.

$_printer = "ML2150" does not work.

Unless $LPT1 is set to "" I cannot even get into my program.  Is there a resolution for printing from within DOSEMU when no parallel port is present on the computer?  

This worked perfectly in DOSEMU 1.2.2.  Any help is appreciated.  I'm clueless and out of ideas.

Thanx,

Joe

---

