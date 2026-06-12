---
title: "Trying to install MS Publisher 2000 with wine"
date: 2006-08-24
forum: Absolute Beginner Talk
---

### Post by Peter Mount on 2006-08-24
Hi

I attempted to install MS Publisher 2000 with WINE last night but it didn't seem to work. It installed the directory for Office in the .wine directory but I couldn't find any file to start MS Publisher 2000.

Do I need to install WineTools as well? I installed WINE from the repository information on the WineHQ site.

Failing this I do have Windows 98SE on my other hard drive. MS Publisher 2000 will work with that but it will just be a drag having to change the hard drive caddies just to change a Publisher file.

Thanks

---

### Post by TrendyDark on 2006-08-24
I don't know much about wine, but I know you can find the "wine drive" in your home folder. You must either select "view hidden files" from the menu or just press "ctrl+H"

You'll find a folder called .wine . Once you're in there, it should look familiar, then just make a link to the application on your desktop.

You can do this by finding the .exe file for publisher, right click and press "make link". Drag the link that is created to your desktop. Right click on it and  goto properties if you want to change the name or icon. 

It should open using Wine automatically. Just in case, check the "open with" tab and if it's not, click the "add" button and then "use custom command". The command is simply, "wine"

---

### Post by Peter Mount on 2006-08-25
Thanks TrendyDark 

I did actually view the hidden directories and get into the .wine directory last night but I might have missed the file. I'll have another look at it when I get home.

I did spend some time looking for the exe file for MS Publisher but for the life of me I couldn't find it. Maybe I was just too tired or something

Have fun

---

