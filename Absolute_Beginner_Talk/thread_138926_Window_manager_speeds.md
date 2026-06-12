---
title: "Window manager speeds"
date: 2006-03-02
forum: Absolute Beginner Talk
---

### Post by Super King on 2006-03-02
I've been reading up on the various "light-weight" Window Managers like Fluxbox and Blackbox, and how they can drastically decrease boot-up time, and overall performance is "snappier."  So, is this faster performance referring mainly to switching between tasks/windows, or also things like application start time? For example, would, say, Firefox do a cold start faster in Fluxbox then in Gnome w/ Nautilus? It doesn't seem like it should but I really am not sure. I ask these questions because I'm wondering if there would be a notable difference running Fluxbox over Nautilus on older, slower hardware.

Thanks.

---

### Post by bluevoodoo1 on 2006-03-02
I use Blackbox, and I think it's great. There isn't a change on system bootup, but after logging in to gdm, Blackbox starts up in under 1 second, where GNOME takes about 10-15(??) seconds. Other things like gnome-terminal take forever to start (in GNOME or Blackbox) but terminals like Eterm, xterm or aterm startup very fast. While browsing files with Nautilus, opening it takes about the same amount of time in Blackbox, which is maybe 3 seconds. Firefox seems about the same, might be a hair quicker on BB. With no actual data to back things up who knows the exact calculations?! But overall things feel a bit quicker and less cluttered in BB, maybe it's just in my head!

---

### Post by mrgnash on 2006-03-02
Ditto for Fluxbox. :KS

---

### Post by moberry on 2006-03-02
Speaking of flux box. I had an issue with that I was wondering if anyone had solved, or had. Under fluxbox (with gnome-settings-daemon running) OO.org is FUGLY, i mean bad... bad. Seems to be a theming issue. Any ideas?

-jordan

---

### Post by bluevoodoo1 on 2006-03-02
[QUOTE=moberry]Under fluxbox (with gnome-settings-daemon running) OO.org is FUGLY, i mean bad... bad. Seems to be a theming issue.[/QUOTE]

Actually, I have that exact problem with Blackbox and OO.org too.

---

### Post by moberry on 2006-03-02
> I use Blackbox, and I think it's great.

And you still think its great :-).

Kidding, but asthetic stuff like that pisses me off, specially when its beautiful i gnome.

-jordan

---

### Post by bluevoodoo1 on 2006-03-02
[QUOTE=moberry]And you still think its great :-).

Kidding, but asthetic stuff like that pisses me off, specially when its beautiful i gnome.[/QUOTE]

HAHA! Indeed, but I'll take Blackbox's performance over GNOME :)

---

### Post by moberry on 2006-03-02
It is quick. As soon as I fix this issue I will go back to using it. I think i have about half the keys mapped to run programs :)

---

### Post by johnraff on 2006-03-02
I'm in the same sort of trying out different window managers stage (I've got a lo-spec machine: 128MB RAM, 450MHz P3 CPU).

On my box I compared the time for Firefox (1.07) to start up and found some *big* differences:
Ubuntu w. 386 kernel & full Gnome:40sec.
Ubuntu w. 686 kernel    "     "      :30sec.
Ubuntu      "          Gnome, & Openbox as window manager:22sec.
Xubuntu-desktop (686) (xfce w.m.) :20sec.
Ub. (686? - I forget) w Fluxbox alone:12sec.
Ub. (686?) w IceWM alone:8sec.
Ub. (686?) w. Openbox alone:7sec.

I like the way Gnome organises everything for me, but it *is* slow:  right now I'm thinking of using Openbox (or possibly IceWM) by itself, and just adding stuff as I need it.

I've read that the new Dapper release of Ubuntu will be faster, so we could just wait for that instead...

---

### Post by IYY on 2006-03-03
If it's an old computer with little RAM, I think applications may start and run faster (the window manager would take far less memory, and the applications would have more left over to work with). 

Just a theory, though. I don't really know much about this issue.

---

### Post by akiro.yamamoto on 2006-03-03
Has anyone done a comparision of XFCE or E16/E17 and Gnome/KDE ?
I think that would be fairly interresting.

---

### Post by bluevoodoo1 on 2006-03-03
[QUOTE=akiro.yamamoto]Has anyone done a comparision of XFCE or E16/E17 and Gnome/KDE ?
I think that would be fairly interresting.[/QUOTE]

For me, I think e16 is fastest, then xfce then GNOME/KDE.

---

### Post by Super King on 2006-03-03
Thanks everyone for the input, especially Johnraff for that timing test with FF. I think I'll be trying out Fluxbox or Openbox with the next old Pentium machine I get my hands on.

---

### Post by Klaidas on 2006-03-03
What do you guys think about IceWM?

---

### Post by delaguer on 2006-03-04
my laptop only has 128mb ram and P3 597Mhz, I used to use Gnome and I like it but it was wayyyyyy slow, OpenOffice was so damn slow that it was almost unusable.....

now I'm running Ubuntu Hoary with IceWM and everything's much faster and snappier... one problem though: I couldn't find my ext usb HD... it used to be automounted on /media/hdname :-k

---

