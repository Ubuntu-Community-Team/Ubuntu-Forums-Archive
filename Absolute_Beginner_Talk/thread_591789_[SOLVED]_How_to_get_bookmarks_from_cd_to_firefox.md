---
title: "[SOLVED] How to get bookmarks from cd to firefox"
date: 2007-10-25
forum: Absolute Beginner Talk
---

### Post by discmaster on 2007-10-25
As the title says; How to get bookmarks from cd to firefox, or desktop to ff, anywhere, just want to get them back into firefox.

Looked all over the HD, what I found was; 
filesystem/usr/lib/mozilla

that is the only thing I could find remotely close to ff to replace my backed up bookmarks. How do I do this...thought it might be as easy as "drag & drop" them someplace, but I guess not :confused:

---

### Post by Kingsley on 2007-10-25
Bookmarks > Organize Bookmarks > File > Import

I'm assuming your bookmarks are saved as a text file.

---

### Post by Maestro23 on 2007-10-25
> **Kingsley said:**
> Bookmarks > Organize Bookmarks > File > Import

I'm assuming your bookmarks are saved as a text file.

Beat me to it.

---

### Post by p_quarles on 2007-10-25
Using the import bookmarks thing is kind of a pain, I think, since it puts your old bookmarks in a new subfolder, requiring you to rearrange them manually. 

You can replace bookmarks file directly by opening the file manager, selecting "show hidden files," going into the folder marked ".mozilla," then "firefox," then the one that begins with a random string of numbers and letters. Drop the bookmarks.html file in their, let it overwrite the old one, and you're good to go.

---

### Post by discmaster on 2007-10-25
> Bookmarks > Organize Bookmarks > File > Import

I'm assuming your bookmarks are saved as a text file. I am doing that very thing, but the bookmarks are not importing...

---

### Post by Kingsley on 2007-10-25
> **p_quarles said:**
> Using the import bookmarks thing is kind of a pain, I think, since it puts your old bookmarks in a new subfolder, requiring you to rearrange them manually. 

You can replace bookmarks file directly by opening the file manager, selecting "show hidden files," going into the folder marked ".mozilla," then "firefox," then the one that begins with a random string of numbers and letters. Drop the bookmarks.html file in their, let it overwrite the old one, and you're good to go.
It's not that much of a pain. All that's required is a few mouse drags and deletion of the "new" bookmarks toolbar folder.

---

### Post by discmaster on 2007-10-25
> You can replace bookmarks file directly by opening the file manager, selecting "show hidden files," going into the folder marked ".mozilla," then "firefox," then the one that begins with a random string of numbers and letters. Drop the bookmarks.html file in their, let it overwrite the old one, and you're good to go.I guess I am at the wrong place, because when I go into my mozilla folder, the only thing in there is a plugins folder... help?

---

### Post by Kingsley on 2007-10-25
Are you bookmarks stored in Firefox on a different operating system or computer? If so, it'd be so easy to use the Foxmarks extension to make the transfer.

---

### Post by discmaster on 2007-10-25
> Are you bookmarks stored in Firefox on a different operating system or computer? If so, it'd be so easy to use the Foxmarks extension to make the transfer.No, I just have the backups on a cd. I am all for the easiest way, whatever works.

---

### Post by p_quarles on 2007-10-25
> **discmaster said:**
> I guess I am at the wrong place, because when I go into my mozilla folder, the only thing in there is a plugins folder... help?
Use your file manager, not Firefox. If you're not sure what this is, hit alt-F1 and then type "nautilus" at the prompt. Then you'll be where you're supposed to be. 

But I can't imagine why it won't import the bookmarks the way others have suggested. Are you sure you have the right type of file?

EDIT: Nevermind, I think I misread your post. What's inside the plugins folder?

---

### Post by discmaster on 2007-10-25
This is what I have; don't know if you can make it out or not...

[[IMG]http://img91.imageshack.us/img91/8047/filekf6.jpg[/IMG]](http://imageshack.us)

Name of the website.url

Is this the wrong type of file? If I click on the url, it opens in a text editor, revealing the full url path...

---

### Post by discmaster on 2007-10-25
There are 8 files inside the plugins folder; 

libtotem-basic-plugin.so

libtotem-basic-plugin.xpt

libtotem-gmp-plugin.so


etc...

---

### Post by p_quarles on 2007-10-25
I can't make out the image, but it sounds like you have the worng thing. Basically, on your old Firefox, you need to go the Bookmark Manager and export your bookmarks. This will create a file called "bookmarks.html." You should then be able to import this into the new Firefox by pointing it to that file. 

As for the contents of your .mozilla folder, that is puzzling. If you have any further trouble importing the easy way, try running the following command (in the terminal) and posting the output back here:
```
ls .mozilla/firefox
```

---

### Post by crane on 2007-10-25
> **discmaster said:**
> I guess I am at the wrong place, because when I go into my mozilla folder, the only thing in there is a plugins folder... help?

Go to your home directory. then hit <ctrl> h 
That will show hidden files. Now find a folder named .mozilla the go into the firefox folder the the XXXXX.default folder. you should see a file names Bookmarks.html.
If not just put your file there and then restart firefox.
Mine is like this.
/home/jason/.mozilla/firefox/vkuuxfit.default/bookmarks.html

---

### Post by discmaster on 2007-10-25
Where is the Mozilla folder normally located? Should there be a bookmarks folder already present in there?I believe I may have the install goofed up? I had 7.04 on here, had issues, reformatted & now installed ubuntu studio. I simply formatted the partition where the first install was (during studio install) & went from there.

---

### Post by discmaster on 2007-10-25
> Go to your home directory. then hit <ctrl> h
That will show hidden files. Now find a folder named .mozilla the go into the firefox folder the the XXXXX.default folder. you should see a file names Bookmarks.html.
If not just put your file there and then restart firefox.
Mine is like this.
/home/jason/.mozilla/firefox/vkuuxfit.default/book marks.html

Ahhh....I see it all now. The bookmarks from this install are there  - I just have to transfer the others over. I believe I got it now - Thanks Guys!!!

---

### Post by crane on 2007-10-25
No problem! Have fun.

---

