---
title: "Showing &amp; Typing International Characters?"
date: 2005-05-12
forum: Apple PPC Users
---

### Post by ipixel on 2005-05-12
Just downloaded and tried both Ubuntu and Kubuntu Live CDs on a couple of old iMacs - congratulations on such an incredible community effort!

I'm a seasoned Mac user, but a Linux newbie, so please forgive me if my questions are basic - the solutions are probably glaringly obvious to an expert user, but can keep a not-so-bright beginner like me occupied for days and days!

I speak Portuguese and Esperanto - the international language. I regularly visit websites that use international characters, and correspond on a daily basis with people who use accented letters and non-latin alphabets. Therefore, it is absolutely vital for me that the system and programs I use can handle UNICODE - that they can not just display these characters easily, but also allow me to type accented latin characters. On the Mac, this is quite easy - the Mac comes with many fonts that have the extended character set we need, and the 'US Extended' Unicode keyboard layout allows me to type all the characters I neeed.

Tiger and Panther are both *terribly* sluggish on my little old iMacs, though. So, I was absolutely *thrilled* to discover that they both ran quite well with Ubuntu/Kubuntu! I would *LOVE* to switch them both over, but I came across a couple of barriers, which are real show-stoppers for me...

------------------------------------------------------------------------------------------
PROBLEM 1: KONQUEROR & ESPERANTO WEBSITES
------------------------------------------------------------------------------------------

Kubuntu looks incredible! - and much to my surprise, and despite reports to the contrary in several posts in these forums, it was quite fast, even on my little 333Mhz Indigo. 

However, although I was able to visit all my Esperanto websites without any hassles using Firefox under Ubuntu, visiting the same sites using Konqueror under Kubuntu did give me problems.

Esperanto uses 6 accented letters (c, g, h, j, s with circumflex, and u with breve). To see a bit of Esperanto, go to the Australian Esperanto Association website ([http://www.esperanto.org.au/](http://www.esperanto.org.au/)) and click on the "bonvenu: esperanta ttt-ejo" link under the head banner. Using the Kubuntu Live CD, if I visit that site with Konqueror, all the Esperanto letters appear as 'square boxes' - the sign of a missing character for that font, or of a character that somehow cannot be displayed. 

I tried going into "Configure Konqueror", selecting alternative fonts and re-loading the pages, but regardless of whatever font I choose (FreeSans, Nimbus, etc.) the Esperanto characters never display...

The oddest thing is that this problem does NOT happen if I use the Ubuntu Live CD, and Firefox - the pages all show without a glitch. What is happening? Are the fonts used in the Ubuntu and Kubuntu Live CDs different? - or am I supposed to do something basic in Konqueror, that I'm missing?...

------------------------------------------------------------------------------------------
PROBLEM 2: UNDERSTANDING & USING KEYBOARD LAYOUTS
------------------------------------------------------------------------------------------

I understand that support for Esperanto is not built-in standard on the Live CDs - even though, if I understand correctly, I can add that pretty easily to my installation by selecting a handful of packages under Synaptic/Kynaptic. Support for many other languages - Portuguese included - however, is already right there on the Live CDs. So, I should be able to select an appropriate keyboard layout, and type characters such as "ç" (c cedilla) and "õ" (o + tilde) without too much hassle. However, using neither Ubuntu nor Kubuntu have I been able to type accented characters in *any* program... Here is the problem:

Finding the places - under Gnome and KDE - where I can enable the extra keyboard layouts was fairly easy. Selecting the layouts, and adding them to my list of available layouts was pretty straight-forward, too. However:

Question: In Gnome, I actually get to see a little preview of the selected keyboard layout. In the preview, each key shows up to 4 character on it. How do I type these characters? I suppose one of them is the 'standard', and the others are characters that we reach via modifier keys, but no matter what key combinations I press (command, option, control, shift, etc.) I can never produce these characters!

Question: Does Gnome have a little 'keyboard layout switcher', like the one that appears in the KDE bottom bar of the screen when you have more than 1 layout enabled?

Question: Does Kubuntu have a utility/program equivalent to the "Keyboard Viewer" app in the Mac, enabling us to see what characters are available for which font, when you press which keys on the keyboard? 

Again, it does not matter what key combinations I press in either Ubuntu or Kubuntu, in any program, with any keyboard layout, I *never* seem to be able to produce accented characters...

I'm guessing that I have to go into the 'advanced' section of the keyboard configuration panels, and set some of the options there on, which probably have to do with the activation of these characters by using modifier keys. However, the options are SO VAST, and the jargon SO INTIMIDATING (what is a 'dead key', 'meta key', or a 'third level modifier'?), that I feel a bit overwhelmed, not even knowing where to start...

Please, HELP! I would LOVE to switch my two little iMacs to Ubuntu/Kubuntu, but these international character problems are real show-stoppers for me!

Any and all guidance would be IMMENSELY appreciated!

Many thanks in advance!

---

### Post by ipixel on 2005-05-15
UPDATE:

Got Konqueror to display the international characters. For future reference: go into "Configure Konqueror...", and select "Fonts". In the font configuration panel, you must select not just a 'default' font which has a good international character set (such as "FreeSans"), but select also fonts for ALL OTHER FONT CATEGORIES (ie, select a default font for "Sans", for "Monospaced", etc.). I selected "FreeSans" for Sans, "FreeSerif" for Serif, and "Monospaced" for Monospaced, and it seems to work.

The last problem is that the TITLE BAR of the windows in Konqueror use the font specified in the System Settings - which, by default, is a font in the 'Vera' family, which does not have international characters. You will have to go to the Control Panel, and change your System Fonts there as well - I replaced all of mine with "FreeSans", and it all works fine now!

---

### Post by BROKEN_LADDER on 2005-11-14
[http://ubuntuforums.org/showthread.php?t=90040](http://ubuntuforums.org/showthread.php?t=90040)

that should answer all your problems folks.  i've seen all the bad help, and finally figured it out myself.

---

### Post by octathlon on 2006-04-28
Edited message because I found the answer:

I had posted a message because I still couldn't figure out how to actually type the keys with the US international keyboard layout but I found the answer.  You use the Right-Alt key. So in other words for Spanish characters:

Right-Alt + a,e,i,o,u = á,é,í,ó,ú
" + u = ü
Right-Alt + 1 = ¡
Right-Alt + ? = ¿

Hope this helps someone.

---

