---
title: "how do i open a .tar.bz2"
date: 2007-04-27
forum: Absolute Beginner Talk
---

### Post by rickycodie on 2007-04-27
i downloaded a the new vuze from azerus and i can't open the friggin thing. how can i do it?
please to be helping me,
ricky

---

### Post by topsites on 2007-04-27
From Terminal:

gzip -d filename.tar.gz
tar -xf filename.tar

Oh, bz2?  Get the gz idk

---

### Post by DSn0wMan on 2007-04-27
Try this```

$ tar jxvf <filename.tar.bz2>
```

---

### Post by rickycodie on 2007-04-27
did i say open, i meant install. and i'm sorry. i have learned my lesson.

---

### Post by TheRingmaster on 2007-04-27
[How to install ANYTHING in Ubuntu!]("http://monkeyblog.org/ubuntu/installing/#source")

---

### Post by DSn0wMan on 2007-04-27
After untaring your tar.bz2 you should look in the dirctory it made for a text file explaining how to install it. More often then not you just do three commands: ./configure, make, sudo make install

for more detailed instructions go here: [http://www.psychocats.net/ubuntu/installingsoftware](http://www.psychocats.net/ubuntu/installingsoftware)

---

### Post by rickycodie on 2007-04-27
> **TheRingmaster said:**
> [How to install ANYTHING in Ubuntu!]("http://monkeyblog.org/ubuntu/installing/#source")
i've tried that and it's not working, but maybe i'm just bieng dumb. i navagate to the directory and i try to use ./configure and no worky. also there is no readme so i'm just lost.

---

### Post by DSn0wMan on 2007-04-27
Do an "ls -ltr" command in that directory and post the output.

---

### Post by rickycodie on 2007-04-28
azureus  Azureus2.jar  Azureus.png  Azureus.torrent.png  plugins
the ls-ltr command didn't work so i just ran ls. thank you for helping me.

---

### Post by DSn0wMan on 2007-04-28
Ok so you are installing Azureus. The best way is to open the terminal and type ```
sudo aptitude install azureus
```

You could probably use what you have by typing ```
java -jar Azureus2.jar
```

---

### Post by TheRingmaster on 2007-04-28
[URL="http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_install_P2P_BitTorrent_Client_.28Azureus.29"]installing Azureus
[/URL]

---

