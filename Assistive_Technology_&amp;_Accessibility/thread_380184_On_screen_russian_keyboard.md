---
title: "On screen russian keyboard ?"
date: 2007-03-09
forum: Assistive Technology &amp; Accessibility
---

### Post by Icarosaurus on 2007-03-09
I'm learning russian, and I'd really like to have an on-screen keyboard with cyrillic letters.
I set up Scim and I'm using an Italian keyboard, so the keys are latin letters and I sometimes go mad :)
How can I do?
Thanks in advance :)

---

### Post by frafu on 2007-03-09
Hello, 

onboard is the default onscreen keyboard shipped with ubuntu. 

When using the default layout from onboard , onboard should display the layout of the default system keyboard settings. 

So you should open the menu System->Preferences->Keyboard, open the layout tab, add the russian layout to the layout list and make it the default layout. (Maybe you will also have to move it to the top of the list in order to be considered as the default layout. (there was once a bug if I remember correctly.) 

Francesco

---

### Post by Icarosaurus on 2007-03-09
Thank you for replying.
Onboard is buggy... it often crashes and didn't solve my problem.

I solved in the simplest way suitable for me.
I used to switch between Italian and Russian using the SCIM icon, but I realized that it's sufficient (for me) to add the russian layout in the keyboard configuration and put the layout icon on the panel.

I just really needed a "picture" of the keyboard to localize the keys. Well, I obtain it by right clicking on the layout icon and selecting "display current layout".

That's good for me..
But I could be in trouble if I need a working on-screen russian keyboard.
Fortunately, I don't.....

---

### Post by frafu on 2007-03-10
Hello, 

I am glad to hear that you solved your problem. 

Nevertheless, could you tell us more about your onboard crashes? 

What version of Ubuntu are you using? In what circumstances does it crash? What system and keyboard language are you using? 

Thanks in advance. 

Francesco

---

### Post by Icarosaurus on 2007-03-10
I'm using feisty, Generic 105 keys keyboard, with italian and phonetic russian layouts.

When I set Russian by default it simply doesn't start (segmentation fault).

Playing with setup window caused crashes too.

I have assistive technology disabled, but enabling it doesn't change the situation.

Naturally, ask if you want to know more!
:-)

---

### Post by frafu on 2007-03-10
I also had segmentation faults some months ago. You might try the following which helped in my case: 

Open the settings dialog and click personalise layout.  onboard then creates a new layout identical to your current one.  Select that and then run onboard.

Hoping that it helps. 

Francesco

---

### Post by Icarosaurus on 2007-03-10
Doesn't seem to work...
I cannot get a russian layout .

---

### Post by t0rtois3 on 2007-03-11
I can't repeat the seg faults but when selecting the Russian keyboard layout I do get blank keys.

I'm working at getting the keyboard layouts using the same system as the graphic that is displayed when you select layouts in the gnome control panel.  This will also allow you to set the onboard layout separate from the system layout  and should also be more robust.

It will take a while though.  Probably feisty + 1 time frame but i'll try to get something ready during Easter.  Until then you could try GOK.  Though that doesn't seem to work at all currently.

---

### Post by frafu on 2007-03-11
Hello t0rtois3,

When I use the default layout, I get a cyrillic keyboard layout if it is chosen in the keyboard preferences. However, when I use my personal edited layout in onboard, I don't get the cyrillic layout. 

The same happens as well through vnc than through nx. 

By the way, to make the cyrillic layout appear in onboard, you might have to choose another layout in onboard and then switch back to the default layout. 

Have a nice day. 

Francesco

---

### Post by Icarosaurus on 2007-03-11
Nothing to do, I'm trying to do what you say... 
segmenteation fault :(

---

### Post by t0rtois3 on 2007-03-12
There's a new version in feisty, hope it fixes your problem.  

I can't really fix the seg fault without more information.

Try removing the .sok directory in your home directory.

---

