---
title: "Software Center"
date: 2010-03-07
forum: Assistive Technology &amp; Accessibility
---

### Post by joeknoodle on 2010-03-07
I have vision problems that prevent me from reading text on bright backgrounds, so the Software Center is just one big blur.

Is there a way to change the color of the background/text for Software Center?

Also, is there a way to change the button/text colors for Software Center?

If it matters, I use the Satanic edition  for its better combination of readable colors, but it doesn't seem to work for Software Center.

I also have Gnome Color Chooser, but I can't find the specific stuff to change.

---

### Post by Swagman on 2010-03-07
Dont use the Software Centre !!

You can use Synaptic. Both apps point to the same place but software centre filters out the less popular apps.

[**GetDeb**](http://www.getdeb.net/welcome) is another location. Nice & big  & graphical

---

### Post by joeknoodle on 2010-03-07
Thanks for the reply, but I wish to be able to use the entire functionality of my system, OS.

In researching this, it does look like the Ubuntu/Gnome people just don't care about people with vision problems. I'm having the same difficulty trying to change the bright background in Gnome Planner.

Please, if any Devs are reading this, please provide some means for users to easily change background/text colors in your applications.

I really enjoy using Ubuntu, but it is utterly useless if I can't see what I'm doing. Even the high contrast color scheme is too hard to see. I need subtle differences on a dark background.

---

### Post by tacantara on 2010-03-07
From what I've read so far, the themes available by default in Ubuntu are not helping you.  Have you tried looking for darker themes at Gnome-look.org?  When you open the Appearance settings (System > Preferences > Appearance) and click on the Theme tab, a link to Gnome-look is available.  You should be able to find a theme that better suits your needs.

Meanwhile, are you able to adjust your computer's monitor (brightness and contrast) to make viewing a bit better?  How about adjusting certain existing themes, such as the high-contrast.  You can change colors, etc.  Perhaps the solution is there.

I hope these ideas are of some use to you.  Good luck :)

---

### Post by Sef on 2010-03-07
Moved to ATA.

---

### Post by themarker0 on 2010-03-08
> **joeknoodle said:**
> Thanks for the reply, but I wish to be able to use the entire functionality of my system, OS.

In researching this, it does look like the Ubuntu/Gnome people just don't care about people with vision problems. I'm having the same difficulty trying to change the bright background in Gnome Planner.

Please, if any Devs are reading this, please provide some means for users to easily change background/text colors in your applications.

I really enjoy using Ubuntu, but it is utterly useless if I can't see what I'm doing. Even the high contrast color scheme is too hard to see. I need subtle differences on a dark background.

Hi, when i get home i will pm you the theme i am using. It is quite dark, i installed it when i was very sick, and couldn't look at light. That is, if you haven't found a better one by then.

---

### Post by Sef on 2010-03-09
> Hi, when i get home i will pm you the theme i am using.

Could you please post it here, so that others who can use it may benefit from it.  Thank you.

---

### Post by ALIENDUDE5300 on 2010-03-09
> **joeknoodle said:**
> Thanks for the reply, but I wish to be able to use the entire functionality of my system, OS.

In researching this, it does look like the Ubuntu/Gnome people just don't care about people with vision problems. I'm having the same difficulty trying to change the bright background in Gnome Planner.

Please, if any Devs are reading this, please provide some means for users to easily change background/text colors in your applications.

I really enjoy using Ubuntu, but it is utterly useless if I can't see what I'm doing. Even the high contrast color scheme is too hard to see. I need subtle differences on a dark background.

I think the colors are hardcoded into the Software Center and non-changeable at the moment. Implementing a color chooser isn't difficult at all, given all the premade ones at Canonical's disposure, but many people, including the developers of the Software Center, didn't even realize that the colors were that important. It's really easy to change on the coding side though... maybe they will add a color selection feature in the future...

---

### Post by ALIENDUDE5300 on 2010-03-09
I'm going to install Qt Designer, download the [source code]("http://archive.ubuntu.com/ubuntu/pool/main/s/software-center/software-center_1.1.16.1.tar.gz"), and see if I can get some basic theming support working for people like you who are unable to use the default theme... It may take a while to get this implemented properly, but I think I know enough about coding to get some basic functionality working.

Edit: Ah... the ui files aren't Qt interface files, they're made in Glade... even easier. :)
Edit 2: Got the menu option working, just have to implement it.
Edit 3: Uploading modified ui file for the Software Center in case anyone else wants to work on this too

---

