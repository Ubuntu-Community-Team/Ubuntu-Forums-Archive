---
title: "Hey Theme Questions what do i need?"
date: 2007-12-06
forum: Absolute Beginner Talk
---

### Post by cerealtx on 2007-12-06
I know that Compiz-fusion is already installed, but what do i need to isntall themes, emerald, gnome, kde? ive used Linux before but i never got into it and now ive decided to acctually learn everything and i want to start off by making it look good ;)

---

### Post by amazingtaters on 2007-12-06
Well, you can get themes for both Compiz and gnome at gnome-look.org. I don't use Compiz because of my crappy integrated video card, but all the gnome themes I use I just pull up System>Preferences>Appearance and drag and drop the theme package onto the list and the rest is magic.

---

### Post by PeterJS on 2007-12-06
> **cerealtx said:**
> I know that Compiz-fusion is already installed, but what do i need to isntall themes, emerald, gnome, kde? ive used Linux before but i never got into it and now ive decided to acctually learn everything and i want to start off by making it look good ;)


There are two elements that go in to theming in liunx, widgets and window decoration. Window decorations are handled by the window decorator, which in your case is Emerald, Gnome defaults to using Metacity as it's window decorator, and KDE uses Kwin. You'll only ever be using one window manager at a time, so when you make changes to you window decorations it will apply to all programs.

The other element widgets depends on which widget tool kit the program was created with. There are two big tool kits, GTK (used by Gnome) and QT (used by KDE), and some smaller ones that are rarely used. Both GTK and QT are fully themeable, but if you say change your GTK theme it will only change GTK programs. If you're using the gnome desktop you can probably get way just setting your GTK theme, and if you're using KDE you can probably just set your QT theme, but if you're using a mixture of both tool kits you're going to want to find themes for each kit that will not look terrible together.

Gnome-look.org has a bunch of GTK themes you can use, while kde-look.org has a large selection of QT themes. Themes generally don't port well between the two, so it's rare to find a theme that has versions for both tool kits, but there are some common looks that are replicated for both tool kits.

I mentioned there are programs that use neither main tool kit, the first example that come to mind is VLC which uses the WXwidgets tool kit, which I think uses GTK themes, so I guess that's not the best example.

---

### Post by SolusNunquam on 2007-12-06
I'm a beginner when it comes to this, but i got my OS done by using Emerald, and finding Application themes online...I also have the extra effects enabled, cube effect etc etc. Very amazing :)

Use the Synaptic Package Manager to install Emerald (Will change your window borders. As far as everything else goes, just right click and customize! lol. 

Here's a screen of my desktop:
[http://celentian.com/Solus/Screenshot.png](http://celentian.com/Solus/Screenshot.png)

---

### Post by pointfivezero on 2007-12-06
> **SolusNunquam said:**
> I'm a beginner when it comes to this, but i got my OS done by using Emerald, and finding Application themes online...I also have the extra effects enabled, cube effect etc etc. Very amazing :)

Use the Synaptic Package Manager to install Emerald (Will change your window borders. As far as everything else goes, just right click and customize! lol. 

Here's a screen of my desktop:
[http://celentian.com/Solus/Screenshot.png](http://celentian.com/Solus/Screenshot.png)

Wow that looks fantastic - I am usually a KDE person but heck, I like what you did there!

:popcorn:

---

### Post by DutyDuty on 2007-12-06
to change emerald themes, remember to use ```
emerald --replace
```!

---

