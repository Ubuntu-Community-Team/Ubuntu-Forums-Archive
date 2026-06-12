---
title: "i have the .bin setup file whats next"
date: 2007-07-22
forum: Absolute Beginner Talk
---

### Post by akkad on 2007-07-22
i have downloaded real player 10 from [http://www.real.com/linux](http://www.real.com/linux) , the downloaded file is a bin file , i dont know how to install it :( ?

---

### Post by JesterDev on 2007-07-22
Open a terminal window or press alt+F2 and type:

```

sudo ./name_of_file.bin

```

There actually might be a .configure file in there in which case you should run that via the same method as above. Sorry I've not install this app in many years.

Or better yet! Open a terminal and type:
```

sudo aptitude install realplay

```

This latter method is easier, and faster. :) It will download and install it for you. But you have to edit your repositories. See this link first:  [http://ubuntuforums.org/showthread.php?t=186792](http://ubuntuforums.org/showthread.php?t=186792)

---

### Post by AtrejuT on 2007-07-22
I'd guess you open a terminal, go to the proper folder and enter
```

chmod +x somefile.bin
./somefile.bin

```

maybe you require super user rights to install it, then you'll have to put a sudo before these commands.

---

