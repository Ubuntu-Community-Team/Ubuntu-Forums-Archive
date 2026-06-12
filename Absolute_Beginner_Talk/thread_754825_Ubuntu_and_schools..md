---
title: "Ubuntu and schools."
date: 2008-04-14
forum: Absolute Beginner Talk
---

### Post by Pictizm on 2008-04-14
Well hello there, I'm new to the forums and wanted to ask some assistence.
A friend and I are minor or less the most nerdy of the whole school and we were experimenting with linux distro's on the ol' Windows 2000 pc's.
These were modified to have some configurations to restore the student account every time the pc's were turned on with a program called skanix illusion or something. All settings were restored and the student couldn't touch any of the system configurations.

Lately alot of pc's are dieing here lately and we putted ubuntu 7.10 on them. I believe that's Feisty. These pc's now have a administrator account and a student account, all configured by me and my other friend.
We do are encountering some problems with the student account, it can do too much.
Well I'll put in a list of stuff I'd like to know how for these pc's.

- Restrictions to specific folders. The student account can actually view and edit the administrators documents, wich is not wanted.

- Student account can change all settings and **** up the account. I either would like some help on completely restricting this without a password OR some little program that resets the account everytime the pc is booting.

- A system to make all the changes made to one pc that completely works with all the features I added for school to just run it and finish it on the other pc's. Like a live cd, but with all the edits for the students and their restrictions.

- And last any other things handy for students that you know of.

Thanks in advance! :)

---

### Post by hyper_ch on 2008-04-14
> **Pictizm said:**
> - Restrictions to specific folders. The student account can actually view and edit the administrators documents, wich is not wanted.
Access is based onto file permissions... while they may READ administrators document by default the may not OVERWRITE those. They can, of course, save them as seperate altered copies.

> **Pictizm said:**
> - Student account can change all settings and **** up the account. I either would like some help on completely restricting this without a password OR some little program that resets the account everytime the pc is booting.
Resetting upon boot would be simple... you could create a "model" home directory for that user and write a small start script that removes the old one and copies the model back into it. Assuming your default user is called "DEFAULT" you could do this as a script:

```

#!/bin/bash
USER=DEFAULT
rm -Rf /home/$USER
mkdir /home/$USER
cp -a /model/$USER/* /home/$USER/
chmod -R 0755 $USER.$USER /home/$USER

```

symlink that script (or somethign similar) into the according runlevels and it will be executed upon boot...

> **Pictizm said:**
> - A system to make all the changes made to one pc that completely works with all the features I added for school to just run it and finish it on the other pc's. Like a live cd, but with all the edits for the students and their restrictions.
Not sure what you mean here


> **Pictizm said:**
> - And last any other things handy for students that you know of.
No clue :)

---

### Post by Pictizm on 2008-04-14
> **hyper_ch said:**
> 
Resetting upon boot would be simple... you could create a "model" home directory for that user and write a small start script that removes the old one and copies the model back into it. Assuming your default user is called "DEFAULT" you could do this as a script:

```

#!/bin/bash
USER=DEFAULT
rm -Rf /home/$USER
mkdir /home/$USER
cp -a /model/$USER/* /home/$USER/
chmod -R 0755 $USER.$USER /home/$USER

```

symlink that script (or somethign similar) into the according runlevels and it will be executed upon boot...


Could you specify in what config I should put it, I'm not working that long with ubuntu yet.
In fact, could you give me a step by step? :mrgreen:

---

### Post by hyper_ch on 2008-04-14
well, create a new user and log in with that one... it will create a his home folder in /home...  then alter it all the way you want until you are happy, and then make a backup of that folder... this will then be the default folder that will be setup upon every boot for that user

---

### Post by GoCool on 2008-04-14
This is what I was precisely looking for. Thank you hyper_ch for the script. But where should I put the script? (Sorry, I was a windows user till now, so there I know you can just put in the Startup folder, but not sure how it works in Ubuntu?)

---

### Post by hyper_ch on 2008-04-14
well, you would create somewhere a script.sh file...

howevere I would put it into /etc/init.d and then run

```

sudo update-rc.d script.sh defaults

```

That should add it to the according runlevels and hence it will be executed upon each boot...

---

### Post by HermanAB on 2008-04-14
Maybe you should look at Edubuntu [http://www.edubuntu.org/](http://www.edubuntu.org/) instead of trying to re-invent the wheel.

Cheers,

Herman

---

