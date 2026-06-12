---
title: "Using programs after Install"
date: 2007-12-31
forum: Absolute Beginner Talk
---

### Post by bscasta on 2007-12-31
I have installed frostwire and it shows up under applications - internet but when i click on it, it doesnt do anything I am a complete newbie to linux but not to computers. I do have an mcp, mcdst, and mcsa. but this has nothing to do with linux so HELP PLEASE with any info

---

### Post by riven0 on 2007-12-31
Try opening it through the terminal. That's a better way to tell if the application is giving any errors. Go to Applications >> Accessories >> Terminal and then type in **frostwire**. Post the output of the command here and maybe someone can help.

---

### Post by kestrel1 on 2007-12-31
Just installed this & it works okay. If you right click on the Applications menu & select 'edit menus' then select 'internet' from the list. Highlight the frostwire link & right click on it. Select 'Properties' & check that the link is pointing to /usr/bin/frostwire
If it is, I would try re-installing the deb package.

---

### Post by bscasta on 2008-01-01
when I do it under terminal it says that I dont have the right java for it?    and when i right click it doesnt give the option of properties just Add this launcher to panel Add this launcher to desktop?   I appreciate you guys help

---

### Post by jken146 on 2008-01-01
To find out which version of Java you have installed:  ```
java --version
``` in a terminal.

To install Sun's latest Java, type:  ```
sudo apt-get install sun-java6-bin sun-java6-jre
```

---

### Post by bscasta on 2008-01-01
ok now i get 
Somethings wrong with frostwire
maybe somethings wrong with java
froswire works best with suns jre 1.4+
your version is 1.60_03

---

### Post by bscasta on 2008-01-01
when i do the java --version it say it could not create the java virtual machine

---

### Post by g2g591 on 2008-01-01
I believe the command you want is java -version, not --version.:guitar:

---

### Post by SOULRiDER on 2008-01-01
Yes, only one - not two.
For some reason frostwire won't work with that virtual machine. Have you tried updating the java alternatives? Check this link out, it explains how to set them [https://help.ubuntu.com/community/Java#head-fef9352fb26820bb774df978180c9dd3a60e777b](https://help.ubuntu.com/community/Java#head-fef9352fb26820bb774df978180c9dd3a60e777b)

---

### Post by bscasta on 2008-01-02
I appreciate all you guys help  but i just installed limewire and it opens so ill just use it. It says theres a firewall but im sure i can figure that one out.

---

### Post by SOULRiDER on 2008-01-02
Thats good to hear :)

---

### Post by jken146 on 2008-01-02
--Oops!

---

### Post by bscasta on 2008-01-02
Oh   i guess i should say SOLVED          sorry im also new to forums

---

