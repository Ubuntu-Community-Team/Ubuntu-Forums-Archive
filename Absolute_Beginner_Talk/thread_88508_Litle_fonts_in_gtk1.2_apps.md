---
title: "Litle fonts in gtk1.2 apps"
date: 2005-11-10
forum: Absolute Beginner Talk
---

### Post by Darksidex on 2005-11-10
Hello,

I've installed ubuntu 5.10 a few days ago, and when I want to use any gtk1.2 application, I'm not able to read anything, the fonts are very little.

I've searched in the forum for some answers, and I've found them, but without success.

My .gtkrc file:
style "user-font"
{
  font="-bitstream-bitstream vera
serif-medium-r-normal-*-*-100-*-*-p-*-iso8859-15"
}


.gtkrc.mine:
style "user-font"
{
  font="-bitstream-bitstream vera
serif-medium-r-normal-*-*-100-*-*-p-*-iso8859-15"
}

.gtkrc-1.2-gnome2:
# Autowritten by gnome-settings-daemon. Do not edit

include "/home/darksidex/.gtkrc.mine"

the attached image is an example of how I see mplayer.

---

### Post by Who on 2005-11-10
You may need to install a GTK1.2 engine (usually just called a gtk engine). They are available from synaptic, and for me, once I had installed them this problem cleared up. I know there is one for Industrial, but I don't know about much else, sorry. (Use Synaptic to search for files with gtk in the name. The file will be something like gtk-engines)

hth

Who

---

### Post by Darksidex on 2005-11-12
Thank you for your answer, but unfourtunally it havent solved my problem. I installed gtk-engine-industrial, but the fonts continue being unreadable.

---

### Post by Juippisi on 2005-11-12
My file has this:
```
style "gtk-default-iso-8859-15" {
       fontset = "-*-helvetica-bold-r-*-*-11-*-*-*-*-*-iso8859-15,\
                  -*-helvetica-bold-r-*-*-11-*-*-*-*-*-iso8859-15,\
                  -*-helvetica-bold-r-*-*-11-*-*-*-*-*-iso8859-15,\
                  -*-helvetica-bold-r-*-*-11-*-*-*-*-*-iso8859-15"
}
class "GtkWidget" style "gtk-default-iso-8859-15"
```

Take a exemplar from that. I suggest you trying that only, because GTK1-apps supports Helvetica. And there's even font size defined.

You can use "xfontsel" to generate those font-lines matching your locales, font sizes and so on.

---

### Post by Darksidex on 2005-11-12
Thank you :) It works perfect.
But now I'm getting this:
```
The font "-*-helvetica-bold-r-*-*-10-*-*-*-*-*-iso8859-15,
                  -*-helvetica-bold-r-*-*-10-*-*-*-*-*-iso8859-15,
                  -*-helvetica-bold-r-*-*-10-*-*-*-*-*-iso8859-15,
                  -*-helvetica-bold-r-*-*-10-*-*-*-*-*-iso8859-15" does not support all the required character sets for the current locale "LC_CTYPE=es_ES.ISO-8859-15@euro;LC_NUMERIC=C;LC_TIME=es_ES.ISO-8859-15@euro;LC_COLLATE=es_ES.ISO-8859-15@euro;LC_MONETARY=es_ES.ISO-8859-15@euro;LC_MESSAGES=es_ES.ISO-8859-15@euro;LC_PAPER=es_ES.ISO-8859-15@euro;LC_NAME=es_ES.ISO-8859-15@euro;LC_ADDRESS=es_ES.ISO-8859-15@euro;LC_TELEPHONE=es_ES.ISO-8859-15@euro;LC_MEASUREMENT=es_ES.ISO-8859-15@euro;LC_IDENTIFICATION=es_ES.ISO-8859-15@euro"
  (Missing character set "ISO8859-15")
  (Missing character set "ISO8859-15")

```

---

