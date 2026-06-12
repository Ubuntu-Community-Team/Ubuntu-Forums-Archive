---
title: "Updating Java"
date: 2007-04-12
forum: Absolute Beginner Talk
---

### Post by noorez on 2007-04-12
I installed Sun Java 6.0 using the

sudo update-alternatives --install /usr/lib/java java /usr/lib/jdk1.6.0/bin/java 300
sudo update-alternatives --auto java

However, now that java 6 update 1 has come out, I want to start using that.

I was having trouble using update-alternatives to remove this link from alternatives. Can someone tell me how to do this?

---

### Post by phossal on 2007-04-13
No need to remove it. Download the new one. Increment the priority number to, say, 301. You should also change the name of the extracted folder. Rather than Java6 (as I suggest in the tutorial in my Sig), make it Java6u1. man update-alternatives for more info.

[edit] I notice you're using priority 300 in your example, and that you've moved the folder to /usr/lib, but you haven't renamed the folder. Who taught you that? :)

---

### Post by noorez on 2007-04-14
I used this from the link in your signature:
sudo update-alternatives --install /usr/bin/java java /usr/lib/Java6/bin/java 300

but i didn't use Java6 as the folder name and kept the extracted folder name.

I tried installing java 6 update 1 by:

sudo update-alternatives --install /usr/bin/java java /usr/lib/jdk1.6.0_1/bin/java 301.
On the command line: java -version shows the new java version but eclipse still apears to be using the old java version. How can I get it to switch to the new java version?

---

### Post by phossal on 2007-04-14
If you've defined the variable JAVA_HOME somewhere, that would cause a conflict. When I first wrote the tutorial, I recommended adding a line exporting JAVA_HOME in .bashrc. If you have that, and it still points to the old one, the launch executable for eclipse may still use it.

What makes you think eclipse is using the old one? Did you update the compiler settings in eclipse?

From the toolbar...

Window -> Preferences -> Java -> Compiler -> Compiler Compliance Level

---

### Post by noorez on 2007-04-14
In my application, I have  section that prints out the property java.vm.version. When I run my app via eclipse, it shows  1.6.0 but if I run it on the command line it shows 1.6.0_01. And in eclipse, how could I tell it to use 1.6.0 update 1? There is only a place for selecting a "major version"...like java 6.

I also check my .bashrc and there was no JAVA_HOME variable there.

---

### Post by phossal on 2007-04-14
1) Are you passing any parameters during compile-time to indicate what compiler should be used?
2) Have you set project-specific compiler settings by right-clicking on the specific project, selecting properties, and editing the Java compiler? Also, when checking this, note the build path and libraries indicated in the Order & Export tab.
3) You've set javac in update-alternatives, pointing to the wrong one. 

I've been awake more than 24 hours, though. ...I'm not thinking quite as clearly as I othewise would. If you're still having trouble when I wake up, I'll try to help you more.

---

