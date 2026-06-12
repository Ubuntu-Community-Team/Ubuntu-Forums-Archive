---
title: "Installing java in Kubuntu"
date: 2008-02-13
forum: Absolute Beginner Talk
---

### Post by Adddress on 2008-02-13
New to Linux -Might be a stupid question but - Have installed Gutsy and with lots of searching have got so far with installing sun- java6 But I now have Konsole open with text about package configuration -which looks like a licence agreement but I don't see how I agree - There is an <Ok> at the bottom - What do I  do next??

---

### Post by jaytek13 on 2008-02-13
Press the tab button. It will highlight <ok>, then press enter.

---

### Post by drtre on 2008-02-13
you're using synaptic packages?

---

### Post by Adddress on 2008-02-13
Thanks - Tab and enter works - So easy when you know how

Adddress

---

### Post by Adddress on 2008-02-13
So I think I have now installed JRE but Konquerer doesn't seem to know - If I go to Configure Konqueror - Java Javascript - there is a path to java option - how do I find what the path should be??

---

### Post by jaytek13 on 2008-02-13
So long as you restarted Konqueror it should be working as is. You can test java here:

[http://www.java.com/en/download/installed.jsp](http://www.java.com/en/download/installed.jsp)

---

### Post by Adddress on 2008-02-13
Sorry - But it just hangs on Loading Applet - Any ideas?

Adddress

---

### Post by Adddress on 2008-02-13
Finally - Did all the things in this link 
[http://ubuntuforums.org/showthread.php?t=163986](http://ubuntuforums.org/showthread.php?t=163986) 

"I don't know, just to be sure, try again 'sudo update-alternatives --config java'. As stated in the wiki article: 'You might want to do the same with jar, javac, javadoc, javah, javap and javaws'. In my case, it's set to the third alternative: '/usr/lib/j2re1.5-sun/bin/java'. Hopefully someone else more knowledgeable could provide you with a better clue?"

And I think this resolved the problem - not sure which one but just tried all of them

Not sure I learnt much from the hit and miss method but it works now.

---

