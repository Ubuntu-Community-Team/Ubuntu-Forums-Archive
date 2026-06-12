---
title: "Kubuntu Guide?"
date: 2007-03-15
forum: Absolute Beginner Talk
---

### Post by 67GTA on 2007-03-15
Does anyone have a link to a good Kubuntu guide similar to ubuntuguide.org? I have downgraded to Dapper (edgy too buggy), and decided to dual boot with Kubuntu Dapper to check out KDE. This is my first KDE experience and need a little help with repositories, ati driver, themes, etc. I found the KDE wikki, but I am not sure about some of the content. I would feel better if I could find some official docs.

---

### Post by John.Michael.Kane on 2007-03-15
[**KUDOS Unofficial Kubuntu FAQ**]("http://kudos.berlios.de/kf/kf1.html")

[**kubuntudesktopguide**]("https://help.ubuntu.com/6.10/kubuntu/desktopguide/C/index.html")

---

### Post by 67GTA on 2007-03-15
Thanks, that is what I needed. I think I may like KDE better once I get to know it. It seems "smarter" than Gnome, if that is the right word.

---

### Post by qiemem on 2007-03-15
Just about everything from ubuntuguide.org still applies to kubuntu. The only difference between the two is the desktop environment (KDE or Gnome), and this is essentially just how stuff looks and behaves. So you're ati drivers will install exactly the same (as far as I know; they did for nvidia). In fact, except for themes and such, everything should carry over from what you did in Gnome. They use the same core system and settings.

As for themes, [http://kde-look.org/]("http://kde-look.org/") is a good place to look, though themes in kde can be tough to install. If you're just looking to tweak the way things look, pretty much anything you would want to change is in System Settings under the K menu.

As for a guide, I'm sure you've already seen the kubuntu documentation: [http://kubuntu.org/documentation.php]("http://kubuntu.org/documentation.php"). That's all I can really tell you about that kind of stuff. KDE can be a little tough to get into. I just tweaked around with it until I understood most of it and now I love it. But it was kind of overwhelming at first. 

Hope that helps!

Oh, if you ever want to "reset" kde (the way everything looks anyway), you can rename (so its backed up still and your mail and such will still be available) the .kde folder in your home directory (i.e. in a terminal, type "mv ~/.kde ~/.kde-backup")

---

### Post by chavo on 2007-03-15
Please don't tell people to rm -rf ~/.kde. It's better to move it out of the way if you need to reset settings. There are settings and more inside this folder, including email, bookmarks, etc. Better to move it out of the way and re-import stuff like mail.

---

### Post by qiemem on 2007-03-15
> 
Please don't tell people to rm -rf ~/.kde. It's better to move it out of the way if you need to reset settings. There are settings and more inside this folder, including email, bookmarks, etc. Better to move it out of the way and re-import stuff like mail.

Heh, good point. Changed my post. Guess I wasn't thinking that far ahead...

---

