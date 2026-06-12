---
title: "Frostwire Won't Load After Installation"
date: 2006-08-27
forum: Absolute Beginner Talk
---

### Post by djross95 on 2006-08-27
I am new to Ubuntu, so I was hoping you could help me with this.  I recently installed the P2P program Frostwire by downloading the deb file and installing it with the program (gconf?) that comes with Ubuntu.  Everything seemd to go well, and an icon was added to the applications list. When I click on the icon, though, nothing happens---no error message or anything.

I know enough about Frostwire to know that it may have something to do with Java.  I did install Java support through EasyUbuntu and I think I'm running Java 1.5.6 (I saw that in a dialog box somewhere).

Can anyone help with this?  Do I just need to tell FW where the Java files are?   Thanks in advance for any help you can provide.....   DR

---

### Post by gerbman on 2006-08-27
Run Frostwire from a terminal window and post the error messages. You're probably right that it has to do with Java. I would recommend removing whatever you installed with Easy Ubuntu, downloading the JRE [here]("http://java.com/en/download/linux_manual.jsp") (choose self-extracting file), and following the instructions listed. This has always worked for me.

---

### Post by djross95 on 2006-08-27
Here you go........... 

Starting FrostWire...
Java exec found in PATH. Verifying...
OOPS, you don't seem to have a valid JRE. FrostWire works best with Sun JRE avai lable at [http://www.java.com](http://www.java.com)
OOPS, unable to locate java exec in  /usr/lib/  hierarchy
You need to upgrade to JRE 1.4.x or newer from [http://www.java.com](http://www.java.com)
ls: /usr/java/j*: No such file or directory
OOPS, unable to locate java exec in  /usr/java/  hierarchy
You need to upgrade to JRE 1.4.x or newer from [http://www.java.com](http://www.java.com)
ls: /opt/j*: No such file or directory
OOPS, unable to locate java exec in  /opt/  hierarchy
You need to upgrade to JRE 1.4.x or newer from [http://www.java.com](http://www.java.com)
djross@Ubuntu1:~$

I guess you were right.  Can you let me know how to uninstall the Java from EasyUbuntu?  I don't have any idea how to do that.   Thanks!     DR

---

### Post by djross95 on 2006-08-27
Sorry for all the questions, but one more:  I'm not sure how to install the self-extracting Java "bin" file....when I double click on it, it opens in Gedit.  I'm sure that's not right!    :-) 

Thanks for your patience......    DR

---

### Post by wsun on 2006-08-27
I get the same error message as well when running frostwire from terminal

---

### Post by cstudent on 2006-08-27
Run update-alternatives from the terminal. Make sure the * indicates you have Sun java as default
```

sudo update-alternatives --config java

```

---

### Post by gerbman on 2006-08-27
DJROSS:  the instructions on the site (next to the download link for the file) tell you how to install using the self-extracting file. You can try installing the JRE without uninstalling the other stuff, it might work.

WSUN:  follow the guide I linked to in my first post.

---

### Post by jconcepcion on 2006-08-27
I have learned, with the latest version of FrostWire that you have to modify the /usr/lib/frostwire/runFrost.sh file adding the begining at the top of the script:

cd /usr/lib/frostwire/runFrost.sh
java -jar FrostWire.jar

This is the only way that it worked properly for me.

---

### Post by gerbman on 2006-08-27
> **jconcepcion said:**
> I have learned, with the latest version of FrostWire that you have to modify the /usr/lib/frostwire/runFrost.sh file adding the begining at the top of the script:

cd /usr/lib/frostwire/runFrost.sh
java -jar FrostWire.jar

This is the only way that it worked properly for me.I think the command you wanted was```
cd /usr/lib/frostwire/
```not```
cd /usr/lib/frostwire/**runFrost.sh**
```

---

