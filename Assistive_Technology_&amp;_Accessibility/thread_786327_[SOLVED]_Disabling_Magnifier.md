---
title: "[SOLVED] Disabling Magnifier"
date: 2008-05-08
forum: Assistive Technology &amp; Accessibility
---

### Post by net-cat on 2008-05-08
(If this is in the wrong area, I apologize in advance.)

I've been using Ubuntu 8.04 for a few weeks now. It's pretty nice, but there are a few things about it that are exceedingly annoying.

The main thing is the fact the the magnifier application is bound to Super+R. I'm used to using that to launch the "Run" box in Windows, so I still go for that sometimes as a force of habit. I don't mind changes in key combinations, but the way this is executed is unforgivable.

It just launches the magnifier application and gives no information on how to undo it. Repeating Super+R doesn't undo it. There is no obvious process I can grep for and kill. There is no icon in the system notification area. There is no information about what's going on what so ever. The only way I've found to get rid of this is to either log out and log back in, or just Ctrl+Alt+Backspace.

So, I would like to know two things:[list=1][*]Once the magnifier is launched, how do I kill it?[*]How do I disable the binding to Super+R?[/list]

I'm using Ubuntu 8.04 x86_64, ATI Radeon HD 2600, ATI Proprietary Drivers and "Extra" Visual Effects in a dual-monitor "big-desktop" configuration. If any other configuration information is needed, I will be happy to supply it.

I've attached a [screen shot](http://ubuntuforums.org/attachment.php?attachmentid=69217&stc=1&d=1210226165) of what's going on.

---

### Post by RCC2k7 on 2008-05-08
The keystroke for the Run box is ALT+F2.

I think the package to download is ccsm from Synaptic. This adds the Custom button on the Visual Effect tabs. Press that button and look for the Zoom plugin. Uncheck the box next to the Zoom plugin to disable it.

---

### Post by net-cat on 2008-05-09
Thank you. That solved the problem. If anyone else has the same question, this is what I did:

Install "simple-ccsm" from Synaptic.
System -> Preferences -> Simple CompizConfig Configuration Manager
On the Accessibility tab, uncheck "Screen Zoom."

(It would be nice if there were a pop-up explaining that the first time it's activated. Without something to that effect, it might alienate Windows users who have far less patience than I do.)

---

### Post by RCC2k7 on 2008-05-10
> **net-cat said:**
> Thank you. That solved the problem. If anyone else has the same question, this is what I did:

Install "simple-ccsm" from Synaptic.
System -> Preferences -> Simple CompizConfig Configuration Manager
On the Accessibility tab, uncheck "Screen Zoom."

(It would be nice if there were a pop-up explaining that the first time it's activated. Without something to that effect, it might alienate Windows users who have far less patience than I do.)

It might alienate some Windows users but make others happy once they find out both of the magnifiers that can be used in Ubuntu are way better than the magnifier that ships with Windows.

---

### Post by Phyzzip on 2008-07-13
Seconded on the pop up. It's nice that there's a screen magnifier that's good etc but when for instance I'm programing in python and accidentally punch that key-combo it's kinda flow breaking to have to go over to my other computer (happened on my rather small screen laptop) and spend a few minutes finding this thread. 

A non-technical user would think it was a bug and grumble while rebooting.

---

### Post by Parama on 2008-07-23
You are so right: This zoom shortcut is actually incredibly annoying. 
Like many others I've used Windows for so many years making the force of habit really stick. 
I think I press the Super+R shortcut about 20-60 times during a normal 8 hour working day for running my command prompt and my beloved PuTTY.
At home I jump right to the shortcut almost every day making me say things I'll probably be banned for life for saying here :-)

---

### Post by JasonSpradlin82 on 2008-10-04
Haha... I totally thought I was reading an entry that I might have typed myself and not remembered.  I had the exact same problem for the exact same reason... Thanks for the fix!

---

### Post by gnulab on 2009-05-20
I agree that this is utterly annoying, specifically to those users who migrated from Windows.

At least a pop up or tool tip to advise users how to exit from the magnified mode. Who would ever thought in order to exit from it, you have to install the ccsm package, then disable it from there.

Perhaps the developer should add some sort of exiting method.

Henry

---

### Post by rob2uk on 2009-05-20
Thank Jeebus I'm not the only one that's been caught out by this!

Thanks guys, I was about to reboot

---

### Post by oxsyn on 2009-07-26
Thanks for solution.

---

### Post by mirror2m on 2009-07-28
Hi guys,

I do not know how you solved the issue, but I found it as <Super><MouseScroll>
And yes, disable ZoomDesktop in Compiz

---

### Post by pvfjr on 2009-09-28
Thanks for the fix!  It should be included by default though.

This is hands down the stupidest thing I've ever run across in an OS. :mad: For the life of me, I can't imagine why they would dream up a trap like this for innocent windows users trying to convert to something new.  It's almost as if they designed it this way, using a very common and habitual shortcut, and no way to get out.  Absolutely ridiculous.

---

### Post by Kangarooo on 2011-02-09
> **mirror2m said:**
> Hi guys,

I do not know how you solved the issue, but I found it as <Super><MouseScroll>
And yes, disable ZoomDesktop in Compiz

Theyre talking about Orca magnifier. Theres no problem with Compiz magnifier. And since compiz magnifier is easiliy activated with mousescroll holding SupaKey then its logical that unscrolling while holding reverses zoom.


BTW a button for orca to quit it is needed. and keypress to enable disable magnifier. For me soluyton opening orca settings didnt work couse on opening orca magnifier some alredy opened windows gets black so i dont see its content.

---

### Post by SundayForever on 2011-02-26
At least a pop up or tool tip to advise users how to exit from the  magnified mode. Who would ever thought in order to exit from it, you  have to install the ccsm package, then disable it from there.

---

