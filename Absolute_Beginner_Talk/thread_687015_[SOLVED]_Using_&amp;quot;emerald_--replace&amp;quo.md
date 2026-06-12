---
title: "[SOLVED] Using &amp;quot;emerald --replace&amp;quot; in terminal works, but when I close it, it turns b"
date: 2008-02-03
forum: Absolute Beginner Talk
---

### Post by papuccino1 on 2008-02-03
What should I do?

Writing that command in Terminal works. But when I close the Terminal window, it switches back to Default. 

I'm sure the answer is so simple.

---

### Post by Majorix on 2008-02-03
Add a & at the end of your command.

---

### Post by Dr Small on 2008-02-03
> **Majorix said:**
> Add a & at the end of your command.
+1
Or execute it in the Run dialog box

---

### Post by papuccino1 on 2008-02-03
> **Majorix said:**
> Add a & at the end of your command.


What does that symbol do at the end? Edit: Tried that and it still changes back when I close the terminal. :S


Hey Dr. Small, you've helped me before what does the +1 do? Where do I put it? Could you write the complete code.



Also, one more glitch. Whenever I open windows or program the tob menu bar is blocked the top panel. (APplication, Places, System) 

Any thoughts on that?

---

### Post by Yes on 2008-02-03
+1 means that he agrees with the quoted text.

Press Alt+F2 and then type in 'emerald --replace'.

---

### Post by Dr Small on 2008-02-03
"+1" = "I agree with the above post"

But, press ALT+F2 and enter your command there to see if it works :)

---

### Post by papuccino1 on 2008-02-03
> **Yes said:**
> +1 means that he agrees with the quoted text.

Press Alt+F2 and then type in 'emerald --replace'.

Ding DING DING. We have a winner. :)  I thought you were supposed to write that in Terminal. Turns out, it's supposed to written in Run Apllication. Who figured!?



One more pet peeve guys. Sometimes when I open a window it opens way to up. What I mean is the menu bar is blocked by the top toolbar. Help?

---

### Post by quanumphaze on 2008-02-03
> **papuccino1 said:**
> One more pet peeve guys. Sometimes when I open a window it opens way to up. What I mean is the menu bar is blocked by the top toolbar. Help?

Alt + click-drag the window
You can do this anywhere on the window (except resize edges and title bar buttons) to move it instead of using the title bar.

Or right click the the window's button on the lower panel and chose move and click when done.

---

### Post by RomeReactor on 2008-02-03
Hi. If you don't want to type **emerald --replace** every time, install **compizconfig-settings-manager**; look for it in Synaptic, or to install from the terminal:
```
sudo aptitude install compizconfig-settings-manager
```

Once it's installed, you can find it in 'System->Preferences->Advanced Desktop Effects Settings'; open it, find and press the **Window Decoration** button, and in the 'Command' section write:
```
emerald --replace
```

---

