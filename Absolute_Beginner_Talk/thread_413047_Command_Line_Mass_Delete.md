---
title: "Command Line Mass Delete"
date: 2007-04-18
forum: Absolute Beginner Talk
---

### Post by sunexplodes on 2007-04-18
Today I've been sorting a lot of downloaded mp3s, and I'm finding a lot of instances of "thumbs.db" and "desktop.ini" among others.

If, in terminal, I go:

locate "desktop.ini"

it'll spit me out a list of all of the files by that name. Is there a flag I can add to the Locate command to have it delete all instances of a file?

---

### Post by sessine on 2007-04-18
you could try something like 
```
for file in `locate "desktop.ini"`
\rm $file
done

```

I think that syntax is right for bash,I'm more familiar with c-shell.  However, it is a bit risky since there is no way to reverse it so it would be worth doing the locate command first and checking the list of files to make sure you don't inadvertently delete something you need.

---

### Post by Tundro Walker on 2007-04-18
If you're dual-booting Win & Ubuntu, you might want to keep your desktop.ini and thumbs.db files in your Windows partition / boot up.  Those are hidden Windows files, and I think they log what's in the folder and how it's to be displayed (IE: so it can use individual folder settings).

Now, if you're just scrounging through an old Win disk you don't care about using with Windows anymore, then just bump all that stuff off.  Better yet, just find what you want, move it someplace into Ubuntu to keep, and then reformat the partition (EG: using gparted) to remove all the rest of the junk w/o having to delete it all.

---

### Post by WW on 2007-04-19
You could use the **find** command.  For example, to remove all occurrences of "desktop.ini" in the current directory and all subdirectories:
```

$ find . -name desktop.ini -exec rm {} +

```

---

### Post by sunexplodes on 2007-04-20
I wasn't dual booting, desktop.ini and thumbs.db just show up in a lot of folders i download. 

I eventually just used the search feature in nautilus, which, despite never working well for me in the past, seemed to do the trick.

Thanks for the suggestions, though!

---

### Post by Famicommie on 2007-04-20
> **sunexplodes said:**
> I wasn't dual booting, desktop.ini and thumbs.db just show up in a lot of folders i download. 

I eventually just used the search feature in nautilus, which, despite never working well for me in the past, seemed to do the trick.

Thanks for the suggestions, though!

Not to bump a resolved thread, but.. BLESS YOU SIR. I have been trying to figure out a good way to do that for months.

---

### Post by Yellow Onion on 2008-02-14
desktop.ini and thumb.db aren't inportant. ones a pre-cache for thumb nails, deleting sometimes helps tell windows that theres been an update to the file and desktop.ini is folder look settings like background picture and weather you prefer list or Icon view
I delete them all the time

---

