---
title: "How do I get gtk2"
date: 2007-03-19
forum: Absolute Beginner Talk
---

### Post by sneffers on 2007-03-19
Hi, I'm an absolute begginer to ubuntu but I'm kinda getin' the feel of it and I like that it is open source. I like the themes and I also like the ones on line but they are labeled for gtk2. I'm not sure what that means but I think it changes the controls and buttons and stuff. Beryl I would like better but I think that will crash and it's not for dapper which is what I am using. I have a gtk2 theme installed but It should have other options for colors I think. Can someone please tell me how to get Gtk2?

---

### Post by floke on 2007-03-19
You can get them all through the synaptic package manager.
Go to System/Administration/Synaptic Package Manager and do a search for GTK

Enjoy

---

### Post by mcduck on 2007-03-19
I'm not quite sure what you actually want. If you are tunning Ubuntu with /default) gnome desktop you already have GTK. That's what all your programs use to draw their interfaces to the screen. Beryl is completely different thing, it has nothing to do with how your programs look like, it only manages window frames and moving windows (+ lots of eyecandy & effects).

If you want different kind of theme for your applications just download one you like from [http://gnome-look.org/]("http://gnome-look.org/").

---

### Post by sneffers on 2007-03-19
well on gnome-look.org there are themes that are labled as gtk1/themes and gtk2/themes. don't I need to get something for the gtk2 themes to be compatible with my computer. I have Linsta (a vista theme) and in the package it shows different colors for borders and panels and stuf but I don't know how to change that. I thought you had to have like a different manager or something compatibility file for gtk2.

---

### Post by kerry_s on 2007-03-19
Make sure you install> gtk2-engines-pixbuf

You can install it with synaptic or command line.

synaptic:
press alt+F2 type> gksu synaptic

command-line:
sudo apt-get install gtk2-engines-pixbuf


Most themes use that engine but fail to mention you need it.

---

### Post by kerry_s on 2007-03-19
> **sneffers said:**
> well on gnome-look.org there are themes that are labled as gtk1/themes and gtk2/themes. don't I need to get something for the gtk2 themes to be compatible with my computer. I have Linsta (a vista theme) and in the package it shows different colors for borders and panels and stuf but I don't know how to change that. I thought you had to have like a different manager or something compatibility file for gtk2.

Gtk1 themes is for old applications that still use gtk1, most app's are gtk2. Gtk2 is already part of your system, it's a library that applications follow to get a certain look and feel/function.

---

### Post by craigyjack on 2007-03-20
Hi,

I am having basically the same problem. I have a theme that I really like, and it comes in several different colors. But when I install the theme in Ubuntu's theme manager (System>Preferences>Theme) it only installs one color (the red, which I do not like at all). I am wondering how I can get the Theme manager to realize all of the colors so I can implement another color.

The theme is Onux, it is found here [http://gnomethemes.org/2006/10/08/onux/](http://gnomethemes.org/2006/10/08/onux/)

I would appreciate it if someone could fill me in on how to get the theme using the other colors. I am a total noob currently.

Thanks,
Craig

---

### Post by Ek0nomik on 2007-03-20
> **craigyjack said:**
> Hi,

I am having basically the same problem. I have a theme that I really like, and it comes in several different colors. But when I install the theme in Ubuntu's theme manager (System>Preferences>Theme) it only installs one color (the red, which I do not like at all). I am wondering how I can get the Theme manager to realize all of the colors so I can implement another color.

The theme is Onux, it is found here [http://gnomethemes.org/2006/10/08/onux/](http://gnomethemes.org/2006/10/08/onux/)

I would appreciate it if someone could fill me in on how to get the theme using the other colors. I am a total noob currently.

Thanks,
Craig

Try to extract the .tar.gz file.  Than move the Onux-Blue folder into ~/.themes

That should do the trick, and ou should be able to find it under Themes.  :)

---

### Post by kerry_s on 2007-03-20
> **craigyjack said:**
> Hi,

I am having basically the same problem. I have a theme that I really like, and it comes in several different colors. But when I install the theme in Ubuntu's theme manager (System>Preferences>Theme) it only installs one color (the red, which I do not like at all). I am wondering how I can get the Theme manager to realize all of the colors so I can implement another color.

The theme is Onux, it is found here [http://gnomethemes.org/2006/10/08/onux/](http://gnomethemes.org/2006/10/08/onux/)

I would appreciate it if someone could fill me in on how to get the theme using the other colors. I am a total noob currently.

Thanks,
Craig

For the one from the link, you need to untar it and just copy or move them to ~/.theme

Got beat :)

---

### Post by craigyjack on 2007-03-20
Thanks guys!

I shall do that. I was just dropping the tar right in the theme perferences. I'll extract it so I can get each color.

Thanks,
Craig

---

### Post by sneffers on 2007-03-20
Mine doesn't have other tar.gz files in the actual package. The theme is called LiNsta 3 and is at gnome-look.org

---

### Post by sneffers on 2007-03-21
Alright everybody, thanks for helping me. I figured out how to change the color but I just decided to forget vista 'cause vista is stupid. But what I had to do was go into a gtkrc file and change some words so it used a differnt color scheme that was located in the same file. Why didn't I think of that before. But I still have one mor question: Do you think I would be able to get beryl or emerald on my computer? I tried a composite manager once, but I had to restart the x server and i couldn't get my computer to turn back into ubuntu so I had to reinstall. That's why I want beryl or emerald 'cause they look cool. Oh yeah, what's compiz?

---

