---
title: "HELP!!! i think i messed something up"
date: 2007-04-10
forum: Absolute Beginner Talk
---

### Post by metalfanatic07 on 2007-04-10
i am trying to install the right java to get frostwire to work without automatically shutting down and now synoptic won't work... this is what i get....

E: Malformed line 22 in source list /etc/apt/sources.list (dist)
E: The list of sources could not be read.
Go to the repository dialog to correct the problem.

i have no idea what i did or how to fix it, all i know is there is now that won't work and update manager won't either.

---

### Post by Vladimirm on 2007-04-10
Ok, open up a terminal and type the following

sudo gedit /etc/apt/sources.list

Scroll down to the 22nd line (i assume this is something you added to install java)
and either comment it out, or delete the line.
Synaptic should run then.

---

### Post by mac.ryan on 2007-04-10
No panic, it can be easily fixed.

Open a terminal and type:
```
sudo cp /etc/apt/sources.list /etc/apt/sources.list.bkup
sudo nano /etc/apt/sources.list
```

The first line makes a copy of the file you are going to edit, the second line gets you editing it.

Then go on the 22nd line of the file and comment it, adding at its very beginning 

```
##
```

Save (CTRL-X, then answer the questions) re-run synaptics... and it should work.

Explanation: while trying to install Java, you probably had to add a "repository" from where to retrieve the packages, and that line was poorly formatted for ubuntu.

The above procedure should reverse the situation.

If you wish you can post here the content of your sources.list, and somebody might find out what is wrong with it...

Best luck!

---

### Post by LaurelLynn on 2007-04-10
Dear metalfanatic07,

From a terminal please type:

$ cat  /etc/apt/sources.list

Then hightlight the output,  right-click the mouse and select Copy.

Back at your browser post the contents back to me, so that I can see what line 22 says.

---

