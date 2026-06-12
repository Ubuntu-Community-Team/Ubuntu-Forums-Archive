---
title: "Erm where have my icons gone??!?"
date: 2007-06-06
forum: Absolute Beginner Talk
---

### Post by dgrafix on 2007-06-06
A little wierd something, i seem to have inadvertently turned off my desktop icons. I can see them in the desktop folder but they are not appearing :/

Any ideas?

---

### Post by p_quarles on 2007-06-06
You're using Gnome? That really is weird. I spent a couple minutes looking for ways to make the icons disappear on purpose, but couldn't. Can you still see panels and panel-launchers? If you make a new desktop launcher from the App menu, does it appear?

---

### Post by steeleyuk on 2007-06-06
Have you tried restarting the computer or restarting X? sometimes Nautilus decides to hide all my icons from me and they don't come back till I log back in again...

---

### Post by lepz on 2007-06-06
Do you have Beryl or Compiz set to load on start-up?

---

### Post by mcduck on 2007-06-06
Try restarting Nautilus (It's the file manager in Gnome, and also handles your desktop). 'killall nautilus' should do the trick.

---

### Post by coffeecat on 2007-06-06
Have a look under Applications > System Tools. Is "Configuration Editor" showing in the list? I can't remember whether it shows in a default install. If it isn't, go to System > Preferences > Main Menu and enable it under System Tools. Once you've opened Configuration Editor, go to apps > nautilus > desktop and check or uncheck whichever icons you want showing.

However, these are the Computer, home, mounted volumes, trash, etc icons and these do not show up in your Desktop folder so I wonder if you are talking about icons for files or launchers that you have put on your desktop. If so I can't help.

---

### Post by dgrafix on 2007-06-10
"Do you have Beryl or Compiz set to load on start-up?"

I did but i removed it. How would beryl make them dissapear? when i was running it i had icons then they just went away.

I have configuration editor but it doesnt make a difference doing that

Basically Nothing is showing, at all...  I cannot even right click on it to get a menu :(

---

### Post by Efros on 2007-06-11
same here

---

### Post by dgrafix on 2007-06-13
Hmm i didnt find the problem but found a fix :/

create a new user then log into that account to create the settings .folders in a new home dir

then copy the new virgin hidden folders for gnome, nautilus, beryl (needs to be run), metacity in new home folder over the broken home folder ones. Im not sure which program was causing the error so i did every one that epossibly effects desktop and icon settings.

This will put everything back to normal :)

I guess you could try deleting them straight out but i figured this way is better because at least then theres a fallback login if it went wrong big time.

Mabe someone has a more scientific approach lol.

---

### Post by Midahed on 2007-06-21
I've had a similar problem several times today.  I have a number if files and links to websites on my desktop.  Four or five times today these have all disappeared.  Once it happens, if I try to open my home or documents folders via the 'Places' menu I get the Ubuntu equivalent of the egg-timer for a couple of seconds, but nothing happens.  I can still open terminal and browser sessions, though.  So I carry on using the PC and some time later - usually just a few minutes - everything comes back.  When it does come back I also get windows opening as a result of my earlier failed attempts to view my home and documents folders.  It's as if something goes to sleep for a while....

At the moment I just have a fairly new default install of Ubuntu 7.04 Feisty 64-bit with very little in the way of add-on packages.  No Beryl here.

Any ideas as to what's causing it, or pointers as to which logfiles I should inspect?

Thanks,

Mike

---

### Post by dan171717 on 2007-06-21
i sometimes getthis problem but it is fine ater a reebot.

in my case i think it is beryl. in your case (possably mine) it might be a bug in gnome

---

