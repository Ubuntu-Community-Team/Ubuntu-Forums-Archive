---
title: "Please help with java problem"
date: 2008-03-02
forum: Absolute Beginner Talk
---

### Post by BossGreen on 2008-03-02
ok, i've been trying to get the java plugins so i can play runescape, and i've hit a dead end i believe.
when i try to open the synaptic package manager i get

```
E:dpkg was interrupted, you must manually run 'dpkg --
configure -a' to correct the problem
E:_cache->open() failed, please report

```
and when i try to type 

```
sudo dpkg --configure -a
```

in the terminal, it says this

```
Setting up sun-java6-doc (6-03-0ubuntu2) ...
This package is an installer package, it does not actually contain the
JDK documentation.  You will need to go download one of the
archives:

    jdk-6-doc.zip jdk-6-doc-ja.zip

(choose the non-update version if this is the first installation).
Please visit

    http://java.sun.com/javase/downloads/

now and download.  The file should be owned by root.root and be copied
to /tmp.

[Press RETURN to try again, 'no' + RETURN to abort]
```


can anyone help me out please?

---

### Post by BossGreen on 2008-03-02
no one knows what to do...?

---

### Post by cotcot on 2008-03-02
What I have installed is sun-java6-jre and sun-java6-plugin (from the official repos). I think you want installing sun-java-jdk. Are you sure this is what you need ?

---

### Post by zxscooby on 2008-03-02
I dunno , To get java i installed the ubuntu-restricted-extras package

---

### Post by BossGreen on 2008-03-02
even if i dont need that, i still cant access synaptic package manager which is juat a little bit important...
i have sun java 6 console and sun java 6 web start i know... but i cant get the others to install...

---

### Post by BossGreen on 2008-03-02
i can now open "synaptic..." but i am not able to actually apply changes.  Normally it would ask for the password and i could, but now i dont even get that option.  It still says the same error message as before when i open it from Applications-System-synaptic package manager.

can anyone tell me how to fix this?

---

### Post by BossGreen on 2008-03-02
well... first off I'd like to thank all 671 people viewing this forum for being so helpful
this has sufficiently been a waste of time asking for help into the dark....

im probably going to switch back to windows when i can.

---

### Post by TheIdiot on 2008-03-02
I was gonna suggest fixing your software sources, running update/upgrade/dist-upgrade/install -f, but never mind. if you expect every ubuntu problem to be answered by this forum IN LESS THAN AN HOUR then stick to Winblows. Enjoy running multiple antivirus/firewalls/antispyware/registry cleaners. kthxbye

---

### Post by BossGreen on 2008-03-02
sorry, but i was frustrated with the help i was getting... and when i do get usefull tips, i get them like how you offered....

im sure you can understand

---

### Post by gigaferz on 2008-03-02
i remember having soma java issues, a few months ago, have youtried going to java.com?

I followd theirs instructions and it worked.

pick the linux self extracting file.(NOT the rpm)

 try restarting the computer, even people claim is not needed it has worked for me numerous times.

---

### Post by BossGreen on 2008-03-02
the instructions dont work the same for me, could it be because i am on xubuntu rather than something else?

---

### Post by TheIdiot on 2008-03-02
I'm on xubuntu as well and didn't have a problem installing java from the repo. The problem you're experiencing sounds like your sources.list is messed up or you didn't update the listing before installing. See if this works:

1) Applications > System > Software Sources
Under the "Ubuntu Software" tab, untick all the boxes. Now retick main, universe, restricted and multiverse.
Under the "Updates" tab, untick the first four boxes. Now retick gutsy-security, gutsy-updates and gutsy-backports.

2) In terminal, try these commands
```
sudo apt-get update
sudo apt-get upgrade
sudo apt-get dist-upgrade
sudo apt-get -f install
sudo dpkg --configure -a
```

---

### Post by BossGreen on 2008-03-02
after i do the first step i get this message

```
Could not download all repository indexes

The repository might be no longer available or could not be contacted because of network problems. If available an older version of the failed index will be used. Otherwise the repository will be ignored. Check your network connection and the correct writing of the repository address in the preferences.[B[/B]
```

---

### Post by BossGreen on 2008-03-02
would unchecking the two Gutsy Gibons cd-rom sources in the Third party software sources in the Software sources Help?

---

### Post by BossGreen on 2008-03-02
well, im gonna go to bed for the night, ill seek further assistance tomorrow.

the main error messages i've been getting are

```
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem.
```
after typing 
```
sudo apt-get upgrade
```

and

```
Setting up sun-java6-doc (6-03-0ubuntu2) ...
This package is an installer package, it does not actually contain the
JDK documentation.  You will need to go download one of the
archives:

    jdk-6-doc.zip jdk-6-doc-ja.zip

(choose the non-update version if this is the first installation).
Please visit

    http://java.sun.com/javase/downloads/

now and download.  The file should be owned by root.root and be copied
to /tmp.

[Press RETURN to try again, 'no' + RETURN to abort]
```


hopefully ill be able to get it working by tomorrow.
thank you for the advice so far people, i feel the problem is drawing to an end.

---

### Post by wormser on 2008-03-31
Try the following in order.

System> Administration> Software Sources and change the Download from.

```
sudo dpkg --configure -a
sudo apt-get -f install
sudo apt-get update
```
If all that goes well then install Java.

```
sudo apt-get install sun-java6-jre sun-java6-plugin sun-java6-fonts
```

Here is a [blog tutorial]("http://www.ubuntugeek.com/how-to-install-java-runtime-environment-jre-in-ubuntu.html") for installing Java.

---

