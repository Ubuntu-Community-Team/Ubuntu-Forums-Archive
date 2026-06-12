---
title: "Is it possible to have output displayed on screen while it is redirected to a file?"
date: 2006-08-06
forum: Absolute Beginner Talk
---

### Post by Akhran on 2006-08-06
Eg. while installing some software, is it possible to redirect all the screen output (like what files are installed where) into a file while still having the output on screen?

Thanks!

---

### Post by Dr. Nick on 2006-08-06
If you are just trying to basically log the teminal output then use "tee" You can see a example and some basic info in the link in my signature "common commands"

> 
[COLOR=#000000][I][B]tee -
  [/B][/I][B]
  [/B]Tee command can be used to write the results of a terminal command into a text file. This can be especially helpful when you are dealing with scripts. Tee will replicate the contents displayed in the terminal to a text file for later viewing. I have used this with apt-get so that I can later see what packages were installed/removed.[I][B][I][B][B][I][I][B][B][I]
  
  [/I][/B][/B][/I][/I][/B][/B][/I][/B][/I]To use it simply run**[B][B][B][B] **[/B][/B][/B][/B][COLOR=#FF0000]**command | tee *myfile* [COLOR=#330000](where myfile is the name of the text file you want created) [/COLOR]**[/COLOR][COLOR=#FF0000][COLOR=#330000]The text file will be made in which ever directory you were in when the command was launched.[/COLOR][/COLOR][/COLOR][COLOR=#000000][COLOR=#FF0000][COLOR=#330000]
  [/COLOR][/COLOR][/COLOR]

---

