---
title: "Democracy and Ubuntu with Multiple Sound Cards - Need Help"
date: 2007-06-08
forum: Absolute Beginner Talk
---

### Post by Bob535 on 2007-06-08
It seems like Democracy (The 3rd Party Video Software) defaults to a soundcard without letting you chose which one. I have two in my system, one which doesnt function properly (onboard) and a PCI card. I run everything through the PCI card and sound works fine for all other applications (including VLC) however I am unable to get sound functioning inside democracy. (Playing the videos manually with VLC works however..)

Anyone able to help?
I have asked on the democracy forums, but no responses... 

I looked for a config file for democracy but was unable to find anything applicable to the situation.

---

### Post by bodhi.zazen on 2007-06-08
[list=number][*]List sound cards : ```
sudo asoundconf list
```


[*]Set default : ```
sudo asoundconf set-default-card <desired default card>
```

Where "<desired default card>" is replaced by the card in the first list you want to be default.


[*]Reboot (to test) ~ should work[/list]

---

### Post by Bob535 on 2007-06-08
Thanks man, that did do the trick.

---

### Post by kazik on 2007-06-11
> **bodhi.zazen said:**
> [list=number]
[*]Set default : ```
sudo asoundconf set-default-card <desired default card>
```
[*]Reboot (to test) ~ should work[/list]

_Do not sudo_ and you won't have to reboot. If you don't sudo, the changes are to user's ~/.asoundrc and you only need to restart the application. Some applications (Rythmbox for example) switch after just stop -> play. :)

---

### Post by bodhi.zazen on 2007-06-11
> **kazik said:**
> _Do not sudo_ and you won't have to reboot. If you don't sudo, the changes are to user's ~/.asoundrc and you only need to restart the application. Some applications (Rythmbox for example) switch after just stop -> play. :)

Thanks for the tip.

---

