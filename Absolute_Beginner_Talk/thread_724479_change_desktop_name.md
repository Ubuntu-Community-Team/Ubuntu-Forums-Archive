---
title: "change desktop name"
date: 2008-03-14
forum: Absolute Beginner Talk
---

### Post by 00arthuryu on 2008-03-14
heya
this is a very noobie question, but is there a way to change the computer name?
Because at the moment it comes up with something really silly as i did a typo when asking for the computer name lol

at the moment it comes up as
```
arthur@arthtysdesktop
```
its not annoying enough to reinstall ubuntu, but its still annoying ^_^

thanks!

---

### Post by joshrobinson on 2008-03-14
never fully tried it, but go to system > administration > network
click general tab
change the hostname and reboot

---

### Post by incen on 2008-03-14
> **joshrobinson said:**
> never fully tried it, but go to system > administration > network
click general tab
change the hostname and reboot

This really is a fancy way! I always do it by modifying 'hostname', which is under /etc.
You can eidt it with any kind of editor you prefer.

---

### Post by Ardrias on 2008-03-14
Or you can just open a terminal and enter ```
sudo hostname DesiredMachineName
``` For most operations, doesnt *need* a reboot.

---

### Post by Forrest Gumpp on 2008-03-14
I think you may already have the answer, but just in case, here it is in perhaps slightly fuller form.

Want to know how I got it?

I clicked on the new topic button on an index page, and entered the question "How to change the name of the computer?" in the topic title field.  I then clicked in the message window and waited for the list of similar topics to come up.  First cab off the rank answered the question!  I clicked the 'Show Single Post button" at the top right of the post that answered the question, went to it in the new tab that opened, and copied the URL.  I then simply abandoned the new topic page and came back to your thread which I had up in a different tab in Firefox, and clicked 'Reply to Thread'.

And here we are!  The link to the answer is:  [http://ubuntuforums.org/showpost.php?p=1525068&postcount=2](http://ubuntuforums.org/showpost.php?p=1525068&postcount=2)

The topic search comparator is the best search function within the Forum.  You are free to use it anytime.

PS  I learnt how to change the name of my computer in the process!  Ain't the UF grand?

---

### Post by incen on 2008-03-14
> **Ardrias said:**
> Or you can just open a terminal and enter ```
sudo hostname DesiredMachineName
``` For most operations, doesnt *need* a reboot.

I've done this several times with Debian; however, it doesn't really work well and the hostname remains unchanged after reboot. I'm not sure if it could be the case for Ubuntu. Anyway, there are options!!! :)

---

### Post by 00arthuryu on 2008-03-14
hey!
Thank you for all the replies!
still abit embarassed from my noobiness lol
but it worked!
Cheers!
Arthy

---

### Post by joshrobinson on 2008-03-14
> **00arthuryu said:**
> hey!
Thank you for all the replies!
still abit embarassed from my noobiness lol
but it worked!
Cheers!
Arthy

dont worry about the noobieness you have to start somewhere, and asking questions is the best way to become an expert linux user
your welcome for the help

---

