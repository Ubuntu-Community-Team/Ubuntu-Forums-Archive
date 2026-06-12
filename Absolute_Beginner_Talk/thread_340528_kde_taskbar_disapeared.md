---
title: "kde taskbar disapeared"
date: 2007-01-17
forum: Absolute Beginner Talk
---

### Post by cypher_666 on 2007-01-17
i am relativley new to all this so please bear with me if i dont use uber tech lingo.

ive recently installed kubuntu 6.10 and was loving it, i had been manually installing some codecs so i could view wmv in kaffeine using the terminal to move them to my root drive where they apparently needed to go.

i went and had some food, restarted my box and lo and behold the taskbar at the bottom with my trashcan etc has dissapeared and wont come back. i have it set to hide and reappear when my mouse hits the bottom of the screen, but its refusing to come out of hiding and i kinda need it.

could i have messed it up simply by using the sudo mv  command in terminal?

anyone got any ideas how to get it back?

thanks in advance for any help.

---

### Post by justifier on 2007-01-17
have you tried rebooting?

---

### Post by ComplexNumber on 2007-01-17
> **cypher_666 said:**
> i am relativley new to all this so please bear with me if i dont use uber tech lingo.

ive recently installed kubuntu 6.10 and was loving it, i had been manually installing some codecs so i could view wmv in kaffeine using the terminal to move them to my root drive where they apparently needed to go.

i went and had some food, restarted my box and lo and behold the taskbar at the bottom with my trashcan etc has dissapeared and wont come back. i have it set to hide and reappear when my mouse hits the bottom of the screen, but its refusing to come out of hiding and i kinda need it.

could i have messed it up simply by using the sudo mv  command in terminal?

anyone got any ideas how to get it back?

thanks in advance for any help.
that sometimes happens. it used to happen all the time when i used PCLinuxOS. 
what you need to do is to go into the terminal(its called konsole) and type 'kcontrol' (for some reason, kubuntu doesn't have the kde control centre in the menu, i've heard). then set it so that it doesn't hide. it will then reappear. then you can set it to hide again.

---

### Post by cypher_666 on 2007-01-17
justifier - yes i tried rebooting, that was my kneejerk reaction from windows, but alas it didnt help so i posted on here.

complex number - thankyou very much, its sorted now, however there was some funky stuff put out by the console before it opened the control centre, any ideas if this is good or bad.....

X Error: BadDevice, invalid or uninitialized input device 168
  Major opcode:  145
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 168
  Major opcode:  145
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
gaz@something:~$ libpng warning: Ignoring gAMA chunk with gamma=0
libpng warning: Invalid cHRM white point

---

### Post by ComplexNumber on 2007-01-17
> however there was some funky stuff put out by the console before it opened the control centre, any ideas if this is good or bad.....
don't worry about it....its nothing.

---

### Post by cypher_666 on 2007-01-17
well thanks again, i had just got everything to how i wanted pretty much and didnt fancy a re-install.

---

### Post by floke on 2007-01-17
I notice this happens to me a fair amount when in KDE (which is one of the reasons I use Gnome!). I find that unchecking the autohide function doesn't allow it to disappear in the first place (though it's a pain since I like the autohide function!).

---

