---
title: "Firefox, Terminals and Windows buttons."
date: 2006-01-05
forum: Absolute Beginner Talk
---

### Post by Kraftwerk on 2006-01-05
*Breezy* Support and Dapper *Development* just seemed *wrong* so I'll just ask over here:

Oh, btw, I'm running Dapper! As my primary desktop OS even!
Things seem to be running smoothly, XFCE *rocks*, but I'm experiencing a few issues.

**1.** Mousebuttons 4 and 5 act like Mouse1 in Firefox and middleclick scrolling doesn't seem to be working either.
I've already changed the mouse section in xorg.conf, already nuked my firefox profile. oh and I changed that middlepastethingy in about:config.
Can I bind a mousebutton to a keycombination?

**2.** I'd like to make the Windows and the button-without-a-proper-name-right-next-to-it buttons less of an embarrassment and bind them to nautilus and the terminal, how do I assign keyboard shortcuts in XFCE?

**3.** Is there a way to create shorter names for terminal commands? *'apt'* instead of *'sudo apt-get'* for example.

Thanks in advance, and yes, I know I shouldn't be screwing around with Dapper, things might break and/or explode without warning maiming me for life etc etc etc. :p

---

### Post by mostwanted on 2006-01-05
[QUOTE=Kraftwerk]
**3.** Is there a way to create shorter names for terminal commands? *'apt'* instead of *'sudo apt-get'* for example.[/QUOTE]


I'll answer this one:

You can't do commands + arguments this way, but you can do commands. You're probably able to do it with arguments as well if you do some bash wrestling.

Go into the terminal and do:

```
$ sudo ln -s /usr/bin/apt-get /usr/bin/apt
```

You'll still have to do sudo, but this way it's at least shortened to apt.

---

### Post by Seq on 2006-01-05
[QUOTE=mostwanted]I'll answer this one:

You can't do commands + arguments this way, but you can do commands. You're probably able to do it with arguments as well if you do some bash wrestling.

Go into the terminal and do:

```
$ sudo ln -s /usr/bin/apt-get /usr/bin/apt
```

You'll still have to do sudo, but this way it's at least shortened to apt.[/QUOTE]

I'm on a windows machine at work, but a better method would be to alias in either ~/.bashrc or ~/.bash_profile . I cannot remember which is preferred offhand, but either should work.

From memory, this should work:

alias apt="sudo apt-get"

though there is more to the apt package manager than apt-get itself :)

---

### Post by carlosqueso on 2006-01-05
For question 3, you can.  you need to edit your .bashrc file ```
sudo gedit .bashrc
```  Scroll to where it has aliases and add ```
alias apt='sudo apt-get'
``` for example.  it's just alias <what you want to type>='<what you want it to mean>'.  It's probably bad practice, but I use it because I forget the spaces on cd ..  

EDIT: Dang....I'm too slow ALWAYS! ;)

---

### Post by benplaut on 2006-01-05
the mousebutton issue may have something to do with different terminology in xorg.conf.

button one is left-click
button two is middle click
button three is right click

scroll up and down are usually 4 and 5, but this can change, depending on the mouse.

dunno of this helps, but good luck!

---

### Post by Kraftwerk on 2006-01-05
Thanks for the replies, that whole alias thing works like a charm. It's exactly what I was looking for!

Oh and btw, about that mouse problem, I already tried switching 4 and 5 with 6 and 7 in xorg.conf but all that did was replace mwheelup and down with page back and forward instead of scrolling up and down. both sidebuttons still refuse to operate properly, which is odd because you'd THINK they would replace the scrollwheel.

It IS a Microsoft mouse though.. could explain a lot ;)

---

### Post by Chipmunk on 2006-01-05
Never thought of that, I am using a microsoft mouse on my Ubuntu system. It's only the bog-standard 2 buttons +middle clicky scrollwheel, but it works fine. Interestingly, it didn't on the same system with XP ;)

---

