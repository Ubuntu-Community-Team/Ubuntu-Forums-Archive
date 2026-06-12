---
title: "Where is My Documents?"
date: 2006-08-20
forum: Absolute Beginner Talk
---

### Post by AhmadMF on 2006-08-20
Hello All

I've been running dapper for almost a month and I love it, I have had no previous experience with linux except for trying a few live CDs, including Warty Warthog's (Ubuntu 5.10).

Now, If I remember correctly, Warty had a folder called "Documents", now, my memory sucks and I really can't be sure if I am right as I don't seem to find warty's CDs. ](*,) 

I can't find any reference to it in dapper though..

So my question is:
Was there actually a documents folder in warty that was removed in subsequent releases? If so, Why? and is there a way to enable it (like some setting to be changed in the configuration editor)?

If there can't be a documents folder.. where is the most reasonable place to store my documents? on my desktop? in my home folder?

---

### Post by jrjr on 2006-08-20
.

---

### Post by scxtt on 2006-08-20
you're stuck in too much of a Windows frame of mind ... you don't need a pre-defined "My Documents" and i'd advise making your own in your home folder ...

---

### Post by meng on 2006-08-20
Nowadays there is no default Documents folder, so create one!
I like to place my docs in /home/meng/Documents
Actually, it would probably make life easier if it were /home/meng/documents
but old habits die hard!
Then it's relatively easy to get apps (e.g. Openoffice) to recognize this as the default save directory.

---

### Post by AhmadMF on 2006-08-20
Thanks for your reply,

I think a my documents folder is kinda nice in that all applications should point to it first, i.e. if I open a file in OO.org it should present me with my documents folder first and if I want to navigate to some place else i can, and besides, it should be available in the "Places" menu for easy access.

Sure, all of the above is already achieved if you use the Home folder as a place to store documents, but I find it cluttered and full of system stuff (though they are hidden by default).

This could also be achieved by creating a seperate partition for documents as you do, but I'm not in the mood to repartion my hard drive now, and i'm satisfied with my current harddrive setup.

What should I do?

Thanks in advance

---

### Post by AhmadMF on 2006-08-20
scxtt: see my last post

meng: will OO.org remember my last selected directory, or should i change something in the settings? and can you add this manually created folder to the "Places" menu?

thanks all

---

### Post by meng on 2006-08-20
First question: don't know offhand.
Second question: navigate to your document folder in Nautilus, then choose Bookmarks > Add Bookmark.

---

### Post by scxtt on 2006-08-20
OO remembers the last folder you've opened, as do most KDE apps (can't remember if Gnome does) ...

---

### Post by AhmadMF on 2006-08-20
thanks so much meng and scxtt, that does it for me (i think)

I was going crazy trying to figure out how to add any folder to the places menu, tried dragging and dropping, tried to find a folder like the one in windows where you add shortcuts and they would appear in the taskbar's quick launch, but nothing...

And it is good to know that OO remembers the last selected folder, it is also good to know that this forum and this great community is ready to give a hand to those who need it... glad to be here :) 

Thanks and see you again when there is another problem ;)

---

### Post by aysiu on 2006-08-20
This is the way I see it:

**Windows**:
C:\Documents and Settings\username\My Documents

**Mac OS X**:
/Users/username

**Ubuntu:**
/home/username

---

### Post by David Corrales on 2006-08-20
You could also look into this driver [http://www.fs-driver.org/index.html](http://www.fs-driver.org/index.html) to access your ext2/3 partitions from windows.

---

### Post by msak007 on 2006-08-20
My default Kubuntu installation had a folder called "Documents" in my home folder (capitalized and all).

---

### Post by jrjr on 2006-08-21
.

---

### Post by AhmadMF on 2006-08-21
I just found a way to get it to do exactly what I wanted, just create a folder named "Documents" (with a capital D).. it will automatically show up on the Places menu without having to bookmark it.

If you want it to show up on the desktop just change the value of /apps/nautilus/desktop/documents_icon_visible to true in the gconf-editor

Now, I'd like to be able to have the Documents folder synched with XP's my documents, I've read somewhere about symlinking... is that what I should do? What are the steps?

---

### Post by jimmygoon on 2006-08-21
No. If you wanted to share that then you should've listened to what everyone else was telling you before ;). You are going to want to make a fat32 partion on your HD. Then you can mount it as /home/USERNAME/Documents and in windows, you can set the My Documents to reside on the fat32 partition, that way they are effectivly sharing the data.

---

### Post by AhmadMF on 2006-08-21
I've just intalled ext2/ext3 driver for XP and now I can see my home partition, and I moved all my documents to the "Documents" folder and pointed XP to it. Problem solved.

Thanks everybody.

---

### Post by meng on 2006-08-21
Great solution. Glad to hear it.

---

### Post by MetalMusicAddict on 2006-08-21
I was a big advocate of the ext3 driver. Just be careful with it. Writing large files in windows with it. For documents you should be fine.

I would also like to say be open as to how linux does things. Dont necessarily try to turn it into windows. Think about the things you would have to re/un/learn if you bought a Mac. Same thing applies here.

---

### Post by AhmadMF on 2006-08-21
MetalMusicAddict, you say you *were* a big fan of it, does that mean that you are not a big fan of it right now? is it unstable? will it damage my data? you got me all worried! :-k

---

### Post by ProjectGod on 2006-08-21
i believe someone has already answered where my documents is. you have to create it! :D

preferably you'll create it under /home/<yourusername>/my documents and create a shortcut onto the desktop.

PLEASE DO NOT CREATE MYDOCUMENTS FOLDER ON DESKTOP!!!!!!!!!!!!!!!!! i once deleted 2 months of work thinking the my documents object on my desktop was just a shortcut to c:\documents and settings\xxx\mydocuments. 

stupid arn't i? :mrgreen:

---

### Post by MetalMusicAddict on 2006-08-21
> **AhmadMF said:**
> MetalMusicAddict, you say you *were* a big fan of it, does that mean that you are not a big fan of it right now? is it unstable? will it damage my data? you got me all worried! :-k
I didnt mean to scare you. I think its fine for small read/writes. I had trouble with writing large data files to a ext3 drive from windows. The current driver is a little newier than the last one I used.

---

