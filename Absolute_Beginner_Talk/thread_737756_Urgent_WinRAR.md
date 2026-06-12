---
title: "Urgent WinRAR"
date: 2008-03-27
forum: Absolute Beginner Talk
---

### Post by D.J. on 2008-03-27
I would like a guide on installing winrar, I've tried a couple of times but have been experianceing problems.


HELP!:(

---

### Post by Lisa Y on 2008-03-27
You can try this....

Step 1. Make sure you have extra repositories enabled.

Step 2. Paste this command into the terminal:

```

sudo aptitude update && sudo aptitude install rar unrar

```

---

### Post by D.J. on 2008-03-27
Both of those commands went in fine, but i still go to extract the .rar's and it says the archive type isnt found.

---

### Post by Lisa Y on 2008-03-27
sorry for the double post.....

But i forgot to add that if you wanted to install winrar....

you would have to install it through WINE (oblivious...unless there is another way) 

i believe these should be the correct steps...i havent tested it...but i have tested installing 

other windows program through wine....i think its mostly all the same...

1) Download winrar...
2) Wine [.exe]
3) Run winrar using wine [ where you installed it]/winrar.exe

If i have any mistakes here...please do correct me

---

### Post by cisforcojo on 2008-03-27
Is there a specific reason you want WinRAR? Or is it you just want to decompress .rar files?

If you use GNOME, "File Roller" works perfectly and comes by default with Ubuntu. You might have to install rar/unrar but it'll work perfectly one this is done.

---

### Post by vargasman on 2008-03-27
Did you try it from the command line? CD into the directory with the .rar file and run this:
```
 sudo unrar  *.rar
```

---

