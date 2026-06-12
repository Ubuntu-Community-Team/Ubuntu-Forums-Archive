---
title: "Special characters"
date: 2008-01-14
forum: Absolute Beginner Talk
---

### Post by darsu on 2008-01-14
I started looking into figuring out how to type macroned vowels. I wanted to find the configuration file where key combinations for special characters are defined, to see what's in it. My locale being en_US, I presume this file is /usr/share/X11/locale/en_US.UTF-8/Compose; I have it open in one window while I try combinations defined there (any combos, not only the ones yielding vowels with macrons) in another window; *None of the combinations work properly*. 

Take for instance the very first Multi_key combo defined in the Compose file.  <Multi_key> <plus> <plus> should produce a #. As far as I know, Multi_key is defined as altGr-shift. I know from experience that altGr-shift-+ gives me a ¿, so this Compose combination gives me ¿¿, not #. 

As another example, the combination for A-macron is given as <Multi_key> <underscore> <A>. This produces ¯A, as the macron doesn't operate as a dead key.

In short, the definitions in the Compose file don't correspond to what my keyboard does. Am I looking at the wrong file, or is something else wrong?

The user Kalle314 seems to have had a very similar problem [here](http://ubuntuforums.org/showthread.php?p=1647960#post1647960), with no reply.

---

### Post by brotulix on 2008-01-17
Have you tried AltGr without using Shift?

AltGr-dash-a gives me an underlined a: ª

AltGr-+ gives me a plus sign above a minus sign: ±

This is on a keyboard with Norwegian layout - I haven't tried with US layout.

Don't know if this is what you meant...?

---

### Post by Yeti can't ski on 2008-02-29
**This post could be related to an Ubuntu bug filed at**: [http://ubuntuforums.org/showthread.php?t=209115](http://ubuntuforums.org/showthread.php?t=209115) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				This problem was resolved by the user stdragon. I am attaching the thread below. If you search "ComposeKey" on Ubuntu Documentation you will also find the answer. 

First thing to do is to add the following line to the file /etc/environment with a text editor:

export GTK_IM_MODULE=xim

(in my case, I used Gedit to edit the file so it was: sudo gedit file/etc/environment)

Then you must make a copy of the file /usr/share/X11/locale/en_US.UTF-8 and save it on your home folder with the name: .XCompose (remember that it will be a hidden file).

Finally, with a text editor you can edit .XCompose to have the key combinations you want. There you will find tons of previously established key combinations. If existing combinations do not suit you, you can edit them, following the syntax established in the other shortcuts.

<Multi_Key> means the "compose key" which as default is the combination of (Shift+AltGr) but you can change it going to System>Preferences>Keyboard>Layout options>Compose Key positions. 

After that, restart the computer and it should work.

I am an absolute beginner so I needed  some time to figure all aspects out. But in the end I did it. Let me now if you need a more detailed answer. I had to set up an Italian keyboard to use German and Portuguese special characters. It was a mess! Good luck.

---

### Post by gaiterin on 2008-05-10
Hi.
Maybe you must modify this:
System/Preferences/Keyboard -> Put in your language the layout.

or

System/preferences/SCIM Method Input -> Put in your language ;)

Regards.

---

