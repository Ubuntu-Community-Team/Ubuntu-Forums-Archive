---
title: "Help Shortcuts Creating (Like Windows)"
date: 2007-02-25
forum: Absolute Beginner Talk
---

### Post by webjames on 2007-02-25
Hi, i was wondering:

i used to have windows XP and on my desktop i had the equivalent of shortcuts to my documents, home, file system. how do i create a shortcut on my Ubuntu desktop?

i have managed to make a link, however when i double click it opens but not with the address bar pointing to the linked directory but the link itself.
for example:

a link to:
```
/home/james/Documents
```

 would look like this when places on the desktop and opened:

```
/home/james/Desktop/link to Documents
```


any ideas?
Thank you,

James

---

### Post by Maestro23 on 2007-02-25
Take a look at my screenshot.  Is that what you are talking about. Right click on Desktop, create url:

The path to my Documents: /home/robert/Docs

*Just one way to do it.  More ways down below.

---

### Post by raja on 2007-02-25
Use the terminal.
```
cd ~/Desktop
ln -s /home/robert/Docs
```
This creates a symbolic link to that directory on your desktop.

---

### Post by mk04 on 2007-02-25
Right click on the original folder and go to make link. You might have to move it to your Desktop or preferred location.

EDIT: I just looked at your screenshot. It looks like your running Xubuntu. So my instructions might not work.

---

### Post by webjames on 2007-02-25
> **Maestro23 said:**
> Take a look at my screenshot.  Is that what you are talking about. Right click on Desktop, create url:

The path to my Documents: /home/robert/Docs

*Just one way to do it.  More ways down below.

Hi just looked at the screen shot. how do you get that window up?

here i have attached 3 screen shot showing what i mean:

01 shows the 'link' on my desktop

02 shows what comes up in the window when i click it. notice in the address bar it says:
"/home/james/Desktop/Documents"
when actually the folder is:
""/home/james/Documents"

03 shows how the path is still inaccurate even when sub folder is browsed:
"/home/james/Desktop/Documents/Foundation of Business"
when it should read:
"/home/james/Documents/Foundation of Business"

i hope this clears up my question!

thanks for your quick responses!

regards,

James

---

### Post by webjames on 2007-02-25
> **mk04 said:**
> Right click on the original folder and go to make link. You might have to move it to your Desktop or preferred location.

EDIT: I just looked at your screenshot. It looks like your running Xubuntu. So my instructions might not work.

I ought to say: i am running Ubuntu 6.10 thanks

---

### Post by mcduck on 2007-02-25
If you want home, computer etc. icons on Gnome desktop there's a better way to do it than just making your own shortcuts:

1. Open Configuration Editor (hit Alt-F2 and run 'gconf-editor'.
2. Browse to apps /nautilus/desktop
3. mark 'computer_icon_visible', 'documents_icon_visible' and 'trash_icon_visible' 

(documents icon only works if you have a directory called 'Documents' in your home dir.)

The reason why this is better way to do it is that this way the icons will change according to the icon theme you are using, and also you can't delete these icons from desktop. (you can of course remove them with Configuration Editor if you want to get rid of them). They are also automatically placed before any drive icons or files if you use the 'Clean Up By Name' from right-click menu on the desktop.

---

### Post by webjames on 2007-02-25
**_BRILLIANT!_**

Just what i wanted!

thank you.

---

### Post by nandotron on 2007-03-17
Hi guys,

Just wondering if you could help me out.  I am running a dual boot system with edgy and xp.  I have read-write access to the windows partition.  is there a way that i can add a shortcut to the xp my documents folder to the places menu?  that would be awesome.

thanks for your help!

Enda

---

### Post by konst88 on 2007-03-17
Using nautilus, navigate to the desired folder.
Bookmarks>add to bookmarks

---

### Post by nandotron on 2007-03-17
That was so easy!  thanks very much

Enda

---

### Post by Killtown on 2007-06-28
How do I create a **Home** icon on my desktop?

---

### Post by kpkeerthi on 2007-06-28
Open terminal and launch gconf-editor. Navigate to apps/nautilus/desktop/ and check the icons you need.

---

