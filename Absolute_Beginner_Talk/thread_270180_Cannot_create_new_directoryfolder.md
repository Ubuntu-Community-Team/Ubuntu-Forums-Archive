---
title: "Cannot create new directory/folder"
date: 2006-10-02
forum: Absolute Beginner Talk
---

### Post by lost+found on 2006-10-02
Hi,

Suppose I am browsing my HDD and want to create a new folder...I get a message saying access denied! This happens for copying or moving things as well. Does this have to do with administrative rights? I am the admin and have the root password, is there a place where you can set something to give you global rights?

Sorry for the newbie Q..

---

### Post by taurus on 2006-10-02
You use "sudo" if you want to move/copy/delete files/directories on your machine if they have only root permission...

---

### Post by lost+found on 2006-10-02
The folder is not root access only, (no padlock on it) this is anywhere on the HDD except my own personal home folder. I did try "sudo" in the konsole "sudo mkdir /...../"  but then it says cannot creat directory, no such file or directory?! I just don't get it..By the way, i'm using the latest version of Kubuntu

---

### Post by annda on 2006-10-02
are you sure you haven't misspelled anything in the path (like parent dir name)? it happens all the time, try hitting the TAB for autocompletion after typing the first letters...

---

### Post by lost+found on 2006-10-02
Yes, I am sure that it is typed correctly. Why would it be saying to me that the directory cannot be found when im trying to create it! Obviously its not there until it exists...I think the problem might be elsewhere.

---

### Post by aysiu on 2006-10-02
Alt-F2 will open a run dialogue.

In that dialogue type...

For Ubuntu: ```
gksudo nautilus
``` For Xubuntu: ```
gksudo thunar
``` For Kubuntu: ```
kdesu konqueror
```

---

### Post by lost+found on 2006-10-02
Thank you for that last post, it seems to have revealed something interesting. Now, that i've "logged into" Konqueror throught the run command instead of by jsut clicking the icon, when i go to media (where the drives should be) now there is nothing...

Any further ideas guys and gals?

---

### Post by Seine on 2006-10-02
> **lost+found said:**
> Yes, I am sure that it is typed correctly. Why would it be saying to me that the directory cannot be found when im trying to create it! Obviously its not there until it exists...I think the problem might be elsewhere.

If you have the path /abc/123/ and you want to create /abc/123/xyz, but you type

mkdir /abc/129/xyz 

then you will get a not found error because 129 does not exist.

As a previous responder said, use tab for autocompletion and let us know how you go.

Cheers
Jem

---

### Post by lost+found on 2006-10-02
Everything is typed correctly, and checked with autocomplete. more precisely im trying to create the directory /usr/lib/hotplug/firmware/ upon entering the password it still says no such file or directory. BUT, an interesting development in this episode as that by using aysiu's method to access the Konqueror browser instead of doing it "normally", not it seems as though not a single directory exists, not even a single drive. The Url is media:/ in Konqueror and there is no items, no files, no folders, where there should be a HDD at least. Strangely this seems to now make sense with what the Konsole is telling me, but then why could i see all this in Konqueror before?

---

### Post by lost+found on 2006-10-02
OK, strangely, after doing the above again, this time it actually showed me the drives etc..and i could create the folder. Seems it is all ok for now, thanks for the help. BTW, does this mean i have to do this everytime i want to change some fodler on the drive? Is this some Kubuntu bug? 

I guess what im saying is, is there a way to get global write permission? It is actually really annoying as half the time it i can write otherwise cant. Even saving a simple file in Kate has become torture...

---

