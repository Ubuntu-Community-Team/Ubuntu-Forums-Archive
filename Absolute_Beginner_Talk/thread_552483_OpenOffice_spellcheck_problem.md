---
title: "OpenOffice spellcheck problem"
date: 2007-09-16
forum: Absolute Beginner Talk
---

### Post by Xorg.conF on 2007-09-16
I have been using the openoffice word, then I noticed that the spell check never works, I use it from the tools menu and it always says no mistakes, but I clearly see there are misspelled words.

whats going on with this thing, thanks for all the help.

---

### Post by some_random_noob on 2007-09-16
If you're using Dapper then you can fix this with the "install new dictionaries" wizard. If you're using something newer, then it doesn't work. Don't ask me why - I'm pissed off about this myself. If you really need spell checking then you could use Abiword or you could help contribute to fixing this problem (If you have the time).

I've posted a possible solution on launchpad if you want to experiment and possibly break something. In my opinion it's worth a try though - just make backups. Check out the following link:

[https://bugs.launchpad.net/ubuntu/+source/openoffice.org/+bug/95274](https://bugs.launchpad.net/ubuntu/+source/openoffice.org/+bug/95274)

... yes, I'm "Uber-nerd". 

**ATTENTION EVERYONE:** Please read the launchpad page which I've posted above, if we try then we could easily fix this issue! :popcorn:

---

### Post by Hagar Delest on 2007-09-16
I managed to run the wizard running OOo with sudo (just for the dics installation).

For spell checking, see here : [Tutorial for Spell check and Language configuration](http://www.oooforum.org/forum/viewtopic.phtml?t=50862).

---

### Post by some_random_noob on 2007-09-16
> **Hagar de l'Est said:**
> I managed to run the wizard running OOo with sudo (just for the dics installation).

For spell checking, see here : [Tutorial for Spell check and Language configuration](http://www.oooforum.org/forum/viewtopic.phtml?t=50862).

But Xorg.conF is using Feisty (According to his profile) and you're using Dapper. You're suggesting that the spellcheck box is simply unticked, and I'm suggesting that Xorg.conF can't install dictionaries in the first place - very different things. Yes you are meant to be able to tick a box and use the "install new dictionary" wizard, but the "install new dictionary" wizard crashes in Feisty!

Xorg.conF probably does not have any dictionaries installed, and if the wizard doesn't work then he's stuck. This is not a case of ticking the spell check box in Tools>Options>Language settings>Writing aids. Xorg.conF needs to install a dictionary first from File>Wizards>Install new dictionary and THEN tick the box to enable it. But the wizard crashes does it not?

Give us a response sometime, Xorg.conF. I think you may be running into an unresolved error.

---

### Post by Hagar Delest on 2007-09-16
No, I'm not talking about ticked boxes (I don't see where you've found that). I've had also this crash issue under Dapper when using the wizard. I managed to run it with sudo.
And you don't need the wizard at all, you can install the files manually, either in the main installation folder or in the user profile. I agree, this requires some manual task (download the dic package, extract its content in the right folder and edit the dictionary.lst file). But there is no dead end here.

---

### Post by Xorg.conF on 2007-09-16
Thanks for the help, I tryed the install a dictionary first from File>Wizards>Install new dictionary and THEN tick the box to enable it method, and so far it works, it underlines words and spellchecks, yeepy.  But it has been said to crash so i'l be watching.  If the problem has no reslove, then I already have abiword installed, but I rather use OOo because it's cooler.

---

### Post by Hagar Delest on 2007-09-16
I'm lost. What's the issue ? You confirm it's solved ?

---

