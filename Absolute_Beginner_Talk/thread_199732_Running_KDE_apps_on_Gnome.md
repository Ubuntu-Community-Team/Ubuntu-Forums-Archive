---
title: "Running KDE apps on Gnome"
date: 2006-06-19
forum: Absolute Beginner Talk
---

### Post by amanda on 2006-06-19
I'm not trying to restart this thread:
[http://www.ubuntuforums.org/showthread.php?t=196231](http://www.ubuntuforums.org/showthread.php?t=196231)

Which led to this:
[http://iball.is-a-geek.org/Members/admin/linux/kde-versus-gnome](http://iball.is-a-geek.org/Members/admin/linux/kde-versus-gnome)

But rather, I am trying to sort something out.

I am more comfortable in Gnome (right now, I don't even remember what fed me up with KDE, sometimes I think about going back) but I much prefer Knotes (the KDE sticky app) to Gnome's Stickies, and I know Quanta pretty well and don't feel much like learning a new code editor. 

So my question is whether there is some inherent problem in running KDE applications on Gnome, assuming that they basically work. Are KDE apps having to run big chunks of KDE to work? Or are they just using a different set of libraries?

Do you see the difference here? Libraries take up space, running takes up RAM. I don't want to get into habits that I'll regret when I start using this computer in earnest, and so I am wondering. I also just want to know.

 I'd put myself into the category of Mixed-Advanced. I can do a lot, but somethings I just can't do. Like evaluate which programs are hogging system resources.

---

### Post by Princey on 2006-06-19
[QUOTE=amanda]I'm not trying to restart this thread:
[http://www.ubuntuforums.org/showthread.php?t=196231](http://www.ubuntuforums.org/showthread.php?t=196231)

Which led to this:
[http://iball.is-a-geek.org/Members/admin/linux/kde-versus-gnome](http://iball.is-a-geek.org/Members/admin/linux/kde-versus-gnome)

But rather, I am trying to sort something out.

I am more comfortable in Gnome (right now, I don't even remember what fed me up with KDE, sometimes I think about going back) but I much prefer Knotes (the KDE sticky app) to Gnome's Stickies, and I know Quanta pretty well and don't feel much like learning a new code editor. 

So my question is whether there is some inherent problem in running KDE applications on Gnome, assuming that they basically work. Are KDE apps having to run big chunks of KDE to work? Or are they just using a different set of libraries?

Do you see the difference here? Libraries take up space, running takes up RAM. I don't want to get into habits that I'll regret when I start using this computer in earnest, and so I am wondering. I also just want to know.

 I'd put myself into the category of Mixed-Advanced. I can do a lot, but somethings I just can't do. Like evaluate which programs are hogging system resources.[/QUOTE]

It depends on what programs you're trying to run. I run some Gnome programs inside of KDE and the same should hold. Some programs require few libraries or dependencies, while others, require quite a bit. Your best best is to use synaptic. See the amount of dependecies and/or libraries needed to run the application in question. Then you can make the choice of whether to go ahead or not. Some many not rquire anything at all. But I can't say offhand which does and which doesn't. Use synaptic, it's the best pointer you can get of what's needed and what isn't.

---

### Post by amanda on 2006-06-19
Synapic won't tell me whether a program is going to hog system resources. I have an absurdly large hard drive: I'm not worried about storage, I'm worried about what all is running at once.

Maybe a better question is about how to read the output of "ps aux" to evaluate this for myself.

---

### Post by beerfan on 2006-07-05
How does one change the theme of KDE apps in Gnome? This is important for getting KDE apps to intregrate well.

[Edit]It seems a solution to this issue is being discussed for Edgy Eft. For those of us on Dapper Drake though, can we just go to KDE-Look.org and download the [QtCurve theme]("http://www.kde-look.org/content/show.php?content=40920"), which is a Kubuntu package? Will this package affect Gnome?

---

