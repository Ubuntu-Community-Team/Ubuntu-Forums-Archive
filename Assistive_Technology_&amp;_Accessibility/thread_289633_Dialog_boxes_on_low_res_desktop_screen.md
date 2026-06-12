---
title: "Dialog boxes on low res desktop screen"
date: 2006-10-31
forum: Assistive Technology &amp; Accessibility
---

### Post by leona on 2006-10-31
Hi

I'm visually impaired and so, I run my desktop at 800x600 so that everything is nice and large such I don't need to use any magnification, I find this quicker for me.

I'm using Ubuntu 6.06 with the GNOME desktop at 800x600

Anyway one side effect of this is that application dialog boxes often are designed for much higher resolution desktops, so that some buttons like 'ok', 'apply' are off my screen.  It will not let me drag the box above or over the task bar, so all I an do is guess and tab till I think I hit got the right button.

I know I could switch to I higher resolution, but then I'd not be able to read it.

Just wondering if anyone else has this issue and if there is some kind of workaround.

Thanks

Leona.

---

### Post by Henrik on 2006-10-31
Hi Leona,

It is a recognised problem that several dialog boxes in gnome do not fit withing 800x600 displays. 

It would be very helpful if you could file bugs agains specific packages in our bugtracker: [https://launchpad.net/distros/ubuntu/+bugs](https://launchpad.net/distros/ubuntu/+bugs)

Like: [https://launchpad.net/distros/ubuntu/+source/evolution/+bugs](https://launchpad.net/distros/ubuntu/+source/evolution/+bugs)

Also useful is filing bugs upstream in gnome:
[http://bugzilla.gnome.org/](http://bugzilla.gnome.org/)

Please ask if you need further help on filing bugs.

---

### Post by leona on 2007-05-18
Arr right, just come across one, but I think I know what your gona say, its a Mozilla issue, but I'll mention it anyway.
I actually use a res of 1024x780 with large (16pt) fonts, works well for me.
I was just using thunderbird and I needed to add a contact, the contact screen comes up , but the OK anc Cancel buttons are off the screen, as is a good part of the last lot of fields.
Just thought I'm mention it, maybe someone to pass that into along to the mozila devs or something?
I noticed you can't drag a dialogue box up pass the 'taskbar' like you can in windows, so there is no way to access these buttons.
thankfully just pressing enter is ok, but still annoying.

Cool, just submitted a [ Bug report ]("https://bugs.launchpad.net/ubuntu/+source/thunderbird/+bug/115484"), probably now get flamed off the bugzilla list, but at least I tried :)

---

### Post by frafu on 2007-05-22
Hello, 

Using the tab button on your keyboard, you can navigate through the items in the dialogue box. It also navigates to the OK and Cancel buttons, even if they are offscreen. The only problem remains that you have to guess whether OK, Cancel (Apply) is highlighted, as you don't see it. 

Enabling the reader to have it spoken to you might help further; but it should also be possible to do it with guessing. (At least I did it yesterday in a windowed wine session. 

Have a nice day. 

Francesco

---

### Post by leona on 2007-05-23
Thanks Francesco and yes you are right you can 'guess' it, but it would be nice if that screen was designed to fit on a lower res system.
I got a reply to the bug to say I can use the Alt while dragging the dialog box, I find this a bit hit and miss sometimes it works sometimes it doesn't.
Its great that there are workarounds, but isn't there some way we could preasure for these apps to be changed, so that workarounds are not necessary?  Isn't that the point of OSS?
The simpilest thing to fix this would be add another tab for address details, that would shorten the dialog thus fix the problem.

---

### Post by frafu on 2007-05-23
Hello leona,

Thanks for telling me about the workaround with the Alt-modifier. 

In fact, with my previous post, I only wanted to tell you about the workaround. On the principle, I agree with you. As long as only the buttons are offscreen, the guessing system is helpful, but it gets more complicated when there are also options offscreen. 

IMHO, the designers should not assume that everybody is using a 1024X768 resolution; I think they should start to try to size the dialogues for a 640x480 resolution. On the other hand, I don't know what the Human User Interface Guidelines suggest... 

Have a nice day.

---

### Post by leona on 2007-05-28
Found another, on Fiesty, Login window is too long for the screen, again options are off the bottom of the screen, again you can use alt and move the mouse to get around this, but there does seem to be a lot of unsed space on the screen, so why is it so big?

---

### Post by leona on 2007-11-04
Noticed that now I have upgrade to Gusty the Alt and drag no longer works, I can not drag a dialog box over the task bar, so when I went to input another contact into Thurderbird again today I could only view half way down the form and had to guess the rest. :(
Can someone please ask the Moz Devs to redesign the input screen, it just doesn't fit on the screen.

---

### Post by cipher_nemo on 2008-01-03
Yes, I've seen this issue as well in 800x600 resolutions. However, it starts to affect every single dialog box for ubuntu itself when the font size is increased.

A better solution for this is to have the development team **put all window/dialog controls inside a panel that will automatically show scroll bars** if the content is larger than the window/dialog size.

This seems like the only sensible solution to me, because there is no way you can account for everyone's resolution. If you fix it for 800x600, then the 640x480 people may still have issues, etc., etc.

I currently use 800x600 for a TV (s-video) output that is the main 'monitor' used for an Ubuntu box running MythTV (built it for my father). Add to that equation his 7+ decade-old eyesight, and it's clear that the dialogs in Ubuntu are not friendly for anything 1024x768 and less because of the need for increasing font sizes.

I'll take a look at the bugs, but posting it on the forums is so much easier for me right now.

---

