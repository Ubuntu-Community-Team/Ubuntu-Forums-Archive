---
title: "lost my home :("
date: 2007-06-19
forum: Absolute Beginner Talk
---

### Post by loop_001 on 2007-06-19
ok heres what i did

i was testing something and instead of logging out i decided to do that new login :D, but i used the same username and password

then it went black, so i pressed reset as i couldnt get into ttyl console when it booted back in it went to login fine, and i tried logging but it said my /home/user *user being me was gone

so then i when ttyl 1 and logged in and went sudo mkdir /home/user and then tried logging in still it failed :D

does this mean i lost all my work in my orginal home dir, if so how to i get back in and if not how do i get back in and get my work back.

thanks

---

### Post by Skrynesaver on 2007-06-19
When you login from the tty what directory are you in?
Was this directory not here already?

Switching to a new user who is yourself is just another login, it should have no effect on the home directory itself

---

### Post by Golyadkin on 2007-06-19
Try this command to see what home directories there are:
> 
sudo ls -la /home/


---

### Post by loop_001 on 2007-06-19
when i login via tty it had no probs but when i try via gdm it gives me an error saying that there is no /home/user dir and would i like to use /root's or something and i click ok or something and it just errors again and takes me back to gdm

ill try that in a sec Golyadkin

---

### Post by loop_001 on 2007-06-19
when i do that command i get 2 things

drwxr-xr-x   2 root root 4096 2007-06-19 22:46 .
drwxr-xr-x 21 root root 4096 2007-06-11 14:50 ..

---

### Post by Golyadkin on 2007-06-19
Ai, that means there is no homedir.

Give this a shot:
> 
sudo mkdir /home/loop
sudo chown -R loop:loop /home/loop


Replace "loop" with your username.

---

### Post by loop_001 on 2007-06-19
ok i just made my own /home/user dir and chowned it

but now that im in where is my orginal home directory any ideas??, there is nothing in my /home at all all my work etc is gone i have pretty much started fresh

so sad :(

---

### Post by bigboy_pdb on 2007-06-19
If you installed linux so that the home directory was on a separate partition (I've always done this so I don't know about using one partition, but it wouldn't hurt to try this either way) then type 'mount' in a terminal (to open the terminal go to 'Applications' -> 'Accessories' -> 'Terminal') to see if the partition with the '/home' directory is listed and mounted.  If you see other partitions listed as being mounted as '/usr', '/var', '/tmp', and '/' then it would appear that your home directory somehow became unmounted.

Did you restart Ubuntu after your problem occurred?

---

### Post by loop_001 on 2007-06-19
this is how it happened -
1. Applications>System Tools>New Login
2. Login as Current user that executed 1.
3. Black Screen (tty not accessible)
4. Reboot Computer
5. GDM as normal
6. Try Login
7. Error Prompt - no home dir, would you like to use root
8. OK error not Writable crash back to GDM
9. tty1
10. Login as user, using root dir
11. ls /home/ - no resaults
12. ls -la /home
drwxr-xr-x 2 root root 4096 2007-06-19 22:46 .
drwxr-xr-x 21 root root 4096 2007-06-11 14:50 ..
13. sudo mkdir /home/user
14. sudo chown -R user /home/user
15. Logout tty1
16. Back to GDM
17. Login as user - no error prompts
18. Login as though fresh install clean home, fresh setting files etc

But there was nothing from my original home, so I have lost all my work and everything.

Does anyone know where it could of possibly gone or why this happened??

Thankyou, in advance
Back tomorrow

---

### Post by loop_001 on 2007-06-19
hey you know what that is what happened for some reason it unmounted itself, it  is there now how to i mount it back so it is set as my home dir again

---

### Post by Skrynesaver on 2007-06-19
your fstab should have an entry for the home directory (/etc/fstab)
If not add the following
/dev/<device home is on>  /home ext2 defaults 1 2
to the file as root and save it.

---

### Post by atria on 2007-06-19
Open /etc/fstab with a text editor and look for your /home entry. Mount it manually using the "mount" command.

I'm not exactly sure why your /home directory isn't mounted automatically though. You might want to post your system logs here ;)

---

### Post by bigboy_pdb on 2007-06-19
If you are using an ext3 filesytem, replace ext2 with ext3 (in the line that Skrynesaver told you to add to the fstab file). If you don't remember whether or not it is ext2 or ext3 it would most likely be the same type of file system as that used for your other partitions that have been mounted.

---

### Post by loop_001 on 2007-06-19
woops now i stuffed it, now the home dir has my / files system in it for some reason

i think tomorrow ill just try and fix it with the live cd :D at least i know what i did now, i cant believe it unmounted oh well i know what to do now to fix it and it will be away tomorrow no probs, ill post back if it fails again but i dont think so :D anyway thx for the help

cya

---

