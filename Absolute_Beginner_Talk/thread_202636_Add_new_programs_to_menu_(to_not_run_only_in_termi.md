---
title: "Add new programs to menu (to not run only in terminal)"
date: 2006-06-23
forum: Absolute Beginner Talk
---

### Post by EWek1 on 2006-06-23
OK, *Brand* spankin new ubuntu n00b here...
I downloaded a program using apt-get (tn5250, an IBM terminal emulator).  I can run the program from terminal without incident.  I believe the program should be able to be run natively and not only through the terminal.  I believe there is functionality that is lost when running through terminal, as the description of what the program is capable of doesn't seem possible only through terminal.  Ok, so the problem is that I can't figure out how to run the program NOT in terminal.  How do I  add something to the Applications list?

Also, while I'm at it, this is an even dumber question, but I figured while I'm here, I'll ask: When I find commands listed somewhere that are multi line like:
sudo apt-get install acroread
sudo apt-get install mozilla-acroread
sudo apt-get install acroread-plugins

Am I expected to enter this all at once, or just the first command, then wait for the prompt, then the second command, prompt, third command?  I'm not sure how to enter them all at once if that's what you're supposed to do.

TIA for any help, I am enjoying ubuntu so far, but obviously haven't progressed too far as of yet.

Thanks!

---

### Post by BoyOfDestiny on 2006-06-23
[QUOTE=EWek1]OK, *Brand* spankin new ubuntu n00b here...
I downloaded a program using apt-get (tn5250, an IBM terminal emulator).  I can run the program from terminal without incident.  I believe the program should be able to be run natively and not only through the terminal.  I believe there is functionality that is lost when running through terminal, as the description of what the program is capable of doesn't seem possible only through terminal.  Ok, so the problem is that I can't figure out how to run the program NOT in terminal.  How do I  add something to the Applications list?

Also, while I'm at it, this is an even dumber question, but I figured while I'm here, I'll ask: When I find commands listed somewhere that are multi line like:
sudo apt-get install acroread
sudo apt-get install mozilla-acroread
sudo apt-get install acroread-plugins

Am I expected to enter this all at once, or just the first command, then wait for the prompt, then the second command, prompt, third command?  I'm not sure how to enter them all at once if that's what you're supposed to do.

TIA for any help, I am enjoying ubuntu so far, but obviously haven't progressed too far as of yet.

Thanks![/QUOTE]

Agreed, they should have menu entries. Your options are adding the debian menu, or right clicking the menus and choose edit menus. Many apps do provide entries automatically, hopefully this will continue to improve...

As for the sudo apt-get install stuff, anyway you want to do it should still work...

**sudo apt-get install acroread mozilla-acroread acroread-plugins**

will also work (although I prefer just using evince [ubuntu's default], I don't want to view pdfs in a browser personally...)

---

### Post by TheFourElements on 2006-06-23
enter in one command at a time. Also, are you using gnome (like almost everyone else) or another GUI. I use windowmaker and If you are using windowmaker you can customize the menu with
```
wmakerconf
```

---

### Post by EWek1 on 2006-06-23
[QUOTE=BoyOfDestiny]Agreed, they should have menu entries. Your options are adding the debian menu, or right clicking the menus and choose edit menus. Many apps do provide entries automatically, hopefully this will continue to improve...

[/QUOTE]


OK, now I just need to understand one more point...What am I supposed to right click on?  How do I add this program to the menu?  When I right click the menu, I get add this launcher to menu, and add this launcher to desktop, but I don't see how to add a particular program to the menu....Sorry for being a total n00b, but I just can't help it!

---

### Post by BoyOfDestiny on 2006-06-23
[QUOTE=EWek1]OK, now I just need to understand one more point...What am I supposed to right click on?  How do I add this program to the menu?  When I right click the menu, I get add this launcher to menu, and add this launcher to desktop, but I don't see how to add a particular program to the menu....Sorry for being a total n00b, but I just can't help it![/QUOTE]

I'm assuming you've got ubuntu 6.06 (if not I'd recommend it...).

Applications Places System
Right clicking on any of these should have an option 
"Edit Menus"

From there choose a category, where you'd like to add it... 
For example Accessories for your terminal emulator...
Click Accessories
Choose File -> New Entry
provide a name for it
provide the command (what you typed in terminal to run it)
choose an icon if you desire...
Click Ok, and you should be set.

---

### Post by EWek1 on 2006-06-24
ok, I've added it to the menu now, but when I click on the program to run it, nothing happens (the menu just disappears) as if it's going off to run, but the program never appears.  If I change the menu item to run in terminal, the terminal window pops up for just a moment, then disappears completely.  If I call the program from a regular terminal session, it works just fine.
What am I missing?

---

### Post by evaristegalois on 2006-06-28
that's where they leave you hanging: I am rather interested in your question as well. Let's say I have installed Opera on my Ubuntu computer. Then I want to place an icon on the desktop which will open Opera without the Terminal intervening. Anyone out there who knows let us know. Here is my strategy via Terminal:

right-click on the panel (the space on the very top of your screen)

select add to panel

double-click on Custom Application Launcher

give your program a name (e.g. "Opera") and a generic name (e.g. "Web Browser")

under Command, type what you would type on the terminal (e.g. "opera") [or type opera %u and do not enable "Run in terminal" -- see my reply further down]

click on "no icon" to select an icon

enable "Run in terminal"

click OK

you're done, all of this in Ubuntu Breezy

--evaristegalois

---

### Post by evaristegalois on 2006-06-29
instead of clicking on "Run in terminal" you can append %u to your command and then the application will not open a terminal as well. If it's Opera, for example, do not click on "Run in terminal" (see my above reply of how to get there) and under Command enter "opera %u". Then, when you click on the application launcher, it will open the application but not a terminal.

--evaristegalois

---

