---
title: "Modify top panel (wingpanel) elementary OS Luna Beta 1"
date: 2012-11-23
forum: Any Other OS
---

### Post by ellisblake on 2012-11-23
Hi can someone guide me of how to modify the top panel ?
At the moment the top panel sits half outside of the desktop area and the icons within the panel are only half visible.

I have tried following their instructions of how to work with the panel but my configuration in gconf and dconf is different from the way they explain it.

They also give examples of how to unlock the desktop and the top panel.But i cant make it work.

Can someone explain at least why is the top panel looking like that?

Thanks

---

### Post by nothingspecial on 2012-11-23
Question moved to it's own thread.

---

### Post by Chdslv on 2012-11-23
> **ellisblake said:**
> Hi can someone guide me of how to modify the top panel ?
At the moment the top panel sits half outside of the desktop area and the icons within the panel are only half visible.

I have tried following their instructions of how to work with the panel but my configuration in gconf and dconf is different from the way they explain it.

They also give examples of how to unlock the desktop and the top panel.But i cant make it work.

Can someone explain at least why is the top panel looking like that?

Thanks

You cannot modify the Wingpanel, the top panel of eOS Luna. I've been asking that for quite sometime, but the devs are not saying anything about that. Most probably, they can't modify it. Anyway, you better ask from eOS forums, or from their main site and in Journal, otherwise blog.

I've used a different panel, but I'd come back later with info. Read my posts. Click on my name and you'd find them

Good day!:)

---

### Post by ellisblake on 2012-11-23
> **Chdslv said:**
> You cannot modify the Wingpanel, the top panel of eOS Luna. I've been asking that for quite sometime, but the devs are not saying anything about that. Most probably, they can't modify it. Anyway, you better ask from eOS forums, or from their main site and in Journal, otherwise blog.

I've used a different panel, but I'd come back later with info. Read my posts. Click on my name and you'd find them

Good day!:)

I am live with the devs right now....and they are getting me to try various things....
but nothing works.
they suggested killall. to restart the panel but it didnt restart and i can only see 2 mil of the panel after killall and in its place is a kind of floating transparent panel.....

---

### Post by blaede22 on 2012-11-23
Hey guys, I'm Cassidy James, a UX designer and Council member from elementary. The user guide you were referring to is for our current release, Jupiter. We don't put documentation up for unreleased versions. Sorry for the confusion. :P

As far as your specific issue, it sounds like some weird bug. Be sure to report bugs [_on Launchpad_]("https://bugs.launchpad.net/elementary"). Out of curiousity, are you running a relatively unmodified Luna Beta 1 install, or was this built ontop of Ubuntu or something? Be sure to include that info on the bug, as well as some hardware details so hopefully we can track down the cause and submit a fix.

---

### Post by Chdslv on 2012-11-23
> **ellisblake said:**
> I am live with the devs right now....and they are getting me to try various things....
but nothing works.
they suggested killall. to restart the panel but it didnt restart and i can only see 2 mil of the panel after killall and in its place is a kind of floating transparent panel.....

I suppose you understand now, why the Elementary OS is in permanent Alpha-Beta state!:) 

Anyway, for the moment you can't modify the top panel - Wingpanel. You also can'y modify the dock - Plank. And, if you take those two items off, this eOS would be a hit. Otherwise, it'd have the same history as Jupitor. Most Linix users don't even remember such a distro.

“The path to Hell is paved with good intentions.”

I've lived a long life, so I know the above saying is true.:)

---

### Post by ellisblake on 2012-11-23
> **blaede22 said:**
> Hey guys, I'm Cassidy James, a UX designer and Council member from elementary. The user guide you were referring to is for our current release, Jupiter. We don't put documentation up for unreleased versions. Sorry for the confusion. :P

As far as your specific issue, it sounds like some weird bug. Be sure to report bugs [_on Launchpad_]("https://bugs.launchpad.net/elementary"). Out of curiousity, are you running a relatively unmodified Luna Beta 1 install, or was this built ontop of Ubuntu or something? Be sure to include that info on the bug, as well as some hardware details so hopefully we can track down the cause and submit a fix.

Hi James,

First let me try to say that in spite of a few issues i really like the way the eOS works and looks.
And to answer your question i run luna beta out of the box ,unmodified .On the same machine though i have ubuntu PP.
I have tried all sorts of things and i reboted the machine numerous times everytime getting  a random result .Sometime i see half of the wingpanel sometime only a few milimitres.
After two days i coundn't find a direcct corespondence between the changes i make ,changing the parameters in the interface via  gconfig tools and the results i get.

One thing i have to mention though...that i do not understand everithing about what the parameters do.So its very possible that i do something wrong.

---

### Post by Chdslv on 2012-11-24
> **blaede22 said:**
> Hey guys, I'm Cassidy James, a UX designer and Council member from elementary. The user guide you were referring to is for our current release, Jupiter. We don't put documentation up for unreleased versions. Sorry for the confusion. :P

As far as your specific issue, it sounds like some weird bug. Be sure to report bugs [_on Launchpad_]("https://bugs.launchpad.net/elementary"). Out of curiousity, are you running a relatively unmodified Luna Beta 1 install, or was this built ontop of Ubuntu or something? Be sure to include that info on the bug, as well as some hardware details so hopefully we can track down the cause and submit a fix.

