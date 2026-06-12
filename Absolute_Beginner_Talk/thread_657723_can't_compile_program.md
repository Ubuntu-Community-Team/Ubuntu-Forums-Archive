---
title: "can't compile program"
date: 2008-01-03
forum: Absolute Beginner Talk
---

### Post by metalpancake on 2008-01-03
Hi. I have been trying to instal cinelerra
(video editing program) using this tutorial:
[https://help.ubuntu.com/community/CompilingEasyHowTo]("https://help.ubuntu.com/community/CompilingEasyHowTo")

When I get to the```
tar xjvf tarballname.tar.bz2
``` part,
I get the following error:
```
cinelerra-2.1-src.tar.bz2: Cannot open: No such file or directory
tar: Error is not recoverable: exiting now
tar: Child returned status 2
tar: Error exit delayed from previous errors

```
I'm sure I'm getting the filename right because I actually pasted it in to the terminal
tanks in advance for the help!:)

---

### Post by Xavieran on 2008-01-03
Did you download it to the Desktop?
If os are you in the desktop directory?

it should look like this if you are:YourUserName@YourComputerName:~/Desktop$

EDIT:You can actually tab-complete file names by typing in a little of them and then pressing tab...

---

### Post by metalpancake on 2008-01-03
yes, I downloaded it to the desktop. Does it need to be put somewhere else?

---

### Post by Xavieran on 2008-01-03
No,you just need to be in the desktops directory in the prompt ...see above...

EDIT:To change directories use ```
cd
```
ie.To change to the desktop do
```
cd Desktop
```

---

### Post by metalpancake on 2008-01-03
so what do you think my problem is?

---

### Post by Xavieran on 2008-01-03
Does the prompt Say ~/Desktop$
My guess is that you are not in the same directory as the file...

---

### Post by metalpancake on 2008-01-03
No, it just says ~$ with nothing between it.

---

### Post by Xavieran on 2008-01-03
Then do cd Desktop and then execute your command...

---

### Post by metalpancake on 2008-01-03
Hmmmmm....
```
bash: cd: desktop: No such file or directory

```

---

### Post by Xavieran on 2008-01-03
Desktop with a capital D...:)

---

### Post by metalpancake on 2008-01-03
Aha! That fixed it!:) Thanks for the help.
if I want to change the directory back to default, how do I do that?

---

### Post by Xavieran on 2008-01-03
cd ..
To go up a directory...and in your case your default directory...

---

### Post by metalpancake on 2008-01-03
ok. I will now try to compile the full program.:)

---

### Post by Xavieran on 2008-01-03
I'm all yours for the next 10 minutes :)
(I have to go to a party soon)

---

### Post by metalpancake on 2008-01-03
Ok, so i got up to the next step in the tutorial, which asks me to install the package apt-file. 
When I tried this it broke this to me:
```
sudo apt-get install apt-file
bash: apt-file: command not found
```:confused:

---

### Post by Xavieran on 2008-01-03
Search synapitic for it...
Sorry my dad turned my computer off...:(

Bye...:(

---

### Post by bwtranch on 2008-01-03
sudo apt-get install aptitude

For better results make a temp folder for downloads like mkdir /home/downloads/whatever

cd /home/downloads/whatever/whatever

This keeps stuff from cluttering up the desktop, oh, sorry Desktop.

use ls to see the contents of a directory. Use cd to change directory. Nice excercise: go to root / then ls then cd to whatever and learn about your file structure.

---

### Post by bwtranch on 2008-01-03
Also, be a good idea to get build-essential

sudo apt-get install build-essential

---

### Post by metalpancake on 2008-01-03
ok, thanks that worked.:)
Now it wants me to run this command:```
:/usr/local/src$ ./configure
```
I did that and once again:```
/usr/local/src$ ./configure
bash: ./configure: No such file or directory

```:confused:
I'm not having much luck with my compiling am I?...

---

### Post by dwhitney67 on 2008-01-03
'configure' is a shell script, or in layman's terms a file with instructions in it.

The error you received was due to the fact that you were trying to run the script in a directory where it does not exist.

Find the directory with the source in it, change directory into it, then run the './configure' again.

P.S.  Some configure scripts use advanced Bash shell scripting.  You mileage may vary with the "basic" bash shell (ash) that is installed by default with Ubuntu.  You may be required to apt-get the "real" bash.

---

### Post by metalpancake on 2008-01-03
d you mean I should change the directory to where my tar.bz files are? (desktop)

And yes. I have installed build essential.:)

---

### Post by iansane on 2008-01-03
I had the same problem. There is no configure file. and when I tried to use the make comand I got errors. Luckily I found the url for the sources list.

```
 deb http://www.kiberpipa.org/~gandalf/ubuntu/feisty/cinelerra/athlonxp/ ./ 
```

After adding that to the sources list

```
 sudo gedit /etc/apt/sources.list 
```

I was able to use apt-get to install it

first
```
 sudo apt-get update 
```
then
```
 sudo apt-get install cinelerra 
```

Normally it's not the safest thing to add sources you don't know but I think I found it on these forums somewhere and I haven't had any problems. Actually it might be at the cinelerra web site. Can't remember.

---

### Post by metalpancake on 2008-01-03
Thanks for the help:)
but...```
E: Couldn't find package cinelerra

```:(

---

### Post by bwtranch on 2008-01-03
Depends on who wrote the program. Did they put a configure script in there? Check the uncompressed archive for this. If you have a file called configure.something then they did. You can run sh dpkg -i install packagename. But, read the readme file first for details. That is your best bet.

---

### Post by metalpancake on 2008-01-03
oops! I didn't put in all the commands you posted!:mad:
I'll try again, and yes, there is a configure file in the package.
How exactly do you add the url to the sources list?

---

### Post by iansane on 2008-01-03
I can't remember but something was missing and that's why I used apt-get. Don't know why it can't find the package after doing apt-get update. Oh, well.... Sorry no help

---

### Post by bwtranch on 2008-01-04
Easiy way to get repositories is through Synaptic. Go to System -> Administration -> Synaptic Package Manager then after a password Settings and Repositories. Enable the ones you want (most). I can't tell you what to enable, that would be unethical:)

---

### Post by metalpancake on 2008-01-04
hmmmmmmmm......... still nothing.:(

---

### Post by xc3RnbFO8P on 2008-01-05
I installed Cinelerra using this information:

[http://cvs.cinelerra.org/docs/split_manual_en/cinelerra_cv_manual_en_2.html#SEC12]("http://cvs.cinelerra.org/docs/split_manual_en/cinelerra_cv_manual_en_2.html#SEC12")

I ran into one problem when I started cinelerra in Terminal

Missing  libGL.so.1.2 in /usr/lib

I found  libGL.so.1.2.xlibmesa in /usr/lib/nvidia

copy and pasted it to /usr/lib and rename it  libGL.so.1.2

I used Pcman to do this (in Pcman> tools> open as root)

---

### Post by metalpancake on 2008-01-05
> I installed Cinelerra using this information:

[http://cvs.cinelerra.org/docs/split_...n_2.html#SEC12](http://cvs.cinelerra.org/docs/split_...n_2.html#SEC12)
__________________
Thanks!:) I'll try again soon.

---

