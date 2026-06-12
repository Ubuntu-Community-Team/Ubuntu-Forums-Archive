---
title: "Planeshift install"
date: 2007-07-02
forum: Absolute Beginner Talk
---

### Post by Istonian on 2007-07-02
I downloaded planeshift. It is a .bin file and I don't know how to install it.

---

### Post by Outrunner on 2007-07-02
```
/path/to/planeshift.bin
```

---

### Post by Istonian on 2007-07-02
when I did that is said bash: /path/to/planeshift.bin: No such file or directory

---

### Post by RomeReactor on 2007-07-02
Hi. Where did you save that file? If I had saved it in my desktop, I would do (from the terminal):
```
cd /home/romereactor/Desktop
```
and then:
```
./file.bin
```
Make sure you replace **file.bin** with the exact name of the planeshift file.

---

### Post by Outrunner on 2007-07-02
> **Istonian said:**
> when I did that is said bash: /path/to/planeshift.bin: No such file or directory

You have to replace that code with the actual path and filename of the .bin. Say the .bin is on your Desktop:

```
~/Desktop/filename.bin
```

---

### Post by Istonian on 2007-07-02
The file is on my desktop, but none of these are working.

---

### Post by RomeReactor on 2007-07-02
You could try making it executable (though I don't think it's necessary). Just remember that you **must** be on the desktop in your terminal:
```
sudo chmod +x PlaneShift_CBV0.3.018.bin
```
and then:
```
./PlaneShift_CBV0.3.018.bin
```

---

### Post by Istonian on 2007-07-02
the file is named ps.bin

---

### Post by Outrunner on 2007-07-02
OK... How this?
```

~/Desktop/ps.bin
```

---

### Post by Istonian on 2007-07-02
it keeps saying the file does not exist, but im looking at it on the desktop

---

### Post by RomeReactor on 2007-07-02
Did you try changing to the desktop directory from the terminal before trying to install? Sometimes installation commands only accept absolute paths (e.g., full path to the file), instead of relative.

---

### Post by Istonian on 2007-07-02
Yes I did. Still nothing.

---

### Post by RomeReactor on 2007-07-02
Try moving the file to your home folder, open a terminal and run:
```
./ps.bin
```
If that doesn't work, try:
```
sh ps.bin
```
Or perhaps try downloading the file from the [official site]("http://www.planeshift.it/download.html#linux")
and when it downloads, move it to your home folder, and:
```
./PlaneShift_CBV0.3.018.bin
```
or:
```
sh ./PlaneShift_CBV0.3.018.bin
```
I'm not too sure if **sh** works for **bin** files, but I seem to remember so.

---

### Post by ub_one on 2007-07-03
I had trouble opening a .bin file as well. Making it an executable solved the problem.
Thanks RomeReactor !

---

### Post by skeeterflea on 2007-07-25
No worky for me either....

user@ubuntuhom:~/Desktop$ ls
GWENDungeonPreview.wmv  PlaneShift_CBV0.3.019-x64.bin  QkCam  Video_1.wmv
user@ubuntuhom:~/Desktop$ sudo chmod +x PlaneShift_CBV0.3.019-x64.bin
Password:
user@ubuntuhom:~/Desktop$ ./PlaneShift_CBV0.3.019-x64.bin
bash: ./PlaneShift_CBV0.3.019-x64.bin: cannot execute binary file
user@ubuntuhom:~/Desktop$

---

### Post by ScottC2105 on 2007-07-25
I am new to Ubuntu and I managed to install it. I downloaded the latest client (PlaneShift_CBV0.3.019-x86.bin) to my desktop. Then I ran the following commands:

```
cd ./Desktop
```

```
sudo chmod +x PlaneShift_CBV0.3.019-x86.bin
```

```
sudo ./PlaneShift_CBV0.3.019-x86.bin
```

The setup wizard then came on screen and it installed and works a treat.

I hope this helps you :).

---

### Post by skeeterflea on 2007-07-26
Thanks , a note to any others that may make the mistake I did... make sure you downloaded the correct bit version for your system.
 :redface:

---

### Post by papuccino1 on 2007-12-11
Every time i try to open the game.
*Applications > Other > PlaneShift Client*
I get an error saying i don't have permission to open that file.

[IMG]http://i6.tinypic.com/7wsja8o.png[/IMG]

Does anyone know how to fix this.
When I installed the game it clicked on next the hole installation, the game installed in "opt" directory.

---

### Post by TechDragon on 2008-02-10
I am having the denied problem that the guy above me has.  Any helps?

---

### Post by dtgolder on 2008-03-08
This game is a pain to install...I had to put a symbolic link in my home directory to make it work

ln -s /opt ./opt


Also--depending on how you do the install, you may have to add yourself to the "games" group...

---

### Post by Shadowmeph on 2008-03-08
> **papuccino1 said:**
> Every time i try to open the game.
*Applications > Other > PlaneShift Client*
I get an error saying i don't have permission to open that file.

[IMG]http://i6.tinypic.com/7wsja8o.png[/IMG]

Does anyone know how to fix this.
When I installed the game it clicked on next the hole installation, the game installed in "opt" directory.

you forgot the 777 command ( I think thats the command)  permission if you havew an irc client go to freenode and the channel is Planeshift ( yes thats the correct spelling of the PlanetSHift irc) they can help you

---

### Post by indefinicy on 2008-03-19
I had a friend help me install the program through the root@ terminal, and now i can't figure out how to open any of the updater, setup or client [as well as uninstaller. i don't want to uninstall it yet, however i know that would not work if i tried] and it's now telling me "There was an error launching application: Details: Failed to execute child process "/opt/PlaneShift/pssetup" (Permission denied)" 

I am very very new to linux and I just want to understand more about to so as to be able to solve these problems myself. What he heck is opt, for one, and why is permission denied? First it told me when trying to install that the /opt was unwritable by user, however i am the only user and the only account on this. i am using ubuntu 7.10 and i just don't understand!  could somebody please explain to me how what the general problem is and how i can fix this?

i am online always, please send me a message if you can actually help me and feel up to it.

[aim : indefinicy .. yim: indefinite_creation]

---

### Post by unclejac on 2008-04-04
> **dtgolder said:**
> This game is a pain to install...I had to put a symbolic link in my home directory to make it work

ln -s /opt ./opt


Also--depending on how you do the install, you may have to add yourself to the "games" group...

Hi dtgolder! 

I agree, not straight forward. Managed to install it. 

Shorcuts on my desktop now, though the icons dont appear to work.

Click on them and nothing happens /much scratching of head now :(

What do you mean a "symbolic link" ? what did you do to cure it?

---

