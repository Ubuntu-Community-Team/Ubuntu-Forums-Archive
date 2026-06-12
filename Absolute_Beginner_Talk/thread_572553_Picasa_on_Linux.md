---
title: "Picasa on Linux"
date: 2007-10-10
forum: Absolute Beginner Talk
---

### Post by Orbital75 on 2007-10-10
I've Notice that Picasa is now available for Linux.  Do I need Wine or will it run without
it.  When I went to the Google site to download it, it stated that it used the Windows
API and mentioned something about Wine.  I got confused so I came here to ask.

---

### Post by rahimveron on 2007-10-10
Wine is included in Picasa. You dont have to install WIne separately. Just download the deb and install.

---

### Post by MrKlean on 2007-10-10
There s a straght linux vrson you can run without wine ; )

---

### Post by i-tech on 2007-10-10
> [http://picasa.google.com/linux/thanks-deb.html](http://picasa.google.com/linux/thanks-deb.html)
No you dont need wine for that :)

---

### Post by nest on 2007-10-10
type on a terminal

```
sudo apt-get install picasa
```

ready for use :)

you should start reading some tutos for begginers.

or using google ;)

---

### Post by rahimveron on 2007-10-10
> **MrKlean said:**
> There s a straght linux vrson you can run without wine ; )

AFAIK Google has not build Picasa Linux-native, so it uses wine, though dont have to install wine separately.

---

### Post by FuturePilot on 2007-10-10
Yes, the Linux version of Picasa is really just a modified Windows version that runs on top of a heavily modified version of Wine. But you don't need to install Wine. It's all in the .deb:)
I wish they would make a native Linux version though.;)

---

### Post by Orbital75 on 2007-10-10
Humm.... Yeah, I am in a Virtual Machine so Wine will kill my Speed and system resources.
Does anyone have a link to the non Wine Version? Is it the same or a watered down version?
Also, I am assuming that it's not in the default repositories, Will I need to add it to my source
list?

Thanks guys.....

---

### Post by nest on 2007-10-10
> **Orbital75 said:**
> Humm.... Yeah, I am in a Virtual Machine so Wine will kill my Speed and system resources.
Does anyone have a link to the non Wine Version? Is it the same or a watered down version?
Also, I am assuming that it's not in the default repositories, Will I need to add it to my source
list?

Thanks guys.....

