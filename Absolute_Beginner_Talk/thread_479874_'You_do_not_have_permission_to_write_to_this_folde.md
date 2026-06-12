---
title: "'You do not have permission to write to this folder.' even though I'm the only accoun"
date: 2007-06-20
forum: Absolute Beginner Talk
---

### Post by Hork on 2007-06-20
t on Ubuntu.

Is there anyway to give my account full write access?  It's the only account on here ('taylor')

---

### Post by bobplano on 2007-06-20
all accounts are basically "limited accounts" meaning they don't have easy access to certain files. you need to use sudo with an administrator account (the account that was made when you installed). the difference between limited and administrator(to use the term loosely) is admins can use sudo. so just use sudo and you have access to everything you need.

---

### Post by NeoLithium on 2007-06-20
Files that are owned by the root user still require root permissions to write to them, which is why you'll see the use of sudo for moving, writing, editing files.  Check out man sudo for more information on it, is there anything particular you were trying to do?

---

### Post by raul_ on 2007-06-20
or you can open the file explorer by typing "gksudo nautilus" in the terminal. You gotta be careful with what you do though

---

### Post by Hork on 2007-06-20
Move a file to the lib folder.

What's 'sudo' and how do I use it?  A terminal command I assume?

---

### Post by Nikron on 2007-06-20
In Linux there's a account called 'root', the super user.  Always.  And root owns all system files, pretty much.  You can act as root, using the command sudo (I first remembered it as 'super user do').  The graphical way to do this is a command called gksudo.  So, it wirte to a file in the folder you could do gksudo gedit /folder/

---

### Post by drivel on 2007-06-20
root is bigest account than you only one user on your Ubuntu

---

### Post by bobplano on 2007-06-20
yes sudo is a command. it just allows root powers to the command you do. you can use gksudo nautilus  to drag it there or something like
sudo mv /file/whever /lib

---

### Post by Zzl1xndd on 2007-06-20
That really is for the protection and Safety of the System. Edit: some people beat me too it, anyway I find this use full open the terminal and enter  "sudo nautilus"
 (without the quotes of course) enter your password and in the window it opens you can basically effect anything. I find this a simple way to do it without too many commands.

---

### Post by wormser on 2007-06-20
Where are you trying to write to?  In order to write or execute some programs you need root privileges.  Typing the sudo or gksudo (for gui apps) it will give you these privileges.  You do not want to have root privileges all the time because that is not safe.

---

### Post by vexorian on 2007-06-20
your user has got the Ability to get root access but it won't get root access unless you request that to happen.

Adding sudo before a command makes the terminal ask you for your password if you give the password the command you just typed will have root access.

gksu is the graphical method for when you are not calling the command from a terminal.

so if you run: gksu nautilus it will ask you for your password and then nautilus will have root access.

But before you do it,  do you REALLY have to write to that folder?

Edit: this forum is way too active, when I began typing none of the las 5 posts was there...

---

### Post by linfidel on 2007-06-20
> **Hork said:**
> Move a file to the lib folder.

What's 'sudo' and how do I use it?  A terminal command I assume?Yes, in a terminal, you type "sudo" then the command you want to execute, and it prompts you for your password.

So, you would enter "sudo mv xxxx /lib".

---

### Post by Hork on 2007-06-20
I get the following error:
Error: no "edit" mailcap rules found for type "application/*"

[edit]Oh boy, I agree with one of the posters who said this forum was active.  None of the like, last 6 posts were there.  Ouch! :(

---

### Post by raul_ on 2007-06-20
> **Hork said:**
> I get the following error:
Error: no "edit" mailcap rules found for type "application/*"

[edit]Oh boy, I agree with one of the posters who said this forum was active.  None of the like, last 6 posts were there.  Ouch! :(

what did you type?

---

### Post by Hork on 2007-06-20
I got it working.

Thanks for the lightning (I really mean lightning!) fast replies, everyone.  You're all great. ;)

---

### Post by arvevans on 2007-06-20
In a terminal screen, enter this command:
[INDENT]man sudo[/INDENT]
This will tell you all about the sudo command.  When viewing man pages, use arrow keys to navigate and hit "q" when done.
_._

---

