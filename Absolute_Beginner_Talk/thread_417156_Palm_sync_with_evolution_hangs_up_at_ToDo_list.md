---
title: "Palm sync with evolution hangs up at ToDo list"
date: 2007-04-21
forum: Absolute Beginner Talk
---

### Post by C-A on 2007-04-21
I am using gpilot to sync my palm zire with evolution in Feisty. Initially, it does fine but then hangs up when it gets to my ToDo list. Everything before the ToDo list seems to sync fine.

I can disable syncing with the ToDo list and the entire sync goes fine and does not hang up.


Ideas?

---

### Post by eapache on 2007-04-21
Does your to-do list have any funny entries in it? (entries with accents or do-dates that don't exist or something?) They might be confusing gpilot. Other than that, the only thing I can think of is that the zire is such an old model that gpilot cannot support it without losing support for newer models like the Z22.

---

### Post by C-A on 2007-04-21
> **eapache said:**
> Does your to-do list have any funny entries in it? (entries with accents or do-dates that don't exist or something?) They might be confusing gpilot. Other than that, the only thing I can think of is that the zire is such an old model that gpilot cannot support it without losing support for newer models like the Z22.

Thanks for the reply. Your post lead me in the right direction. I looked for funny entries and realized the task where gpilot would hang at did not have a due date and was not assigned a category (work/personal). I gave it a due date and assigned a category and it worked. Not sure which thing caused the problem because I didn't make the changes one at a time but at least its working.

---

### Post by eapache on 2007-04-22
It's good that it's working. Was the category of the item 'unfiled' or did it have no category at all?

---

### Post by C-A on 2007-04-22
> **eapache said:**
> It's good that it's working. Was the category of the item 'unfiled' or did it have no category at all?

Not sure now if it was unfilled or didn't have a category listed at all but I am glad its working. Feisty has been the easiest distro for me so far to get gpilot to work.

---

### Post by elyk on 2007-05-02
I've got a similar problem, but mine also hangs when it goes to synchronize the calendar. The computer sitll shows that it's syncing, but the pilot throws a "connection lost" dialog and turns off. It's weird that I'm experiencing these problems because hotsync worked perfectly fine before I upgraded from edgy.

---

### Post by Hiko96786 on 2007-05-11
Aloha,
   Checking all of my todo's I hade them unfiled and no due dates, fixing that it worked great. I bet there is something in the calendar that is causing it to hang up that is similiar.
Mahalo,
Hiko

---

