---
title: "[SOLVED] java for frostwire in feisty?"
date: 2007-08-05
forum: Absolute Beginner Talk
---

### Post by kleo skywalker on 2007-08-05
I'm on Feisty and need to install Frostwire. I looked around and found that Frostwire needs Java to work. I looked for Java in Add/remove as well as Synaptic, but get so many options that I'm confused. So my questions are:
1) Which is the latest version of Java that'll work on Feisty?
2) There are so many options, which ones do I need to install for Frostwire?
I don't mind using the terminal either if someone can tell me what to type in it.
Thanks.

---

### Post by overdrank on 2007-08-05
> **kleo skywalker said:**
> I'm on Feisty and need to install Frostwire. I looked around and found that Frostwire needs Java to work. I looked for Java in Add/remove as well as Synaptic, but get so many options that I'm confused. So my questions are:
1) Which is the latest version of Java that'll work on Feisty?
2) There are so many options, which ones do I need to install for Frostwire?
I don't mind using the terminal either if someone can tell me what to type in it.
Thanks.

Hi maybe this thread will help
[http://ubuntuforums.org/showthread.php?t=513551&highlight=java+for+frostwire](http://ubuntuforums.org/showthread.php?t=513551&highlight=java+for+frostwire)
Good luck! :)

---

### Post by kleo skywalker on 2007-08-05
> **overdrank said:**
> Hi maybe this thread will help
[http://ubuntuforums.org/showthread.php?t=513551&highlight=java+for+frostwire](http://ubuntuforums.org/showthread.php?t=513551&highlight=java+for+frostwire)
Good luck! :)

Thanks, but I'd seen this thread before posting - sorry, but it's too long and doesn't exactly answer my specific questions. Also, the person there isn't using Feisty - don't know if that matters, though.
So still looking for answers to my questions.
Thanks.

---

### Post by overdrank on 2007-08-05
> **kleo skywalker said:**
> Thanks, but I'd seen this thread before posting - sorry, but it's too long and doesn't exactly answer my specific questions. Also, the person there isn't using Feisty - don't know if that matters, though.
So still looking for answers to my questions.
Thanks.

In that thread  rsambuca speaks of what works with feisty, 

I had problems for a while as well, but it seems that frostwire liked java 5 better than java6. I am not using dapper, but I just installed java via synaptic, or you can just type
Code:

sudo apt-get install sun-java5-jre

Frostwire looks in certain places for java, and depending on which ubuntu you are using, it could place it somewhere else, so you might have to edit the file which tells frostwire where to look for java (or create a symlink)

---

### Post by HereInOz on 2007-08-05
If you want to make your Jave installation really easy, and not have to get involved in writing symbolic links for Firefox, and things like that, install Automatix2 
[http://www.getautomatix.com/wiki/index.php?title=Installation](http://www.getautomatix.com/wiki/index.php?title=Installation)

and that will run the script to download, install and configure Java for you, as well as a whole heap of other stuff.

The purists among us will sneer at Automatix users, but life wasn't meant to be difficult.

---

### Post by kleo skywalker on 2007-08-07
For the next person looking to do this simply, here goes:
1) Mark and install **sun-java6-jre** using *Synaptic packge manager* (you can search for "sun" or java" to find it). This also seems to install some other stuff that you need to get it working.
2) On Frostwire's website, download the package for Ubuntu. I opted to *Open with GDebi Package Installer*, but I suppose you could save to disk and install from there.
3) That's that, and Frostwire will show up on the Internet menu.

---

