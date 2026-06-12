---
title: "How do I change directories..."
date: 2005-12-22
forum: Absolute Beginner Talk
---

### Post by gatorbrit on 2005-12-22
OK this is not as simple as that..

I know to use cd /home/name

but how do I change a directory when the directory name has a space in it.

For example cd /c_drive/Program Files
returns
c_drive/Program not found.


I am using wine in a "fake" windows dir.

Thanks

---

### Post by bscbrit on 2005-12-22
cd "/home/user/this has a space in it" - I think will do the job.

---

### Post by kabus on 2005-12-22
Insert a "\" behind "Program", then hit space and tab.
Usually a space gets interpreted as the end of an argument, but the "\" tells the command line to ignore the special meaning of a character.

---

### Post by DevilsAdvocate on 2005-12-22
I think you can also put it in quotes thusly:

"Program Files" or 'Program Files'

---

### Post by daschl on 2005-12-22
the most time you'll find this way:

```

$ cd .wine/drive_c/Program\ Files/

```

hth

---

### Post by gatorbrit on 2005-12-22
thanks that seems to work. 
I was also running into probs because i was trying to change to a hidden dir i.e.   /.wine/ without doing sudo

---

### Post by daschl on 2005-12-22
[QUOTE=gatorbrit]thanks that seems to work. 
I was also running into probs because i was trying to change to a hidden dir i.e.   /.wine/ without doing sudo[/QUOTE]

its no problem to change into a dotfile with your normal user (well, if the permessions are set that only root can view the files then you obviously cannot ;))

BUT you have to watch out

/.wine tries to change to a directory located directly after the "root" directory (which sits on top of all)
.wine changes to a directory which is in the same directory as you are.

for example:

```

michi@notix:~$ cd /.wine
bash: cd: /.wine: file or directory not found
michi@notix:~$ cd .wine
michi@notix:~/.wine$

```

but:

```

michi@notix:~$ cd /etc
michi@notix:/etc$ pwd
/etc
michi@notix:/etc$ cd ~
michi@notix:~$ cd etc
michi@notix:~/etc$ pwd
/home/michi/etc
michi@notix:~/etc$

```

do you see the difference?

---

### Post by gatorbrit on 2005-12-22
Thanks, that helps alot.  

Another related question.   I have a couple of apps that now run nicely in wine, they are textpad and stata (a statistical package).  Can I create nice menu items or desktop shortcuts for these apps so I don't have to always go through the terminal?

---

### Post by gatorbrit on 2005-12-22
Answered my own question.

Created a "launcher"  
with the following in the command line
wine "/home/richard/.wine/drive_c/Stata8/wstata.exe"

and another with
wine "/home/richard/.wine/drive_c/Program Files/TextPad 4/textpad.exe"

works perfectly.  

I am now able to be 100% linux for work.  Very cool.

---

### Post by ninotob on 2005-12-22
I just want to say this is a perfect thread.  Gatorbrit wrote a great title -- it's descriptive of his problem (rather than the all too common "Help Me Please").  Gatorbrit described his problem clearly which allowed the various solutions to be stated easily (sloppy questions lead to answers like "if you mean A then do B, but if you mean X then do Y).  And then there is some follow up detail, some obvious work on gatorbrit's part (sometimes just asking a question leads one to find the answer independently) and most importantly -- it really worked out.  It makes me happy to see these kinds of threads.  Kudos to everyone.  ;-)

---

### Post by gatorbrit on 2005-12-22
Thanks so much for the comments on the "perfect thread"!

I have found the forums here to be fantastic.  I have gone from being a linux noobie to a full blown user in about 2 weeks.  I can pretty much get everything I need in ubuntu, and I know that what I can't - I can figure out.

This has been a pretty rewarding experience.  

Thanks again to all the forum experts who are willing to put in the time to help us noobies get going.

:)

---

