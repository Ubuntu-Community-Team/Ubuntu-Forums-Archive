---
title: "Oh NO!!!!"
date: 2007-01-19
forum: Absolute Beginner Talk
---

### Post by qwazert on 2007-01-19
I just replaced my video card and now I get the message that Xserver won't start! I've tried doing:

sudo dpkg -reconfigure xserver-xorg 

from the command line, but all it does is give me a list of dpkg options. What have I done and how can I fix this??? I don't want to use Wiindose!!!!

---

### Post by ciscosurfer on 2007-01-19
> **qwazert said:**
> I just replaced my video card and now I get the message that Xserver won't start! I've tried doing:

sudo dpkg -reconfigure xserver-xorg 

from the command line, but all it does is give me a list of dpkg options. What have I done and how can I fix this??? I don't want to use Wiindose!!!!The correct command is```
sudo dpkg-reconfigure xserver-xorg
```

---

### Post by taurus on 2007-01-19
```
sudo dpkg-reconfigure -phigh xserver-xorg
```
Did you change from what video card to which video card?

---

### Post by llamakc on 2007-01-19
> **qwazert said:**
> I just replaced my video card and now I get the message that Xserver won't start! I've tried doing:

sudo dpkg -reconfigure xserver-xorg 

from the command line, but all it does is give me a list of dpkg options. What have I done and how can I fix this??? I don't want to use Wiindose!!!!

For starters use a better & more descriptive subject when you make a post to help others help you.

The command should be:

sudo dpkg-reconfigure xserver-xorg

Note that there's no space between dpkg & -reconfigure

Next, if the debconf prompt is in front of you with choices, you now have to chose them. When it gets to the part about which driver to use, use the one that corresponds to your card.

If you would have originally posted that "I have card XXX, which driver should I use when reconfiguring xserver-xorg?" You'd have not only solved the problem but left a very informative post for others.

So, what sort of card did you put in?

---

### Post by qwazert on 2007-01-19
I recently (a few minutes ago) changed my video card to a VooDoo3 PCI.
Now, all I can do is boot to command line in SAFE mode...X will not start, no matter what I do!
I ran the "lspci -x" command and found my video card at 2:0a.0 yet X says it doesn't exist!

What did I do and how can I fix this....I hate running windows, but I'd rather do that than reload this all over again!!!!

---

### Post by riven0 on 2007-01-19
Then I'm guessing you already did a reconfiguration? How about choosing Vesa as your graphics driver? Have you tried that yet?

---

### Post by taurus on 2007-01-19
I merged your two threads since they are the same problem.

---

