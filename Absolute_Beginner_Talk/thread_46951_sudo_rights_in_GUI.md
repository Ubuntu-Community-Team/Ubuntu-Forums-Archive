---
title: "sudo rights in GUI"
date: 2005-07-06
forum: Absolute Beginner Talk
---

### Post by PaulWiggers on 2005-07-06
Hello,

I am not allowed to do anthing in the GUI. How can i get enough rights so that i can move and/or delete files?

tia

---

### Post by Kvark on 2005-07-06
Type this in a terminal:
gksudo nautilus

Then you get a nautilus window where you can move/delete files as root.

"gksudo gedit file" works to edit a text file with gedit as root and so on for other programs.

---

### Post by PaulWiggers on 2005-07-06
Thanks,

but i was more looking for a means of getting sudo right in the complete system, and not just only in the program you are specifying. Is this possible?

---

### Post by aysiu on 2005-07-06
Then, instead of opening a terminal and typing *gksudo nautilus*, create a custom launcher in the panel called "browse as root" and make the command *gksudo nautilus*.

To add a custom launcher, right-click on the panel, pick "add to panel," then select "custom application launcher."

---

### Post by Umbra on 2005-07-07
So, with all these, r u trying to say there is no way to start and manage a root session by completly?

---

### Post by aysiu on 2005-07-07
[QUOTE=Umbra]So, with all these, r u trying to say there is no way to start and manage a root session by completly?[/QUOTE] Can you give a reason for needing to have a root session? If you create that custom launcher I recommended, you can just click on a button and browse the file manager as root. When you close that window, you're done.

If you create a root session, that means you have to log into root. Then, when you're done, you have to log out of root. Then, you have to log back into user.

Seriously, give the custom launcher a go. If you absolutely must enable a root login, you can do so as described [here](http://ubuntuforums.org/archive/index.php/t-31053.html).

---

### Post by Umbra on 2005-07-07
Im not refering just to use a file brower, the reason for start a root session would be to make changes in the system, faster and more confortable than being using the sudo command for every single thing you want to setup.

---

### Post by tread on 2005-07-07
But you don't need it every single time. Say you start synaptic, and enter the password once. For the next 15 minutes,  that password is remembered, so if you wanted to go into the Login Screen setup, you don't need to type in the password again.

[http://ubuntuguide.org](http://ubuntuguide.org)  has information on how to setup a root account and allow him/her to login to gnome, but I would really advise against using that because its risky.

---

### Post by aysiu on 2005-07-07
[QUOTE=Umbra]Im not refering just to use a file brower, the reason for start a root session would be to make changes in the system, faster and more confortable than being using the sudo command for every single thing you want to setup.[/QUOTE] If you file browse as root, that's how you make changes in your system. You type the gksudo command *once* to set up the custom launcher. After that, you *click* with your mouse on the launcher and you can browse files and folders *graphically* with root privileges.

Look, just try out the custom launcher. If you don't like it, you can always delete it. After all, it's just an icon. I also gave you instructions for enabling a root login.

---

### Post by Umbra on 2005-07-07
Well, looking it that way it seems useful, but think about ppl who dont use gnome. Im one of them, i installed kubuntu and im new to linux.

---

### Post by aysiu on 2005-07-07
[QUOTE=Umbra]Well, looking it that way it seems useful, but think about ppl who dont use gnome. Im one of them, i installed kubuntu and im new to linux.[/QUOTE] Since Gnome is the default desktop in Ubuntu, people on these forums will assume you're talking about Gnome unless you go out of your way to say, "I'm using Kubuntu" or "I put KDE on my Ubuntu installation."

Maybe this thread might help you, then?

[http://ubuntuforums.org/archive/index.php/t-26349.html](http://ubuntuforums.org/archive/index.php/t-26349.html)

---

### Post by PaulWiggers on 2005-07-07
Thanks for all the reply's

But the reason why I want complete control is because right now i cannot save text files (or wil that be changed then). And because i am having some trouble with my adsl and my modem gives me the msg that the connection has been refused. Just want to check if that has something to do with my rights. But what you are saying is that you can only get sudo rights on one thing and not on the complete system?

---

### Post by Kvark on 2005-07-07
To edit a textfile as root you type "gksudo gedit file" in a terminal.

It is bad security to have root all over when you only need it for one or a few programs.

---

### Post by Leliel on 2005-07-07
[QUOTE=Kvark]To edit a textfile as root you type "gksudo gedit file" in a terminal.

It is bad security to have root all over when you only need it for one or a few programs.[/QUOTE]

on the other hand, it is also the first step, on the path to the single login system windws uses, which is even more insecure

after all, if logging off, and logging on again as root, is too much hassle, sooner or later typing a password will be too mcuh hassle, so you just use root for day to day.

it's little niggles like this, that are fast turning me off ubuntu

---

### Post by nocturn on 2005-07-07
[QUOTE=Leliel]on the other hand, it is also the first step, on the path to the single login system windws uses, which is even more insecure

after all, if logging off, and logging on again as root, is too much hassle, sooner or later typing a password will be too mcuh hassle, so you just use root for day to day.

it's little niggles like this, that are fast turning me off ubuntu[/QUOTE]

I disagree.  I have been working this way for years and it makes sense.
Logging out and back in as root is what you have to do on windows, thereby making it more comfortable for un with admin privileges all the time.

If you log out, and log in as root and then realize you need to check a howto, there goes FireFox, as root.  Everything you do: as root.

With sudo, you launch everything as a user, and become root only for a specific command (like synaptic).  This makes sense.

---

### Post by GrootBrak on 2005-07-07
I cannot even get my synaptic packet manager to open and I certainly don't have application launcher anywhere on my desktop. Seems like I missed a lot of things as well. The guide often show the procedure how to do/activate apps, but I usually don't have the specific selections on the desktop available. Do I have an old installation?

---

### Post by aysiu on 2005-07-07
[QUOTE=PaulWiggers]Thanks for all the reply's

But the reason why I want complete control is because right now i cannot save text files (or wil that be changed then). And because i am having some trouble with my adsl and my modem gives me the msg that the connection has been refused. Just want to check if that has something to do with my rights. But what you are saying is that you can only get sudo rights on one thing and not on the complete system?[/QUOTE] You can't save *any* text files, or you can't save configuration text files? Are you using Ubuntu with KDE, or are you using Kubuntu? All of the suggestions I gave you give you temporary root access to the file browser. This means any file you navigate to within that window you will have root privileges to edit, copy, move, whatever. Once you close that window, you're back to user. The only issue has really been getting the temporary root access for *KDE* v. *Gnome*.

I guess I'm asking you... what's the problem?

Is it that you're frustrated because you think your installation may be busted and that you're finding you need root privileges for everything and you think your permissions may be off?

Or are there special files that you need access to just to set up Kubuntu/Ubuntu, but you're finding there are a lot of these special files (five or six), so you don't want to have to type into a terminal every time you want to edit them?

I'm address the latter situation.

---

### Post by Umbra on 2005-07-07
PaulWiggers:


Use this way, it worked fine for me and it is easy:

-in the terminal use sudo passwd root, specify the root password.
-end session
-in the logon screen, lower icons, choose login with terminal
-login as root
-use command startx

your x windows system will start in root mode.

---

