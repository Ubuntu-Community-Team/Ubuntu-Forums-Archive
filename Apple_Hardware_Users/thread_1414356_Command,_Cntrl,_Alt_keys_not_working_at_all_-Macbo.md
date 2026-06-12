---
title: "Command, Cntrl, Alt keys not working at all -Macbook Pro 5,5 w/ 9.10"
date: 2010-02-23
forum: Apple Hardware Users
---

### Post by Sgt_P on 2010-02-23
I have been searching through all the guides, and FAQs, and previous posts, but can't find a resolution to my particular issue - hopefully someone here can help!
 
I have a Macbook Pro 5,5 with Karmic (9.10) 64-bit installed, dual booting with OSX. My problem is, the Command (apple key), Cntrl, and Alt keys don't do anything. For example, if I click Cntrl+C it does not copy, just types a "c" as if I wasn't hitting the Cntrl key at all. I've lost many functions this way.
 
I have tried setting the keyboard layout and model to various setups (Apple-Apple USA, Macbook Pro Intl-USA Apple,....etc) but none work. I've also looked at manually setting the layout, but the visual layout doesn't even have the same number of keys down at the bottom left - my keyboard has 4 (command, control, alt, and function).
 
Any advice is appreciated.

---

### Post by donaldmartin on 2010-02-23
Have you installed all the patches - checking for updates?

---

### Post by Sgt_P on 2010-02-23
> **donaldmartin said:**
> Have you installed all the patches - checking for updates?
 
I've looked at this page :[https://help.ubuntu.com/community/MacBookPro5-5/Karmic](https://help.ubuntu.com/community/MacBookPro5-5/Karmic)
but there isn't anything about my problems with the keyboard.
 
Do you know of any patches for keyboard function on MabookPro 5,5 with 9.10?

---

### Post by alexmurray on 2010-02-24
I take it this is for the standard keyboard built into you MBP? This should work out of the box unless you've changed the keyboard layout or something...

Try setting the Keyboard layout to the standard US.

Also try checking /var/log/Xorg.0.log for any messages related to keyboard model etc too..

---

### Post by Sgt_P on 2010-02-24
It is the built in keyboard. I'm not sure why it doesn't work with default install settings/detection. I have already tried standard US layout (along with every other layout that looked remotely applicable).
 
Can someone running the same configuration (MBPro 5,5 w/ 9.10 64-bit) without problems open up their keyboard layout setting and tell me what the layout/model is set to? Hoping that will do it...

---

### Post by inphektion on 2010-02-24
have you installed pommed?  I never did and keyboard works fine but i know in the wikis it says to.

---

### Post by Sgt_P on 2010-02-24
> **inphektion said:**
> have you installed pommed?  I never did and keyboard works fine but i know in the wikis it says to.
I did install pommed, but it seems to only fix other issues like keyboard backlighting, or Fn key issues.
 
If yours is working, would you mind posting the layout/model from your Preferences->Keyboard->Layout window?

---

### Post by Sgt_P on 2010-02-25
Ok, I have made some progress. Here is what I have tried, and what has/hasn't worked:
[INDENT]1. I tried a new install on a different partition to check if the installation detection works - it does not for me, same problem.
[/INDENT][INDENT]2. I was able to set the Control key location through the Preferences->Keyboard->Layout window. I now have Cntrl+C for copy capability, for example.
[/INDENT][INDENT]3. I checked the output for the other three keys (Fn, Alt, and Command) and got an output number for 2 of them. Fn doesn't seems to be registering at all.
[/INDENT]If anyone is still following this and can assist, do you know how to change the keymapping in Karmic. That would allow me to fix Alt and Command. I use Command *a lot* to bring up the contextual menu with a command+mouseclick on my iMac/Karmic, would like to do so on my MBP as well.
 
More importantly, why in the world am I the only person that seems to have this problem!!! Sigh.

---

### Post by linuxopjemac on 2010-02-25
All I know about this sort of thing is in the keyboard section you can select layouts, then layout options. I have the left Alt setup to have the 3rd level keys....maybe it is of any help to you.

---

### Post by jerrycal on 2011-05-16
This a year old, but in case anybody is having the problem with MacBook Pro 5,5 (and others, most likely) here is the fix: 
[https://help.ubuntu.com/community/AppleKeyboard#Default%20Behavior](https://help.ubuntu.com/community/AppleKeyboard#Default%20Behavior)

---

