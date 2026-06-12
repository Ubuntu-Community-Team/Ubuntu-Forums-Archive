---
title: "Gone with the Wind"
date: 2006-09-06
forum: Absolute Beginner Talk
---

### Post by thedivvyman on 2006-09-06
Hi everyone - I have had ubuntu installed for nearly two weeks now, and like I said before, I love it, I know nothing about how it works -but I love it. I have posted quite a few times on here about different things, but I'm afraid to say I am struggling a bit. Very often I get advice on certain things, but in most cases, along with the advice, a link is provided which will send me to a tutorial. Now I think it is probably me, but it seems like the authors of these articles presume the reader to have substantial knowledge. I have absolutely none. My interest in computers started  in Windows 98  to  Millenium  days, therefore  I have no knowledge of dos, except I knew it existed. I find the Manuals in ubuntu hard to follow so if anyone could start me off at the terminal and some simple commands (and what they do) and when to press enter, I would be grateful.
An example: I have tried to install flash player. I have tried manually following tutorials with no joy - I have tried using Synaptic package manager, and had no luck. So now I think to myself is there half the files installed or what?
I still can't stream video on  the interweb that's for sure.
I really want to learn this stuff so if anyone can  help, I would appreciate  it. 
Sorry this post is a bit like "Gone With the Wind" but I just wanted to get my point accross.:???: :???: :???: 
Great  forum  BTW

Thanks in advance

---

### Post by aysiu on 2006-09-06
Even though they may *look* intimidating, these terminal-command tutorials aren't as hard as you think they are.

First of all, learn to copy and paste--retyping is for the birds. Retyping commands takes longer, and you're likely to mess up (natural human error). You might miss a letter or forget upper- and lower-case matter. Copy is **Control-C**. Paste in the terminal is **Shift-Insert.**

After every command you enter, press **Enter** to have that command take effect.

For example, if a tutorial says > Use these commands: ```
sudo aptitude update
sudo aptitude install flashplugin-nonfree
``` You would highlight *sudo aptitude update*, copy it, paste it in the terminal and then hit **Enter**. Then you would highlight *sudo aptitude install flashplugin-nonfree*, copy it, paste it in the terminal and hit **Enter** again.

For Flash, for example, do this:

**Step 1**: Close your web browser.

**Step 2**: Enable extra repositories (more software available to install) by following these instructions:
[http://www.psychocats.net/ubuntu/sources](http://www.psychocats.net/ubuntu/sources)

I promise--it's copy and paste, just as I described it before.

**Step 3**: Paste this command into the terminal: ```
sudo aptitude update && sudo aptitude install flashplugin-nonfree
```

**Step 4**: Start your web browser again.

---

### Post by xpod on 2006-09-06
> Even though they may look intimidating, these terminal-command tutorials aren't as hard as you think they are

Click ,drag,click,enter...click,drag,click,enter etc etc.WHAT could be easier?

EDIT:.....or HIGHLIGHT,CLICK,ENTER.....(can follow tutorials but still getting terminology wrong)...lol

---

### Post by shoot2kill on 2006-09-06
i can see where this guy is comin from, wen i first started, i kind of overlooked it was just copy n paste, cos it seemed so easy, and linux was so hard (my first thought) i thought i had to understand and change/configure the terminal commands

but yeah, Copy n paste..

---

### Post by aysiu on 2006-09-06
> **shoot2kill said:**
> i can see where this guy is comin from, wen i first started, i kind of overlooked it was just copy n paste, cos it seemed so easy, and linux was so hard (my first thought) i thought i had to understand and change/configure the terminal commands

but yeah, Copy n paste..
I didn't overlook copy and paste. When I first started, nobody told me you *could* copy and paste. Now, whenever I can remember to, I always favor > copy and paste these commands into the terminal over > type these commmands into the terminal I didn't realize at first you could copy and paste. And it took me even longer to realize you could drag and drop into the terminal.

---

### Post by shoot2kill on 2006-09-06
ohh, yes definately.. at first i was the same.. Ctrl + V in the terminal, just gave me a nice

> 
^V


:D :D :D

---

### Post by marklid on 2006-09-06
... or if you have a 3 button mouse, highlight the text, then middle click in  the terminal window to paste the highlighted text !

---

### Post by shoot2kill on 2006-09-06
yeah sure... ****DONT REALLY KNOW***

but i would not give this as advice, as my middle button is assigned differently.. lol

---

### Post by Mimsy on 2006-09-06
Last week or so, the first time somene suggested a terminal command to fix a problem I had, it was such a long one that I didn't dare typing it, in case I messed it up. I highlighted it, right-click -> copy, then opened the terminal, Edit -> Paste. Enter.

The problem went away.

I felt really smart. Hehe. :-)

/Mimsy

---

### Post by shoot2kill on 2006-09-06
thats it exactly, i followed a guide about installing new software.. and it was just multiple C+P's (bout 40) and wen it was all done, i had the biggest smile on my face, and felt like a linux Pro... :D :D :D (now i know different.. lol)

---

### Post by petri on 2006-09-06
One more? 

Highlight with left mousebutton - paste with mousewheel click (everybody has those?)

...and one more, in terminal Edit - Preferences and there chance Shift Ctrl V to what you want...


EDIT: ...too slow :???:

---

### Post by shoot2kill on 2006-09-06
> **petri said:**
> One more? 

Highlight with left mousebutton - paste with mousewheel (everybody has those?)

...and one more, in terminal Edit - Preferences and there chance Shift Ctrl V to what you want...
nope, i dont have the mouse wheel shortcut.. i have wheel, but middle button is not paste.. :D :D :D

---

