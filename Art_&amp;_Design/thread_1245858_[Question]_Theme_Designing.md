---
title: "[Question] Theme Designing"
date: 2009-08-21
forum: Art &amp; Design
---

### Post by adhika_rexuss on 2009-08-21
[FONT="Tahoma"]
Hi all,

I'm really a newbie in theme designing and would like to try to design my own theme.

I hope I'm asking this in the right place.

I used to download themes from gnomelook.org site.
Basically, we can see on the left menu there are some menus like GTK 1.x, GTK 2.x, Metacity, and GDM Themes.

I've read the programming in GTK 2.x which requires some basic or maybe advance knowledge on C or C++ programming from this [website]("http://library.gnome.org/devel/gtk-tutorial/stable/").

I've taken a look on settingup Metacity which is using XML from this [website]("http://developer.gnome.org/doc/tutorials/metacity/metacity-themes.html").

As for me, designing Metacity would be something I can understand easily as compared to GTK 2.x.

After checking on those 2 documents, I'm more curious and may be some of you can answer my curiosity:
[LIST=1]
[*]Do GTK 2.x and Metacity tightly related?
[*]I wanted to create a them which is similar like [this]("http://www.gnome-look.org/content/show.php/Simple-Slim?content=68772")because I like the thin border. What can I use to do this? (GTK 2.x or Metacity?)
[*]Everytime I check on GTK 2.x on gnomelook.org it is always about scrollbar, checkbox, drop down menu and etc. Is this what GTK 2.x is all about?
[*]I can see the some of the people there can even change the Ubuntu log in the Application menu where is this done? (GTK 2.x or Metacity?)
[/LIST]

I still have lots of curiosities but I think I have to stop it right there for a moment.
Your answers are highly appreciated.

Thank you,
Adhika
[/FONT]

---

### Post by mcduck on 2009-08-21
Writing *GTK themes* doesn't require any programming. Writing *GTK theme engines* does.. :)

GTK themes are what change the appearance of your applications, Metacity themes change the window borders. So they are not related (apart from Metacity theme's ability to pick some colors from your GTK theme), but you need both to theme your desktop.

(GTK1 is very old, you rarely see any programs using it any more. GTK2 is what pretty much every program on Gnome desktop is using)

Login window is changed by GDM themes (GDM being the program that handles the login).


So the answers to your questions:
[B]
1. Do GTK 2.x and Metacity tightly related?[/B]
No, they are separate things that are both used on your desktop.
[B]
2. I wanted to create a them which is similar like thisbecause I like the thin border. What can I use to do this? (GTK 2.x or Metacity?)[/B]
Metacity. GTK has nothing to do with window borders.

**3. Everytime I check on GTK 2.x on gnomelook.org it is always about scrollbar, checkbox, drop down menu and etc. Is this what GTK 2.x is all about?**
Yes. GTK is the toolkit used by programmers to create the user interfaces for programs. GTK themes change how the programs look like.

**4. I can see the some of the people there can even change the Ubuntu log in the Application menu where is this done? (GTK 2.x or Metacity?)**
Neither one. GDM login screen is themed by using GDM themes.

The best way to star learning how to create the themes is to take some existing theme you like, make a copy of it, open it's files and start changing things.

---

### Post by adhika_rexuss on 2009-08-21
Hi mcduck,

Thanks a lot for your answer.
I really have to appology on my fourth question.

What I'm trying to ask was:
4. I can see some of the people there can even change the Ubuntu logo which sits next to the Application menu. Where can this be done? (GTK 2.x or Metacity?)
Can I do it with my current theme?

Thank you,
Adhika

---

### Post by mcduck on 2009-08-21
> **adhika_rexuss said:**
> Hi mcduck,

Thanks a lot for your answer.
I really have to appology on my fourth question.

What I'm trying to ask was:
4. I can see some of the people there can even change the Ubuntu logo which sits next to the Application menu. Where can this be done? (GTK 2.x or Metacity?)
Can I do it with my current theme?

Thank you,
Adhika
No need to apologize, questions are what these forums are for.. :)

The icon in the menu applet comes from your icon theme. If you want to change that icon independently from the rest of the theme, just browse through the theme's directories and replace the image with your own.

Look for icon called "start-here.svg", it's usually located in scalable/places/-directory inside the icon theme's directory. If you are using themes that come with Ubuntu you'll find the icon themes in /usr/share/icons, abd te themes you have installled yourself will be in ~/.icons.

(note that there will be one actual image, and then many links to the same image with different names. Just find the actual image and replace that, no need to touch the links)

---

### Post by adhika_rexuss on 2009-08-23
Hi mcduck, 

in gconf editor, I can see toolbar_icons_size in /desktop/gnome/interface/toolbar_icons_size.

Do you know what is this affecting? I've been looking for this in google but so far I cannot find any good explanation for it.
Can you point me a documentation I can learn from?

Thank you,
Adhika

---

### Post by mcduck on 2009-08-23
That will switch between two possible icon sizes (and spacing) in all your GTK program's toolbars.

Like the keys description says, you can switch between "small-toolbar" or "large-toolbar".

Just try it yourself and you'll see the difference. :)

---

### Post by adhika_rexuss on 2009-08-23
Hi mcduck,

