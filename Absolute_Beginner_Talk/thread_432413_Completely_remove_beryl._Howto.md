---
title: "Completely remove beryl. Howto?"
date: 2007-05-04
forum: Absolute Beginner Talk
---

### Post by pjones0404 on 2007-05-04
I had beryl running and it was perfect. i then made some unneeded changes and it will not even load now. in fact it freezes then entire desktop when i launch it.

how can i completely remove it so i can start w/ a clean slate? i have a tutorial for how i set it up so it will not be a problem getting it back. Can i just go to synaptic and remove all beryl options that are selected?

Thanks for any and all help that u can provide.

---

### Post by Billy McCann on 2007-05-04
You can do it like that, through synaptic, just be sure to choose "remove completely".  Or you can use the code below.  It'll remove emerald and emerald themes as well purging the configuration files with them.  

```
sudo apt-get update && sudo apt-get remove --purge beryl beryl-manager emerald emerald-themes
```

---

### Post by pjones0404 on 2007-05-04
thanx for the quick reply. i ran the command listed above an recieved the following output.

[I]E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
[/I]

i will try it through synaptics and see what happens. i will let you know the outcome.

thanx again

---

### Post by Billy McCann on 2007-05-04
Close Synaptic first.  That'll free up the resource.

---

### Post by pjones0404 on 2007-05-04
well i removed everything and attempted to run through the tutorial again and still the same issue w/ it freezing up. the unneeded change that i made that caused the isue is listed below. i am not sure what it does i was attempting to get ri of the black windos issue. 

*In the advanced beryl options, set: Texture from Pixmap; Force AIGLX and XGL binding. Leave the others as automatic.*

after i did this the issue started.i tried to sudp apt-get remove beryl and then reinstall but no luck. is there a possibility that the change i made is saved somewhere else that is not being removed when i uninstall beryl?

---

### Post by Billy McCann on 2007-05-04
Well, I thought that any changes you made to Beryl Settings would have been erased when you purged Beryl et al from your system.  Did you run the code that I gave you, the one above?  

Why don't you join us in Freenode?  We should be able to help you in #ubuntu-effects.  :)

App's > Internet > XChat

Join Ubuntu servers.

---

### Post by pjones0404 on 2007-05-04
yeah i ran the code u gave me and then ran through the tutorial that i have and the same thing happened. i am joining irc now.  i have not spent much time in irc before so i tend to fall behind as it scrolls by pretty quick. is there someone i should look for?

thanx for the help again.

---

### Post by Billy McCann on 2007-05-04
Just join and then ask for thebillywayne

---

### Post by Amablue on 2007-05-04
I was about to start a new thread, but it looks like someone else is having the exact problem I am. 

I changed one setting, and then Beryl completely froze my entire computer and I had to reboot. I started it up again, and tried to change the setting on beryl, but opening it at all freezes the computer. I completely removed it through synaptic, and then reinstalled it and the same thing happened again. 

If someone figures out how to fix this make sure to post it here so I can fix mine too.

---

### Post by Billy McCann on 2007-05-04
When you start Beryl, and you have the red jewel in your notification area, right click it and select "Advanced Beryl Options" > Rendering Path > Automatic.  Right now, all of *mine* in that entire "Advanced Beryl Options are set to Automatic.

---

### Post by Amablue on 2007-05-04
I can't, the instant Beryl starts the entire computer freezes. I can move the mouse, but nothing at all responds.

---

### Post by pjones0404 on 2007-05-04
well the guys in irc were able to get me back on track. i am sooo thankful as i did not want to have to reformat and install just to get beryl running again. if anyone is curious they advised me to run the following command then reinstall.

*rm ~/.beryl-managerrc; mv ~/.beryl ~/.beryl.save; mv ~/.emerald ~/.emerald.save*

---

### Post by Amablue on 2007-05-04
Awesome, that did it. 

Thanks =D

---

### Post by Billy McCann on 2007-05-04
Cool.

---

