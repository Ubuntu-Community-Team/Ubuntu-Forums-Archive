---
title: "Don't Know How to Comment Out"
date: 2007-05-23
forum: Absolute Beginner Talk
---

### Post by NuttBoxer on 2007-05-23
Apologies in advance if this is so noob I should have found it in an already existing guide.  I am trying to configure Dansguardian, and the how to guide instructs me to "comment out" the following line: 

UNCONFIGURED - Please remove this line after configuration

As far as I can tell this means I need to put a pound sign(#) in front on the word UNCONFIGURED, for example:

#UNCONFIGURED - Please remove this line after configuration

But after I do that, I'm not sure how to proceed so that the change is saved and the file is no longer unconfigured.

---

### Post by drowner on 2007-05-23
Try a space after the #

---

### Post by NuttBoxer on 2007-05-23
After putting the space do I simply close the Terminal and the changes are saved?

---

### Post by drowner on 2007-05-23
What program are you using to edit it?

I'm not good with all of them, you see.

---

### Post by NuttBoxer on 2007-05-23
I'm using Gnome Terminal 2.18.

---

### Post by icechen1 on 2007-05-23
> **NuttBoxer said:**
> Apologies in advance if this is so noob I should have found it in an already existing guide.  I am trying to configure Dansguardian, and the how to guide instructs me to "comment out" the following line: 

UNCONFIGURED - Please remove this line after configuration

As far as I can tell this means I need to put a pound sign(#) in front on the word UNCONFIGURED, for example:

#UNCONFIGURED - Please remove this line after configuration

But after I do that, I'm not sure how to proceed so that the change is saved and the file is no longer unconfigured.

use gksudo gedit [link to the file here] to save file as root because it is not in /home,right?

---

### Post by lazyart on 2007-05-23
are you using gedit or maybe nano to edit file?

---

### Post by drowner on 2007-05-23
edit: icechen corrected themselves

---

### Post by Hobo Joe on 2007-05-23
I know someone said this already, but what you need to do is type:

```

gksudo gedit <file>

```

Then make the change, then save the settings.

Just wanted to make that clear. :)

---

### Post by NuttBoxer on 2007-05-23
It's Nano, sorry for the confusion.

---

### Post by drowner on 2007-05-23
> **NuttBoxer said:**
> It's Nano, sorry for the confusion.

Ok good.

At the bottom of the screen there will be insrtuctions on how to quite, when you quit it will ask you to save the file, if you like

If you just close the terminal, it wont (but nano should make a back up)

---

### Post by lazyart on 2007-05-23
Control-X will exit nano and ask to write the changes.

---

### Post by NuttBoxer on 2007-05-23
I saw the control prompts, but didn't understand how to use them.  Sorry this should have been a much shorter thread.  Just one more question.  I now have 5 different conf files in my Dansguardian folder, three of them have red "X's" beside the icon.  Should I remove these files, leave them, or will correctly configuring via Nano, and then saving, delete the bad files?

---

### Post by NuttBoxer on 2007-05-23
Thank you very much to everyone for their help, greatly appreciated!

---

