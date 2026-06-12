---
title: "Aldabra (Adwaita GTK2 theme)"
date: 2011-05-31
forum: Art &amp; Design
---

### Post by ceramicm on 2011-05-31
[Aldabra]("http://en.wikipedia.org/wiki/Aldabra_giant_tortoise") is a GTK2 theme that uses the Murrine and Pixmap engines to mimic the look of Adwaita, the default GNOME 3 theme.

The goal of this theme is to provide [visual consistency]("https://bugzilla.gnome.org/show_bug.cgi?id=646556") between GTK2 and GTK3 applications. It is a work in progress: over the next few days, I hope to add accurate buttons and to fix application-specific issues.

Anyone is welcome to rename, package, or otherwise distribute the theme (in whole or in part). Constructive feedback is greatly appreciated.

*Edit*: Aldabra is now available on [GNOME-look.org]("http://GNOME-Look.org/content/show.php?content=142247").

---

### Post by murderslastcrow on 2011-05-31
Sort of related, if any Arch users read this thread, a package is available from AUR. [https://aur.archlinux.org/packages.php?ID=49459]("https://aur.archlinux.org/packages.php?ID=49459")

P.S. It would be simpler to package if the file were a .tar.gz or .tar as opposed to a .zip file- it may help me keep the file up to date more easily since I could directly source your gnome-look file. And if the version number is in the filename that's even better, but here I am being a perfectionist once again. XD Great job, I think this is gonna' get pretty popular over the summer.

---

### Post by ceramicm on 2011-05-31
Uploaded a .tar.gz to GNOME-look. File contents have not changed, only archive format. Could someone verify that the file can still be downloaded and uncompressed? I have had trouble recently with .tar.gz files in Fedora 15.

Thanks murderslastcrow, for uploading Aldabra to AUR.

---

### Post by murderslastcrow on 2011-05-31
Thanks for changing it- how very odd, though. It says it's not gzipped and gives an error, but if I just renamed it from tar.gz to tar it uncompresses just fine. So maybe compressing to a tar would be the way to go for now, since I can't open the tar.gz. I can confirm it on several different distros, so I don't think it's specific to one of us.

So yeah, .tar is probably the easiest route to go. And you're welcome- hopefully we can get an official Adwaita GTK 2 theme sometime in the near future. You know, before there are no more GTK 2 applications. XD Keep up the good work.

---

### Post by ceramicm on 2011-05-31
New version (0.5.1) attached to [first post]("http://ubuntuforums.org/showpost.php?p=10884199&postcount=1") and on [GNOME-look.org]("http://GNOME-Look.org/content/show.php?content=142247"). Fixed expanders and changed archive format to .tar because of problems uncompressing .tar.gz.

*Edit*: Another new version (0.5.2) in the same places. Fixed Firefox menubar selected text color.

---

### Post by ceramicm on 2011-05-31
Someone asked about native Firefox tabs on the Aldabra GNOME-look page. If anyone here is interested: First, unselect "Tabs on Top" in Firefox. Then, create a userChrome.css file in $HOME/.mozilla/firefox/[profile].default/chrome. Paste this ([http://pastebin.com/HEqfuyCi](http://pastebin.com/HEqfuyCi)) into the userChrome.css file and restart Firefox.

The active tab is overlapped on the right, I'm still working on that.

---

### Post by murderslastcrow on 2011-05-31
Wow- didn't know we could change the tabs in Firefox, that's great. Thanks for keeping us updated- things seem to be working very well now. Just a few modifications and you could probably call this a 0.9, if not a 1.0. :D Thanks for devoting your time to this. You're obviously pretty talented at adapting themes.

---

### Post by ceramicm on 2011-05-31
Thanks! New version (0.6) includes Adwaita styled checkboxes and radiobuttons. They are not applied perfectly yet. Please let me know if you find regressions.

---

### Post by murderslastcrow on 2011-05-31
Radio buttons and checkboxes are looking sweet. Aside from the button widget, what else is left to do from a visual standpoint?

---

### Post by ceramicm on 2011-06-01
I don't know of anything else besides buttons and app-specific tweaks. If anyone notices something that needs work, please comment.

I uploaded a new version of the Firefox userChrome.css [here]("http://pastebin.com/znJTpuHm"). Not much has changed. I added the Adwaita toolbar background and resized some elements. Still havent't figured out how to fix tab overlap. Screenshot attached.

---

### Post by murderslastcrow on 2011-06-01
Wow- Firefox is lookin' good! I haven't found many applications that seem to need any specific tweaks, but again, I could just have a really bad eye for what would use a change.

By the way, looks like you've 'earned some huge hero points' according to this post (at the end).

[http://linuxart.com/log/archives/2011/05/31/adwaita-gnome-3-theme-for-chrome/]("http://linuxart.com/log/archives/2011/05/31/adwaita-gnome-3-theme-for-chrome/")

Told you it'd catch on fast.

---

### Post by mxt on 2011-06-01
> **ceramicm said:**
> I don't know of anything else besides buttons and app-specific tweaks. If anyone notices something that needs work, please comment.

In several applications (geany, tomboy, gedit-gtk2) the toolbar has no lower border. Advaicium solves this by adding a lower border to toolbar.png, and the result is pretty good IMHO.

---

### Post by ceramicm on 2011-06-01
[QUOTE=mxt]In several applications (geany, tomboy, gedit-gtk2) the toolbar has no lower border. Advaicium solves this by adding a lower border to toolbar.png, and the result is pretty good IMHO.[/QUOTE]
Thanks for pointing this out! I just uploaded a new version (0.6.1) that adds the lower border and also better applies checkboxes and radiobuttons.

[QUOTE=murderslastcrow]By the way, looks like you've 'earned some huge hero points' according to this post (at the end).

[http://linuxart.com/log/archives/201...me-for-chrome/]("http://linuxart.com/log/archives/2011/05/31/adwaita-gnome-3-theme-for-chrome/")

Told you it'd catch on fast.[/QUOTE]
Hah, that's really cool.

Now that the theme has stabilized somewhat, I'll probably ask in #gnome-design about the plan for visual consistency in GNOME 3.2. I skimmed the [GNOME 3.2 Features Page]("http://live.gnome.org/ThreePointOne/Features"), but didn't find anything relevant.

---

### Post by Venemo on 2011-06-01
It seems that this theme looks broken in Qt applications.

---

### Post by mxt on 2011-06-01
> **ceramicm said:**
> If anyone notices something that needs work, please comment.

The only applications I found were the toolbar looks pretty bad are eclipse and synaptic.

---

### Post by ceramicm on 2011-06-01
[QUOTE=Venemo]It seems that this theme looks broken in Qt applications.[/QUOTE]
Can you give me a specific application or two to test? Which Qt apps are commonly used in GNOME?

[QUOTE=mxt]The only applications I found were the toolbar looks pretty bad are eclipse and synaptic.[/QUOTE]
Ok, I'll look at them. Thanks.

*Edit*: New version (0.6.2) adds a gVim-specific fix.

---

### Post by murderslastcrow on 2011-06-01
Which Qt applications? Minitube, Minitunes, and VLC all look pretty accurate to me, but assuming you're using QGtkStyle for the theme compatibility, it may look distorted in any variety of applications I haven't tested (like any of the KDE applications).

It'd be good to have some target to more clearly see what's wrong, although it's not entirely possible for themers to control how QGtkStyle translates the theme.

---

### Post by jtfolden on 2011-06-01
This may have gotten lost in the other thread but I was wondering if it were possible at all to apply the toolbar background to Banshee?

---

### Post by ceramicm on 2011-06-01
[QUOTE=jtfolden]This may have gotten lost in the other thread but I was wondering if it were possible at all to apply the toolbar background to Banshee?[/QUOTE]
I worked on this earlier today actually. I attached a screenshot showing my progress so far. Without getting too technical, Banshee uses custom widgets that make things difficult. I've looked at the Banshee source code and other themes, and--as far as I know--no one has perfected Banshee toolbar themeing yet.

The author of Zukitwo (one of the most popular GTK3 themes on GNOME-look) says this: ([*Source*]("http://GNOME-Look.org/content/show.php?content=140562&forumpage=2"))[QUOTE=lassekongo83]Banshee doesn't seem to use a standard GtkToolbar. Every fix I've tried doesn't work.[/QUOTE]
I'll keep trying, and I'll keep you updated.

---

### Post by Venemo on 2011-06-01
> **ceramicm said:**
> Can you give me a specific application or two to test? Which Qt apps are commonly used in GNOME?

I tend to use Konversation (the best IRC client ever) on my Gnome. Here is a screenshot: [http://i52.tinypic.com/2hn46cw.png](http://i52.tinypic.com/2hn46cw.png)

At my first glance, the scrollbar looks very ugly (nowhere near how it should look), and the tab control is also a bit off. (And the edges of the tabs look quite ugly.)

> **murderslastcrow said:**
> Which Qt applications? Minitube,  Minitunes, and VLC all look pretty accurate to me, but assuming you're  using QGtkStyle for the theme compatibility, it may look distorted in  any variety of applications I haven't tested (like any of the KDE  applications).

Yes, I do use QGtkStyle, and I've used it with a wide variety of Gtk themes, so I believe it would be possible to make it compatible.

> **ceramicm said:**
> Banshee uses custom widgets that make things difficult. I've  looked at the Banshee source code and other themes, and--as far as I  know--no one has perfected Banshee toolbar themeing yet.

Banshee has an IRC channel on GimpNet - I think it would be worth to ask its authors for help.

---

### Post by Venemo on 2011-06-01
I also asked the guys in #gnome-design (at GimpNet) whether they would be interested in taking your theme into upstream.
They were very interested. I think you should really contact them. :)

---

### Post by jtfolden on 2011-06-01
> **Venemo said:**
> I also asked the guys in #gnome-design (at GimpNet) whether they would be interested in taking your theme into upstream.
They were very interested. I think you should really contact them. :)

I saw further discussion of this on at least one of the mailing lists today, as well, with the suggestion it be brought upstream. :)

---

### Post by murderslastcrow on 2011-06-01
Oh, hopefully it can be fixed for Konversation. I haven't been able to reproduce the issue for any of the KDE applications I've installed- it would be nice to know what widget is used for the grey areas and narrow down which widget/color is being translated a bit closer.

So far as I know it should be possible to do a modification specific to a certain application. Anyway, despite the theme engine dependencies (very few and common, but still there), I would love to see this bundled in Gnome 3.2 if there are no other plans.

---

### Post by ceramicm on 2011-06-02
Ok, here's my to do list:
[LIST]
[*]Fix buttons.
[*]Look into the [Firefox theme]("http://img541.imageshack.us/img541/3728/firefoxgnome2.png") designed by Patrick Ulbrich (pulb) (discussed [here]("http://linuxart.com/log/archives/2011/05/31/adwaita-gnome-3-theme-for-chrome/")).
[*]Work on Unity panels, Konversation scrollbars and tabs, Banshee toolbars, Synaptic toolbar handles, Emacs scrollbars, and pgAdmin3 tabs.[/LIST]

Later today, I will ask about Banshee toolbars in #banshee (good idea, Venemo, thanks!), and I will ask about the plans for visual consistency in Gnome 3.2 in #gnome-design.

[QUOTE=jtfolden]I saw further discussion of this on at least one of the mailing lists today, as well, with the suggestion it be brought upstream.[/QUOTE]
Do you remember which list? I'd like to read the thread, if you can find it again.

Thanks, everyone, for the feedback and support. It's very encouraging!

---

### Post by kingofspades8 on 2011-06-02
How come when I install it says it won't look as intended because 'Adwaita' is not installed?  I tried installing Adwaita but wasn't successful...

---

### Post by murderslastcrow on 2011-06-02
Ah, does the theme link to the current Adwaita GTK 3, now? That may be why, but I remember it including an independent GTK 3 when I last checked. Where did you try to install Adwaita from, exactly?

---

### Post by kingofspades8 on 2011-06-02
Actually I couldn't find a link to the actual Adwaita, only Adwaita-improved.  I remember finding one the other day on some Debian site but I can't find it now.  Could you provide a link?

---

### Post by kingofspades8 on 2011-06-02
Ok I found it:

[http://rpm.pbone.net/index.php3/stat/4/idpl/15770012/dir/fedora_1/com/adwaita-gtk3-theme-3.0.1-1.fc15.x86_64.rpm.html](http://rpm.pbone.net/index.php3/stat/4/idpl/15770012/dir/fedora_1/com/adwaita-gtk3-theme-3.0.1-1.fc15.x86_64.rpm.html)

However, it was in .rpm so I used alien to convert it and then installed once it was .deb.  Maybe that wasn't the right way to go about it?

---

### Post by ceramicm on 2011-06-02
@kingofspades8, try Aldabra version (0.7) and please tell me if it solves your problem. I think the 0.6 series index.theme file had a bug.

The new version (0.7) corrects the index.theme file (there was an incorrect dependency on Adwaita), uses the official Adwaita checkboxes and radiobuttons, and removes the active tab underline. Also, if anyone is using the Firefox userChrome.css I linked to earlier, the line " background-image: url("file:///usr/share/themes/Aldabra/gtk-2.0/Assets/toolbar.png") !important;" should be changed to " background-image: url("file:///usr/share/themes/Aldabra/gtk-2.0/assets/toolbar.png") !important;"

@murderslastcrow, Aldabra still bundles Adwaita's GTK 3 files. Also, I had to upload the archive as a zip. The .tar was bigger than GNOME-look.org's upload size limit.

---

### Post by kingofspades8 on 2011-06-02
Ok I just installed 0.7 and now I'm getting a really baffling message:

"Aldabra won't work correctly because Aldabra is not installed"

I'm installing by just dragging and dropping the Aldabra folder into the appearance preferences themes tab, and it said installed succesfully.

---

### Post by ceramicm on 2011-06-02
@kingofspades8 index.theme is the problem; I'm just not 100% sure what the correct contents should be. Sorry for the difficulties.

*Edit*: As of the newest version (0.7.2), Aldabra displays as a full theme in gnome-appearance-properties without errors/warnings about missing dependencies.

---

### Post by kingofspades8 on 2011-06-02
I've installed it and now it seems to work.  However it's not listed as its own full theme under appearance preferences, but I can customize it under controls and window borders.  I'm not sure if my explanation is clear, but I can provide a screenshot.

---

### Post by ceramicm on 2011-06-02
[QUOTE=kingofspades8]I've installed it and now it seems to work. However it's not listed as its own full theme under appearance preferences, but I can customize it under controls and window borders. I'm not sure if my explanation is clear, but I can provide a screenshot.[/QUOTE]
I'm glad it's working now. Your explanation was clear, thank you. I'll look into it more.

*Edit*: As of the newest version (0.7.2), Aldabra displays as a full theme in gnome-appearance-properties without errors/warnings about missing dependencies.

---

### Post by kingofspades8 on 2011-06-02
Actually I'm starting to wonder if there's something wrong with my setup now.  I just tried installing other themes from GNOME-look and they all have that problem - I can use them through customize but they don't make new entries.  So maybe not take my feedback too seriously...

Good job on the theme itself though, looks really nice!

---

### Post by murderslastcrow on 2011-06-02
Thanks- I found a way around the zip issue, so it shouldn't be a problem at all. If you do end up linking to Adwaita, it'd be nice to know ahead of time so I can bring Adwaita in as a dependency. (I assume people will want them together)

Just under 1 MB- cool. What's the limit for gnome-look.org, by the way?

---

### Post by ceramicm on 2011-06-02
@murderslastcrow 750KB.

New version (0.7.2): Aldabra displays as a full theme in gnome-appearance-properties without errors/warnings about missing dependencies.

---

### Post by murderslastcrow on 2011-06-02
One issue that I'm not sure these theme engines can fix, but I don't think the line for dragging the menubar is at all functional. None of the GTK 2 applications I've used (tons) will allow me to click and drag the window by the menubar. I'm not sure if that's what that option is for, but if it is, it's not working here. I may need to test it out on another distribution, but for the most part I have vanilla GNOME packages.

Of course, if that's not what the option means at all, and it refers to scrubbing through menus or something like that, it would be nice if there were an option for dragging to turn it on. I'm pretty sure it wouldn't work on Qt applications, but that doesn't seem like an easy issue to get over (then again, they did it with Ubuntu's defaults, so there must be a way, while it may not be entirely theme-related).

But I know you're swamped with features as it is, so if it's not an obvious solution I don't mind waiting until the rest of the features are done. I'm actually surprised you've been so receptive to input, and grateful.

---

### Post by ceramicm on 2011-06-02
@murderslastcrow I can click the area on the menubar (to the right of the Help menu) in (eg.) Abiword. If I left-click said area and hold down my left mouse button (the cursor will become a hand), and then wiggle the mouse while still holding down the left mouse button, the window will move.

I'm not sure why it doesn't work for you. I have tested it successfully in Firefox, Abiword, Pidgin, and GIMP. I have yet to find a GTK2 app that doesn't move. I'm running Fedora 15.

---

### Post by kingofspades8 on 2011-06-02
Ok so it seems theme installing is not working well in the appearance manager, since I'm not being able to install themes on my laptop either.  I reported a bug on launchpad, but that terminal output only seems to occur with your theme, so it might be problems in the theme as well?

Link to the terminal output:

[https://launchpadlibrarian.net/72843435/gnome%20theme%20bug](https://launchpadlibrarian.net/72843435/gnome%20theme%20bug)

---

### Post by ceramicm on 2011-06-02
Here are two updated version of the userChrome.css for Firefox:
For tabs on bottom: [http://pastebin.com/CvPXTQNF]("http://pastebin.com/CvPXTQNF")
For tabs on top: [http://pastebin.com/HEqfuyCi]("http://pastebin.com/HEqfuyCi") (created by [inckie]("http://GNOME-Look.org/usermanager/search.php?username=inckie"))

@kingofspades8 I booted into an old Ubuntu partition, unzipped Aldabra, copied it to /usr/share/themes, and then opened gnome-appearance-properties. The theme showed up and I didn't get any errors in the window. I didn't check the terminal for errors, but I will later. Thanks for the feedback!

---

### Post by murderslastcrow on 2011-06-02
Hm, it may be a bug in Arch, then. I'll load up the Fedora USB and check it out. It may be an issue with the Murrine engine in Arch- does the option depend on any specific engine, or is it general enough to apply to any theme, despite the engine? Just wondering.

---

### Post by vbarnar on 2011-06-02
I've installed serveral packages and everything almost looks like Gnome3 default theme style, except my titlebar and the close button. These look really oldschool. How can i change that?

---

### Post by kingofspades8 on 2011-06-02
@ceramicn: Maybe disregard that terminal output then.  I think it's a bug in gnome-appearance-properties, since it happens with other themes as well.

---

### Post by ceramicm on 2011-06-02
[QUOTE=vbarnar]I've installed serveral packages and everything almost looks like Gnome3 default theme style, except my titlebar and the close button. These look really oldschool. How can i change that?[/QUOTE]
Could you post a screenshot, please?

---

### Post by vbarnar on 2011-06-02
as requested.

It looks nothing like the Gnome3 theme.
When i try to install the theme from the themeselecter in Natty, it says the theme will not look as intended because the required GTK+theme Aldabra was not installed

---

### Post by kingofspades8 on 2011-06-02
@ceramicn:  I'm starting to think there's both a bug in appearance manager and one with your theme.  I've summarized my findings on launchpad for now, will probably post them on Bugzilla as well:

[https://bugs.launchpad.net/ubuntu/+source/gnome-control-center/+bug/791787](https://bugs.launchpad.net/ubuntu/+source/gnome-control-center/+bug/791787)

Should I continue posting updates on this thread about this?

---

### Post by kingofspades8 on 2011-06-02
@vbarnar:  That's actually what GNOME-Shell looked like for me under Ubuntu, even with the actual Adwaita theme.

---

### Post by ceramicm on 2011-06-02
@kingofspades8 Yes, please continue to post in this thread.

I may know what the problem is. See if this works: Delete any old versions of Aldabra and then try adding the attached theme (by dragging it to gnome-appearance-properties or by copying it to $HOME/.themes or /usr/share/themes). After you have installed the version below, please select/apply it (it may not appear in the main window of gnome-appearance-properties, but it should be listed in the Details > Controls tab). Post here once you have finished that, and tell me which method you use to install it as well as any errors you encounter.

---

### Post by ceramicm on 2011-06-02
Update on Firefox userChrome.css:

[A (tabs on bottom)](http://pastebin.com/ATd9cfgb)
[B (tabs on top with gradients)](http://pastebin.com/2yXSP6uX)
[C (tabs on top without gradients)](http://pastebin.com/VrSMLpXf)

To use one of these themes, create a userChrome.css file in $HOME/.mozilla/firefox/[profile].default/chrome. Paste the theme code of your choice into the userChrome.css file and restart Firefox.

[SIZE="1"]Themes created by [inckie](http://GNOME-Look.org/usermanager/search.php?username=inckie) and myself.[/SIZE]

---

### Post by kingofspades8 on 2011-06-02
@ceramicn:  I just dl and installed it using drag and drop.  No terminal output this time, and says 

"GNOME Theme Aldabra-0.7.2.unofficial correctly installed"

However, the theme doesn't show up on the list of themes, only under the customize for other themes.

---

### Post by ceramicm on 2011-06-02
@kingofspades8 Right, that's exactly what I expected. There is a bug in the bundled Adwaita code (either in gtk-3.0 or metacity-1). For versions 0.7.2 and lower, I have not touched this code. Will you please try version 0.7.3? Thanks for your patience.

---

### Post by kingofspades8 on 2011-06-02
@ceramicn:  I install .7.3 and received the volley of terminal output, though it works just fine :D  

I've attached a screenshot.


This time there was an additional error though:

** (gnome-appearance-properties:3802): WARNING **: Invalid borders specified for theme pixmap:
        /home/alex/.themes/Aldabra/gtk-2.0/assets/scroll-background.png,
borders don't fit within the image

---

### Post by jtfolden on 2011-06-03
> **ceramicm said:**
> 

Do you remember which list? I'd like to read the thread, if you can find it again.


Here's a couple messages in Fedora "Desktop" Mailing list:
[http://lists.fedoraproject.org/pipermail/desktop/2011-May/007270.html](http://lists.fedoraproject.org/pipermail/desktop/2011-May/007270.html)
[http://lists.fedoraproject.org/pipermail/desktop/2011-May/007271.html](http://lists.fedoraproject.org/pipermail/desktop/2011-May/007271.html)

Thanks for the work on Banshee, btw, I know it's a bit of an odd one when it comes to theming.

Btw, I seem to recall a post where you indicated that you were now using the checkbox style from Adwaita but I'm not seeing those in Aldabra 7.3 here. The 'checks' are black marks on boxes with a blue background. I can't remember but I'm assuming that's the old clearlooks checkbox?

---

### Post by kingofspades8 on 2011-06-03
@ceramicn: I've attached the current terminal output, though the theme appears to be working 100% fine.

I had a quick question about themes in general.  I noticed that you included a wallpaper in the "backgrounds" folder.  When changing themes, is the wallpaper supposed to change as part of the theme?  

On a related note, do you know where I can get the background you used, but with the birds on it (the default Fedora 15 one)?

---

### Post by ceramicm on 2011-06-03
@jtfolden Thanks for the mailing-list links.

I popped in the #banshee and #gnome-design IRC channels yesterday:

#banshee (specifically bertrand) directed me to a few older [lines of code]("http://git.gnome.org/browse/banshee/tree/src/Core/Banshee.ThickClient/Banshee.Gui/BaseClientWindow.cs#n212") that "force the toolbar to look like it's just a regular part of the window since the stock toolbar look makes Banshee look ugly."  Bertrand said, " I'm not sure we still need to do it, probably need to remove that and see how it looks on various themes." So, soon it may become easier for everyone to theme Banshee.

#gnome-design (specifically jimmac) said (at least as far as I understood) that Aldabra would not be taken upstream, but that it has slightly motivated low-priority upstream theme-engine work. That's good news!

Another new Firefox userChrome.css ([http://pastebin.com/TxtGMFpj]("http://pastebin.com/TxtGMFpj")). Aligns some elements and works for either tabs on top or tabs on bottom. Thanks [inckie]("http://gnome-look.org/usermanager/search.php?username=inckie") for the update!

Checkboxes and radiobuttons should be styled like Adwaita in most applications. Can you please specify which applications are giving you the wrong checkboxes?

@kingofspades8 I'm not entirely sure what the backgrounds folder is used for. The folder included in Aldabra is copied from Adwaita. I've attached the Fedora (birds) backgrounds below.

---

### Post by jtfolden on 2011-06-03
> **ceramicm said:**
> Checkboxes and radiobuttons should be styled like Adwaita in most applications. Can you please specify which applications are giving you the wrong checkboxes?

I noticed it in Banshee and system-config-firewall off the top of my head.


> @kingofspades8 I'm not entirely sure what the backgrounds folder is used for. The folder included in Aldabra is copied from Adwaita. I've attached the Fedora (birds) backgrounds below.


I believe the backgrounds folder contains the "default" background for Gnome and GDM? At least on Fedora 15, the stripes wallpaper is not found in /usr/share/backgrounds/gnome as one would expect.

---

### Post by murderslastcrow on 2011-06-03
The included wallpaper is something they're trying to promote so themes have a few more features to them. You can always change the wallpaper individually in System Settings.

I noticed that the checkboxes work in the General Preferences tab in Banshee's preferences dialog, but if you go to Extensions on the very right, all the checkboxes have a black checkmark on a navy-bluish box. So it's probably some different kind of checkbox that certain GTK 2 applications use only in certain contexts. I'm not sure exactly where the distinction takes place in a more general sense, but it seems to be a different type of widget.

---

### Post by ceramicm on 2011-06-04
[QUOTE=murderslastcrow]I noticed that the checkboxes work in the General Preferences tab in Banshee's preferences dialog, but if you go to Extensions on the very right, all the checkboxes have a black checkmark on a navy-bluish box. So it's probably some different kind of checkbox that certain GTK 2 applications use only in certain contexts. I'm not sure exactly where the distinction takes place in a more general sense, but it seems to be a different type of widget.[/QUOTE]
Yes, I noticed the same thing. I've looked into it before without success. I may try again soon.

---

### Post by inckie on 2011-06-05
> **ceramicm said:**
> Another new Firefox userChrome.css ([http://pastebin.com/TxtGMFpj]("http://pastebin.com/TxtGMFpj")). Aligns some elements and works for either tabs on top or tabs on bottom. Thanks [inckie]("http://gnome-look.org/usermanager/search.php?username=inckie") for the update!

Nah, no need to thank me—I’m just glad to help! :)

Here’s the link to the latest version of the CSS: [http://pastebin.com/PRyitD0s]("http://pastebin.com/PRyitD0s")

By the way, I think I found a possible explanation for our pinned tabs issue [here]("http://forums.mozillazine.org/viewtopic.php?p=10675793&sid=bf73624b0879c3bc30460a5bcea76d86#p10675793").

---

### Post by Ulukai on 2011-06-05
Great work so far, this theme keeps improving with every release! 

I found 2 more problems: 
- With LibreOffice 3.4, the menubar text is white when clicked, on a light grey background, which makes it unreadable. 
- In menus, when hovering an entry, the checkbox icon stays black, while in GTK3 applications the checkbox icon becomes white.

---

### Post by kingofspades8 on 2011-06-05
@ceramicn: Thanks!  I had been looking for those backgrounds but couldn't find them anywhere, only variations.

As far as the terminal output, nobody's responded on either Gnome-bugzilla or launchpad, but I reinstalled Ubuntu and the output comes out even before installing your theme.  So it's a bug in Gnome.

There's a few small glitches I noticed on your theme, they're just little visual 'nicks'.  I thought it was dirt on my monitor at first, but I've attached a screenshot where I circled them.  Good job with the updates, keep them coming.  I'm looking forward to version 1.0!

---

### Post by ceramicm on 2011-06-06
Newest version (0.7.4) correctly colors radios and checks in menus, and gets rid of the scrollbar "invalid borders" error.

@kingofspades8 I noticed the same thing when I booted into my old GNOME2 Ubuntu install. I think it's a metacity bug. I tested the pure Adwaita metacity files (the Aldabra metacity is 99% Adwaita metacity) and had the same glitches.

@Ulukai Fixed your second issue and looked at the first. I installed LibreOffice 3.3 and menubar/menuitem colors were correct. I installed LibreOffice 3.4 and selected menubar items were colored white. I spent a good bit of time editing the gtkrc trying to fix that coloring without breaking coloring everywhere else, but I didn't find a solution and eventually gave up. Please let me know if you find a theme that has seperate colors for selected menubar items and selected menuitems in LibreOffice 3.4, and I'll update Aldabra.

---

### Post by tiper on 2011-06-06
I'm using ubuntu 10.04 and a bug I have are anoying circles over the minimize, close and 'menu' in the upper corners of the window borders

[IMG]https://lh3.googleusercontent.com/-jsR20P-gtMQ/Te0SJSCs2oI/AAAAAAAAABg/58rk0XotYoE/s800/Screenshot.png[/IMG]

---

### Post by Ulukai on 2011-06-06
> **ceramicm said:**
> Newest version (0.7.4) correctly colors radios and checks in menus, and gets rid of the scrollbar "invalid borders" error.

@Ulukai Fixed your second issue and looked at the first. I installed LibreOffice 3.3 and menubar/menuitem colors were correct. I installed LibreOffice 3.4 and selected menubar items were colored white. I spent a good bit of time editing the gtkrc trying to fix that coloring without breaking coloring everywhere else, but I didn't find a solution and eventually gave up. Please let me know if you find a theme that has seperate colors for selected menubar items and selected menuitems in LibreOffice 3.4, and I'll update Aldabra.

Thanks for the efforts, I'll keep an eye open and hope you will find it eventually.

---

### Post by thebluesgnr on 2011-06-06
> **tiper said:**
> I'm using ubuntu 10.04 and a bug I have are anoying circles over the minimize, close and 'menu' in the upper corners of the window borders

[IMG]https://lh3.googleusercontent.com/-jsR20P-gtMQ/Te0SJSCs2oI/AAAAAAAAABg/58rk0XotYoE/s800/Screenshot.png[IMG]

That's because you're using an old version of metacity. I don't know if the latest one in the 2.x branch works better, but it probably does. The theme was only tested with metacity 3.

---

### Post by Venemo on 2011-06-07
> **Ulukai said:**
> Thanks for the efforts, I'll keep an eye open and hope you will find it eventually.

This one is worth a bug report against LibreOffice 3.4, since it worked in 3.3, this is clearly a regression.

---

### Post by Ulukai on 2011-06-07
> **Venemo said:**
> This one is worth a bug report against LibreOffice 3.4, since it worked in 3.3, this is clearly a regression.

Bug 38038 opened. 

[https://bugs.freedesktop.org/show_bug.cgi?id=38038](https://bugs.freedesktop.org/show_bug.cgi?id=38038)

---

### Post by mxt on 2011-06-14
To fix toolbars in Eclipse (and other swt apps), you could change the style of "*swt*toolbar*" widgets. 

For instance I added this line:

```
widget "*swt*toolbar*" style "default"
```

---

### Post by ceramicm on 2011-06-15
@mxt Thanks! I added that line to the gtkrc (version 0.7.5).

I don't have much time to work on Aldabra in the coming weeks, but if anyone contributes fixes or enhancements, I will add them. Here is a list of things I know that still need to be done:
[LIST]
[*]buttons
[*]LibreOffice 3.4 menubar text
[*]Banshee toolbar, listview header arrow, extensions checkboxes
[*]system-config-firewall checkboxes
[*]Emacs scrollbar
[*]Konversation scrollbars & tabs
[*]Synaptic toolbar handles
[*]pgAdmin3 tabs
[/LIST]

---

### Post by jtfolden on 2011-06-15
I was just browsing the comments on a thread and noted a users photo attachment of Banshee being successfully themed (toolbar). Perhaps it might provide a clue to track down that theme?

[http://www.omgubuntu.co.uk/2011/06/beatbox-adds-album-art-sound-menu-support/#comment-226417199](http://www.omgubuntu.co.uk/2011/06/beatbox-adds-album-art-sound-menu-support/#comment-226417199)

---

### Post by ceramicm on 2011-06-15
@jtfolden The toolbar background color is changed, yes, but only because the entire window background color is changed. It (currently) cannot be changed independently, per [Bug 636523]("https://bugzilla.gnome.org/show_bug.cgi?id=636523").

---

### Post by ceramicm on 2011-06-19
A Fedora packager asked me to clarify the license of Aldabra so that it could be packaged for the Fedora repositories. After some discussion, I decided to release Aldabra under the LGPLv2+, the same license used by Adwaita. If anyone has a problem with that, please let me know. I'm not an expert on licenses.

---

### Post by murderslastcrow on 2011-06-21
Thanks for the information- I think that's the perfect license for it. It also gives the GNOME developers the future option of adopting it officially without bringing in much extra baggage.

Again, the hope would be that everyone migrates their applications to GTK 3 sooner than later to take advantage of it, but as well all know, there are still Qt3 applications flying around out there, so we'll see how things go.

Until then, this has been a pretty awesome gift to the community. Thank you again- I've honestly gotten a lot more curious about theming since this endeavor started.

---

### Post by kingofspades8 on 2011-06-22
@ceramicn:

Just wanted to say congratulations on getting your theme into the Fedora repositories!  I've been using it since it was released on both my desktop and laptop.

---

### Post by ceramicm on 2011-06-22
@murderslastcrow @kingofspades8 Thank you both for the kind words!

---

### Post by murderslastcrow on 2011-07-08
Just so everyone knows, I found out why the window dragging doesn't work in Arch- it includes vanilla gtk2 which has no patches for this support by default. Fedora and Ubuntu seem to have these patches.

An AUR package for this functionality is in the works, though, if anyone reading this is an Archer. [https://bbs.archlinux.org/viewtopic.php?pid=951944]("https://bbs.archlinux.org/viewtopic.php?pid=951944")

Looks like this theme has been packaged by default in Fedora- pretty kickin'.

---

### Post by maximo1010 on 2011-11-05
I removed my rude stuff I posted before.

I cooled down somewhat as of now and I would kindly ask you do improve as much as you can in your theme so I can import all of this.


Edit: I killed Advaicium because there's no reason to do a theme that's so freaking far behind everything, I will admit. I think it's better to start off with a new theme, Ada X (first version will be 10.0 Shooting Star) and combine all ports into one.

---

### Post by maximo1010 on 2011-11-05
(sudo rm -rf /dev/uforums/maximo1010/rudeposts/*.*)

---

### Post by maximo1010 on 2011-11-05
Congrats. I am going to have to catch up now :( *cries*

---

### Post by maximo1010 on 2011-11-05
> **mxt said:**
> In several applications (geany, tomboy, gedit-gtk2) the toolbar has no lower border. Advaicium solves this by adding a lower border to toolbar.png, and the result is pretty good IMHO.

I just screenshotted the toolbar of it including the borders.

---

