---
title: "&quot;Cancel&quot; Icon"
date: 2007-01-29
forum: Art &amp; Design
---

### Post by Lfrb on 2007-01-29
Hi,

Am I the only one who has a really really ugly Cancel icon ?? There is also the "No" icon (I guess) that is really inconsistent with the "Yes" icon. It's only a red circle (look like a red LED) Is it normal ?

Here is a screenshot

--
Louis-Francis

---

### Post by paparucino on 2007-01-30
> **Lfrb said:**
> Hi,

Am I the only one who has a really really ugly Cancel icon ?? There is also the "No" icon (I guess) that is really inconsistent with the "Yes" icon. It's only a red circle (look like a red LED) Is it normal ?

What do you mean with inconsistent? it seems normal for me.

---

### Post by Lfrb on 2007-01-30
You're right, my bad...the "Yes" icon or "Ready" icon is a green circle. But they are still ugly icons. And the cancel icon definitively doesn't look like the "Apply" and "Ok" icons.

Why ??

Can you post a screenshot of your cancel button !?

--
Louis-Francis

---

### Post by paparucino on 2007-01-30
> **Lfrb said:**
> You're right, my bad...the "Yes" icon or "Ready" icon is a green circle. But they are still ugly icons. And the cancel icon definitively doesn't look like the "Apply" and "Ok" icons.

Can you post a screenshot of your cancel button !?
Is there a particular program which shows in that way or all the programs act in that way?
Tell me an application.

---

### Post by Lfrb on 2007-01-30
I have the same "ugly" cancel icon EVERYWHERE ...and I got the "Ready" and "Not ready" icons in baobab.

It's really weird because Tango and Human don't have any icon to override the default GTK cancel icon !?!

Why ?

Thanks
--
Louis-Francis

---

### Post by Lfrb on 2007-01-30
I just got another example of what I tried to explain.

Here is the window that appears when I quit Gaphor.

--
Louis-Francis

---

### Post by paparucino on 2007-01-31
> **Lfrb said:**
> I just got another example of what I tried to explain.

Here is the window that appears when I quit Gaphor.

I've no idea, but IMHO I don't see any strange behaviuor.

---

### Post by Lfrb on 2007-01-31
Ok,

I might be the only one who doesn't like to have a very pixelated red X on every Cancel buttons when the Apply button have an icon consistent with the Human theme.

I would prefer to have another icon, but I guess I will have to create it myself and to change the theme.

Thanks
--
Louis-Francis

---

### Post by Robvdl on 2007-02-20
You're not the only one, I personally dislike the red X for cancel buttons too, it's very ugly, even the old yellow arrow in Dapper was nicer for the GTK cancel buttons than this new icon in Edgy.

And the red dot for the GTK 'no' button is very ugly too, very outdated, both these icons seriously need updating in both the Human and Tango icon sets, so they match the rest of the icons.

---

### Post by tom56 on 2007-02-22
> **Lfrb said:**
> I have the same "ugly" cancel icon EVERYWHERE ...and I got the "Ready" and "Not ready" icons in baobab.

It's really weird because Tango and Human don't have any icon to override the default GTK cancel icon !?!

Why ?

Thanks
--
Louis-Francis

There is actually a reasoning behind this, if I recall correctly. Technically no GNOME program should ever have a "Cancel", "Yes", or "No" button as it goes agains the Human Interface Guidelines. The reason being that these buttons' functions are often confusing - instead developers are meant to use verbs e.g.

instead of:

Do you want to save this file?
Yes        No

use:

Do you want to save this file?
Save      Discard

Because these buttons are being phased out they are not considered to be a priority when creating new icon sets (and both Human and Tango are still relatively new).

---

### Post by garba on 2007-02-28
whatever, that icon stinks and keeps popping up all over the place, the same goes with the dread emblem icon used to mark inaccessible folder, i really can't understand why the art team won't update these icons, they spoil an otherwise perfect artwork with their crappy look, too bad

---

### Post by Jimmy_r on 2007-02-28
> **garba said:**
> whatever, that icon stinks and keeps popping up all over the place, the same goes with the dread emblem icon used to mark inaccessible folder, i really can't understand why the art team won't update these icons, they spoil an otherwise perfect artwork with their crappy look, too bad

Because the art team no longer has any influence over those things.
Sabdfl and his hand-picked artist runs the show now...

---

### Post by zoop on 2007-03-17
> **tom56 said:**
> There is actually a reasoning behind this, if I recall correctly. Technically no GNOME program should ever have a "Cancel", "Yes", or "No" button as it goes agains the Human Interface Guidelines. The reason being that these buttons' functions are often confusing - instead developers are meant to use verbs.

Can you point me to a document where this is stated?

