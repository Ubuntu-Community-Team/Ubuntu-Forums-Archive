---
title: "how do I set my pci soundcard as the default?"
date: 2006-03-18
forum: Absolute Beginner Talk
---

### Post by stefenkillsit on 2006-03-18
I have a built in soundcard for my mobo, but I also have a better soundcard, in a pci slot...how do I set the pci card as the default soundcard?

---

### Post by KansasJoe on 2006-03-18
Disable the onboard card in the bios and it will make your pci card the default card

---

### Post by mlind on 2006-03-18
you can do it by creating file ~/.asoundrc and defining your card there. This is the
case if you're using alsa.

```

cat /proc/asound/cards

```

to see ordering of your soundcards.
use you favourite editor to create .asoundrc file and paste the following
definition

```

pcm.!default {
    type hw
    **card 1**
}
ctl.!default {
    type hw           
    **card 1**
}

```

change card number to one you want to use.

---

### Post by stefenkillsit on 2006-03-18
thanks, I got it to work alright

---

### Post by mlind on 2006-03-18
which method did you use? disabled other soundcard or by using .asoundrc ?

---

### Post by Haegin on 2006-05-27
Slight variation on this...
How do I change the soundcard on the fly so I can switch from my audigy 2 to my usb headset when other people need to sleep?

---

### Post by mlind on 2006-05-27
[QUOTE=Human Prototype]Slight variation on this...
How do I change the soundcard on the fly so I can switch from my audigy 2 to my usb headset when other people need to sleep?[/QUOTE]

Try from System > Preferences > Sound 
and the "Default Soundcard" option.

That ~/.asoundrc is probably useless then.

Or if headset is marked as a soundchannel for audigy2
just mute PCM sound channels and unmute headset.

---