if you look at the picture below, what I was thinking of the small tool-bar is the one in the blue box. Does this affected by the setting of toolbar_icons_size in gconf?
[IMG]http://ubuntuforums.org/attachment.php?attachmentid=125931&stc=1&d=1251034609[/IMG]
I also wanted to set the height of the one in the green box to be smaller than that. Can this be done?

One other thing, if you look at the picture below:
```

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=125932&stc=1&d=1251034609[/IMG]
 

```
is it possible to make the ubuntu logo smaller so I can reduce the panel size at least 20 px or if possible 18 px which is the smallest size?

Also, I've read some of documentations on modifying the theme, especially the metacity theme from the XML file. I will try that.
As you can see, I really like to use the Metabox window border. I found out that this window border is light weight.

Thanks,
Adhika

---

### Post by mcduck on 2009-08-23
Yes, the toolbar_icon_size changes the are you have marked in blue. It doesn't really change the icons into much smaller ones, but still makes the toolbar a bit more compact.

Apart from that, the spacing of widgets comes from your GTK2 theme, so if you want to change the height of the area marked with green you'll need to edit the GTK2 theme to use less padding for widgets. Or find a theme that's already more compact.

To make the menu applet's icon smaller just replace the original icon image with a smaller one.

You should be able to make the panel as small as you like, as long as the menu applet's icon and your text size are small enough. Other applets than the menu applet should be able to scale their icons automatically.

---

### Post by adhika_rexuss on 2009-08-23
Hi mcduck, 

thanks for the enlightment. Speaking of Menu applets, do you mean that I have to change the whole icon sizes which resides under Applications, Places and System in order to have the panel height that I desired?

Thanks,
Adhika

---

### Post by mcduck on 2009-08-23
> **adhika_rexuss said:**
> Hi mcduck, 

thanks for the enlightment. Speaking of Menu applets, do you mean that I have to change the whole icon sizes which resides under Applications, Places and System in order to have the panel height that I desired?

Thanks,
Adhika

No, only the logo you see in the panel.

---

### Post by adhika_rexuss on 2009-08-24
Hi mcduck, 

I finally made it by following the clues from this [thread]("http://ubuntuforums.org/showthread.php?t=1214812").
I replaced the start-here.png in /usr/share/icons/Tangerin/24x24/places/ with the one from /usr/share/icons/Tangerin/16x16/places/

What I need to know is which configuration that points gnome to pick the start-here.png logo inside /usr/share/icons/Tangerin/24x24/places/ folder?

Thank you,
Adhika

---

### Post by mcduck on 2009-08-24
> **adhika_rexuss said:**
> Hi mcduck, 

I finally made it by following the clues from this [thread]("http://ubuntuforums.org/showthread.php?t=1214812").
I replaced the start-here.png in /usr/share/icons/Tangerin/24x24/places/ with the one from /usr/share/icons/Tangerin/16x16/places/

What I need to know is which configuration that points gnome to pick the start-here.png logo inside /usr/share/icons/Tangerin/24x24/places/ folder?

Thank you,
Adhika

If you replace the correct image, it will be used automatically (as long as you are using the theme in which you replaced the image).

(in the root of every icon theme you'll find a text file called "index.theme" which tells what directories belong to the theme, and icon themes from which additional icons should be inherited)

---

### Post by adhika_rexuss on 2009-08-24
Hi mcduck, index.theme doesn't show the default folder that will be used for the start-here.png. Does gnome automatically choose the icon from 24x24 by default? is there any other file that we can modify so the default size for ubuntu logo will be 22x22 or 16x16 for intance?

---

### Post by mcduck on 2009-08-25
> **adhika_rexuss said:**
> Hi mcduck, index.theme doesn't show the default folder that will be used for the start-here.png. Does gnome automatically choose the icon from 24x24 by default? is there any other file that we can modify so the default size for ubuntu logo will be 22x22 or 16x16 for intance?

No, like I said it only shows directories, and doesn't define each individual icon. They are simply based on using standard names for directories and icons. It's up to programs to pick the icons they want.

Pretty much all programs and panel applets automatically use smaller/bigger icons based on how much space they have available. Your only problem here is that the Menu Bar-applet doesn't do that (and doesn't have an easy way to select icon independently from the icon theme, like all the other menu applets have).

---

### Post by adhika_rexuss on 2009-08-25
sorry, I erased my previous post. this thread is not ready for closing as the tittle is theme designing.

---

### Post by adhika_rexuss on 2009-10-22
Hi mcduck, do you know how I can use [this]("http://www.gnome-look.org/content/show.php?content=112398&forumpage=2") GTK 2.x theme?

---

### Post by mcduck on 2009-10-22
> **adhika_rexuss said:**
> Hi mcduck, do you know how I can use [this]("http://www.gnome-look.org/content/show.php?content=112398&forumpage=2") GTK 2.x theme?

First rename the package you downloaded so that the extension is ".tar.gz" instead of the ".gz" it now is. Then extract the contents of the package, and inside you'll find 4 more .tar.gz packages and userchrome.css file.

Three of the packages are different variations of the theme, and you should be able to install them in the normal way (open System/Preferences/Appearance and drag&drop the package into the Theme tab).

The fourth package contains Emerald themes, which you can install with the Emerald Theme Manager if you are using Emerald.

The userChrome.css file goes to ~/.mozilla/firefox/*yourprofile*/chrome/

---

