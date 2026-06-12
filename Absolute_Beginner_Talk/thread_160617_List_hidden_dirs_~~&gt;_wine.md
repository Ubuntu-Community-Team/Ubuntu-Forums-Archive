---
title: "List hidden dirs ~~&gt; wine"
date: 2006-04-15
forum: Absolute Beginner Talk
---

### Post by zorlab on 2006-04-15
Having installed wine, luckilly through the Great Automatix bundle. I did not have alot of task to figure out such as naming c: etc  **BUT** since installing Macromedia Dreamweaver, I find all the dirs are hidden, and as such, how do I list hidden dirs, in order to find the path to the executable so I can create a  desktop launcher for it? 


One thing I did was login as root, go to home/USER and type find

EEK!  so many dirs  wizzing by so fast. 

What are my options here........   so I can actually see the specific dir I need, or an argument to list by page. 

[COLOR="Teal"]Forgive the post here in Absolute Beginner _However_ this  seems to have become the best place to get an answer, as it seems most people in My catagory, with some experience, post here, and yet, do not quallify as per the stickys. :)[/COLOR]

---

### Post by fng on 2006-04-15
It's probably installed in /home/USER/.wine/drive_c/Program Files

All hidden dirs start with a period.
you can view them in a terminal by typing ls -al in the correct dir or the key combination ctrl + h in nautilus

---

### Post by zorlab on 2006-04-15
Yes  but  

here is what I get..
....................................................................
[B]root@SCSI:/home/barry/.wine/drive_c# ls
Program Files  windows
[email]root@SCSI:/home/barry/.wine[/email]/drive_c# cd Program Files
bash: cd: Program: No such file or directory
[email]root@SCSI:/home/barry/.wine[/email]/drive_c#[/B]
...................................................................

---

### Post by zorlab on 2006-04-15
its got to be that pesky little space  that Linux does not like  ''''''
Whats the work around?  [B]tried %20, _
[/B]

---

### Post by xenmax on 2006-04-15
You can use \ like this;
```
cd Program\ Files
```However, i never use it since thanks to "Tab" key - for ex: type cd Prog and hit tab key - it will auto-complete for you

---

### Post by zorlab on 2006-04-15
that gets me there, thanks xemax

Now If only the Launcher worked  :(  
Back to the drawing board..... 

Any Help is appreciated

---

