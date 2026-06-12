---
title: "Using autotrace package Ubuntu Studio"
date: 2013-07-09
forum: Art &amp; Design
---

### Post by Derelinquat fenestras on 2013-07-09
Hello all,

Casting a net here...

I found a package called autotrace in synaptic, which is supposed to convert bitmaps to vector graphics...

In the description it states that the program was originally designed to be a GIMP plugin, but is now stand alone.
I can not find it on my list of programs and [alt]+F2 --> autotrace also does nothing.
I also looked through plugins of all of my graphic manipulation programs (i.e. GIMP, Inkscape, et al.) and could not find it there either.

Does anyone know how to use it, and if so is it useful?  The concept is appealing to me, but I have not been able to test it.

Thanks

---

### Post by Hylas de Niall on 2013-07-09
It seems to me that it is a command-line only app:
     [http://packages.ubuntu.com/lucid/autotrace](http://packages.ubuntu.com/lucid/autotrace)
     [http://manpages.ubuntu.com/manpages/dapper/man1/autotrace.1.html](http://manpages.ubuntu.com/manpages/dapper/man1/autotrace.1.html)

If you prefer GUI auto-tracing why not use the trace feature in inkscape?

HTH

---

### Post by Derelinquat fenestras on 2013-07-09
Thank you for the suggestion!

I'm pretty new to the Vector graphics design medium...  How would I go about tracing with Inkscape...

I feel like all of my GIMP/PS experience is kind of handicapping me in Inkscape... :)

---

### Post by Hylas de Niall on 2013-07-09
Inkscape tracing:

First 'import' a bitmap image into inkscape,
select it,
then, from the 'path' menu select 'trace bitmap'.
That will bring up a dialog window with a preview pane where you can trace the bitmap image in varying and confugurable ways.
when you click 'update' in this window it will show a preview of the trace you are going to do (you can 'update' as often as you like until you get the result you want).
When you're happy with the preview, click 'okay'.
Depending on the levels of detail you have set you might have to wait a minute or so until the trace completes.
When done, the vector trace image is placed over the bitmap on the 'page'.

HTH

:)

---

