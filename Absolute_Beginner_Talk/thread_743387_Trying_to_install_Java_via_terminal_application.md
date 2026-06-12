---
title: "Trying to install Java via terminal application"
date: 2008-04-02
forum: Absolute Beginner Talk
---

### Post by JMann on 2008-04-02
Please bear with me. I'm a brand new linux user

I'm trying to install java off of [http://java.com](http://java.com). I'm being told to type "su" in the terminal and then type in my root password. I'm typing in the same password I've been using for everything else - logging on, turning on other applications, etc., but now I'm getting "Authentication failure." Also, no text appears when I type in the password, though I assume this is okay for security reasons.

Am I typing in the wrong password, or am I using terminal incorrectly?

Thanks.
__________

---

### Post by Daveth on 2008-04-02
why not get it out of the Ubuntu repository instead? Much easier :)

---

### Post by tangibleorange on 2008-04-02
> **JMann said:**
> Please bear with me. I'm a brand new linux user

I'm trying to install java off of [http://java.com](http://java.com). I'm being told to type "su" in the terminal and then type in my root password. I'm typing in the same password I've been using for everything else - logging on, turning on other applications, etc., but now I'm getting "Authentication failure." Also, no text appears when I type in the password, though I assume this is okay for security reasons.

Am I typing in the wrong password, or am I using terminal incorrectly?

Thanks.
__________

hi there,

as the above poster suggested, it is much easier to install java via the repositories. first, enable all your apt sources:

go to System-->Administration-->Software Sources and make sure "main universe restricted and multiverse" are all ticked. then go back into your terminal and type:

```
sudo apt-get install sun-java6-jre
```

if you need just the JRE (for running java applications). 

or, if you need the JDK (for making java apps) type this afterwards:

```
sudo apt-get install sun-java6-jdk
```

hope that helps! this link is very good for explaining how to install software in ubuntu on general:

[https://help.ubuntu.com/community/InstallingSoftware]("https://help.ubuntu.com/community/InstallingSoftware")

---

### Post by stchman on 2008-04-02
> **JMann said:**
> Please bear with me. I'm a brand new linux user

I'm trying to install java off of [http://java.com](http://java.com). I'm being told to type "su" in the terminal and then type in my root password. I'm typing in the same password I've been using for everything else - logging on, turning on other applications, etc., but now I'm getting "Authentication failure." Also, no text appears when I type in the password, though I assume this is okay for security reasons.

Am I typing in the wrong password, or am I using terminal incorrectly?

Thanks.
__________

To install java 1.5 use the following statement in a terminal:

```
sudo apt-get -y install sun-java5-bin sun-java5-fonts sun-java5-jdk sun-java5-jre sun-java5-plugin
```

This is for 1.5, if you want 1.6(latest) then substitute 6 for 5 in the above statement.

---

### Post by JMann on 2008-04-02
> **tangibleorange said:**
> 

go to System-->Administration-->Software Sources and make sure "main universe restricted and multiverse" are all ticked.

I'm not seeing these options (I'm in version 8.04, not sure if this makes a difference), however I followed your other steps and it seems to be working.

Thanks for your help!

---

### Post by JMann on 2008-04-02
tangible orange,

After trying your advice, I still got the following message on websites:

> Get the latest Java Runtime Environment to use Sun Download Manager

Internet Explorer Users: Check the top of this page for a "Java(TM) Web Start ActiveX Control" message in the information bar. If it appears, click it to finish detecting your Java version.

We were unable to detect a recent version of Java Runtime Environment (JRE) on your system. With the latest JRE, you can automatically download, install, and run Sun Download Manager (SDM) directly from this page. We highly recommend SDM to easily manage your downloads (pause, resume, restart, verify, and more). Visit java.com for the latest JRE.

stchman,

I tried what you said and the following happened:
> josh@pc212:~$ sudo apt-get -y install sun-java5-bin sun-java5-fonts sun-java5-jdk sun-java5-jre sun-java5-plugin
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
josh@pc212:~$ dpkg --configure -a
dpkg: requested operation requires superuser privilege


Help??? :)

---

### Post by Crafty Kisses on 2008-04-02
> **Daveth said:**
> why not get it out of the Ubuntu repository instead? Much easier :)

Yeah, that is a lot easier.

---

### Post by stchman on 2008-04-02
> **JMann said:**
> tangible orange,

After trying your advice, I still got the following message on websites:



stchman,

I tried what you said and the following happened:


Help??? :)

Put a sudo in front of dpkg --configure -a

---

### Post by The Cog on 2008-04-02
What's with all the command-line stuff? Menu System->Administration->Synaptic and search for "jre". You have a choice of java 5 or 6, I think. Mark for installation and apply.
I'm not in hardy at the moment, but that's how it's been done on all the previous versions. You _may_ have to menu settings->repositories and enable the restricted ones, but probably not.

---

### Post by Dragonlaw on 2008-04-04
Hello,

I have been following the steps taken here and now the terminal just shows me this "Configuring sun-java5-jre " along with the "Operating System Distributor License for Java v1.1 (DLJ)".

Have I done anything wrong?

---

### Post by spiderbatdad on 2008-04-04
Is there a details arrow to click? You probably need to accept an eula.
Ususally it pops up on its own, but not always.

---

### Post by Dragonlaw on 2008-04-04
No there isn't.  At the bottom of the License is just <ok>.

---

### Post by I_R_LEENUCKS_MAN on 2008-04-04
If you want to get su access, you have to do ```
sudo su
```

EDIT: If you want, you can use add/remove programs. That's what I ended up doing, worked a hell of a lot better than bin installation

---

### Post by tubasoldier on 2008-04-04
> **The Cog said:**
> What's with all the command-line stuff? Menu System->Administration->Synaptic and search for "jre". You have a choice of java 5 or 6, I think. Mark for installation and apply.
I'm not in hardy at the moment, but that's how it's been done on all the previous versions. You _may_ have to menu settings->repositories and enable the restricted ones, but probably not.

Because it is easier to give an answer that way. A copy/paste approach as opposed to "click here, then here, then here." One simple thing that will fix it. You can communicate with your computer like an infant, by pointing. Or you can communicate with a sentence. Its really up to you.

---

### Post by zvacet on 2008-04-05
```
sudo apt-get install ubuntu-restricted-extras
```

---

### Post by tangibleorange on 2008-04-05
> **Dragonlaw said:**
> No there isn't.  At the bottom of the License is just <ok>.

just press down on the arrow keys and you should scroll down to the bottom of the license. then when your think is on OK, press enter. that should accept the license.

---

### Post by harshask on 2008-04-05
I too am experiencing similar problems ... .. 

harsha@harsha-desktop:~$ sudo apt-get install sun-java6-jdk
Password:
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
harsha@harsha-desktop:~$ 
harsha@harsha-desktop:~$ su
Password: 
su: Authentication failure
Sorry.


If i have to run the  "dpkg --configure -a    " command ..... I hav to be superuser... But the second time i enter the password i have been using for all purposes .. It shows authentication failure ..What do i do now? ....

---

### Post by tangibleorange on 2008-04-05
> **harshask said:**
> I too am experiencing similar problems ... .. 

harsha@harsha-desktop:~$ sudo apt-get install sun-java6-jdk
Password:
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
harsha@harsha-desktop:~$ 
harsha@harsha-desktop:~$ su
Password: 
su: Authentication failure
Sorry.


If i have to run the  "dpkg --configure -a    " command ..... I hav to be superuser... But the second time i enter the password i have been using for all purposes .. It shows authentication failure ..What do i do now? ....

Run this command from a terminal:

```
sudo dpkg --configure -a
```

---

