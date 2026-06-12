---
title: "entering an editor in gFTP"
date: 2007-12-09
forum: Absolute Beginner Talk
---

### Post by gleble on 2007-12-09
When going to options in gTFP what do I enter to invoke Text Editor?

---

### Post by squaregoldfish on 2007-12-09
In the General tab of the options dialog, change the 'Edit program' to:

gedit

That should do the trick

Steve.

---

### Post by gleble on 2007-12-09
Just when I thought I was getting somewhere I run into this little glitch(see above) when trying to edit my website. I've almost had it with ubuntu, no sound, no wireless then this.(see my other posts) Can someone please restore my faith

---

### Post by gleble on 2007-12-09
I tried entering gedit and I get this error "Edit: .. is a directory. Cannot edit it."

---

### Post by gleble on 2007-12-09
The files I am trying to edit are .php .js and .inc Why does ubuntu think they are directories?

---

### Post by bsell on 2007-12-09
> **gleble said:**
> The files I am trying to edit are .php .js and .inc Why does ubuntu think they are directories?
It's likely because they are directories :)

As squaregoldfish pointed out, to use the text editor of your choice go to the FTP menu and select Options and on the General tab type in your text editor.

---

### Post by gleble on 2007-12-09
They're not directories they are just text files, what their extensions suggest 

go to the FTP menu and select Options and on the General tab type in your text editor.

I know how to get there but not what to enter.  gedit doesn't seem to work.

---

### Post by bsell on 2007-12-09
> **gleble said:**
> They're not directories they are just text files, what their extensions suggest 

go to the FTP menu and select Options and on the General tab type in your text editor.

I know how to get there but not what to enter.  gedit doesn't seem to work.

I've used gedit as my text editor in gFTP. Try adding the % metacharacter after typing gedit (add a space between the t in gedit and the %). 

I use Bluefish as my editor and that's what I'm going to suggest you use. It's available in the repositories.See the attached screenshot.

---

### Post by gleble on 2007-12-09
Sidestepped the problem. Editing the local file directly then refreshing gFTP works fine for my purposes. Thanks or the help

---

