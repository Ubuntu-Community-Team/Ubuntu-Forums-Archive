---
title: "Modifying Yakuake default key"
date: 2007-05-06
forum: Absolute Beginner Talk
---

### Post by Limitlesschannels on 2007-05-06
How do i modify the default key (F12) for Yakuake.  It instantly conflicted with my new Feisty installation as that is also apparently the default search button.  Seeing as I view yakuake as as obviously more important than search, i just pulled the search option off my session default run list, but I would like it to remain F12 for whenever i need it and relocate my yakuake to my tilde (  ` or ~ ) key instead to be consistent with all the wonderous games i love and a tad more convenient that reaching to a semi-awkward F12.
If anyone could just point me to the config file for yakuake, that would be great.  I couldn't find it myself.

---

### Post by Tundro Walker on 2007-05-06
Just my 2 cents, but I'd use "tilda" instead, since it works regardless of what desktop you have.

Tilda is a quake-style command-line, and I'm so hooked on it, I have it auto-load when my computer boots.  I haven't even started a regular command-line in about 1 month, that's how much I rely on tilda.

In tilda, you can configure the usual terminal stuff, like background and text color, text bolding, transparent screen, etc, but you can also configure the dropdown speed, or just have it flip to it instantly.  I found on my older 800mhz, the animated dropdown was a bit chopped (even on a tweaked, lean-running Xubuntu install).

Other thing I've noticed with Tilda is that when using Compiz, the text gets all screwed up if you use animated dropdown.  So, personally, I switched mine off; mine just instantly shows up when I hit my quick key, which, just like in Quake, I made to be my tilda ...IE: ` / ~ ... key   (LOL!)

For a while, when I was configuring Ubuntu quite a bit, I was auto-loading a "sudo Tilda" also, hot-keyed to CTRL+`. So, for stuff I needed to do as normal user, I'd just "`" to bring up my regular console.  When I needed to "sudo" stuff as super-user, I'd Ctrl+` to bring up my super-user tilda console.  However, once I was done tweaking with Ubuntu, I stopped auto-loading the super-user one.  I keep the regular one, though, because it is useful.

When Tilda first runs, it'll show the config screen.  However, you'll probably want to view the config, then alter it.  So, mess with the config options, then save, and it loads.  If you don't like it, type "exit" and Tilda will close (like a normal terminal window).   Open a regular terminal screen, and type...

```
tilda -C
```

...which will bring up the config menu again.  Tweak with it, then save/close, and tilda will start with your changes.  If you want to mess with the config some more, then go to your regular terminal screen that you started tilda in, and CTRL+C to kill tilda in it.  Then just UP ARROW to make your terminal auto-fillin "tilda -C" again, hit Enter, and keep fiddling with the Config screen.

Note that if you type in ....

```
sudo tilda -C
```

...you'll be setting up the config for super-user's tilda screen, not your regular log in's tilda.  Likewise, typing in...

```
sudo tilda
```

...will start super-user's tilda, not your regular log in's tilda.

Ok, with it all the way you like it, you can go to "(Start) > System > Preferences > Sessions" and on the first tab called "Startup Programs", click "New", and add the Name "Tilda" and the Command "tilda" (lower-case...Linux is case-sensative).  This makes it auto-start whenever you log in for whatever session / user you're currently running.  I have mine set to auto-start hidden (you set the hidden flag in the tilda config options), so when I boot up, I don't even see it.  But, when I need it, I just slap the "`" key and it springs into action.

Hope this helps.

---

### Post by igknighted on 2007-05-06
In my experience, Yakuake is much more reliable.  So if you are using KDE, stick with Yakuake.  Tilda bogs down for no reason it seems, scroll times are bad, and it gets jumpy (even with proper video drivers installed)

---

### Post by Limitlesschannels on 2007-05-06
Hm, i just tried Tilda and it is interesting, a lot different.  That is really interesting about your sudo terminal (CTRL + "`" ) versus simple terminal ("`") hotkeys.  I agree with igknighted, though.  I prefer the look and feel of yakuake.  Tilda does seem more customizable, though, so i could probably work it to my preferences.  it looks like i might just need to work with each for a while longer.

Still, does anyone know how to modify the default key for yakuake?

---

### Post by -Chi.0 on 2007-06-02
> **Limitlesschannels said:**
> Hm, i just tried Tilda and it is interesting, a lot different.  That is really interesting about your sudo terminal (CTRL + "`" ) versus simple terminal ("`") hotkeys.  I agree with igknighted, though.  I prefer the look and feel of yakuake.  Tilda does seem more customizable, though, so i could probably work it to my preferences.  it looks like i might just need to work with each for a while longer.

Still, does anyone know how to modify the default key for yakuake?
I can totally understand what your feeling about Yakuake and it's quite simple to change the access key if your in KDE.

1st.) Press **F12 **to bring up good old Yakuake
2nd.) locate the buttons in the lower right corner of the terminal
3rd.)now you should see a [+]  ** [Downward arrow] ** [X] key\button\icon
4th.)you need to press the ** [Downward arrow] **key\button\icon to pull up the drop down. *"LoL I just said pull up the drop down"*
5th.)move you mouse cursore down to were it says **Shortcuts**
6th.)click on where it says **Change Access Key**
7th.)now you should have a **Configure Shortcuts - Yakuake Dialog** on your screen.
8th.)you can check out the screen shout in the *attachments * \\:D/
and that's it if you run KDE I will just guess that you know how to setup shortcut keys from their :)
Hope this helped out Enjoy;)

PS: *Check out this awesome project that my fellow forum members and my self are working on. What is great about it is that you can what the progress in the Ubuntu Forums.* ;)

Link --> [http://ubuntuforums.org/showthread.php?t=427011]("http://ubuntuforums.org/showthread.php?t=427011")

---

### Post by Limitlesschannels on 2007-06-04
neat.  It works in Gnome as well, you don't need to be in KDE.  I just assumed the right click menu was the extent of customizable yakuake.  it is always nice to find a plethora of other options.

---

### Post by -Chi.0 on 2007-06-05
Hey thanx for the extra info Gnome and I hope this helped out a great deal :) 
I Don't use Gnome and have used KDE for years now but i'm glad that it works on more then one window manager. That's  beauty of linux :)

---

