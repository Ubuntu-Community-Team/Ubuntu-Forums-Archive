---
title: "Menu Editor ?"
date: 2006-10-09
forum: Absolute Beginner Talk
---

### Post by ghostshadow189 on 2006-10-09
hi all ,
I want to add an entry that when i click to it , it'll run my script (.pl , .sh or something like that) . But when i use Alacarte Menu Editor to add new entry , i browse to this script and tick with run in terminal , and then click to it in menu , the terminal appear and then disappear , so i cant see script's result . so how can i make the terminal still appear to see the result and continue to use this terminal ?
thanx for ur helps

---

### Post by jem7v on 2006-10-09
Maybe you could add something to the end of your script to make it require a user input before it finished - ie, just add a point where it asks for you to "press any key to continue" so it can't end and exit until you've had a chance to look it over?

That would be my suggestion (coz I haven't written a script in a long time and don't quite remember the details of it), but I'm sure there's a more elegant solution floating around out there on the net...

---

### Post by ghostshadow189 on 2006-10-09
> Maybe you could add something to the end of your script to make it require a user input before it finished - ie, just add a point where it asks for you to "press any key to continue" so it can't end and exit until you've had a chance to look it over?

but like that , i cant continue to use the terminal , just can see output , hit enter and terminal disappear

---

### Post by po0f on 2006-10-09
ghostshadow189,

[Click here](http://www.ubuntuforums.org/showthread.php?t=269408), read second post.

---

### Post by ghostshadow189 on 2006-10-09
thanx for this help , it so useful , but there still a problem that it just allow us see the result but we cant continue to use this terminal , for ex type another command , just see result and close it .
for example , i creat a script and then click to it in menu , it appear script's syntax , so we can continue type ur args to run this script again ?
or for example , i type "gnome-terminal --execute cd TestDir" -> it'll appear a window but we cant continue type another command like ls , mkdir , etc .

---

