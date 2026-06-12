---
title: "How is this done?"
date: 2009-11-13
forum: Art &amp; Design
---

### Post by Imoen on 2009-11-13
I would like to know how to make the windows partially transparent as it is in the attached image. I see this many places but even when I install the theme it is shown in I don't get my windows to be the same.

---

### Post by Exodist on 2009-11-13
Check out Beryl @ Gnome-Look

---

### Post by Imoen on 2009-11-14
That is where I got that theme from. The problem is that when I install/apply the theme I do not get the effect. I have tried on multiple themes and get the same result.

---

### Post by Bucky Ball on 2009-11-14
You will get more help by using more descriptive thread titles in future. ;-)

---

### Post by AJB2K3 on 2009-11-14
Have you got both beryl and the theme installed?
IIRC, Right click on the tool bar and pick properties.
Some were in properties is the option to turn on the advanced options, turn them on then turn the opacity down to get semi transparent.

---

### Post by Tickborn on 2009-11-14
Hi,
I got those effects with Compiz *+ **Emerald*** for windows decoration. They are both in the repositories.
Cheers

---

### Post by coldReactive on 2009-11-14
> **Imoen said:**
> That is where I got that theme from. The problem is that when I install/apply the theme I do not get the effect. I have tried on multiple themes and get the same result.

ALT+F2 to bring up the run command,

emerald --replace

Then in Application Autostart or Sessions, whichever you have ,add the same command as a new autostarted app.

---

### Post by kholdstare on 2009-11-14
there should be a option in compiz options.

---

### Post by steveneddy on 2009-11-14
The window borders will become transparent by using emerald as the window manager.

Install fusion-icon to help you switch between compix and metacity and find the emerald setting faster and easier.

The window in the attached pic that I see that is transparent is the Gnome terminal, which can be made transparent by opening up the terminal and going to 

Edit --> Profile Preferences

go to the Background tab and click on the transparent background radio button.

Get rid of the menu chooser in terminal by right clicking inside the terminal and unchecking "Show Menubar"

Here are more of my transparency instructions if you are interested.

---

### Post by VCoolio on 2009-11-14
If you mean transparant windows like [this]("http://ubuntuforums.org/showpost.php?p=8293069&postcount=584"), you'll need to use the [murrine rgba engine]("http://www.cimitan.com/murrine/") (the svn version that is, not the one that is default in the repos). There is a [good howto here]("http://janhouse.deviantart.com/art/Gnome-quot-Aero-look-quot-tutorial-142265951").

---

### Post by coldReactive on 2009-11-14
> **VCoolio said:**
> If you mean transparant windows like [this]("http://ubuntuforums.org/showpost.php?p=8293069&postcount=584"), you'll need to use the [murrine rgba engine]("http://www.cimitan.com/murrine/") (the svn version that is, not the one that is default in the repos). There is a [good howto here]("http://janhouse.deviantart.com/art/Gnome-quot-Aero-look-quot-tutorial-142265951").

Which has experimental support with gnome global menu, sadly.

---

### Post by atleastzero on 2009-11-15
It's definitely an option that is available in Compiz. I made my Terminal transparent independant of those settings though. In the preferences for your Terminal, there are color options for the foreground (text) and the background. I set mine to white text on a black background, then have my transparency at around 40%. 
 
Hope this helps.

---

### Post by coldReactive on 2009-11-15
> **atleastzero said:**
> It's definitely an option that is available in Compiz. I made my Terminal transparent independant of those settings though. In the preferences for your Terminal, there are color options for the foreground (text) and the background. I set mine to white text on a black background, then have my transparency at around 40%. 
 
Hope this helps.

The opacity/saturation settings through compiz force you to transparent the entire window (text included.) Wish Compiz team could allow text/window transparency separate.

---

### Post by atleastzero on 2009-11-15
> **coldReactive said:**
> The opacity/saturation settings through compiz force you to transparent the entire window (text included.) Wish Compiz team could allow text/window transparency separate.
 
Oh, that would be beautiful.

---

### Post by HalfEmptyHero on 2009-11-15
Install compizconfig-settings-manager, you will find it in System > Preferences and then go to Opacity, Brightness, and Saturation. Under Windows, select New and then the + sign. If you want all programs to be transparent, change the Type from Window Class to Window Type and then type in Normal. If you only want a certain program transparent, keep the type on Window Class and then type in the name of the program.

---

### Post by coldReactive on 2009-11-15
> **HalfEmptyHero said:**
> Install compizconfig-settings-manager, you will find it in System > Preferences and then go to Opacity, Brightness, and Saturation. Under Windows, select New and then the + sign. If you want all programs to be transparent, change the Type from Window Class to Window Type and then type in Normal. If you only want a certain program transparent, keep the type on Window Class and then type in the name of the program.

And what if you don't want the text transparent too?

---

### Post by HalfEmptyHero on 2009-11-15
> **coldReactive said:**
> And what if you don't want the text transparent too?

Unfortunately not possible yet, but if you use white text on a dark background it is still readable.

---

### Post by Minsky on 2009-11-19
> **HalfEmptyHero said:**
> Install compizconfig-settings-manager, you will find it in System > Preferences and then go to Opacity, Brightness, and Saturation. Under Windows, select New and then the + sign. If you want all programs to be transparent, change the Type from Window Class to Window Type and then type in Normal. If you only want a certain program transparent, keep the type on Window Class and then type in the name of the program.

Is it possible for menu backgrounds to be transparent with just leaving the outline and menu items text visible?

---

### Post by venkatad on 2009-11-24
> **Imoen said:**
> I would like to know how to make the windows partially transparent as it is in the attached image. I see this many places but even when I install the theme it is shown in I don't get my windows to be the same.
Install comfiz settings manager, comfiz(i think if u install cairo deck that ll get u comfiz),and install emerald theme manager.

go to gnome-look.org website in the left navigation check from beryl themes.
Choose vista look, or glass like themes
 download them (ex:home/mydocuments/downloads).

open emerald manager:  system->preferences->emerald manager
once emerald opens->hit import direct to downloads folder /home/mydocuments/downloads DONE..!
make sure visual effects turned on extra or normal instead of NONE

--cheers

---

