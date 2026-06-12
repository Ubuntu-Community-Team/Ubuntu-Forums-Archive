---
title: "Nautilus can't be used now, due to an unexpected error."
date: 2007-09-18
forum: Absolute Beginner Talk
---

### Post by S15_88 on 2007-09-18
quick question, never encountered this before and i'm quite puzzled.  i open my home folder, go to a folder called "school" then "psych" and when the folder opens in the bottom left corner it says 5 files...and the size, but none of the files are visible! and then the folder has to be force quit.  then my home folder opens back up and this error pops up:
> 
Nautilus can't be used now, due to an unexpected error.
more details:
Nautilus can't be used now, due to an unexpected error from Bonobo when attempting to locate the factory.Killing bonobo-activation-server and restarting Nautilus may help fix the problem.


what puzzles me the most is that when i go to the terninal and navigate to the folder and type: ls, it shows all the names of the files.  when i do: sudo nautilus it opens it up and when i go to the psych folder everything is there and behave's normally!

why when i go to the psych folder regularly through my home folder it goes haywire!  

any help would be greatly appreciated!

Thanks, Alain

---

### Post by Tommy on 2007-09-18
> **S15_88 said:**
> when the folder opens in the bottom left corner it says 5 files...and the size, but none of the files are visible! and then the folder has to be force quit. 


Have you tried logging out and back in? That SHOULD kill off and restart any errant GNOME processes that are stuck.

If that doesn't work, try rebooting, and also check your dmesg for any strange errors (open a terminal and type "dmesg").

---

### Post by S15_88 on 2007-09-18
i've logged on and off several times and also rebooted several times.  i managed to get the files i needed and copy them and i downloaded the lecture notes again so i have everything back to normal, i was forced to delete the previous folder.

any ideas on why this happened and how i could've fixed it!  that would not have been good if i lost all my school work!

---

### Post by Tommy on 2007-09-19
I have a few guesses, but that's all they are. Feel free to add your own...

It could have been a permissions issue -- if you had logged in and messed with some files in those directories as root (using sudo for instance), you may have uncovered a bug in Nautilus regarding permissions.

It's also possible you had some corrupted files due to a hardware issue. Your hard drive may have had a glitch or whatever.

And if you never see the issue ever again, I would definitely blame cosmic rays. see [http://neutronm.bartol.udel.edu//listen/main.html](http://neutronm.bartol.udel.edu//listen/main.html)

> A single cosmic ray particle can change a computer memory cell, or change a chromosome in a reproductive cell.

As a computer tech I frequently fell back on that explanation when we could determine nothing else.

---

### Post by docinsano on 2007-10-05
I've read alot of other threads regarding this issue but I can't find a solution. I'm having this same problem with nautilus on ubuntu with my imac g3. I read something about updating Nautilus, but other than that no dice.

---

### Post by usererror on 2008-05-27
I am having this issue to, it's gotta be a permissions thing.  I got it as soon as I removed nearly every right to a user via the permissions option in the Settings menu.  I am making a Kiosk so I don't mind there's no nautilus...but it's still weird.

---

### Post by Tommy on 2008-05-27
> **usererror said:**
> I am having this issue to, it's gotta be a permissions thing.  I got it as soon as I removed nearly every right to a user via the permissions option in the Settings menu.  I am making a Kiosk so I don't mind there's no nautilus...but it's still weird.

So this supports the theory that it's a permissions error. 

I would suspect with a kiosk, some other applications you may be using MIGHT also demonstrate unusual bugs if there are NO writeable directories. It seems like it would be easiest to have a small home partition (limit the size of whatever files might get written) and give that user all the normal non-administrative permissions in Ubuntu EXCEPT remove them from sudoers. But I haven't done this so you're the expert!

With the original poster, I would suggest logging in as a normal user and then using Terminal to chmod and chown all the files in the home directory -- I bet there's a directory and/or file having unusual permissions. (The problematic file or directory may even be hidden.)

---

