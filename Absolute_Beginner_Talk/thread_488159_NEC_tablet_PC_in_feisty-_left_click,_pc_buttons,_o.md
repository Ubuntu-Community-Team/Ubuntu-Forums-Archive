---
title: "NEC tablet PC in feisty- left click, pc buttons, on-screen keyboard problems"
date: 2007-06-29
forum: Absolute Beginner Talk
---

### Post by AbsolutMayhem on 2007-06-29
Extreme newbie here -- never ran Linux before this week. Did some DOS in the old days (15 years ago!). I saw posts under hardware and laptops re: tablets, but they were WAY too technical for me. If anyone can help me, I need explicit step-by-step instructions, please.

I have a NEC Versalite tablet PC; running Feisty. It's a slate tablet and has no mouse or keyboard attached. The pen input device works okay for right click functions since I upgraded to Feisty. I upgraded stepwise like I was supposed to from Dapper . My issues, in order of importance to me:

The pen's left-click function doesn't work. In Windows XP, it worked by pressing the pen on the tablet for a few seconds, or by using a button on the pen itself. I usually did the pen pressing thing for left click-and it's driving me nuts not to have it. I have to plug in a USB mouse to left click.

Screen orientation and tablet pc function buttons don't work. The up and down  and enter buttons work okay. Most important to me is the screen orientation.

Even though I've enabled the on-screen keyboard to appear at login, it doesn't show. I've enabled assistive technology. So I have to plug a USB keyboard into the machine to login. I'll probably use automatic login to get by this problem in the meantime, but I'd like to have a password login for the long run.

One more thing that's important. I've added apps (Wine, for example) using synaptic or add/remove programs, and some of them don't show up under applications, or if I do a search, even after a reboot.   

Thanks. I really want to get this up and working, because I hate using Microsoft products.:p

---

### Post by bcw on 2007-07-08
> **AbsolutMayhem said:**
> Extreme newbie here -- never ran Linux before this week. Did some DOS in the old days (15 years ago!). I saw posts under hardware and laptops re: tablets, but they were WAY too technical for me.

In one week you've gone from Dapper to Feisty.  You might want to re-think that self-evaluation - you may have to stretch to get  what you want anyway...

> I have a NEC Versalite tablet PC; running Feisty. It's a slate tablet and has no mouse or keyboard attached. The pen input device works okay for right click functions since I upgraded to Feisty. I upgraded stepwise like I was supposed to from Dapper . My issues, in order of importance to me:

As the stylus was working, can you say what sort it is?  Are you using the Wacom driver, the fpit, or ?

> The pen's left-click function doesn't work.

I don't know for certain what you mean by this.  Please answer these questions:
[LIST=1]
[*]Does the mouse cursor follow the stylus around when you move it?  Is it supposed to?  (My wacom digitiser doesn't require contact for tracking, but my touchscreens don't register position until I tap).
[*]Is this stylus designed to enter a left-mouse-button click when you push against the screen with the tip?
[*]Is there another way to enter a left-mouse-button click with this stylus, and if so, what is it?
[*]What other buttons does it have, and what are they supposed to do?
[*]Is this stylus supposed to have an eraser?
[/LIST]

>  In Windows XP, it worked by pressing the pen on the tablet for a few seconds, or by using a button on the pen itself. I usually did the pen pressing thing for left click-and it's driving me nuts not to have it. I have to plug in a USB mouse to left click.

The reason I'm asking is I don't have one of these (I have Fujitsu slates), and there is no delay between pressing on the screen and getting a left-mouse-click event on my slates, so I'm checking what you're expecting here.  It may seem like I'm asking what you've already written, but I am not clear after reading your description.

> Screen orientation and tablet pc function buttons don't work. The up and down  and enter buttons work okay. Most important to me is the screen orientation.

First, let's establish what sort of digitiser (the driver question above) you have.  As well, what is the display chip your system uses?  You could append the output of this command to your reply to help answer that:
```
lspci
```

> Even though I've enabled the on-screen keyboard to appear at login, it doesn't show.

Umm, which one?  I know of four.

For that matter, which flavor of Ubuntu are you using?   'Ubuntu' comes with a Gnome desktop, 'Kubuntu' defaults to the KDE desktop, etc.  It matters.

>  I've enabled assistive technology. So I have to plug a USB keyboard into the machine to login. I'll probably use automatic login to get by this problem in the meantime, but I'd like to have a password login for the long run.

I log in with an XVkbd on-screen keyboard.  I've never gotten GOK to work.  There are a number of manual steps required to have the GOK keyboard show at login, but even after doing them, it doesn't show, so I gave up on it.  In my other posts, I have detailed how to get XVkbd at login with KDM, and a reply speaks to using it with GDM.  Use the search, Luke...

> One more thing that's important. I've added apps (Wine, for example) using synaptic or add/remove programs, and some of them don't show up under applications, or if I do a search, even after a reboot.

WINE isn't an application to be found in the menu, although there may be several applications that are associated with it.  WINE is a set of libraries that allow running MS Windows programs without MS Windows.  You'll need to read a bit about that, as working with it depends on what approach you take.  I'm using CrossOver Office, and don't have any recommendations about other approaches.

As for the other items, depends on what they are.  Some also aren't in the menus, some should be, but aren't picked up by 'competing' desktops (KDE vs. Gnome vs. XFCE, etc.).  So you'll have to be more specific in order to get any help.  But you might install the 'menu' package which attempts to install all items in the menu that have menu entries.  Again, WINE and some others aren't desktop programs, but 'menu' is fairly desktop agnostic, so might help.

> Thanks. I really want to get this up and working, because I hate using Microsoft products.:p

I don't mind their products, but I don't like helping the company - they are convicted criminals.  Better not to give them any more money.

Cheers,
Bret

---

