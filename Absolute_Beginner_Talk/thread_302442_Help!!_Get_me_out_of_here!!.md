---
title: "Help!! Get me out of here!!"
date: 2006-11-18
forum: Absolute Beginner Talk
---

### Post by Anaphylaxis on 2006-11-18
I am following this [how to]("https://help.ubuntu.com/community/Installation/LowMemorySystems"), and I am doing a server install of linux. 

Now I am editing my sources.list so that I can get fluxbox. But how the hell do I get back to the command line from the sources list? What to type? There are no WINDOWS damnit!! :-D

---

### Post by Arisna on 2006-11-18
Hit escape.  Now type a colon.  It should appear at the bottom of the screen.  Type a "q" (no quotes) and hit enter.  This will quit the editor.  Put a "w" before the "q" to save your changes, or follow the "q" with a "!" if you want to quit and discard changes.

---

### Post by namah on 2006-11-18
what are you using to edit the sources list. Are you already in fluxbox? more info

---

### Post by Anaphylaxis on 2006-11-18
Thank YOU!!! But the bastard still won't find fluxbox.. :confused:   

Hmm.. more sources editing to be done, I guess. But huge thx. *hug

---

### Post by Anaphylaxis on 2006-11-18
> **namah said:**
> what are you using to edit the sources list. Are you already in fluxbox? more info

I am using my keyboard. I haven't got any desktop manager. Server install. Fun. See what I can figure out. Complete n00b.. :p

---

### Post by Anaphylaxis on 2006-11-18
Hmm.. one more thing, if I can be a bit cheeky. How do I get backspace and return to actually make changes in the document, like erase and new page, without just moving the cursor around?

---

### Post by janne5011 on 2006-11-18
i dont know what u use but use nano

nano myfile
edit the file then
for saving
ctrl+x
then "y"
then enter
thats it
thoose other editors like vi or vim is not a chocice when new to linux.

---

### Post by IYY on 2006-11-18
vi is a wonderful editor, but it's certainly not for beginners. It takes a week or so to learn.

As suggested above, use nano for now.

---

### Post by mips on 2006-11-18
If i was you I would not use vim but nano instead, much easier for people like myself. It has a little menu at the bottom that explains all the keys etc.

```
sudo nano /etc/apt/sources.list
```

For fluxbox you need to enable the **Universe **repositories.

Followed by

```
sudo aptitude update
sudo aptitude install fluxbox fluxconf x-window-system-core xdm dillo synaptic
```

---

### Post by Anaphylaxis on 2006-11-18
Ha, I found out!! You have to hit the "i" button to swap modes in vim. Small tutorial can be found here: [another vim tutorial]("http://tips.webdesign10.com/another-vim-tutorial")

On my way to get fluxbox installed.. veeeery excited to find out whether I am able to use it or not.

Thanks for the help, guys.

---

### Post by aysiu on 2006-11-18
Edit your repositories list while also backing it up: ```
sudo nano -B /etc/apt/sources.list
``` You can enable extra repositories by removing the # sign from any line starting with the word *deb*.

To save, press Control-X, Y, then Enter.

Finally: ```
sudo aptitude update
sudo aptitude install fluxbox
```

---

