---
title: "Password Issues"
date: 2006-03-22
forum: Absolute Beginner Talk
---

### Post by Paul Bennett on 2006-03-22
Hello.

I am a new Ubuntu user and im trying to configure my dial up connection ising pppconfig in the terminal.

I type 
```
sudo pppconfig
```

it asks for my password

I enter my user password, hit enter and nothing happnes. No launch, no error, just goes to the next line. I type 

```
sudo pppconfig
``` 

again, and this time nothing happens at all. 


This may be unrelated, but the same kind of thing happens when I try to lauch password protected items form the appications menues. 

I try to run network config, or add programs.

It prompts for a password

I enter my user password

The box gies away, and nothing happens. No launch, no error,

Im kinda lost. Any Ideas?

Your time is much appreciated.

Pau.

---

### Post by Sef on 2006-03-22
Have you tried System > Administration > Networking to set up your dial up?  Much easier that way.

---

### Post by Mustard on 2006-03-22
[QUOTE=Paul Bennett]


It prompts for a password

I enter my user password

The box gies away, and nothing happens. No launch, no error,

Im kinda lost. Any Ideas?

Your time is much appreciated.

Pau.[/QUOTE]

I would be curious if you have installed using the 'Expert' install option in the installer.  If you have then the first user account is not set up with superuser privileges, as is the case with the default install method.  If you can confirm this then I can give you some idea how to proceed.  Basically I think you don't have an entry in your /etc/sudoers file for your current user, if the above situation is the case, and you would need to use the visudo command from a root prompt to edit the sudoers file.  I can give full instructions for that.

---

### Post by caffinide on 2006-03-22
you are still running it as yourself. I have done this enough times at school, I know this by heart. you can't do this from your normal user account... unless I am mistaken...

---

### Post by Paul Bennett on 2006-03-22
I didnt go for expert install. Just the standard. The only user account created was the one during/after the install.

How should I go about making my account "Superuser"? (if its not?) How can I tell if it is??

Thanks.

---

### Post by caffinide on 2006-03-22
you can tell because it has # at the end of the prompt ( from experiance) and root in its name. but its got root in it also, but im unfortunently on a windows machine and am too lazy to switch

---

### Post by caffinide on 2006-03-22
oh sorry, double post

---

### Post by Mustard on 2006-03-22
[QUOTE=Paul Bennett]I didnt go for expert install. Just the standard. The only user account created was the one during/after the install.

How should I go about making my account "Superuser"? (if its not?) How can I tell if it is??

Thanks.[/QUOTE]

Ok, here is a test to see if you have superuser privileges already.

Type this in terminal

```
sudo whoami
```

This is what it shows on my terminal...

```
mustard@slave:~$ sudo whoami
Password:
root
mustard@slave:~$

```

---

### Post by Paul Bennett on 2006-03-23
[QUOTE=Mustard]Ok, here is a test to see if you have superuser privileges already.

Type this in terminal

```
sudo whoami
```

This is what it shows on my terminal...

```
mustard@slave:~$ sudo whoami
Password:
root
mustard@slave:~$

```[/QUOTE]

[QUOTE=Mustard]I would be curious if you have installed using the 'Expert' install option in the installer.  If you have then the first user account is not set up with superuser privileges, as is the case with the default install method.  If you can confirm this then I can give you some idea how to proceed.  Basically I think you don't have an entry in your /etc/sudoers file for your current user, if the above situation is the case, and you would need to use the visudo command from a root prompt to edit the sudoers file.  I can give full instructions for that.[/QUOTE]

Ok, thanks. I did
```
sudo whoami
```

I typed the password.

Nothing happens. Just goes to the next line

I will say this. My apssword is all numbers. Does this matter?

---

### Post by Mustard on 2006-03-23
I'm a bit confused by the above answer.  Are you saying you did install with expert install or are you saying you did the command?

-edit-

I think you should have a look at this post I did in another thread anyway and inspect your /etc/sudoers file.  It certainly seems like your sudoers file is mucked up.

[http://www.ubuntuforums.org/showpost.php?p=646267&postcount=10](http://www.ubuntuforums.org/showpost.php?p=646267&postcount=10)

---

### Post by Paul Bennett on 2006-03-24
No. _I did not do expert install._. Thanks for the link. Ill look it over :)

Any more ideas?

---

### Post by xenmax on 2006-03-24
Try this thread.
[http://ubuntuforums.org/showthread.php?t=146859](http://ubuntuforums.org/showthread.php?t=146859)

---

### Post by Paul Bennett on 2006-03-24
Ok. Thanks. I definaly thinkg that I need to edit my sudoers file. However, how do I edit it?

How do I log on as root and open it? I cant log on from the login screen, becase of some permission error.

Thanks.

---

### Post by Mustard on 2006-03-24
[QUOTE=Paul Bennett]Ok. Thanks. I definaly thinkg that I need to edit my sudoers file. However, how do I edit it?

How do I log on as root and open it? I cant log on from the login screen, becase of some permission error.

Thanks.[/QUOTE]

The thread link I posted earlier tells you how to do this.  Perhaps you would like to read it again. :)

Use the grub menu to boot up in 'Recovery Mode', this will drop you to a root prompt.  From there you can use the visudo command to edit your /etc/sudeors file.

---

### Post by Paul Bennett on 2006-03-24
Ok. Please excuse my ignorance, but I'm not quite sure what this "grub" menu of which you speak is.

EDIT: A little googleing told me what is is, but how do i get to it?

---

### Post by Mustard on 2006-03-24
[QUOTE=Paul Bennett]Ok. Please excuse my ignorance, but I'm not quite sure what this "grub" menu of which you speak is.[/QUOTE]

That's ok.  I like easy questions. :)

When you boot up your computer, it goes through the BIOS stuff on your screen and then you are presented with a menu which has your choices for booting up Ubuntu.  Usually there are options for booting the kernel (it might be labeled Breezy Badger in your situation), then there is usually an option for 'Recovery Mode', then an option for 'Memtest'.  You want to choose the 'Recovery Mode' option.

If you don't see these, its possible that your grub menu has been set to be hidden, in which case you would need to press the ESC key to see it, just after the BIOS screen finishes.

---

### Post by BBD on 2006-03-25
I have the same problem!. Every time when I type the user`s password it seems that it accepts it but nothing appears. 
I have tryed everything and I have still the problem :(

---

### Post by xenmax on 2006-03-25
@Paul Bennett: If you did not do an expert install, plz follow Mustard's instructions like he said.

@BBD: Again, look at codejunkie's post in the thread i posted - follow his instructions. try his part1 if performed did an expert installation, else try part2

---

### Post by Paul Bennett on 2006-03-25
**Thank you very much.**

My problems are resolved! (the ones I was having with my computer anyway)

---

### Post by ds[de] on 2006-03-25
[QUOTE=Paul Bennett]**Thank you very much.**

My problems are resolved! (the ones I was having with my computer anyway)[/QUOTE]

Congrats :)

But it would be nice to know what exactly the problem was and how you solved it, so that other users who use the search function and find this thread can use the same solution as you.

Regards,
ds[de]

---

