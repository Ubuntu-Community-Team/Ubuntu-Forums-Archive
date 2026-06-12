---
title: "Java 6"
date: 2007-06-23
forum: Absolute Beginner Talk
---

### Post by mitchell486 on 2007-06-23
I had Java working. And then one day I went to go play at pokerroom.com and ka-put. It didnt work anymore. So I went to install it from their site. And wow. It's not even letting me get that far. I mean. I have java 6 installed but my Firefox will NOT recognize that its there. I have been trying for the last two days. Can anyone offer me any advice other than "Stop sucking at life" Cuz I am pretty sucky right now. :(

---

### Post by Inxsible on 2007-06-23
Post the output of the following:

```
java -version
```

---

### Post by mitchell486 on 2007-06-23
```
The program 'java' can be found in the following packages:
 * j2re1.4
 * gij-4.1
 * kaffe
 * jamvm
 * java-gcj-compat
 * cacao
 * sablevm
Try: sudo apt-get install <selected package>
Make sure you have the 'universe' component enabled
bash: java: command not found
mitchell@mitchell-desktop:~$
```


That is what I got when I typed that. Uh. I might have f'ed up my computer eh? Poop. :(

---

### Post by mitchell486 on 2007-06-23
Hey. If I have a second user created. My name. Mitchell. I want to be able to edit stuff as root. I can't seem to log into root. I know the password for it. But I don't know how to actually be logged in as root so that I can edit some folders such as /usr/lib/jvm. ? Anyone know how? OR! If you know how to make me root. That'd work too. :D

---

### Post by Inxsible on 2007-06-23
> **mitchell486 said:**
> ```
The program 'java' can be found in the following packages:
 * j2re1.4
 * gij-4.1
 * kaffe
 * jamvm
 * java-gcj-compat
 * cacao
 * sablevm
Try: sudo apt-get install <selected package>
Make sure you have the 'universe' component enabled
bash: java: command not found
mitchell@mitchell-desktop:~$
```


That is what I got when I typed that. Uh. I might have f'ed up my computer eh? Poop. :(

Did you run ```
java -version
``` or just ```
java
``` ?

---

### Post by bodhi.zazen on 2007-06-23
Logging on as root is disabled.

You can use sudo :

sudo -i

If you know the PW :

sudo su

If you use graphical programs :

gksudo <application_to_run_as_root>

OR

You can boot to recovery mode.

If you want to see a longer discussion (asn see how to enable root graphical logins) see this thread :

