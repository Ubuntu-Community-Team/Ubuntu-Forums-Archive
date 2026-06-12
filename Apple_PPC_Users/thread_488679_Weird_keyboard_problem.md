---
title: "Weird keyboard problem"
date: 2007-06-30
forum: Apple PPC Users
---

### Post by joninkrakow on 2007-06-30
I have a Pismo. I installed Ubuntu last week, and had no problems with the keyboard in the Gnome system or KDE. In my experimenation, I uninstalled it, and tried Yellow Dog, and failed with an install of OpenSUSE, so I re-loaded Ubuntu, and now, my shift keys don't work in Gnome! The cursor blinks when I type a letter, but nothing comes out! I don't think I changed anything from the default on install, and besides that, I've tried just about everyhing I could think of, changing to various keyboards, but nothing changes it. As you can see, caps work in OS X, and in the buffer terminal windows in Ubuntu (control-alt-Fkeys), but _not_ in the terminal in Gnome! Worse, I am pretty sure they were working last night when I installed Ubuntu, and probably this morning. I think the only "change" is that I added some Apple fonts. Could that have done it? (Unfortunately, I don't remember when the problem started--I wasn't typing caps until later this morning. Right now, Ubuntu is useless to me until I can solve this problem... TIA

-Jon

---

### Post by joninkrakow on 2007-06-30
I am happily replying to myself in Firefox Ubuntu--notice the caps, ;-) I solved it, and am posting in reply in case somebody else finds themselves with this problem.

I discovered the problem quite by accident. I thought my problem might be the fonts, so I rebooted Ubuntu, but while my session was reloading, I found myself in the terminal. On a whim, I hit a cap-key, and it worked! However, a couple seconds later--it didn't! The only difference was that the Gdesklets had launched! I had forgotten I had added those. I disabled them, and got my caps back! Now, how does one submit bug reports for that.... ;-) On my way to find out. Sorry to bother everybody here.

-Jon

---

### Post by reh4c on 2007-06-30
> **joninkrakow said:**
> I am happily replying to myself in Firefox Ubuntu--notice the caps, ;-) I solved it, and am posting in reply in case somebody else finds themselves with this problem.

I discovered the problem quite by accident. I thought my problem might be the fonts, so I rebooted Ubuntu, but while my session was reloading, I found myself in the terminal. On a whim, I hit a cap-key, and it worked! However, a couple seconds later--it didn't! The only difference was that the Gdesklets had launched! I had forgotten I had added those. I disabled them, and got my caps back! Now, how does one submit bug reports for that.... ;-) On my way to find out. Sorry to bother everybody here.

-Jon

Hello!  I noticed this problem a few weeks ago, and followed up on a gnome bug located here:
[http://bugzilla.gnome.org/show_bug.cgi?id=430612](http://bugzilla.gnome.org/show_bug.cgi?id=430612)
Hopefully, the developers can fix it!
Also, please see this post for a workaround:
[http://ubuntuforums.org/showthread.php?t=482513&highlight=caps](http://ubuntuforums.org/showthread.php?t=482513&highlight=caps)
:popcorn:

---

