---
title: "Netbeans, I just wont work properly!"
date: 2007-11-27
forum: Absolute Beginner Talk
---

### Post by tranquito on 2007-11-27
I recently installed the Java6 v1.6.0.16 JDK on my Ubuntu boot (I'm dual booting with Windows, sorry about that!) but when I downloaded Netbeans I was faced with numerous problems.

The installation to, opt/netbeans-5_5-linux.bin, goes fine and the Netbeans installer recognises my version of JDK but when I try and run Netbeans I get loads of different error messages about failing to load modules as well as some telling me that I only have JRE (liar!).

I properly set the JDK path during installation so why is it doing this? I don't have any weird configs, my Ubuntu is pretty much the same as when I installed it two weeks ago.

Any advice would be greatly appreciated.

PS
Off topic, what does the terminal command  "chmod a+x" and  "chmod +x"actually do?

---

### Post by luisromangz on 2007-11-28
How did you install java? From the repositories? Or did you install the installer package from Sun's site?

Those commands grant running permissions to all users and the actual user respectively.

---

### Post by tranquito on 2007-11-28
I used the installer package from Sun's website, should I have used repositories?

---

### Post by fulllefty on 2007-12-03
Sorry for not answering :(
I have the same problem too with netbeans.

I have installed Java 1.6.0 from Ubuntu 7.04 repository DVD
& allready do the:

#update-configuration..java (sorry i don't remember the command exactly)

Then I installed Netbeans 5.5 debian package that downloaded from
[http://ubuntu.osuosl.org/pool/multiverse/n/netbeans5.5](http://ubuntu.osuosl.org/pool/multiverse/n/netbeans5.5)

It consist of 3 packages, the installation went well, but when I run the Netbeans I get the same error like tranquito described up there (error loading modules because on the system only installed jre <which is not true>)

Can anyone help me why this is happening :confused:

---

### Post by siciliancasanova on 2007-12-03
I just installed net beans off their website and chmod + x to the bin file and installed, everything seems to be running fine.  The version I'm running is 5.5.1

---

### Post by siciliancasanova on 2007-12-03
Also point out for those of you who use Ruby on Rails, I was trying earlier today and last night to get Aptana going to develop some Ruby web apps and just couldn't get it done.  After no replies on the forums to my post and seeing this extensive blog post [http://www.lifeonrails.org/2007/8/30/netbeans-the-best-ruby-on-rails-ide]("http://www.lifeonrails.org/2007/8/30/netbeans-the-best-ruby-on-rails-ide")

I have decided to give NetBeans a try to develop RoR apps.  I as the guy who made the post, was not aware that NetBeans was an IDE for everything.  I assumed it was something that had to do with Java only.  Well I was wrong and it's accomplishing all my tasks.

Stick with it guys, it's definitely worth it.

---

### Post by dennis_matutina on 2007-12-17
> **fulllefty said:**
> Sorry for not answering :(
I have the same problem too with netbeans.

I have installed Java 1.6.0 from Ubuntu 7.04 repository DVD
& allready do the:

#update-configuration..java (sorry i don't remember the command exactly)

Then I installed Netbeans 5.5 debian package that downloaded from
[http://ubuntu.osuosl.org/pool/multiverse/n/netbeans5.5](http://ubuntu.osuosl.org/pool/multiverse/n/netbeans5.5)

It consist of 3 packages, the installation went well, but when I run the Netbeans I get the same error like tranquito described up there (error loading modules because on the system only installed jre <which is not true>)

Can anyone help me why this is happening :confused:
Hi there,

For the entire day, that is my problem too!, But I kept on at it since I wanted to learn Java and Netbeans seems to be less complex than Eclipse (at least at first glance).

Anyway, here's what I did:

$ sudo updatedb  ## to update the slocate db
$ locate java ## take note where the J2SE JDK  is located 
                   ##and copy in terminal (Shift+Cntl+C)
$ cd /etc/netbeans5.5 
$ su   to change or gksudo gedit netbeans.conf ## not sure about the last command
                                                                     ## but you need to be root to edit it
Then you have to change:
netbeans_jdkhome="path of your J2SE JDK"

save and try it out.

If you still get a blank gray dialog screen, it could be a compiz problem. Check out [https://help.ubuntu.com/community/CompositeManager/CompizFusion](https://help.ubuntu.com/community/CompositeManager/CompizFusion). What I did is just execute :
$ metacity --replace 
and I can see Netbeans5.5 and begin to use it. 

Hope this helps. I'm using Gutsy Gibbon on a dual core T2080 Intel Processor and Mobile Intel Graphics Media Accelerator 950, 1 GB DDR2, barely meeting the recommended specs for Netbeans....

Dennis
:guitar:

---

### Post by fulllefty on 2008-01-22
@siciliancasanova
thank you for your information, now I know that there is no problem with the package.

@dennis_matutina

thank you very much, after I am doing what you said in the post, it works!!!

---

### Post by sundar22in on 2008-01-22
@fulllefty:
Where did you get Ubuntu 7.04 repository DVD? I am looking for one!

~ Sundar ~

---

### Post by WakkiTabakki on 2008-01-22
Check:
[http://cdimage.ubuntu.com/releases/gutsy/release/](http://cdimage.ubuntu.com/releases/gutsy/release/)

/N

---

