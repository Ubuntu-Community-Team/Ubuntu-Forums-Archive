---
title: "FireFox Extension problem : Gtk-CRITICAL:"
date: 2006-12-03
forum: Absolute Beginner Talk
---

### Post by rubbsdecvik on 2006-12-03
Hello all.  I'm running Firefox with the StumbleUpon extension.  Not long ago Firefox would start and immediately it would close.

I started it in safe mode via:

```
firefox -safe-mode
```

and by process of elimination I was able to determine that it was the StumbleUpon extension that was giving me trouble.  Here is what I would get when I started Firefox in the terminal with the extension enabled.

```

(Gecko:9737): Gtk-CRITICAL **: gtk_widget_get_parent_window: assertion `GTK_IS_WIDGET (widget)' failed

(Gecko:9737): Gdk-CRITICAL **: gdk_window_is_viewable: assertion `window != NULL' failed

(Gecko:9737): Gtk-CRITICAL **: gtk_widget_get_parent: assertion `GTK_IS_WIDGET (widget)' failed

``` 

I'm guessing this isn't just an extension problem.  

Not sure where to go from here.  I am running Kubuntu Edgy.  I would appreciate any help anyone can give me, because I would love to be able to use this extension some more.

Thank you.

---

### Post by rubbsdecvik on 2006-12-03
bump

---

### Post by aysiu on 2006-12-03
Based on [this Google search for your error](http://www.google.com/search?num=100&hl=en&lr=lang_en&safe=off&q=Gtk-CRITICAL+**%3A+gtk_widget_get_parent_window%3A+assertion+%60GTK_IS_WIDGET+%28widget%29%27+failed&btnG=Search), I'd say it has to do with a theme you have installed.

---

### Post by rubbsdecvik on 2006-12-03
Thank you... I'll try that.

(That was a duh moment)

---

### Post by rubbsdecvik on 2006-12-03
You were right... it was the theme.  Which is unfortunate, because I liked that theme.  But such as life.


Thanks again!

---

### Post by aysiu on 2006-12-03
> **rubbsdecvik said:**
> You were right... it was the theme.  Which is unfortunate, because I liked that theme.  But such as life.


Thanks again!
Maybe there's some way you can file a bug report with the theme's developer?

---

### Post by Atomic Dog on 2006-12-04
> **rubbsdecvik said:**
> Thank you... I'll try that.

(That was a duh moment)

Don't feel bad.  At work I get questions that are so simple a google search produces the answers easily yet I can't seem to get them to use it.

Your question is good that it adds to the knowledge base of this forum!

---

### Post by wadeall on 2006-12-07
Hi  i have the same problem  Firefox was working fine until I put the Stumbleupon extension on it.  I am using the Noia extrate Theme.  is  this the  problem? How do I solve this issue?

Wade

---

### Post by rubbsdecvik on 2006-12-07
That was the theme I was using.  

I had to disable either StumbleUpon, or Noia Extreme.  

I still haven't found a way to fix it yet.  

But disable one or the other and FF should work.  

Just in case you don't know how to do it,

In a terminal:
```
firefox -safe-mode
```

and then you can disable which ever things you want in the addons menu.

I'll let you know if I find a better fix.

---

