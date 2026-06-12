---
title: "Java NoClassDefFoundError"
date: 2005-12-23
forum: Absolute Beginner Talk
---

### Post by Revert on 2005-12-23
I've installed Java 1.5.0_05 and have it all set up, but I'm having trouble running programs from the terminal.  I have a simple helloworld type program, and while it runs perfectly in jEdit, and I can compile it with javac, whenever I try to run it, I get the NoClassDefFoundError.

Terminal Text: 

eli@core:~/Desktop$ javac helloworld.java
eli@core:~/Desktop$ java helloworld.class
Exception in thread "main" java.lang.NoClassDefFoundError: helloworld/class

What could be causing it not to run here, but to run in jEdit?  I only recently started doing Java on Linux, so is there some fundamental thing I'm missing that's different depending on the platform?  Am I typing in the commands correctly?

Thanks for any help, this is really getting annoying. :)

---

### Post by darth_vector on 2005-12-23
i havent programmed in java in a long time, but if i remember correctly you dont put in the .class when executing. just

java helloworld

and java will find the .class file and take care of the rest.

---

### Post by Revert on 2005-12-23
Son of a...

Thank you so much; I can't believe it was that easy.  I started programming on IDEs and hadn't ever used the command line compiler before. :)

---

### Post by darth_vector on 2005-12-23
lol, no worries. if you have any problems head over to the programming forum. there are lots of people with all levels of experience that are more than willing to help.

---

### Post by gamma on 2006-01-27
Wow! I just spent a good 15 minutes trying to figure out why I was getting this error. I rebooted my computer once, and tried exporting the java directory and everything. Thanks.

---

### Post by AngryPanda on 2006-02-18
#-o I can't *believe* it was this simple! Thanks for the help!

---

