---
title: "Crippled Ubuntu Install"
date: 2006-08-23
forum: Absolute Beginner Talk
---

### Post by selfmade on 2006-08-23
I just installed Ubuntu 5.10 on a partition to dual-boot with windows. when i log on, it notifies me of updates. if i click on the link, it asks for my password, but then nothing else happens. synaptic wont open. i used the automatic automatix install and it doesnt work. add programs wont open. apt-get update wont work. when i try to edit the sources.list, it won't open. i know i created the apt-get directory during install, so i don't know why this is happening. do i have to reinstall?

---

### Post by wpshooter on 2006-08-23
May I ask you why you are installing 5.10 when Dapper Drake 6.06.1 is available ?

---

### Post by selfmade on 2006-08-23
i had the cd for 5.10. its also what had been installed on here before. a friend of mine built and set up this computer for me, and as a kind of learning experience he gave me the cd and told me to figure it out. i know that he had installed it previously and that it worked. i just cant figure out what i did wrong or how to fix it. besides, i saw the madness on the forums yesterday about uopgrades breaking x. thats scary.

---

### Post by TrendyDark on 2006-08-23
If you have a spare CD laying around, I'd suggest installing the latest version of Ubuntu. It is much better than 5.10, plus the installation is a lot easier to understand.

---

### Post by selfmade on 2006-08-23
actually i dont have a cd burner (i know, ::gasp::). im also stubborn...this should work.

---

### Post by wpshooter on 2006-08-23
Download and burn the DESKTOP version of Dapper Drake 6.06.1 and install on your hard drive once you get booted up to the desktop.  Make sure you check the intergrity of the CD by using the sum check function on the initial boot screen menu.

If it was me I would use a WIPING program to get rid of everything completely from the drive before installing the new version of Ubuntu, that is assuming there is nothing on it that you need or that you need to backup.

---

### Post by TrendyDark on 2006-08-23
> **selfmade said:**
> actually i dont have a cd burner (i know, ::gasp::). im also stubborn...this should work.

Oh wow. . . haha.

Well, it sounds kind of like something with your root account is messed up.

You are entering the root password when you're trying to enter synaptic correct?

---

### Post by selfmade on 2006-08-23
i actually used the same password for root as for the user account specifically so i wouldnt screw it up.
and apt commands arent tel;ling me the password is wrong. it just doesnt do anything.

---

### Post by selfmade on 2006-08-23
i reinstalled ubuntu, same thing. check sources.list, its empty. i had to chek it manually b/c i could not open it in the terminal. also it is read-only and i cant get it to let me edit properly. i must be the only person with any computer knowledge who can kill apt by accident.

---

### Post by Tomosaur on 2006-08-23
To open a read-only file, you need to open it using sudo. You also will not be able to see the contents of the file in a text editor unless you use sudo.

---

### Post by selfmade on 2006-08-23
wont open with sudo gedit /etc/apt/sources.list

which says to me that the problem is .root.

i guess that means i need to reinstall and do smg diff with the partitions. could someone give me a hand on how to set this up properly?

---

### Post by steve.horsley on 2006-08-23
So what does it say when you do **sudo gedit /etc/apt/sources.list**?

If it says nothing and just returns to the command line, that's tricky - try this: **sudo nano /etc/apt/sources.list**

That's gotta say something!

---

### Post by selfmade on 2006-08-23
sudo nano /etc/apt/sources.list   asks for pw, then nothing

---

### Post by steve.horsley on 2006-08-24
Weird. Can you try these two and see what happens?
[B]grep admin /etc/group
sudo pwd[/B]

Is your username listed by the first command? If not, you need to add yourself to the admin group somehow - use recovery mode and then the command (assuming your username is selfmade):
**adduser selfmade admin**

---

### Post by selfmade on 2006-08-24
megan@ubuntu:~$ grep admin /etc/group
lpadmin:x:104:megan
megan@ubuntu:~$ sudo pwd
Password:
megan@ubuntu:~$

---

