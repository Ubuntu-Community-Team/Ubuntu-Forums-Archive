---
title: "Nautilus always returns search results 0"
date: 2007-08-22
forum: Absolute Beginner Talk
---

### Post by philinux on 2007-08-22
Where as gnome-search-tool finds any relevant files.

Am I missing something?

---

### Post by philinux on 2007-08-22
Anyone?

---

### Post by Vadi on 2007-08-22
Try Places - Search for Files..., click on 'Look in folder' and select 'File System'. That'll have it search your entire desktop.

Or, install Google Desktop!

---

### Post by philinux on 2007-08-22
Cheers but why wont nautilus do that?

I use sudo nautilus to poke around and edit delete stuff etc.

---

### Post by Vadi on 2007-08-22
Because by default is searches in your home folder only.

And I always launch it via the Places on top... not sure what you mean about sudo nautilus and such.

---

### Post by philinux on 2007-08-22
> **Vadi said:**
> Because by default is searches in your home folder only.

And I always launch it via the Places on top... not sure what you mean about sudo nautilus and such.

Thanks for reply.

So how do I change the default?

sudo nautilus I mean I open terminal and type in sudo nautilus.

But search [COLOR="Red"]always[/COLOR] draws a blank.

---

### Post by Vadi on 2007-08-23
I don't think you need to open nautilus like that.

It's automatically loaded when you start your ubuntu... on top of the screen, see "Places"? Click on it, and then select "Search for files...". And where it says 'Look in folder' just select File System.

As for setting the default location, I don't know how to do that. It's not too much of a problem though to change it.

---

### Post by philinux on 2007-08-23
I do what your saying but you cant always move or delete a file that way. Sudo nautilus gives you nautilus with root privilages.

---

### Post by happy-and-lost on 2007-08-23
The Nautilus search uses locate, right?

Open up a terminal and run *sudo updatedb*. It'll take a while, but may solve your problem.

---

### Post by philinux on 2007-08-23
Ok here's the problem.

Places - search for files allows for searching File Sytem from "Look in Folder" brill. But you dont have privilages to access certain files once you've found them.

Nautilus only searches in root and desktop, not file system this is why its return 0 results.
So how on earth do you add the file system into nautilus search function?

---

### Post by porcorosso on 2007-08-23
I've been pretty frustated by this behavior, too.

I think the problem stems from the fact that the designed behavior of nautilus is to let us find files that we're *supposed* to find -- if you know what I mean. But, if you start nautilus with sudo, and the double-click on File System in the left pane of nautilus **before** clicking on the search option, then it will find all the non-user files.

At least that's the way it works for me.

---

### Post by porcorosso on 2007-08-23
> **philinux said:**
> Ok here's the problem.

Places - search for files allows for searching File Sytem from "Look in Folder" brill. But you dont have privilages to access certain files once you've found them.

Nautilus only searches in root and desktop, not file system this is why its return 0 results.
So how on earth do you add the file system into nautilus search function?

Heh, I posted while you were posting. Did you look at my suggestion in the message preceeding yours? Does that work for you?

---

### Post by philinux on 2007-08-23
Ah I'm with you now, but that only works if it's a perfect match of file name seems to me.

I tried what you suggested and searched for thunderbrid, no result but places search did the trick, this is weird.

---

### Post by porcorosso on 2007-08-23
Hmmm. It's working fine for me. If I type "etc" (no quotes) in the search field I seem to get every folder and every file that has those three consecutive letters in it. Doesn't seem case sensitive, either. I can type etc, ETC, Etc, whatever. I'm going to get the same results.

Or am I misunderstanding you?

---

### Post by philinux on 2007-08-23
Places search works. sudo nautilus dont and I clicked on file system first before searching. And Places Search is really quick too

---

### Post by nvteighen on 2007-08-23
There's a great tool you might want check out: it's the "locate" command. It works using an index (like Google Desktop), so it's fast and really useful. The "problem" is that the index must be updated manually through "sudo updatedb".

---

### Post by porcorosso on 2007-08-23
> **philinux said:**
> Places search works. sudo nautilus dont and I clicked on file system first before searching. And Places Search is really quick too

