---
title: "[SOLVED] /Home/.dmrc not recognized"
date: 2007-09-18
forum: Absolute Beginner Talk
---

### Post by jmeyer on 2007-09-18
[SIZE="3"]When I logon to my Windows domain it gives me an error about the /Home/.dmrc not being recognized and the file should be owned and 644 permissions.  i have tried that and it then gives and error about your session only lasting 10 seconds and /.gnome2 directory not created Permission denied.  I have tried the other threads that have the same issue, but for some reason the solutions don't work.  

my home dir is: /home/DOMAIN/username.  i have done chmod 644 to this as well as to /home/DOMAIN/username/.dmrc.  i also did chown to this directory.  

when i do this it still says the session was only open for 10 seconds.  

I want to login to our network and be able to see my favorites and documents on my ubuntu machine.  right now all i can do is login, it doesn't save anything back to the windows server.

Please help[/SIZE]

---

### Post by jamvegan on 2007-09-18
Don't know about your first problem, but the session lasting less than 10 seconds and inability to create .gnome2 are the result of you chmoding your home directory to 644.  Doing so removed the execute permission, and when a directory does not have execute permission, you cannot access it or anything below it in the directory structure.  755 are the appropriate permissions for your home directory (and it should be owned by you, though /home should be owned by root).

---

### Post by Dr Small on 2007-09-18
[http://ubuntuforums.org/showthread.php?t=535555&highlight=.dmrc](http://ubuntuforums.org/showthread.php?t=535555&highlight=.dmrc)

---

### Post by jmeyer on 2007-09-21
[SIZE="3"]That did not help, Sorry.  I tried to make the /home chmod 755 and my directory 644.  I gave me an error that my session only lasted 10 seconds and will not let me go into Ubuntu.  

I use /home/NST as my home directory for my network domain.  then my login into our network jmeyer.  i am trying to pull documents from our windows domain into /home/NST/jmeyer.[/SIZE]

---

### Post by jamvegan on 2007-09-21
Apologies if I'm not understanding what you're saying, but any directory that you set to 644 will be unusable, as will anything in it.  If I am understanding you and the current permissions on /home/NST/ and/or home/NST/jmeyer and/or /home/jmeyer (if such exists) are 644, they need to be changed to 755.  The thread that Dr Small linked never said to change any directory to 644, only the .dmrc file.

---

### Post by jmeyer on 2007-09-24
[SIZE="2"]Hello,

I tried to change the /home dir and /home/NST dir to 755 and the .dmrc file to 644.  it did not work.  does the .dmrc file need to be in /home or can it reside in /home/NST?? 

When I tried to copy it, it said omitting directory .dmrc and then it didn't copy.  
I used:
> 
sudo cp .dmrc /home 

when i was in the /home/NST directory[/SIZE]

---

### Post by bodhi.zazen on 2007-09-24
.dmrc needs to be in /home/NST

Try this :

> 	sudo chmod 644 .dmrc
	sudo chown user_name .dmrc
	sudo chmod 755 /home/user_name
	sudo chown -R user_name /home/user_name

	OR, if that fails:

> 	sudo chown -R user_name /home/user_name 
	sudo chmod 755 /home/user_name
	sudo rm -rf /home/user_name/.dmrc

Where  user_name = your log-in name :p

---

### Post by jmeyer on 2007-09-25
[SIZE="2"]Thanks Bodhi

The second option worked and I am no longer getting the .dmrc not recognized error.  Now i just need to know where and how this saves back to my network profile.  I will open another post for that issue unless you have some thoughts. [/SIZE]

---

