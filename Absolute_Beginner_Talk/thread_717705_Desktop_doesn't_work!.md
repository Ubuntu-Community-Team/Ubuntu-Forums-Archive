---
title: "Desktop doesn't work!"
date: 2008-03-07
forum: Absolute Beginner Talk
---

### Post by Fixman on 2008-03-07
When I logged in today, there were no icons on desktop, and I could not click it to make a "selection square". Help!

---

### Post by {BzF}~JOKesTER on 2008-03-07
If Your Using Gnome:

IMPORTANT: The Use Of The rm -rf Command Is Used Here Because Of An Important Reason!!!!

Ok Assuming Your Using Gnome Do This:

At The Login Screen In Ubuntu:

Press:

Ctrl And Alt And F1    -- At The Same Moment

Now It Will Ask You To Login - Do So And Type This Command:

rm -rf .gnome .gnome2 .gconf .gconfd .metacity

{Note You Might Have To Prefix This With "Sudo" To Work}

Now Type:

restart

And When You Login Again Everything Should Be Back To Normal.

Hope This Helps!!:):)

---

### Post by adi_das on 2008-03-07
DO u Dual boot?

---

### Post by Het Irv on 2008-03-07
Have you tried restarting the X-Server (CTRL-ALT-Backspace), or a hard reboot?  Everynow and then on my desktop X-Server will do some funky stuff, I think it has to do with the graphics drivers I have not being quite right.

Jokesters command will clear out your settings and put everything back to the defaults.  He probably should have said that.  Just letting you know.

---

### Post by Fixman on 2008-03-07
I doubt that would work, I think I have show_desktop as false, however if I run

```

gconftool-2 --type bool --set /apps/nautilus/preferences/show_desktop true

```

Nothing happens.

---

### Post by {BzF}~JOKesTER on 2008-03-07
Yes Sorry - I Should Have Mentioned That It Will Reset All Your Desktop Effects - Themes And All That To Default - However That Should Fix The Problem>..

---

### Post by Fixman on 2008-03-07
> **adi_das said:**
> DO u Dual boot?

Yes I do.

---

### Post by {BzF}~JOKesTER on 2008-03-07
Good God,

Dude If You'd Just Run That Command It Will Fix Your Problem.

What Seems To Be The Delay??

:):confused::):confused:

---

### Post by Fixman on 2008-03-07
> **{BzF}~JOKesTER said:**
> Good God,

Dude If You'd Just Run That Command It Will Fix Your Problem.

What Seems To Be The Delay??

:):confused::):confused:

Isn't there a good way to do it that doesn't nuke my configuration files, having me to reconfigure everything?

---

### Post by smurphy_it on 2008-03-07
One or more of your conifguration files could be corrupt causing the problem.

It is a bit of a hassle to reconfigure, but at least you know you starting out at a known good configuration.

---

### Post by Fixman on 2008-03-07
> **{BzF}~JOKesTER said:**
> 
rm -rf .gnome .gnome2 .gconf .gconfd .metacity


Dude, I just had to modify ~/.gconf/apps/nautilus/preferences and I could do it without nuking it, I was lucky I didn't follow your advice, since I would still be reconfiguring. So, seriously, **if you don't know about something then don't post**. Please.

---

### Post by {BzF}~JOKesTER on 2008-03-07
Not Really - This Will Just Reset The Desktop Theme's And Stuff -Easily Re-installed

---

### Post by Fixman on 2008-03-07
> **{BzF}~JOKesTER said:**
> Not Really - This Will Just Reset The Desktop Theme's And Stuff -Easily Re-installed

Haven't I just told you that I worked it out without reseting the themes?

---

