---
title: "java loaded but not recognized // runescape"
date: 2007-11-24
forum: Absolute Beginner Talk
---

### Post by wet_colored_arch on 2007-11-24
I've read forums and seem to be going in circles and not getting anywhere with Java.  Need help so my kids can switch to Ubuntu and run things like runescape.

When enter runescape, get message to load plugin. I have tried both the CGJ and Java/Sun alternatives, including both at same time when I ran out of things to try. I have tried to load these through Firefox with a machine using a very clean install of Gutsy.

1)  If  I used the CGJ web browser 0.92 alternative I simply get "error loading aplet" when I retry.  If I run "about(colon)plugins: from Firefox URL line the CGJ information is shown as existing. (not the case with SUN as shown below)

2) If I use the SUN option as a plugin, I am told the plugin is missing and I need to load, but when I try to load it says that it is already loaded and won't proceed.  The other "odd" thing is that if I am in firefox, with only Sun loaded and run "about(colon)plugins" from URL line in Firefox, the Sun Java is not shown.  It seems that somehow it is not visible to Firefox but I really am not sure.  

One of the threads suggested Epiphany browser.  This did not work either.
Another thread suggested using a repository with a now broken link to an alternative/altered tool from doku?

Another thread suggested that a symbolic link needed to be created to have mozilla load the sun plugin properly.  This might make sense as about(colon)plugins does not show the plugin and Runescape asks for things to be loaded (even though I thought I loaded it)

Therefore, I think what I need is help.
1)  Which files/applications do I need to remove (using Synaptic?) to get me back to a staring point that makes sense.  
2) What is really needed as Synaptic has a number of applications with a "java" association of some kind in the description?
3)  Which path should I try, CGJ or Sun or a hybrid?
4)  How can I see if the Sun is loaded, even though Firefox says it isn't?
5)  If it is loaded, could it be a link problem?  A thread talked about creating a symbolic link from one folder to .mozilla/plugin but I don't know what/how is a symbolic link and the .mozilla/plugin folder did not seem to exist in my system. I need a simpler way or more detail to get this right. (still a relative noob although I can occasionally get something done with terminal and gedit)

I can see from the forums people seem to get this to work quickly or not at all and the threads seem to die off.  Any suggestions are appreciated.

---

### Post by jken146 on 2007-11-24
You can use ```
java -version
``` to see which version of Java you have installed currently, if you aren't sure.

What I would do is go into Synaptic, do a search for 'java' and "completely remove" every package that is a Java runtime environment or plugin.  Then click on Reload.  Next search install the package sun-java6-jre and reload again (aka 'sudo apt-get update').  Next install the Sun Java plugin for Firefox, sun-java6-plugin .  This should do the trick.

---

### Post by wet_colored_arch on 2007-11-24
I want to make sure I understand what to uninstall.

the version listed is:  
java version "1.5.0"
gij (GNU libgcj) version 4.2.1 (Ubuntu 4.2.1-5ubuntu5)

when I use a keyword of "java" for search in synaptic there are 25+ items listed and few are shown explicitely as runtime or plugin.  I uninstalled completely - only those items that explicitely said JRE or plugin,  and then installed JRE and plugin through synaptic.  I got the license information (for the first time) and was hopeful. 

Then I opened firefox, accessed the site I got the same message that Java wasn't installed but when I went to install, it said it was installed (very confusing) and I remain stuck.

Checking about(colon)plugins now shows no Java installed.  This is similar as before.  I only get java showing up if I load the gci plugins (which only result in failed aplet

Now java -versions won't execute only saying "could not create java virtual machine" even though I loaded it and it shows up under Add/Remove programs

There must be some relationship between cgj and java that I don't understand and there must be some reason terminal and firefox seem unaware of Sun Java6.  Other threads talk also about loading some cgj plugins and mapping a symbolic link but there isn't enough detail for me to get it right.

---

### Post by mig5 on 2007-11-27
Are you running 32 bit or 64 bit ubuntu?

Are you sure that you have sun-java6-plugin installed (in synaptic)?  If you do, uninstall it (remove it completely) and then install it again, all with firefox closed.
If java still doesnt work and the plugin isnt showing up in about(:)plugins, navigate to /usr/lib/firefox/plugins/ and post here what files are listed there and whether they are symbolic links or files (links should have an arrow in the corner of their icon, or something similar).

---

### Post by geoff07 on 2007-11-28
this is just to thank the earlier respondent for the simple but useful advice which solved it for me.  It seems that there were just too many competing versions of Java around.  Hushmail now works.

G

---

