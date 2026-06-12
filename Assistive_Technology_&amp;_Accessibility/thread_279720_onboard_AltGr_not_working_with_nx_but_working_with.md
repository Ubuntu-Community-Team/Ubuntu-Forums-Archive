---
title: "onboard AltGr not working with nx but working with vnc"
date: 2006-10-18
forum: Assistive Technology &amp; Accessibility
---

### Post by frafu on 2006-10-18
Hello, 

I have stumbled on another problem when using onboard through nx: 

When I click on the AltGr modifier key, the letters on the keys of onboard change and I can see the symbols. For example, as I am using the german layout, the letter q is replaced with the @ symbol. 

However, when I click on the @ symbol, it does not get typed; the letter q gets typed instead. 

Finally, you may want to know that with vnc, the problem does not occur: when I click on the @ symbol, the @ symbol gets typed as it should be. 

frafu

---

### Post by t0rtois3 on 2006-10-19
Very strange I have absolutely no idea about this one.  

I shall try and reproduce when I get a second (which have been in quite short supply lately).

---

### Post by frafu on 2006-10-19
I have added a line of keys to the keyboard in order to have a few keys on the first pane. 

In the picture attached to this message you can see the modified onboard and the corresponding part of the keyboard definition file. 

Maybe that it helps you to know that the @ I added in the upper line does work; but it is an @ that is typed without any modifier activated.

---

### Post by frafu on 2006-10-25
I have just discovered that the problem not only occurs with the altgr modifier: 

On my german layout, there is the + sign. By pressing the shift, the + changes to *. However when I click on the *, onboard types a +. 

It does not so with all the keys; for the capital letters it works. For the . that is changed into a : it also works as it should... 

The problem also occurs with dead keys: the ´ dead key is changed to the ` dead key when shift is pressed; however I don't get è but é.

frafu

---

