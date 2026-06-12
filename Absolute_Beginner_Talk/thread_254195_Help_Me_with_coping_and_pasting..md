---
title: "Help Me with coping and pasting."
date: 2006-09-09
forum: Absolute Beginner Talk
---

### Post by Jimit87 on 2006-09-09
1) i have two folders on my desktop.
2) one is called etpro and other one is called ETH 1.0.0 (deleted abcd and got this one)
3) i want to copy few files to a free game i downloaded and installed.
4) The game directory is as follow, ** /usr/local/games/enenmy-territory/[/SIZE]**
5) i want to copy the WHOLE etpro folder from my desktop to my game directory.
6) i want to copy two files from my eth 1.0.0 folder from my desktop to my game directory, those two files are called, libETH.so and run.sh.
7) HOW DO I COPY AND PASTE those files from my desktop to my game directory?
8) i try to drag and drop (move) those files from my desktop to my game directoy but it game me the following messege.
"Error while copying to "/usr/local/g...y-territory".
You do not have permissions to write to this folder."
i am logged into administrator account (there is only one account on my ubuntu)
9) please reply to my #7. i am sure i have to use a program called terminal but don't know what commands and all.

Thank you.

---

### Post by croak77 on 2006-09-09
Open a terminal and use the mv command
```
cd abcd
sudo mv  libman.so run.sh /usr/local/games/enenmy-territory/
```

Or use nautilus the GNOME file manager  with gksudo nautilus and just open the destination and drag the folder/file to where you want.

You need to be root cause a user doesn't not have the proper permissions.

---

### Post by PPAAUULL on 2006-09-09
You created the folder in a root access area only you have to copy it using the terminal or open an file explorer with root. do you know how to do that?

---

### Post by Jimit87 on 2006-09-09
First of all, thank you both for your reply. 2nd let me make my first post little bit clear and then reply me with exact commands i need to use to copy and paste files to my game folder.

---

### Post by bodhi.zazen on 2006-09-09
> **Jimit87 said:**
> Ok i have two folders on my desktop that i downloaded from a web.

one is called etpro
and other is called, abcd

k now,

i want to copy that whole ETPRO folder from desktop to a game i downloaded, called wolfenstein enemy territory. 

**[SIZE="4"]i have my wolfenstein in following folder, /usr/local/games/enenmy-territory/[/SIZE]**

HOW DO I COPY AND PASTE THAT FOLDER FROM DESKTOP TO THAT wolf. FOLDER?

AND, i have to copy two files from abcd folder to that game directory as well and they are called, libman.so and run.sh 8)

HOW DO I COPY THAT PASTE THOSE TWO FILES FROM MY ABCD FOLDER TO MY WOLFENSTEIN ENENMY TERRITORY FOLDER?


i tried moving it from desktop to that enemy terr. folder, (by dragging it into that folder) but i get following error mess.


"Error while copying to "/usr/local/g...y-territory".
You do not have permissions to write to this folder."
i am logged into administrator account (there is only one account on my ubuntu)


LOL. 

To COPY
```
sudo cp -r /home/user_name/Desktop/etpro /usr/local/games/enenmy-territory
sudo cp /home/user_name/Desktop/abcd/libman.so /usr/local/games/enenmy-territory
sudo cp /home/user_name/Desktop/abcd/run.sh /usr/local/games/enenmy-territory
sudo chmod 777 /usr/local/games/enenmy-territory/run.sh
```

The last line (chmod) will prevent your next questions (run.sh will give you a permission error unless you make it executable, thus chmod ....)

You can delete abcd and etpro from deskto if you wish.

---

### Post by Jimit87 on 2006-09-09
> **PPAAUULL said:**
> You created the folder in a root access area only you have to copy it using the terminal or open an file explorer with root. do you know how to do that?

No i don't. but i think what you and croak77's 2nd option are saying is much easier, so can u tell me how to do that?

Thank you.

---

### Post by aysiu on 2006-09-09
Open the explorer with root:

Press Alt-F2 and then type the following command

**Ubuntu**: ```
gksudo nautilus
``` **Kubuntu**: ```
kdesu konqueror
``` **Xubuntu**: ```
gksudo thunar
```

---

### Post by Jimit87 on 2006-09-09
> **bodhi.zazen said:**
> LOL. 

To COPY
```
sudo cp -r /home/user_name/Desktop/etpro /usr/local/games/enenmy-territory
sudo cp /home/user_name/Desktop/abcd/libman.so /usr/local/games/enenmy-territory
sudo cp /home/user_name/Desktop/abcd/run.sh /usr/local/games/enenmy-territory
sudo chmod 777 /usr/local/games/enenmy-territory/run.sh
```

The last line (chmod) will prevent your next questions (run.sh will give you a permission error unless you make it executable, thus chmod ....)

You can delete abcd and etpro from deskto if you wish.

i think what you are saying is working but when i tried to copy etpro, it opened a new enenmy-territory folder in my game directory with etpro fiesl in it. now i have two enenmy-territory folders.
i am suppose to have a folder called "etpro" in my original enenmy-territory folder. 

and btw, how do i delet the new created enemy-territory folder? i don't see send to trash option when i right click. 

lol. 
can u look at my first edited post and now reaply with exact command? i changed some files soo. 

thank you.

---

### Post by croak77 on 2006-09-09
Open a teminal and type;
```
gksudo nautilus
```

It will ask for your password. You are now running nautilus as root which means you have permission to write to /usr. Just drag the folder/file to the destination. But I already said this.

---

