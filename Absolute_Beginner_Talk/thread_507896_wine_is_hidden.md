---
title: "wine is hidden????"
date: 2007-07-23
forum: Absolute Beginner Talk
---

### Post by DaH-RaT on 2007-07-23
hi everyone its me again, I am having a bit of trouble with wine. I installed it  with the guid from the official ubuntu feisty guide . but yet it does not seem to make any  shortcuts  ( Applications/Accessories/Wine File ) is this normal? i do know there was a new wine that came out and i have that version. any ideas? no exe's give me the wine option when right cliking them also i hit CTRL H  in home and .wine is not there. also searched for it and nothing. yet it is installed?????

---

### Post by Nythain on 2007-07-23
have you run winecfg in the terminal yet... you have to run that (its the setup and config) and it will create the necessary directories... that should solve your no .wine folder in your home directory issue... as for right clicking on exe's and having a wine option... cant help you there... i dont think i've ever noticed one, though i wasnt looking. I find it more usefull to run the exe in a terminal session so i can see any output that might arise. running an exe in terminal is easy, you just type
wine /path/to/your.exe
making sure to replace that with the path and name of the exe

if you cant get a right click option then you could consider creating your own entries in the applications menu using the same syntax you would use in terminal.

---

### Post by DaH-RaT on 2007-07-23
okay that was exactly the problem i maybe have over seen it i guess :)  the winecfg helped alot now i think i can do the rest to create a shortcut in accessories , thanks again Nythain!!

---

