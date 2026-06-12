---
title: "browser jumping to historical page"
date: 2008-02-11
forum: Absolute Beginner Talk
---

### Post by crageye on 2008-02-11
on kubuntu, using both firefox and opera, its weird when scrolling all of a sudden i am sent back to a page from history. it doesn't happen all the time and i am yet to find a pattern. but it does happen every now and then. or could it be in my touchpad/mouse settings... 
any clues..

---

### Post by nikoPSK on 2008-02-11
> **crageye said:**
> on kubuntu, using both firefox and opera, its weird when scrolling all of a sudden i am sent back to a page from history. it doesn't happen all the time and i am yet to find a pattern. but it does happen every now and then. or could it be in my touchpad/mouse settings... 
any clues..

please see if there is any info when this happens in the terminal by running it as so:

```
firefox
```

---

### Post by asmoore82 on 2008-02-11
> **crageye said:**
> on kubuntu, using both firefox and opera, its weird when scrolling all of a sudden i am sent back to a page from history. it doesn't happen all the time and i am yet to find a pattern. but it does happen every now and then. or could it be in my touchpad/mouse settings... 
any clues..

you are accidentally Middle-Clicking.
This causes the browsers to attempt to load the last highlighted text as a URL.

to change this behavior in Firefox:
Open "Edit -> Preferences"
Click the "Advanced" pane(last one);
Click the "General" Tab(first one under "Advanced");
and check the option "use autoscrolling"
in the second section "browsing"

This will cause a Middle-Click to "autoscroll" instead;
but a Middle-Click on a link will still "Open in New Tab"

---

### Post by nikoPSK on 2008-02-11
> **asmoore82 said:**
> you are accidentally Middle-Clicking.
This causes the browsers to attempt to load the last highlighted text as a URL.

to change this behavior in Firefox:
Open "Edit -> Preferences"
Click the "Advanced" pane(last one);
Click the "General" Tab(first one under "Advanced");
and check the option "use autoscrolling"
in the second section "browsing"

This will cause a Middle-Click to "autoscroll" instead;
but a Middle-Click on a link will still "Open in New Tab"

thanks for that. :)

---

### Post by crageye on 2008-02-12
> **asmoore82 said:**
> you are accidentally Middle-Clicking.
This causes the browsers to attempt to load the last highlighted text as a URL.

to change this behavior in Firefox:
Open "Edit -> Preferences"
Click the "Advanced" pane(last one);
Click the "General" Tab(first one under "Advanced");
and check the option "use autoscrolling"
in the second section "browsing"

This will cause a Middle-Click to "autoscroll" instead;
but a Middle-Click on a link will still "Open in New Tab"


I will try it out. How is that middle-click happening on a touchpad!

---

### Post by nikoPSK on 2008-02-12
> **crageye said:**
> I will try it out. How is that middle-click happening on a touchpad!

maybe your touchpad has a special feature? Like some have scrolling on the side, etc

---

### Post by Steveway on 2008-02-12
Middle-click on a touchpad is normally made by tapping with 2 fingers on the pad. (At least mine does this.)

---

### Post by nikoPSK on 2008-02-12
> **Steveway said:**
> Middle-click on a touchpad is normally made by tapping with 2 fingers on the pad. (At least mine does this.)

that might be it, accidentally applying two points of contact.

---

### Post by groovomata on 2008-03-06
Hey All, I get the same problem with ubuntu gutsy on a Dell 6400 inspiron laptop, however only when I use my touchpad (not a mouse) and when compriz is enabled. When I use my touchpad with firefox it seems to act like mouse gestures and move firefox back to a previously visited page. It can be quite a drag when filling out online forms or typing information into a field like I'm doing now. 
If anyone has a fix for this problem I'd be grateful!
Thanks,
Erik.

---

### Post by groovomata on 2008-03-20
Has no one had a similar problem or found a solution to it? I'm surprised!

---

### Post by Joeb454 on 2008-03-20
It's the same problem as above :)

I only just realised 2 points of contact == middle click. Middle click is also at the extreme top right of my touchpad.

I normally use a USB mouse at home though.

**groovomata** please try the same steps as above

---

### Post by groovomata on 2008-03-20
I must confess that I've disabled compriz for the past while to see if I could reproduce the problem without it and indeed firefox still jumps back to previously visited pages with compriz disabled. 
E.

---

### Post by groovomata on 2008-03-20
I've discovered on the Dell Inspiron 6400, the touchpad includes vertical and horizontal scrolling features indicated by a bar on the right side of the touchpad for vertical scrolling, and a bar on the bottom of the touchpad for horizontal scrolling. Moving your finger along the vertical bar will scroll the internet page up and down; however moving your finger along the horizontal bar along the bottom of the touchpad will actually 'scroll' firefox historically through the pages you've visited on that tab. Moving your finger left along the horizontal bar causes firefox to go back to the last pages I visited while moving your finger right will return firefox to the most recent page. 

Accidently touching the bottom scroll bar is what causes the unexpected jumps that firefox seems to do by loading pages previously visited. Knowing this helps me to understand what is happening when firefox seems to jump around. I've played around with the settings but I can't seem to turn off the 'historical scrolling' feature of firefox. 

Cheers,
Erik.

---

