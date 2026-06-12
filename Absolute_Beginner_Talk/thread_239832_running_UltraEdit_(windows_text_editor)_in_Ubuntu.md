---
title: "running UltraEdit (windows text editor) in Ubuntu?"
date: 2006-08-19
forum: Absolute Beginner Talk
---

### Post by JohnJSal on 2006-08-19
Ok, I have searched high and low for a good text editor to use in Ubuntu that can do some of the things that UltraEdit can do, and I'm simply not satisfied. Perhaps you guys can give me more suggestions, but for now I'm just wondering, is there any way I can run UltraEdit in Ubuntu? If so, would it be simple to do so?

Thanks,
John

---

### Post by taurus on 2006-08-19
Have you tried to run it under wine or even CrossOver Office?  Remember, wine is free while I believe you have to pay like $35 for a copy of CrossOver Office from Codeweaver...

---

### Post by JohnJSal on 2006-08-19
I suppose I could give it a try, but I was hoping to keep things down to a minimum in terms of programs like that. But I guess I have no choice in this case.

---

### Post by taurus on 2006-08-19
Or you can contact the people that create it to see if they plan to have it for Linux!!!

---

### Post by JohnJSal on 2006-08-19
Well, it does work with wine! But so far I've only tried opening up the uedit32.exe file from my /windows partition, and it doesn't seem to detect any of my settings or options, because it opens up like I just installed it for the first time. That's weird, since it's being opened from the same directory as where I use it from Windows.

---

### Post by taurus on 2006-08-19
I guess it looks for the setup/configure in your home directory in Dapper, not Windows...  So, maybe you can copy your config to somewhere like ~/.ultraedit or have it point to where it is on your Windows partition.

---

### Post by JohnJSal on 2006-08-19
Is there a way for me to just install UltraEdit on Ubuntu? I tried using wine to run the UE setup.exe file, but it said something about insufficient disk space (which is not the case) and stopped.

---

### Post by digby on 2006-08-19
Have you played with any of the text editors available for linux?  There are some out their that really are quite renowned.  

Take a look at gedit (in gnome) or kate (in KDE) along with vi, emacs, bluefish (for html), and many others.

If you're just looking to run the one you are familiar with, however, then you're already on the right path.  As to your question of why it couldn't find you settings, it's looking in the wrong spot.  When you run a program inside wine and it looks for a file in c:\somewhere\, wine interprets this to mean something like /home/username/.wine/drive_c/Program Files... etc

If you copy your config files from your windows partition to the corresponding location in ~/.wine, it should work fine.

As for your insufficient disk space, I'm not really sure what could cause that... can you post the ouput of the command 'df'?

---

### Post by JohnJSal on 2006-08-20
Well, what I did was reinstall UltraEdit on my shared partition and accessed it from Ubuntu that way. Except that somehow the changes I make while in Linux are still affecting my other copy of UE on my C: drive!

Another small problem is that wine doesn't seem to render my bold fonts for syntax highlighting. :(

---

