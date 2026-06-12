---
title: "Window Managers"
date: 2005-06-28
forum: Absolute Beginner Talk
---

### Post by AntiDragon on 2005-06-28
Hello there!

I've looked high and low but can't figure this out:

Is there a way to replace Gnome's window manager with Enlightenment using a GDM session? So that the default session is still Gnome and whatever the default WM is but that you can select Gnome with E instead when you log on.

I've set up a .desktop file in the xsessions folder for Enlightenment. But it just loads E and not Gnome. I don't want to permanently change Gnome's default wm. Can anyone help me?

---

### Post by tread on 2005-06-28
You can't run gnome-session with enlightenment instead of metacity, enlightenment isn't wm-compliant. What you could though, is run enlightenment and then start gnome-settings-daemon and gnome-panel .. 

You'll have to find out how to add startup programs to enlightenment though .. I have done thing in e17 but I have no idea about e16.

---

### Post by AntiDragon on 2005-06-28
[QUOTE=tread]You can't run gnome-session with enlightenment instead of metacity, enlightenment isn't wm-compliant. [/QUOTE]

Really? My bad - I assumed it was as I'd read about it being "Gnome Compliant". I guess they're not the same thing?  :? 

Still, I know Gnome will run on top of e16 as others have managed it. But I'm interested in how you worked it with e17 though - to be honest, I'm more interested in e17 than e16 but I figured that sticking with e16 was the safer option.

Of course, now that someone's shown me they way I'm tempted to dive right in.... :wink: 

Thanks!

---

### Post by tread on 2005-06-28
I just have gnome-session running in e17, not the panel. Dont need it with engage already there. I think there is a HOWTO somewhere on this forum for e17 .. good luck with it!

Good point about the gnome-compliant e though .. I dunno what they mean by that! I do know if I try to run skippy I get a message saying current wm isn;t compliant.

---

### Post by AntiDragon on 2005-06-28
OK. Found [an E17 guide](http://get-e.org/User_Guide/English/index.html) - nicely detailed. There's also links to a pre-compiled Debian package - I guess I have to decide if I'm ready to start fiddling with MAKE/CVS and such like yet  :-P 

Do you need to have gnome-session running on top to use the various gnome apps (gedit etc.) or will they run anway? They just need the GTK don't they?

---

### Post by tread on 2005-06-28
gnome-session is what keeps your gtk apps looking pretty, it manages the themes really. So yes, you don;t need it to run gtk apps, but you need it if you want to keep them skinned. And the default gtk theme (not Human) is ugly :)

---

### Post by AntiDragon on 2005-06-28
Thanks for all this!

Two last questions (mainly 'cos I'm too impatient to wait and find out for myself):

1.  When you start gnome-session does it load up the Gnome menu bars at the top and bottom of the screen or is that a function of metacity?

2.  (A bit of a brainwave maybe?) When you create .desktop files for new GDM managed sessions, there's an EXEC entry that runs the wm. Could I point that to a custom shell script that calls Enlightenment first and then straightaway runs Gnome-session?  
(That would basically fulfil my original desire - I don't want to fiddle with .xinit type files as I'm still too new to this.)

---

### Post by tread on 2005-06-28
1. No, it just manages the gnome theme in e17. I imagine it does more, but it doesnt start the panel (possibly because of compliance issues?)

2. I dunno, maybe. Or better yet, create a script like this:
```

exec enlightenment && exec gnome-settings-daemon && exec gnome-panel

```
and stick it in /usr/local/bin, then modify the xsession file so it runs this. That might work :)

---

### Post by AntiDragon on 2005-06-28
Ahh...

> [FONT=Courier New]exec enlightenment && exec gnome-settings-daemon && exec gnome-panel[/FONT] 

...perrrrrrfect!

That's what I was thinking off - my version would've been a lot messier though. I'd forgotten about the whole && thing ever since I found out that Windows decided to randomly ignore it......Grrr... :-x 

Again, massive thanks - I'm well on my way to being Linux literate (I hope!)  :smile:

---

