---
title: "Deleted font now - (gedit:1163): Pango-WARNING **: shape engine failure, expect ugly"
date: 2007-07-22
forum: Absolute Beginner Talk
---

### Post by captlogic on 2007-07-22
Ok, I've got feisty and everything was just peachy, except my fixed width font, monospace, looked terrible.  I have a lcd panel and the monospace fixed width font didn't look black, but fuzzy red, green & blue.  I've got the font rendering set to sub-pixel smooth.  I had installed some fonts after install so I figured maybe I goofed something.
I went to the fonts panel and changed the fixed width font from Monospace to another fixed width font.  Problem solved in 'Terminal' but not in other programs.  I THINK firefox was one that still showed the problem when displaying text that was supposed to use fixed width (i.e. code snippets).  I thought maybe some apps picked the font to use, but not based on the font preferences dialog.  So I just deleted the offending font.:confused:  What have I done?

Most things still work, Terminal looks good.  The big problem is with gedit.   'sudo gedit /etc/exports' gives the following error

(gedit:1163): Pango-WARNING **: shape engine failure, expect ugly output. the offending font is 'Monospace Not-Rotated 9.9990234375'

(gedit:1163): Pango-WARNING **: pango_font_get_glyph_extents called with null font argument, expect ugly output

Then I get squares as characters in gedit.

Things I now know.
1.  Do not just delete the font, there must be a removal procedure.  WIP
2.  RTFM, first.

I've searched around about the Pango error, but don't seem to find anything similar to my situation.  Can someone point me in the right direction.  I want to fix this error without replacing the monospace font.  (It's not in Recycle anymore nor am I sure it came with my outside font collection or default with ubuntu.)

Thanks in advance.
Painfully Noobing
Patrick

---

### Post by testube_babies on 2007-07-22
Well, this won't solve your real problem, but it will address some of your other issues.

1)  Firefox uses its own fonts.:mad: I've seen ways to fix firefox fonts, but I can't seem to find them now.
2)  You might want to try [this]("http://ubuntuforums.org/showthread.php?t=343670) for improved subpixel font rendering
3)  When you open a graphical application as root, use gksudo instead of sudo:  [http://psychocats.net/ubuntu/graphicalsudo](http://psychocats.net/ubuntu/graphicalsudo)

---

### Post by stmiller on 2007-07-22
Try this:

> sudo dpkg-reconfigure fontconfig-config
sudo dpkg-reconfigure fontconfig

And choose: Native, Always, No bitmapped fonts.

May have to restart X. (Control+Alt+Backspace)

---

### Post by captlogic on 2007-07-22
> **testube_babies said:**
> Well, this won't solve your real problem, but it will address some of your other issues.

1)  Firefox uses its own fonts.:mad: I've seen ways to fix firefox fonts, but I can't seem to find them now. That explains much > **testube_babies said:**
> 
2)  You might want to try [this]("http://ubuntuforums.org/showthread.php?t=343670) for improved subpixel font rendering
3)  When you open a graphical application as root, use gksudo instead of sudo:  [http://psychocats.net/ubuntu/graphicalsudo](http://psychocats.net/ubuntu/graphicalsudo) Thanks for the tip, I never knew.

Frank Rocks :guitar:

---

### Post by captlogic on 2007-07-22
That seems to have done the trick.  Thanks so much.

---

