---
title: "Gimp remove multiple color channels"
date: 2011-06-19
forum: Art &amp; Design
---

### Post by Lolpanda on 2011-06-19
Alright so I'm working on a wallpaper for a friend and while screwing around in gimp, I found the Channels dialog. Took out green and blue to give the entire image a blood red-ish look to it and it looked really cool. (Im a noob with gimp so thats why what follows.. follows) 

Figured that if I saved it, it would ACTUALLY remove the colors, not just show it as "This is what it would look like if..." I was wrong. Spent the last hour googling around trying to find my answer, one link I found was an ubuntuforums post that described how to remove a single color layer (which worked fine) [http://ubuntuforums.org/showthread.php?t=1404416](http://ubuntuforums.org/showthread.php?t=1404416)

But I can only get it to work for JUST green or JUST blue, not both. Was hoping someone could walk me through how to do it.

---

### Post by prokoudine on 2011-06-20
*"Layer > From visible"* will always create a new layer with whatever your have in front of you. Disable color channels, run this command from menu, and you can save/export the file: since the top layer contains what you had when you disabled some channels, you'll see what you want.

Update: [here]("http://libregraphicsworld.org/articles.php?article_id=36") is a more complete write-up on the subject.

---

