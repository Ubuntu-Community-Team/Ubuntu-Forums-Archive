---
title: "New to Ubuntu / Gnome"
date: 2005-03-09
forum: Art &amp; Design
---

### Post by justaguynpc on 2005-03-09
Let me preface this immediately,  this is not to be intended as a KDE vs Gnome flame post ...............

I am accustomed to KDE.  KDE offered me the ability to mix and match colors from my desktop to be incorporated into the window theme I chose to apply.  For those of you familiar with KDE know what I am talking about.  I am thinking that it was the primary reason I stayed with KDE so long .............. until Ubuntu.

Ubuntu has given me the experience of using Gnome, and only Gnome, since it is Gnome-centric.  Now that I am learning my was around, I have to ask "Where is the desktop customization control in Gnome that KDE afforded me?"  I have tried and tried to find a window decoration / scheme that I like, with the defaults provided, and found nothing that I am crazy about.  I have visited, and had visited as a KDE user, Gnome-look.org, but am confused (greatly) by the GTK 1.X and the GTK 2.X, only to get even more confused by Metacity.

What are these?  What should I use? What shouldn't I use?  What are their pros and cons?  I hear alot about "clearlooks", but am not educated enough to know what I am looking at, or should look for.

I ask that someone with patience give me a quick rundown, or link to a tutorial on gnome desktop because I am having trouble finding the simpliest answers when I google.  I reallt want to change the default theme / colors on my desktop.   

Thanx!!!

justaguy

---

### Post by bored2k on 2005-03-09
Computer > Desktop Preferences > Themes . 
I don't think that was Rocket Science hard ...

Backgrounds on you're desktop, right clic on it > change background .
Not quantum physics.

GDM or Login Screen ?
Computer > System Configuration > Login Screen Setup.

--

Computer > Home
That's you're file manager, if you survived Konqueror/Windows Explorer, you can deal with this.

We would really like more specific questions, because most of the questions are gnome related, and we cant resume all of it in 10 lines .

---

### Post by justaguynpc on 2005-03-09
Yep, well aware of how to change desktop, and how to change window decorations.  What I am asking is, with GTK 1.X, and GTK 2.X, along with Metacity: what are the differences? What are the pros/ cons?  Can I use just any theme out there?   Is there a similiar method (as with KDE) of changing the colors of existing window decorations to better match my wallpaper.

Guess rocket science kicked your butt, eh?  

Thanks for the attempt ........... anyway.

---

### Post by Yukonjack on 2005-03-09
[QUOTE=justaguynpc]Yep, well aware of how to change desktop, and how to change window decorations.  What I am asking is, with GTK 1.X, and GTK 2.X, along with Metacity: what are the differences? What are the pros/ cons?  Can I use just any theme out there?   Is there a similiar method (as with KDE) of changing the colors of existing window decorations to better match my wallpaper.
Guess rocket science kicked your butt, eh?  
Thanks for the attempt ........... anyway.[/QUOTE]

GTK1.x older GTK2.x is newer and looks better The gtk is how your interface looks, metacity is your window border looks, you can mix and match the gtk theme with a metacity to give you a look that you like. A gtk engine is what you need to see the different gtk theme. Some gtk theme will be for the smooth engine or the clearlook engine and so on. Some metacity works better with a certain theme but from my experience most of them works well with any theme. 

Hope this help you out.

---

### Post by maruchan on 2005-03-09
I don't think there's an easy way to change the colors of the window decorations like you can in Windows or KDE. I have looked, but I haven't found anything. Also, by the (non-)answers you're getting about that, I'm thinking you're sunk.

Good luck though, let us all know when you find it.

---

### Post by justaguynpc on 2005-03-09
[QUOTE=Yukonjack]GTK1.x older GTK2.x is newer and looks better The gtk is how your interface looks, metacity is your window border looks, you can mix and match the gtk theme with a metacity to give you a look that you like. A gtk engine is what you need to see the different gtk theme. Some gtk theme will be for the smooth engine or the clearlook engine and so on. Some metacity works better with a certain theme but from my experience most of them works well with any theme. 

Hope this help you out.[/QUOTE]
 Thanks Rick!  That was more in-line with what I was asking originally.  Appreciate the feedback.

Am moving to Ontario from Florida in a few short months,  should be seeing more of the Canadian hospitality!

justaguy

---

### Post by Yukonjack on 2005-03-09
[QUOTE=justaguynpc]Thanks Rick!  That was more in-line with what I was asking originally.  Appreciate the feedback.
Am moving to Ontario from Florida in a few short months,  should be seeing more of the Canadian hospitality!
justaguy[/QUOTE]

Glad to help and good luck with your big move  :wink:

---

### Post by Papaskunk on 2005-04-03
One more thing having to do with Metacity. Metacity isn't just a window decoration, it's a window manager. KDE for example uses its own window manager, KWin. Gnome however does not have its "own". By default it ships with Metacity, but you can use any window manager you want. The Metacity window decoration is the the default window decoration of the Metacity window manager. So if you hear talk of things working with Metacity, you know it's the window manager they're talking about and not the theme.

---

### Post by HungSquirrel on 2005-04-04
> By default it ships with Metacity, but you can use any window manager you want.
Sort of.  Most of them make GNOME very glitchy.  ;)

AFAIK there is no easy way to customize colorschemes in GNOME.  This is one of its big turnoffs for me too.  GNOME tries to leave all the control in the hands of the system, whereas KDE's Control Center gives it to the user.  You pretty much have to manually edit a text file with hex values to make changes to your colorscheme.

---

### Post by basse1989 on 2005-04-05
The color of the metacity theme is controlled by the gtk theme currently in use, as you might have noticed. If you want to install clearlooks, which I **really** like, i think it's in the hoary repositories.

---

