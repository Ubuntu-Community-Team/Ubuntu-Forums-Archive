---
title: "how do i install pspvc? install.sh"
date: 2007-02-11
forum: Absolute Beginner Talk
---

### Post by Ceta on 2007-02-11
How do I install pspvc? It is an archive file I guess. the file is calll install.sh.  Can someone tell me what steps I take to begin installation please?

---

### Post by orlox on 2007-02-11
won't it work to jus execute it from a terminal??

just go to the directory the file is, and do:

```
./install.sh
```

---

### Post by Ceta on 2007-02-11
Well, I just saved it on the desktop then extracted it to the desktop. I double clicked the install.sh and selected to run in terminal, some stuff wizzed by on the screen then the terminal closed.  I cant find pspvc anywhere, so i guess it didnt work.

---

### Post by Ceta on 2007-02-12
I tried installing from source with the instructions at this website: [http://www.psychocats.net/ubuntu/installingsoftware](http://www.psychocats.net/ubuntu/installingsoftware) but I get the follow error after saving the tar file on my desktop and typing tar -xvzf pspvc-install-0.2.1.tar.gz in the terminal



rain@the-cube:~$ tar -xvzf pspvc-install-0.2.1.tar.gz
tar: pspvc-install-0.2.1.tar.gz: Cannot open: No such file or directory
tar: Error is not recoverable: exiting now
tar: Child returned status 2
tar: Error exit delayed from previous errors

---

### Post by jimrockford on 2007-03-06
I'm new to Linux and sure appreciate step by step instructions when I get stuck.  Since I haven't been able to find any while trying to install pspvc, I figured I'd roll my own.  I managed to successfully install it by piecing together bits from a bunch of posts.  Let's see if we can put it all together in one place.

This worked for me in Ubuntu Edgy.  Hopefully, it'll work for you.

[INDENT]1. Download pspvc from here: [http://pspvc.sourceforge.net/]("http://pspvc.sourceforge.net/"), saving it to your desktop.

2. Double click the pspvc tar.gz file on your desktop.

3. Press "Extract", ensure "Desktop" is listed as the location to extract the files, and then press the "Extract" button (again).

4. You should now have a pspvc-install-0.2.1 folder on your desktop.

5. Open Terminal or Konsole (whichever you have installed).

6. Install dependencies using this command: 
```
sudo apt-get install libgtk2.0-dev libfaac-dev libxvidcore4-dev nasm build-essential
```
7. Several development libraries that pspvc requires will install.  You'll see a bunch of output and it'll take a few seconds to complete.

8. Next, enter the following command, replacing *user* with your user name.  This will change the prompt to the pspvc installation directory. ```
cd /home/user/Desktop/pspvc-install-0.2.1
```
9. To begin the pspvc install, enter this command: ```
sudo ./install.sh
```
10. When the install completes, you should see a message that says "PSPVC installation completed".  You're done!

11. Enter *pspvc* at the prompt to start the application.[/INDENT]

Is it any good?  I don't know.  I just got it to work.  I guess it's time to play with it.

Good luck!

---

### Post by pdrift on 2007-04-27
dude, you are the mother effin man. i followed your instructions ans it worked.
i been tryin for 2 days and finally its workin.

i used your instructions and it worked for me on feisty

i had this program on edgy and it works very wonderfully
especially if your on a higher firmware on your psp
or custom firmware like me. thank you!!!!!

---

### Post by diss on 2007-05-12
tanks for the HOW TO worked for me too on feisty :D

---

### Post by hawi on 2007-06-25
Hi, i found this thread via google when i have not been registered. 

And i even did to say BIG BIG BIG THANKS @jimrockford !!!!!!!!! The other Google-results have been in french and and i don't speak this language as good as english. Thank you again for your perfect installation instruction, jim!

Greets from Germany Dusseldorf
HaWi

---

### Post by gigaferz on 2007-08-19
ive been looking for 2 weeks now, seems that it will work, is encoding right now, thank you!!

---

### Post by illbashu on 2007-11-06
i am getting this error... 
make: yasm: Command not found
make: *** [common/amd64/dct-a.o] Error 127
-e \E[01;31mERROR during compilation or installation of X264

can someone plz help :/

---

### Post by AmBerTyK on 2008-02-17
@jimrockford

man u really rock!! thnx for yo instructions.. works like magic.. =)

---

### Post by jav on 2008-02-25
illbashu:
Try "sudo apt-get install yasm"

---

### Post by illbashu on 2008-03-04
^thx now i am getting this

```
ERROR: XviD not found
If you think configure made a mistake, make sure you are using the latest
version from SVN.  If the latest version fails, report the problem to the
ffmpeg-devel@mplayerhq.hu mailing list or IRC #ffmpeg on irc.freenode.net.
Include the log file "config.err" produced by configure as this will help
solving the problem.
-e \E[01;31mERROR during configure FFMPEG

```

---

### Post by Technomouse on 2008-05-13
Thanks dude !

I have quoted you on my LJ 

technomouse.livejournal.com

Hope thats ok?

---

