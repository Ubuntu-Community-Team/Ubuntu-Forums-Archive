---
title: "rm fails"
date: 2006-03-23
forum: Absolute Beginner Talk
---

### Post by marwal on 2006-03-23
I saw that the hidden folder .Thumbnails was growing out of control and decided to clean it out. So with Nautilus I selected all thumbnails in the "failed" folder and hit "Delete".
OK, so all this crap just moved to my .Trash-folder (my mistake - i know how to enable delete in Nautilus now).

So i left-clicked on my trash-applet and selected "Empty Trash"
The fans started spinning like crazy and when i used "top" in the terminal it said the trash-applet used 100% CPU.

So when i should clean out the other thumbnails i navigated to the folder in my terminal and gave the command "rm -rf *.png"

The system responded "Argumentlistan för lång" (this is swedish for The argumentlist's too long". The folder contained about 3000 thumbnails.

Could someone give me some hints how i should do this the next time my thumnailsfolder expands too much.

I'm using Dapper but this isn't really a dapper-question i think.

---

### Post by dcstar on 2006-03-23
[QUOTE=marwal]
......
So when i should clean out the other thumbnails i navigated to the folder in my terminal and gave the command "rm -rf *.png"

The system responded "Argumentlistan för lång" (this is swedish for The argumentlist's too long". The folder contained about 3000 thumbnails.

Could someone give me some hints how i should do this the next time my thumnailsfolder expands too much.

I'm using Dapper but this isn't really a dapper-question i think.[/QUOTE]
This is probably what you want:

[http://ubuntuforums.org/showpost.php?p=605229&postcount=2](http://ubuntuforums.org/showpost.php?p=605229&postcount=2)

---

### Post by marwal on 2006-03-23
I don't have a Thumbs.db folder - i'm not on a windows platform.
I have a .thumbnails folder with subfolders "fail" and "normal".

---

### Post by dcstar on 2006-03-23
[QUOTE=marwal]I don't have a Thumbs.db folder - i'm not on a windows platform.
I have a .thumbnails folder with subfolders "fail" and "normal".[/QUOTE]
That is an example, replace it with what you want.

---

### Post by Cirrocco on 2006-06-11
I've seen that command on the net and on the forums and it's obviously NOT a cut and paste command.  It doesn't do anything, and I don't understand the syntax to debug the problem.

can someone post the command that I can run on my .thumbnails folder that will recursively go into the subfolders and remove .png files without it complaining about the volume of files for it to clean?

what I mean by that last bit: if that directory gets too large, a rm command will return: "bash: /bin/rm: Argument list too long"

---

### Post by BenTyreman on 2006-06-11
```
find /dir/with/png/files/ -iname "*.png" -exec rm -f {} \;
```

should do the trick.

WARNING: Get the directory wrong and it will recursively delete any png files!

---

### Post by BaffledMollusc on 2006-06-11
I think this might be a known (and unfixed) bug. See

[https://launchpad.net/distros/ubuntu/+source/nautilus/+bug/34247](https://launchpad.net/distros/ubuntu/+source/nautilus/+bug/34247)

---

### Post by Sjovan on 2007-06-25
find . -name '*.png' | xargs rm

will also do the trick.

edit:
remember to be in the right directory

---

