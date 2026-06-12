---
title: "Need help installing Java"
date: 2007-10-19
forum: Absolute Beginner Talk
---

### Post by smalss on 2007-10-19
I just installed Gutsy and i want to install Java. Can anyone tell me how to do that from command line??

---

### Post by FuturePilot on 2007-10-19
```
sudo apt-get install sun-java6-jre sun-java6-bin sun-java6-plugin sun-java6-fonts
```
That should do it.:)

---

### Post by mlentink on 2007-10-19
Sure.

Although you can make it easy on yourself by going Applications>Add/Remove Software and search for Java. Take your pick, hit Apply and you're done... (no terminal commands necessary)

---

### Post by smalss on 2007-10-19
I installed the java stuff through the add/remove, but how can i update to 1.5 so that i can run frostwire??

---

### Post by smalss on 2007-10-19
K, nm the java stuff didn't work when i tried to install it from add/remove and from the command line! :S

any suggestions to try?

---

### Post by rsambuca on 2007-10-19
Those methods both work.  You just have to enable your "Multiverse" repositories first.  "System -> Administration -> Software Sources"

---

### Post by nickenich1 on 2007-10-19
> **FuturePilot said:**
> ```
sudo apt-get install sun-java6-jre sun-java6-bin sun-java6-plugin sun-java6-fonts
```
That should do it.:)
I tried your code:
sudo apt-get install sun-java6-jre sun-java6-bin sun-java6-plugin sun-java6-fonts

The system answers: 
sun-java-bin depends on unixodbc which is not installable
                  depends on libstdc++5  which is not installable
sun-java-jre depends on java-common(>=0.24 ) which is not installable

What is wrong with my system?

If you have an idea I'll be glad you let me know.

---

### Post by Sef on 2007-10-24
> I installed the java stuff through the add/remove, but how can i update to 1.5 so that i can run frostwire??

1.6 is in Add/Remove.  In search type in this:  > Sun Java 6.  Click on the top option and hit apply.

---

