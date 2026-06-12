---
title: "gDesklets Bug 430612 – Disables 'caps' key...Need help"
date: 2007-06-23
forum: Apple PPC Users
---

### Post by reh4c on 2007-06-23
**This post could be related to an Ubuntu bug filed at**: [http://bugzilla.gnome.org/show_bug.cgi?id=430612](http://bugzilla.gnome.org/show_bug.cgi?id=430612) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				Fellow PPC users,
I found a bug when using gDesklets on my iBook.  Here is my synopsis in bugzilla:  

"I can confirm this problem exists using 7.04 on my iBook G4.  Let me try to
explain.  First, install gDesklets.  Next, run the daemon.  Finally, open a
terminal or another text entry program and try to use the "shift" key to either
make a capital letter or a symbol colocated with the number keys.  The shift
key does not work properly.  Something is conflicting with the keybindings. 
It's very annoying...not being able to use the shift key.  When I stop the
gDesklets daemon, my shift key works properly again.  Please help solve this
bug."

However, the developers don't have a PPC to test.  It's "working nicely" on an x86.

Can one of you please confirm this bug on your PPC?  Please post your feedback here or make comments in bugzilla to get this bug fixed.  Thanks!

---

### Post by tnseditor on 2007-06-23
My friend just had this problem last night running on G4 ppc.  I was demonstrating a Live CD with her and installed several things using the Live CD.  After running gDesklets her shift keys wouldn't work either.  I had wondered what the problem was and had her reboot.  Since you suggested it, that sounds like what the problem was.  Thanks!

---

### Post by luckyd on 2007-06-24
I took me a while to find it, but heres the fix. Go to the gdesklets icon in the tool bar, then right click on it and select configuration. Then go to the the option that says toggle key for floating mode, and change the key combination to something that dosn't include the "shift" key. Hope this helps :)

P.S. Thumbnails show how to do it if I was unclear.

---

### Post by reh4c on 2007-06-25
Thanks!  I'll pass the info. along to the gDesklets developers.  :D

---