I only found several references in the HIG to OK and Cancel buttons, even with screenshots of the same, see for instance [here](http://developer.gnome.org/projects/gup/hig/2.0/controls-buttons.html).

---

### Post by tom56 on 2007-03-17
> **zoop said:**
> Can you point me to a document where this is stated?

I only found several references in the HIG to OK and Cancel buttons, even with screenshots of the same, see for instance [here](http://developer.gnome.org/projects/gup/hig/2.0/controls-buttons.html).

Um, they first sentence of the page you pointed me to perhaps...?

"**Label all buttons with imperative verbs**, using header capitalization. For example, Save, Sort or Update Now. Provide an access key in the label that allows the user to directly activate the button from the keyboard."

---

### Post by zoop on 2007-03-18
> **tom56 said:**
> "**Label all buttons with imperative verbs**, using header capitalization. For example, Save, Sort or Update Now."

Fair enough, but with all the "OK" and "Cancel" buttons plastered all over the HIG I still fail to see this as a strict requirement.

For one, I think a "Cancel" button - which BTW **is** a verb - will always be useful. There are several dialogs in Ubuntu where I couldn't think of anything else to call the button. The OK button is a different story though...

What I'm trying to say here is that it's not at all clear what the real issue is here...

If the Gnome guys really wanted to get rid of all OK and Cancel buttons, then they should announce that prominently so people like me can make patches to the applications which still have them.

If they don't then I really can't understand why people develop icons for [MP3 players, Gamepads and every little application](http://tango.freedesktop.org/Tango_Fridays) and we still don't have a cancel icon. I just fail to see how someone who's interested in artwork can live with that ugly one...

But, things being the way they are, at least Ubuntu should care about its Look and Feel and include an own icon, at least in the default theme. In [the bug report about the missing icons](https://bugs.freedesktop.org/show_bug.cgi?id=8057) there's a link to ones that look like the current ones only nicer.

---

### Post by tom56 on 2007-03-18
There are other factors in play here as well though. For example any changes you make using a program (e.g. in a preference window) should apply instantly so there ought to be no need for a cancel button as you can't cancel anything anyway.

---

### Post by Jimmy_r on 2007-03-20
Here is some more on this: [http://developer.gnome.org/projects/gup/hig/2.0/windows-utility.html](http://developer.gnome.org/projects/gup/hig/2.0/windows-utility.html)

---

### Post by zoop on 2007-03-21
> **Jimmy_r said:**
> Here is some more on this: [http://developer.gnome.org/projects/gup/hig/2.0/windows-utility.html](http://developer.gnome.org/projects/gup/hig/2.0/windows-utility.html)

This all true and I agree with it. But none of this says that no Cancel buttons should exist. In fact many of the screenshots there include a cancel button and some even an OK button.

Some dialogs where I think a Cancel icon is in order:
[list]
[*] Logout dialog
[*] Empty Trash dialog
[*] Add user dialog (click "Add user" in the User and Groups control panel applet)
[/list]

The last one is an example where instant apply doesn't make much sense.

So I'm still unconvinced that "there is no actual need for a cancel icon" is the actual reason that no good one exists...

I have really no idea what the real reason is, though... And the same goes with the completely insane behavior of the tasklist applet, that's also bugging me for years...

But enough with the ranting! GNOME is still the best free desktop. I recently tried Kubuntu again and while they have a nice cancel icon I was back to GNOME/Ubuntu within the same day... :)

---

### Post by lapsey on 2007-03-22
Regardless if it is the 'right' thing not to have a cancel button or not - you should only drop the icon until you can guarantee all apps won't use a cancel button. I thought the aim for ubuntu was a consistently slick UI. Or was I wrong?

Heck, if you want to talk bloodyminded principles why don't they just go the whole hog and only supply TWM or ratpoison as the default ubuntu window manager? It's more efficient, don'tcha'know, and besides, REAL ubuntu users don't need graphics.

---

### Post by tom56 on 2007-03-22
But it's not a case of bloodyminded-ness. The current icon works fine. It isn't seen often for the reasons we've been over, and therefore when making new icons it doesn't really take priority. If you don't like it, go talk to the Tango folks or the GNOME folks and I'm sure they'll be happy to let you design a new one for them. It's not that they think the current one is perfect, just that other icons are more important.

---

### Post by garba on 2007-03-22
ok but the truth is, that icon is still there, it looks like crap and pops up from time to time i.e. it gives a HORRIBLE impression, it's a stain on an otherwise wonderful artwork... the same applies with the icon used as an emblem when a folder is not accessible (cross in a red square), funny thing is we already have an "unauthorized" emblem in the human iconset but it's not being used... and don't get me started on the emblem used for symlinks :)

---

### Post by aidanr on 2007-03-22
couldn't agree more, there are a few ugly icons in an otherwise beautiful set, it's a pity that cancel one shows up so much :???:

---

### Post by tom56 on 2007-03-27
It's your lucky day! (Or Friday is)

Tango Friday are doing all the GTK stock icons (including cancel) - [http://www.andreasn.se/blog/?p=44](http://www.andreasn.se/blog/?p=44)

I suggest you head along to the #tango on freenode and help them out.

---

### Post by bsantos on 2007-03-28
Connect to server... has an ugly cancel button. :p

---

### Post by hugmenot on 2007-03-29
BTW, the cancel icon has already been dealt with in g-i-t subversion just by linking it to process-stop.

---

### Post by aidanr on 2007-03-29
that looks much better =D>

---

### Post by kpolice on 2007-03-30
Some work from the tango guys:
[http://www.andreasn.se/blog/?p=45](http://www.andreasn.se/blog/?p=45)
[http://www.andreasn.se/blog/images/gtk-tango.png](http://www.andreasn.se/blog/images/gtk-tango.png)

[IMG]http://www.andreasn.se/blog/images/gtk-tango.png[/IMG]

---

### Post by lapsey on 2007-04-15
That's delicious!

It's great to see a fully consistent icon set in Feisty. <3 Tango project.

---

