---
title: "Non-GUI text editing."
date: 2006-10-09
forum: Absolute Beginner Talk
---

### Post by equal on 2006-10-09
Sooo... I'm not a newb, but this feels like a newb question. I messed up my /etc/X11/xorg.conf file, and now X won't load. I'm running from the Dapper live CD at the moment. 

When my computer boots up, I have two questions

1- what is a command line text editor i can use. gedit won't work, im guessing because it's a GUI app.

2- how do I go about editing line 54 (the one I'm having trouble with)

---

### Post by alpv on 2006-10-09
Hello,

1) "vi <file>", where <file> is the one you need to edit. 

2) When you enter the vi environment, type "/54", that will put you in line 54.

3) Press "i", so you can insert text and edit the line.

4) Press "esc"

5) Type ":wq" to save and quit

File should be updated.

-Andrés

---

### Post by dmizer on 2006-10-09
some like vi, but i find the commands to be illusive (you have to know them before using vi).  i suggest nano, as the command functions are displayed below the text area.
```
sudo nano /etc/X11/xorg.conf
```

---

### Post by reacocard on 2006-10-09
You can use nano. It's very easy to use, just use the arrow keys to change where the cursor is. In the little command bar at the bottom, ^ means CTRL, so ^O (save) would be CTRL+O. A screenshot is attached so you can see what its like.

---

### Post by equal on 2006-10-09
phew! vi was scaring me. nano should do the trick. Thanks so much. With any luck, I'll be back up in 3 mins!

---

### Post by equal on 2006-10-09
ugh that didn't work. sigh. you know when they tell you to make a backup of the file, and you think "pfffffffffffft backup". yeah. go me. 

The problem I'm having is this: I tried following the advice given on this page [here]("http://http://www.cs.cornell.edu/~djm/ubuntu/") to configure a 5 button mouse (which, if I'm not mistaken should be called a 7-button mouse). 

Now I get an error saying line 54 of my xorg.conf file is causing a problem , that "..." is not a valid option.

I tried changing it to what's written in the how-to page. doesn't work. Tried changing it to what's written as the old setup, doesn't work.

If I'm not mistaken though, my original xorg file didn't say 
Option		"Protocol"		"ExplorerPS/2"
It had something other than ExplorerPS/2

any ideas?

---

### Post by lemonsCC on 2006-10-09
My line 54 says >  Option          "CorePointer"

> Option          "Protocol"              "ExplorerPS/2"
  is on line 56

---

### Post by bodhi.zazen on 2006-10-09
> **equal said:**
> ugh that didn't work. sigh. you know when they tell you to make a backup of the file, and you think "pfffffffffffft backup". yeah. go me. 

The problem I'm having is this: I tried following the advice given on this page [here]("http://http://www.cs.cornell.edu/~djm/ubuntu/") to configure a 5 button mouse (which, if I'm not mistaken should be called a 7-button mouse). 

Now I get an error saying line 54 of my xorg.conf file is causing a problem , that "..." is not a valid option.

I tried changing it to what's written in the how-to page. doesn't work. Tried changing it to what's written as the old setup, doesn't work.

If I'm not mistaken though, my original xorg file didn't say 
Option		"Protocol"		"ExplorerPS/2"
It had something other than ExplorerPS/2

any ideas?

LOL :lol: Restore from backup.

He he he...

Try this;

```
sudo dpkg-reconfigure -phigh xserver-xorg
```

If that works [color=darkred]BACKUP !!![/color]

---

### Post by equal on 2006-10-09
CorePointer implies to me that you've got a laptop, and a touchpad. I do not.

---

### Post by lemonsCC on 2006-10-09
Umm if it thinks I have a laptop and touchpad there are some serious issues here becuase this would be an ENORMOUS laptop.  :p  This is a desktop.

---

### Post by equal on 2006-10-09
**lemonsCC**: haha  bahh I don't know enough about this. My roommate's laptop said that, so I pretended I knew something.

**bodhi.zazen**: Thanks bud! that did it!

---

### Post by comppsyco on 2006-10-09
You know, it might be worth it to learn how to use vi for later reference. The best way to do that, I think, is to use vimtutor (just type it in at the prompt)

---

### Post by bodhi.zazen on 2006-10-09
> **comppsyco said:**
> You know, it might be worth it to learn how to use vi for later reference. The best way to do that, I think, is to use vimtutor (just type it in at the prompt)

Start with nano, migrate to vim.

---

### Post by lemonsCC on 2006-10-09
equal:  no problem glad its working anyhow.

Why get used to vi when nano isn't going anywhere?

---

### Post by dmizer on 2006-10-10
> **lemonsCC said:**
> Why get used to vi when nano isn't going anywhere?

i agree.  i never really understood why people cling to vi.  i've never encountered a situation i couldn't resolve with nano.  text copy and paste was pretty difficult at first but i can still do it.

what's the catch?

---

### Post by n0dl on 2006-10-10
well there are several superb text editors that do not require X, such as emacs, vi(m), nano, pico etc. But in your case, i would go something simple, such as nano or pico at first (just to get the job done). While I actively promote the usage of vim over any text editor, learning the basics at the moment might not be in your best interest (unless you can wait and stay in CLI for a couple of more, hours or days depending on how well you could understand the various guides on the internet.) If you choose to use vim i suggest you read the cheatsheet guide gentoo has on their site in their desktop documents page. Good start.

---

