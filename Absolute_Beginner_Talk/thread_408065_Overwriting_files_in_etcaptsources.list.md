---
title: "Overwriting files in /etc/apt/sources.list"
date: 2007-04-12
forum: Absolute Beginner Talk
---

### Post by t2000kw on 2007-04-12
I was trying to follow some instructions on how to write to a write-protected file. I am using Xubuntu. I will post my printer question separately but was trying to follow the instructions here, which require modifying a text file and entering a command that doesn't seem to do anything:

[http://mambo.kuhp.kyoto-u.ac.jp/~takushi/#canon](http://mambo.kuhp.kyoto-u.ac.jp/~takushi/#canon)

I tried to add the following line to etc/apt/sources.list:

deb [http://mambo.kuhp.kyoto-u.ac.jp/~takushi/ubuntu](http://mambo.kuhp.kyoto-u.ac.jp/~takushi/ubuntu) ./

which I got an error message that the file is write protected. I can't find out how to disable the write protection. 

I also tried to run this command in terminal but nothing appeared to ahppen. I expected an error since I wasn't able to add the above line to the sources.list file.

deb [http://mambo.kuhp.kyoto-u.ac.jp/~takushi/ubuntu](http://mambo.kuhp.kyoto-u.ac.jp/~takushi/ubuntu) ./

I am able to log in as superuser in terminal but that doesn't change anything in the GUI. I cannot seem to log in at the beginning GUI login screen as SU with my password. 

I got to get started here before I can figure out how to add a workable printer driver for my Canon i850 printer. I can get the supplied drivers (using one for the BJC-6000) to print on about 1/4 of the page using the proper "letter" size chosen under paper size, and I can fiddle with different settings to get it to print over more of the page, by changing the dpi setting and the paper size, but still not over the full page (or it's too big and goes way beyond the borders). 

But first, let's tackle writing to a write protected file. 

Thanks!!!

---

### Post by taurus on 2007-04-12
Open a terminal and type

```
gksudo mousepad /etc/apt/sources.list
```

---

### Post by Gazneth on 2007-04-12
Try this but be very careful editing sources manually you can break apt-get. I've done it myself.    
```
sudo gedit /etc/apt/sources.list
```
Good luck:D

---

### Post by t2000kw on 2007-04-12
Thanks, both of you. It saved without a problem.

A couple of questions. I did log in as superuser in case it would give me problems. Did I have to do that?

Now, how do I get the command to run:

# apt-get install libcnbj-2.2 bjfilter-2.2 pstocanonbj

It does nothing. I'm assuming, of course, that this will really work.

---

### Post by tonyr1988 on 2007-04-12
You didn't need to log in as superuser. The "sudo" allows you to have temporary superuser (root) access.

Try "apt-get install libcnbj-2.2 bjfilter-2.2 pstocanonbj" (if you're not superuser)

It should say something. What's it telling you?

---

### Post by taurus on 2007-04-12
What happens if you run these two commands from a terminal?

```
sudo aptitude update
sudo aptitude install libcnbj-2.2 bjfilter-2.2 pstocanonbj
```

---

### Post by Malakia on 2007-04-12
You need to add sudo in front of the apt-get and you need to do this to

```
sudo apt-get update
```
```
sudo aptitude install libcnbj-2.2 bjfilter-2.2 pstocanonbj
```

Then it should work.

---

### Post by t2000kw on 2007-04-12
> **taurus said:**
> What happens if you run these two commands from a terminal?

```
sudo aptitude update
sudo aptitude install libcnbj-2.2 bjfilter-2.2 pstocanonbj
```

That did something. Let me look over the instructions some more and see what I can come up with from here. I can always come back to this and add to the post.

Thanks so far!!!

Donald

---

### Post by t2000kw on 2007-04-12
It's working now--sort of. I don't have the high resolution native to the printer (I think it's 1440 x 720) but I do get 600 x 600 dpi. It's better than nothing. If I need better resolution, I cna always go back to Windows, once I fix it's problem of surprise reboots (Windows reports a driver crashing the computer, so I plan to wipe out the Windows directory and reinstall Windows, then the apps I use the most often and keep it as clean as possible after that.

Thanks very much.

Next problem to tackle is using Wine with a particular email program, but I'll put that in a separate post. I already have made some progress in that direction. That will sell my wife on Linux, I think. Got Wine installed and it loads the program but there's a file missing. Windows doesn't care about the missing file but Wine does.  I'll reinstall the Windows program and see if the missing file takes care of itself before I ask for further help.

---

### Post by tonyr1988 on 2007-04-13
Like you said, that would probably belong best in another post (your wine + e-mail issue), but real quick: have you tried going to [http://appdb.winehq.com/](http://appdb.winehq.com/) and looking for the program? They usually have instructions on getting it to work properly.

---

### Post by t2000kw on 2007-04-13
I'll try that, thanks!

---

### Post by t2000kw on 2007-04-13
> **tonyr1988 said:**
> Like you said, that would probably belong best in another post (your wine + e-mail issue), but real quick: have you tried going to [http://appdb.winehq.com/](http://appdb.winehq.com/) and looking for the program? They usually have instructions on getting it to work properly.

I went there this morning. The program, Agent, an email and newsgroup reader, is not
 listed. It's not a surprise, as it has a very limited commercial distribution. Possibly a few thousand at most. On the other hand, it's not the target of hackers for that reason, and I like it that way. 

I do have Thunderbird working just fine--I just don't like it near as much. Agent has some very advanced scripting built into it, has a very good Bayesian junk filter, and other nice features. And it's the only one my wife wants to use. 

I've noticed an irritating thing about this board. When the important part of the page has loaded, with all of the messages on the page, I'll scroll down to where I want to read or reply to and the page, still loading images, will push what I'm looking at down out of sight. 

My fix for now is to just wait until the text is loaded and click on the stop button in my browser. If I end up needing something that hasn't loaded yet, I'll click refresh.

---

