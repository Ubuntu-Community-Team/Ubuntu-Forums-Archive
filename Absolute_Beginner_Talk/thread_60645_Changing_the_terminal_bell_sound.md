---
title: "Changing the terminal bell sound"
date: 2005-08-28
forum: Absolute Beginner Talk
---

### Post by judabuddhist on 2005-08-28
This may be a bit of a silly question, but how can one change the default beeping sound made by a terminal to something else? I just moved into a room with a roommate who also uses linux, and it's become apparent that having the same terminal bell will quickly get confusing. having one be a ping or something would solve the problem

thanks

---

### Post by linuxfanatic1024 on 2005-08-28
What terminal are you using? Linux console, Konsole, the GNOME terminal, or something else? We need to know that first.

---

### Post by aysiu on 2005-08-29
Am I being naive? Isn't it just System > Preferences > Sound > Sound for Events?

---

### Post by judabuddhist on 2005-08-29
[QUOTE=linuxfanatic1024]What terminal are you using? Linux console, Konsole, the GNOME terminal, or something else? We need to know that first.[/QUOTE]

gnome terminal actually. And Sound preferences doesn't have an option to change the sound, just turn it off entirely

---

### Post by philipMac on 2005-10-08
Hey Juda, do you mind me asking did you ever find out how to change the system bell?
Cheers, 
Philip.

---

### Post by linuxfanatic1024 on 2005-11-08
[quote=judabuddhist]gnome terminal actually. And Sound preferences doesn't have an option to change the sound, just turn it off entirely[/quote]

Oh, sorry. I don't use GNOME. :neutral:

---

### Post by rrreima on 2008-03-10
Hey, this discussion is a bit old now, but since this was the first hit on Google with words "changing terminal bell", I felt compelled to add this piece of information here (so you don't have to go through too many search results).

To get a different kind of beep from the pc speaker, just use the command "xset b [volume in % of maximum] [pitch in Hz]". Man xset will tell more, and including it in your login script might be a good idea.

and yes, it works in gterm, at least now in 2008...

cheers,
  Rrrrrreima

---

