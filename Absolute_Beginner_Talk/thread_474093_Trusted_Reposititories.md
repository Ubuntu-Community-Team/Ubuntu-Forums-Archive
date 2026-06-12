---
title: "Trusted Reposititories?"
date: 2007-06-14
forum: Absolute Beginner Talk
---

### Post by alecwh on 2007-06-14
Sorry, I'm SURE I spelled that wrong. 

Are there additional "repositionories" that I can add which will give me a lot more application choice in Symtimatic?

Thanks, sorry, I have no idea how to spell it.

---

### Post by BlahMan_of.Doom on 2007-06-14
Add the universe and multiverse repos's.

---

### Post by Inxsible on 2007-06-14
you can add the medibuntu reps and the tuxfamily reps for some cool apps that you might wanna try out

---

### Post by kittyhawk63 on 2007-06-14
> **alecwh said:**
> Sorry, I'm SURE I spelled that wrong. 
Are there additional "repositionories" that I can add which will give me a lot more application choice in Symtimatic?
Thanks, sorry, I have no idea how to spell it.

If you have a mouse with a roller wheel you can **highlight** a command and in Terminal press the wheel down and it will paste the command. You do not have to use right click <copy> and then right click <paste>. The mouse wheel will do it for you.

Do you know how to open the Terminal and type in commands? If you do, copy/paste [COLOR=Red] gksudo gedit /etc/apt/sources.list [/COLOR]into Terminal:
hit <enter> on keyboard

A page will appear.
Remove the [COLOR=Red]# [/COLOR]in front of any "[COLOR=Red]deb[/COLOR]" lines.
Save

Close that page

Now copy/paste [COLOR=Red] sudo apt-get update[/COLOR] into Terminal:
hit <enter> on keyboard

While you're at it copy/paste [COLOR=Red] sudo apt-get upgrade [/COLOR]into Terminal:
hit <enter> key on keyboard
That should get you up-to-date. Remember to add the other repositories mentioned earlier.

---

### Post by alecwh on 2007-06-14
Thanks kittyhawk. I opened that file, but there wre no "dub" lines that had #'s before them.

But that is what I"m lookin for, a way to get a LOT more packages.

---

### Post by kittyhawk63 on 2007-06-14
> **alecwh said:**
> Thanks kittyhawk. I opened that file, but there w[COLOR=Red]e[/COLOR]re no "d[COLOR=Red]e[/COLOR]b" lines that had #'s before them.
But that is what I"m lookin[COLOR=Red]g[/COLOR] for, a way to get a LOT more packages.

Glad I could help. Save this thread and you can assist someone else with these instructions. (The [COLOR=Red]red[/COLOR] letters betray the teacher in me.)
kh

---

### Post by Nythain on 2007-06-14
hehe... i think the file they were trying to point you to is /etc/apt/sources.list
i on habbit of typign the two regularly have cought myself typing the wrong one for a certain situation :)

also as mentioned, google medibuntu to get to thier site with instructions on how to add thier repo to the list

uncomment the multiverse and universe repos that are already in teh list

havent tried the tuxfamily repos myself so i cant tell you much about them

---

### Post by kittyhawk63 on 2007-06-14
Thanks Nythain. You're right. It is:  /etc/apt/sources.list I made the correction. Thanks again.
kh

---

