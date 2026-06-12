---
title: "How to install a .run file"
date: 2007-05-29
forum: Absolute Beginner Talk
---

### Post by NewJack on 2007-05-29
I need some help.  I downloaded the following file from Sourceforge so that I could install UFO: Alien Invasion:

ufoai-2.1.1-linux_hotfix2.run

This is supposed to be a package installer, but when I click on it from the Desktop nothing happens.  No installation occurs at all.  What am I doing wrong?  Is there some command line that I should be running to get this file to work or do I have to convert it to get it to install in Ubuntu?

Thanks in advance!
Joe

P.S.-  I wasn't sure whether to post this here or in the Gaming section?

---

### Post by Sparkster185 on 2007-05-29
Do you know if it's just a shell script?  What happens if you less or cat the file?  If you see something like

#!/bin/bash or #!/bin/ksh at the top of the file, it's a shell script.

If it is, to run it all you need to do is (assuming it's called something.run)

```

sudo sh ./something.run

```

---

### Post by lazyart on 2007-05-29
it needs execute permissions as well.```
cd ~/Desktop
sudo chmod +x ufoai-2.1.1-linux_hotfix2.run
```

From there you may or many not need to run it with sudo.

---

### Post by NewJack on 2007-05-29
Thank you for the response guys!

---

### Post by NewJack on 2007-06-04
Thanks for the tip lazyart, worked like a charm!

:D

---

### Post by Spam Banjo on 2007-09-19
Thanks guys. Helped me out too.

AGAIN!!

---

### Post by tormaser on 2008-02-15
hi guys, when i try to instal i got the next error:

Could not open the file /home/xxxxxx/ufoai-2.2-linux.run.

gedit has not been able to detect the character coding.
Please check that you are not trying to open a binary file.
Select a character coding from the menu and try again.

can u help me?

---

### Post by unoodles on 2008-02-15
try typing it without it ./
so you would be typing:

sudo sh <.run file>

---

