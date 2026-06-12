---
title: "[SOLVED] Can't make a new folder in my Home folder"
date: 2007-09-13
forum: Absolute Beginner Talk
---

### Post by TaoBoogie on 2007-09-13
Hello
I have just tried to make a folder in my "home" folder but the "make new folder" is greyed out. When I looked at the "home" folder properties under the Permissions tab I find the message "You are not the owner, so you can't change these permissions"
This disturbs me as I am the owner, how has this happened and how can I change it so Ubuntu sees me as the owner.
Thanks for your help.

---

### Post by llamakc on 2007-09-13
Because you are not the owner. Somewhere, at some time you did something. Either you moved stuff around from a previous install, tried installing software and followed some terminal commands, etc...

Do this:

Open a terminal and type:

cd /home

ls -l

and cut/paste the output.

Next, type:

cd ~

ls -l

and cut/paste the output.

---

### Post by TaoBoogie on 2007-09-13
Thank you llamakc
Here are the results:

tao@tao-laptop:~$ cd /home
tao@tao-laptop:/home$ 
tao@tao-laptop:/home$ ls -l
total 4
drwxr-xr-x 42 tao tao 4096 2007-09-13 23:09 tao
tao@tao-laptop:/home$ 


tao@tao-laptop:/home$ cd ~
tao@tao-laptop:~$ 
tao@tao-laptop:~$ ls -l
total 60
-rw-r--r-- 1 tao tao 20097 2007-09-12 21:09 CD-ROM.odt
drwx------ 3 tao tao  4096 2004-06-11 19:39 Debian
drwxr-xr-x 3 tao tao  4096 2007-09-13 23:12 Desktop
lrwxrwxrwx 1 tao tao    26 2004-06-11 14:48 Examples -> /usr/share/example-content
-rw-r--r-- 1 tao tao 12252 2007-09-13 01:01 handy hints.odt
-rw-r--r-- 1 tao tao 16370 2007-09-12 19:15 installation problems.odt
drwxr-xr-x 2 tao tao  4096 2007-09-13 22:51 utorrent
tao@tao-laptop:~$

I have had some problems with this install, I wonder if this is the reason.

---

### Post by alienexplorers on 2007-09-13
GO to your Tao Directory and do a ls -l

---

### Post by smah77 on 2007-09-13
Try :
```
cd /home
chown -R tao
```
in the terminal.

---

### Post by TaoBoogie on 2007-09-13
do you mean like this;
> tao@tao-laptop:~$ ls-l
bash: ls-l: command not found
tao@tao-laptop:~$ 

Or do I need to change directory within the terminal? I'm not sure how to do that I know I type "cd"
Please excuse my ignorance I am new to this. All I can seem to do is this:

> tao@tao-laptop:~$ ls-l
bash: ls-l: command not found
tao@tao-laptop:~$ cd: tao
bash: cd:: command not found
tao@tao-laptop:~$ cd tao
bash: cd: tao: No such file or directory
tao@tao-laptop:~$ 


---

### Post by smah77 on 2007-09-13
Oops!  That should be:
```
cd /home
chown -R tao:tao tao
```

---

### Post by TaoBoogie on 2007-09-13
ok I am here now:

> tao@tao-laptop:~$ cd /home
tao@tao-laptop:/home$ chown -R tao:tao tao
tao@tao-laptop:/home$ 

---

### Post by smah77 on 2007-09-13
> **TaoBoogie said:**
> ok I am here now:

You should be able to make new folders now.  Give it a try.

---

### Post by TaoBoogie on 2007-09-13
No sorry I get the same result as before. I can make a new folder in my tao directoty but noit in my home directory. have I missed an instruction?

---

### Post by llamakc on 2007-09-13
/home/tao IS YOUR home directory. /home is the parent directory of /home/tao and you as a user should NOT be making directories there unless you know what you are doing.

What was your reasoning for doing so? Maybe we can help you with an alternative.

---

### Post by bodhi.zazen on 2007-09-13
Your home directory is /home/tao

/home is owned by root and holds the home directories of all users (except root which is /root)

Try this in a terminal :

echo $HOME

---

### Post by TaoBoogie on 2007-09-13
The last instruction gave this result:

