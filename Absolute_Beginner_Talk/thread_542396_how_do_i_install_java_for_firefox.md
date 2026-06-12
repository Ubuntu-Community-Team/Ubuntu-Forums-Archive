---
title: "how do i install java for firefox"
date: 2007-09-03
forum: Absolute Beginner Talk
---

### Post by antisocialist on 2007-09-03
i have the file jre-6u2-linux-i586.bin
i downloaded it from the java site and i want to install it
im a noob at ubuntu cuz i just got it and i want someone to give me a step by step way to do this (or at least noob friendly =p)
thanks in advance...

---

### Post by BoneyOne on 2007-09-03
Java is in the repo's so just type

```
sudo apt-get install java; j2re1.4-mozilla-plugin
``` into a terminal and it will install.

---

### Post by Duck2006 on 2007-09-03
Try System => Administration => Synaptic package manager and do a serach for java
or Applications => add/remove... and load it from there.

---

### Post by antisocialist on 2007-09-03
i did that and it prompted me for password.
i tried to type it in but it wouldnt let me type at all.
should i retry?

---

### Post by swinte1 on 2007-09-03
it does not print the password characters to the terminal when you type the password.  So just type the password and hit enter.

---

### Post by scragar on 2007-09-03
it does type it just doesn't show.

---

### Post by nowshining on 2007-09-03
what do u mean by it wouldn't let you as it should and it's the same password you use to sign into your account that you are using now.. when you type it in it you will not see anything except for circles which is a representation of you inputting you password - each circle represents what you put in the password box...

---

### Post by nowshining on 2007-09-03
and for the terminal what [scragar]("http://ubuntuforums.org/member.php?u=319899") said nice one..forgot to add that.. :) i was thinking of the synaptic package manager of one of the posts..

---

### Post by antisocialist on 2007-09-03
i tried hitting enter and it said wrong
i hit enter again and it looked like this:
[IMG]http://i207.photobucket.com/albums/bb172/antisocialist/whatigotwhenitriedthat.png[/IMG]

---

### Post by antisocialist on 2007-09-03
> **nowshining said:**
> what do u mean by it wouldn't let you as it should and it's the same password you use to sign into your account that you are using now.. when you type it in it you will not see anything except for circles which is a representation of you inputting you password - each circle represents what you put in the password box...

what i mean is i typed and absolutely nothing happened
there where no circles or anything just nothing...

---

### Post by nowshining on 2007-09-03
like what the other person said nothing will show so just type it out like you normally do and hit the enter key..this is a safey feature in ubuntu linux.. :)

---

### Post by Gremlinzzz on 2007-09-03
paste in terminal
sudo apt-get install sun-java6-jre sun-java6-plugin sun-java6-fonts
heres a guide
[http://ubuntuguide.org/wiki/Ubuntu:Feisty](http://ubuntuguide.org/wiki/Ubuntu:Feisty)

---

### Post by nowshining on 2007-09-03
after looking at the post again it seems like the second time you got it, but the plug in cannot be found maybe they gave you the wrong command..

---

### Post by nowshining on 2007-09-03
[Gremlinzzz]("http://ubuntuforums.org/member.php?u=200690") seems to have the write command....

---

### Post by gOLdenHaWK3D on 2007-09-03
> **antisocialist said:**
> what i mean is i typed and absolutely nothing happened
there where no circles or anything just nothing...

You typed in wrong command dear :)
The correct syntax is
[I]
sudo apt-get install sun-java6-jre sun-java6-plugin sun-java6-fonts
sudo apt-get install j2re1.4-mozilla-plugin[/I]

These are two commands. Run them seperately one after the other. This should work fine. Have you enabled the Universe & Multiverse repositories from Synaptic Manager?

---

