---
title: "Xmodmap at Startup"
date: 2006-07-17
forum: Absolute Beginner Talk
---

### Post by kaje on 2006-07-17
It appears I have mapped two keys wrong and everytime I boot up I have to run xmodmap ~/.Xmodmap to get the keys working again. The first time I created the file and restarted X, I had a window that popped up asking me which Xmodmap file I want to use. I don't see that anymore to switch it to the correct one. Can anyone tell me how to go abut getting that back so I can correct my problem? Thanks.

---

### Post by xXx 0wn3d xXx on 2006-07-17
1. create a new test file. Name it xmodmap with no extension.

2. Type: "#! /bin/bash" --no quotes at the top

3. Type the command you want to execute on a line after that.

4. Save it and make it executible. >  
sudo chmod 777 /path/to file/

5. Move it to /usr/local/bin

6. Under System > Prefrences > sessions on the far right tab add "xmodmap."

---

### Post by kaje on 2006-07-18
danke!

---