### Post by Jimit87 on 2006-09-09
yaya. guys. i did it with your help.
i copied and pasted all my fiesl into my enenmy-territory directory.

one more question though.

how do i run the run.sh file? my game suppose to start by running that file.

Thank you and god bless you all.

:)

---

### Post by Jimit87 on 2006-09-09
> **croak77 said:**
> Open a teminal and type;
```
gksudo nautilus
```

It will ask for your password. You are now running nautilus as root which means you have permission to write to /usr. Just drag the folder/file to the destination. But I already said this.

it didn't ask me any password, but it opend my desktop folder and then i was able to copy and paste the needed files to my game directory by dragging them and copy > paste them.

aysiu: thank you.

---

### Post by Jimit87 on 2006-09-09
Ok, now you just have to help me with the post #10 question. 

Thank you.

---

### Post by bodhi.zazen on 2006-09-09
1. to run the line see my first post re making it executable (chmod 777 ....)

[I told you you would be asking this........] :-\"

2. Then run from a terminal, are you using wine?

If so: wine /usr/local/games/enenmy-territory/run.sh

Else: sh /usr/local/games/enenmy-territory/run.sh

If this works, edit /home/user/.bashrc and add a line
```
alias enemy='sh /usr/local/games/enenmy-territory/run.sh'
```
or alias enemy='wine /usr/local/games/enenmy-territory/run.sh' as the case may be.


Close (exit) the terminal, open an new terminal.

You should now be able to run the game by typing enemy in the terminal.

You can also make a launcher or shortcut.

---

### Post by Jimit87 on 2006-09-09
> **bodhi.zazen said:**
> 1. to run the line see my first post re making it executable (chmod 777 ....)

[I told you you would be asking this........] :-\"

2. Then run from a terminal, are you using wine?

If so: wine /usr/local/games/enenmy-territory/run.sh

Else: sh /usr/local/games/enenmy-territory/run.sh

If this works, edit /home/user/.bashrc and add a line
```
alias enemy='sh /usr/local/games/enenmy-territory/run.sh'
```
or alias enemy='wine /usr/local/games/enenmy-territory/run.sh' as the case may be.


Close (exit) the terminal, open an new terminal.

You should now be able to run the game by typing enemy in the terminal.

You can also make a launcher or shortcut.

ok so when i put in sudo chmod 777 /usr/local/games/enenmy-territory/run.sh
i get the following error mess.
 "chmod: cannot access `/usr/local/games/enenmy-territory/run.sh': No such file or directory" 

i do have it in my directory i see it so whats wrong?

---

### Post by bodhi.zazen on 2006-09-09
You mentioned two folders (directories) previously.

Delete the one you do not need (gksudo nautilus)

I hope you did not delete the wrong one....

---

### Post by Jimit87 on 2006-09-09
> **bodhi.zazen said:**
> You mentioned two folders (directories) previously.

Delete the one you do not need (gksudo nautilus)

I hope you did not delete the wrong one....

oh i found out what the problem was, i copied your cmd and you porbably typed real fast and wrote enenmy wrong. 

Ok so i ahev libETH.so and run.sh in my game directory
eth.pk3 in .etwolf directory.

how do i run the game? on the home page it says "./run.sh" but obviously it doesn't work for me.

what am i doing wrong?

when i put "chmod 777 /usr/local/games/enemy-territory/run.sh" in terminal i get nothing then i put in
"sh /usr/local/games/enemy-territory/run.sh"

and i get "/usr/local/games/enemy-territory/run.sh: line 9: ./et.x86: No such file or directory"

what am i doing wrong?

Thank you.

---

### Post by bodhi.zazen on 2006-09-09
sorry for the typo. :redface:

First, it is normal to see no output with chmod 777 /usr/local/games/enemy-territory/run.sh.

run.sh is now running, we have a different error message to contend with now. Making progress.

It looks like you are missing a file "et.x86".

Are you running Linux native or under wine? I assume Linux since you used the sh ....

Can you find "ext.x86" anywhere? Home folder? elsewhere? if so we can do a link.

Try running:
```
cd /usr/local/games/enemy-territory/
sh ./run-sh
```

---

### Post by Jimit87 on 2006-09-09
k nvm, after rebooting, i clicked on run.sh and it started the game. unfort. when i got connected to server, the next second it closes and brings me back to my desktop. :(

any one know what to do to solve this problem?

---

### Post by bodhi.zazen on 2006-09-09
LOL.... :lol:

so it's working? =D>

Could be a firewall problem. See if the site has a FAQ. At this point I suggest you start a new thread as it is unlikely anyone is going to respond with an answer as this thread is "Help Me with coping and pasting" and we are several pages in.

Best of luck.

---

### Post by Jimit87 on 2006-09-09
k i have files in its places now. but when i click on run.sh and start it via terminal, game starts, i see servers, then i join one and boom next second, my game diappears, the terminal diapperas and i am back on my desktop. why?

---

### Post by bodhi.zazen on 2006-09-09
> **Jimit87 said:**
> k i have files in its places now. but when i click on run.sh and start it via terminal, game starts, i see servers, then i join one and boom next second, my game diappears, the terminal diapperas and i am back on my desktop. why?

If you start in a terminal you should get error messages when you crash, no.

What are those error messages? -> google search or post error messages.

---

### Post by ins0mniac on 2007-05-10
> k i have files in its places now. but when i click on run.sh and start it via terminal, game starts, i see servers, then i join one and boom next second, my game diappears, the terminal diapperas and i am back on my desktop. why?

oh I dont know, at I guess I would suggest it's because you're lame enough to cheat in a free online game?

---

