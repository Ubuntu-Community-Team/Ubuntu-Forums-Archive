---
title: "Panels and cups using the same scheme?"
date: 2007-05-15
forum: Absolute Beginner Talk
---

### Post by Limitlesschannels on 2007-05-15
Hey everyone.  I have been using Gnome-Color-Chooser for a long time now and I have been quite happy with my lovely black panels, but I recently noticed that upon opening gnome-cups-manager the interface seems to be the very same black with my panel font.  It isn't too big of a deal since I can still run it fine (aside from the dropdown menus appearing black and making them near invisible) but I was just curious why it is using the same scheme, is cups programmed to borrow system characteristics or something?  I really have no idea how cups runs or how the panels run, but it just seemed odd since none of my other administrative menus/programs seem to behave this way.

---

### Post by n8bounds on 2007-05-15
Yeah, you can tell when you are using a package that alters Gnome that didn't ship with the distro's standard Gnome desktop, can't you.  Why don't you just try finding a GTK theme from gnome-look.org that suits your needs?  They are sometimes very well integrated and avoid problems like that.

---

### Post by Limitlesschannels on 2007-05-17
Yeah, I haven't really found anything that fits my needs, plus it is so tiring to just scroll through pages and pages and pages of the stuff; i got sick of that back in my WinXP days looking for StyleXP themes.

---

### Post by n8bounds on 2007-05-17
right on dude, thats whats so great about linux:  4,129 different ways to attack the same problem

---

### Post by JackTheDipper on 2007-05-20
@Limitlesschannels.
Are you using gnome-color-chooser 0.2.x ? It shouldn't have this problem anymore. ;-)

@n8bounds:
many color bugs of GNOME became reproducable via this app and so they could be fixed. ;-)

best regards,
Jack

---

### Post by Limitlesschannels on 2007-05-22
Jack:  heheh, I am not even that modern.  0.1.3 all the way!!  Well, guess it is time to upgrade.. I will report back.

and, yeah, I love being able to do the same thing a thousand different ways.  high-five, tux

EDIT: Alright, I installed the newest version and it does not seem to effect cups in the same way.  But, it really doesn't seem to effect the menus at all.  I can't figure out how to just change the color of the dropdown menus through the panel.  It was so easy in the last one.  Is that the "Start Menu:  Not Yet Possible With Gnome"  box under the panel tab?  If so, then now I miss the old version...

---

### Post by JackTheDipper on 2007-05-23
Are you sure that this was possible with 0.1.3 ? Afaik there is currently no way to colorize the start menu without affecting other menues (outside the panel), although I'm not quite sure.

---

### Post by Limitlesschannels on 2007-05-23
Well, it did colorize other menus, like cups, that's why i wrote this thread.  But it still had the option to colorize the start menu, which doesn't even seem to be there in this version (0.2.1)

---

### Post by JackTheDipper on 2007-05-24
hmmm. I compared the database of 0.1.3 with the one of 0.2.1 and the only difference in the panel section is that widgets with "print" in its name are no longer automatically affected.
So where did you set the start menu colors, in the panel section? (The main colors affect also menu colors)

Would adding an option to colorize _all_ gnome menues (also in applications) be enough for you as the start menu cannot be changed alone?

Jack ;-)

---

### Post by Limitlesschannels on 2007-05-26
I honestly don't remember, you are probably right being a maintainer and all, heh, but i just remember setting the color of the drop down applications/places/system menus and not being able to do anything as I forgot to change the font color to oppose the black background.  The colorize_all_gnome menus wasn't really what I was going for, but it was probably a root of my unfamiliarity with the options of the newer version.  Instead, I went back, albeit somewhat indirectly, to your first response and switched over to the Ubuntu Studios theme.  It has just about everything I want and I am liking it quite a bit.  Thanks for all the troubleshooting, though; even though there really seems to be nothing wrong, it works has it should.

---

