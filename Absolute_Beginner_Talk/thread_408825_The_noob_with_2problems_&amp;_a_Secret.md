---
title: "The noob with 2problems &amp; a Secret"
date: 2007-04-13
forum: Absolute Beginner Talk
---

### Post by microsoft92sucks on 2007-04-13
The problem 1.
Ok im trying to install Limewire but it says i need a different java. some thing like JRE and said i could get it a jave.com i went there dowloaded it (i wasent sure wat version 2 get couse theres 4 differnt once just for linux) and when i opened it it opened with some    KDevelop thang i downloaded to do some C++ programing and it keeps freaven and it wont install. So do i have the wrong version or wat.(i am running Ubuntu)

Problem 2.
I have a Belkin wireless G usb Network Adapter and i don't know how to install it with Linux i looked it up and found lil help so please help me with these to problem.

And now for the Secret Look at the picture with the Tree that comes with the os and theres a few faces and a monster in it u can easily see and i thought i seen tux but now i cant find him. but the most seeble face is in the mid laft of the screen.

---

### Post by Zwalther on 2007-04-13
1 What version of Java did it say it needs? Are you sure you can't install that version with synaptic?

2 Did you try this: [http://www.gidforums.com/t-4390.html](http://www.gidforums.com/t-4390.html)

---

### Post by microsoft92sucks on 2007-04-13
When I open it with that it says this

"Starting without administrative privileges

You will not be able to apply any any changes. But you can still export the marked changes or create a download script for them."
and then it pulls up the Synaptic package manager :confused: 
 not sure cant find were it said that now but its wat ever one java.com has on it. 

And its a USB adepter and all i can find about it is i need ndiswrapper-1.41 (which i got but cant get to install) and a few other things i know nothing about.

Im srry i suck at this I thought i was pretty good at a computer when i had windows but know i dont feel so bright but i will not give up on Linux. im just gonna need a LOT of help 4 awhile till i get used to it (ive only had it 4 a few days.

---

### Post by microsoft92sucks on 2007-04-13
umm ok i just posted that and re read it and im dumber then i thought u ment synaptic as some other program thing im srry 4 being so dumb.

and to answer that ? 
i dont know ill check right now 

please put up with my stupieded lol

---

### Post by microsoft92sucks on 2007-04-13
**This post could be related to an Ubuntu bug filed at**: [http://java.com/en/download/linux_manual.jsp?locale=en&amp;host=java.com:80](http://java.com/en/download/linux_manual.jsp?locale=en&amp;host=java.com:80) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				Look at that wat 1 should i download couse im having trouble with it. and its sun java jre or somthang

"JAVA SOFTWARE for Linux
MANUAL DOWNLOAD
 
 
Java Software 		Java Runtime Environment Version 6 Update 1
Download other Java software versions

To complete the download of the Java Runtime Environment, please select from the list below. Please note that downloads are subject to our license agreement.
 

	
 
		
Step 1: Download 	Step 2: Install 	Step 3: Verify
Linux RPM (self-extracting file)
(filesize: 17.67 MB) 	Begin Java software download for Linux RPM (self-extracting file) 	Instructions 	Verify Java software installation

Once you have installed Java software on your computer, you must restart your browser. You can verify that it has been installed correctly by clicking on the 'Verify Installation' button above.

Linux (self-extracting file)
(filesize: 18.15 MB) 	Begin Java software download for Linux (self-extracting file) 	Instructions
Linux x64 (see below Note)
(filesize: 17.15 MB) 	Begin Java software download for Linux x64 	Instructions
Linux x64 RPM (see below Note)
(filesize: 16.75 MB) 	Begin Java software download for Linux x64 RPM 	Instructions"

---

### Post by Zwalther on 2007-04-14
Don't worry about sounding dumb. We all sounded dumb when we started with linux :)

You had the right synaptic. You should either start it from the menu (System->Administration->Synaptic) or should can type "sudo synaptic" in a terminal. That way you will run synaptic as root and you will be able to apply your changes.
After you start up synaptic, you should click on search and type java there. You will find several packages for java. I'm not sure which one limewire needs.

About your wifi adapter. I don't know anything about your particular type but it might run with ndiswrapper. Try googling for ndiswrapper and your particular type of adapter. 
It's possible that it won't run at all under linux, because there are still a lot of hardware manufacturers that don't want their software to be run by free software users.

---

### Post by Austin_KW on 2007-04-14
Which belkin is it, if it is version 2000 or 3000 then I think it is the ralink rt73 driver see [http://ubuntuforums.org/showthread.php?t=400236](http://ubuntuforums.org/showthread.php?t=400236). If it is version 4000 then you need your windows driver with ndiswrapper.

---

### Post by microsoft92sucks on 2007-04-14
Thanks for helping every1 i think i found the right java. and its sun java when i put that i found 2 thangs Sun Java(TM) Runtime Environment (JRE) 5.0 and The Java(TM) Plug-in, Java SE 5.0  im just downloading them both and im downloading another p2p called azruse or somthan ive seen it befor but never used (its the 1 with the frog if my spelling of it is to bad) is it any good? And i think thats the wrong _Usb Network adapter_
 and would calling belkin help anything. 1 more thing how do i put pics on here couse my Ubuntu

---

### Post by thefoolisme on 2007-04-14
If you are still having problems with the java and limewire after installing JRE 5, check this link out.  [http://daveshuck.instantspot.com/blog/index.cfm/2007/2/7/Installing-Java-6-16-in-Linux](http://daveshuck.instantspot.com/blog/index.cfm/2007/2/7/Installing-Java-6-16-in-Linux)

It discusses his path to updating java, but the part that might be beneficial is where he discusses configuring java.  I had installed Java 5, and Frostwire, and thought I was good to go, but I had not configured which Java for Ubuntu to use.  Once I configured it right, it was smooth sailing.

---

### Post by microsoft92sucks on 2007-04-14
i downloaded it from the Ad/remove thing under Applications so do i still need to do all that couse that seems over my head til i get better at this stuff.

and can some1 try to help me with my Belkin Wireless G USB Network Adapter

---

### Post by microsoft92sucks on 2007-04-14
I found out who to get my Belkin adepter to work but im still haven trouble with limewire 
:oops: [http://ubuntuforums.org/images/smilies/icon_redface.gif](http://ubuntuforums.org/images/smilies/icon_redface.gif) so any help with that would be well thanked. 

And thank u 4 helpin with belkin as well

---

### Post by thefoolisme on 2007-04-14
Check the java version running in your system by entering this in the terminal:

java -version

If it doesn't say version 1.5 is running, paste this in the terminal:

sudo update-alternatives --config java

Here's a copy of what comes up on mine:

There are 4 alternatives which provide `java'.

  Selection    Alternative
-----------------------------------------------
          1    /usr/bin/gij-wrapper-4.1
 +        2    /usr/lib/j2se/1.4/bin/java
          3    /usr/lib/jvm/java-1.5.0-sun/jre/bin/java
*         4    /usr/lib/jvm/jdk1.6.0/jre/bin/java

Press enter to keep the default[*], or type selection number: 

If the default (the one marked with a *) isn't java 1.5 on your system, then enter the number that corresponds to 1.5.

If you type in:

java -version       

again, it should now show version 1.5.

If that doesn't work, I would suggest trying Frostwire.  It's just like limewire - same screen configuration and everything.

---

