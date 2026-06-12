---
title: "[SOLVED] fastest gtk-2 engine?"
date: 2008-02-14
forum: Absolute Beginner Talk
---

### Post by kaiju on 2008-02-14
i'd need a gtk theme that's as fast as possible (340 mhz processor under the hub :D ).
what is the best engine to build on?
also, it would be awesome if somebody could recommend a theme i can start tayloring to my needs.

thanks :)

---

### Post by uclalinux on 2008-02-14
why don't you try xubuntu, it is like ubuntu but for older computers

---

### Post by kerry_s on 2008-02-14
> **kaiju said:**
> i'd need a gtk theme that's as fast as possible (340 mhz processor under the hub :D ).
what is the best engine to build on?
also, it would be awesome if somebody could recommend a theme i can start tayloring to my needs.

thanks :)

the inbuilt ones will always be the fastest. 
what window manager or desktop are you planing on using?

with 340mhz you really need to go custom install to get the best speed.
[http://www.psychocats.net/ubuntu/minimal](http://www.psychocats.net/ubuntu/minimal)

how much ram do you have, that also makes a big difference?

my systems 450mhz 256mb ram, i use a debian custom install, debian works better on the old stuff. :)
[http://ubuntuforums.org/showthread.php?p=4331293#post4331293](http://ubuntuforums.org/showthread.php?p=4331293#post4331293)

---

### Post by kaiju on 2008-02-14
@uclalinux: i don't really like desktop environments, so i'm using fluxbox anyway; and without all the gnome stuff loaded, there's not much of a difference between ubuntu and xubuntu (i have tried both).

@kerry_s: i'm using fluxbox and have 256 mb of ram. (and my hobbies are bla bla bla :P )
i did a minimal install once, but somehow messed it up and decided to get the full bag again.
i've also been thinking about debian or arch, just didn't have the patience yet.
anyway, this is not about the overall speed of the computer, but i can certainly tell the difference between some of the different gtk themes when using e.g. thunar.


as for the gtk 2 engines, i'm supposing i could just edit the files of my existing themes and they would still automatically use the engines i have, right? or how does that work?

also, it would be really cool if you people could suggest me some nice minimalistic themes :)

---

### Post by FuturePilot on 2008-02-14
Any theme that doesn't make extensive use of pixmaps will be fast.
I've found that pixmap themes tend to be a bit slower than non-pixmap themes

---

### Post by kerry_s on 2008-02-14
> **kaiju said:**
> @uclalinux: i don't really like desktop environments, so i'm using fluxbox anyway; and without all the gnome stuff loaded, there's not much of a difference between ubuntu and xubuntu (i have tried both).

@kerry_s: i'm using fluxbox and have 256 mb of ram. (and my hobbies are bla bla bla :P )
i did a minimal install once, but somehow messed it up and decided to get the full bag again.
i've also been thinking about debian or arch, just didn't have the patience yet.
anyway, this is not about the overall speed of the computer, but i can certainly tell the difference between some of the different gtk themes when using e.g. thunar.


as for the gtk 2 engines, i'm supposing i could just edit the files of my existing themes and they would still automatically use the engines i have, right? or how does that work?

also, it would be really cool if you people could suggest me some nice minimalistic themes :)


have you tried some of the other ones in synaptic, i've alway's liked the spherecrystal theme, it's like mac.
i don't have any engines installed, jwm doesn't except windows themes and rox-filer i did the icon theme myself.

---

### Post by RedSquirrel on 2008-02-15
I tend to use the "Mist" theme when I'm looking for something fast (which is almost always! :)). Clearlooks doesn't seem too bad either.

On my system, if I want to modify a theme, I copy the theme's directory tree from /usr/share/themes to ~/.themes and give it a new name ("theme-blah-mine"). The engine is still used, but according to my pretty settings in my custom gtkrc file.

---

### Post by kerry_s on 2008-02-15
> **RedSquirrel said:**
> I tend to use the "Mist" theme when I'm looking for something fast (which is almost always! :)). Clearlooks doesn't seem too bad either.

On my system, if I want to modify a theme, I copy the theme's directory tree from /usr/share/themes to ~/.themes and give it a new name ("theme-blah-mine"). The engine is still used, but according to my pretty settings in my custom gtkrc file.

hey RedSquirrel,
did ya see my little jwm project? i'm doing different setups. :)
[http://ubuntuforums.org/showthread.php?p=4331293#post4331293](http://ubuntuforums.org/showthread.php?p=4331293#post4331293)
i took out the openbox screen shot, cause well it's just blank.
but i did that 1 for you, cause i was thinking eventually your going to say "what about openbox?"

so this 1's for you. :lolflag:

---

### Post by urukrama on 2008-02-16
> **RedSquirrel said:**
> I tend to use the "Mist" theme when I'm looking for something fast (which is almost always! :)). Clearlooks doesn't seem too bad either.

I was about to suggest Mist as well.

---

### Post by kaiju on 2008-02-16
@RedSquirrel & urukrama: after having tried the different themes that come with ubuntu, i definitely agree that 'mist' is the fastest.

thanks, everybody :)

---

### Post by RedSquirrel on 2008-02-16
> **kerry_s said:**
> hey RedSquirrel,
did ya see my little jwm project? i'm doing different setups. :)
[http://ubuntuforums.org/showthread.php?p=4331293#post4331293](http://ubuntuforums.org/showthread.php?p=4331293#post4331293)
i took out the openbox screen shot, cause well it's just blank.
but i did that 1 for you, cause i was thinking eventually your going to say "what about openbox?"

so this 1's for you. 

Thanks. I'm sure urukrama was glad to see an **Openbox** shot as well. :)

I'll check out your other thread now...

---

### Post by RedSquirrel on 2008-02-16
> **urukrama said:**
> I was about to suggest Mist as well.

It's one of my favourites. I just started using it again this morning after trying out dozens of GTK and Openbox themes. I did that last weekend too, but so far I haven't found anything that I can stick with for more than a few minutes. I always go back to the basics. ;)



