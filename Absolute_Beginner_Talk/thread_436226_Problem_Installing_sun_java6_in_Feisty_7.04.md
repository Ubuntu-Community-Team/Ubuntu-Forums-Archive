---
title: "Problem Installing sun java6 in Feisty 7.04"
date: 2007-05-07
forum: Absolute Beginner Talk
---

### Post by a2c39a on 2007-05-07
Hi Folks,

I've been trying to upgrade from sun java5 to sun java6!
After much installing and removing of java 5 & 6, the current situation is as follows:

1. Both sun java5 & sun java6 are installed (using synaptic).
2. I have run: sudo update-alternatives --config java
   and set sun java6 to 'provide java'
3. I have run: sudo nano /etc/jvm
   and added: /usr/lib/jvm/java-6-sun
   to the top of the list and ^O saved it.
4. I have rebooted (many times).
5. I have checked and repeated the above several times.

However, when I type: java -version or javac -version
they both still say: java version "1.5.0_11"

Please let me know what I have done wrong or what extra needs to be done to switch over to sun java6?

Many thanks, John.

---

### Post by ticopelp on 2007-05-07
Have you tried:

sudo update-alternatives --config java

and switching to the new version that way?

---

### Post by fakie_flip on 2007-05-07
Why don't you remove the old java? Your symbolic links are probably pointing to the wrong java. They should be pointing to the same as mine.

chris@ubuntu:~$ ls -l $(which java)
lrwxrwxrwx 1 root root 22 2007-01-17 02:07 /usr/bin/java -> /etc/alternatives/java
chris@ubuntu:~$ ls -l /etc/alternatives/java
java         java.1.gz    java_backup  java_vm      javaws       javaws.1.gz
chris@ubuntu:~$ ls -l /etc/alternatives/java
lrwxrwxrwx 1 root root 36 2007-04-06 01:50 /etc/alternatives/java -> /usr/lib/jvm/java-6-sun/jre/bin/java
chris@ubuntu:~$

---

### Post by a2c39a on 2007-05-07
Hi,

Thanks for the replies.

ticopelp. Thanks but see item 2 in my list of what I have done!

fakie_flip. This comes under what I have done but not listed above.

My first attempts involved removing java5 and installing java6.
Result of this was no java at all!! Yes, all the symbolic links still pointed to java5. They still do!!
In my ignorance of ubuntu/linux I was expecting the synaptic installation to update the symbolic links but no this does not happen. I tried unlinking one before I did a java6 install but it remained unlinked after the install! So I put it back manually (at that time to java5).
There are quite a number of symbolic links associated with java surely I do not have to unlink all of them manually and replace all of them manually?
This sounds a very laborious business.
Is there something wrong with the way synaptic is installing java6?
Should it add new symbolic links?
Should synaptic have removed the old symbolic links when I used it to remove java5? 
(because it left them all pointing at nothing and with properties of 'broken link'!)

So what have I done wrong?

Many thanks for your help, John.

---

### Post by fakie_flip on 2007-05-07
I heard of others having problem with java in Feisty. I believe it is a bug in Feisty. The reason java works for me is because I had it already when I upgraded to Feisty.

---

### Post by ticopelp on 2007-05-07
Yeah, sorry about that, I missed it until after I'd already posted. I'm afraid I can't be of any further help.

---

### Post by a2c39a on 2007-05-07
Hi fakie_flip,

Thanks again.
Looking at your commands I get the following results:

(you seem to have two different outputs for: ls -l /etc/alternatives/java which confuses me slightly)

jeb@jeb-mdlt2-linux:~$ ls -l $(which java)
lrwxrwxrwx 1 root root 40 2007-04-28 06:01 /usr/bin/java -> /usr/lib/jvm/java-1.5.0-sun/jre/bin/java
jeb@jeb-mdlt2-linux:~$ ls -l /etc/alternatives/java
lrwxrwxrwx 1 root root 36 2007-05-07 21:36 /etc/alternatives/java -> /usr/lib/jvm/java-6-sun/jre/bin/java

So usr/bin/java does not point at /etc/alternatives it points directly to java5
is this my problem?
Is it just a symbolic link?
If so, can I just replace it manually?

Many thanks, John.

I've looked and yes this is the symbolic link for java but what about all the other symbolic links for javac etc. they are also wrong!

---

### Post by fakie_flip on 2007-05-07
You could try. Just incase it doesn't work, you can create some backups. If this doesn't work, you'll be able to restore the backed up files.

sudo mv -v /usr/bin/java /usr/bin/java_backup
sudo ln -s /etc/alternatives/java /usr/bin/java

---

### Post by fakie_flip on 2007-05-07
You could always remove all java packages, and then go to [http://java.sun.com/javase/downloads/index.jsp](http://java.sun.com/javase/downloads/index.jsp)
 download jdk se 6 Linux version from there, and install it.

---

### Post by a2c39a on 2007-05-07
Hi fakie_flip,

I think I'm getting somewhere at last!
The penny has dropped and I've realised that java is referring to java the program not java the complete system!
So I did the above checks for javac and the /usr/bin/javac already pointed to /etc/alternatives/javac
So I ran: sudo update-alternatives --config javac
and selected javac6 to provide javac.
Then I unlinked the /usr/bin/java symbolic link
and replaced it with: ln -s /etc/alternatives/java java

Now for both java -version and javac -version 
I have version 1.6.............Hooray!

Many thanks for your help. We got there in the end.

There are as I said several other java related symbolic links which still point to 1.5 but it would take some while to check them all out.  So for now I'll let it run like this and see what happens.
I'll post again if I have any other problems or observations. I'll mark it as resolved later if all seems OK.

Thanks again, John.

---

### Post by fakie_flip on 2007-05-07
Glad you got it working. You're welcome.

---

