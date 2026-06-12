---
title: "annoying error message"
date: 2007-03-17
forum: Absolute Beginner Talk
---

### Post by noob_saioke45601 on 2007-03-17
hey all, everything i install i always get this message.

```
Setting up sun-java5-doc (1.5.0-08-0ubuntu1) ...
This package is an installer package, it does not actually contain the
J2SDK documentation.  You will need to go download one of the
archives:

    jdk-1_5_0-doc.zip jdk-1_5_0-doc-ja.zip

(choose the non-update version if this is the first installation).
Please visit

    http://java.sun.com/j2se/1.5.0/download.html

now and download.  The file should be owned by root.root and be copied
to /tmp.

[Press RETURN to try again, 'no' + RETURN to abort] 

```

i press enter and it pops up again. i always have to type no twice then itwill proceed. sometimes the program wont even install cause of it or if it does it has no sound or somthing. i downloaded the jdk doc file to my desktop but no dea where to put it. i notice it should be owned by root.root and copied to /tmp so how do i do that?

---

### Post by dstew on 2007-03-17
To copy a file owned by root, use sudo:

sudo cp ~/Desktop/jdk-1_5_0-doc.zip /temp

What are you installing? Are you trying to install the Sun Java development kit, or the Sun Java run-time environment and plug-in? Are you using Add/Remove Programs, or Synaptic?

---

### Post by whistlerspa on 2007-04-21
I installed feisty on my desktop and laptop yesterday and each machine gets this error. To complete Synaptic installations I'm currently typing 'no' twice when prompted. The software appears to function post install. I've tried going to the suggested java website but it appears to be defunct or non-existent. My destop is running java 1.5 and my laptop 1.6

Does anyone have any idea how to fix this?

---

### Post by whistlerspa on 2007-04-21
OK fixed it finally

Did a Google search for the zip file mentioned and downloaded it to /tmp using sun's download manager and extraction program - and that was it problem solved.

---

