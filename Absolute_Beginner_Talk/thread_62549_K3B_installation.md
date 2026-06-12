---
title: "K3B installation"
date: 2005-09-05
forum: Absolute Beginner Talk
---

### Post by sophtpaw on 2005-09-05
I installed K3B using synaptic. when i fired it up for the first time it told me that cdrdao was missing. So, i went back to Synaptic and installed cdrdao.

I have two questions:

1. Why did Synaptic not take care of cdrdao first, is it not a dependency issue?

More importantly,

2. How can i get K3B to launch from Applications / Sound &Video? right now i have to use Terminal to do so. I thought apt-get/synaptic automatically did that with most apps and K3B being one of the major ones?


much obliged,


--
sophtpaw

---

### Post by frodon on 2005-09-05
The K3B icon is in Debian>applications>System tools or something like that (i have a french version). However if you want to have a K3B icons in Application>Sound & Videos you can use SMEG (it's a gnome menu editor) and add yourself the icon of K3B where you want in the menu.

---

### Post by felix.rommel on 2005-09-05
Do you use Ubuntu Warty or Hoary?

Only in the newest version of Gnome 2.10 which is included in Hoary the menus are shared by Gnome and KDE. I think the Gnome version in Warty does not have the new common menu format so your KDE programs like K3B isn't visible in your Ubuntu menu.

A workaround is to add a starter to the panel on top of the screen by yourself (I have the german version so some things will be named a little bit different):

1. Right click on the panel on top and choose "Add to panel"
2. Then you get a window with a list. Choose "User defined starter" or sth. like that and you will get a dialog where you can insert the data:

Name: K3b
Command: k3b

You can also add an icon if you click on the button for symbol. Then choose a icon like

/usr/share/pixmaps/k3b.xpm

---

### Post by sophtpaw on 2005-09-05
[QUOTE=felix.rommel]Do you use Ubuntu Warty or Hoary?

Only in the newest version of Gnome 2.10 which is included in Hoary the menus are shared by Gnome and KDE. I think the Gnome version in Warty does not have the new common menu format so your KDE programs like K3B isn't visible in your Ubuntu menu.

A workaround is to add a starter to the panel on top of the screen by yourself (I have the german version so some things will be named a little bit different):

1. Right click on the panel on top and choose "Add to panel"
2. Then you get a window with a list. Choose "User defined starter" or sth. like that and you will get a dialog where you can insert the data:

Name: K3b
Command: k3b

You can also add an icon if you click on the button for symbol. Then choose a icon like

/usr/share/pixmaps/k3b.xpm[/QUOTE]

Thx Guys (frodon & rommel)

actually the latter method sounds more doable, although i don't really want it on my Panel right now. But i've never used SMEG although i'll have a look a that too. Hopefully it is intuitive enough to use for a newb like me

thx again  :grin: 

--
sophtpaw

PS
Sorry, forgot - i use Hoary 5.04 Ubuntu GNU/Linux in Gnome

---

### Post by sophtpaw on 2005-09-05
[QUOTE=frodon]The K3B icon is in Debian>applications>System tools or something like that (i have a french version). However if you want to have a K3B icons in Application>Sound & Videos you can use SMEG (it's a gnome menu editor) and add yourself the icon of K3B where you want in the menu.[/QUOTE]


I followed the Smeg route as you suggested. It is straightforward for someone like me to use, so i got excited at the prospect of experiencing the satisfaction of achievment, even in something as small as installing k3b to apps menu. However, i got this error message:

Cannot launch entry

Details: Failed to execute child process "K3B" (No such file or directory)

Ca vous dit quelquechose?

So, there it is in Apps./sound & video with icon but it won't launch  :-? 

Any further advise most welcome and needed,

--
sophtpaw

---

### Post by ScoobyDan on 2005-09-05
sophtpaw,

> Details: Failed to execute child process "K3B" (No such file or directory)

Remember that *NIX is case-sensitive, so "K3B" is different to "k3b" - are you sure the link you created in SMEG uses the correct format for the command to execute?

Daniel

PS - I apologise if you are an experienced user (just seen your post count) - I am a Ubuntu newbie, and this seems the most logical answer for your problem.

---

### Post by sophtpaw on 2005-09-05
[QUOTE=ScoobyDan]sophtpaw,



Remember that *NIX is case-sensitive, so "K3B" is different to "k3b" - are you sure the link you created in SMEG uses the correct format for the command to execute?

Daniel

PS - I apologise if you are an experienced user (just seen your post count) - I am a Ubuntu newbie, and this seems the most logical answer for your problem.[/QUOTE]


ScoobyDan, you Genius!

I presumed, wrongly that the name of a killer app like K3B would be capitalised in something like a Menu list. But i was wrong, and the thought of case-sensitivity had not even occurned to me. 

 I apologise if you are an experienced user (just seen your post count) - I am a Ubuntu newbie

Not at all! I am a total newb. Every extra day i use GNU/Linux i find out even more how much that is true. If i have a high post count, its because i am the babies of the forums crying for help alot.  ;-) 

thx again,

--
sophtpaw

---

### Post by ScoobyDan on 2005-09-05
sophtpaw,

Glad I could help!

Daniel

---

