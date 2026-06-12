---
title: "Unity under Archlinux"
date: 2016-01-11
forum: Arch and derivatives
---

### Post by sollidsnake on 2016-01-11
Hello Ubuntu fellows.
I'm a archlinux user, and I'm trying to port the unity desktop to use under archlinux. Currently there's already a Unity-for-Arch project, but with the last gnome updates it's broken. I got most of the way done: I built the ubuntu specific packages and got unity running, but there's still 2 issues I couldn't fix:

1. Menus are duplicated. When I open a program, I get duplicated menus - it's shown both on global menu bar and locally the window. I also get this warning which I think might be related:
```
"WARNING **: Couldn't connect to accessibility bus: Failed to connect to socket /tmp/dbus-GyJk3FE0pL: Connection refused"
```

2. Themes are not applied. I tried changing the theme in gnome-tweak-tool but nothing happens.

What could be causing these issues? I think it might be some missing package or some missing patch I left behind, but so far I got no clue.

Thanks in advance!

---

### Post by Bucky Ball on 2016-01-11
*Thread moved to **Arch and derivatives**.*

---

### Post by QDR06VV9 on 2016-01-11
> [COLOR=#000000]What could be causing these issues? I think it might be some missing package or some missing patch I left behind, but so far I got no clue.[/COLOR]

Hi sollidsnake
I have spent 2 days trying to the same, The Wiki has the best info to get the job done though..(with a little trial and error)LOL


Installation
> Warning: Installing Unity means that many official packages will be replaced with patched Ubuntu versions. Be careful to check the resulting package conflicts.
Unity can be installed on Arch Linux from an unofficial repository or alternatively from source.
From the unofficial repository
Add the Unity-for-Arch repository. Available packages are listed on GitHub. It is recommended to install the freetype2-ubuntuAUR package.
Additional packages are available from Unity-for-Arch-Extra - see GitHub for available packages.
From source
All of the PKGBUILDs can be browsed on the GitHub repository, where Unity-For-Arch provides a minimal working Unity shell, and Unity-For-Arch-Extra provides some additional applications, including lightdm-ubuntuAUR (LightDM with Ubuntu patches), ubuntu-themesAUR, unity-tweak-tool (a popular Unity configuration tool) and more.
Install git and navigate to a directory in which the sources can be built, then do:
```
$ git clone [https://github.com/chenxiaolong/Unity-for-Arch.git](https://github.com/chenxiaolong/Unity-for-Arch.git)
```

More info here [https://wiki.archlinux.org/index.php/Unity](https://wiki.archlinux.org/index.php/Unity)
For me it was not worth the effort..I will watch this thread to see your thoughts and progress.:D
Kind Regards

---

### Post by sollidsnake on 2016-01-11
> **runrickus said:**
> Hi sollidsnake
I have spent 2 days trying to the same, The Wiki has the best info to get the job done though..(with a little trial and error)LOL
For me it was not worth the effort..I will watch this thread to see your thoughts and progress.:D
Kind Regards

I'm also almost giving up, that's why I'm trying asking for help in forums. I've got some projects to work on and I might leave this behind, at least for now. What kills me it's that everything is working, there's only these two issues now.
But I'll still try a little further. I'll post here if I make any progress.

Thanks. :D

---

### Post by QDR06VV9 on 2016-01-11
> **sollidsnake said:**
> I'm also almost giving up, that's why I'm trying asking for help in forums. I've got some projects to work on and I might leave this behind, at least for now. What kills me it's that everything is working, there's only these two issues now.
But I'll still try a little further. I'll post here if I make any progress.

Thanks. :D
Thanks for the update:D
I got it to build fine, the only problem comes in when there are updates and then after a restart Unity is broke again](*,)
But when i test things like this I have another DM to fallback on..
Here is hoping that you are more successful than i was..:cool:
Regards

---

### Post by sollidsnake on 2016-01-11
It's broken because the current packages in Unity-for-Arch are out-dated. You gotta update them to the xenial version. But it seems there's been a lot of changes and new packages in xenial. I even had to install mir to build some packages. There's a lot of work to be done, but first we gotta fix these issues. :)
Also, you gotta use lightdm to launch unity, otherwise somethings may not work.

---

### Post by QDR06VV9 on 2016-01-11
> **sollidsnake said:**
> It's broken because the current packages in Unity-for-Arch are out-dated. You gotta update them to the xenial version. But it seems there's been a lot of changes and new packages in xenial. I even had to install mir to build some packages. There's a lot of work to be done, but first we gotta fix these issues. :)
Also, you gotta use lightdm to launch unity, otherwise somethings may not work.
Yes you are right the current packages in Unity-for-Arch are out-dated.
But with all the changes going on with Xenial you also will get a broken DM
I had better luck with using the Wily Builds.
[COLOR=#000000][FONT=Tahoma]**It looks like installing unity will always be an experiment that won't hold up, since there is no active repos which would maintain updates.**
More Info [/FONT][/COLOR][http://forum.unity3d.com/threads/unity-on-arch-manjaro-linux.350315/](http://forum.unity3d.com/threads/unity-on-arch-manjaro-linux.350315/)
EDIT: I could use the MDM also so either will work lightdm or mdm, but GDM will Not Work..

---

### Post by sollidsnake on 2016-01-11
> [COLOR=#000000][FONT=Tahoma]**It looks  like installing unity will always be an experiment that won't hold up,  since there is no active repos which would maintain updates.**
I have hope. Canonical is porting unity to qt5/mir and hopefully it will be more portable than unity on x11/compiz.[/FONT][/COLOR] So maybe a **yaourt -S unity8** will be enough in a not-so-long-I-hope future.
But in case unity8 is a "mess" just like current unity, we should do the repository approach, that worked for me for almost 3 years. There was a break now and then but it wasn't hard enogh to fix. And those breakes probably could be fixed by adding the breaker package to the repository.

---

### Post by QDR06VV9 on 2016-01-11
> **sollidsnake said:**
> I have hope. Canonical is porting unity to qt5/mir and hopefully it will be more portable than unity on x11/compiz.[/FONT][/COLOR] So maybe a **yaourt -S unity8** will be enough in a not-so-long-I-hope future.
But in case unity8 is a "mess" just like current unity, we should do the repository approach, that worked for me for almost 3 years. There was a break now and then but it wasn't hard enogh to fix. And those breakes probably could be fixed by adding the breaker package to the repository.
I am glad your are more resilient then I am, Kudos to you:D
I just noticed this..
> [COLOR=#000000]2. Themes are not applied. I tried changing the theme in gnome-tweak-tool but nothing happens.[/COLOR]

I also had Mate installed so I just used Appearance Preferences from Mate to Change the Themes, Logged out and Back in to Unity.
This adventure will keep you on toe's for quite some time;)
But Hey this is the best way to Learn and Grow.
Cheers

---

### Post by sollidsnake on 2016-01-12
> **sollidsnake said:**
> 
1. Menus are duplicated. When I open a program, I get duplicated menus - it's shown both on global menu bar and locally the window.

I found out that this also happens on the xenial daily build, so it's not an archlinux specific issue. I just realized that xenial is under heavy development I think I can only wait until it's more stable to keep on going with unity under arch.

---

