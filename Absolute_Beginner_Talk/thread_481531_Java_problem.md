---
title: "Java problem"
date: 2007-06-22
forum: Absolute Beginner Talk
---

### Post by groeswenphil on 2007-06-22
Trying to install java runtime environment in order to add movies and sounds to my Open Office presentations.

I've installed JRE and it appears to be working.
Now I'm stuck on this:-

Set up OpenOffice.org to use Java Media Framework
Use the Tools > Options > OpenOffice.org > Java menu
Click the Class Path... Button.
Click the Add Archive... Button.
Browse to the jmf.jar file to add it.

I can't find the jmf.jar file

Any ideas?
Phil

---

### Post by NeoLithium on 2007-06-22
I think it's in /usr/share/java

---

### Post by steve.horsley on 2007-06-22
I don't know where you get jmf.jar from, but it doesn't appear to be part of the standard JRE java runtime. I guess it's a separate download.

---

### Post by groeswenphil on 2007-06-22
Didn't read the instructions properly.
I should d this first.

Add support for MP3 audio
Download javamp3-1_0.zip from
[http://java.sun.com/products/java-media/jmf/mp3/download.html](http://java.sun.com/products/java-media/jmf/mp3/download.html).
Extract mp3plugin.jar.
Move mp3plugin.jar to the lib/ext directory in your installed java directory. You may need administrator rights to do this.
Copy jmf.jar to the lib/ext directory in your installed java directory. You may need administrator rights to do this.
In the console window, type java com.sun.media.codec.audio.mp3.JavaDecoder. You may need administrator rights to do this.

---

### Post by groeswenphil on 2007-06-22
Got this far, but can't find this one.

Move mp3plugin.jar to the lib/ext directory in your installed java directory. 

Not sure where I can find my installed java directory.
Phil

---

### Post by NeoLithium on 2007-06-22
Your installed java directory would be in /usr/lib/jvm  It may be something like /usr/lib/jvm/java-6-sun depending on which version you have installed. You can just use nautilus to poke around to find just where you have to drop it.

---

### Post by groeswenphil on 2007-06-22
Why is this so hard to do?

Why are so many people  so patient with me.

O.K. I've found where to put it, but I need administrator rights.
Where can I buy one?
Thanks,
Phil

Also, still can't find the jmf.jar file

---

