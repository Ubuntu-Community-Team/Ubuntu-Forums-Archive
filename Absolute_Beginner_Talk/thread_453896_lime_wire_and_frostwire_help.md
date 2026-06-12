---
title: "lime wire and frostwire help"
date: 2007-05-24
forum: Absolute Beginner Talk
---

### Post by baskettplayr on 2007-05-24
i downloaded limewire first and like the interface wanst loading so then i tryied frost wire and it did the same thing... heres a pic for example.
[IMG]http://i120.photobucket.com/albums/o164/baskettplayr/Screenshot.png[/IMG]
any suggestions?

---

### Post by Dayylin on 2007-05-24
Hi,

Have you set up java on this machine?

Brian aka Dayylin

---

### Post by discmaster on 2007-05-24
Yeah, I believe it is a java 6.1 thing. Let me know if you get it to work, I couldn't.

---

### Post by NeoLithium on 2007-05-24
Open up a terminal window (Applications -> Accessories -> Terminal) and type this in:
```

sudo update-alternatives --config java

```
Ensure that you select the sun java option.  That should do the trick.

---

### Post by baskettplayr on 2007-05-24
ummm... i didnt have to change anything and this is what it looked like is this right?
[IMG]http://i120.photobucket.com/albums/o164/baskettplayr/Screenshot-1-1.png[/IMG]

---

### Post by NeoLithium on 2007-05-24
Yep, that's all correct. How did you install frostwire?

---

### Post by baskettplayr on 2007-05-24
well i went to the java website and it said i didnthave the latest version  so im downloading one now i will tell u if it works ok?:guitar:

---

### Post by NeoLithium on 2007-05-24
Sounds good. Hopefully it works for you :)

---

### Post by qamelian on 2007-05-24
> **baskettplayr said:**
> well i went to the java website and it said i didnthave the latest version  so im downloading one now i will tell u if it works ok?:guitar:

If you have Desktop Effects enabled, you need to either disable them, or download and install Sun Java 6.1 which corrects this bug.

---

### Post by baskettplayr on 2007-05-24
um will someone give me the a download link for  java 6.1  i  mean, thanks!

---

### Post by baskettplayr on 2007-05-24
^bump^

---

### Post by discmaster on 2007-05-24
[http://www.java.com/en/download/linux_manual.jsp](http://www.java.com/en/download/linux_manual.jsp)

I downloaded the 2nd one in the list. Then, I clicked on installation instructions, & from that point I was lost. I did this a week or so ago & gave up on it. 

Hopefully some of the "techier" guys on here will take notice & help a newb. out!

---

### Post by baskettplayr on 2007-05-24
oh ok
lets hope soo

---

### Post by discmaster on 2007-05-24
Any help on this, fellow Ubuntu members?

> To install the Linux (self-extracting) file

Follow these instructions:

   1. At the terminal: Type:
      su
   2. Enter the root password.
   3. Change to the directory in which you want to install. Type:
      cd <directory path name>
      For example, to install the software in the /usr/java/ directory, Type:
      cd /usr/java/

      Note about root access: To install the JRE in a system-wide location such as /usr/local, you must login as the root user to gain the necessary permissions. If you do not have root access, install the JRE in your home directory or a subdirectory for which you have write permissions.
   4. Change the permission of the file you downloaded to be executable. Type:
      chmod a+x jre-1_5_0-linux-i586.bin

I am trying to install to my home directory; this is what I end up with...

> tr@tr-desktop:~$ cd /home
tr@tr-desktop:/home$ chmod a+x jre-6_1-linux-i586.bin
chmod: cannot access `jre-6_1-linux-i586.bin': No such file or directory


I drag the downloaded file into the home directory first...

---

### Post by baskettplayr on 2007-05-24
bump

---

### Post by NeoLithium on 2007-05-24
The /home directory still requires root permissions.  For you to do it without root, you have to move the .bin file to your /home/USERNAME directory

Although, there's nothing wrong with installing it the root way, though however you feel comfortable still works too.

---

### Post by discmaster on 2007-05-24
Well, I don't know about baskettplayr, but I'm just not getting it. The directions didn't work for me a week or so ago, & they still aren't! I know I am doing something wrong here with the commands?, but I don't know how to figure this out.

(Did I mention I am a "green" newbie)! ;)

Is there any way you can "dumb it down" to something that a recent windows convert can understand? ;)

Much appreciated! :)

---

### Post by baskettplayr on 2007-05-24
lol discmaster i hear same thing here!!!

---

### Post by discmaster on 2007-05-25
Anyone able to "dumb down a bit" post # 14 instructions for a recent windows convert to understand?

---

### Post by discmaster on 2007-05-26
Thought I'd give this a shot again...
> tr@tr-desktop:~$ sudo
usage: sudo -K | -L | -V | -h | -k | -l | -v
usage: sudo [-HPSb] [-p prompt] [-u username|#uid]
            { -e file [...] | -i | -s | <command> }
tr@tr-desktop:~$ cd
tr@tr-desktop:~$ cd /home
tr@tr-desktop:/home$ chmod a+x jre-6u1-linux-i586-rpm.bin
chmod: cannot access `jre-6u1-linux-i586-rpm.bin': No such file or directory
tr@tr-desktop:/home$ chmod jre-6u1-linux-i586-rpm.bin
chmod: missing operand after `jre-6u1-linux-i586-rpm.bin'
Try `chmod --help' for more information.
tr@tr-desktop:/home$ ./jre-6u1-linux-i586-rpm.bin
bash: ./jre-6u1-linux-i586-rpm.bin: No such file or directory
tr@tr-desktop:/home$ 


For the life of me, I can't figure this out!

The directions on Sun's java install are not clear for a noob like me - **Please Help!!!**

---

### Post by baskettplayr on 2007-05-28
bump

---

### Post by Prisma on 2007-05-29
Hey basketplayr this issue is very easy to fix. Ubuntu fix it automatically. All you have to do is install the restricted codecs which install automatically when you open a movie file. 

Is not that this have anything to do with codecs (or maybe it does?) but it looks like when you install the codecs ubuntu update some aditional files which honestly dont know what they are. There is one update to the Hal. Maybe someone in this forum would explain to Us why this updates fix the problem.

But anyway, for even an easier solution just install automatix:

[http://www.getautomatix.com/apt/dists/feisty/main/binary-i386/automatix2_1.1-4.5-7.04feisty_i386.deb]("http://www.getautomatix.com/apt/dists/feisty/main/binary-i386/automatix2_1.1-4.5-7.04feisty_i386.deb")

and search for the restricted codecs. Install them. After you have installed the codecs, the update manager of Ubuntu will ask you to update some system files. 

just update Ubuntu and thats it. No more crashing of Azureus, no more gray window when you fire up frostwire, no more desktop effects deactivation to use those java programs.

Let me know if this fix your problem.  :D


P.D. One of those programs updated when you install the codecs is frostwire, very estrange isnt it?... LOL this is like Chinese medicine, it works even though you don't know why.... :D

---

