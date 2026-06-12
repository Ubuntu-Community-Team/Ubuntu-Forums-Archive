---
title: "[SOLVED] Couple of problems"
date: 2008-01-20
forum: Absolute Beginner Talk
---

### Post by Fraser from Scotland on 2008-01-20
I wasn't sure where to post this, mods; please move accordingly. 
Problem 1. I downloaded a movie but it's split into lots of .tar.0001 then it continues till 23 or something. I don't know how to just make it into a movie file to watch it. There is a screenshot to better explain it.

Problem 2. I have conky set to run at boot but-only sometimes- when i start it will be overlapping (underlapping i guess) the panel at the top is above conky. This only happens sometimes and can be fixed if I killall conky then start conky again. Very irritating.

I am studying just now so will be periodically checking this thread so don't expect a quick reply.

---

### Post by Fraser from Scotland on 2008-01-20
bumpn :/

---

### Post by Ebuntor on 2008-01-20
> **Fraser from Scotland said:**
> I wasn't sure where to post this, mods; please move accordingly. 
Problem 1. I downloaded a movie but it's split into lots of .tar.0001 then it continues till 23 or something. I don't know how to just make it into a movie file to watch it. There is a screenshot to better explain it.

You'll need the application File-roller. You can install it via the terminal or GUI.

Via the terminal
```

sudo aptitude install File-roller
```Via the GUI:
Go to Applications => Add/Remove
In the search bar type "Archive Manager" 
It should be the first result, click the box and click apply changes.

After you installed the program simply go the your tar files and right click one of them (doesn't matter which one). And click "Extract here" It will automatically extract all of them and combine them as one file.

> 
Problem 2. I have conky set to run at boot but-only sometimes- when i start it will be overlapping (underlapping i guess) the panel at the top is above conky. This only happens sometimes and can be fixed if I killall conky then start conky again. Very irritating.

I am studying just now so will be periodically checking this thread so don't expect a quick reply.Simply add  "sleep 30 && conky" This will make it wait for 30 seconds before starting conky.

EDIT: Sorry if the CLI and GUI explanation is a bit too detailed. If you could install conky I'm sure you can easily install file-roller too. :)

---

### Post by Fraser from Scotland on 2008-01-20
I installed file roller and tried to do extract here, but it only let me create archive so i did that. And then  I extracted the archived tar.gz and it just gave me all the same files.

where do i add the sleep command to?

---

### Post by Ebuntor on 2008-01-20
> **Fraser from Scotland said:**
> I installed file roller and tried to do extract here, but it only let me create archive so i did that. And then  I extracted the archived tar.gz and it just gave me all the same files.


Just be certain I understand your correctly: In the directory you right-clicked one of the files and selected "extract here" in the context menu? After that file roller popped up saying you could only make an archive?

>  
where do i add the sleep command to?

I understood you added it to the startup list in the session menu, right? In the command bar in front of the word "conky" type the sleep command.

---

### Post by erginemr on 2008-01-20
In case Fileroller doesn't work for you:
I am sure there is a more sophisticate (read, bash-esque) way to do this, but as a quick and dirty way:

Assume you have 5 files: movie.001 movie.002 movie.003 movie.004 movie.005
To combine them, you issue the following command:
cat  movie.001 movie.002 movie.003 movie.004 movie.005 > movie.tar

It may seem hard to write 23 files like this at first, but you can make use of the "Tab", which will do most of the work for you.

---

### Post by Fraser from Scotland on 2008-01-20
It still doesnt work :S did you see the screenshot? Every file is a .tar, i don't know how to make it into a movie

---

### Post by Fraser from Scotland on 2008-01-20
The .tar files arent inside a compressed folder, they are just in a normal folder.

---

### Post by Fraser from Scotland on 2008-01-20
Ok, I'll recap since this has probaly got confusing.

I downloaded a movie, then when it was finished I went into the folder it was in (See screenshot 1)
and all the files were named mts-rot.tar.001 but the numbers increased upto 46.(See screenshot 2)

What i need to know is how to watch the movie, I have tried using file roller but when I left click on one of the mts-rot.tar.001 files it doesn't let me "extract here" like i was instructed to do.

Please help!!

Screenie 1: [http://img120.imageshack.us/img120/8381/screenshotjy8.png](http://img120.imageshack.us/img120/8381/screenshotjy8.png)

---

### Post by Fraser from Scotland on 2008-01-20
bleh bump

---

### Post by frup on 2008-01-20
open terminal and paste in:
cd MOVIE;cat mts-rot.tar.* > mts-rot.tar

---

### Post by Fraser from Scotland on 2008-01-20
I did that. What did it do?

---

### Post by Fraser from Scotland on 2008-01-20
Can someone help? I don't have a clue what this code did!

---

### Post by Fraser from Scotland on 2008-01-20
.....anyone?

---

### Post by frup on 2008-01-20
Sorry was having lunch...

In that movies folder should be a file named mts-rot.tar now that should have the whole movie in it... If the simple way worked.

---

### Post by Fraser from Scotland on 2008-01-20
there is one called mts-rot.ta   i might have changed it by accident.

What do i do now?

---

### Post by Fraser from Scotland on 2008-01-20
I'm going to bed now, I'll see what i can do in the morning.

---

### Post by frup on 2008-01-20
If its mts-rot.ta not .tar that means the >mts-rot.tar bit just missed the r off the end. rename it to .tar and if everything is right it should be an archive with the file inside.

---

### Post by rjmdomingo2003 on 2008-01-21
Try **[COLOR="Blue"]right-clicking[/COLOR]** mts-rot.tar.001, and click extract here. A folder (may be named mts-rot) will appear, and inside is your movie file (e.g. .avi, .mpeg).

---

### Post by Fraser from Scotland on 2008-01-21
It worked!!! Thanks Everyone!!

---

