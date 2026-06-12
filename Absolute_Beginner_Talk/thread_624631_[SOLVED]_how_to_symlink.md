---
title: "[SOLVED] how to symlink?"
date: 2007-11-27
forum: Absolute Beginner Talk
---

### Post by staticvoid on 2007-11-27
Hi, for the life of me I cannot get java installed. I've taken every tutorial on the net and installed plugins and uninstalled them over and over again.

basically: in firefox i try to play a java applet ([http://www.java.com/en/download/help/testvm.xml](http://www.java.com/en/download/help/testvm.xml)) and it won't work.

I think it has to do with the symlinking. here is the contents of my plugins folder:
[IMG]http://i71.photobucket.com/albums/i123/broinjc/screenshot1-1.png[/IMG]

thank you in advanced. 

sv

---

### Post by ukripper on 2007-11-27
[https://help.ubuntu.com/community/Java](https://help.ubuntu.com/community/Java)

---

### Post by The Cog on 2007-11-27
Your existing symlink is broken (shown by the cross - it links to a nonexistent file). 

If you are doing this manually instead of the usual ways the link that ukripper gave you, you can create a symlink most easily by using nautilus. You may need root priviledge which you can get by launching nautilus with this command:
**gksu nautilus**
Use Ctrl-N to make a second window. 
In one window, go to the firefox plugins folder
In the other window, go to the JRE plugin/i386/ns7/ directory. Then drag /libjavaplugin_oji.so to the firefox directory using the **middle mouse button** and select link here in the popup menu.

---

### Post by staticvoid on 2007-11-27
Thank you so much  The Cog, that is EXACTLY what I needed. This explains why firefox can't play java, says it has the plugin install, but about: plugins shows no java plugin.

Thanks again,

Static V

---

### Post by staticvoid on 2007-11-27
oh wait, wheres the JRE plugin/i386/ns7/ directory?

sv

---

### Post by staticvoid on 2007-11-27
Oh wait, theres a link to the folder in the plugins directory! DOH!  haha..

sv

so, i middle clicked drag and dropped and it worked GREAT. btw, what if I don't have a middle click button, then what?

---

### Post by The Cog on 2007-11-27
You can emulate a middle-click or drag by using both the left and right buttons at the same time. 

I don't know where the Synaptic-installed JRE gets put I'm afraid - I always install my own JRE.

---

### Post by staticvoid on 2007-11-27
where do you install it? usr/java?

sv

---

### Post by The Cog on 2007-11-27
No, I install my JDK in /opt/jdk1.6.0_03, but that's just personal preference.

---

### Post by staticvoid on 2007-11-28
Oh ok. cool.

sv

---

