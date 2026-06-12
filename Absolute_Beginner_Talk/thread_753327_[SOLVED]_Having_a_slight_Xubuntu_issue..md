---
title: "[SOLVED] Having a slight Xubuntu issue."
date: 2008-04-12
forum: Absolute Beginner Talk
---

### Post by Famicommander on 2008-04-12
I just installed Xubuntu, and I'm having some problems enabling my adblocking for Opera.

I know I'm supposed to edit the URLfilter.ini file to look like this:
[http://www.fanboy.co.nz/adblock/opera/urlfilter.ini](http://www.fanboy.co.nz/adblock/opera/urlfilter.ini)

But I don't know how to access the urlfilter.ini from Xubuntu. Any help would be much appreciated.

---

### Post by TheOctagon on 2008-04-12
I'm not a Xubuntu user (I use the standard Ubuntu), but I think I've used common-denominator commands in what follows, so this should work for you.
[LIST=1]
[*]From the Xubuntu menu, select Applications > Accessories > Terminal.
[*]Type "sudo updatedb" <enter>, then enter your Xubuntu password to authorise this command as super-user. This updates the list of files and directories that will be used in the following command. It might take a while.
[*]Type "locate -i urlfilter.ini" <enter>. This should give you the full path to the file.
[*]Type "nano" followed by a space, then the full path and file name retrieved in the previous step, then <enter>. This should open the file in the nano text editor.
[*]Make your required changes.
[*]Press Control-X.
[*]Press "Y" then <enter>, then <enter> again to confirm the changes.
[*]Type "exit" <enter> to exit the terminal console window.
[/LIST]

Does that fix it?

---

### Post by kerry_s on 2008-04-12
open thunar
press ctrl+h to see hidden files
click on .opera
locate URLfilter.ini
click on it, it will open in mousepad, make your changes and save.

it may not exist yet, to activate it simply block something in opera using the right click menu on a web page, then just over write it with yours.

---

### Post by vinceUUUU on 2008-04-12
Hello

sometimes in these browsers.....you have to edit the config file

in the address bar you can type.....about:config

this shows all the browsers settings that are editable..

hope this may help somehow

Vince.

---

### Post by Famicommander on 2008-04-12
> **kerry_s said:**
> open thunar
press ctrl+h to see hidden files
click on .opera
locate URLfilter.ini
click on it, it will open in mousepad, make your changes and save.

it may not exist yet, to activate it simply block something in opera using the right click menu on a web page, then just over write it with yours.

That did the trick. Thanks.

---

### Post by kerry_s on 2008-04-12
> **vinceUUUU said:**
> Hello

sometimes in these browsers.....you have to edit the config file

in the address bar you can type.....about:config

this shows all the browsers settings that are editable..

hope this may help somehow

Vince.

i give you a big thanks, cause you made me laugh. :lolflag:

---

