---
title: "simple issue, have i gone mad?!?!"
date: 2005-07-11
forum: Absolute Beginner Talk
---

### Post by NaOH on 2005-07-11
i'm new to ubuntu, but quickly catching on.  There is one thing that perplexes me, and i've pulled out some hair over this seemingly simple issue.  I can navigate fine through the terminal, except within my home directory.  For instance, getting to my desktop is seemingly impossible.  I enter "cd /home/x55/desktop" and the response is always "no such file or directory."  I'm dumb, what the heck am i forgetting?  ](*,)

---

### Post by Kvark on 2005-07-11
Directory and file names are case sensitive. Thus /home/x55/desktop, /home/x55/DESKTOP and /home/x55/deSkToP are all entirely different directories then /home/x55/Desktop.

---

### Post by Knome_fan on 2005-07-11
It's Desktop, not desktop.

And tabcompletion is your friend.  :wink: 
Type cd /home/x55 and press tab and it will show you all the directories you can access under /home/x55.

Type cd /home/x55/D and press tab and it will automplete the path to /hoe/x55/Desktop if there is only this one directory starting with a D.

---

