---
title: "Absolute Beginner - after update no login possible"
date: 2006-06-28
forum: Absolute Beginner Talk
---

### Post by dawandeh on 2006-06-28
hey!

i downloaded the ubuntu 6.06 yesterday...installing was easygoing...today i plugged in a friends dslcable and downloaded the updates...
BIG SURPRISE:
after restart the login screen comes up as usual...i enter username and password and up comes a black screen for 1 second saying:
"Ubuntu 6.06LTS computername tty1"
"computername login:"
then i get back to the login screen!

-when i type a wrong username or pw...he says "incorrect login/pw"
- typing the correct username/pw ->no login possible as described above

i really do hope someone can help me on this, please don´t send me back to winxp:???: 

tnx a lot
dawandeh

---

### Post by simone.brunozzi on 2006-06-28
You can try to boot in recovery mode, or to insert a liveCD and boot a recovery mode from there.

Hope it helps.

Cheers,

---

### Post by dawandeh on 2006-06-28
thanks for the hint!

i started in recovery mode....the screen is black now and it says:
"root@mycomputer:~#"

as i am a complete newbie(downloaded it yesterday), i don´t know what to do now...
..can i recover my password? reenter my passwords?
..what/how can i do it at this stage/what do i have to type???

tnx
dawandeh

---

### Post by bruce89 on 2006-06-28
If you need to change your password type ```
passwd <username>
``` from the recovery mode.

---

### Post by dawandeh on 2006-06-28
i changed my password, but the result is the same...no login possible...

---

### Post by simone.brunozzi on 2006-06-28
[QUOTE=dawandeh]i changed my password, but the result is the same...no login possible...[/QUOTE]

Ok, here it is:

when you enter recovery mode, you will see a prompt.
When the prompt ends with $, it means that you are a normal user.
When it ends with #, it means that you are root (superuser), and thus you can do EVERYTHING.
You change your current root password typing "passwd", or your user's password (suppose your user is tom) typing "passwd tom".

Now you need to reboot and start in normal mode.

If you can't reach a login screen, you have some other problem.

Cheers,

---

### Post by dawandeh on 2006-06-28
so i´m a superuser not able to anything:-)

i did as you told me, i changed the password, but i can´t get over the login screen(problem described in my first post)...

i have no idea what the problem is, but could(following a windows coputer logic) a new update resolve the problem? is there any way to deinstall the update which caused the problem???

tnx for ur patience and help
dawandeh

---

### Post by simone.brunozzi on 2006-06-28
Hmm... it doesn't seem easily solvable...

as root (on a normal, white-on-black prompt), try this:

aptitude clean
aptitude update
aptitude upgrade

the first "cleans" your recent updates; the second updates the list of newer packages; the third installs them.

Hope it works.

Cheers,

---

### Post by dawandeh on 2006-06-28
heidihoh!

it works!!!
thank u so much for helping me out!

greetz
dawandeh

---

### Post by simone.brunozzi on 2006-06-29
wow, I'm very happy that it worked!

Glad to be of help! Remember the Ubuntu spirit towards other people... you can be of help too!

Cheers,

---

### Post by dakira on 2006-11-06
Hi,

> **dawandeh said:**
> heidihoh!
it works!!!
thank u so much for helping me out!


I just stumpled upon the same problem on a friends computer. Just for the sake of completeness, let me tell you what exactly your problem was:

Your harddrive was full ;-)

So the line that helped was *apt-get clean* because it freed up some disk-space so you could login again.

Again, I was just adding this information in case someone else has this problem. *clean* will only work, if there are old packages left on your computer. If you have this problem just go to a text-terminal (CTRL+ALT+F1) and login. Than delete some unneeded stuff from your $HOME dir.

Wiping /tmp is also helpful.

dakira

---

