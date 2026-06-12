---
title: "minimize maximize window broken in compize fusion"
date: 2007-10-21
forum: Absolute Beginner Talk
---

### Post by Kilarin on 2007-10-21
I've got an odd issue.
I run NoteTab under Wine.  Whenever I put the "visuall effects" setting under the appearance tab to anything greater than NONE, my minimize and maximize functions disappear for that window, and that window only.  they work fine for everything else.  including other applications running under Wine.

Not only do the min/max buttons disappear, but if you right click the min/max functions are grayed out.   I tried playing around with the different compiz fusion functions under the custom setting, and got the behavior to vary somewhat.  With animations turned off the min/max functions on that one window will appear ok when the window first opens, but then as soon as you click maximize, they disappear again.  So not a lot of difference there.

I went through the custom menu and turned EVERYTHING off except for "window decorations" because when you turn that one off, the top control bar on every window disappears completely.  

At any time, I can go to the appearance menu, click NONE under the visual effect tab, and Notetab suddenly min/maxes just fine again.

Again, the REALLY odd thing is that its ONLY this one window.  I can have firefox, thunderbird, various system windows, terminals, etc, all open, and they work just fine, even when I'm running all kinds of special effects.  But, right there in the midsts of them, will be Notetab with no min/max button.

Any help would be appreciated!

---

### Post by Kilarin on 2007-10-24
I still am having the same problem.  It's frustrating because I was enjoying playing with Compiz Fusion.  Everything ELSE works just fine, just this one window is wrong.

Does anyone have any advice on what direction I should check next?

Thanks!

---

### Post by JLoiac on 2007-10-29
try viewing the browser in full view or auto hiding the panel.

---

### Post by Kilarin on 2007-10-30
I thank you VERY much for responding!
But I don't quite understand what you are asking me to do.
> auto hiding the panel.
By "browser" do you mean the application that is misbehaving, which is NoteTab Pro running under Wine.   In that case, what do you mean by "full view"?  I not only don't have minimize/maximize buttons, but when I right click the minimize and maximize options are greyed out.

It's quite bizarre because I can turn effects off, and the buttons/options come immediately back.  Then turn effects back on and the buttons/options for min/max are gone again.  Completely and reliably repeatable.  And it affects no other windows.

>  or auto hiding the panel.
What panel?  I just have the app open on the desktop.  I set the "task bar" to Auto Hide, just in case that was the panel you were speaking of.  It didn't make any difference in the behavior of my NoteTab Window.

---

### Post by Kilarin on 2007-10-30
I thought perhaps some screenshots might help explain whats going on.

First, here is what it looks like with the visual effects set to NONE:
[[IMG]http://img89.imageshack.us/img89/5739/minmax3noneeq7.jpg[/IMG]](http://imageshack.us)
You will note that all of the windows have the min/max buttons (other than the appearance window itself, which shouldn't)

Now then, I click "NORMAL" under the visual effects, and THIS is what happens immediately:
[[IMG]http://img221.imageshack.us/img221/4426/minmax3normmg1.jpg[/IMG]](http://imageshack.us)
Note that on the NoteTab window, the min/max buttons are gone.  I couldn't capture it in the screenshot, but a rightclick on the NoteTab bar shows the min/max options greyed out now.  

NoteTab is running under Wine, but this isn't happening to all Wine windows, because Password Safe in the above picture is ALSO running under Wine, and nothing strange is happening to it's buttons.

When I go back to NONE for visual effects, the min/max buttons come right back.

---

### Post by Kilarin on 2007-11-05
I upgraded to the newest version of compiz fusion through the normal ubuntu update process, then tested this again.  I'm still having exactly the same bizarre effect.  For that one window, and for that window only, turning on ANY affects causes the minimize/maximize buttons to disappear, and on the rightclick menu for that window minimiaze/unmaximize are grayed out.      I've tried playing with all of the advanced compiz fusion settings and nothing seems to make any difference.

Why this one window?  Why not any other windows?  And what on earth is causing it?

---