Hello Cassidy, I like you eOS, but don't like your Wingpanel and Plank. Whatever Shnatsel says, the Wingpanel looks identical to Gnome-shell panel, and just like that, it doesn't move out of the way. Just because of Flippery, we could move the clock to right in Gnome-shell 3.4.1, and with Eddiefulmetal auto-hide the panel, but after that no way to do that. Plank is unconfigurable, not like its parent Docky.

Whoever, who made Gala must be highly commended! Gala is 99% Elementary experience! I use Gala with many panels and sessions, even in Unity (or Ubuntu desktop). Mind you, I can't write a single line in Python, maybe "Hello World." 

If you drop the Wingpanel and Plank, you might be able to release the final Luna.:)

Take care!

Ch

PS; Check my other posts, if you like
You can notice in the screenshot that there is no Wingpanel or Plank, and all three buttons are on the right

---

### Post by ellisblake on 2012-11-24
> **Chdslv said:**
> Hello Cassidy, I like you eOS, but don't like your Wingpanel and Plank. Whatever Shnatsel says, the Wingpanel looks identical to Gnome-shell panel, and just like that, it doesn't move out of the way. Just because of Flippery, we could move the clock to right in Gnome-shell 3.4.1, and with Eddiefulmetal auto-hide the panel, but after that no way to do that. Plank is unconfigurable, not like its parent Docky.

Whoever, who made Gala must be highly commended! Gala is 99% Elementary experience! I use Gala with many panels and sessions, even in Unity (or Ubuntu desktop). Mind you, I can't write a single line in Python, maybe "Hello World." 

If you drop the Wingpanel and Plank, you might be able to release the final Luna.:)

Take care!

Ch

PS; Check my other posts, if you like
You can notice in the screenshot that there is no Wingpanel or Plank, and all three buttons are on the right

and how do i uninstall the wingpanel?
As you can see above i had some issues with the wingpanel and now it dissapeard complettely but and in its place what's left is   a transparent floating panel.

---

### Post by Chdslv on 2012-11-24
> **ellisblake said:**
> and how do i uninstall the wingpanel?
As you can see above i had some issues with the wingpanel and now it dissapeard complettely but and in its place what's left is   a transparent floating panel.

Okay, first of all, maybe you'd have to reinstall eOS Luna Beta 1, or if you believe its working well, you can keep it. Whatever your decision, the solution is the same.

In your terminal, 

>  gksudo pantheon-filesThen, navigate to /usr/bin and find wingpanel and rename it anyway you like, for example wingpanel1, then navigate to /usr/share/applications and find Wingpanel, and remane it too. (in /usr/bin it starts with a small letter, and in /usr/share/applications in a capital letter.)

Also find Plank also in /usr/share/applications and/or /usr/bin and rename them. That way, you stop them from appearing. 

Then, you install any dock/ you like start and put that panel/dock in the startup applications. Now, you'd have the panel/dock you like and the Pantheon and Gala and everything.

Here is an example. I have Lxpanel installed, just to show you. I took off Docky too. You can make the Lxpanel autohide too.:)

By the way, this is Luna Beta 1 as it came and with my wallpaper and the tweaks.

Take care!

Ch

---

### Post by ellisblake on 2012-11-24
> **Chdslv said:**
> Okay, first of all, maybe you'd have to reinstall eOS Luna Beta 1, or if you believe its working well, you can keep it. Whatever your decision, the solution is the same.

In your terminal, 

Then, navigate to /usr/bin and find wingpanel and rename it anyway you like, for example wingpanel1, then navigate to /usr/share/applications and find Wingpanel, and remane it too. (in /usr/bin it starts with a small letter, and in /usr/share/applications in a capital letter.)

Also find Plank also in /usr/share/applications and/or /usr/bin and rename them. That way, you stop them from appearing. 

Then, you install any dock/ you like start and put that panel/dock in the startup applications. Now, you'd have the panel/dock you like and the Pantheon and Gala and everything.

Here is an example. I have Lxpanel installed, just to show you. I took off Docky too. You can make the Lxpanel autohide too.:)

By the way, this is Luna Beta 1 as it came and with my wallpaper and the tweaks.

Take care!

Ch

thank you 
That worked perfectly

---

### Post by Chdslv on 2012-11-24
> **ellisblake said:**
> thank you 
That worked perfectly

I'm glad!:)

Here is another screenshot, now with Awn dock, and without Wingpanel and Plank. The Slingshot launcher in on the far left corner the letter A on green background. A for Araliya and that's the flower you see on the screen.

Take care!

Ch

---

### Post by ellisblake on 2012-11-24
> **Chdslv said:**
> I'm glad!:)

Here is another screenshot, now with Awn dock, and without Wingpanel and Plank. The Slingshot launcher in on the far left corner the letter A on green background. A for Araliya and that's the flower you see on the screen.

Take care!

Ch

That looks good.
The lxpanel works well for me  but i cant find a way to add logout,suspend,shut down plugins .Where would those be or how can these applets be added ?

---

### Post by ajith4mpbvr on 2013-07-02
is there any ways to replace the dockey and wing panel with old ubuntu panel ( before unity has become the default one)?

---

### Post by ubigeek2907 on 2013-07-03
after looking and figuring out what the problem was, so everybody can find it, just delete permanently the .config folder of your home... that's all

---

