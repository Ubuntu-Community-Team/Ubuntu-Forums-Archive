---
title: "onboard and switch button"
date: 2006-10-19
forum: Assistive Technology &amp; Accessibility
---

### Post by frafu on 2006-10-19
Hello, 

When I click on switch button of onboard, the keyboard returns at once to the first pane; afterwards I click on the upper menubar of the screen to get its contextual menu. Unfortunately, the contextual menu does not appear; the cursor changes shape and shows a hand. It does so with nx and with vnc. 

I suppose 'switch button' is not working or am I doing it wrong? 

frafu

---

### Post by t0rtois3 on 2006-10-19
I've seen this one before, and I think this ones a gnome bug.  Sometimes the settings deamon sometimes ignores this gconf key:
/desktop/gnome/peripherals/mouse/left_handed

run gconf-editor and navigate to this key.  You should see the tickbox next to it clicking on and off.  

I'll bug someone about it when I get the chance.

Chris

---

### Post by frafu on 2006-10-20
Hello, 

You are right: clicking on 'switch button' toggles the checkbox on and off; but the left click does not work. 

Is there a chance that it does not work, because it needs an entry of a specific mouse model (left handed mouse model) in some gnome configuration? 

frafu

---

