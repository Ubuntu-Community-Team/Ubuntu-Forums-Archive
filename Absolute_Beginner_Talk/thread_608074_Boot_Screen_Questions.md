---
title: "Boot Screen Questions"
date: 2007-11-09
forum: Absolute Beginner Talk
---

### Post by P4rD0nM3 on 2007-11-09
Hey guys, is there a way to disable the Ubuntu boot screen (Ubuntu logo plus progress bar)...and instead show text? I like it better if it's all text instead of that one...

---

### Post by Duck2006 on 2007-11-09
In your menu.lst remove the splash and quit from the i think it's the kernel line.

---

### Post by Duck2006 on 2007-11-09
Change this

kernel		/boot/vmlinuz-2.6.20-16-generic root=UUID=900abd02-0810-49de-9ab8-7d5a823aedbe ro quiet splash

to this

kernel		/boot/vmlinuz-2.6.20-16-generic root=UUID=900abd02-0810-49de-9ab8-7d5a823aedbe ro

inyour menu.lst and the bar and ubuntu will be gone.

---

### Post by oilchangeguy on 2007-11-09
> **P4rD0nM3 said:**
> Hey guys, is there a way to disable the Ubuntu boot screen (Ubuntu logo plus progress bar)...and instead show text? I like it better if it's all text instead of that one...

unless you're having boot problems there's no real reason to do this. i don't have your answer. but neither does post #2. never ever enter a command when someone tells you, i think this is correct.

---

### Post by P4rD0nM3 on 2007-11-09
Where is the menu.lst? And how do I change that long line?

---

### Post by matthewcraig on 2007-11-09
/boot/grub/menu.lst

You will need to use the sudo command to edit this file.

---

### Post by Rinzwind on 2007-11-09
sudo gedit /boot/grub/menu.lst

find the 'quiet' somewhere at the bottom and delete that word.

---

### Post by P4rD0nM3 on 2007-11-09
> **oilchangeguy said:**
> unless you're having boot problems there's no real reason to do this. i don't have your answer. but neither does post #2. never ever enter a command when someone tells you, i think this is correct.

Ok, I don't get what you mean...but this is all I want to do.

In Vista, you can disable the GUI while Vista is booting...then you can select something that will display the drivers as they are being loaded.

That's what I wanted to do...nothing more. For me it's prettier.

---

### Post by P4rD0nM3 on 2007-11-09
> **Rinzwind said:**
> sudo gedit /boot/grub/menu.lst

find the 'quiet' somewhere at the bottom and delete that word.

Does deleting quiet turn off the logo boot screen?

---

### Post by Rinzwind on 2007-11-09
> **P4rD0nM3 said:**
> Does deleting quiet turn off the logo boot screen?

No. It will do 2 things:
before your splash screen you get code in normal text.
During the Ubuntu splash screen there is text with an OK behind it.
Same goes for shutting down: text below the Ubuntu splash.

To get rid of the splash screen you need to uninstall usplash.

---

### Post by P4rD0nM3 on 2007-11-09
Ok, looks like that's what I want to do...uninstall usplash. I'll put the word quiet back right?

---

### Post by P4rD0nM3 on 2007-11-09
Like do I really have to uninstall it? Can't I just disable it? I just want to boot in text mode...like Debian.

---

### Post by P4rD0nM3 on 2007-11-09
Can someone please help me boot in text mode?

---

### Post by sports fan Matt on 2007-11-09
Pardon, Sorry i cant but i do have a question..what is around the correct screen resolution for startup manager for a resolution of 1152X864?  I tried the one 1280X1024 and when i restarted ot took me a few extra seconds to boot cause i had the wrong resolution and just wondering for that 1152X?864 resolution what one i should use and color bit..Thanks

---

### Post by P4rD0nM3 on 2007-11-09
Man, I have no idea.:lolflag:

---

### Post by sports fan Matt on 2007-11-09
thats ok..lol  Its just a tiny small incoveince..it says something to the effect of your screen resolution isnt right in the boot, but after that my desktop and dark clouds screen saver come up..a hair smaller but its ok..i can adjust them:)

---

### Post by sports fan Matt on 2007-11-09
or, would it be easier to uninstall startup manager and just live with the boot?

---

### Post by P4rD0nM3 on 2007-11-09
No I got mine to work. Hehehe.

---

### Post by sports fan Matt on 2007-11-09
how?  and what would u use for 1152X764 resolution?  all it says is it says its not right..lol

---

### Post by P4rD0nM3 on 2007-11-09
That's your resolution?

---

### Post by JBAlaska on 2007-11-09
@ sox fan Matt,most times 1024x768 is the correct resolution for the upsplash.
```
sudo gedit /etc/usplash.conf
```
Whatever you change it to,remember to;
```
sudo update-usplash-theme usplash-theme-ubuntu
```

@ OP,100% text boot;
[http://ubuntuforums.org/showthread.php?p=2250022](http://ubuntuforums.org/showthread.php?p=2250022)

---

### Post by sports fan Matt on 2007-11-10
Jb , Thanks

OP:  Yeah, my eyes arent that great so the larger text helps my eyes greatly:)

---

### Post by tubasoldier on 2007-11-10
You should be able to turn off Usplash. It is a service. so if you have the boot up manager installed (bum) then you can simply disable it. Unless you really want to mess with grub's menu.lst or uninstalling it

---

### Post by azurepalm on 2007-12-23
hey, that's excellent tip. i downloaded bum and it is just what i needed. thanks.

maybe ubuntu should put it as default installed program for v8.04

---

