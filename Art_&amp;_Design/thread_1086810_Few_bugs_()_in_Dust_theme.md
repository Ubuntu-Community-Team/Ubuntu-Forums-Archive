---
title: "Few bugs (?) in Dust theme"
date: 2009-03-04
forum: Art &amp; Design
---

### Post by aspora.isernia on 2009-03-04
Hi to all!
I've recently installed Dust theme from this link [https://wiki.ubuntu.com/Artwork/Incoming/DustTheme]("https://wiki.ubuntu.com/Artwork/Incoming/DustTheme") on ubuntu 8.04, but I noticed 2 little (probably) bugs:

1- sometimes the shell produces this message:
$HOME/.themes/Dust/gtk-2.0/gtkrc:709: error: unexpected identifier `highlight_ratio', expected character `}'
$HOME/.themes/Dust/gtk-2.0/gtkrc:709: error: unexpected identifier `highlight_ratio', expected character `}'

2- in Thunderbird the completion menu that suggests the receiver when composing a new email uses black fonts on black background and only the selected item is readable since it has white font on brown background (see attachment).

There is any fix to those two issues?
Thanks in any case...

a.i :D

---

### Post by smartboyathome on 2009-03-04
1) is because Intrepid uses a newer murrine engine thain Hardy. I suggest finding a backport of it.
2) is because Firefox/Thunderbird don't play nice with dark themes. There is a config file for dark themes for them somewhere on gnome-look.org, can't remember the name though. :S

---

### Post by exploder on 2009-03-05
> 1) is because Intrepid uses a newer murrine engine thain Hardy. I suggest finding a backport of it.

Here is the newer murrine engine smartboyathome mentioned.

[http://gnome-look.org/content/show.php/Murrine+Engine+(Ubuntu+Packages)?content=99516](http://gnome-look.org/content/show.php/Murrine+Engine+(Ubuntu+Packages)?content=99516)

I have the newer engine installed in Hardy and it works fine.

---

### Post by aspora.isernia on 2009-03-05
> **exploder said:**
> Here is the newer murrine engine smartboyathome mentioned.

[http://gnome-look.org/content/show.php/Murrine+Engine+(Ubuntu+Packages)?content=99516](http://gnome-look.org/content/show.php/Murrine+Engine+(Ubuntu+Packages)?content=99516)

I have the newer engine installed in Hardy and it works fine.

Thanks for your answers: I installed the murrine you linked me, but now I receive those messages...

```
$HOME/.themes/Dust/gtk-2.0/gtkrc:708: Murrine configuration option "highlight_ratio" will be deprecated in future releases. Please use "highlight_shade" instead.
$HOME/.themes/Dust/gtk-2.0/gtkrc:709: Murrine configuration option "lightborder_ratio" will be deprecated in future releases. Please use "lightborder_shade" instead.
$HOME/.themes/Dust/gtk-2.0/gtkrc:708: Murrine configuration option "highlight_ratio" will be deprecated in future releases. Please use "highlight_shade" instead.
$HOME/.themes/Dust/gtk-2.0/gtkrc:709: Murrine configuration option "lightborder_ratio" will be deprecated in future releases. Please use "lightborder_shade" instead.
```

Should it be enough to modify the file as suggested? I'll check and report.
Thanks again

a.i ;)

---

### Post by Giant Speck on 2009-03-05
> **aspora.isernia said:**
> Thanks for your answers: I installed the murrine you linked me, but now I receive those messages...

```
$HOME/.themes/Dust/gtk-2.0/gtkrc:708: Murrine configuration option "highlight_ratio" will be deprecated in future releases. Please use "highlight_shade" instead.
$HOME/.themes/Dust/gtk-2.0/gtkrc:709: Murrine configuration option "lightborder_ratio" will be deprecated in future releases. Please use "lightborder_shade" instead.
$HOME/.themes/Dust/gtk-2.0/gtkrc:708: Murrine configuration option "highlight_ratio" will be deprecated in future releases. Please use "highlight_shade" instead.
$HOME/.themes/Dust/gtk-2.0/gtkrc:709: Murrine configuration option "lightborder_ratio" will be deprecated in future releases. Please use "lightborder_shade" instead.
```Should it be enough to modify the file as suggested? I'll check and report.
Thanks again

a.i ;)

Yes, all you should have to do is go into the .gtkrc file and change all instances of "highlight_ratio" and "lightborder_ratio" to "highlight_shade" and "lightborder_shade", respectively.

---

### Post by aspora.isernia on 2009-03-05
Done!! No more debug messages. Thank to all of you for your help!!

Now I have to fix the problem with Thunderbird: any idea on how to modify the aspect of the application? Something like about:conf of Firefox?

Cheers

a.i ;)

---

### Post by zeus77 on 2009-03-07
I'd also love to know how to fix the Thunderbird issue... or even better, a Thunderbird dust theme to match the Firefox dust theme (aka dustfox)...
zeus77

---

### Post by Just-Jon on 2009-03-15
.

---

### Post by ryall on 2009-06-02
EDIT: sorry for some reason I got mixed up with Dust and the New Wave theme. You can probably still fix this by editing the userChrome.css file, see [http://www.mozilla.org/support/thunderbird/tips](http://www.mozilla.org/support/thunderbird/tips) for examples.



Create a directory called *chrome* in your *~/.mozilla-thunderbird/<uid>.default* directory.
Then add the file *userChrome.css*

Add this to the file (I copied this from the New Wave firefox theme [https://addons.mozilla.org/en-US/firefox/addon/11239](https://addons.mozilla.org/en-US/firefox/addon/11239)) :

```
/* This file fixes the New Wave Firefox/Thunderbird issue with unreadable text in the menubar
 *
 * Created by Anton Kerezov <ankere@gmail.com>
 *
 * Feel free to modify and share
 */
@namespace url("http://www.mozilla.org/keymaster/gatekeeper/there.is.only.xul"); /* set default namespace to XUL */



/*make the menubar use gray color for text*/
menubar > menu {
   color: #E5E5E5  !important;
}
/*make the menu use white color for text on mouse over*/
menubar > menu:hover {
  color: white;
}

/* use black for the prelight state */
menubar > menu[_moz-menuactive="true"][open="true"] {
  color: black !important;
}

/* Make the statusbar use grey color for text.
 * This improves usability.
 */
statusbar
{
        font-weight: normal !important;
        color: rgb(50%,50%,50%) !important;
}
```

restart thunderbird and you should see nice light text on your dark menubar ;)

---

### Post by aspora.isernia on 2009-06-03
I was so happy to read your post!! But... Still no readable addresses :(
Thank you for all.
I have noticed that this Dust problem happens also with a brand new installation of Jaunty Jackalope. Hope someone will fix it...

a.i

---

### Post by captaincrook on 2009-06-03
I've begun using this theme albeit in XFCE. I have one little annoyance though, is it possible to remove the little box "overlay" on a button?

[Over button1.](http://img5.imageshack.us/img5/7088/buttoncnr.png)

---

