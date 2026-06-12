---
title: "I got bashed!"
date: 2007-04-03
forum: Absolute Beginner Talk
---

### Post by ausbun on 2007-04-03
I was trying to execute a .bin file on my desktop and got this message:

ausbun@ausbun-desktop:~/Desktop$ ./pokerth-0.3-linux.bin
bash: ./pokerth-0.3-linux.bin: Permission denied


I can't recall seeing  this "bash:" reply. 

I checked the properties on the file and it says it is executable.

Am I doing something wrong? 

Thanks in advance for any suggestions.

---

### Post by dbbolton on 2007-04-03
put "sudo" first

```
sudo ./pokerth-0.3-linux.bin
```

---

### Post by ausbun on 2007-04-03
When I do this, I get "command not found."

---

### Post by dbbolton on 2007-04-03
did you remember to 'cd' to the folder containing the .run file ?

i.e.
```
cd ~/Desktop
```

---

### Post by Amackera on 2007-04-03
Make sure you get the period before the slash.

---

### Post by ausbun on 2007-04-03
the period's there! There should be a space after "sudo" and before the period. right?

---

### Post by confused57 on 2007-04-03
Maybe this will help:
[http://www.monkeyblog.org/ubuntu/installing/](http://www.monkeyblog.org/ubuntu/installing/)

---

### Post by WalmartSniperLX on 2007-04-03
I could be completely wrong with this but would 

```

sudo sh pokerth-0.3-linux.bin

```

work once you have cd to the dir?

---

### Post by benskiedra on 2008-01-20
I came up with same problem and FOUND the solution... 
To launch the installer you simply have to set proper permissions for execution, or just right-click the installer, go to permission tab and select 'Allow executing file as program'. That's it.

---

### Post by Joeb454 on 2008-01-20
You might even be able to double click the file on your desktop after doing what the above post says :)

For a start, the GUI is easier to use, but you'll learn to use the terminal in time. I hardly use the GUI now except for surfing the net etc.

---

