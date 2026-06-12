---
title: "Hi all new here&gt; i am an absolute beginner, and of course i need some help."
date: 2008-03-25
forum: Absolute Beginner Talk
---

### Post by justinsn95 on 2008-03-25
I just recently installed Ubuntu and this will be my very first Linux experience. I hope i can keep it, if i can make everything work that i need to i will be able to do so. The main problem i am having is that i can not seem to download and install anything, even though what i am installing is for Linux, sometimes ubuntu specifically. I managed to get limewire going, i loved it's package deal. Just like with windows, i just downloaded it and then opened the package and clicked install and it all worked perfectly. But i am afraid that is where my dificulties started. After that, i attempted to watch a youtube vid that would explain how to set up wine, only to find out i had no flash player.So, the page re directed me to where i could download one for Linux. So i did download it, and even though i clicked on the one called "YUM" i tink it sent me the one called "RPM". Either will work i guess. Anyway, i got it on to my desktop but when i try to click on it and install it, i get this message:

"Could not open the file /home/justin/Desktop/jre-6u5-linux-i586-rpm.bin using the Western (ISO-8859-15) character coding.Please check that you are not trying to open a binary file.
Select a different character coding from the menu and try again."

I am afraid i do not know any other way to go about this as i am a complete noob to ubuntu. Can anyone tell me what i am doing wrong? Or tell me where i can get all the flash players and stuff that i need? (like java and tar.gz). I really dont see why it wont work i got the one for ubuntu. This is the general response i get from the OS with just about everything new that i try to do. It seems to resist me at every turn. I go online and get things that are for ubuntu, only to download them and find out that i cant usethem for some reason or another. I have to admitit is becoming frustrating. Once i get java then will i be able to install packages the way that i should be able to?

Also, i went to java.com and tried to follow the instructions there, but after i enter "su" in my terminal, it asks for the root password. i entered my user password but that is not it. anyone know how i can learn the one that i need to do this?

---

### Post by aysiu on 2008-03-25
These links should help you...

**Install Java**
[http://www.psychocats.net/ubuntu/java](http://www.psychocats.net/ubuntu/java)

**Install Flash**
[http://www.psychocats.net/ubuntu/flashmanual](http://www.psychocats.net/ubuntu/flashmanual)

**Install things in general**
[http://www.monkeyblog.org/ubuntu/installing](http://www.monkeyblog.org/ubuntu/installing)

**Understanding basics of installation**
[http://www.psychocats.net/ubuntu/installingsoftware](http://www.psychocats.net/ubuntu/installingsoftware)

P.S. If you're using Ubuntu, forget YUM and RPMs--those are for Fedora, not Ubuntu.

---

### Post by Samurai Penguin on 2008-03-25
aysiu, you sure did cover the bases on that one

---

### Post by Ripfox on 2008-03-25
Go to your synaptic package manager under system/administration and install "ubuntu restricted extras"

You may have to click on "settings" then "repositories" in synaptic and enable the extra repos, then click "reload" before you can find the package you need there.

GL

---

### Post by aysiu on 2008-03-25
> **ripfox said:**
> Go to your synaptic package manager under system/administration and install "ubuntu restricted extras"

You may have to click on "settings" then "repositories" in synaptic and enable the extra repos, then click "reload" before you can find the package you need there.

GL
There's a step-by-step screenshot-based tutorial on this process:
[http://www.psychocats.net/ubuntu/nonfree](http://www.psychocats.net/ubuntu/nonfree)

The [*ubuntu-restricted-extras* metapackage](http://packages.ubuntu.com/gutsy/ubuntu-restricted-extras) is a pointer to a group of popular proprietary packages (Flash player, MP3 playback, Microsoft fonts, Java, Unrar).

---

### Post by pacsum on 2008-03-25
> **ripfox said:**
> Go to your synaptic package manager under system/administration and install "ubuntu restricted extras"

You may have to click on "settings" then "repositories" in synaptic and enable the extra repos, then click "reload" before you can find the package you need there.

GL
+1
Or you can use Applications > add/remove and there select on the upper right part of the screen "SHOW: ALL AVAILABLE APPS and search for **ubuntu restricted extras**. If it throws an error go to System > Administration > Software Sources and check all the options.

---

### Post by Ripfox on 2008-03-25
> **aysiu said:**
> 

P.S. If you're using Ubuntu, forget YUM and RPMs--those are for Fedora, not Ubuntu.

Yep Ubuntu normally used the > deb  package, since it is built on Debian Linux. But watch out, not all deb files are compatible with Ubuntu, in fact they can wreak havoc. Reading about the file before installing it is a good thing, as well as considering the source.

---

### Post by justinsn95 on 2008-03-25
thanks that is very helpful. i like that guide you wrote. i think a person who has never touched a computer could use that. I am starting from square one, and i wish to learn this OS inside and out.

---

### Post by justinsn95 on 2008-03-26
i came up with another question, (of course) What i wanted to know was, how do i enable universe and multiverse so that i can sudo apt-get Amarok? (isnt that what you do?) i need a more intuative media player, i have to say that rythmbox that comes with ubuntu is not so great. It is lacking in several areas compared to WMP or Realplayer. Thats just my humble opinion anyway.I was told that i can get this other one called amarok that is a lot better.

---

### Post by Circus-Killer on 2008-03-26
you enable repos by going to System > Administration > Software Sources 

and select the repos you want (in this case universe/multiverse)

also, if you are using ubuntu and not kubuntu, i would recommend giving exaile a try, before trying amarok. exaile is built to be very similar to amarok, except that it uses gtk (primarily gnome) instead of qt (primarily kde).

EDIT: btw the correct command to install amarok would be: ```
sudo apt-get install amarok
```

---

### Post by aysiu on 2008-03-26
AmaroK is in the Main repositories. You shouldn't have to enable Universe or Multiverse to get it.

---

### Post by justinsn95 on 2008-03-27
> **aysiu said:**
> AmaroK is in the Main repositories. You shouldn't have to enable Universe or Multiverse to get it.

is there a sub repositories somewhere? or a site that has a list of programs (along with descriptions) that are not on the main repositories list? That i can get using sudo apt-get intall.. i am really starting to love that feature. but i dont think you can use it on all free ubuntu software can you?

---

### Post by kesman on 2008-03-27
Mostly you can. There might be newer versions of software in getdeb.net, and some applications have a repository of their own which always provide the latest version, for example wine and gmusicbrowser.

---

### Post by Ub1476 on 2008-03-27
Popular packages which is not in the (Debian) repos, can be found on [getdeb.net]("http://www.getdeb.net/").

---

### Post by aysiu on 2008-03-27
> **justinsn95 said:**
> is there a sub repositories somewhere? or a site that has a list of programs (along with descriptions) that are not on the main repositories list? That i can get using sudo apt-get intall.. i am really starting to love that feature. but i dont think you can use it on all free ubuntu software can you?
You shouldn't really have to go to a site. Just use Applications > Add/Remove or System > Administration > Synaptic Package Manager to browse software packages and descriptions.

---

### Post by ubuntu-freak on 2008-03-27
Not much I can add to this great thread, but if you want to improve the streaming of audio/video content in Firefox, convert sound and video files, or need help with DVD playback/ripping/burning - take a look at my [how-to](http://ubuntuforums.org/showthread.php?t=661833). If you're a casual desktop user, you may be happy with your current setup, but give the how-to a go if you have more advanced needs. 
 
Welcome to Ubuntu by the way,
 
Nathan 
 
P.S. Making VLC the default DVD player may not work for now, I'm working on it though.

---

