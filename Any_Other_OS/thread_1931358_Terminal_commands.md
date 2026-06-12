---
title: "Terminal commands"
date: 2012-02-25
forum: Any Other OS
---

### Post by waseembaraskar on 2012-02-25
Hi everyone,

After successfully installing ubuntu ultimate edition.
1 - i am keen to learn console command.
if anyone have good notes or pdf about command please send me.

Now, Second thing i am facing is while installing new package i have to be login as root

i am try to do like this

> 
baraskar@baraskar-laptop:~$ su
Password:


After entering default password which i inserted while installing ubuntu. .
it show wrong password.

what i should do ?
what is default root password.

thanx . . .

---

### Post by jacob.david on 2012-02-25
By default Ubuntu doesn't create root accounts. Instead you have to use sudo to do the admin tasks.
For e.g. sudo apt-get install <pakage>
As for the unix commands, IMO it is better to google around and start. You can also use the man & info command once if you know the command but not sure about its usage.

---

### Post by winh8r on 2012-02-25
Hi,

firstly , for help with gaining root privileges have a look here:

[https://help.ubuntu.com/community/RootSudo]("https://help.ubuntu.com/community/RootSudo")


and for help with the command line look here:


[http://ubuntuforums.org/showthread.php?t=1909108]("http://ubuntuforums.org/showthread.php?t=1909108")

there is a link in my sig below which will allow you to install CLI Companion which is useful for learning the command line as you can add your newly learned commands to it and write your own description of what they do.

I hope this helps you.

---

### Post by scheibenlosen on 2012-02-25
> **waseembaraskar said:**
> Hi everyone,

After successfully installing ubuntu ultimate edition.
1 - i am keen to learn console command.
if anyone have good notes or pdf about command please send me.

Now, Second thing i am facing is while installing new package i have to be login as root

i am try to do like this



After entering default password which i inserted while installing ubuntu. .
it show wrong password.

what i should do ?
what is default root password.

thanx . . .

 Like the other person said, there is no default root password. What I do after a fresh Ubuntu install is to open a terminal, and then type "sudo -s" (no quotes). It'll ask for your user password. Enter that, and then you'll be at root's command line. Then type in "passwd" (no quotes) and you'll be prompted for a password. Enter a different password than what your user password is. You'll be asked to enter the same password again. When you've done that, root has its own password. Make sure you remember what it is, or you could well be buggered if you forget it. :)

---

### Post by Triblaze on 2012-02-25
There's a lot to learn, but you pick it up.

Personally, these are probably the two most helpful commands for new users:
man
apropos

Man is short for manual. If you find a command you don't know, type "man [command]", and it'll give you the manual page for that command. Hit q to exit the man page.

Apropos is kind of like a search function. Type "apropos [keyword]", and it'll give you all the commands that deal with that keyword.

You can use these two to help you find your way around. Other than that, the links posted are good.

---

### Post by Lars Noodén on 2012-02-25
Here are some resources on learning your way around the shell:

[http://ubuntuforums.org/showthread.php?t=1909108](http://ubuntuforums.org/showthread.php?t=1909108)

If you think about it as shell script programming rather than a "command" line then it is easier to learn.  What you have before you is a full interpreter which can be programmed.  Even if you are just writing a one-line program, it is still programming!

---

### Post by mcduck on 2012-02-25
> **scheibenlosen said:**
> Like the other person said, there is no default root password. What I do after a fresh Ubuntu install is to open a terminal, and then type "sudo -s" (no quotes). It'll ask for your user password. Enter that, and then you'll be at root's command line. Then type in "passwd" (no quotes) and you'll be prompted for a password. Enter a different password than what your user password is. You'll be asked to enter the same password again. When you've done that, root has its own password. Make sure you remember what it is, or you could well be buggered if you forget it. :)

Couple of things to notice here...

First, you should use "sudo -i" instead of "sudo -s" or "sudo su", as only "sudo -i" loads root's environment variables correctly. The other two commands can result in unexpected problems since you end using your normal user's environment but with root's permissions.
(read [this post]("http://ubuntuforums.org/showpost.php?p=6188826&postcount=4") for more details)


..and second, while you are free to enable the root account if you want to (not that you'd actually need it for anything), it's not actually advised to give instructions for doing that in these forums (simply because it's not necessary for anything, and because helping people is a lot easier if they are following Ubuntu's security model instead of using root account).

---

### Post by oldos2er on 2012-02-25
Thread moved to Other OS/Distro Talk.

---

### Post by Version Dependency on 2012-02-25
Might take a look at this [website]("http://playterm.org/") for learning the command line.

---

