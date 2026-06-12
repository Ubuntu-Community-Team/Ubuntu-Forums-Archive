---
title: "LimeWire won't open!"
date: 2006-09-26
forum: Absolute Beginner Talk
---

### Post by voodoonirvana on 2006-09-26
I have been using LimeWire for about two weeks now with not a single problem. I have tried restarting, opening with the terminal, moving it to my Home folder and then opening it with the the terminal. I know about the case sensitivity thing too so its not that. When I click on the icon, it simply wont open.

---

### Post by croak77 on 2006-09-26
When you open it from a terminal, are there any error messages?

---

### Post by voodoonirvana on 2006-09-27
> **croak77 said:**
> When you open it from a terminal, are there any error messages?

No it simply tells me "command not found."
Am I opening it right? All I have to do is type LimeWire right?

---

### Post by Perfect Storm on 2006-09-27
Have you checked if it still is installed (accidently uninstall it?)
```
locate limewire
whereis limewire
```

---

### Post by voodoonirvana on 2006-09-27
> **Artificial Intelligence said:**
> Have you checked if it still is installed (accidently uninstall it?)
```
locate limewire
whereis limewire
```

Yeah it says it's in usr/lib/LimeWire

---

### Post by Perfect Storm on 2006-09-27
What about in /usr/bin
?
There should be a limewire shript in /usr/bin

Try limewire in the terminal (linux is case sensitive)

---

### Post by voodoonirvana on 2006-09-27
> **Artificial Intelligence said:**
> What about in /usr/bin
?
There should be a limewire shript in /usr/bin

Try limewire in the terminal (linux is case sensitive)

Yes there is a shell script in there. And yes I know the terminal is case sensitive, still doesnt work.

---

### Post by Perfect Storm on 2006-09-27
Strange...wonder if the launcher script is damaged.


Try this:
```

cd /usr/lib/LimeWire
sh runLime.sh
```

---

### Post by voodoonirvana on 2006-09-27
> **Artificial Intelligence said:**
> Strange...wonder if the launcher script is damaged.


Try this:
```

cd /usr/lib/LimeWire
sh runLime.sh
```

Ok so I got this:

runLime.sh: 44: Syntax error: "(" unexpected (expecting "}")


Bad news?

---

### Post by Perfect Storm on 2006-09-27
By any chance you are running Ubuntu Edgy?

---

### Post by voodoonirvana on 2006-09-27
> **Artificial Intelligence said:**
> By any chance you are running Ubuntu Edgy?

Nope, Im using dapper.

---

### Post by Perfect Storm on 2006-09-27
Hmmm...Then I don't know what's wrong. I know that Limewire on edgy is broken (back in 23 aug) - [http://www.gnutellaforums.com/showthread.php?t=60358](http://www.gnutellaforums.com/showthread.php?t=60358)

Did an update of limewire been added reasonly?

---

### Post by voodoonirvana on 2006-09-27
> **Artificial Intelligence said:**
> Hmmm...Then I don't know what's wrong. I know that Limewire on edgy is broken (back in 23 aug) - [http://www.gnutellaforums.com/showthread.php?t=60358](http://www.gnutellaforums.com/showthread.php?t=60358)

Did an update of limewire been added reasonly?

No, not that I know of. Do you think it could be something conflicting with it? I recently downloaded gstreamer but that about it in the past week and this just started happening yesterday.

---

### Post by Perfect Storm on 2006-09-27
Sorry, I can't answer that :-/


Well, try with a reinstall of limewire and see if it solves anything. Also before reinstalling delete .LimeWire in your home folder.

---

### Post by voodoonirvana on 2006-09-27
> **Artificial Intelligence said:**
> Sorry, I can't answer that :-/


Well, try with a reinstall of limewire and see if it solves anything. Also before reinstalling delete .LimeWire in your home folder.

Okay, should I do this through the terminal or just move all LimeWire stuff to the trash?

---

### Post by Perfect Storm on 2006-09-27
You can just right click on .LimeWire in your home folder and click "Move to trash".

---

### Post by voodoonirvana on 2006-09-27
Okay I just re-installed and it still is not opening! :(

---

### Post by Perfect Storm on 2006-09-27
Sorry, can't help you any further.


Well, you can try frostwire it's a free version of limewire.

---

