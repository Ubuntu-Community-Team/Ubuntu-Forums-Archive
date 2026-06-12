---
title: "How do you use WINE?"
date: 2006-09-09
forum: Absolute Beginner Talk
---

### Post by dckirba on 2006-09-09
Hello all, how are you?

I just installed WINE and cabinstaller (?) using synaptic. So how do I now go about and see if any of my windows programs work in linux now? I tried navigating to an exe file and double-clicking, but that doesn't seem to work. 

I also tried searching the forum, but not too hard because for some reason nothing popped up in the first 2 pages :) It's saturday, I haven't slept all night and I'm lazy :)

Thanks for your help,
cheers,
David K

---

### Post by Klaidas on 2006-09-09
> wine /path/to/program.exe should work.

---

### Post by dckirba on 2006-09-09
Thankyou :)

---

### Post by dckirba on 2006-09-09
Hmm... it creates a file in my home folder called .wine and then does nothing... :(

---

### Post by frequenicity on 2006-09-09
Was that an install program? It installs to a /home/you/.wine/ folder which will basically pretend to be your C drive.

After install, it's 
wine /home/you/.wine/c_drive (i believe)/Program\ Files/whatever/path/programrunfile.exe

Remember, TAB is your friend.

---

### Post by dckirba on 2006-09-12
Hi frequenicity,

I tried that and this is what I get in the terminal:

david@david:~$ wine /home/david/.wine/drive_c /media/hdc1/Program\ Files/Macromedia/Fireworks\ MX\ 2004/Fireworks.exe
wine: could not load L"C:\\.": Invalid handle
david@david:~$ wineserver: could not save registry branch to /home/david/.wine/system.reg : Permission denied
wineserver: could not save registry branch to /home/david/.wine/userdef.reg : Permission denied
wineserver: could not save registry branch to /home/david/.wine/user.reg : Permission denied
q
bash: q: command not found
david@david:~$ sudo wine /home/david/.wine/drive_c /media/hdc1/Program\ Files/Macromedia/Fireworks\ MX\ 2004/Fireworks.exe
Password:
wine: could not load L"C:\\.": Invalid handle
david@david:~$


any suggestions? I don't even know if the Macromedia products work well in wine, but I'd really like to try :)

Thanks again,
Cheers,
David K

---

### Post by Wega on 2006-09-12
And one more question about Wine: after installation of one program I have to copy one more file into the virtual "Program files" folder. HoW?

---

### Post by bodhi.zazen on 2006-09-12
Well, that is how you use wine.

How to get any particular program running however is a different story.

Search the Ubuntu forums for how to wine.

Best source, however, is wineHQ.

[WineHQ](http://appdb.winehq.org/)

Put the name or your program in the gray box on the left and click "search".

---

### Post by bodhi.zazen on 2006-09-12
> **Wega said:**
> And one more question about Wine: after installation of one program I have to copy one more file into the virtual "Program files" folder. HoW?

Drag 'n drop with nautilus. or cp (copy) mv (move)

ex:
```
 cp /path_to_file/file_2_copy /path/to/location.
```

2 problems:

[list=number][*]your .wine directory is "hidden".
[*]Linux does not like spaces in the path.[/list]

Thus use:[list=number]
[*]~/.wine/c/Program\ Files/....
[*]~/.wine/c/"Program Files"/....[/list]

---

