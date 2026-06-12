---
title: "Ubuntu and Wine Questions!"
date: 2005-12-15
forum: Absolute Beginner Talk
---

### Post by lilrockerboy on 2005-12-15
Alright, so I've figured out alot more then I expected to in a few short days, but I have hit another wall. I have successfully installed Macromedia Flash and Dreamweaver into my system but if I want to run the program I have to go:

Home/.wine/c:/program files/macromedia/flash.exe
[COLOR="Red"]**Sorry if that's wrong, but I hope you understand*[/COLOR]
But when I go add a shortcut in the "graphics" tab it says the dir doesn't exist?! Any ideas?! It's just annoying to go through the folders to run a program when I could just use the link! Thanks again everyone! I really appreciate the help!

---

### Post by Sutekh on 2005-12-15
Did you create the link yourself?

When calling a directory with a space you need to use the forward slash

as in;

.../program\ files/macromedia/...

Easy way might be to use the terminal and change directory (cd) to the one you want, then copy the full path from the terminal into the link dialog box.

---

### Post by lilrockerboy on 2005-12-15
If I change the directory will that screw anything up in Wine! But thanks for the heads up with the space and forward slash thing!

---

### Post by Sutekh on 2005-12-15
If we're talking about changing the directory specified in the *link* to flash.exe (wherever it is), then there won't be any problems.

---

### Post by lilrockerboy on 2005-12-15
Perfect! I'll have to try this when I get home! Thanks again! it's funny how a free service gets you better support in both professionalism and quickness then any Microsoft crap! Awesome! Thanks, now if only I could boot Ubuntu on my laptop! Then I'll have the straight conversion. Here's another question I'm not sure if any of you have tried out the Nintendo WiFi connection with the Nintendo/Buffalo USB adaptor, but any idea if this will work in Ubuntu?!

---

### Post by brentoboy on 2005-12-15
[QUOTE=Sutekh]Did you create the link yourself?

When calling a directory with a space you need to use the forward slash

as in;

.../program\ files/macromedia/...

Easy way might be to use the terminal and change directory (cd) to the one you want, then copy the full path from the terminal into the link dialog box.[/QUOTE]

another way to allow for a space in a folder name is to enclose it in single quotes - in my opinion, it is easier to read that way...

.../'program files'/macromedia/

notice, this is a little bit different than the windows way, where you encluse the entire path in double quotes like so...

".../program files/macromedia/"

-b

---

### Post by trivialpackets on 2005-12-15
[QUOTE=lilrockerboy]If I change the directory will that screw anything up in Wine! But thanks for the heads up with the space and forward slash thing![/QUOTE]
  
Why would you change the directory and not just change the link?

---

### Post by brentoboy on 2005-12-15
[QUOTE=lilrockerboy]Perfect! I'll have to try this when I get home! Thanks again! it's funny how a free service gets you better support in both professionalism and quickness then any Microsoft crap! Awesome! Thanks, now if only I could boot Ubuntu on my laptop! Then I'll have the straight conversion. Here's another question I'm not sure if any of you have tried out the Nintendo WiFi connection with the Nintendo/Buffalo USB adaptor, but any idea if this will work in Ubuntu?![/QUOTE]

you should post a new question to the forum with this, becuase it will attract its own interest, and different types of people will read it.

--
as far as the wine link try running your exe from a command line.
open a terminal
run:

wine  (the full path to your exe)

once you get that to launch correctly, create a new shortcut, and use it as the command run by the shortcut.

ps, ~ is short for home.  (there's no place like ~)
so 
~/.wine/... 
might save you from getting carpel tunnel syndrome at a young age.
-b

---

### Post by lilrockerboy on 2005-12-15
[QUOTE=eric.proctor]Why would you change the directory and not just change the link?[/QUOTE]

Sorry, haha! I'm just trying to figure this out! I've been a Linux user since Monday! :) I'm trying to learn as much as possible but every new thing seems to open up more and more! So I'm never to sure! I've still have "Windows rules" stuck in my head!

---

