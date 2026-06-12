---
title: "Dangerdeep problems"
date: 2007-07-19
forum: Absolute Beginner Talk
---

### Post by ahoman66 on 2007-07-19
I am trying to copy files from a folder on my desktop to /usr/share/games/dangerdeep. but I keep getting this from the command line...

ahoman66@machine-laptop:~/Desktop/dangerdeep$ cp fonts /usr/share/games/dangerdeep
cp: omitting directory `fonts'
ahoman66@machine-laptop:~/Desktop/dangerdeep$ 

I have installed Danger of the Deep but need to install the data files that came in a zip file to the /usr/share/games/dangerdeep folder .

No luck

Thank you
Allen

---

### Post by sad_iq on 2007-07-19
It should be ```
sudo cp -r fonts /usr/share/games/dangerdeep
``` The -r stands for recursive...it will copy the fonts folder with all the files inside!!

---

