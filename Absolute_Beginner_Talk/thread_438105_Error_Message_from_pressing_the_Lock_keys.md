---
title: "Error Message from pressing the Lock keys"
date: 2007-05-09
forum: Absolute Beginner Talk
---

### Post by Robert98374 on 2007-05-09
Hello everyone!
The issue is that whenever i press the Numlock, Caps lock and the scroll lock its throws up this error message

Bad key or directory name: "/desktop/gnome/peripherals/keyboard/host-Bobby's Computer/0/numlock_on": `'' is an invalid character in key/directory names

They still work after i press them it just displays that error message evertime
I thought that when i upgraded to 7.04 it would fix it. I am assuming that its a bug? or a fairly easy fix?

---

### Post by Skrynesaver on 2007-05-09
What have you called you computer ?
```
 hostname
```

---

### Post by Robert98374 on 2007-05-09
Bobby's Computer

I know that i am now not supposed to use some of the charcters that were in the name but i am not sure how to change them

---

### Post by Skrynesaver on 2007-05-10
Hi again Robert

Sorry about the delay in getting back to (sleep and all that ;) ).
The hostname of a computer should always be a single word, having a space in the hostname breaks all sorts of things but the apostrophe is also interpreted as a single quote and so many scripts that use your hostname will be broken by this.
to change your hostname go to System/Administration/Network.
On the general tab, you will find a box named "Host Name" change it here to a single word with no punctuation.

---

### Post by Robert98374 on 2007-05-10
It gave me the warrning

This will prevent you from launching new applications, and so you will have to log in again. Continue anyway?

So should i be scared or does it mean that i just need to restart my computer before it works again?

---

### Post by Skrynesaver on 2007-05-10
Applications running in X-windows (the windowing environment in Unix) can be run on any connected machine that is allowed to connect, (Very useful on networks), this means that when you change your hostname the reference to your machine becomes broken.  Restarting the X-server with the new settings resolves this, relax and go for it ;)

---

### Post by Robert98374 on 2007-05-11
Kewl beans done and now changed :-) but back to my orginal problem?

---

### Post by Skrynesaver on 2007-05-11
The apostrophe in the hostname was the cause of the original problem
> 
Bad key or directory name: "/desktop/gnome/peripherals/keyboard/host-**Bobby's Computer**/0/numlock_on": `'' is an invalid character in key/directory names

I'm not at a gnome machine at the moment and don't know the GUI very well. Perhaps someone else can say if this path is auto-updated or if a reconfigure is necessary

---

