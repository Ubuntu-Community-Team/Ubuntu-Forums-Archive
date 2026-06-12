---
title: "Beginner Questions :) [help :) ]"
date: 2007-07-20
forum: Absolute Beginner Talk
---

### Post by AranelSurion on 2007-07-20
There is my questions (please help me :) ) ;

1. How can I add a "background image" to ttyX (CTRL ALT F1-F2 ..)  ? And how can I choose 1024X768 for ttyX? 

2. How can I add "multimedia shortcuts" from my keyboard*? I know "Keyboard Shortcuts" , But I'm wanting bind (Back) , (Next) and (Stop) keys.

[SOLVED] 3. How can I stop the "Spell Checking" in Firefox? (and other programs?)

4. How can I start the "Task Manager" from keyboard shortcut. CTRL + ESC combination doesn't work.

5. How can I setup and test my webcam? [test-webcam won't work?]

Sorry, but I'm really beginner and this questions are big problems for me. Please, help me :)

P.S: Yes, I don't know English very well.

---

### Post by Kingsley on 2007-07-20
Go to the advanced section of the Firefox preferences to turn off spell checking.

---

### Post by tomcheng76 on 2007-07-20
4 How can I start the "Task Manager" from keyboard shortcut. CTRL + ESC combination doesn't work.
[http://ubuntuforums.org/showthread.php?t=412228](http://ubuntuforums.org/showthread.php?t=412228)

---

### Post by alphane on 2007-07-20
2. How can I add "multimedia shortcuts" from my keyboard*?

I've got my multimedia keys set up in keyboard shortcuts. Exaile (my music player) picks up on these keys and skips/stops tracks etc as I would expect - I assume this would work for you also?

---

### Post by MohitRajani on 2007-07-20
How can I add a "background image" to ttyX (CTRL ALT F1-F2 ..) ? And how can I choose 1024X768 for ttyX? 

the x window is on CTRL +ATL + F7.
just right click on the desktop and at the bottom click "Change Desktop Background".

to change the screen resolution go to System->Preferences->Screen Resolution

---

### Post by tomcheng76 on 2007-07-20
i think that he meant the console 1 to 6
by pressing CTRL ALT F1 - F6
i want to know also, dark background is boring...

---

### Post by AranelSurion on 2007-07-20
> **MohitRajani said:**
> How can I add a "background image" to ttyX (CTRL ALT F1-F2 ..) ? And how can I choose 1024X768 for ttyX? 

the x window is on CTRL +ATL + F7.
just right click on the desktop and at the bottom click "Change Desktop Background".

to change the screen resolution go to System->Preferences->Screen Resolution

Thanks for your answer, but I'm not wanting background and resolution for X. I'm wanting for ttyX. CTRL ALT F1 etc.

---

### Post by AranelSurion on 2007-07-20
> **alphane said:**
> 2. How can I add "multimedia shortcuts" from my keyboard*?

I've got my multimedia keys set up in keyboard shortcuts. Exaile (my music player) picks up on these keys and skips/stops tracks etc as I would expect - I assume this would work for you also?

Thanks for your answer.

Yes, works. But i'm wanting "custom shortcuts". Example ; Press "Back" multimedia button and FFox(or Nautilus etc.) back 1 page. Another example ; Press "Computer" multimedia button and Nautilus gives you the hdb1 directory.

---

### Post by Mornedhel on 2007-07-20
I think GNOME does not have any other shortcuts than the ones in the Keyboard Shortcuts section. Beryl lets you configure more, and if you don't want something that heavy just for shortcuts, then xbindkeys (not sure of the name) may help you (binds custom commands to keys). You can, however, easily bind a key to your Home directory in Nautilus (in the GNOME Keyboard Shortcuts). I think there are shortcuts for Next, Previous, Play/Pause and the like there (not sure, don't remember). If so, just press your multimedia keys as you would any other.

Also remember, almost all GNOME applications let you reassign accelerators : open the application of your choice, let's say Epiphany, click on the File menu item, hover down to Quit, and press Ctrl Alt Shift T (or whatever). The Quit action is now bound to Ctrl Alt Shift T. This might help you for some of your needs (the Back button for instance).

Also, the tty1-6 do not need the X Server to run and may be used even if you messed up your xorg.conf (deceptively easy when poking around to get custom resolutions). Not sure you can set a background for them. If you really want a console-only tty with a background, create a new gnome-terminal profile with a background image, and run it fullscreen (F11).

[Edit : oh my god, accidentally forgot the f in shift, got edited out...]

---

### Post by louieb on 2007-07-20
1. How can I add a "background image" to ttyX (CTRL ALT F1-F2 ..)  ? And how can I choose 1024X768 for ttyX?
[http://www.faqs.org/docs/Linux-HOWTO/Bash-Prompt-HOWTO.html#AEN343](http://www.faqs.org/docs/Linux-HOWTO/Bash-Prompt-HOWTO.html#AEN343)
Don't know about the image but text color can be changed maybe the background color too.  
Google is you friend.  [Linux - Google Search]("http://www.google.com/linux")

---

### Post by alphane on 2007-07-21
> **AranelSurion said:**
> Thanks for your answer.

Yes, works. But i'm wanting "custom shortcuts". Example ; Press "Back" multimedia button and FFox(or Nautilus etc.) back 1 page. Another example ; Press "Computer" multimedia button and Nautilus gives you the hdb1 directory.

Back in Nautilus with backspace works automagically for me.  Firefox, however, does need some tweaking.

Place "about:config" in the firefox address bar. Filter for or look for any entry that contains "backspace".  The key value for this will be set to 0 - set it to 1.

Close, reopen, et voila!

---

