---
title: "Permission denied on .bin and .run files"
date: 2006-09-18
forum: Absolute Beginner Talk
---

### Post by theshiznoz on 2006-09-18
I wonder if anyone can help a semi-noob :roll: 
I am using Dapper Drake,
I don't seem to be able to run anything in the terminal without having a permission denied error.  I have changed the permissions to have full read,write and execute on each file that i have the problem with, but it makes no difference.  I am also using the sudo command.

Here is a list of what happens when I try to run Jedi Outcast install script in the terminal :

> areid@anthony-desktop:~$ sudo sh jedi.outcast_1.04-multilanguage-2.run
Verifying archive integrity... All good.
Uncompressing Star Wars Jedi Knight II: Jedi Outcast 1.04-multilanguage Installe r.......................................................
./setup.sh: line 207: /home/areid/.setup20840: Permission denied
areid@anthony-desktop:~$


And here when I try to run Nexuiz 3D Deathmatch Game:

> areid@anthony-desktop:~/My Downloads/games/Nexuiz$ sudo sh nexuiz-linux-glx.sh
Password:
nexuiz-linux-glx.sh: line 14: /home/areid/My Downloads/games/Nexuiz/nexuiz-linux-686 -glx: Permission denied
nexuiz-linux-glx.sh: line 14: /home/areid/My Downloads/games/Nexuiz/nexuiz-linux-686 -glx: Success
areid@anthony-desktop:~/My Downloads/games/Nexuiz$

This is happening on everything that I try to run.
Can anyone please shed some light on this for me because it's starting to get me down.
I have only been using Ubuntu for a couple of weeks. I have been a Suse user for 8 years. but I don't have a clue whats going on here though!:( 
And I don't want to go back to Suse !!![COLOR="Red"][/COLOR]

---

### Post by saintj0n on 2006-11-02
I think this will help....
Go to terminal, then type: sudo
password:******
cd /directory_with_file
chmod 755 'filename' (without the quotes)
sh 'filename'

Good luck!

---

### Post by HokeyFry on 2006-11-23
open a terminal, cd to the directory the file is in and type

```

sudo chmod a+x filename.bin

```

then type in ./filename.bin


i dont know if this will work for a .run file but for a .bin file ive done it several times, i know it works

---

### Post by Fenrirwulf on 2008-01-18
Thank the Lords of Kobol! I was beginning to think the Frakking Cylons had stuck a virus on my machine...ROFL! :)

---

