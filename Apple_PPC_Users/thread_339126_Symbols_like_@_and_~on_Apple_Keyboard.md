---
title: "Symbols like @ and ~*on Apple Keyboard"
date: 2007-01-15
forum: Apple PPC Users
---

### Post by mbrennwa on 2007-01-15
Dear all,

(I posted the below question to the Beginners Talk forum first, but I thought I'd also post it here)

I just installed Ubuntu 6.10 on my G4 PowerBook. I knew how to type symbols like @ and ~ on Mac OS X, but this seems not to work the same way in Ubuntu (Note: I'm writing this in Mac OS X, not Linux...). Also, the numeric keypad seems to be dead. Please help me use my keyboard...

Matthias

---

### Post by samden on 2007-01-16
Did you select the correct keyboard layout while installing? I'm not sure how to change it now, but I am sure someone will have a suggestion. However are you using an American keyboard, a British one or what? I have a British keyboard but told Ubuntu it was an American one so I could type a hash sign, as this is necessary sometimes in the terminal and I am not sure how to type hash from my keyboard as it does not show this symbol. And I figured I was unlikely to have to type a pound sign much anyway!

Note this when deciding on what layout to use, make sure your layout includes the hash sign! I will be interested in what people say on this thread.

---

### Post by terryeden on 2007-01-17
I had a non-working  numeric keypad.  I fixed it by hitting num-lock!

Also, when installing Ubuntu, go through the Keyboard detection section - should make sure all the keys on the kybd are working as they should.

---

### Post by Tommy on 2007-01-21
> **terryeden said:**
> I had a non-working  numeric keypad.  I fixed it by hitting num-lock!

Also, when installing Ubuntu, go through the Keyboard detection section - should make sure all the keys on the kybd are working as they should.

If you don't want to go through the whole install process again, you can open a terminal and type this:
```
sudo dpkg-reconfigure xserver-xorg
```

For most of the entries, just accept what it says, but watch specifically for the keyboard options and choose the ones that seem right. And if after configuring xserver-xorg your display gets royally screwed up or something, just switch to a virtual terminal and go into the /etc/X11/ directory and copy the xorg.conf.<today's_date> file to xorg.conf and restart the X server.

But if you're not using the standard Apple hardware, you should also try some Google searches with <your keyboard model> xorg. It may be that it's not being detected correctly.

---

### Post by MyNdWaRp on 2007-01-21
I also had this issue, and my mac keyboard does "NOT" have a numlock key, however; after pressing the clear key (located where the numlock key would be on an american qwerty keyboard) the numbers began to work. Hope this helps you out.

---

### Post by gnomeza on 2007-01-22
> **samden said:**
> I have a British keyboard but told Ubuntu it was an American one so I could type a hash sign...

If you have a compose key configured then you can type a hash sign as:  compose, +, +.

I *highly* recommend getting the compose key working - it's a killer feature for me.
Not being able to use it on other systems makes me cry...

On my powerbook I use the enter key to the right of the space as compose (same location as on Sun systems).

The latest authoritative list of compose combinations for en_US.UTF-8 is here [http://webcvs.freedesktop.org/xorg/lib/X11/nls/en_US.UTF-8/Compose.pre?revision=1.3&view=markup](http://webcvs.freedesktop.org/xorg/lib/X11/nls/en_US.UTF-8/Compose.pre?revision=1.3&view=markup)

---

