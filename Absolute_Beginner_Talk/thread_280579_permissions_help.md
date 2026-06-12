---
title: "permissions help"
date: 2006-10-19
forum: Absolute Beginner Talk
---

### Post by pregoeater on 2006-10-19
ok so when i first got ubuntu i could not get access to all my folders so i typed in a code in the terminal to give me access to EVERYTHING i now know that it was not such a good idea can i undo that somehow?


thanks
pre

---

### Post by grim918 on 2006-10-19
What exactly did you type into the command line to give you access to everything.

---

### Post by kernco on 2006-10-19
You'll have to reset everything by hand.  I don't know whether you did "chmod 777" on everything, or whether you did "chown" to make you the owner of everything.  Depending on what you did, either "chmod" everything back to protected or "chown" everything back to root, then give yourself permission or ownership of everything in /home/your-username.

---

### Post by kernco on 2006-10-19
I guess I should provide exact commands since this is a beginner forum.

If the command you used before started with "chown", then do this:
$ sudo chown -R root /
$ sudo chown -R username /home/username

If the command you used before started with "chmod", then do this:
$ sudo chmod -R 755 /

DON'T DO THIS YET.  I'm not that confident in my Linux ability, so I want someone else to verify that this is the correct thing to do.

---

### Post by pregoeater on 2006-10-19
i have no clue which one i used it was 3 weeks ago, my  first day i installed. I found the command in the forum and typed it in.


thanks
pre

---

### Post by bodhi.zazen on 2006-10-19
Without knowing the command it is hard to know how to advise you.

Perhaps if you did a search in the forums you could find the post you followed and recall the command.

No offense, but I would NOT follow the advice of kernco.

Either:[list=number][*]Reinstall Ubuntu.[*]Make yourself a new user. In this case add the new to the admin group.[/list]

To jog your memory:

Did the command involve visudo or gksudo?

---

### Post by pregoeater on 2006-10-19
im pretty sure it was the one with 777 in it



pre

---

### Post by bodhi.zazen on 2006-10-19
Let me look at my sys later tonight.

I can advise a series of chmods, but I do not want to guess.

You may want to consider re-installing. It may be faster.

---

