---
title: "Enemy Territory 2.60b how?"
date: 2008-01-22
forum: Absolute Beginner Talk
---

### Post by whoscheesemine on 2008-01-22
I am currently using this guide to Insall Wolfenstein: Enemy Territory.

[HTML]https://help.ubuntu.com/community/EnemyTerritory[/HTML]

Everything is completely hunky dory except for the fact that the guide doesn't tell me how to update 2.60 to 2.60b. In the guide it just said to change the file name to download the appropriate version, but that came back with a 404. So I found sites that offer a zip file of the et.x86 and the etded.x86 files that I have to replace with the one's I have to update to 2.60b. It won't allow me to replace those files as I do not have permission. If someone could give me a terminal command or two to take care of this that'd be great, or if someone could give me a terminal command that would allow me to replace those two files that'd be great as well. (a little redundant) I saw a post similar to this but it didn't help me at all. Thanks a lot. You guys have been more than helpful helping me to understand this OS a little better day by day. Also, if anyone feels like explaining things in a "why" type attitude don't feel the need to keep your mouth shut. I'd love to hear it!:popcorn:

---

### Post by bvanaerde on 2008-01-22
There are two options:

Option 1:
Open the terminal, go to the directory where you extracted those files, and type:
```
sudo cp et.x86 /usr/local/game/enemy-territory/
sudo cp etded.x86 /usr/local/game/enemy-territory/
```
*I'm assuming you installed the game in the default directory.*

Option 2:
```
gksudo nautilus
```
This will open your file browser, but with admin rights. This way, you can copy the files like you're used to. But [COLOR="Red"]**be careful**[/COLOR] with this, as it's quite easy to do something wrong this way!

---

