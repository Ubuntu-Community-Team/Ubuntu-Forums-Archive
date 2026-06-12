---
title: "Newb Ubuntu installation question"
date: 2007-12-29
forum: Absolute Beginner Talk
---

### Post by Hypnotik on 2007-12-29
Hello everyone.  I'm trying to install Ubuntu for the first time.  I followed the instructions for downloading and burning to a disc.  When I attempt to boot from the cd I get through the first few questions, then I get an error.  The error says that the cd is not for installation.  Those aren't exact words but it's something like that.  

Any suggestions??

Thanks for looking,

Jeff

---

### Post by taurus on 2007-12-29
Which file did you download and where did you download it?

[http://www.ubuntu.com/getubuntu/download](http://www.ubuntu.com/getubuntu/download)

---

### Post by SidewinderPro2 on 2007-12-29
After rebooting with the disk, a menu should come up with different choices on it. The first one is something along the lines of "Install and Use". There are other options below it, but highlight the first one and press enter. From there it should take you to the Ubuntu desktop. If that doesn't work I think you're going to need to use the alternate CD for installation, but get a second opinion on that.

Did you burn the .iso the correct way? You didn't just save the .iso onto a disk as simply 1 file did you?

---

### Post by Hypnotik on 2007-12-29
I downloaded from the ubuntu website, version 6.06.1 server edition.

The first time I burned the cd it was all one file.  On my second try I used the InfraRecorder and now the cd has a few different file folders and a few loose files.

Should I download one of the other versions?

Jeff

---

### Post by g7kse on 2007-12-29
I'd suggest the 7.10 Ubuntu version from ubuntu.com, unless you're after a server version

---

### Post by Hypnotik on 2007-12-29
The exact error message is: 

[!]Detect and mount cd-rom
Incorrect cd-rom detected
the cd-rom drive contains a cd which cannot be used for installation.

please insert a suitable cd to continue with the installation.


Thanks for the help

Jeff

---

### Post by g7kse on 2007-12-29
sounds like it didn't get burnt as an image. did you just copy it stright onto a disk or burn image?

---

### Post by Hypnotik on 2007-12-29
It's an image.  I used the InfraRecorder.  When I double click the cd I have a bunch of folders and loose files.  I also used the md5 utility to check and it said the checksums matched.  I think I'll download 7.10 server and try to reburn it again. 


Jeff

---

### Post by g7kse on 2007-12-29
If you're still having problems and I hope not you know where to come

---

### Post by Hypnotik on 2007-12-29
Absolutely.....seems like a very helpful community, it's not all that often you find that type of thing.

Stay tuned....heh I'll probably be back.


Jeff

---

### Post by Hypnotik on 2007-12-29
In infrarecorder, does the write method matter?  The options are:

session-at-once
track-at-once
tao with zerogap
and
3 different raw writing options


I believe the first time I used SAO.

Is that right?

Jeff

---

### Post by ugm6hr on 2007-12-29
> **Hypnotik said:**
> I believe the first time I used SAO.

Is that right?

Yes. That will close the CD (so you won't be able to add any further files).

---

### Post by Hypnotik on 2007-12-29
Things seem to be working with version 7.10.  Working on the partition now.  We'll see how it goes, i'm bound to run into another problem.

Thanks for the help

Jeff

---

### Post by Hypnotik on 2007-12-29
Heh I knew I'd be back.


So my current harddrive is 41 gb (i plan on using ext hd's and all that), I partitioned 25 gb to Ubuntu.  When I click to make changes i receive the message "No root file defined, please correct"  

Well....I don't know how to correct the problem.


Jeff

---

### Post by ugm6hr on 2007-12-29
In the partitioning screen - you need to create at least 1 ext3 partition with a *mount point* **/** (aka root) and 1 swap partition (recommend 1.5-2 times RAM, max 700MB).

See the explanation at the bottom of the list of partitions.

This might help: [http://www.psychocats.net/ubuntu/installing](http://www.psychocats.net/ubuntu/installing)

[IMG]http://img379.imageshack.us/my.php?image=feistydual10ea7.png[/IMG]

---

### Post by Hypnotik on 2007-12-29
Ok...well everything seems to have worked.

I'm now at the username@ubuntu prompt.  I read through one of the guidelines on this site and explains what all the symbols mean....but not actually what to do at this prompt.

Any help would be great.

Jeff

---

### Post by JoshuaRL on 2007-12-29
That would be the username and password that you created in the install.  That's how you log into Ubuntu.

I just want to make sure you understand that the server version is headless (No GUI).

Normal Ubuntu is the one you need if you want a desktop OS.  But I'm really not trying to be insulting if it came across as that.

---

### Post by ugm6hr on 2007-12-30
@Hypnotik:
Are you talking about Terminal (see the link below about Code entries), or do you just get a black screen with text when you boot up (you have either done a Server install, or there is a problem with graphics card driver)?

---

### Post by Hypnotik on 2007-12-30
I didn't know that the server edition didn't have GUI.  When I was asked what I wanted to install, I installed the LAMP, and the two databases (MySQL, and PreGre i think it was), and a couple other things.

When the computer loads I definately have stuff on the screen.  I went through the part where I enter my username and password, now I have a prompt that is *username*@ubuntu then a couple symbols.  I'm assuming that's the terminal.

So just to clarify, with version 7.10 server does not have GUI?  It's all CLI?

Thanks,
Jeff

---

### Post by ugm6hr on 2007-12-30
> **Hypnotik said:**
> So just to clarify, with version 7.10 server does not have GUI?  It's all CLI?


Yes.  You can add a GUI though.  Although most people just install the "desktop version" directly.  The differences are briefly explained here: [http://www.ubuntu.com/](http://www.ubuntu.com/)

To add GUI:
```
sudo aptitude update
sudo aptitude install ubuntu-desktop
```

This will add the full desktop suite.  However, I think this will download from the internet, so it may be better to just re-install the desktop version from the CD.

---

### Post by Hypnotik on 2007-12-30
Well and that's the problem.  I attempted to enter a couple commands, including the ones you posted and the message I get is:

fatal: open /etc/postfix/main.cf: no such file or directory.  Jeff is not in the sudoers file.

Then it takes me back to the jeff@ubuntu:~$ prompt.


Thanks.

Jeff

---

### Post by slibuntu on 2007-12-30
Just to be clear, what exactly are you looking for here? A server or a normal operating system?

---

### Post by Hypnotik on 2007-12-30
Heh.  Originally I wanted to set up a server, rip my cds, so that I can access the music when I am in the computer lab at school.  It was recommended to me by one of the CSI instructors to use Ubuntu.  I have seen the Ubuntu OS on a couple of the computers in our server room.  I guess I assumed that by installing the server edition, I would the use of the server and the GUI OS.  Am I incorrect?  I guess maybe I should install the OS and get used to the way things work then try the server.

I really have read alot of the info on ubuntu's website....it just seems like the problems that I'm encountering aren't listed anywhere.

Thanks again for the help.

Jeff

---

### Post by slibuntu on 2007-12-30
Well I'm not really sure how to help you to be honest, but now that we know what you're at, somone will come along and help you!

---

