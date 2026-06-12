---
title: "onboard: questions about keyboard definition"
date: 2006-10-19
forum: Assistive Technology &amp; Accessibility
---

### Post by frafu on 2006-10-19
Hello, 


I copied and modified the default keyboard definition to add a few keys that I missed on the first pane. (see picture below) 

Now I wonder why each keyline only has one keysym tag. Should there not be a keysym for each modifier-state as the printed character varies with the state of the modifiers? 

Can the id of a key in a pane be the same as the id of a key in another pane? For example if I want to have the modifiers in every pane, can I use the same id? As I did not know it, I always added the number 1 to the id I created. 
What if I have the shift modifier in every pane. If I activate the shift in pane1,what happens to the shift in pane2? 

Further, when I select for example the pane with the function keys, I still can see the first pane underneath. I find it disturbing. Is there a way I can hide the first pane when another pane is visible? I thought of adding a rectangle of the size of the keyboard without id to each pane under the keys to cover the first alpha pane. 

Finally, if somebody is interested in the modified keyboard definition, I can upload it here. (though I don't think it to be very well made for now) 


frafu

---

### Post by t0rtois3 on 2006-10-19
It's not necessary to have a keysym for each modifier-state.  The keysym (in this case but not always) represents a physical key and not a character.

I'm not sure about the same id across panes, looking at the code it might work.  I didn't mean it to do that though :)

Having multiple modifiers works, onboard keeps track of how many times a modifier has been pressed across the whole keyboard and doesn't release the modifier until they have all been released.  

In the .sok set backgroundAlpha to 1.0 for each pane
<pane backgroundRed='0.6' filename='test-Functions.svg' backgroundBlue='0.7' backgroundAlpha='1.0' backgroundGreen='0.3' font='5' id='Functions'>

Chris

---

### Post by frafu on 2006-10-20
> **t0rtois3 said:**
> It's not necessary to have a keysym for each modifier-state.  The keysym (in this case but not always) represents a physical key and not a character.
 

OK; keysym represents the physical key of a hardware keyboard; let us call it keycode. I suppose (like in macos7), there is a file that maps, for each modifier-combination, the keycode to a specific character (charcode)!? 

But what happens if the keysym does not correspond to a keycode? 

> 
In the .sok set backgroundAlpha to 1.0 for each pane
<pane backgroundRed='0.6' filename='test-Functions.svg' backgroundBlue='0.7' backgroundAlpha='1.0' backgroundGreen='0.3' font='5' id='Functions'>


Thanks for the explanation. I have set backgroundAlpha to 0.9. This way it is much easier to differentiate the working pane from the disabled underlying pane. 

frafu

---

