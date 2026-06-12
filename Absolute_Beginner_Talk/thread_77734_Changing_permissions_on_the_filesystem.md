---
title: "Changing permissions on the filesystem"
date: 2005-10-17
forum: Absolute Beginner Talk
---

### Post by Mrtn on 2005-10-17
I wanted to extract something in my root directory (to change the appearance of Gaim) but it says I do not have the privileges. Being a windows XP user and recently having switched to ubuntu I do not know what to do.

Can I change the privileges somehow so I can read, write and execute wherever the hell I want to or is that not possible?

Or would it be a serious breach of security or whatever? :)

Thanks a lot.. !

---

### Post by LHZ on 2005-10-17
You execute  command with root priviledges by typing 'sudo <command>'. sudo stands for 'Super User DO'. This will prompt you for your password (your normal user password), and then execute the command.

For instance, if 
> 
cp /bla/derf/*.* /bin

gives a permission violation, you can do 

> sudo cp /bla/derf/*.* /bin

By default, 'sudo' only works if you're on the first user account that was made at installation. If you need help with that, let me know.

*edit:* (I forgot to mention this, but it's kind of important) you could set up the computer so that you always have access to everything, but that's  recipe for disaster. Linux tools will easily let a typo ruin your system, since it doesn't give you any 'are you sure?' prompts when you do something serious. It's best to restrict access to the critical system files (pretty much everything outside of /home) to root only, and use 'sudo' if you want to change anything. Much safer that way, since a random mistake won't mess up your entire filesystem.

---

### Post by Mrtn on 2005-10-17
Thanks...

So if I want to extract an archive in the Gaim map... what do I need to type?

sudo something...

but can't you just login as the root user or something? Isn't there an easier way?

I logged on as root now... but I still can't change read write privileges :(

---

### Post by LHZ on 2005-10-17
[QUOTE=Mrtn]Thanks...

So if I want to extract an archive in the Gaim map... what do I need to type?

sudo something...[/QUOTE]

To be honest, I've ever used GAIM, so I don't really know. Is there any documentation to be find where you downloaded the files?

[QUOTE=Mrtn]but can't you just login as the root user or something? Isn't there an easier way?[/QUOTE]

You can type 

> sudo su

Which will log you in as root. Remember to type 

> exit

afterwards, to return to your normal account.

[QUOTE=Mrtn]I logged on as root now... but I still can't change read write privileges :([/QUOTE]
That's weird. What exacty did you do, and did you get some form of error message?

---

### Post by Mrtn on 2005-10-17
Well, I was able to transfer the file but when I want to change the permissions from Places >> Computer >> Filesystem then it says sorry, the permissions could not be changed.

It gives the following error when logging in (as root)

$HOME/.dmrc file has incorrect permissions and is being ignored

---

### Post by LHZ on 2005-10-18
What are the permissions of /home/.dmrc? You can check with 

> ls -al

Or you can start a file browser with root privileges with

> gksudo nautilus

---

