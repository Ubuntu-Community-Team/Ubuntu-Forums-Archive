---
title: "How do I install programs?"
date: 2006-04-08
forum: Absolute Beginner Talk
---

### Post by jerryrowe on 2006-04-08
Hello, Ubuntu community!

I installed Ubuntu a few minutes ago, and I now see why people love Linux so much.

Unfortunately, I have no blasted clue how to install a Dreamwaver-equivalent program on Linux.

On Windows, it was easy: you get a gigantic install file, double-click it, and *poof!* the program is installed.  

What in the world do I do?  What kind of file(s) do I even download?  I don't even know where to start, and I looked on the Ubuntu Wiki, Google, and other places.

Help!

Thanks!

jerry

---

### Post by OldSchool on 2006-04-08
For a Dreamwaver-equivalent you could try [Quanta.]("http://quanta.kdewebdev.org/") Either use "Add Applications" under the "Applications" menu or type

> sudo apt-get install quanta

in a terminal window

---

### Post by dermotti on 2006-04-08
Or open synaptic

---

### Post by jerryrowe on 2006-04-09
Okay, I went to "Applications > Add Applications" and hit "Advanced," and then did a search for Quanta.  But its description said it was for the KDE, and I thought the KDE and the GNOME environments were different (as in, incompatible).  

Is that how I am supposed to install any program, though?  I went to download NVU, and got a file type I have never seen before... a *.tar.bz2 file.  What in the world do I do with that?

I appreciate the advice to go look at Quanta, and I will likely try it out.  But for future reference, what do I do with these tar.bz2 files?

Thanks again!

jerry

---

### Post by bionnaki on 2006-04-09
[http://www.psychocats.net/linux/installingsoftware.php](http://www.psychocats.net/linux/installingsoftware.php)

---

### Post by bionnaki on 2006-04-09
all you have to do is

> sudo apt-get install nvu

---

### Post by trent dillman on 2006-04-09
.tar.gz files are like .zip files, usually with source code to create programs.

---

### Post by jerryrowe on 2006-04-09
Oh, okay.  I looked in the .tar.gz2 file, and unpacked it, but is there anything in there I should mess with?  I tried just double-clicking the install and installsh files, but no install / installshield -like thing appeared.

Also, I went to the command line under Applications > Accessories, and I typed this:

```
sudo apt-get update
```

...and it updated.  Yay!  I had no idea this was anything I needed to do.

Then, I typed:

```
sudo apt-get install nvu
```

...just like you said.  What was weird was it replied with: 

```
E: Couldn't find package nvu
```


Then I thought: Hey, I could install from source!  So I did what you said to do on that link you gave me [(here]("http://www.psychocats.net/linux/installingsoftware.php")), and followed the directions.

1. I downloaded the *.tar.bz2 file.
2. I did the "sudo apt-get install build-essential" step, and it updated. Yay!
3. I renamed the file "obscure.tar.bz2" because the filename was about 40 characters long and it seemed easier to do it this way.
4. In the command line, I typed "tar -xvzf obscure.tar.bz2"
5. I got an error message: "Cannot open: No such file or directory."

So what should I do now?  Thanks, by the way, yet again.  Using the command line is obviously super efficient, and I can't wait to really "get it" mentally, but I am afraid I'm just not there yet, since it isn't working like I think it should.

What step am I missing here?  NVU *is* supported by Ubuntu, right?

Thanks again!  This is making my journey into LinuxLand much better; I've already gotten a couple of people interested in it, too. 

jerry

---

### Post by aysiu on 2006-04-09
You need [extra repositories enabled](http://www.psychocats.net/ubuntu/sources) in order to install Nvu via apt-get. I would recommend Quanta, though, and that doesn't need extra repositories.

If you prefer to install things graphically, check this out:
[http://www.psychocats.net/essays/winuxinstall](http://www.psychocats.net/essays/winuxinstall)

---

### Post by jerryrowe on 2006-04-09
Okay, even stranger:

Just out of curiosity, I tried to install Mozilla Thunderbird from the command line using apt-get.  Woot!  Success!  This is amazing.  Yay for Linux!  I am sold.

But why in the world won't it get NVU?  Does Ubuntu suddenly not like it, or what?

Thanks a ton, again!

---

### Post by jerryrowe on 2006-04-09
Sweet!  I installed Quanta, since everyone's recommending it so much.

Thanks for letting me know it was just an extra-repository issue!

One question though:  What is this about KDE and GNOME being incompatible?  Did I misread something when I was reading about Linux?  I thought KDE programs and GNOME programs were like Windows and Mac programs: you can't run one on the other.  What was it that I was misunderstanding?

Thanks again!  Man, this sure is a great community.  Answers with no mockery over being new to the program.

jerry

---

### Post by aysiu on 2006-04-09
[QUOTE=jerryrowe]
One question though:  What is this about KDE and GNOME being incompatible?  Did I misread something when I was reading about Linux?  I thought KDE programs and GNOME programs were like Windows and Mac programs: you can't run one on the other.  What was it that I was misunderstanding?[/QUOTE] You can run Gnome programs in KDE and vice versa. They may load more slowly, but they work.

---

