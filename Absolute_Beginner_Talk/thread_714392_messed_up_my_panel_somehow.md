---
title: "messed up my panel somehow"
date: 2008-03-03
forum: Absolute Beginner Talk
---

### Post by bben on 2008-03-03
I changed an option somewhere and it removed 'advanced' options when I right click my toolbar.

So now when I right click it, I don't get the properties option, can't move and lock/unlock buttons, can't add stuff to the panel... I just get Help and Panel info.

I've searched google and these forums for six hours but can't find anything, so either I'm the first person ever to change that particuler option, or i'm using the wrong keywords on the search function...

I just switched from Vista and I was trying to configure my desktop to look exactly as I wanted. In other words, I was changing anything that seemed as if it can be changed just to see what it does :P

Anyway, any help would be very much appreciated.

------- Solved: I installed Ubuntu Tweak and there's an option to lock the panel in it... heh.

---

### Post by locosmurf on 2008-03-07
hey man I'm glad you solved it. I was just searching through the forums looking for people to help and as I always play with my panels (I just installed kiba-dock today and have been messing with it lol) I figured I could help you, but I guess not. anywho, if you ever need help on something you mess up due to tweaking the million options ubuntu gives you then search the forums and/or pm me. The reason I installed ubuntu in the first place was to tweak it and play with it. I never expected to actually use it as my main OS but here I am today ^_^

so since its now 3:00 am im going to stop rambling and move on to the next post!!!

---

### Post by mcduck on 2008-03-07
Have you been playing with the gconf-editor? That's the only place I know where you can disable those options..

Press Alt-F2 and run 'gconf-editor'. Then browse to apps/panel/global and make sure that "locked_down" is _not_ enabled.

---