### Post by metalfanatic07 on 2007-04-10
this is what line 22 says... 
deb [http://www.java.com/en/download/linux_manual.jsp](http://www.java.com/en/download/linux_manual.jsp)

---

### Post by mac.ryan on 2007-04-10
> **metalfanatic07 said:**
> this is what line 22 says... 
deb [http://www.java.com/en/download/linux_manual.jsp](http://www.java.com/en/download/linux_manual.jsp)

That is indeed a webpage, and not a direcotory from which you can download packages...

Could you tell us what how-to you are following? That way we might understand better and help you out... :)

---

### Post by metalfanatic07 on 2007-04-10
[http://ubuntuforums.org/showthread.php?t=305337&highlight=frostwire+install](http://ubuntuforums.org/showthread.php?t=305337&highlight=frostwire+install)

I tried deleting the line, synoptic still didn't work

---

### Post by mac.ryan on 2007-04-10
> **metalfanatic07 said:**
> [http://ubuntuforums.org/showthread.php?t=305337&highlight=frostwire+install](http://ubuntuforums.org/showthread.php?t=305337&highlight=frostwire+install)

I assume you got troubles at step #3... did you managed to get the file .bin on your desktop?

> I tried deleting the line, synoptic still didn't work

Did you save the file before to exit nano (or gedit)? And did you restarted synaptics? Please follow LaurelLynn instructions above and post here the content of your file. It sounds very strange deleting that line didn't change anything...

---

### Post by LaurelLynn on 2007-04-10
Years of programming experience has taught me that where it says the problem is, and where things started to go wrong are often completely different.

That was the reason I asked to see the whole file.

---

### Post by metalfanatic07 on 2007-04-10
That is the whole source list and now line 24 is a problem. 


## Major bug fix updates produced after the final release of the
## distribution.

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.

deb [http://www.java.com/en/download/linux_manual.jsp](http://www.java.com/en/download/linux_manual.jsp)

deb [http://java.sun.com/j2se/1.4.2/download.html](http://java.sun.com/j2se/1.4.2/download.html)
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) dapper main restricted universe multiverse
deb [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) dapper-security main restricted universe multiverse
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) dapper-updates main restricted universe multiverse
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse
deb [http://wine.budgetdedicated.com/apt/sources.list.d/dapper.list](http://wine.budgetdedicated.com/apt/sources.list.d/dapper.list) -O /etc/apt/sources.list.d/winehq.list


and yes i did get that file onto my desktop.

---

### Post by LaurelLynn on 2007-04-10
Try and comment out the first two entries with a ¨#¨ they appear to be webpages, not repositories.

---

### Post by metalfanatic07 on 2007-04-10
[QUOTE=mac.ryan;2433004]I assume you got troubles at step #3... did you managed to get the file .bin on your desktop?



i can't get past step 3, i get a wierd error...
mike@Mike:~$ sudo mkdir /usr/java
mkdir: cannot create directory `/usr/java': File exists
and... 
mike@Mike:~$ sudo cp jre-1_5_0_11-linux-i586.bin /usr/java
cp: cannot stat `jre-1_5_0_11-linux-i586.bin': No such file or directory

---

### Post by metalfanatic07 on 2007-04-10
> **LaurelLynn said:**
> Try and comment out the first two entries with a ¨#¨ they appear to be webpages, not repositories.

that worked, now for the whole installing java so frostwire doesn't shut down automatically on startup

---

### Post by mac.ryan on 2007-04-10
It should work if you would comment (adding ## at the beginning of the line) or delete (but make a copy before!) the lines that finish with .jsp and .html.

They do not look like repos but just webpages.

Reading the how-to about frost-wire - though - I can't figure out how those lines ended up in your file. Did you tried some other method beforehand?

Concerning the installation of Frostwire, can you follow the steps after the 3rd? Where do you get in troubles exactly?

If you saved your file on your Desktop, is it likely that you should change:

```
sudo cp jre-1_5_0_11-linux-i586.bin /usr/java
```

from the original how-to into

```
sudo cp ~/Desktop/jre-1_5_0_11-linux-i586.bin /usr/java
```

---

### Post by mac.ryan on 2007-04-10
LaurelLynn has been quicker for the comment. :(
I think I guessed about changing the command in the how-to... ;)

---

### Post by metalfanatic07 on 2007-04-10
> **mac.ryan said:**
> It should work if you would comment (adding ## at the beginning of the line) or delete (but make a copy before!) the lines that finish with .jsp and .html.

They do not look like repos but just webpages.

Reading the how-to about frost-wire - though - I can't figure out how those lines ended up in your file. Did you tried some other method beforehand?

Concerning the installation of Frostwire, can you follow the steps after the 3rd? Where do you get in troubles exactly?

If you saved your file on your Desktop, is it likely that you should change:

```
sudo cp jre-1_5_0_11-linux-i586.bin /usr/java
```

from the original how-to into

```
sudo cp ~/Desktop/jre-1_5_0_11-linux-i586.bin /usr/java
```

mike@Mike:~$ sudo cp ~/Desktop/jre-1_5_0_11-linux-i586.bin /usr/java
cp: cannot stat `/home/mike/Desktop/jre-1_5_0_11-linux-i586.bin': No such file or directory

this is what i got

---

### Post by mac.ryan on 2007-04-10
> **metalfanatic07 said:**
> mike@Mike:~$ sudo cp ~/Desktop/jre-1_5_0_11-linux-i586.bin /usr/java
cp: cannot stat `/home/mike/Desktop/jre-1_5_0_11-linux-i586.bin': No such file or directory

this is what i got

Of course it won't work... you have to change the name of the file from the version in the how-to (edited some time ago) to the version you just downloaded! :)

Look at the file you have on your desktop: if you downloaded right now it should be called "jre-6u1-linux-I586.bin"; so change the command above in order to match it! :)

[BTW: I assume you are running ubuntu, and not kubuntu or xubuntu...]

---

