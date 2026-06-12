---
title: "GNOME theme idea question"
date: 2007-10-08
forum: Art &amp; Design
---

### Post by fredbird67 on 2007-10-08
I have an idea in mind for a GNOME theme for Christmas I'd like to share with the GNOME crows on GNOME-Look.org.  However, I just downloaded a theme that's kinda similar in style but not color that I'd like to base it on, and I was just poring over the code for it, and I can't make heads nor tails of this one.  I think I know what some of them are, but on the others, can anyone tell me in plain English what normal, prelight, active, selected, and insensitive refer to?

FG, BG, and text are all self-explanatory, but what does "base" refer to?  I apologize if this sounds like a dumb question, but to be honest, I'm a KDE fan (running PCLinuxOS -- so sue me!), yet I was curious and wanted to try my hand at creating a GNOME theme.

Thanx in advance,
Fred

---

### Post by VictorR on 2007-10-11
NORMAL is the usual state of the widget.
PRELIGHT is the the mouse is above the widget.
ACTIVE is when one clicks on the widget
SELECTED is when it is selected, if it can be selected (not applicable for buttons, for example).
INSENSITIVE means disabled in Windows terms, one cannot interact with this widget at all.

Some widget unfortunately have different meaning for the above states. The TAB (GtkNotebook) uses ACTIVE as for not-active tab, and NORMAL for selected or active tab.

base is the background for text, for example in the GtkEntry (input box).

You  can try this trick:
in the gtkrc file select a style, which is applied to a certain widget, and set all the states to different contrast colours, like
style "theme-notebook" = "theme-default"
{
	bg[ACTIVE]   = "#FF0000" #red colour
       bg[NORMAL] = "#FFFF00" #yellow colour      
	bg[INSENSITIVE] = "#333333" #very dark gray
and so on to FG, text and base
}
and with The Widget Factory see how it looks like and what is actually used in that widget.

---

