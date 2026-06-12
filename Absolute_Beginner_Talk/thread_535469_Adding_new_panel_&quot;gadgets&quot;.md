---
title: "Adding new panel &quot;gadgets&quot;"
date: 2007-08-26
forum: Absolute Beginner Talk
---

### Post by fraser_m on 2007-08-26
Is there way to manually install new panel "gadgets" in "Add to Panel"?

---

### Post by ticopelp on 2007-08-26
Do you have a specific gadget in mind?

I installed timer-applet for the panel, and I had to compile it from source. Wasn't hard, though.

---

### Post by fraser_m on 2007-08-26
i was looking for an analogue clock, like on vi$ta sidebar, and a rss/gmail checker

---

### Post by ticopelp on 2007-08-26
> **fraser_m said:**
> i was looking for an analogue clock, like on vi$ta sidebar, and a rss/gmail checker

Versions of both of those are available in the repos. Go to Add / Remove Programs, pick "All Open Source Applications" from the drop-down, and search for "clock" and "gmail"

Or try:

```
sudo apt-get install gmail-notify
```

```
sudo apt-get install matchbox-panel
```

```
sudo apt-get install cairo-clock
```

Cheers.

---

### Post by Perfect Storm on 2007-08-26
side bar? You properly looking for gDesklets for that.
Search synaptic for gmail notify, if your sourcelist is set up with universe and multiverse you should find a couple of things for the panel.

---

