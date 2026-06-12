---
title: "Where do downloads go"
date: 2006-10-12
forum: Absolute Beginner Talk
---

### Post by meseleto on 2006-10-12
Ok. When you download programs from synaptic package manager that are not big applications (ie bittorent,scribus) where do the downloads go? I check on the properties and it gives the location of hundreds of different files sometimes. Which one is the one that actually runs my program? In windows it use to be the .exe but what is it in linux that tells me that's the program I need?

Also, how come when I double click on these files or click the option of opening it in the terminal nothing happends?

---

### Post by encompass on 2006-10-12
What are you trying to run... that would be a better question.  In linux you rarely have to look at where it goes.  But to inform you. linux doesn't use extenstions to identify a file.  It knows from a special tagging system.  That way people can't send malicious code. To make a long explination short.
So what do you want to run?

---

### Post by tonyr on 2006-10-12
Reading your question literally:
The downloaded file is <something>.deb, and is referred to as
a **package**. It ends up in /var/cache/apt/archives.  
The executables usually end up in /bin or /usr/bin.  Programs
like **synaptic**, **apt-get**, **dpkg**, **dselect**, **gdebi** 
process the package, extract all the files and put
them where they are supposed to be.  The executables usually end 
up in /bin or /usr/bin, and sometimes in other places, and 
could have a name that looks a lot like the name of the package
that you downloaded.  There are usually a lot of other files in
the package that get put in other directories: documentation,
reference and other supporting files, icons, etc.  All of those
kinds of files have conventional common directories in linux.

If your question is, as **encompass** supposes, 'How do I know 
what the name of the program is when I install a package with
**synaptic**?", many times an entry for the program is made in 
the Applications Menu. In /bin or /usr/bin, you might find a 
file with a name  that looks a lot like the name of the package 
that you downloaded.

If you are asking about something else entirely, please be a little more 
specific.

You might also try the **man** utility,

---

### Post by Charles Hand on 2006-10-12
If your question is, "I downloaded something, now how do I run it?", if it's a gui program it will often appear somewhere in your menu bar under "Applications" or "System". Usually you can make a pretty good guess as to where to find it. For example, bittorrent would appear under Applications->Internet. Gimp would appear under Applications->Graphics

If it's a command-line application, it will have been installed in your path so that you would simply type "xyz" in a terminal window to run program xyz. If you want to know for some reason where an executable is (gui or command-line), type
```
which <name-of-program>

e.g.

which scribus

```

but you don't have to know where it is in order to run it.

---

### Post by stig on 2006-10-12
On my system Scribus ends up in the Applications menu under Graphics (although it would make more sense for me under Office).

Alternatively, you can key Alt F2, type in scribus and click OK.

---

### Post by meseleto on 2006-10-13
Sorry if I wasn't clear. Here is an example. If i'm download a demo of a game like: "quake4-linux-1.0-demo.x86.run" and it ends up on my desktop, how do I run this program? I'm assuming it's with the terminal.

---

### Post by encompass on 2006-10-13
That's alot better...
In Terminal...
if your read the instructions... it could be compressed...
tar
zip
tar.gz
rar
etc...
in that case you could probably jsut click on it...
but if it is to be run...
> chmod +x file.name
chomod changes the mode of the program to different things... the +x means it will be change for(+) x which is executable.
from there... type...
> ./file.name
That will run it.
there are many other file types to work with, even more than windows.  But you will get most of them... jpg png and other too. :P
tremulous right?  I recommend running that as root so all your friends can run it in their accounts too...
> sudo ./tremulous.bla_dee_bla

---

### Post by meseleto on 2006-10-13
Hmm still doesn't work. When I type:

chmod +x quake4-linux-1.0-demo.x86.run

I recieve a message telling me that the file/directory does not exist.

---

### Post by encompass on 2006-10-13
then your not in the right place...
if you went strait to the terminal the desktop is found at
> cd Desktop
Otherwise your in you home directory, a different place than your desktop.

---

### Post by Rhubarb on 2006-10-13
> **meseleto said:**
> Hmm still doesn't work. When I type:
chmod +x quake4-linux-1.0-demo.x86.run
I recieve a message telling me that the file/directory does not exist.

I think this is because you're still in the home directory, you need to change directory to your Desktop folder:

```
cd Desktop
```

Then you can do the +x thing and run it.

---

### Post by meseleto on 2006-10-13
> **Rhubarb said:**
> I think this is because you're still in the home directory, you need to change directory to your Desktop folder:

```
cd Desktop
```

Then you can do the +x thing and run it.

OK i changed my directory and all it shows me when i try putting that command in know is my original line. For example, 

james@james-laptop:~/Desktop$

then i enter in the command chmod +x quake4-linux-1.0-demo.x86.run and i still get:

james@james-laptop:~/Desktop$

---

### Post by 3rdalbum on 2006-10-13
It's meant to do that - if you don't get an error message when entering that command, it means that the file has successfully been made executable.

Now just type:

```
./quake4-linux-1.0-demo.x86.run
```

If it's an installer, then you'll have to do:

```

sudo su #type in your password when it asks
./quake4-linux-1.0-demo.x86.run
```

---

### Post by meseleto on 2006-10-13
> **3rdalbum said:**
> It's meant to do that - if you don't get an error message when entering that command, it means that the file has successfully been made executable.

Now just type:

```
./quake4-linux-1.0-demo.x86.run
```

If it's an installer, then you'll have to do:

```

sudo su #type in your password when it asks
./quake4-linux-1.0-demo.x86.run
```

It works great now. Thanks!

---

