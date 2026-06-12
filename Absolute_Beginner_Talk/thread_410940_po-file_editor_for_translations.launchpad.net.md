---
title: "po-file editor for translations.launchpad.net"
date: 2007-04-16
forum: Absolute Beginner Talk
---

### Post by paark.s on 2007-04-16
I've been translating using web-based in launchpad.net for month and decided to use an offline PO editor. I chode Gtranslator and It doesnot work with launchpad.net because it change something inside the file and launch pad won't accept it. The email quote below...

I wrote

> > I've downloaded it from translations.launchpad.net and use
> > Gtranslator to open the file. All I 've done to the file is I
> > translated it and changed font in Gtranslator. Since this is an
> > convenient way to translate the file I dont want to switch to web-base
> > again.
> >    Do you have any suggestion except the one provided in the first email.
replied
> Ok, I have tried this and I can confirm that Gtranslator indeed
removes 'X-Rosetta-Export-Date' field.

The bug is already reported upstream:

  [http://bugzilla.gnome.org/show_bug.cgi?id=392323](http://bugzilla.gnome.org/show_bug.cgi?id=392323)

If you can't wait for the bug to be fixed in Gtranslator, I can
suggest you try some other offline PO editor.

Alternative workaround is to manually re-insert
"X-Rosetta-Export-Date" header before uploading file back to
Launchpad, but that's tricky and it's easy to make a mistake there (so
do it only if you know what you are doing).


_I am here just to ask for an suggestion on which PO-file editor should I use?_Esp.,the one that work well with launchpad rosetta.

thank

---

### Post by ibanezix on 2007-04-16
How about [http://www.poedit.net/](http://www.poedit.net/)

Its binaries are common in many distros, not sure about Ubuntu.

---

### Post by paark.s on 2007-04-17
I got the program from ubuntu repository. Thouht it's the same you've suggested.

thanks.

---

### Post by paark.s on 2007-04-17
I've tried it.This program work fine with Launchpad.net.

thanks again.

---

