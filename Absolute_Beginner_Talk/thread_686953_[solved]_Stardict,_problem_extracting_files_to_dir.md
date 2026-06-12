---
title: "[solved] Stardict, problem extracting files to directory"
date: 2008-02-03
forum: Absolute Beginner Talk
---

### Post by Marfish on 2008-02-03
Hello, I finally found a free dictionary that supports french-english and english-french, but now I cant seem to extract the necessary files downloaded from the site to use them in the program. The dictionary is called Stardict. I can extract them easily enough, but its when I try to extract them into the file thats been suggested by the programs site, that I get an error. It tells me that I do not have permission. I can download the necessary software from a deb file but it will not let me do it myself, id take it from a deb file if I could but I do not know where to find for them. Heres the terminal message from when I tried to move the file into the directory. 
marlon@marlon-laptop:~/Desktop$ tar -xjvf stardict-freedict-eng-fra-2.4.2.tar.bz2
stardict-freedict-eng-fra-2.4.2/
stardict-freedict-eng-fra-2.4.2/dictd_www.freedict.de_eng-fra.idx
stardict-freedict-eng-fra-2.4.2/dictd_www.freedict.de_eng-fra.dict.dz
stardict-freedict-eng-fra-2.4.2/dictd_www.freedict.de_eng-fra.ifo
marlon@marlon-laptop:~/Desktop$ mv stardict-freedict-eng-fra-2.4.2 /usr/share/stardict/dic
mv: cannot move `stardict-freedict-eng-fra-2.4.2' to `/usr/share/stardict/dic/stardict-freedict-eng-fra-2.4.2': Permission denied
marlon@marlon-laptop:~/Desktop$ 
Could someone please help, I have no idea what to do and I really need this and I dont want to have to have to go to my windows os everytime I want to do my french. Any help will be much appreciated.

---

### Post by Marfish on 2008-02-04
Lol, sorry. I found out what the problem was. I wasnt using sudo. Should have been pretty obvious with the permission and everything, ah well.

---

