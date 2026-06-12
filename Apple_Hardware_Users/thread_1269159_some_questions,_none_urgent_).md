---
title: "some questions, none urgent :)"
date: 2009-09-17
forum: Apple Hardware Users
---

### Post by gwydionwaters on 2009-09-17
so i have installed 9.04 on my ppc g4 laptop, it seems to work quite nicely and i am leaning towards dropping osx, which i currently dual boot 'just in case' lol i started with 8.10 but used the automated upgrade. there are a few things that seem wrong and a few i just would enjoy to be a little different. so here they are.

first is about booting. it seems that sometimes ubuntu just doesn't want to boot, usually after an update or similar. it will pass the loader and bootstrap, i get to the cursor after the quick 'please wait...' and then it sits and either does no more or suddenly reboots. interesting..

another is heat and fans, not to say the laptop overheats (although the case on the left side seems warm most of the time) but it seems to be more involved in cooling down. the fans go more often and at varying speeds. perhaps ubuntu is just more efficient at managing cooling? this does appear to be related to cpu usage, they kick in more with heavier use, with osx they don't come on until after the heat has risen where as now it is simultaneous.

when i close the lid the screen stays on and the computer does not suspend, i had the settings set to suspend on close but after update to 9.04 the option is gone.
also my osx partition is no longer available to mount, after update that is.

and two i would like to change..
my right click operator. using a tutorial i found i changed the /etc/default/mouseemu file to use my alt/option key but it is set to the alt portion which requires also the fn key. any ideas on what key code i should use for the key singly? the line in the config looks like this ```
RIGHT_CLICK="-right 56 272"       # Alt key + click
```also touch scrolling.. i have tried using xorg and screwed my system pretty good, got stuck in low res/color, barely made it out alive. so i looked into the hal settings and found some for the touch synaptics but have not been able to use this successfully.

looking for any thoughts or ideas, thanks for reading.

---

