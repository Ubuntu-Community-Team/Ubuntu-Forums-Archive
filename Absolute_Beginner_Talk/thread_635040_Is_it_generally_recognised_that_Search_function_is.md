---
title: "Is it generally recognised that Search function is rubbish... or is it just me?"
date: 2007-12-08
forum: Absolute Beginner Talk
---

### Post by snuffy on 2007-12-08
I have been using ubuntu for a year or so, and dread having to search for something because i can't for the life of me try to get the bloody search function to work... even when i know the file is there.

in windows searching is the easiest thing to do in the world. in ubuntu it seems like 'they' don't want me to find anything! 

What is going on? am i stupid or is it generally known that search is useless?
is there a how-to? don't know why there should be one for something that should be easy to do.

you help is gratefully appreciated.

tim.

---

### Post by awthomp on 2007-12-08
Try Kerry Beagle search:

```
sudo apt-get install kerry
```

It works wonders.

---

### Post by davidc502 on 2007-12-08
Maybe I'm doing something different than you are because I have Ubuntu indexed, so searches are generally faster than in Windows, and I seem to find what I'm looking for.

Try this.. In command line, switch user to su, and run the following command. You can run the same command as a user, but you will get messages for the files you don't have rights to see.

find / -name java

The / in this command signifies the find command to look under root directory. You can also search for files this way in a particular directory like /home/david as well as do wildcard searches *.jpg etc.

Or you can do the same thing in GUI by going to places and then select "search". 

You probably already do this, but I thought I would throw it out there in case you didn't know.

David

---

### Post by apoth on 2007-12-08
Can't say I've ever used it, I use locate to find files by name and grep to find by contents. It works on all distros I've used so I guess I've stuck with it.

---

### Post by sourcemorph on 2007-12-08
well i find the inbuilt tool just about ok.. in 7.10 they also gave tracker... but i find it too moody, sometimes it gives awesome results, sometimes it just doesn't show any files... dunno what the prob is.

i tried beagle too, but its too resource heavy, i guess it always takes something like 30mb ram in the background.

---

### Post by mahiyar on 2007-12-08
Search from nautilus (ctrl + F) is as you describe "grumpy", but use menu>places>search for files. I feel that it gives better control. The new search tracker tool (erstwhile google desktop) also searches your mail. Mostly they have performed expectedly, havent tried testing yet.

---

### Post by arvevans on 2007-12-08
The original CLI (Command Line Interface) tool is always available:

[INDENT]sudo find /* -name *filename* -print[/INDENT]

Now if someone would just write a GUI wrapper around that as a search tool.

Arv
_._

---

### Post by GOREMEISTER on 2007-12-14
"Places - Search for files"

This tool seems to find files well, but when I try to drag and drop a large quantity (4200 jpegs)  of files to another folder, the search tool  just disappears and nothing is copied. This is basic functionality that should just work.

Since the search tool sucks, what is the best way to search for all of my pictures in multiple folders and have them copied into a single folder???

---

### Post by mahiyar on 2007-12-14
learn CLI commands -- find, locate, grep, pipes,wild characters and you will have greatest search functionality ever.

---

### Post by GOREMEISTER on 2007-12-14
I just tried Ctrl-F in Nautilus and it only found 512 files out of 13000??? What the heck?

---

### Post by GOREMEISTER on 2007-12-14
> **mahiyar said:**
> learn CLI commands -- find, locate, grep, pipes,wild characters and you will have greatest search functionality ever.

Hey, if I got rid of Gnome, my computer would be much faster too! Great idea, just use the CLI all the time!

But wait, I have other things to do with my life, like make money, instead of playing in the command line....

---

### Post by olejorgen on 2007-12-14
One hting that's really annoying is that I can't cut files from a search result.

---

### Post by philinux on 2007-12-14
i tried trackerd - it borked so removed it.

Gone back to using Places > Search for files

Then gksudo nautilus to do what ever with em.

Two windows side by side. a workaround but hardly satisfactory.

---

### Post by The Cog on 2007-12-14
As far as I can tell, the nautilus Go->Search For Files (Ctrl-F) is utterly broken and has been since I first tried it in Hoary. I suppose I ought to post a bug report, but you'd think they would have noticed themselves by now.

---

### Post by philinux on 2007-12-14
> **The Cog said:**
> As far as I can tell, the nautilus Go->Search For Files (Ctrl-F) is utterly broken and has been since I first tried it in Hoary. I suppose I ought to post a bug report, but you'd think they would have noticed themselves by now.

Agreed search from nautilus is borked but Places>Search seems to work fine.

---

### Post by rune0077 on 2007-12-14
Yep, I use Places > Searches too, and it works fine. Nautilus search doesn't: it's fairly useless if you ask me.

---

### Post by The Cog on 2007-12-14
Ooh. You're right.

Y'know, I had always assumed that Places->Search would be the same search tool as the nautilus one (which I already found was broken), so I never even tried it. 

Thanks for enlightening me.

---

### Post by philinux on 2007-12-14
Caveat,

Places > Search as it says on the tin searches for files (file names containing) only. It will not show directories.

---