> tao@tao-laptop:~$ echo $HOME
/home/tao
tao@tao-laptop:~$ 

The reason for me doing this was I was following the instructions [here]("http://news.softpedia.com/news/uTorrent-under-Ubuntu-in-3-Easy-Steps-49037.shtml") to try to install utorrent in ubuntu.
Then it went all horribly wrong. Well actually when I completed the instructions and clicked on the uTorrent icon I made on the desk top I got the message; 
> There was an error launching the application...Details: Failed to execute child process "/home/tao/utorrent/utorrent.exe (Permission denied)
I installed Wine as per the instructions on the page I linked to.
btw thanks a million for the pactient help.

---

### Post by Tyke91 on 2007-09-13
LOL!

/home/tao is your home directory silly

/home is owned by root. you can only create new folders there by changing yourself to root using ```
sudo
``` or by creating a user

EDIT: D'oh... didn't read the second page.

in the future, please name your files completely. 

/home is the directory owned by root that contains YOUR home folder

/home/tao is commonly reffered to as YOUR home folder... we thought you couldn't edit this.



and the reason why you don't own all your directories is simple... if you did, you would be able to unwittingly comprimize your system with a click of a button... not only that, but any viruses you download (there are maybe 40 for linux... if you get one, shame on you) will be able to destroy your entire computer... it's one of the reasons why windows is so unsecure :D all of the important files on a linux system are owned by a user called root. you can become root for a short time by typing the prefix "sudo" before a command and typing root's password.

---

### Post by llamakc on 2007-09-13
Those instructions fail to tell you to create the folder:

mkdir /home/tao/utorrent

Did you do that on your own?

---

### Post by llamakc on 2007-09-13
> **Tyke91 said:**
>  you can become root for a short time by typing the prefix "sudo" before a command and typing root's password.

WRONG.

One who is in the sudoers file in /etc/sudoers can execute commands as root by typing "sudo name-of-command" and entering their USER PASSWORD.

---

### Post by TaoBoogie on 2007-09-13
Well I now understand that there is a "Home" folder. and *my* home folder is /home/tao/
Still I made a folder in my "tao" folder called "utorrent" as I originally thought of that as my "home" folder. then when the programme did not work when I clicked on the icon I made for the programme on my desktop, I thought they must have meant create the utorrent folder in the "Home" folder. Hence the misunderstanding.
In the instructions on the page I linked to it did say;
> Now create a folder called utorrent in your home directory, then download the latest version (Standalone, NOT the installer) of the uTorrent application from Softpedia and place it in the folder you've just created.
Which I did do. SO the file structure goes "/home/tao/utorrent/utorrent.exe"
So I don't really know where I went wrong with the (utorrent) installation, and to tell the truth, I am a bit wary of trying again. If I do will it harm ubuntu going through those steps again?
Well at least I've learned something more about Ubuntu's file system.
I now know that there is a Utorrent package already in the "add/remove programmes" but I do not know how it is started. 
Practice practice Tao old chap I guess.

---

### Post by bodhi.zazen on 2007-09-13
:lolflag:

sudo -i

to become root

sudo <command> executes a single command as root.

Users in the admin group have "full access" to sudo.

visudo allows you to safely edit /etc/sudoers and you can allow a user or group either full or limited access to sudo. Limited access = restricted number of commands.

---

### Post by TaoBoogie on 2007-09-13
*Sigh* I have such a lot to learn. I am a mere tadpole in the Ubuntu ocean. :)
Thank you all for guiding me through the home/not Home debacle I still don't know why the utorrent is not working but that is for another day when I'll try again, perhaps. I'm just so wary that I may try to install/un-install something especially through the terminal, that will wreck my Ubuntu.
Ah well, nobody promised me a rose garden.
[IMG]http://tao.serveit.org/ubuntu/ubuntao.jpg[/IMG]

---

### Post by Tyke91 on 2007-09-13
> **llamakc said:**
> WRONG.

One who is in the sudoers file in /etc/sudoers can execute commands as root by typing "sudo name-of-command" and entering their USER PASSWORD.





ooof. embarrasing :P

i guess i just couldn't tell the difference as i set my root password to be the same as my own. (only one user on my system... me)

---

