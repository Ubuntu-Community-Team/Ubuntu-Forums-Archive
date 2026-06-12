---
title: "How do I disable sleep permanently?"
date: 2007-07-24
forum: Absolute Beginner Talk
---

### Post by marco123 on 2007-07-24
Hi.  I'm trying to disable the sleep button on my keyboard but can't find a sleep option in Keyboard Shortcuts menu?

I've found something which might be it in /etc/acpi/events/sleepbtn which says - 

# /etc/acpi/events/sleepbtn
# Called when the user presses the sleep button

event=button[ /]sleep
action=/etc/acpi/sleep.sh


Could I maybe comment out the last 2 lines?  Also is it safe to edit this file?  Or is there another way to permanently disable sleep?

Many thanks, Marco.

---

### Post by deadgobby on 2007-07-24
You could check your BIOS and see what the sleep time is. Some monitors will go to sleep after 20 minutes or so. Even if you have the sleep mod set for 1 hour. You might want to check your monitor internal settings and see if you can change the sleep time. 
Gobby

---

### Post by Golyadkin on 2007-07-24
> **marco123 said:**
> 
Or is there another way to permanently disable sleep?


Drinking five of the biggest mugs of latte from Starbucks does the trick for me :)

---

### Post by Majorix on 2007-07-24
I think its safe to comment out the 2 lines you mentioned. It will disable the trigger for sleeping. No action - no reaction.

If anything goes wrong you can run from terminal and use nano to uncomment the lines. But I don't think you will need it.

Good luck!

---

### Post by mkoyle on 2008-01-12
Although Marco never posted again, the above probably does disable that button's functions.

I was asking myself how to do this (i.e. I knew how once but forgot; anyway [https://wiki.ubuntu.com/FeistySuspendOverview](https://wiki.ubuntu.com/FeistySuspendOverview) gave me the clue I needed about which file to edit).  That page says that the first thing the hibernate.sh and sleep.sh scripts do is verify that the functions are not disabled in /etc/default/acpi-support

If you want to disable the power button AND the gnome logout screen buttons, the following is a good option:

Edit /etc/default/acpi-support and comment out the second and fourth lines.  If you know how to do that, you're done reading my post.  ;)  

If you don't know how to do that without instructions, use the following:

Applications --> Accessories --> Terminal

```
sudo gedit /etc/default/acpi-support
```

The beginning of the file should look like the following:

```
# Comment the next line to disable ACPI suspend to RAM
ACPI_SLEEP=true

# Comment the next line to disable suspend to disk
ACPI_HIBERNATE=true
```

Add pound (comment) symbols (#) like the comments say and the result should look like this:

```
# Comment the next line to disable ACPI suspend to RAM
#ACPI_SLEEP=true

# Comment the next line to disable suspend to disk
#ACPI_HIBERNATE=true
```

Hope this is helpful.

--Matthew

---

