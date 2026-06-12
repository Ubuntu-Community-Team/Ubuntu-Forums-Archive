---
title: "Installing Enemy Territory"
date: 2006-07-28
forum: Absolute Beginner Talk
---

### Post by WPAStrangla on 2006-07-28
I am a beginner to Ubuntu and am really enjoying it so far, but I have some problems installing Wolfenstein Enemy Territory. I downloaded the Linux version but where do I go from there?

---

### Post by benuski on 2006-07-28
> **WPAStrangla said:**
> I am a beginner to Ubuntu and am really enjoying it so far, but I have some problems installing Wolfenstein Enemy Territory. I downloaded the Linux version but where do I go from there?

What format is the file that you downloaded in?  And by that, I mean the file extension

---

### Post by WPAStrangla on 2006-07-28
The file is a .run

Full Name: et-linux-2.55.x86.run

---

### Post by Koookie monster on 2006-07-29
As far as I know, like this:

1) open up a terminal window
2) go to the directory where you downloaded the file, probably like this: "cd Desktop"
3) make the file executable: chmod u+x et-linux-2.55.x86.run
4a) to install for all users write "sudo ./et-linux-2.55.x86.run". You will be asked your password and then an installer will appear.
4b) or if you want to install it to your home directory, drop out the "sudo" part.

The "./" part means that it executes a file in the current directory. That is why it is necessary, to avoid confusion with commands (like dir, ls, ...).

Hope this helps -- see you at the battlefields, arr! ;)

[edit: added step 3]

---

### Post by justas1 on 2006-08-08
And i have this problem. I try write to terminal chmod u+x et-linux-2.55.x86.run but it dosnt work (write: NO SUCH FILE OR DIRECTORY). How can i start ET?

---

### Post by justas1 on 2006-08-08
Help

---

### Post by carverj on 2006-08-08
Sorry, but did you type sudo before chmod?
Did you make sure you changed to the correct directory first?
ie, cd /*path to .run file*
Hope this helps, I am jealous you can run this game, and a friend told me that games can be utilized extremely well if run in Linux !!?

---

### Post by GoldBuggie on 2006-08-08
I would do step 3 with "./"

```
sudo chmod +x **./**et-linux-2.55.x86.run
```

---

### Post by WPAStrangla on 2006-08-08
I get this error

> su: Authentication failure
Sorry.
/home/shawn/.setup6895: error while loading shared libraries: libgtk-1.2.so.0: cannot open shared object file: No such file or directory
./setup.sh: line 143:  6919 Segmentation fault      "$setup" "$@" 2>>$NULL
The setup program seems to have failed on x86/glibc-2.1

See [http://zerowing.idsoftware.com/linux/](http://zerowing.idsoftware.com/linux/) for troubleshooting

---

### Post by flaak_monkey on 2006-08-12
after installing screen is blank....

---

### Post by Perfect Storm on 2006-08-12
> **WPAStrangla said:**
> I get this error

Install libgtk1.2

```
sudo apt-get install libgtk1.2
```

---

### Post by Perfect Storm on 2006-08-12
> **justas1 said:**
> And i have this problem. I try write to terminal chmod u+x et-linux-2.55.x86.run but it dosnt work (write: NO SUCH FILE OR DIRECTORY). How can i start ET?

Make sure that the script is in the right place where you running the command. If it's on you Desktop;

```
cd Desktop
```

or

```
cd && cd Desktop
```

other;

```
cd /to/the/location
```

Then run the other commands afterwards.

---

### Post by flaak_monkey on 2006-08-12
i got sound but no video.....

---

### Post by TooDamFast on 2006-08-12
Ive noticed that people tend to get overly complicated when it comes to .run files.  Im a total linux noob but if you left click on the file click on properties and change the permision to allow exicute.  then just double click the file it runs.  to noobs the command line stuff my get tricky.  what kind of system are you using, (video card, ram, cpu)?  This game rocks (with the total combat elite mod).  have you installed the newest video drivers?

---

### Post by carverj on 2006-08-14
> Ive noticed that people tend to get overly complicated when it comes to .run files. Im a total linux noob but if you left click on the file click on properties and change the permision to allow exicute. then just double click the file it runs. to noobs the command line stuff my get tricky.

Huh, there you go. I have honestly never done it successfully the easy way before, but now I have.
The amount of times I have gotten stuck making, configuring, etc.

---

### Post by meborc on 2006-08-14
just a tip - ET should be 2.60 (latest) and not 2.55 ... you can find update files on the net though if you have installed the 2.55 version...

the game absolutely rocks... it runs so well on my NV geforce 2 mx 32MB sh***y card i couldn't believe my eyes when i first tried it... it is way better then CS in my oppinion...

---

### Post by TooDamFast on 2006-08-15
if you like Cs you may want to install the TC:elite mod.  
[http://truecombat.com/intro.php](http://truecombat.com/intro.php)
feels better than CS to me.  and less arcade feeling that ET.

---

### Post by jrjr on 2006-08-15
.

---

