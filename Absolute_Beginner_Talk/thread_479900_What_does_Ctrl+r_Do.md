---
title: "What does Ctrl+r Do?"
date: 2007-06-20
forum: Absolute Beginner Talk
---

### Post by LordKelvan on 2007-06-20
Hi:

I asked this before, but never received a response.  When I am on the desktop and I press ctrl+r , the desktop refreshes itself.  I was wondering if anyone knows:

a) What command ctrl+r executes
b) How to add a menu item which executes a key sequence, if no one knows about (a).

Cheers,
LK

---

### Post by MichaelLerch on 2007-06-20
a) CTRL - R issues a refresh within the OS or an App.  Example being, using the keybind in Firefox will issue a page refresh.   Using it on the desktop refreshes the desktop.

b) Not so sure, but I'm sure it'd be nifty.

---

### Post by LordKelvan on 2007-06-20
Thanks - so do you know the command that ctrl+r issues, i.e. what would I type into the terminal to cause my desktop to refresh itself?

---

### Post by p_quarles on 2007-06-20
According to this:
[http://linuxfud.wordpress.com/2007/02/15/add-a-refreshreload-gui-button-to-your-gnome-panel/](http://linuxfud.wordpress.com/2007/02/15/add-a-refreshreload-gui-button-to-your-gnome-panel/)

```
killall gnome-panel nautilus
```

The link gives specific instructions for setting it up.

---

### Post by ryanVickers on 2007-06-20
> killall gnome-panel nautilus
Wouldn't that kill the panels and desktop manager!?!  I know they would restart within seconds, and no damage would be done, but...!

I installed the "scripts" using Automatix2 (see signature), and I bet you could make a simple one to do this!

---

### Post by p_quarles on 2007-06-20
> **ryanVickers said:**
> Wouldn't that kill the panels and desktop manager!?!  I know they would restart within seconds, and no damage would be done, but...!

I installed the "scripts" using Automatix2 (see signature), and I bet you could make a simple one to do this!
Well, yes, but I got the idea that this is precisely what LordKelvan wants to do. A macro would work too, but wouldn't that pretty much do the same thing?

---

### Post by LordKelvan on 2007-06-20
Thanks for the suggestions but I've tried that command before, but it does not have the same effect.  The effect from ctrl+r (i.e. the effect I am looking for) seems less.......drastic.  

The closest analogy I can think of is in Windows, with the "Refresh Desktop" item in the context menu when you right-click on the desktop.  

[Edit]:  Actually, checking on my kubuntu install, I see that they have a "Refresh Desktop" entry in the context menu, just like in Windows, which achieves the effect I am looking for.  Does that perhaps help?

---

### Post by p_quarles on 2007-06-20
I don't use KDE, so I wouldn't know.

My best guess, though, tells me that KDE and Gnome shortcuts probably don't all have bash command equivalents. Your best bet, then, would be to follow ryanVickers' suggestion and try to setup a script.

---

### Post by king0lag on 2007-06-20
Are CTRL+R and F5 the same?

---

### Post by LordKelvan on 2007-06-21
Yes - F5 and Ctrl+r achieve the same effect.  I guess I will download automatix2 to see if they have a script to do what I want.  I'll report back.

[Edit]: Installing automatix2 does not install any scripts right?  I have to install automatix2, then pick which scripts to install right (I ask since I just want to copy their scripts, not actually use them directly).

---

### Post by ryanVickers on 2007-06-21
> [Edit]: Installing automatix2 does not install any scripts right? I have to install automatix2, then pick which scripts to install right (I ask since I just want to copy their scripts, not actually use them directly).

Correct.  A;lso, it's just "scripts", you can't pick what you want.  there's 3, one for root file browser at this spot, one for root gimp with this file, I made a gimp one to do the same, and one more I deleted because it was useles to me.  So, they don't have refresh, but I bet you could make one!  They're real simple - They look complex, but all it has to be is a terminal command in a textfile with execute permissions!

---

### Post by LordKelvan on 2007-06-21
Yeah, I am not a stranger to scripts - the problem, which still remains, is that I don't know what terminal command ctrl+r issues, so I can't make a script which achieves the same functionality.  Surely someone out there knows the command?

---

### Post by ryanVickers on 2007-06-21
Right, never thought of that! :p

If you know a bit of C++ and have enought time on your hands, if it was me (and these things were true about me :)), I would look in the Ubuntu source code and find what it does when you hit the "refresh" button in the File Browser! :)

---

### Post by quinnten83 on 2007-06-21
ask thet question in the developers sub forum??

---

### Post by LordKelvan on 2007-06-21
Hmm - you know that might not be a bad idea.  I think I will try that.

---

### Post by avik on 2007-06-21
> **ryanVickers said:**
> If you know a bit of C++ and have enought time on your hands, if it was me (and these things were true about me :)), I would look in the Ubuntu source code and find what it does when you hit the "refresh" button in the File Browser! :)

Actually, wouldn't it be better to look in the GNOME source code?

---

### Post by bobby_d on 2008-01-30
Actually, just looked in the sources - I too would like to "reload" Nautilus from command line.. as Ctrl-R maps to "Reload" button in Nautilus, looked at sources: 

**nautilus-window-menus.c**
```

{ "Reload", GTK_STOCK_REFRESH,                        /* name, stock id */
    N_("_Reload"), "<control>R",           /* label, accelerator */
    NULL,                                      /* tooltip */ 
    G_CALLBACK (action_reload_callback) },
```

This is probably where the binding is made... Then: 

```
static void
action_reload_callback (GtkAction *action, 
			gpointer user_data) 
{
	nautilus_window_reload (NAUTILUS_WINDOW (user_data));
}
```

so nautilus_window_reload is probably the function called... Then also:

**nautilus-window.c**
```
	gtk_binding_entry_add_signal (binding_set, GDK_F5, 0,
				      "reload", 0);
...
class->reload = nautilus_window_reload;

```

**nautilus-window-manage-views.c**
```
/* reload the contents of the window */
void
nautilus_window_reload (NautilusWindow *window)
{
...
}
```

I thought maybe adding a switch to the sources, so one could call the nautilus_window_reload function through something like 'nautilus --reload', but I doubt it will effect the running instance of Nautilus.. 

But, looking at the signal thing, maybe someone knows of a possibility  to send the "reload" signal to a running Nautilus from command line ??? 

Cheers

PS: Just saw [http://ubuntuforums.org/archive/index.php/t-658040.html](http://ubuntuforums.org/archive/index.php/t-658040.html) and 
> You could try the program called xautomation (sudo apt-get install xautomation) . Then for sending F1 the call is

xte "key F1" 

and the following command will invoke reload of desktop through keypresses
```
xte 'mousemove 1 50' 'mousedown 1' 'mouseup 1' 'key F5'
```
 but will also move your mouse pointer :) so still better to know a command line for doing it directly...

---

