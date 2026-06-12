---
title: "Keyboard shortcut launcher problem"
date: 2008-01-31
forum: Absolute Beginner Talk
---

### Post by dinostabOMG on 2008-01-31
I have the Win-keys mapped to "hyper." Here is screenshot of some of my keyboard shortcuts:

[IMG]http://josephjacir.com/stuff/Screenshot-Keyboard Shortcuts.png[/IMG]

The only of of these shortcuts that involve the Win key that actually works is Mod4+T - Run a Terminal. The rest do nothing when I press them. Why?? And how can I fix it?

This problem would be less baffling if Mod4+T didn't work either, but I just don't know what this could be about.

---

### Post by dinostabOMG on 2008-02-02
I should perhaps add that I have my keyboard setup with the Generic 101-key PC settings, and US English as the layout. I also tried changing the Win key to Super, it still doesn't work.

---

### Post by kaiju on 2008-02-02
i should first admit that i don't actually know what could cause the problem you are experiencing with the gnome keybindings.

but... if you can't find a solution to it, you might want to try disabling it and using xbindkeys instead. from my experience outside of fluxbox i can say that it's a very powerful keybinder. you would need to add all the commands manually of course, which might be a drawback for you, but man xbindkeys really tells you all there is to know.

---

### Post by dinostabOMG on 2008-02-02
Thanks for the suggestion, kaiju. How can I disable the default keyboard shortcut manager so they don't conflict?

Love your icon by the way!

---

### Post by dinostabOMG on 2008-02-02
I added this to .xbindkeysrc:

```
"gcalctool"
 Mod4 + c
```

It didn't work. So I ran xbindkeys -k and pressed Left Win Key + C, which is what I was trying to cause to run the calculator. This is what I got:

```
Press combination of keys or/and click under the window.
You can use one of the two lines after "NoCommand"
in $HOME/.xbindkeysrc to bind a key.
"NoCommand"
    m:0x50 + c:115
    Mod2+Mod4 + Hyper_L

```

Mod2 is apparently Num Lock? But I don't have its detection enabled in .xbindkeysrc. I'm not sure what Hyper_L means, is this in addition to Mod4? I don't know what m:0x50 + c:115 means. I certainly wasn't pressing five keys, if that is what this is implying. I changed the Win keys to Meta instead of hyper and the output changed to Meta_L instead of Hyper_L but this hardly seems to be the culprit.

---

### Post by cknight on 2008-02-03
This is a wild shot in the dark, as I'm not overly familiar with Gnome, but try changing your key bindings to lowercase.  E.g. 
```
Mod4 + H
```
becomes
```
Mod4 + h
```

Normal alphabet keys j(a,b,c,d,e,...) are generally recognized as lowercase by X.  E.g. pressing the 'H' key sends a key event to the kernel associated with the symbol 'h'.  Good luck!

---

### Post by kaiju on 2008-02-03
well if you take a look at the output of 'xbindkeys -k', you'll see that it clearly says 'You can use **one of the two lines** after "NoCommand"' :)
that means that in your .xbindkeysrc file you'll have not more and not less than

"gcalctool"
    m:0x50 + c:115

you could of course use the second variant instead, but that also contains Mod2 for numlock (which probably means this key shortcut should only work when numlock is on).
after saving the .xbindkeysrc file you have to give xbindkeys a HUP signal (look it up in 'man xbindkeys') and you are set.

to make it always load under gnome, you need to add xbindkeys to your session.
i don't know how you could completely disable the gnome keybinder, my bet would be to just disable the keys you don't need.

and then again, maybe someone here can help you make the gnome keys work and you won't need to bother. in any case, good luck ;)

---

### Post by dinostabOMG on 2008-02-03
Thanks for your help. I think it's starting to become clear that for some reason the Win key is not being detected properly, especially in combination with other keys. For now, I have set the calculator to run with Alt + keypad 0, which works fine. As I started to understand the output of xbindkeys -k, I realised that the C was not being detected at all, it was only detecting Mod4 + Meta_L. I think the GNOME keyboard manager must be doing the same thing, which is why those hotkeys don't work. Is this worth submitting a bug report about? Does anyone else experience this behavior? Surely if it were more widespread they would have noticed that most of the hotkeys don't work before releasing the distro...

---

### Post by kaiju on 2008-02-03
hm, interesting.
i tried 'xbindkeys -k' with windows button + c myself, and got the same output you quoted above, except that i have Super_L where you had Hyper_L.
this is what i got for control+c:
    m:0x14 + c:54
    Control+Mod2 + c
and this, for control+v:
    m:0x14 + c:55
    Control+Mod2 + v

however, the output for both win+c and win+v is the same:
    m:0x50 + c:115
    Mod2+Mod4 + Super_L
with this Super_L key taking the place of c:54 and c:55, respectively.
in my case, this substitution is probably caused by the fact that i already have these keys assigned to fluxbox's keygrabber.
could there be another program in control of these keys?
and what happens if you replace c:115 with c:54 in your config file?

---

