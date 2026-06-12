---
title: "Installing JIN/JAVA"
date: 2007-11-10
forum: Absolute Beginner Talk
---

### Post by yearofthetiger on 2007-11-10
I have been trying to get jin and java installed for the last couple of days. I still am learning ubuntu 6.06, I have learned a lot, but still am frustrated that I can't install these downloads.

I have 2 questions: How do I go about enableing multiverse/universe in <synaptic?>.

The other question is where do I go, and what do I do regarding these instructions on installing jin:

 Install Jin ***********

***********************************



1. Extract the tar.gz file you downloaded into some directory (if you got this

   file from the tar.gz file, then you're done :-)).



2. Make sure that the "java" binary is in your PATH. If you have one of the

   latest versions of Java installed, that will usually already be the case.

   Type "java -version" in a shell to see whether it works and to find the

   version of Java you have.

   If you don't have it in your PATH and don't know how to add it, ask in

   channel 212 on ICC, channel 85 on FICS, a newsgroup or #linuxnewbies on IRC.



3. Change to the jin directory (this will usually be in the format

   jin-<version> (jin-2.14 for example) and run Jin with "./jin". You can also

   create a symlink to the jin script in your ~/bin directory. If the jin script

   doesn't work for you for some reason, you can also run Jin with

   "java -jar jin.jar" from Jin's directory (the last part is important).



4. See [http://www.jinchess.com/wiki/index.php/Browser_(Unix](http://www.jinchess.com/wiki/index.php/Browser_(Unix)) for information

   on setting your BROWSER variable. Setting it properly allows Jin to open URLs

   when you click them in your preferred browser.



5. If you run Jin using a shortcut in your favorite desktop environment, Jin

   comes with a nice icon (icon.png in the main directory) for you to use.



6. If you encounter any bugs, want to ask for a certain feature or ask any 

   general question about Jin, see the sourceforge project page at

   [https://sourceforge.net/projects/jin/](https://sourceforge.net/projects/jin/) or email me directly at

   [email]msasha@engineer.com[/email].

---------------------------------------------------

sorry to be such a newb, I tried reading many threads and read many different ideas, but stiil i can't install these things. I think my ubuntu needs configuring.

---

### Post by overdrank on 2007-11-10
HI and for adding repos these links will help
[https://help.ubuntu.com/community/Repositories/Ubuntu](https://help.ubuntu.com/community/Repositories/Ubuntu)
[https://help.ubuntu.com/community/Repositories/CommandLine](https://help.ubuntu.com/community/Repositories/CommandLine)
And maybe this will help with the java
[https://help.ubuntu.com/community/Java](https://help.ubuntu.com/community/Java)
Good luck! :popcorn:

---

### Post by yearofthetiger on 2007-11-10
Thank you for reply, I will read your links and get back on this thread.

---

### Post by yearofthetiger on 2007-11-10
well, I installed java in terminal, I even accepted the license.

when I go to verify my java it still won't do it.

I am totally lost in what I am doing wrong.

---

### Post by yearofthetiger on 2007-11-10
why won't java verify? what am I doing wrong?

---

### Post by yearofthetiger on 2007-11-10
well, after some research i have found that dapper isn't that compatible with java if you are using amd 64, which I am.

I guess i will download a more up to date version and see what happens with that.

---

### Post by DeepNoob on 2007-11-10
If you're installing JIN for ICC, I found an older version of Blitzin (2.3 I think) on the net that runs fine in wine.

---

