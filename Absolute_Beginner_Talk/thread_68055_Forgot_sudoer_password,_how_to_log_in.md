---
title: "Forgot sudoer password, how to log in?"
date: 2005-09-21
forum: Absolute Beginner Talk
---

### Post by rajsarkar on 2005-09-21
Hi,

I installed Edubuntu preview release. During first log-in I am getting the message that either username or password is wrong. May be I did some mistake during installation which is unlikely for the password as it is asked for twice. Only the username could be entered wrongly.

I then, boot in recovery mode and tried to add more sudoers which did not work.

Where can I find the "sudo"'s username and password or how can I add new sudoer with password. 

Once I am logged in hoe can I check the sudoer detail?

Thanks,

Raj

---

### Post by Wolki on 2005-09-22
[QUOTE=rajsarkar]Where can I find the "sudo"'s username and password or how can I add new sudoer with password. 

Once I am logged in hoe can I check the sudoer detail?[/QUOTE]

I forgot how to add new sudoers (iirc it involves visudo), but you should be able to find out the username by logging into recovery mode, then executing "cat /etc/passwd" It will show a (detailed) list of all users. The first ubuntu user usually has the number 1000, so the line should look like "<username>:x:1000". Then "su <username>" and "passwd" to set a new password.

---

### Post by az on 2005-09-22
[QUOTE=rajsarkar]Hi,

I installed Edubuntu preview release. During first log-in I am getting the message that either username or password is wrong. May be I did some mistake during installation which is unlikely for the password as it is asked for twice. Only the username could be entered wrongly.

I then, boot in recovery mode and tried to add more sudoers which did not work.

Where can I find the "sudo"'s username and password or how can I add new sudoer with password. 

Once I am logged in hoe can I check the sudoer detail?

Thanks,

Raj[/QUOTE]
What do you mean add more sudoers?

From the recovery mode prompt, do

adduser (name)

also, check to see what the name of your first user is.  then change it's password accordingly

ls /home
passwd (user) (newpassword)

then run
init 2 
to boot into your fixed system!

---

### Post by rajsarkar on 2005-09-23
Thanks for all the replies. 

I could solve the problem.

I just did [COLOR=Navy]cat /etc/passwd[/COLOR] and I was able to recognize my sudo username. (one letter was missing from my usual user name)

However, one interesting observation:
from recovery mode I executed the following command: 
[COLOR=Navy]export EDITOR=nano && sudo visudo[/COLOR]
But I could not found my user name there. Where is the name of the sudoer and other users stored?

-Raj

---

### Post by wishyjr on 2005-09-23
hello everybody! (this is my first post) I'm really impressed with the ubuntu community so far -hope i can get in on the fun soon..

but i'm having a similar problem rajsarkar..

ive installed ubuntu (fairly easily) but cant log into the gnome login screen. Its giving me "the username/password is wrong" message. So ive tried to do what was suggested on this topic but it wont let me create any users! at all. I used the cat /etc/passwd ocmmand at the recovery prompt and got a load of information -nothing to do with any users though. so i went ahead and ran newuser which at first seemed to run but then stops and reverses all the commands it just ran (new group,new user etc.)

but theres a little more..

when i was installing ubuntu, there came the point where i was to define a user name and password then a repeat of the password (as you do :) ) but once i hit enter after inputting the password for the second time it just went back to the enter user part of the install process again. I tried this 3 or 4 times but it just kept returning to the same part - eventually, i just cancelled (which i didnt think would work to be honest) and the install carried on regardless.

any ideas chaps?

EDIT: oh i forgot to mention - when trying to 'adduser' and the systgem runs all the little bits that add the name (i.e. creating group, creating name, creating directory in home or whatever it says) it displays a 1000 next to it. now am i correct in thinking that that is the first username number? if so then doesnt that mean that theres no users setup on my system (apart from the 'superuser' or root)?

thanks

---

### Post by wishyjr on 2005-09-24
anyone got even a single suggestion? should i try reinstalling ubuntu form scratch? cant i add a first user after install at all?

---

### Post by phen on 2005-09-24
did you use invalid characters for your username? i am not perfectly sure, but i think that /\().- and so on are not valid username-characters! maybe you confused the installer a bit :)

did you try to use cat /etc/passwd as described above?

---

### Post by wishyjr on 2005-09-24
hiya, yeah im pretty sure i didnt use invalid charaters -i did use a digit though but i thought they were ok. does the name have to contain a certain amount of letters?

i also used the cat /etc/passwd and it displayed a big long list of data, alsorts of things but nothing related to a username or password, however i couldn catch the first part of the data, is there a way of getting it to stop until i press a key or something?

thanks for the reply

---

### Post by Wolki on 2005-09-24
[QUOTE=wishyjr]i also used the cat /etc/passwd and it displayed a big long list of data, alsorts of things but nothing related to a username or password,[/quote]

It does, Ubuntu creates a lot of users on installation, but only one you can actually log in into. That's usually the one with the number 1000.

> 
however i couldn catch the first part of the data, is there a way of getting it to stop until i press a key or something?


Either scroll up afterwards (shift-pgup) or tell Ubuntu to send the output to a program that allows scrolling up/down. You do that by adding "| less" to a command. Like "cat /etc/passwd | less"

---

### Post by wishyjr on 2005-09-24
cool, thanks alot - i'll give it a go. should the 'loginable' username and password be at the top if i scroll up or am i just not looking hard enough!? :)

---

### Post by wishyjr on 2005-09-24
ok, tried using the shift-pgup to have a look for the user info on a cat/etc/passwd but i'm honestly telling you there is no login username and password and no uid 1000

btw i tried running adduser again and realised its stopping with this line:

chown 1000:1000 /home/wishy: operation Not Permitted

so i was thinkin my problem might be with read/write permissions on my home partition. As its stopping there adn then reversing what it previously did (i.e. add group, add username etc.) Is there anything i should specifically setup whe sorting out my partitions? i thought i'd done it properly but now i'm second guessing :)
I'd set a seperate FAT32 partition to be used by both winXP and Ubuntu which i think i set  to mount as /home -did i make a boo boo?

any thoughts please chaps? my brain is workin overtime (esp. for a saturday) :)

---

### Post by Mustard on 2006-03-08
I believe fat32 doesnt remember permissions, iirc.

-edit-

I dug this thread up in a search and seemed to have resurrected it. :)

I thought I was looking at 'New Posts'. :D

---

