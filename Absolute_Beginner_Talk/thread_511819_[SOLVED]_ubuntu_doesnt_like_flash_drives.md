---
title: "[SOLVED] ubuntu doesnt like flash drives"
date: 2007-07-28
forum: Absolute Beginner Talk
---

### Post by plr4ever on 2007-07-28
hello

i just installed fiesty on 2 different computers, a laptop (mine)and desktop (cousins). before i installed ubuntu, i backed up files from my laptop to the desktop w/ a 2 gb flash drive. this is when i discovered the annoying as sin ,trash folder on the flash drive. when i tried wiping the flash drive on the ubuntu desktop, it said 
error while deleting
blah/blah/blah cannot be deleted becuase you do not have permission to modify its parent folder

:confused:

well i was still excited about putting ubuntu on my laptop, so i just deleted the folder in on the windows. well now i have ubuntu on the laptop, and when i tried putting the files back on the laptop, i cannot use the flash drive becuase i cannot delete the files taking up 1.7 gb of space.


What is this? i understand ubuntu is more secure than windows by limiting my rights to manage certain files, but this is insane. i need to use my flash drive, and it wont give me permission to modify _**my own files!!!!!!!**_ i dont know what it is, but i just want to be able to use the flash drive. i never thought i could say windows was superior to ubuntu, but in this it is. 


why is ubuntu so hard with so many things? i thought i would love it, and i did until i started getting knee deep in this impossible to use OS. I hope it gets better, i dont want to have to go back to windows.

---

### Post by Happy_Man on 2007-07-28
Well.... yes...... Ubuntu does prevent you from deleting the trash. It is easier to just do that in Windows. No idea why, though.

---

### Post by Hallvor on 2007-07-28
Try typing 

> sudo chmod 777 /media/usbdisk

.. if that is where your flash drive is mounted.

Ubuntu is so "hard" because it is secure. Everything is locked down by default to make a secure OS. If Ubuntu gets insecure, it is because the user made it insecure. As far as I can remember, Windows XP runs as administrator by default and I actually had to activate the firewall! Two different philosophies.

---

### Post by Jimmyfj on 2007-07-28
First of all the files on your flash drive are probably NFTS file system. Therefore you need to install, and activate NFTS read/write tools on your Ubuntu. Those tools are in the repos.

---

### Post by Pragmatist on 2007-07-28
I understand your frustration.  You are not alone.  You are, however, overreacting and panicking.  Most problems are solvable, you just have to know how to solve them.  That is why we are here :)  Remember:  Just because something is new and unfamiliar to you, does not make it inferior to something that is familiar to you.  You already know how to use Windows.  To learn something new, like Linux, requires time and trouble.  Some people come to Linux with the expectation that it will work better than windows and they won't have to learn a thing to get it to work.  That is not true.   There is a learning curve.  Now, let's see about your problem...

Did you try usingthe** sudo **command?  You can remove files using the **rm** command prefixed with the ** sudo **command.  BEFORE TYPING WHAT FOLLOWS, MAKE SURE YOU REALLY WANT TO DELETE THE FILES AND THAT YOU'VE CAREFULLY TYPED THE COMMAND.

Say you want to delete a directory called "Trash" that is located on your flash drive, and your flash drive is mounted at /media/flash  We will assume the Trash folder is at: **/media/flash/Trash** You would open a terminal and type:
> sudo rm -r -f /media/flash/Trash
rm is the remove command, -r tells the command to remove "recursively" which means it will remove everything from that point forward including all subdirectories.  Without the -r it will at most remove all the files in a single directory.  The -f switch tells rm to remove by "force"  This just means that rm won't prompt you to confirm each delete.  Now you can see why this combination -r and -f  can be deadly.  If you mistype it you can delete everything on your hard drive!  For example, if you typed "rm -rf /media/flash" you would remove everything on your flash drive. This is why they call this "the resume command" because if you use it, you could end up having to rewrite your resume and look for a new job!  SO BE CAREFUL!!!
(Note:  I use the above command all the time, I am just very careful with it--like handling a knife in the kitchen--useful, but dangerous if your careless)

---

### Post by plr4ever on 2007-07-28
> **Pragmatist said:**
> I understand your frustration.  You are not alone.  You are, however, overreacting and panicking.  Most problems are solvable, you just have to know how to solve them.  That is why we are here :)  Remember:  Just because something is new and unfamiliar to you, does not make it inferior to something that is familiar to you.  You already know how to use Windows.  To learn something new, like Linux, requires time and trouble.  Some people come to Linux with the expectation that it will work better than windows and they won't have to learn a thing to get it to work.  That is not true.   There is a learning curve.  Now, let's see about your problem...

Thanks pragmatist, it wasnt linux i was really frustrated at, it was that i spent 30 minutes finding out how to post this question before i found the solution. I am just used to windows and knowing it top-down. I didnt expect things like this to be difficult as they are. plus it takes me 2 minutes of typing sudo pon/poff dsl-provider just to use the internet!!!! well i guess there are somethings that software this new cant do as easily as a multibillion dollar 20 y/o software company can. well i still love linux, no matter how much some simple things arent simple to do. 



THanks:guitar::KS

---

### Post by Pragmatist on 2007-07-28
> **plr4ever said:**
> well i guess there are somethings that software this new cant do as easily as a multibillion dollar 20 y/o software company can....

First, Linux is a direct descendant of Unix.  Unix is MUCH older than windows.  MS came out with windows/386 in the 1985, running on top of lame DOS.  3.1, the first halfway decent version of Windows, didn't come out until 1992 and it was a piece of crap compared to the multi-user Unix which had been around since the 60's.  Windows didn't become multiuser until Windows NT which didn't come out until 1993!  Look at the server market, and you'll see that serious businesses run their web servers on Linux.  Linux servers account for about 90% of the whole server market, so anytime you are surfing on the net the odds are very strong that you are receiving information from a Linux box!

Second, you are making the classic mistake:  You think that, because your having trouble with Linux, and your not having trouble with Windows, Linux must be inferior.  Let's see, how do I answer something this obvious. I have no real trouble with Linux and thousands of others also have little to no trouble.  Why would you think that your individual experience would provide conclusive evidence that Linux is inferior to Windows?  Now if you said, "I run Windows with success, and I have not yet been able to run Linux with success" that would make more sense.

---

### Post by ugm6hr on 2007-07-28
> **Happy_Man said:**
> Well.... yes...... Ubuntu does prevent you from deleting the trash. It is easier to just do that in Windows. No idea why, though.

That's interesting. 

Xubuntu7.04 doesn't behave like that at all.  Right-click trashcan->Empty trash, then press return to confirm.  Deleted (presumably forever).

Presumably, the other way would be to cut and paste from USB to HD - then delete from HD.

---

### Post by Vague on 2007-07-28
> **plr4ever said:**
> well i guess there are somethings that software this new cant do as easily as a multibillion dollar 20 y/o software company can.

Get viruses?  (Sorry, I had to).

Anyway, as has already been pointed out, Linux itself is almost 16 years old.  It's not exactly new.

---

### Post by kelvin spratt on 2007-07-28
your internet should load at startup if set up correctly, and you must unmount flash drives that also applies in windows, in Linux  the flash drive or any external memory will write protect itself if not unmouted to protect its self as i found out when i first used Linux i was lucky if i left it mounted and restarted the machine it gave me read/ write so i reformatted it ok since

---

