---
title: "Where do they go?"
date: 2006-04-03
forum: Absolute Beginner Talk
---

### Post by SilentSam on 2006-04-03
Sorry, i'm new here,

I used Gnome App Install to d/l a program (Stellarium). 
Embarrassingly, i have no clue as to how the Linux file structure works or what file extesions do what so i can't even FIND said program much less run it.
Same goes for wine. If it doesn't appear in the applications menu i'm screwed.

Any help?
Thanks,
sam

---

### Post by taurus on 2006-04-03
Not in front of my Ubuntu right now but click Applications -> Graphics or any other options.  Otherwise, Applications -> Accessories -> Terminal and type
```

stellarium

```

---

### Post by KansasJoe on 2006-04-03
in your terminal type which programname...where programname is name of your program

which stellarium

this will show you where the executable is

as far as wine is concerned it will be under .wine in your home folder....the . means it's hidden so you can do it in terminal as cd .wine or with nautilus with control + h

---

### Post by Choad on 2006-04-03
programs are (usually) stored in 

/bin

or

/usr/bin

(bin stands for "binary" as in a program that has been compiled down in to binary)


linux doesnt really rely on file extentions in the same way that windows does. instead files are just maked "is executable" to make it executable, otherwise its just a file, and how its used depends on what program is handling it.

---

### Post by SilentSam on 2006-04-03
Thanks for the replies everyone. That could'nt be any more simple ](*,) 

Why the heck can't Windows do that?!

Feel'n dumb,
sam

ps Has anyone read [this]("http://www.amazon.com/gp/product/1590596277/sr=8-1/qid=1144110197/ref=pd_bbs_1/103-1709025-6288638?%5Fencoding=UTF8"), or [this]("http://www.amazon.com/gp/product/0132435942/sr=8-2/qid=1144110197/ref=pd_bbs_2/103-1709025-6288638?%5Fencoding=UTF8")? I'm looking for a good primer/refrence :)

---

### Post by rfruth on 2006-04-03
Haven't read either book, the Ubuntu Chronicles seem good 
   [http://pykeylogger.sourceforge.net/wiki/index.php/Ubuntu:Chronicles]("http://pykeylogger.sourceforge.net/wiki/index.php/Ubuntu:Chronicles")

---

### Post by taurus on 2006-04-03
Those two books like nice to me!  If you want to learn more about your Ubuntu, then you should go for it.  I don't think you have to get both since I am sure they both cover almost the same stuff!!!

---

### Post by SilentSam on 2006-04-03
Thanks again guys,

..some cool little tidbits [here]("http://pykeylogger.sourceforge.net/wiki/index.php/Ubuntu:Chronicles#Synaptics_Touchpad"). Thanks for taking the time,
:) 
sam

---