[http://picasa.google.com/linux/thanks-deb.html](http://picasa.google.com/linux/thanks-deb.html)

---

### Post by Orbital75 on 2007-10-10
I tried installing Picasa but I can't get it to install..... I'm running Ubuntu in Virtual Box
could that be the issue?  Here is the error....

User@MyComputer:~$ su
Password: Password
root@MyComputer:/home/User# dpkg -i /tmp/picasa_2.2.2820-5_i386.deb
(Reading database ... 138139 files and directories currently installed.)
Unpacking picasa (from .../tmp/picasa_2.2.2820-5_i386.deb) ...
dpkg-deb: subprocess paste killed by signal (Broken pipe)
dpkg: error processing /tmp/picasa_2.2.2820-5_i386.deb (--install):
 short read in buffer_copy (backend dpkg-deb during `./opt/picasa/lib/libfreetype.so.6.3.8')
Errors were encountered while processing:
 /tmp/picasa_2.2.2820-5_i386.deb

I tried 1st to install it with The Deb package installer since it didn't
work I went to the command line.  I got the same error in both.

---

### Post by AlexenderReez on 2007-10-10
> **Orbital75 said:**
> I tried installing Picasa but I can't get it to install..... I'm running Ubuntu in Virtual Box
could that be the issue?  Here is the error....

User@MyComputer:~$ su
Password: Password
root@MyComputer:/home/User# dpkg -i /tmp/picasa_2.2.2820-5_i386.deb
(Reading database ... 138139 files and directories currently installed.)
Unpacking picasa (from .../tmp/picasa_2.2.2820-5_i386.deb) ...
dpkg-deb: subprocess paste killed by signal (Broken pipe)
dpkg: error processing /tmp/picasa_2.2.2820-5_i386.deb (--install):
 short read in buffer_copy (backend dpkg-deb during `./opt/picasa/lib/libfreetype.so.6.3.8')
Errors were encountered while processing:
 /tmp/picasa_2.2.2820-5_i386.deb

I tried 1st to install it with The Deb package installer since it didn't
work I went to the command line.  I got the same error in both.

please install it with double click....to see dependency issue ...

---

### Post by Incense on 2007-10-10
You can install it if you add the Google repo from this page. 

[http://www.google.com/linuxrepositories/ubuntu704.html]("http://www.google.com/linuxrepositories/ubuntu704.html")

Then just it's just an apt-get away. 

Cheers.

---

### Post by Orbital75 on 2007-10-10
Thanks, I'll give adding the repositories a try.  :)

Edit: Well, I added the PGP Keys and the Repository and it installed fine.
However, I was hoping for the version that didn't use Wine.
I'm in a Virtual Machine and it took 3 minutes for the license agreement to pop up.
after about 10 minutes of trying to read the agreement ( it wouldn't scroll ) too slow.
I decided just to close it and not use it.  Besides I read a line about it putting third party
software on the machine but never stated what.  

Oh well..... I don't need a slow running Wine needing program on my Virtual Machine.
It's just to slow..... Besides from the agreement, looks like that want to install some spyware.

---

### Post by MrKlean on 2007-10-11
BUT...it doesn't work on 64 bit ; (

---

### Post by Orbital75 on 2007-10-11
Well, I found this on the Google / Picasa site..... Isn't there a Version that won't Run
Wine. I'm currently on a Virtual Machine and Wine just won't work ( Killing Me Slow )....... 
Plus what's going on with this Third Party Stuff in the Licence Agreement ?

> **How do I download Picasa for Linux?**

As you may know, Picasa is now available for Linux users. Picasa for Linux runs the current Windows version of Picasa on the open-source Windows application-programming interface (API), Wine.

This version is available on Google Labs and can be installed from [http://picasa.google.com/linux/](http://picasa.google.com/linux/). You can find answers to the most common questions at [http://picasa.google.com/linux/faq.html](http://picasa.google.com/linux/faq.html)

At this time, we're unable to provide personal support for the Linux version of Picasa; however, we encourage you to ask questions and share feedback in our Help Group for Picasa for Linux users at 

[http://groups.google.com/group/Google-Labs-Picasa-for-Linux](http://groups.google.com/group/Google-Labs-Picasa-for-Linux)

What is sooo hard about writing it for linux natively...... Come on Google your already collecting information.

---

### Post by frozen1 on 2007-10-12
Oh man this is not like windows at all. Please help me get to understand linux. I am running Fiesty Fawn and am trying to follow the above instructions and am having no luck. I downloaded the above linux Picasa unto my desktop and then typed "sudo apt-get install picasa" into Adept and got nothing. So I take it a 'Terminal' is not Adept. Please point me to a beginner forum link I can read or give me better instructions. I also tried to install Absolute Poker and it is sitting on my desktop. Please don't take my words as impatience, I will read and search all I have to but I am completely lost and I appreciate any help

---

### Post by FuturePilot on 2007-10-12
Just double click on the file you downloaded. Simple eh?:)

---

### Post by Depressed Man on 2007-10-12
Press alt+f2 and type in (without the quotes) "gnome-terminal" if you are using gnome (assuming here). Gnome's interface if you haven't changed it is brown, light brown, and orange colors. 

You can also type in terminal and wait for the list of programs to respond then click the one that says terminal.

Then type in (again without quotes) "sudo apt-get install picasa"

Or if you downloaded the deb from Google (right click and save as.. or click and let the default action occur) it should do it for you. Just click.

---

### Post by frozen1 on 2007-10-12
Double clicking opens up 3 files and clicking them does nothing. I found Konsole and typed in sudo apt-get install picasa. and it looked for it but could not find it. I'll see if I can point to it.

---

### Post by frozen1 on 2007-10-12
this is what Konsole did

sudo apt-get install picasa
Reading package lists... Done
Building dependency tree
Reading state information... Done
E: Couldn't find package picasa
teresa@laptop:~$

---

### Post by tashmooclam on 2007-10-12
The problem with picasa for linux is that it is not picasa2, so there is no "picasa web album" button.
Although you can't tell, there is indeed wine in there. The picasa file is therefore HUGE. 
Although I really like that program, I just began to get used to F-spot and learn to live with it. 
Emailing from F-spot with Thunderbird didn't work well. 
So, although I use thunderbird, I made evolution my "default email". Now sending pictures using F-spot works. F-spot also worked with my picasa web albums, so I use F-spot now.
I can't remember how I downloaded picasa. Would the synaptic package manager work?

---

### Post by frozen1 on 2007-10-12
Ha thought I would drag the desktop icon for picasa into Konsole and paste it this is what I got

teresa@laptop:~$ '/home/teresa/Desktop/sudo apt-get install picasa'
bash: /home/teresa/Desktop/sudo apt-get install picasa: Permission denied
teresa@laptop:~$

I didn't even ask for my password...

---

### Post by FuturePilot on 2007-10-12
I see you must be using KDE, no?
If so, then right click on the file and in one of the right click menus there's an option to install it.
Using the apt-get install command only works if what you are trying to install is in a repo that you have added or is in one of the Ubuntu repos.

---

### Post by quinnten83 on 2007-10-12
Here you go, research material.
I was frequently reffered to this guide when I was starting out:
[http://cutlersoftware.com/ubuntuinstall/#installing_a_package_manually]("http://cutlersoftware.com/ubuntuinstall/#installing_a_package_manually")

It is a general resource guide for installing software in ubuntu, should work similarly for Kubuntu. A little googlin will give you the specific information you need.

---

### Post by frozen1 on 2007-10-12
Yes I am using KDE. Thanks for the info. So simple when you know what to do THANKS FuturePilot, and everyone else. I can't believe I didn't see the install under 2 right clicks. Thanks to everyone who responded.

---

### Post by Orbital75 on 2007-10-12
Is there a non wine version?  It's to slow on a virtual machine.......
Plus what Third Party Software is it installing?

---

### Post by FuturePilot on 2007-10-12
No there is no native Linux version. I think the 3rd party software it is referring to is Wine.

---

### Post by Orbital75 on 2007-10-12
Ah.... Well that isn't so bad then ( Third Party Stuff ) referring to Wine.
That I don't mind. 

I switched to Ubuntu to avoid all this " We're including
this Third Party Software to enhance your experience Stuff ".
All that is, is Bloat and Nagware.  

Well, I was hoping to be able to use Picasa but it looks like
until I install Ubuntu Natively, I won't be able to use it.
I'm sure it's not that hard to write it natively Google
got huge deep pockets.

---

### Post by antisocialist on 2008-01-31
> **Orbital75 said:**
> 
I'm sure it's not that hard to write it natively Google
got huge deep pockets.

not only that but the founder of google also "invented" (aka derived from debian) ubuntu linux, and yet there is no ubuntu linux version of the software.

go figure

---

### Post by Incense on 2008-02-01
> **antisocialist said:**
> not only that but the founder of google also "invented" (aka derived from debian) ubuntu linux, and yet there is no ubuntu linux version of the software.

go figure

Not quite mate. Shuttleworth has nothing to do with Google...

[http://en.wikipedia.org/wiki/Mark_Shuttleworth]("http://en.wikipedia.org/wiki/Mark_Shuttleworth")

---

