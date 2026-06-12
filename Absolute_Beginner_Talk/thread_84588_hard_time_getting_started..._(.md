---
title: "hard time getting started... :("
date: 2005-10-31
forum: Absolute Beginner Talk
---

### Post by No_Germs on 2005-10-31
i've switched to ubuntu from windows a couple of days ago, and i can't seem to use it very well-
i don't think i completley understand how installation of new software works on ubuntu all the way through:
1. i wanted to install the java runtime environment. so i downloaded it, and after that i was instructed to type a command on the command line in order to make it executable, and then run it from the command line so i'll see the binary agreement. i thought that i won't be using the command line so often. why not use the full potential of a graphical user interface and just allow me to double click it? (sorry for sounding like a clueless windows user :)). is this really the way to do it, or is it possible through the graphical interface, also?
2. i'm trying to install the Eclipse Sdk. this time, i did manage to find it using synaptic, but now matter which of the packages i choose, i get an error message:

eclipse-platform:
 Depends: eclipse-platform-common but it is not going to be installed
 Depends: eclipse-rcp but it is not going to be installed
i figured there's a cross dependency here so i need to install all the packages that are cross-dependent at the same time, so i've marked all the packages that we're written on the error message as missing, but i still got a similliar error message...

please help....

---

### Post by HJThis on 2005-10-31
Hello,No_Germs & Welcome

Here is a great link that maybe of help to you

