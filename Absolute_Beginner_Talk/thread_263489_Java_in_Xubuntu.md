---
title: "Java in Xubuntu"
date: 2006-09-23
forum: Absolute Beginner Talk
---

### Post by jordi_rc on 2006-09-23
Hello.

I am wondering if there is some way to install Java JDK in my Xubuntu PC that is NOT connected to internet (why? My DSL provider is a ###!!!???### and I am waiting for them to activate it from 52 days ago).

I don't know how to install the Java developer kit in Xubuntu, and when I go to Sun Java page there are instructions for other Linux systems, and a .rpm but not .deb

Also, I am very confused about JEE, EE, SE... I need to develop a java chat servlet and client, just this, and some GUI. What should I download????
Before they did those stupid changes of names, there was only JRE and JDK, so I am very confused.


And, by the way... what is Blackdown Java and what is better: Sun Java or Blackdown java?? What is the difference?

:shock: :shock: :shock: 

Hope that someone may help me.

Thanks.

Jordi

---

### Post by xyz on 2006-09-23
[Restricted Format]("https://help.ubuntu.com/community/RestrictedFormats#head-55315677ab8f9890825549fa2ecebdde4bc68087")

Should get Java for you. Good luck!

---

### Post by PPAAUULL on 2006-09-23
You could also use Automatix. it installs it for you.

---

### Post by xyz on 2006-09-23
[That's True!]("http://www.getautomatix.com/wiki/index.php?title=Installation")

---

### Post by jordi_rc on 2006-09-23
Thanks for all those links

Xubuntu comes with synaptic, to install packages.
If I had my dsl modem and connection, I will do that install as you say.
The problem is that I have not it yet, so I wish to know if there is some way to install jdk manually and easilly, or if you think I better wait a bit more and hope I had DSL soon.
What do you think?

Jordi

---

### Post by xyz on 2006-09-23
I'm not sure I understand what you're saying! And, in my huble and limited opinion, I don't think you can get Java WITHOUT ANY Internet at all.
Unless you buy it in a store? I don't know!
[http://java.com/en/download/manual.jsp](http://java.com/en/download/manual.jsp)

---

### Post by jordi_rc on 2006-09-23
Thanks anyway,

I think I will wait till dsl modem is in my house.

Thanks again

Jordi

---

### Post by xyz on 2006-09-23
How about going to a friend's, at school or work, or a CyberCafé and download it + copy to CD?

---

### Post by jordi_rc on 2006-09-28
FINALLY I GOT JAVA WORKING OK MANUALLY.

It's really easy in Xubuntu.

1) You go to Java Sun page and download the .bin package for Linux of Java SDK (link: java se, jdk 5.0 update 8)

2) Login as root

3) Do chmod 777 over the file in Terminal

4) Do chmod 777 over the folder where you will install it, or not if you use some folder of the filesistem belonging to root

5) Execute the .bin file simply with:
           
              ./jdk-1_5_0_08-linux-i586.bin

6) Answer Yes and wait

7) Now we install Firefox Plugin. Go to 

          usr/lib/firefox/plugins

8) Open Terminal there and type:

 ln -s /directory/of/java/jdk1.5.0_08/plugin/i386/ns7/libjavaplugin_oji.so


If you did well, Java is installed and Firefox has Java too.

Now, to have Java commands avaliable as root in terminal, open thunar, fin the file in the home of root user, called :
            .bashrc
It's a hidden file, so select View Hidden Files in thunar.

Add this to the end of the file:
# enable java commands
PATH="$PATH:/your/java/directory/jdk1.5.0_08/bin"
export PATH

HOW SMART I AM !! ;) ;) 


Jordi

---

