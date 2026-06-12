---
title: "First Wine Experiment"
date: 2007-08-03
forum: Absolute Beginner Talk
---

### Post by ukulele_ninja on 2007-08-03
Im embarking on my first wine install but I have no idea what to do! I downloaded Wine and am currently downloading Second Life as I hear it works really nice with Wine. What exactly do I need to do to get this running and how do i install it with Wine? If you have a guide to point me in the right direction that would be great too!

---

### Post by anewguy on 2007-08-03
Hopefully you installed WINE via the package manager repositories.:)

I've never download what the game you are talking about, but I will guess it will have some executable for installation?  If so, just open a terminal window and do the following:


wine path-to-file/file-name-of-install-executable  (obviously you need to replace the string)

That tells WINE to execute the file you are pointing to.  With luck, it should install to the c: drive in WINE and maybe even put an icon on your desktop to run the program.

Good luck!:)

---

### Post by ukulele_ninja on 2007-08-03
Ok it installed fine and it did put a icon on my desktop, except when I try to run it says it cant detect direct-x then it crashes. What do I do in this instance?

---

### Post by anewguy on 2007-08-03
Well, your at the limit of my knowledge in this area!  Perhaps someone else can help you now?

BTW - is there any kind of configuration file for it that perhaps you could override the direct x setting in?:)

---

### Post by Lacrimstein on 2007-08-03
read here:[http://appdb.winehq.org/appview.php?iVersionId=4619]("http://appdb.winehq.org/appview.php?iVersionId=4619")

Basically, you're out of luck unless you are running Ubuntu Dapper Drake

---

### Post by splintercellguy on 2007-08-03
Maybe....

Did you follow the HOWTO and set application profile in winecfg for secondlife.exe to XP and sound to OSS? And perhaps the latest 0.9.41 might do it, [http://winehq.org](http://winehq.org).

---

### Post by ukulele_ninja on 2007-08-03
How do I set all of that?

---

### Post by Lacrimstein on 2007-08-03
open terminal and run "winecfg" - a really usefull tool

in the "Applications" tab select "Add Application..." and locate the game's launcher .exe file (Its probably in one of the folders in ~/.wine/drive_c/)
Then under "Windows Version" select "Windows XP"

Sound Tab:
make sure that all the checkboxes except "OSS Driver" are unchecked

That's it:KS

---

### Post by ukulele_ninja on 2007-08-03
Maybe tis is my problem then because I dont have a wine folder that I can find anyway...also, where it asks me which version I want to use, the highest it goes in Windows 2000

---

### Post by Lacrimstein on 2007-08-03
o.0

Perhaps you are using an older version of wine? check in the "About" tab. The newest version is currently 0.9.42.

---

### Post by Lacrimstein on 2007-08-03
Also, the .wine folder is a hidden one (starts with a dot)
And the "Add Application..." button should automatically take you there...

---

### Post by ukulele_ninja on 2007-08-03
yep, 9.33.... how do i update it?

---

### Post by Lacrimstein on 2007-08-03
open terminal, type "sudo synaptic"
scroll down until you see "wine" package, right-click on the box next to it, and select "Mark For Installation" or "Mark For Upgrade", then click the "Apply" button and wait until it finishes the installation

ALWAYS see if a program is in Synaptic repositories before downloading it from some random site - it might be outdated there (and its a lot easier to install from Synaptic)

---

### Post by ukulele_ninja on 2007-08-03
Alright did it the correct way this time but it says the same thing still :(

---

### Post by Lacrimstein on 2007-08-03
What do you mean "Same thing still" ? The version of wine? or the game?

---