[http://help.ubuntu.com/starterguide/C/faqguide-all.html#fg-installing-applications](http://help.ubuntu.com/starterguide/C/faqguide-all.html#fg-installing-applications)[PHP][/PHP]

Best of luck:rolleyes:

---

### Post by tonysathre on 2005-10-31
try this:
sudo apt-get install sun-j2re1.5
java -version

---

### Post by No_Germs on 2005-10-31
thanks, what about the Eclipse problem- how do i overcome this mutual dependency problem?

---

### Post by HJThis on 2005-10-31
Hi,No_Germs

If yo have a look at the link i posted there is
a tonn of info on this & more.

Best of luck

---

### Post by editrix on 2005-10-31
[QUOTE=No_Germs
i don't think i completley understand how installation of new software works on ubuntu all the way through:
1. i wanted to install the java runtime environment. so i downloaded it, and after that i was instructed to type a command on the command line in order to make it executable, and then run it from the command line so i'll see the binary agreement. i thought that i won't be using the command line so often. why not use the full potential of a graphical user interface and just allow me to double click it? (sorry for sounding like a clueless windows user :)). is this really the way to do it, or is it possible through the graphical interface, also?
2. i'm trying to install the Eclipse Sdk. this time, i did manage to find it using synaptic, but now matter which of the packages i choose, i get an error message:

eclipse-platform:
 Depends: eclipse-platform-common but it is not going to be installed
 Depends: eclipse-rcp but it is not going to be installed
i figured there's a cross dependency here so i need to install all the packages that are cross-dependent at the same time, so i've marked all the packages that we're written on the error message as missing, but i still got a similliar error message....[/QUOTE]

Okay, one newbie to another.

I read a lot of hype about Ubuntu for months before I tried it, and everyone agreed: It's easy! The trouble is, all those people who claim it's easy are experienced Linux users. So, relatively speaking, it *is* easy, but it's not a walk in the park.

I have to keep reminding myself: There's a huge learning curve to Windows, too. But it comes right after the Blue Screen of Death. In LInux, the learning curve is up front, but once you know what you're doing, there is no Blue Screen of Death--ever.

So, you're going to have to get used to it. You **will** be using the command line. Again, once you know what you're doing, it's often easier than the GUIs.

Regarding your specific problems:

1. I haven't tried installing Java yet, so I can't comment on how to do it but, see above, you'll have to get used to the command line--some people even learn to love it. :) 

2. There's probably a manual for apt-get somewhere on the web. Sorry, I don't have a reference for you, but I'm sure Google does. You don't have to memorize it, but you should at least understand the basics. Like Windows, Linux programs often need other programs to help them run. In Linux, they're called dependencies. So if you want to install something that has them, you install the dependencies, too. Synaptic will tell you what else you need--right click on the name of the program you want to install.

In Windows, they don' tell you anything, they just install the program and overwrite DLLs you need to run other programs, and then you spend a week on a HUGE learning curve of "DLL Hell" (Google that!) and then, like me, you say f*** it, if I'm going to spend this much time learning, it'll be for something worthwhile--Like Linux.

Since Ubuntu is based on Debian, you can help yourself by reading a lot about how Debian works. Just don't get terribly confused if Ubuntu does it differently--e.g., the sudo/root password conventions.

And be very patient with yourself.

---

### Post by David Marrs on 2005-10-31
The [Unofficial Ubuntu Guide](http://www.ubuntuguide.org/#jre) can help you with the j2re.

I'm not sure about your synaptic problem (synaptic's just a front end to apt-get, btw), but you should be able to do a smart install, where all dependancies are resolved automagically. Indeed, that's the whole point of using something like apt in the first place.

---

### Post by No_Germs on 2005-10-31
[QUOTE=HJThis]Hi,No_Germs

If yo have a look at the link i posted there is
a tonn of info on this & more.

Best of luck[/QUOTE]
i've looked at it, and it does explain alot of other things. but it doesn't answer my question-
when i try to install the Eclipse-platform package a new window pops up, telling me me that there are further changes need to be made, like installing ant ,junit,etc( i don't have a check box next to each item so i guessed when i allow the operation it installs all dependent packages alos)... 
i have two buttons on that window: "cancel" and "mark". so i click "mark", and then it shows an error dialog:
eclipse-platform:
 Depends: eclipse-platform-common but it is not going to be installed
 Depends: eclipse-rcp but it is not going to be installed
like i haven't allowed it to install the dependencies...

edit:
i've read this article on how to use synaptic:
[http://www.tuxmagazine.com/node/1000042](http://www.tuxmagazine.com/node/1000042)
and it says that after i click "mark" i then need to click "apply", but i don't get to that point. i get the error message right after i click "Mark"... am i doing something wrong?

thanks to all  you guys, BTW :)

---

### Post by editrix on 2005-10-31
[QUOTE=No_Germs]
when i try to install the Eclipse-platform package a new window pops up, telling me me that there are further changes need to be made, like installing ant ,junit,etc( i don't have a check box next to each item so i guessed when i allow the operation it installs all dependent packages alos)... 
i have two buttons on that window: "cancel" and "mark". so i click "mark", and then it shows an error dialog:
eclipse-platform:
 Depends: eclipse-platform-common but it is not going to be installed
 Depends: eclipse-rcp but it is not going to be installed
like i haven't allowed it to install the dependencies...
thanks to all  you guys, BTW :)[/QUOTE]

Well, first off, I searched the forums for Eclipse, and there's a ton of posts, so I'm going to be lazy and let you read all of them for yourself :) 

However, I got curious as to what it is, and my Synaptic tells me that the *only* thing it has is eclipse-nls-sdk--which is a localized message catalog for eclipse. IOW, my list of installable packages is different from yours.

What I'm thinking is, the dependencies you need are in a repository not in your sources.list. Understand, I'm new at this too and may be wrong. But it's quite obvious others have installed Eclipse successfully--although they're having problems, otherwise they wouldn't be posting ;) 

If you don't find your answer after you've read the posts in the results of your search, you might consider asking one of the folks who have installed it successfully. Nothing like asking someone who's been there before you.

---

### Post by public_void on 2005-10-31
The best thing to do is follow the Unofficial Ubuntu 5.04 Starter Guide  ([here]("http://www.ubuntuguide.org/#jre")) step by step from the beginning. Yep that will mean going into the terminal (command line) and typing all that stuff. When it comes to updates/upgrading stuff use the terminal. It may seem easy using the Graphical User Interface. But all it takes is to type a line, press return and the rest is done all for you. You may have to press y to confirm, but thats not too much to ask. 

When you start I'd say don't download any .rpm or .tar.gz yet (or manual download stuff). At first I hadn't a clue what I did with them, still haven't really, but I'll learn.

---

### Post by No_Germs on 2005-10-31
oh sorry for not mentioning this- i've tried installing from the command line, also. i got this error message:
**********
sudo apt-get install eclipse-platform

Reading package lists... Done
Building dependency tree... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

  eclipse-platform: Depends: eclipse-rcp (= 3.1.1-1ubuntu3) 
E: Broken packages
****
notice that it says that this installation depends on eclipse-rcp. if try to install eclipse-rcp it says;
 eclipse-rcp: Depends: libswt3.1-gtk-java
and so on... :/

---

### Post by tonysathre on 2005-10-31
here this will help....everyone needs to know how to compile apps so remember this...

make a diirectory (probably in your home directory) for the new app... move the gzipped tarball to that directory. open a terminal and cd (change directory) to the directory containing you tarball. type tar zxvf filename.tar.gz for a gzipped tarball or type tar jxvf for a bzipped tarball. this will extract all the files..then ls to see the new subdirectory that was created..then cd to that directory..now type ./configure then type make then sudo make install...thats it...after doing a couple of times you should be able to compile apps in no time...just the time that it takes to make and make install of course.

im not exactly sure about the problem but i would assume that the package on the repo server is broken and ubuntu doesnt want to install any broken packages

---

### Post by No_Germs on 2005-10-31
[QUOTE=tonysathre]here this will help....everyone needs to know how to compile apps so remember this...

make a diirectory (probably in your home directory) for the new app... move the gzipped tarball to that directory. open a terminal and cd (change directory) to the directory containing you tarball. type tar zxvf filename.tar.gz for a gzipped tarball or type tar jxvf for a bzipped tarball. this will extract all the files..then ls to see the new subdirectory that was created..then cd to that directory..now type ./configure then type make then sudo make install...thats it...after doing a couple of times you should be able to compile apps in no time...just the time that it takes to make and make install of course.
packages[/QUOTE]

ummmm,
a. i really didn't get that :)
b. how's that related to my problem? :)

---

### Post by tonysathre on 2005-10-31
that was to public void to help him compile apps

---

