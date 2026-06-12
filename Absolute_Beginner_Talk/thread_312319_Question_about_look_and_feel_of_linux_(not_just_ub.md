---
title: "Question about look and feel of linux (not just ubuntu) apps"
date: 2006-12-04
forum: Absolute Beginner Talk
---

### Post by kirsis on 2006-12-04
Hello all,

I have a few not ubuntu-specific questions about linux. I hope that's acceptable as I have no idea where else to ask something like this. I'm trying to learn linux and installed Ubuntu some time ago. So far things've been peachy, I have to say :) I was very impressed with how the system booted and I could browse the internet while ubuntu installs itself.

But I digress.

My questions are concerning the look and feel of linux applications. I've noticed there is a lack of unified look. Some apps use the Tk widget toolkit (which looks crap imo), some use GTK+ (which is what the Gnome desktop environment is built upon, right?). Then there's Qt (which KDE apparently is built upon).

So do these (and other similar) widget toolkits use XLib to draw the widgets?

Then there's wxWidgets that "utilize the native platform's controls and utilities". Wrappers basically. On windows, I guess, it calls Win32 API functions. But what about linux? Is there anything that can be called "native" when it comes to GUI calls?

Does it detect which other widget toolkits, such as GTK+, are present, and employ those?

Or does it draw its own widgets on linux, with xlib?

I'm also under the assumption that whatever happens on a higher level, it all comes down to XLib. Right? At the lowest level, is all drawing on screen done through xlib?

---

If you think this is not an appropriate place for questions like these, I'd be grateful if you'd just tell me where I can find out more about linux, and how it works. What makes it tick :)

Thanks

---

### Post by Sef on 2006-12-04
> My questions are concerning the look and feel of linux applications. I've noticed there is a lack of unified look. Some apps use the Tk widget toolkit (which looks crap imo), some use GTK+ (which is what the Gnome desktop environment is built upon, right?). Then there's Qt (which KDE apparently is built upon).


Correct about Gnome and KDE.

> If you think this is not an appropriate place for questions like these, I'd be grateful if you'd just tell me where I can find out more about linux, and how it works. What makes it tick


If they weren't ok, they would be moved to another place.

---

### Post by 23meg on 2006-12-04
[QUOTE=kirsis]So do these (and other similar) widget toolkits use XLib to draw the widgets?[/QUOTE]
Yes, Xlib provides ways to interact with the X server, but doesn't draw the widgets. Toolkits such as GTK+ use it to draw their own widgets.
[QUOTE=kirsis]
Then there's wxWidgets that "utilize the native platform's controls and utilities". Wrappers basically. On windows, I guess, it calls Win32 API functions. But what about linux? Is there anything that can be called "native" when it comes to GUI calls?

Does it detect which other widget toolkits, such as GTK+, are present, and employ those?

Or does it draw its own widgets on linux, with xlib?[/QUOTE]It's environment-aware, so there's no need for an ultimate "native" library. It calls whatever is being used to render the widgets; in a GNOME environment, it uses GTK+ widgets, in a KDE one, QT widgets. Not sure, but perhaps in a barebones X environment, it would resort to Xt. 

Xt would perhaps be as native as it gets, since it's built into X. Keep in mind that it's native to X in all platforms it runs on, not just Linux. Same goes for GTK+ and QT; they run on many other platforms than Linux.

---

### Post by 23meg on 2006-12-04
[QUOTE=kirsis]I'm also under the assumption that whatever happens on a higher level, it all comes down to XLib. Right? At the lowest level, is all drawing on screen done through xlib?[/QUOTE]Xlib doesn't do any drawing by itself; it provides an interface to the X protocol for client applications, as well as widget toolkits that use it. It's the lowest level programming interface, but not the lowest level component of X.

---

### Post by kirsis on 2006-12-04
Got'cha. Thanks a lot for the clarifications

---