Just to be sure -- you clicked, or you double-clicked? I have to double-click File System in the left-hand pane of nautilus so that the full list of folders under the file system shows before I click the Search function on the toolbar to make it work properly.

I presume one also has to set nautilus to view hidden files, if the target happens to be a hidden file.

---

### Post by philinux on 2007-08-23
> **porcorosso said:**
> Just to be sure -- you clicked, or you double-clicked? I have to double-click File System in the left-hand pane of nautilus so that the full list of folders under the file system shows before I click the Search function on the toolbar to make it work properly.

I presume one also has to set nautilus to view hidden files, if the target happens to be a hidden file.

Doubled clicked. It seems it works if you also double click on a folder but that defeats the object of a system wide search.

---

### Post by steve.horsley on 2007-08-23
I think you just have to accept that nautilus file search is broken. And given how long it's already been broken, I think it is lkely to remain that way indefinitely.

---

### Post by philinux on 2007-08-23
> **steve.horsley said:**
> I think you just have to accept that nautilus file search is broken. And given how long it's already been broken, I think it is lkely to remain that way indefinitely.

Thanks Steve I think you're dead right. Maybe it will get fixed in Gutsy?

So my work around is Places>search gives list of files (very quicktoo) then  sudo nautilus to fiddle with said files. Two windows side by side.

---

### Post by yogo on 2007-08-23
I just wish there was a simple way of choosing the default location from the places search.

About 98% of the time I want to do a filesystem search and the default location is just a mere annoyance, easily enuf changed but just bothersome to always have to do it.

---

### Post by porcorosso on 2007-08-23
I don't know...

It looks to me as though it works the way it was designed to work. Ordinarily, one opens a file browser to look for files within his own profile. Security would demand that you go a couple of more steps to be sure that you really want to be performing file operations manually on system files.

Using sudo nautilus I can easily get a full file-system-wide search for anything I want by double-clicking on File System in naultilus' left pane and then clicking on the search icon. I wouldn't want it to be easier than that for using a file browser on system files. You have to enter a password -- after "sudo nautilus" -- and then you have to deliberately change the default starting point for the search. It's set up pretty much the same way in Vista, which is a better way that it has ever been done in Windows before.

Keeping systems secure usually means the users have to take a few extra steps to get down-and-dirty with operating system and software components. I would think that was a good thing.

---

### Post by philinux on 2007-08-23
Ok thats exactly what I do. But try searching for thunderbird. I got zilch. I thing even with sudo its still looking in root and homefolder.

---

### Post by porcorosso on 2007-08-23
> **philinux said:**
> Ok thats exactly what I do. But try searching for thunderbird. I got zilch. I thing even with sudo its still looking in root and homefolder.

Oh, that's very odd. I have Ubuntu (very different configurations, too) on three machines here, and mine are very definitely not behaving the way you're reporting nautilus to behave. I'm getting a search over the entire file system, and it's very quick.

I'm sorry I don't know what to suggest. I have no idea whether yours is the norm, or mine is. Weird.

---

### Post by Draught on 2007-09-16
The index is automatically updated only for the user's home

To search a file in the File System you first need to do
```
sudo updatedb
```

---

### Post by philinux on 2007-09-16
Did that first as well!

---

### Post by Draught on 2007-09-17
> So my work around is Places>search gives list of files (very quicktoo) then sudo nautilus to fiddle with said files. Two windows side by side.

Well I read the thread more carefully and I think I understand what's burning you

The solution is in your first post

```
sudo gnome-search-tool
```

Select **Other...** for the **Look in folder**, and type **/**

You can now open all files in root mode

---

### Post by philinux on 2007-09-17
> Select Other... for the Look in folder, and type /

You can now open all files in root mode

Nice try it nearly works!

I created an empty folder in dev called mobile. It found all the folders and files with mobile in, like kmobile etc  but not my test folder, weird. Even searching for mobil missed it. I even did sudo updatedb just to make sure. So to be certain I'll have to stick to my two screen work around.

---

