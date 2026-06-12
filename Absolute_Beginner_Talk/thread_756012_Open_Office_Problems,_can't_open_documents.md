---
title: "Open Office Problems, can't open documents"
date: 2008-04-15
forum: Absolute Beginner Talk
---

### Post by nicklikesfire on 2008-04-15
Hiya,

So with open office, if I try to open a file that schould open using one of the open office programs, it blinks the open office logo thing onto the screen for a split second, then closes it, and the file never opens. Same goes for just opening one of the programs.

Initially I though it was just minimizing it or something else, that I couldn't figure out because I'm clumsy with this kind of stuff, but I think I have an actual problem at this point.

Also, I'm trying to install WYSIWYG web builder using wine, and that's not working either. maybe I should make a seperate thread for that though.

I'm stuck, thanks in advance for any help you can give me. Any ideas?

---

### Post by natirips on 2008-04-15
try deleteing your openoffice settings using these commands from your console: ```
cd
rm -r .openoffice.org2
```Note that this ".openoffice.org2" part might be different if you have a different version of open office, you can check the filename manually by typing "ls -a" in your console and looking for it.
Once you delete these files, you can try starting open office, and it will rewrite the files anew (just tested it). If you however insist on non trusting me, you can try just renaming the directory rather than deleteing it:```
cd
mv .openoffice.org2 .openoffice.org2_old
```. Now try opening open office, if you want to revert the old files do the following:```
cd
rm -r .openoffice.org2
mv .openoffice.org2_old .openoffice.org2
```Note that "rm -r something" command deletes a direcory/folder, while "mv something" command moves/renames one. "cd" is just to make shore you are in your home directory (where most of the settings are stored).

---

### Post by nicklikesfire on 2008-04-19
Thanks for the ideas, but still no luck. Any new ideas?

---

### Post by natirips on 2008-04-19
Try reinstalling open office (I hope you're not using it via wine [SIZE="1"](freeked-out laugh here)[/SIZE]). If that doesn't work I'm out of ideas.

---

### Post by nicklikesfire on 2008-04-19
> **natirips said:**
> Try reinstalling open office (I hope you're not using it via wine [SIZE="1"](freeked-out laugh here)[/SIZE]). If that doesn't work I'm out of ideas.

how would I even go about doing that. I know I need to do it through synaptic, but then what? should I search for openoffice and then just mark anything already installed for reinstallation?

sorry, like I said, I'm really not good at this yet.

Thanks so much!

---

### Post by msayed2004 on 2008-04-19
Can you open it by the terminal & tell us what it say ?
```
ooffice
```

---

### Post by natirips on 2008-04-19
> **nicklikesfire said:**
> how would I even go about doing that. I know I need to do it through synaptic, but then what? should I search for openoffice and then just mark anything already installed for reinstallation?
Exactly. Although if you don't like working in Synaptic, you can try the Add/Remove programs. But also try listening to the other guy. He might have some more elegant method.

---

### Post by nicklikesfire on 2008-04-19
> nick@nick-desktop:~$ ooffice

** (process:12427): WARNING **: Unknown error forking main binary / abnormal early exit ...
nick@nick-desktop:~$ 


That seems bad, hah hah.

---

### Post by nicklikesfire on 2008-04-19
and also:

> nick@nick-desktop:~$ wine PROGRAM dreamweaver
Bus error (core dumped)
nick@nick-desktop:~$ 


not sure if that means anything or not though

---

### Post by msayed2004 on 2008-04-19
Unknown error ?
Then try to reinstall it!

---

### Post by prshah on 2008-04-19
> **nicklikesfire said:**
> should I search for openoffice and then just mark anything already installed for reinstallation?


Open a terminal Applications->Accessories->Terminal and give the command ```
sudo apt-get --reinstall install openoffice.org
```

---

### Post by nicklikesfire on 2008-04-19
> **prshah said:**
> Open a terminal Applications->Accessories->Terminal and give the command ```
sudo apt-get --reinstall install openoffice.org
```

Did that, still getting the same thing out of my terminal:

nick@nick-desktop:~$ ooffice

> ** (process:12655): WARNING **: Unknown error forking main binary / abnormal early exit ...
nick@nick-desktop:~$ 

hmm. I really appreciate everyones help on this so far!

---

### Post by calc on 2008-04-19
> **nicklikesfire said:**
> That seems bad, hah hah.

I think this problem is fixed in Ubuntu 8.04 (Hardy). So upgrading may help resolve the problem for you.

---

