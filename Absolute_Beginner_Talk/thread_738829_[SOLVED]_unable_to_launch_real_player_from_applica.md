---
title: "[SOLVED] unable to launch real player from applicatons menu."
date: 2008-03-29
forum: Absolute Beginner Talk
---

### Post by bhadotia on 2008-03-29
i recently installed real player . it worked fine for a day but now I'm unable to launch it from the applications menu , the following message is coming :

            Failed to execute child process "realplay" (Permission denied)

 NEED HELP.:confused::confused::confused:

---

### Post by pbpersson on 2008-03-29
quite often if you attempt a command from the console it will give you more information

When I get into a console (terminal) session and just type the word realplay on my machine it starts up realplayer.

Does yours work the same way?

---

### Post by bhadotia on 2008-03-29
when i typed the command he following message came:

```
Command 'realplay' is available in '/usr/bin/realplay'
bash: realplay: command not found

```

don't know what that means:confused::confused::confused:
I'm more confused.

---

### Post by pbpersson on 2008-03-29
I looked in my /usr/bin and in that directory is a link that points to a shell script called realplay

Hey.....when you installed RealPlayer were you logged on as yourself?  You did not run the install as root, did you?

I discovered my actual shell script is located in /home/phil/RealPlayer/realplay

---

### Post by bhadotia on 2008-03-29
I actually don't exactly know how to install the player . i had problems installing it , so i took help from the forum . i did not know where to install ;it somebody told me to put it in /usr/bin/realplay ; so thats what i did. if you say i can reinstall it in some other place.

---

### Post by pbpersson on 2008-03-29
Okay....if you know where you installed it then you should be able to run the shell script manually to see if it works.

On my machine, I typed:

cd /home/phil/RealPlayer/RealPlayer

to get to the location where the application is installed.  Then to run it I typed:

./realplay

and that launched the application.  Keep in mind that in Linux, everything is case sensitive.  Therefore, RealPlayer is totally different than realplayer

When I am in the directory and do an ls -l command, these are the files I see:

phil@Phil-Kubuntu:~/RealPlayer/RealPlayer$ ls -l
total 652
drwxr-sr-x 2 root root   4096 2008-01-06 13:47 Bin
drwxr-sr-x 2 root root   4096 2007-07-26 17:29 codecs
drwxr-sr-x 2 root root   4096 2007-07-26 17:29 common
drwxr-sr-x 2 root root   4096 2007-07-26 17:29 doc
-rw-r--r-- 1 root root  25129 2008-01-06 13:47 install.log
drwxr-sr-x 2 root root   4096 2007-07-26 17:30 lib
-rwxr-xr-x 1 root root  11286 2007-07-26 17:29 LICENSE
drwxr-sr-x 2 root root   4096 2007-07-26 17:29 mozilla
drwxr-sr-x 2 root root   4096 2007-07-26 17:30 plugins
drwxr-sr-x 2 root root   4096 2007-07-26 17:29 postinst
-rw-r--r-- 1 root root   3072 2007-07-26 17:29 README
-rwxr-xr-x 1 root root   2492 2008-01-06 13:47 realplay
-rwxr-xr-x 1 root root   2486 2008-01-06 13:47 realplay.bak
-rwxr-xr-x 1 root root 570344 2007-07-26 17:30 realplay.bin
drwxr-sr-x 7 root root   4096 2008-03-29 00:03 share

---

### Post by kushykush on 2008-04-04
I tried all the above and my Real Player is not launching from Desktop. It installed properly as I can now play it inside Firefox.  When first installed Real Player opened up.  Now nothing happens when the icon is clicked.

Very annoying.  Can some one help?

---

### Post by bhadotia on 2008-06-22
I've got it : I installed realplayer without being root . 

Thanks guys.

---

