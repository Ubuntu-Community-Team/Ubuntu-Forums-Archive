---
title: "Window position not remembered"
date: 2007-09-30
forum: Absolute Beginner Talk
---

### Post by Eric Weir on 2007-09-30
I'm getting the impression from scouring the archives on this question, but is it REALLY the case that applications will not remember size and position under GNOME? I find this unbelievable and extremely irritating -- windows opening in awkward locations, having to reposition them every time a new window is opened, e.g., a new message or compose window in Thunderbird.

Is Kubuntu/KDE more hospitable in this respect?

Thanks,

---

### Post by t0n1 on 2007-10-02
I have the same issue. Some applications do open in the same positions, and some do not. Firefox does not, Evolution does not.
Any help would be appreciated.

---

### Post by Paul820 on 2007-10-02
I think it's down to the application to remember their windows positions, you can't expect gnome to remember all the applications specific positions. Some programs do remember their positions, have a look in their preferences.

---

### Post by kiderjones on 2007-11-13
Compiz Fusion has a* Place Windows* option under windows management in the setting manager. Works pretty well.

---

### Post by Eric Weir on 2007-11-13
> **kiderjones said:**
> Compiz Fusion has a* Place Windows* option under windows management in the setting manager. Works pretty well.

Thanks. I've dealt with the issue for now by moving over to Kubuntu. The solution there is not entirely satisfactory either. For one thing, you have to configure every single window you encounter, e.g., all the various windows associated with Thunderbird, unlike in Windows, where the default is for windows to remember their position. It's not something you even have to think about there. [Doesn't make me wanna stick with Windows, though.]

I haven't installed Compiz Fusion. I'll wait till I upgrade to gusty where it comes installed.

---

### Post by Eric Weir on 2007-11-13
> **Paul820 said:**
> I think it's down to the application to remember their windows positions, you can't expect gnome to remember all the applications specific positions. Some programs do remember their positions, have a look in their preferences.

Hmm. It's no problem for Windows. Surely a lot easier than trying to define which windows get remembered and which don't, which is the way Kubuntu tries to do it. 

From my experience with the latter, I'd say it really can't be done. The possibilities for setting up rules there don't allow some windows to be remembered and cause other windows to show up in places with sizes that are totally inappropriate from the point of view of what the user was trying to accomplish by setting up rules.

Regards,

---

### Post by wub on 2007-11-14
There are two ways I think this might be approached: one would be for windows that >have< been moved/sized to remember the settings in effect when they were closed (or the ap was closed), but there may be something simpler.

I have noticed that the right side of the desktop is the odd child out.  If you could see my screen right now, you would see a full-sized browser window all the way to the right, partially hiding a terminal window at its left, but >all< my desktop icons are fully in view!  Yeah!  I could click one >right now< without moving or minimizing anything.

Anyone else think that makes sense?  

Could we have a switch somewhere that tells Ubuntu that when a new application opens its main window, it does so by sticking the right side to the right edge of the current desktop, instead of left to left?  Or I suppose I could move all of my icons all the way to the right, but of course the next one will be created at the top left.

---

### Post by Eric Weir on 2007-11-15
> **wub said:**
> There are two ways I think this might be approached: one would be for windows that >have< been moved/sized to remember the settings in effect when they were closed (or the ap was closed), but there may be something simpler.

From the perspective of the user -- at least this one -- that would be the simplest alternative. [Maybe not for the developer.] It is the Windows solution. If windows open with a position/size that's not problem, no problem. If you want to move em, you only have to do so once. 

> I have noticed that the right side of the desktop is the odd child out.  If you could see my screen right now, you would see a full-sized browser window all the way to the right, partially hiding a terminal window at its left, but >all< my desktop icons are fully in view!  Yeah!  I could click one >right now< without moving or minimizing anything.I don't have any icons on my desktop and for the most part never have. It's not icons that concerns me. It's the subsidiary windows used by applications.  And there it's not just position but size that's an irritant. Why should a window that displays a tiny amount of information and that has maybe one or two buttons open to the full size of the application?

I moved to Kubuntu in large part because it promised a solution to this problem. I'll probably stick with it but it's solution isn't a lot better. For one thing, you have to go through a complicated rigamorole -- lots of mouse clicks! -- for every window. For another, it really only provides for customization of classes of windows. So if an application uses two windows of one class, and the user wants to assign them a different size or position  he/she's out of luck. 

There's a "match window title" option that provides a solution to this problem, IF the title refers to the window's function, e.g., "print," rather than its content, e.g., "Reply to thread 'Window position not remembered.'" Unfortunately many windows, e.g., all TB message windows, take their title from their content.

So, I come back to where I started: the simplest solution is to have windows remember their size and position when last open.

---