[http://ubuntuforums.org/showthread.php?t=365998](http://ubuntuforums.org/showthread.php?t=365998)

---

### Post by mitchell486 on 2007-06-23
The first. I put in java -version... and thats what i got. dude. I swear. I messed it up a while ago. :S and in my other post it explains why I cant put jre1.6.0_01 folder into my jvm folder because I am not root. And I should be. Its weird. :(

---

### Post by mitchell486 on 2007-06-23
```
java-1.5.0-sun 53 /usr/lib/jvm/java-1.5.0-sun
java-6-sun 63 /usr/lib/jvm/java-6-sun
```




Thats what I got when I put that in. Seemed to work a little better that time? I dunno. I'm new at this so. I suck at life. :(

---

### Post by mitchell486 on 2007-06-23
Wait wait wait. So I can't actually log in as root ever? I can't be the owner of my own computer? Well thats just silly. :S That means I can't edit folders like I need to.

---

### Post by bodhi.zazen on 2007-06-23
LOL

sudo give anyone in the admin group root powers. It is a security feature.

If you want to disable it, you can :

sudo passwd

Then follow the link I gave you.


[size=2]HOWEVER[/size]

I advise you use sudo as in my first post. Did you try 

```
sudo -i
```

To edit files as root :

```
gksudo gedit /path/to/file
```

geidit is a graphical program so use gksuo.

[size=2]READ THIS[/size]

[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

gksudo : [http://www.psychocats.net/ubuntu/graphicalsudo](http://www.psychocats.net/ubuntu/graphicalsudo)

You can also sudo -s if you want a new shell.

---

### Post by mitchell486 on 2007-06-23
Oohhh See i was looking at it wrong. I want to move a folder. I see. I'm logged into root in 'Terminal' Aight. I got that. Now. Do you know how to move a whole folder from one location to another? 


The long and short of it is I want to move /home/mitchell/jre1.6.0_01 to the new location where its supposed to be /usr/lib/jvm


If you could help that would be stupendious and I would owe you much thanks and as a man would have to then father your children because that's the rules of the africans. :D

---

### Post by Inxsible on 2007-06-23
I am not sure you use all the packages that were listed. But you can install java 6 and see if that works.

```
sudo aptitude install sun-java6-jre sun-java6-plugin sun-java6-fonts
```

---

### Post by mitchell486 on 2007-06-23
Uh it said it installed. I then tried looking in my JVM folder and java 6 still isnt there. I need to know how to get to that folder to put files in there. Like. log into root. take the file from ```
/home/mitchell
``` and put it in the folder ```
/usr/lib/jvm
```

---

### Post by bodhi.zazen on 2007-06-23
To do it graphically, 

[gksudo nautilus[/code]

Then you can copy/paste/drag ....

On the CLI:

```
sudo mv /home/mitchell/jre1.6.0_01 /usr/lib/jvm[code]

OR you can link:

[code]sudo ln -s /home/mitchell/jre1.6.0_01 /usr/lib/jvm
```

If you get an error that /usr/lib/jvm exists, move or delete this first.

---

### Post by Inxsible on 2007-06-23
Now try and run the first command i gave you.

```
java -version
```

EDIT : While replying to a thread, It got moved, and now my reply came to the first thread here in Absolute Beginners. Strange !!

---

### Post by mitchell486 on 2007-06-23
I am going to father your children. I FINALLY got it moved. Thank you for your support and help. I could have NEVER done it without you. If you ever need anything let me know. <3 I am definitely adding you to the list of amazingly smart Ubuntu genius's that i need to help me. :D Thanks mang. <3

---

### Post by Inxsible on 2007-06-23
WTF : Two threads seem to have gotten mixed here !!

Cant make no sense of nothing !

---

### Post by bodhi.zazen on 2007-06-23
Threads merged so as not to duplicate efforts.

Edit: I see you have it solved now.

Welcome to Ubuntu !

---

### Post by bodhi.zazen on 2007-06-23
> **Inxsible said:**
> Now try and run the first command i gave you.

```
java -version
```

EDIT : While replying to a thread, It got moved, and now my reply came to the first thread here in Absolute Beginners. Strange !!

He he he ...

That was me

Sorry for the confusion.

I was working on the thread "Root" and the merge function held over the defaults from my last moderation. #-o

I have the various threads sorted out now.

---

### Post by Inxsible on 2007-06-23
> **bodhi.zazen said:**
> Threads merged so as not to duplicate efforts.

Edit: I see you have it solved now.

Welcome to Ubuntu !

:)

---

### Post by mitchell486 on 2007-06-23
Ok. I had it ALMOST solved. I will still love you if you could help a poor man just alittle more. I have it in the correct folder. Now I am going to try one more time. But I think I am still having trouble with Java 6 working in Firefox.

---

### Post by mitchell486 on 2007-06-23
Ok. Here's the scoop. I have done EVERYTHING that Java has told me to do so that I can get it to work in Firefox. But. It still won't. I don't know why. This is what I get when I type java -version. ```
root@mitchell-desktop:/usr/lib/mozilla-firefox/plugins# java -version
The program 'java' can be found in the following packages:
 * j2re1.4
 * gij-4.1
 * kaffe
 * jamvm
 * java-gcj-compat
 * cacao
 * sablevm
Try: apt-get install <selected package>
Make sure you have the 'universe' component enabled
bash: java: command not found
root@mitchell-desktop:/usr/lib/mozilla-firefox/plugins# 

``` 

My friend is here to help. I'm going to try some things. Brb. Any help would still help.

---

### Post by mitchell486 on 2007-06-23
Sorry for all the confusion. I got it working in firefox now. I don't know if its all good throught the system or not but it works for what I want so. :D Thanks again. Later guys. <3

---

### Post by ellgor on 2007-06-23
Hi, 

Had the same sort of problem when accessing Coral Poker, applets wouldn't load and all that, the actual Java version that makes them work is the JRE 1.4.2 which is listed in the synaptic package manager. One last thing, it works with the Firefox but has problems with any other browser, I also use Opera, but it hung after 5 mins or so.

Regards, Ellgor.

---

