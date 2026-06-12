---
title: "Installing Sun JDK?"
date: 2005-10-31
forum: Absolute Beginner Talk
---

### Post by Nevyn on 2005-10-31
I installed Ubuntu 5.10 Breezy Badger just yesterday, and am having my first experience of Linux ever. 
I need to be programming Java, so I installed Emacs and then tried to install Sun JDK 5.0. The RPM .bin-file just wants to be opened by a text editor (dont know which application to use when opening .bin-files). Then I found a thread concerning installing JRE. Figuring it was a similar procedure, I followed the posters tip, which follows:

1.Download and and save (non-RPM file) file into like '/home/(usrname)/java'
2.Open a terminal window and type 'sudo apt-get install fake root java-package'
3.Then type: 'sudo apt-get fake root make-jpkg (name of java file)'
4.Then Type: 'sudo dpkg -i *.deb

However, no. 2 on this list results in following error message:
E: Couldn't find package root

Is this the correct way to install the Sun JDK, what do I have to do to make it work. Otherwise: iwhat is the correct way to do it?

Im very new to Linux and for instance dont know what a fakeroot is, so a complete walkthrough would be perfect. 

Help is very appreciated.

---

### Post by tonysathre on 2005-10-31
i think that the fake root part should be fakeroot

---

### Post by majed on 2005-10-31
Look at this:

**[http://ubuntuforums.org/showthread.php?t=76754]("http://ubuntuforums.org/showthread.php?t=76754")**

Worked fine with me :)

---

### Post by Nevyn on 2005-10-31
Than'ks for the tip, majed.
I followed the instructions in the thread you provided, majed. Since I need the Java Developement Kit (jdk) and not the Runtime Enviroment (jre) i changed all the jre:s in the instructions to jdk:s. 
I didn't get any error messages, but I don't think i worked, since the the command 'javac' doesn't work. I need the compiler since I neded to write small Java-programs.

Is there anybody who has the JDK installed?

---

### Post by majed on 2005-10-31
Hummm... if everything worked with no errors then i suppose its there but not in your path?!

do a find in a terminal to see if it is there or not..

Run this in a teriminal:  

         sudo find / -name javac -ls

If you find javac, then it is a matter of setting your path :)

---

### Post by Nevyn on 2005-10-31
When trying to compile, the terminal returns this:
bash: javac: command not found

I did a search according to your instructions and javac was found in the supposed folder. I would think the command 'javac' needs to be connected with the javac-program in some way (that may be what you are suggesting above, majed, but I couldn't sor that out).
Again, this is something I do not know how to do, or even if it is the correct assumption.

majed > I think you have the whole thing under full control, I just want to check so there won't be a misunderstanding.  You know there's a difference between jre and jdk, and that the instructions you linked me to was for jre, but I need the jdk to work?

I'm thankful for the quick responses.

---

### Post by Leif on 2005-10-31
try this :

   1.  open a terminal
   2. type "sudo gedit /etc/apt/sources.list"
   3. at the end of that file, put in "deb [http://ubuntu.tower-net.de/ubuntu/](http://ubuntu.tower-net.de/ubuntu/) breezy java" (replace breezy with hoary if that's what you're using)
   4. save & close
   5. type "sudo apt-get update"
   6. type "sudo apt-get install sun-j2re1.5" (or, for developers, "sudo apt-get install sun-j2sdk1.5")
   7. to link to firefox, type " sudo ln -s /usr/lib/j2sdk1.5-sun/jre/plugin/i386/ns7/libjavaplugin_oji.so /usr/lib/mozilla-firefox/plugins"

this way everything will get updated automatically

---

### Post by majed on 2005-10-31
Well, i know you are doing the JDK, and you should be OK.. the only thing is, I don't develop so i don't know if there is an easier way of doing this, but i know it all goes down to environment variables in the end.. if u r a java developer, then i suppose u know about this (unless u r an IDE guy)..

So, here's how..

Set the PATH environment variable in terminal (or in /etc/profile or ~/.bashrc if you don't want to do it manually each time).

PATH=$PATH:<path_to_javac>:.
export PATH

if course, replace <path_to_javac> with the path to javac that you got  earlier from the find command.. so the tow lines would look something like this:

PATH=$PATH:/usr/local/jdk1.5.0_05/bin:.
export PATH

---

### Post by Nevyn on 2005-10-31
Thanks majed!

That was the final information I needed. I can now write, compile and execute java-programs.

[SIZE="1"]I did try Leif's method, but that resulted in the error message pasted below. Since majed's instructions worked, I don't need to work on that any more though.
"Errors were encountered while processing:
 emacs21
 cedet-common
 eieio
 speedbar
E: Sub-process /usr/bin/dpkg returned an error code (1)"
[/SIZE]

Thanks again!

---

