---
title: "nautilus scripts..."
date: 2006-11-28
forum: Absolute Beginner Talk
---

### Post by serosis on 2006-11-28
How exactly do you get nautilus scripts to work?

i have a "root-nautilus-here" and a "root-terminal" script in my 'nautilus-scripts' directory, yet they aren't showing up at all.

is there some sort of installation process or a specific filename extension or for that matter a file name format?

it'd be kinda nice to have these scripts work (although i probably don't need the root-nautilus-here script since i have an launcher on the desktop).

---

### Post by 23meg on 2006-11-28
Make the script executable if it isn't, and place it in your ~/.gnome2/nautilus-scripts folder. 

You may also find [this trick]("http://www.ubuntuforums.org/showthread.php?t=24008") useful if you're interested in root-nautilus-here.

---

### Post by serosis on 2006-11-28
making it executable...

oh thats just changing the permissions right?

well, why didn't I think of that :/

---

### Post by lapsey on 2006-11-28
> **serosis said:**
> making it executable...

oh thats just changing the permissions right?

well, why didn't I think of that :/

i think so, but chmod a+x is all i know

---

### Post by 23meg on 2006-11-28
No, the executable flag is independent. Use *chmod +x * or right click the file, go to Properties / Permissions and check the "Allow executing file as program" checkbox.

---

### Post by xopher on 2006-11-28
You should also take a look at nautilus-actions [(http://www.grumz.net/?q=taxonomy/term/2/9)]("http://www.grumz.net/?q=taxonomy/term/2/9")

I used to use nautilus scripts, but this is just so much smoother ;) Better integrated with the interface.

---

### Post by serosis on 2006-11-28
cool, thanks guys

---

### Post by serosis on 2006-11-28
oh and quick question...

how do you get rid of "Quit..." from the system menu on the toolbar?

---