> **kaiju said:**
> @RedSquirrel & urukrama: after having tried the different themes that come with ubuntu, i definitely agree that 'mist' is the fastest.

Glad you found something suitable. :)

---

### Post by kaiju on 2008-02-16
actually, most of the time i've been using mist up until now, too. what your posts did was to reassure me that it's the best one i can get ready-made :)
(industrial is my other favorite)

> It's one of my favourites. I just started using it again this morning after trying out dozens of GTK and Openbox themes. I did that last weekend too, but so far I haven't found anything that I can stick with for more than a few minutes. I always go back to the basics. 
RedSquirrel, may i ask what exactly you mean by 'going back to the basics'?

oh and i've looked into the gtkrc files of some of the installed themes, but colors are the only thing i can recognize in there :P
how do the themes get all the pretty little pictures and such?

---

### Post by kerry_s on 2008-02-17
the pictures can be changed to, you copy the part you want from the gtkrc to your ~/.gtkrc-2.0, then just have your way with it till it works. i do a similar thing for my rox setup.

here's what my ~/.gtkrc-2.0 looks like right now.
the top sets my rox background, the bottom is for the buttons.

```
pixmap_path "/home/user/.backgrounds"
style "rox" = "default"
{
  bg_pixmap[NORMAL] = "blue.png"
}
widget_class "*ViewCollection*" style "rox"

pixmap_path "/home/user/.icons/rox-theme"
style "normal" {
  stock["gtk-go-up"] = {{"up.png"}}
  stock["gtk-home"] = {{"home.png"}}
  stock["gtk-jump-to"] = {{"bookmark.png"}}
  stock["gtk-refresh"] = {{"refresh.png"}}
  stock["gtk-zoom-in"] = {{"zoom-in.png"}}
  stock["gtk-zoom-fit"] = {{"zoom-fit.png"}}
  stock["rox-show-hidden"] = {{"hidden.png"}}
}
widget "*" style "normal"

```

---

### Post by kaiju on 2008-02-17
thanks, kerry_s. are you suggesting that the bitmap profiles of different gtk applications can be changed separately? (because if it's so than that's a wicked cool thing)

i've recently found this: [http://live.gnome.org/GnomeArt/Tutorials/GtkThemes](http://live.gnome.org/GnomeArt/Tutorials/GtkThemes)
i haven't had the time to read it through yet, but it looks like useful information.

---

### Post by RedSquirrel on 2008-02-17
> **kaiju said:**
> RedSquirrel, may i ask what exactly you mean by 'going back to the basics'?

I have installed a large number of themes and engines but I always seem to drift back to Mist or Clearlooks (with some colour adjustments). I guess I consider Mist and Clearlooks to be fairly common, so I called them "basics". ;)

---

### Post by yabbadabbadont on 2008-02-17
> **RedSquirrel said:**
> I have installed a large number of themes and engines but I always seem to drift back to Mist or Clearlooks (with some colour adjustments). I guess I consider Mist and Clearlooks to be fairly common, so I called them "basics". ;)

And Glider.  Mustn't forget Glider.  :)

(Although I generally use MIst too)

---

### Post by kaiju on 2008-02-18
oh i see.
mist is the fallback option for me too.

what about raleigh? i've read that it doesn't even use an engine. which means that it must be the least you can get ;) does anybody know if it can still be customized?

---

### Post by stchman on 2008-02-18
> **kaiju said:**
> i'd need a gtk theme that's as fast as possible (340 mhz processor under the hub :D ).
what is the best engine to build on?
also, it would be awesome if somebody could recommend a theme i can start tayloring to my needs.

thanks :)

A processor that slow would be a candidate for Puppy.  Ubuntu in any flavor is too much for a proc that slow.

---

### Post by kaiju on 2008-02-18
> **stchman said:**
> A processor that slow would be a candidate for Puppy.  Ubuntu in any flavor is too much for a proc that slow.

well, i'm using fluxbox anyway, with only gnome-screensaver started at login, and i've also removed some daemons i didn't need. besides, i mostly use lightweight apps, so i'm not sure a small distro's somewhat better speed  can compensate me for not being able to use the huge ubuntu repositories. (oh, and ubuntu is darn easy too, which is just perfect for a lazy kid like me ;) )

so, where was i...
how do i make raleigh pretty, folks? :D

---

### Post by RedSquirrel on 2008-02-18
> **kaiju said:**
> so, where was i...
how do i make raleigh pretty, folks? :D

Yes, you can modify it. The Raleigh gtkrc theme file is empty, so just add something to it (in your custom Raleigh theme directory under ~/.themes).

---

### Post by kaiju on 2008-02-18
oh, i see. thanks :)

---

### Post by solar george on 2008-05-29
If you're still interested xfce-stellar appears to be the fastest gtk engine
[http://gianvito.wordpress.com/2008/02/20/gtk-engines-benchmarks-whats-the-fastest/4/](http://gianvito.wordpress.com/2008/02/20/gtk-engines-benchmarks-whats-the-fastest/4/)

---

### Post by kaiju on 2008-05-29
thanks for the info.
i still use Mist (looks like it's listed as the fastest among the non-xfce ones on the page in your link, too), but the issue has sort of lost priority in the meantime, as i find i'm mostly avoiding graphical apps lately :)

---

### Post by solar george on 2008-05-29
The trouble with the Xfce ones is that you have to edit them or they force you to use their icon theme.

---

