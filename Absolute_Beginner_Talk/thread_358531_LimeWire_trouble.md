---
title: "LimeWire trouble"
date: 2007-02-10
forum: Absolute Beginner Talk
---

### Post by Baelfael on 2007-02-10
I used this guide:

[http://easylinux.info/wiki/Ubuntu#How_to_install_P2P_Gnutella_Client_.28LimeWire.29](http://easylinux.info/wiki/Ubuntu#How_to_install_P2P_Gnutella_Client_.28LimeWire.29)

to install LimeWire onto my Ubuntu system. It seemed to install, but when I go to Applications > Internet and click on LimeWire, it doesn't open. I know I have Java installed, I got it from the Add/Remove program.

Anyone help?

---

### Post by taurus on 2007-02-11
Try to run it from a terminal to see what's the error message is.

```
limewire
```

---

### Post by Baelfael on 2007-02-11
It returns with:

bash: limewire: command not found

---

### Post by taurus on 2007-02-11
Are you sure you have it installed on your machine?

```
locate limewire
```

---

### Post by Baelfael on 2007-02-11
That returned with:
```
/home/rih29/.icons/CrystalClear-GNOME-1.0.0/128x128/apps/limewire.png
/home/rih29/.icons/CrystalClear-GNOME-1.0.0/16x16/apps/limewire.png
/home/rih29/.icons/CrystalClear-GNOME-1.0.0/64x64/apps/limewire.png
/home/rih29/.icons/CrystalClear-GNOME-1.0.0/32x32/apps/limewire.png
/home/rih29/.icons/CrystalClear-GNOME-1.0.0/48x48/apps/limewire.png
/home/rih29/.icons/CrystalClear-GNOME-1.0.0/22x22/apps/limewire.png
/usr/share/gnome/help/desktopguide/sample/runLime.sh_limewire
```

---

### Post by taurus on 2007-02-11
See what happens when you run this command?

```
/usr/share/gnome/help/desktopguide/sample/runLime.sh_limewire
```

---

### Post by Baelfael on 2007-02-11
```
bash: /usr/share/gnome/help/desktopguide/sample/runLime.sh_limewire: Permission denied
```
...what the hell? :-I

---

### Post by taurus on 2007-02-11
```
ls -la /usr/share/gnome/help/desktopguide/sample/runLime.sh_limewire
```

---

### Post by Baelfael on 2007-02-11
> **taurus said:**
> ```
ls -la /usr/share/gnome/help/desktopguide/sample/runLime.sh_limewire
```
What does that do?

---

### Post by taurus on 2007-02-11
To list the permission & owner.

---

### Post by Baelfael on 2007-02-11
All's it returned with is:
```
-rw-r--r-- 1 root root 30 2005-05-29 04:58 /usr/share/gnome/help/desktopguide/sample/runLime.sh_limewire
```

---

### Post by taurus on 2007-02-11
What's the output of this command?

```
ls -la /opt/LimeWire/
```

---

### Post by Baelfael on 2007-02-11
That returned:

```
bash: ./usr/share/gnome/help/desktopguide/sample/runLime.sh_limewire: No such file or directory
```

---

### Post by Baelfael on 2007-02-11
Anything else?

---

### Post by phossal on 2007-02-11
If you have Java installed, just download the[ LimeWire "Other"]("http://www.limewire.com/LimeWireSoftOther") package directly from LimeWire.com. Then you simply double click the runLime.sh script that comes with it and it will launch. It is essentially self-contained and you can put the folder anywhere you want.

---

### Post by xpod on 2007-02-11
You could also consider frostwire if your still having trouble with limewire.It`s a free fork of Limewire and a much better alternative imho:) 

[http://www.frostwire.com/](http://www.frostwire.com/)

gtk-gnutella is mabey an ever better choice for that type of thing.It`s in synaptic and dosent even require the java i believe?

---

### Post by Baelfael on 2007-02-11
> **xpod said:**
> You could also consider frostwire if your still having trouble with limewire.It`s a free fork of Limewire and a much better alternative imho:) 

[http://www.frostwire.com/](http://www.frostwire.com/)

gtk-gnutella is mabey an ever better choice for that type of thing.It`s in synaptic and dosent even require the java i believe?
I installed FrostWire but now THAT won't open when I go to Applications > Internet > FrostWire.


:mad:

---

### Post by phossal on 2007-02-11
:popcorn: Entertaining, really.

---

### Post by Baelfael on 2007-02-11
;_;

Can anyone help. >: (

---

### Post by phossal on 2007-02-11
Go down to post #15. Download LimeWireOther.zip (from the link I've provided in post #15), and save it to your desktop. Extract it. Issue chmod+x on runLime.sh. Double Click It. Download Music and Be Happy.

---

### Post by Baelfael on 2007-02-11
I got LimeWire to work, but xpod said that FrostWire was a better alternative. So that's what's giving me problems.

---

### Post by phossal on 2007-02-11
It's *not* a better alternative.

---

### Post by phossal on 2007-02-11
If you're dead set on using FrostWire, here is the LimeWire-like "other" package for FrostWire: [FrostWireOther]("http://frostwire.com/download.php?file=http://www.frostwire.com/frostwire/4.13.1/frostwire-4.13.1.5-1.noarch.tar.gz")

1. Download it.
2. Extract it.
3. Double-click runFrostwire.sh
4. Download and Be Happy.

---

### Post by Baelfael on 2007-02-11
> **phossal said:**
> If you're dead set on using FrostWire, here is the LimeWire-like "other" package for FrostWire: [FrostWireOther]("http://frostwire.com/download.php?file=http://www.frostwire.com/frostwire/4.13.1/frostwire-4.13.1.5-1.noarch.tar.gz")

1. Download it.
2. Extract it.
3. Double-click runFrostwire.sh
4. Download and Be Happy.

Didn't work, but I can stay with LimeWire. Thanks for the help though.

---

### Post by phossal on 2007-02-11
Ah. You need to configure the path to JAVA_HOME. Java programs that exist independently like FrostWire search for that environment variable.

Typically, I put in my ~/.bashrc file.

---

### Post by xpod on 2007-02-11
> I got LimeWire to work, but xpod said that FrostWire was a better alternative. So that's what's giving me problems.

My apologies for that slightly mis-leading statement.They are of course basically the same and do the same job but frostwire is the free version and your not constantly pestered to update to the pro version as you are with limewire which is why it`s better in my opinion

What works is whats best though eh.

---

### Post by WiseElben on 2007-02-11
[Frostwire]("http://www.frostwire.com/") is great because of the lack of ads. Here is why FrostWire was created: [http://www.frostwire.com/?module=about](http://www.frostwire.com/?module=about)

---

### Post by AllanP on 2007-02-20
> **Baelfael said:**
> I got LimeWire to work, but xpod said that FrostWire was a better alternative. So that's what's giving me problems.

How did you get it to work. I bought LimeWireLinux.rpm (pro version). I have Java and it shows up under Applications/Internet/Limewire but, when I click on it nothing happens. I tried from terminal and get "runLime.sh: 44: Syntax error: "(" unexpected (expecting "}")".

Regards, Allan

---

### Post by phossal on 2007-02-20
runLime.sh may have #!/bin/sh instead of #!/bin/bash as it's shebang line.

---

### Post by AllanP on 2007-02-20
> **phossal said:**
> runLime.sh may have #!/bin/sh instead of #!/bin/bash as it's shebang line.

Thanks for the speedy reply. I opened up runLime.sh and the first line reads "#!/bin/bash".

At the end of the file it says "echo "Something went wrong with LimeWire."
    echo "Maybe you're using the wrong version of Java?"
    echo "(LimeWire is tested against and works best with with Sun's JRE, Java 1.4+)"
    echo "The version of Java in your PATH is:"
    java -version
    echo 
fi
". Does that mean it can't find Java?
If so would I have to direct it to Java somehow. As you can tell I'm not to hep on all this stuff.

I have echo "Something went wrong with LimeWire."
    echo "Maybe you're using the wrong version of Java?"
    echo "(LimeWire is tested against and works best with with Sun's JRE, Java 1.4+)"
    echo "The version of Java in your PATH is:"
    java -version
    echo 
fi
I have echo "Something went wrong with LimeWire."
    echo "Maybe you're using the wrong version of Java?"
    echo "(LimeWire is tested against and works best with with Sun's JRE, Java 1.4+)"
    echo "The version of Java in your PATH is:"
    java -version
    echo 
fi
I have echo "Something went wrong with LimeWire."
    echo "Maybe you're using the wrong version of Java?"
    echo "(LimeWire is tested against and works best with with Sun's JRE, Java 1.4+)"
    echo "The version of Java in your PATH is:"
    java -version
    echo 
fi
I have Java version 1.4.2.

---

### Post by AllanP on 2007-02-20
Oooooooops don't know what happened there. I was trying to paste version and wound up with multiples

---

### Post by phossal on 2007-02-20
What is the output of the following: 
```
java -version
ls -l $(type -path -all java)
```
The second one is likely to yield: /etc/alternatives/java. If it does, then do this:
```
ls -l /etc/alternatives/java
```

Out of curiosity, were you ever able to get the *free* version of LimeWire running? I've diagnosed problems with LimeWire hundreds of times, but never with the pay-to-play package. The [LimeWireOther.zip]("http://www.limewire.com/LimeWireSoftOther") file makes running LimeWire as easy as a click - *but it could be useful in diagnosing your problem.*

---

### Post by kelbizzle on 2007-02-20
Frostwire works just as good as limewire. Even though I don't use either. But I know for sure you won't have any problems installing it via automatix . [http://www.getautomatix.com/](http://www.getautomatix.com/)

---

### Post by AllanP on 2007-02-20
> **phossal said:**
> What is the output of the following: 
```
java -version
ls -l $(type -path -all java)
```
The second one is likely to yield: /etc/alternatives/java. If it does, then do this:
```
ls -l /etc/alternatives/java
```

Out of curiosity, were you ever able to get the *free* version of LimeWire running? I've diagnosed problems with LimeWire hundreds of times, but never with the pay-to-play package. The [LimeWireOther.zip]("http://www.limewire.com/LimeWireSoftOther") file makes running LimeWire as easy as a click - *but it could be useful in diagnosing your problem.*

Thanks I'll give that a whirl. I had the free version on Windows and upgraded to the pro version. When I did I also downloaded the rpm for Ubuntu as I am really trying to dispense with Windows entirely. But I digress; in answer to your ?; no I haven't

---

### Post by phossal on 2007-02-20
> **kelbizzle said:**
> Frostwire works just as good as limewire. Even though I don't use either. But I know for sure you won't have any problems installing it via automatix . [http://www.getautomatix.com/](http://www.getautomatix.com/)

Wow. Pay attention, mate. He *paid* for the pro package. 

Here is the deal in a nutshell, runLime is looking for JAVA_HOME or the Java executable. I'm not sure how the pro package installs it, but if you have installed Java correctly (either from the repository, or manually) then just *clicking* runLime.sh should work. 

Perhaps you need to run *sudo update-alternatives --config java*. We just need to know which version of Java you have installed, and where it is. I typically do all the steps of the problem that I'm trying to help out with. I just downloaded and installed the JDK, and I just downloaded the LimeWireOther.zip package (the easiest way), and it was as simple as double-clicking runLime.sh. Limewire opened right up for me.

---

### Post by AllanP on 2007-02-20
Tried that and got this: lrwxrwxrwx 1 root root 24 2006-11-03 18:32 /etc/alternatives/java -> /usr/bin/gij-wrapper-4.1

Still no Limewire

Thanks again for your efforts.

---

### Post by phossal on 2007-02-20
Right, Allen. One of two things is true, you *haven't* installed JDK 5 (or 6) which you need to do, or you haven't *enabled* them via update-alternatives.

If you have already installed JDK 5 (or 6), you need to enable it using update-alternatives like so:
```
sudo update-alternatives --config java
```
or you need to *get* JDK 5 (or 6) either using the repository or directly from SUN.

---

### Post by AllanP on 2007-02-20
[QUOTE=phossal;2185139]Wow. Pay attention, mate. He *paid* for the pro package. 

Here is the deal in a nutshell, runLime is looking for JAVA_HOME or the Java executable. I'm not sure how the pro package installs it, but if you have installed Java correctly (either from the repository, or manually) then just *clicking* runLime.sh should work. 

Perhaps you need to run *sudo update-alternatives --config java*. We just need to know which version of Java you have installed, and where it is.

Here's what I get:

There is only 1 program which provides java
(/usr/bin/gij-wrapper-4.1). Nothing to configure.

---

### Post by AllanP on 2007-02-20
> **phossal said:**
> Right, Allen. One of two things is true, you *haven't* installed JDK 5 (or 6) which you need to do, or you haven't *enabled* them via update-alternatives.

If you have already installed JDK 5 (or 6), you need to enable it using update-alternatives like so:
```
sudo update-alternatives --config java
```
or you need to *get* JDK 5 (or 6) either using the repository or directly from SUN.

OK I'll get going on that. Thanks

---

### Post by kelbizzle on 2007-02-20
Oh sorry about that. I must of overlooked it. Just never knew anyone to pay for FREE filesharing technologies that don't offer anything worth paying for thats his first mistake.  If you paid for the pro version why not get "Free" tech support by email.  Get what you pay for brother. Don't be a silly consumer. Good Luck to ya.

---

### Post by AllanP on 2007-02-20
Actually I found my transfer speeds did in fact improve with the paid version. Yes I guess I am the sucker and do believe in paying for what I use; even Ubuntu.

HAGO

---

### Post by wethepeople172 on 2007-02-28
Im New To Ubuntu And I Have Everything I Want But Limewire, I Downloaded What Everyone Said And Double Clicked The runlime.sh and it doesnt do anything....any help would be nice

---

### Post by AllanP on 2007-02-28
> **wethepeople172 said:**
> Im New To Ubuntu And I Have Everything I Want But Limewire, I Downloaded What Everyone Said And Double Clicked The runlime.sh and it doesnt do anything....any help would be nice

I'm no expert and find myself looking for help a lot. Did you get the info on installation from the Limewire web site? [http://www.limewire.com/english/content/ug49/ug_installation.shtml](http://www.limewire.com/english/content/ug49/ug_installation.shtml)

Here it is: Linux - Open a shell and cd (change directory) to the directory where you downloaded the installer. At the prompt type: sh ./LimeWireLinux.bin

I had to do the following to get my Limewire Pro working:


Paste the code below into Terminal. When you are prompted to install Dash,
select ?NO.?
sudo dpkg-reconfigure dash
That assumes that he is running Ubuntu 6.10 (Edgy Eft)

---

### Post by Perfect Storm on 2007-03-02
Here's how I've done it (edgy):

Download Limewire Pro (yes, I don't mind paying for stuff I really like) the .rpm file to your Desktop, then:
```
sudo aptitude update && sudo aptitude upgrade
sudo aptitude install sun-java6-jre sun-java6-plugin sun-java6-fonts sun-java6-bin alien
sudo update-alternatives --config java

```
Set java to version 6
then;
```
cd Desktop
sudo alien -i LimeWireLinux.rpm
sudo nano sudo nano /usr/bin/limewire

```

set it so it look like this:

[b]#!/bin/bash
cd /usr/lib/LimeWire
bash runLime.sh
[/b]

save and exit.

```
limewire
```

---