### Post by antisocialist on 2007-09-03
> **Gremlinzzz said:**
> paste in terminal
sudo apt-get install sun-java6-jre sun-java6-plugin sun-java6-fonts
heres a guide
[http://ubuntuguide.org/wiki/Ubuntu:Feisty](http://ubuntuguide.org/wiki/Ubuntu:Feisty)

i did that and its doing something.
says its gonna take 40 some odd minutes
im just gonna wait it out

---

### Post by antisocialist on 2007-09-03
> 
These are two commands. Run them seperately one after the other. This should work fine. Have you enabled the Universe & Multiverse repositories from Synaptic Manager?

how i do that?

---

### Post by nowshining on 2007-09-03
i've always just copied and pasted both at the same time - input password and it works.. - bubble

---

### Post by nowshining on 2007-09-03
copy and paste them into the terminal by copying from this forum, go to the terminal right click and click paste now to use a command that you've done before hit the UP arrow key until you find the one u want and if you pass it up hit the down arrow key.. :) just a quick tip..

---

### Post by Gremlinzzz on 2007-09-03
Good site for noobs click the link
[http://www.psychocats.net/ubuntu/](http://www.psychocats.net/ubuntu/)

---

### Post by gOLdenHaWK3D on 2007-09-03
> **antisocialist said:**
> how i do that?

Goto System>Administration>Synaptic Pakage Manager
Click on Settings>Repositories.
Check all 4 repositories.

Then run the commands I told you before. Its too easy.

---

### Post by antisocialist on 2007-09-03
> **gOLdenHaWK3D said:**
> Goto System>Administration>Synaptic Pakage Manager
Click on Settings>Repositories.
Check all 4 repositories.

Then run the commands I told you before. Its too easy.

i ran first command it prompted for y or n i entered y and it said abort and prompted for a new command
i entered command again enter y hit enter and same thing happened

---

### Post by antisocialist on 2007-09-03
i closed terminal and restarted it and it worked.
im gonna wait for the dl to finish
why does the terminal download so slowly though its like 10kb on a 300kb connection?

---

### Post by gOLdenHaWK3D on 2007-09-03
> **antisocialist said:**
> i ran first command it prompted for y or n i entered y and it said abort and prompted for a new command
i entered command again enter y hit enter and same thing happened

Are you getting some sort of errors?
Do one more thing. Just run *sudo apt-get update* command before you type the ones I told you before.

---

### Post by gOLdenHaWK3D on 2007-09-03
> **antisocialist said:**
> i closed terminal and restarted it and it worked.
im gonna wait for the dl to finish
why does the terminal download so slowly though its like 10kb on a 300kb connection?

Good. :)

---

### Post by antisocialist on 2007-09-03
> **gOLdenHaWK3D said:**
> Are you getting some sort of errors?
Do one more thing. Just run *sudo apt-get update* command before you type the ones I told you before.

so do i close the terminal while the first one you told me runs and then re open it and enter that one?

---

### Post by gOLdenHaWK3D on 2007-09-03
> **antisocialist said:**
> so do i close the terminal while the first one you told me runs and then re open it and enter that one?

No. If Ubuntu is downloading the packages for you, then its fine. Do it in case it says that the package is not available in the repos etc. Else leave it.

---

### Post by Gremlinzzz on 2007-09-03
another way
go too synaptic package manager in the search window type java  click search
scroll till you find sun-java6-jre and sun-java6-plugin put a check in square choose install click apply
 after put this command in terminal
sudo apt-get install sun-java6-jre sun-java6-plugin sun-java6-fonts
too get extras

---

### Post by antisocialist on 2007-09-04
> **Gremlinzzz said:**
> another way
go too synaptic package manager in the search window type java  click search
scroll till you find sun-java6-jre and sun-java6-plugin put a check in square choose install click apply
 after put this command in terminal
sudo apt-get install sun-java6-jre sun-java6-plugin sun-java6-fonts
too get extras

i opened synaptics got this message:
E: dpkg was interrupted, you must manually run "dpkg --configure-a to correct the problem.
E:_cache->open() failed, please report
what do i do/how do i report

---

### Post by Gremlinzzz on 2007-09-04
paste in terminal
 sudo dpkg --configure-a
then try install again

---

### Post by Gremlinzzz on 2007-09-04
> **Gremlinzzz said:**
> paste in terminal
 sudo dpkg --configure-a
then try install again

sudo "dpkg --configure-a 
correct command

---

