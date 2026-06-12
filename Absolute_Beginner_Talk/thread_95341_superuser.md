---
title: "superuser"
date: 2005-11-26
forum: Absolute Beginner Talk
---

### Post by paulozzzz on 2005-11-26
People,

I recently installed Ubuntu and the installation program did not ask me to enter the root pasword.

I need to change the /etc/hostname file which belongs to the root user and my current user can only read it.

I need to login as root in order to change it.  The problem is that when I enter the su command the blank password does not work and I do not have a clue of what to do.

What is the procedure to login as root in Ubuntu?  In Kurumin, for instance, the root password is set to blank so you can define it in the first time you try to login as root, but in Ubuntu it has become a rather mysterious procedure.

---

### Post by ofek on 2005-11-26
You can use sudo, have a look at this wiki: [https://wiki.ubuntu.com/RootSudo?highlight=%28sudo%29]("https://wiki.ubuntu.com/RootSudo?highlight=%28sudo%29")

---

### Post by paulozzzz on 2005-11-26
Thanks.  However I would like to start the graphical text editor and edit the file.  Is there a way to execute this "sudo" by double-clicking the file in the file manager?

---

### Post by Tiede on 2005-11-26
I can't recall if there is a way. But if your problem is about using the command line to sudo because it seems difficult (although it is not ;) ) you can try either 
>  To run a program using sudo that normally is run as the user, such as gedit, go to Applications --> Run Application and enter gksudo gedit.
or better yet:
if you are running Breezy Badger, > go to Applications --> System Tools --> Run as different user.

---

### Post by paulozzzz on 2005-11-26
"I can't recall if there is a way. But if your problem is about using the command line to sudo because it seems difficult (although it is not  )"

Actually I prefer the console.  The main problem is the name of the executable that starts the grapical editor.  I see no problem in using "sudo <executable> /etc/hostname" for instance.

"To run a program using sudo that normally is run as the user, such as gedit, go to Applications --> Run Application and enter gksudo gedit."

It worked, thanks!  But how about the other executables that I possibly need to run as root?  How can I know the exact name?  In this case you knew the system name of the editor ("gedit").  In Windows I check the properties of the shortcuts to find out the name of the executable files.  How do I do this in Ubuntu?

"or better yet:
if you are running Breezy Badger,
Quote:
go to Applications --> System Tools --> Run as different user."

That was very useful, but I still need to know the executable name.

Edit do add:  that last procedure did not work because it requested the root password, which I do not know.

---

### Post by Kvark on 2005-11-26
The name of a program's executable usually the program's name in lower case. For example Firefox's executable is called firefox, Stream Tuner's executable is called stream-tuner and Synaptic's exectuable is called synaptic.

As for the graphical text editor, if you had gone to "help->about" in it's menues then you would have seen that it's name is Gedit, knowing that you could have tried with "gksudo gedit /path/file" in the terminal.

So try "gksudo <graphical program's name in lower case>" in the terminal.

---

### Post by paulozzzz on 2005-11-26
[QUOTE=Kvark]The name of a program's executable usually the program's name in lower case. For example Firefox's executable is called firefox, Stream Tuner's executable is called stream-tuner and Synaptic's exectuable is called synaptic.

As for the graphical text editor, if you had gone to "help->about" in it's menues then you would have seen that it's name is Gedit, knowing that you could have tried with "gksudo gedit /path/file" in the terminal.

So try "gksudo <graphical program's name in lower case>" in the terminal.[/QUOTE]

Hmmm...  that would suffice.  Thanks.

Thanks all for the help offered.:D

---

### Post by saywell on 2005-11-26
I too have had this problem, and the above seem only to be work-arounds.
How do you log in as root?
Why doesn't the installer ask you to set a root password?

William

---

### Post by aysiu on 2005-11-26
[QUOTE=saywell]I too have had this problem, and the above seem only to be work-arounds.[/quote] The best workaround I know of is to create a launcher with the command ```
gksudo nautilus
``` for Gnome or ```
kdesu konqueror
``` for KDE. It's a lot faster and easier to use than a separate root login.

> 
How do you log in as root?
Why doesn't the installer ask you to set a root password? Read this for all the details: [https://wiki.ubuntu.com/RootSudo](https://wiki.ubuntu.com/RootSudo)

---

### Post by paulozzzz on 2005-11-26
Well, the Ubuntu is installed in my notebook and I would like to master my private system (no one else uses it and it is not connected to a LAN), so I would like to simply log in as root and do whatever I want with my system.

Using the restricted account the setup program has created for me leads to nagging situations.  I often have to retype my password when I perform certain commands and this is very, very annoying.

How can I master an OS without full privileges?

---

### Post by Kvark on 2005-11-26
[QUOTE=paulozzzz]Well, the Ubuntu is installed in my notebook and I would like to master my private system (no one else uses it and it is not connected to a LAN), so I would like to simply log in as root and do whatever I want with my system.

Using the restricted account the setup program has created for me leads to nagging situations.  I often have to retype my password when I perform certain commands and this is very, very annoying.

How can I master an OS without full privileges?[/QUOTE]
If you mean that you want to be logged in as root all the time then consider that every single program you run while logged in as root has complete control over your computer. That includes the web browser, the java runtime environment, some cool utility you feel like trying, some silly game you play, a bash script a friend gave you, a terminal command you misstyped, a drag n' drop you picked up by mistake, a keyboard shortcut where you hit the wrong key. and everything else.

If you mean that you want to use a user account most of the time but log in as root to do admin taks. Why would you want to log out from your account and re-login to another account every time you want to install something?

Sudo/gksudo is IMO a convient way to be able to do admin taks without giving complete control to every single program. And the password nags serve as warnings that it is an action that changes the system so you should think twice.

---

### Post by paulozzzz on 2005-11-26
[QUOTE=Kvark]If you mean that you want to be logged in as root all the time then consider that every single program you run while logged in as root has complete control over your computer. That includes the web browser, the java runtime environment, some cool utility you feel like trying, some silly game you play, a bash script a friend gave you, a terminal command you misstyped, a drag n' drop you picked up by mistake, a keyboard shortcut where you hit the wrong key. and everything else.

If you mean that you want to use a user account most of the time but log in as root to do admin taks. Why would you want to log out from your account and re-login to another account every time you want to install something?

Sudo/gksudo is IMO a convient way to be able to do admin taks without giving complete control to every single program. And the password nags serve as warnings that it is an action that changes the system so you should think twice.[/QUOTE]

Hmmm...  It makes more sense to me now.:smile:

---

