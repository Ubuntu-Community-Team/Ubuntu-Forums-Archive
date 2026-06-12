---
title: "A few questions"
date: 2005-09-03
forum: Absolute Beginner Talk
---

### Post by Edrihan on 2005-09-03
I recently switched from Windows XP to Ubuntu and I'm finding the switch very refreshing except for a few snags.

1. The whole admin password thing is confusing because the password I gave during the installation doesn't work. Sometimes in the terminal when it asks me for a pasword the keyboard ceases to work.

2. I don't know what the difference (or usage) of admin and sudo are.

3. Where should I install things (C:/Program Files equivilent) if I want something for my user/all users.

I think once I understand these things I'll be better equipped to deal my *ahem* few other problems.

---

### Post by brk3 on 2005-09-03
These are kind of funny questions, but il try to answer best i can! To be honest I would suggest you spend just a little time reading other forum posts/docs about sudo on ubuntu.

1. The password you gave during installation should work. Just remember its your own user password you give. And make sure your entering it correctly - the keyboard doesnt stop working! It just doesnt show up what your typing, for security sake.(its the same as stars showing up on most password dialogs) also make sure your caps lock isnt on. unlike windows, linux is case sensitive.

2. Admin is admin :) sudo is the program used to gain admin('root' in linux terms) privlages. To run a program or command with root privs, you would type sudo <command>

3. /usr/bin. but you dont/shouldnt have to worry about this. Programs default installation will make them available to all accounts/users.

Hope that helps, keep using ubuntu :)

---

### Post by weasel fierce on 2005-09-03
Sudo is basically a short cut to Admin / root status, for a limited amount of time.

Basically, instead of logging in separately as root, you just enter the command with sudo, for the purpose of whatever task you are doing, then it expires a few minutes later.

---

### Post by az on 2005-09-03
". The whole admin password thing is confusing because the password I gave during the installation doesn't work. Sometimes in the terminal when it asks me for a pasword the keyboard ceases to work."

There is no reason why the password you assigned your user at installation time is not working.  It is not because of some intricate sudo/su/administer made thing.  There should only be one password for you to use on your system.  Either you made a typo or you have a hardware failure or something.

If you need to change your password, boot into recovery mode (press ESC at boot time, if you do not know what I mean) and type

passwd (yourusername) (yournewpassword)

and then
init 2 
to continue to boot into regular mode.  


"I don't know what the difference (or usage) of admin and sudo are."

Are you running Ubuntu or Kubuntu?  


" Where should I install things (C:/Program Files equivilent) if I want something for my user/all users."

Linux makes use of shared libraries in a much different way than Windows.  The answer to your question would be either /bin /sbin /usr/bin or /usr/sbin, but there are also libraries.  The package manager takes care of that, so you do not have to worry about it.

To list the files in a package, look in synaptic or, from the comand line
dpkg -L (package)


"I think once I understand these things I'll be better equipped to deal my *ahem* few other problems."

Take your best shot!  There are no dumb questions!

---

### Post by Edrihan on 2005-09-04
Kubuntu is KDE Ubuntu, correct? I'm using Ubuntu. The sudo password is the same as the root password, right?

---

### Post by az on 2005-09-04
[QUOTE=Edrihan]Kubuntu is KDE Ubuntu, correct? I'm using Ubuntu. The sudo password is the same as the root password, right?[/QUOTE]

I was asking about Kubuntu because KDE has an "administrator mode"  That is irrelevant.

The sudo command is litterally "superuser do", meaning "do this command as superuser, since I am on the soduers list".  Sudo will then ask you for your password to make sure you are you.

---

### Post by xequence on 2005-09-04
When you say the keyboard ceases to work... You mean when you do sudo and it asks you for your password? It is working, its just it doesent show your password OR the * stuff. I think it is more secure. You just have to type it without seeing it.

---

### Post by Edrihan on 2005-09-04
Ok. Got that. Is there a way to check if your sudo powers are working? I'm also having trouble installing tarballs. When I try to compile it in the terminal with make, the terminal can't find the gcc. Where can I configure that? I'm going to have a few more questions after, but I'd like to get a handle on this. This switch to Linux is becoming daunting!

---

### Post by az on 2005-09-04
[QUOTE=Edrihan]Ok. Got that. Is there a way to check if your sudo powers are working? I'm also having trouble installing tarballs. When I try to compile it in the terminal with make, the terminal can't find the gcc. Where can I configure that? I'm going to have a few more questions after, but I'd like to get a handle on this. This switch to Linux is becoming daunting![/QUOTE]

Try 
sudo tail /etc/sudoers


You should not be able to read that file without root priviledges.


What do you need to install by tarball?  Most of the time (I am serious) you just need to enable a repository (use synaptic)- it is probably already in Ubuntu.

If you want to compile something you need to install the build-essential package (again, use synaptic).  Yo uwill also need the headers to whatever library you are compiling with (like the linux-headers if you are compileing a kernel module or libgtk2.0-dev if you want to compile something with gtk...)  What libraries you need are listed in the ReadMe in the tarball, usually.

---

### Post by Edrihan on 2005-09-04
Okay, I read that file and it basically says ALL a bunch of times so I think I'm good. Heh, what is a repository?

---

### Post by az on 2005-09-04
You install software from a repository.  Run synaptic.

---

### Post by jameswilhelm on 2005-09-04
Have a look at:

[https://wiki.ubuntu.com/Repositories?highlight=%28repositories%29](https://wiki.ubuntu.com/Repositories?highlight=%28repositories%29)

There is a LOT of information on wiki.ubuntu.com.

Happy hunting/learning :-)

And just saw the wiki link in azz's post - oh, well.

---

