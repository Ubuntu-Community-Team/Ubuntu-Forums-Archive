---
title: "americas army bin file"
date: 2005-08-27
forum: Absolute Beginner Talk
---

### Post by jasonpeinko on 2005-08-27
what do i do with the bin file i downloaded for americas army linux version?

---

### Post by edwina on 2005-08-27
What happens if you just click on it?

You probably need to execute it as root, which means browsing to its folder in a terminal then just typing its name to execute it. Might be "./" then it's filename. Not sure, so let us know what happens  ;-)

---

### Post by jasonpeinko on 2005-08-28
[QUOTE=edwina]What happens if you just click on it?

You probably need to execute it as root, which means browsing to its folder in a terminal then just typing its name to execute it. Might be "./" then it's filename. Not sure, so let us know what happens  ;-)[/QUOTE]
 nope here is what i get
```

root@ubuntu:/home/jason/Desktop # ./armyops210-linux.bin
bash: ./armyops210-linux.bin: Permission denied

```

---

### Post by jasonpeinko on 2005-08-28
anyone? is there a repositor for aa?

---

### Post by Jussi Kukkonen on 2005-08-29
[QUOTE=jasonpeinko]nope here is what i get
```

root@ubuntu:/home/jason/Desktop # ./armyops210-linux.bin
bash: ./armyops210-linux.bin: Permission denied

```[/QUOTE]
 You haven't set the executable bit:
**chmod u+x armyops210-linux.bin**

---

### Post by thepcdoctor on 2005-09-02
I've got americas army run file on my desktop and can't install it. What am I doing wrong? Do I need to navigate to the path?? If so how do I do that? Sorry if this is a stupid question. I am a complete linux novice.


theboss@ubuntu:~$ sudo sh ./armyops230-linux.run
sh: ./armyops230-linux.run: No such file or directory

---

### Post by bjweeks on 2005-09-02
Open the terminal and go the directory the file is in by```
cd /home/username/folder
``` then mark it executable with ```
chmod +x file.bin 
``` then run it by ```
./file.bin
```

---

### Post by Slugger on 2005-09-02
Thanks that was great now I can install Americas Army.

---

### Post by bjweeks on 2005-09-02
No problem glad I could help.

---

