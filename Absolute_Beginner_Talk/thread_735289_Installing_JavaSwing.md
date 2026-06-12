---
title: "Installing Java/Swing"
date: 2008-03-25
forum: Absolute Beginner Talk
---

### Post by Sequences on 2008-03-25
Hi,

I have been trying to code GUIs with Java using Eclipse in Ubuntu, and every time that I run it, the window pops up but that is where it stops. There is nothing displayed: no buttons, no pictures, nothing of any sort. It is as if I simply created a window. Eclipse did not give me an error and this is the second time that this has happened-second program to be more specific. So I know that on my computer, it is not an isolated event. I have tried to reinstall the Java stuff, but to no avail. 

So, yeah, what can I do? I asked one of my computer guru friends about this and he said it has something to do with Swing. But I do not know how to specifically reinstall that or stuff.

Thanks in advance.

---

### Post by herbster on 2008-03-25
For starters, run it from a terminal and paste the output.

---

### Post by nick_h on 2008-03-25
Have a look under Window->Preferences and Java->Installed JREs to see what JRE you are using in Eclipse.

---

### Post by Lord Illidan on 2008-03-25
It might help to post the code here, too.

---

### Post by Sequences on 2008-03-26
> **nick_h said:**
> Have a look under Window->Preferences and Java->Installed JREs to see what JRE you are using in Eclipse.

I am using java-1.5.0-sun-1.5.0.13 

I'm sure it is not the code for my program because if i copy and paste the project onto another computer, everything runs and displays properly.

---

### Post by nick_h on 2008-03-26
You could try sun-java6-jre rather than sun-java5-jre.

Swing works for me with Eclipse 3.2 and java 6 with Gutsy.

---

### Post by ahsile on 2008-03-26
Had the same problem last week...

Make sure your project isn't using the GCJ 1.5 runtime. Right click your project and select properties. Select the option for java build path. If it *is* using the gcj library click the button on the right to add a new library, select JRE libraries, then choose the sun JRE. Finally remove the GCJ library from your build path.

Hope this helps :)

---

### Post by Sequences on 2008-03-27
> **ahsile said:**
> Had the same problem last week...

Make sure your project isn't using the GCJ 1.5 runtime. Right click your project and select properties. Select the option for java build path. If it *is* using the gcj library click the button on the right to add a new library, select JRE libraries, then choose the sun JRE. Finally remove the GCJ library from your build path.

Hope this helps :)

Thanks for the advice. However, the library that I am using is JRE System Library [java-1.5.0-sun-1.5.0.13], which I assume should be the correct library to use? When I run the program, a window still pops up but with nothing on it. :(

---

