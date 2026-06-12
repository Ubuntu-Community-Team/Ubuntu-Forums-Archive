---
title: "No Danish special keys?"
date: 2006-07-29
forum: Absolute Beginner Talk
---

### Post by tjp.thomas on 2006-07-29
Boy... did I stumble onto a potential Ubuntu show-stopper here i Denmark.. I have installed Ubunto Dapper Drake, and untill 5 minutes ago, I was loving it. Now I am not so sure... I cannot use any of the special danish characters!

In xorg.conf I have 

<code>
Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"dk"
	Option		"XkbVariant"	"dk"
EndSection
</code>

However that does not do it for me. Can anyone help me finding a solution to this problem?

TIA!

---

### Post by Fass on 2006-07-29
Tried setting the keyboard layout through Gnome's settings?

---

### Post by tjp.thomas on 2006-07-29
Can you help me there? where to go?

---

### Post by dsokus on 2006-07-29
On your desktop panel, 

System->Preferences->Keyboard->Layouts

"Add", and select Denmark->"Eliminate dead keys" from the list on the left. This should enable the Danish keys. 

In order for you to be able to select it comfortably on your desktop, right-click the panel, select "Add to panel" from the drop-down menu, scroll down and under "Utilities" double-click "Keyboard Indicator". A little sign should appear on the Panel, which you can click to change the language.

It worked for me: æ Æ ø Ø å Å

Hope this helps. :)
Another (K)Ubuntu user from Denmark.

---

### Post by tjp.thomas on 2006-07-29
I cannot edit the layout!?!? I get an error when activating XKB configuration... Now can anyone help me?

---

### Post by dsokus on 2006-07-29
What is that error?

---

### Post by tjp.thomas on 2006-07-29
Error activating XKB configuration.
This could be due to several circumstances:
- a bug in libxklavier library
- a bug in X server (in utility programs xkbcomp o xmodmap)
- a X server with a not compatible implementation of libxkbfilebile

Server X versin:
The X.Org Foundation
70000001

---

### Post by tjp.thomas on 2006-07-29
I works now ?!?!?... just logged out-in... and got æøå\ and $!.... THANKS GUYS!... the Eliminate dead keys did the trick!

---

### Post by dsokus on 2006-07-29
OK, try this: open a Terminal window, and type 

$ setxkbmap -layout 'dk,us' -model pc105

Then try setting it again. Do you get the same error?

---

### Post by dsokus on 2006-07-29
Oh, great that it works now. Enjoy! :D

---

### Post by tjp.thomas on 2006-07-29
Then it stops working... will try $ setxkbmap -layout 'dk,us' -model pc105 and get back with results!

---

### Post by tjp.thomas on 2006-07-29
Initially; it worked using the setxkbmap -layout 'dk,us' -model pc105. I could use Danish characters and from the keyboard indicator I could select either DK or US keyboard. However, loggin out and back in reverts the situation. I get an error prompt with xkb problems upon login, and I can no longer select US from the indicator- am now testing setxkbmap -layout 'dk' -model pc105. Will get back with results.

---

### Post by tjp.thomas on 2006-07-29
This is very strange. If I use the setxkbmap -layout 'dk' -model pc105 danish is back in business... but only until I login again... then I need to redo the command again. any help?

---

### Post by Thirsteh on 2006-07-29
You could just make a simple shell script that does 'setxkbmap -layout 'dk' -model pc105 danish' at boot and put it in init.rc, but I am prettttyy sure there's an option in the xorg.conf file where you can select the keymap.

It's strange, I've never had this problem in Linux, (and I'm danish too) except in Gentoo, but only because you have to do it manually there anyway. Did you choose 'Danish' during the installation?

---

### Post by tjp.thomas on 2006-07-29
My xorg.conf looks like this:
Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"dk"
	Option		"XkbVariant"	"dk"
EndSection

To me that indicates that it should in fact be setup correctly. Can you help me with the shell script?

---

### Post by Fass on 2006-07-29
This is a longshot, but I've heard about people having problems with "Option XkbVariant." I don't have the line in my xorg.conf and my Swedish keyboard works just fine, so it might be worth removing it and then restarting X to see if that helps.

You could also try out reconfiguring X by running

```
sudo dpkg-reconfigure xserver-xorg
```

---

### Post by dsokus on 2006-07-29
> **tjp.thomas said:**
> This is very strange. If I use the setxkbmap -layout 'dk' -model pc105 danish is back in business... but only until I login again... then I need to redo the command again. any help?
Oh, you do need to run that every time you start a session. Go to
System -> Preferences -> Sessions -> Startup commands, "Add", and write the line to "command". Then it's supposed to work every time you start the session. 

I got the info from another thread here, namely [http://ubuntuforums.org/showthread.php?t=75197](http://ubuntuforums.org/showthread.php?t=75197)

I hope it works. :)

---

### Post by tjp.thomas on 2006-07-29
THAT DID IT!!!... added it to startup... now it works... THANKS GUYS!

---

### Post by Sharpeee on 2006-09-14
I get the same error message everytime I log in! The keyboard layout problem got fixed by deleting the "kbdvariant" line in xorg.conf.
Now, how do I get rid of this error message?

---

