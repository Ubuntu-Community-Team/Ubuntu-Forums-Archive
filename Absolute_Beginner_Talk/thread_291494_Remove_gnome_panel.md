---
title: "Remove gnome panel"
date: 2006-11-02
forum: Absolute Beginner Talk
---

### Post by DOD1951 on 2006-11-02
I moved to KDE 3.5.2 from Gnome desktop because I like the interface more. I used to have a top and bottom panel with the gnome desktop. I removed the top panel easily by selecting delete pane;l. How do I remove the gnome bottom panel which doesn't have the delete panel option?

---

### Post by Dr. Nick on 2006-11-02
Just curious, maybe I misunderstand you; But if you are using KDe why do the gnome panels being deleted matter?

If you want try 

killall gnome-panel

That wont delete the panel, just shut it down

---

### Post by DOD1951 on 2006-11-02
I should have explained better. When i started the KDE session on login i get both the KDE panel and the Gome panel. I suppose i have a sort of Ubuntu/Kubuntu hybred, mongrel mix of desktop.:) The kill gnome-panel worked, thanks for that, but i suspect it will reappear after reboot.

---

### Post by zekopeko on 2006-11-02
> **DOD1951 said:**
> I should have explained better. When i started the KDE session on login i get both the KDE panel and the Gome panel. I suppose i have a sort of Ubuntu/Kubuntu hybred, mongrel mix of desktop.:) The kill gnome-panel worked, thanks for that, but i suspect it will reappear after reboot.

hmmm.... 

try loging in your gnome session and there removing the panel

don't really know what is the problem but this seems logical

---

### Post by pbaehr on 2006-11-02
If killall gnome-panel worked you could always make a script and add it to your session start as a last resort.

There must be a better way, though.

---

### Post by LinuxIsInnovation on 2007-12-27
It worked for me:
Open gconf and goto /apps/panel/toplevels and set these values:
auto_hide: yes
auto_hide_size: 1
expand: no
hide_delay: 1
monitor: 3
unhide_delay: 10000
x: 10000
y: 10000

This will hide the panel permanently. :D

---

### Post by cartisdm on 2008-01-04
> **sayakb said:**
> It worked for me:
Open gconf and goto /apps/panel/toplevels and set these values:
auto_hide: yes
auto_hide_size: 1
expand: no
hide_delay: 1
monitor: 3
unhide_delay: 10000
x: 10000
y: 10000

This will hide the panel permanently. :D

Been looking all over for an answer to this problem, finally this worked great!  Thanks!

---

### Post by krelverehan on 2008-04-07
> **DOD1951 said:**
> I moved to KDE 3.5.2 from Gnome desktop because I like the interface more. I used to have a top and bottom panel with the gnome desktop. I removed the top panel easily by selecting delete pane;l. How do I remove the gnome bottom panel which doesn't have the delete panel option?

I would just go into 

[COLOR="Sienna"]menu >> preferences >> sessions[/COLOR]

Click on the [COLOR="Sienna"]current sessions[/COLOR] tab and find the [COLOR="Sienna"]gnome-panel[/COLOR] on the list turn its style to [COLOR="Sienna"]normal[/COLOR] rather than [COLOR="Sienna"]refresh[/COLOR].

And bash [COLOR="Sienna"][FONT="Courier New"]$ killall gnome-panel[/FONT][/COLOR]

I am not too sure if this would keep when you restart... Hope this helps.

[COLOR="Red"]**[/COLOR]Take note this this disables you to alt-f2  to run applications. But there are other programs, namely [[COLOR="Blue"]Gnome-do[/COLOR]]("http://do.davebsd.com/"), that I find far better.[COLOR="Red"]**[/COLOR]

---

### Post by hanniph on 2008-05-27
If you don't want to disable alt+f2 dialog, then you may try a simple trick. Remove everything from unnecessary panel. Open preferences of the panel and make sure it expanded. Then set the background of the panel to transparent. In such case, you won't get rid off it but you won't simply see it.

---

