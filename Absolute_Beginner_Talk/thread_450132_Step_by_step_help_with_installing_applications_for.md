---
title: "Step by step help with installing applications for COMPLETE beginner"
date: 2007-05-21
forum: Absolute Beginner Talk
---

### Post by Shinapple on 2007-05-21
Hi all,

I've been running Ubuntu (currently Feisty) for a few months now with no running problems, but need to learn how to install programs from the terminal. I have asked this question in numerous places several times before but keep getting given tutorials which I don't understand.

 What I really need is a step by step guide to what I should be doing... ie. someone running through exactly what I have to type and what it means. I guess this is probably a pretty tedious thing to be doing but I just don't think I'm going to get it otherwise. I would like to install "Thinking Rock" which gives [manual install instructions]("http://www.thinkingrock.com.au/download/1.2.3/tr-1.2.3-linux-install.html"), but when I try to follow them I am obviously missing something and it just doesn't go anywhere. If someone can have a look at it and tell me step by step exactly what I need to do I would be ever indebted to your kindness! 

Thanks,
Shelly.

---

### Post by mikewhatever on 2007-05-21
First, the link you posted does not open.
Now, all you need seems to be here [https://help.ubuntu.com/7.04/add-applications/C/advanced.html#apt](https://help.ubuntu.com/7.04/add-applications/C/advanced.html#apt)

---

### Post by Shinapple on 2007-05-21
Okay, link should work now, and I guess to clarify... I am getting stuck at point 4 of the instruction guide I have linked to. As I said above, I have been given basic instruction guides similar to the one you just linked to then, but I need the steps explained. I know there is probably no one willing to actually do this for me, but if I don't ask I won't ever know.

---

### Post by wormser on 2007-05-21
> 4  Make the shell scripts are executable:
$ cd thinking-rock-1.2.3/
$ chmod +x thinking-rock.sh
$ chmod +x xdg*

5 Run the application. For example:
$ ./thinking-rock.sh 

I think your problem with step 4 is you cannot cd into that directory because it is not in your current directory.  You need to find the place that the package got unzipped to.  It is probably in the same location where it was downloaded to.  I am going to guess that is was the desktop.  If so, then open your terminal.

```
cd Desktop/thinking-rock-1.2.3
```

That will put you  into the directory and you will be able to execute the rest of the commands.  Let us know how it goes.

---

### Post by jiminycricket on 2007-05-21
A very nice guide is here: [How to install ANYTHING in Ubuntu]("http://monkeyblog.org/ubuntu/installing/")

or the one from aysiu which is really user friendly: [http://www.psychocats.net/ubuntu/installingsoftware](http://www.psychocats.net/ubuntu/installingsoftware)

---

### Post by Shinapple on 2007-05-21
> **wormser said:**
> I think your problem with step 4 is you cannot cd into that directory because it is not in your current directory.  You need to find the place that the package got unzipped to.  It is probably in the same location where it was downloaded to.  I am going to guess that is was the desktop.  If so, then open your terminal.

```
cd Desktop/thinking-rock-1.2.3
```

That will put you  into the directory and you will be able to execute the rest of the commands.  Let us know how it goes.

Thanks that has helped me in the right direction. I think what I really need is someone to sit down with me and run through the install so I can watch and learn what they do. Luckily I have a few friends who might help, if only I can drag them away from their own systems for a few minutes! 

Thanks again from the help, I might return when I am a bit more skilled! I feel as if even the beginners forum is too advanced for me !

---

### Post by wormser on 2007-05-21
> **Shinapple said:**
> Thanks that has helped me in the right direction. I think what I really need is someone to sit down with me and run through the install so I can watch and learn what they do. Luckily I have a few friends who might help, if only I can drag them away from their own systems for a few minutes! 

Thanks again from the help, I might return when I am a bit more skilled! I feel as if even the beginners forum is too advanced for me !

Just a quick note for you.  The best way to install new programs is threw Synaptic.  Go to System> Administration> Synaptic.  You can search for programs, check the ones you want then click install.  The program you wanted to install was an exception.  You should find everything you need in Synaptic.  Just search the forums or post a question if you ever need help.

---

### Post by mikewhatever on 2007-05-21
> **Shinapple said:**
> Okay, link should work now, and I guess to clarify... I am getting stuck at point 4 of the instruction guide I have linked to. As I said above, I have been given basic instruction guides similar to the one you just linked to then, but I need the steps explained. I know there is probably no one willing to actually do this for me, but if I don't ask I won't ever know.

Well, there is a limit to how basic a guide can get. You can't expect every single word in every single command explained, can you. The guide I suggested actually explains every single command there is.

---

### Post by exelan on 2008-01-06
I just tried to do the same thing, only when I ran the shell script I got this message

```
~/STUFF/thinking-rock-1.2.1$ ./thinking-rock.sh 
WARNING: Error loading security provider org.bouncycastle.jce.provider.BouncyCastleProvider: java.lang.ClassNotFoundException: org.bouncycastle.jce.provider.BouncyCastleProvider not found in gnu.gcj.runtime.SystemClassLoader{urls=[file:thinking-rock-linux-1.2.1.jar], parent=gnu.gcj.runtime.ExtensionClassLoader{urls=[], parent=null}}
WARNING: Error loading security provider gnu.crypto.jce.GnuCrypto: java.lang.ClassNotFoundException: gnu.crypto.jce.GnuCrypto not found in gnu.gcj.runtime.SystemClassLoader{urls=[file:thinking-rock-linux-1.2.1.jar], parent=gnu.gcj.runtime.ExtensionClassLoader{urls=[], parent=null}}
Aborted (core dumped)
```

---

### Post by jaya28inside on 2008-02-09
excuse me... i was wondering may i ask something here?
coz lastly i just download the alternatives of Linux
and so installed with the Command Line System...

looks like DOS
and then after completed it.. i get confused 
what should i do next...

some users suggesting me 

do 

>  sudo apt-get install ubuntu-desktop



and then really works... sorry i'm newbee here...
but then appeared after i type 

> 
STARTX


is it reaching the Safe mode looks like windows had?

so then what should i do next?
i really need help here... plzz 

many thanks

=============now i'm Linux-er
not a Widow-er.... :p

---

### Post by jan quark on 2008-02-09
> excuse me... i was wondering may i ask something here?
coz lastly i just download the alternatives of Linux
and so installed with the Command Line System...

looks like DOS
and then after completed it.. i get confused
what should i do next...

some users suggesting me

do

Quote:
sudo apt-get install ubuntu-desktop
and then really works... sorry i'm newbee here...
but then appeared after i type

Quote:
STARTX
is it reaching the Safe mode looks like windows had?

so then what should i do next?
i really need help here... plzz

many thanks


I think taurus is right ( same question in another thread) and you have downloaded the server edition

and since your network is not working you cannot access the internet to download the GUI

the graphical user interface

so you have to download once again the desktop edtition or the alternate edition BUT making sure it is not the server editi

---

