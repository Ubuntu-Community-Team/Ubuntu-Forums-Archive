---
title: "Can anyone tell me how to enable the &quot;paper plane&quot; effect in Gutsy?"
date: 2007-11-27
forum: Absolute Beginner Talk
---

### Post by shakajumbo on 2007-11-27
It may not be "useful" but it's the absolute COOLEST effect I've ever seen!!

Thanks :)

[http://www.youtube.com/watch?v=28T3JgdfnyE](http://www.youtube.com/watch?v=28T3JgdfnyE)

---

### Post by UtahApocalypse on 2007-11-27
You will need to enable Compiz and then select Animations.

---

### Post by timbounceback on 2007-11-27
sudo apt-get install ccsm

then go to system - preferences - advanced desktop effect settings and go to animations

---

### Post by Six_Digits on 2007-11-27
> You will need to enable Compiz and then select Animations.
> sudo apt-get install ccsm

then go to system - preferences - advanced desktop effect settings and go to animations

It should be easy to find but add this to "Window Match" when you add the effect:

```
(type=Normal | Dialog | ModalDialog | Utility | Unknown)
```

I have problems if I don't do this...

---

### Post by exactopposite on 2007-11-27
hey that's pretty cool

---

### Post by exactopposite on 2007-11-27
> **Six_Digits said:**
> It should be easy to find but add this to "Window Match" when you add the effect:

```
(type=Normal | Dialog | ModalDialog | Utility | Unknown)
```

I have problems if I don't do this...

what's that system info widget you have running to the right?

---

### Post by Six_Digits on 2007-11-27
Conky. Quite a fun little app.

[http://conky.sourceforge.net/](http://conky.sourceforge.net/)

It's downloadable in the repositories. Refer to that link for help or PM me.

---

### Post by exactopposite on 2007-11-27
> **Six_Digits said:**
> Conky. Quite a fun little app.

[http://conky.sourceforge.net/](http://conky.sourceforge.net/)

It's downloadable in the repositories. Refer to that link for help or PM me.
 i got it installed  but i don't see anything anywhere on my system to change the settings/preferences for it. I only looked for a minute or 2 tho. I'm about to go cook dinner and i'll be back later. I'd would imagine i can find the info on how to tweak it in the forums, but i'll pm you if i need some help. thanks for the reply.

---

### Post by Six_Digits on 2007-11-27
Theres no GUI for the settings, only a .conkyrc file you'll create and edit in your home directory.

---

