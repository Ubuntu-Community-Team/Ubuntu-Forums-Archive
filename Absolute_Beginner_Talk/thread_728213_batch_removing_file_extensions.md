---
title: "batch removing file extensions"
date: 2008-03-18
forum: Absolute Beginner Talk
---

### Post by jamesjeffries1 on 2008-03-18
I have ended up with a load of mp3 files with an extra extension. they are now in the format "filename.mp3.bc!" (the exclamation mark is part of it not an emphasis) and i want them to be "filename.mp3". they wont play with this extra extension, so any idea how to remove it?
Thanks

---

### Post by tanguyr on 2008-03-18
> **jamesjeffries1 said:**
> I have ended up with a load of mp3 files with an extra extension. they are now in the format "filename.mp3.bc!" (the exclamation mark is part of it not an emphasis) and i want them to be "filename.mp3". they wont play with this extra extension, so any idea how to remove it?
Thanks

Open a terminal in the directory containing your files and type:

```

for i in $(ls *.bc\!); do mv $i ${i%\.bc\!}; done

```

---

### Post by jamesjeffries1 on 2008-03-18
ok that gives me this output:

mv: cannot stat `01.': No such file or directory
mv: cannot stat `Logistics': No such file or directory
mv: cannot stat `-': No such file or directory
mv: cannot stat `Welcome': No such file or directory
mv: cannot stat `To': No such file or directory
mv: cannot stat `The': No such file or directory
mv: cannot stat `Future': No such file or directory
mv: cannot stat `-': No such file or directory
mv: cannot stat `DoG.MP3.bc!': No such file or directory
.... etc etc.

think this is because of having spaces in the names (bad practice i know but there not my files)

have also tried using morphose2 to do it but it just crashed everytime.
anyother suggestions?

---

### Post by erginemr on 2008-03-18
I think the script stucks at spaces inside the file names. Without going into any detail, you  may need to use quotes such as "$i" or similar to handle spaces inside the file names.

However, I will suggest a different GUI program: krename. I think you should give it a try:
```
sudo aptitude install krename
```

---

### Post by glennric on 2008-03-18
You can also make a script with the contents:
```
#!/bin/bash
IFS="
"
for i in $(ls *.bc\!); do
	mv $i ${i%\.bc\!};
done
```
Then make the script executable and execute it in the directory with the bc! files in it.  The 
IFS="
"
make the script not split filenames on spaces.

---

### Post by jamesjeffries1 on 2008-03-18
thanks that last script worked

---

### Post by tanguyr on 2008-03-19
> **jamesjeffries1 said:**
> thanks that last script worked

yeah, sorry, my bad - forgot to take into account that file names might contain spaces.

/t

---

### Post by Oldsoldier2003 on 2008-03-19
> **erginemr said:**
> I think the script stucks at spaces inside the file names. Without going into any detail, you  may need to use quotes such as "$i" or similar to handle spaces inside the file names.

However, I will suggest a different GUI program: krename. I think you should give it a try:
```
sudo aptitude install krename
```

Thunar has bulk rename for the xubies  :)

---

