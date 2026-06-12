---
title: "A couple of newb questions"
date: 2006-10-10
forum: Absolute Beginner Talk
---

### Post by timmins on 2006-10-10
Hi guys, three really basic questions. Your help is appreciated.

1, I am having trouble installing Mplayer, I am attempting to follow instructions seen here: [http://www.linux.com/article.pl?sid=04/07/01/1940236](http://www.linux.com/article.pl?sid=04/07/01/1940236)
The part I'm having trouble with is here: 

"To install MPlayer from source code, download the code tarball. Extract the files into a temporary directory. Change to the directory into which you downloaded the files and enter the following commands:

./configure --enable-gui
make
su (if you're not already root)
make install "

I'm not sure where to "enter the following command", I have the temp folder in front of me in a window, where do I put the commands, in the terminal?



2. how do I set up video out from my video card (I can find the specs if you need em), I simply have a AV cable from my card to my TV.



3. I am not receiveing emails from ebay into my newly set up evolution client, all other emails work, just not ones affiliated with ebay.


Thanks alot.

-Kyle

---

### Post by Boatswain on 2006-10-11
Hi Kyle.  I'll answer the one that I can and leave the rest to people who know a lot more than me:

> **timmins said:**
> 
I'm not sure where to "enter the following command", I have the temp folder in front of me in a window, where do I put the commands, in the terminal?

-Kyle

Yes, you need to enter the commands into the terminal, but you need to make sure you're in the right place when you do it.  That is, if you've downloaded the file into /home/kyle/newdir you'll need to open the terminal (which will start you at /home/kyle {assuming your user name is kyle} and type in "cd newdir", then execute the commands.

Best of luck with the rest!

Tom

---

### Post by timmins on 2006-10-11
thanks for the reply
I'll give that a try
maybe It'll fly
:p

---

### Post by pstep9407 on 2006-10-11
Another option, Kyle, that will leave you wondering why in the world anyone ever uses ____ operating system, is to use apt-get. I noticed that Ubuntu does have a binary of mplayer in the repository. This means that you don't have to compile it, which is prone to error, and takes time. So, if you're ready to make your life easy, either find and open synaptic (under system administration) or just open your new friend, the Terminal, and issue the following commands:
```
sudo apt-get install mplayer
```
You'll be shown a slew of other packages that mplayer *depends* on, and asked if you want to continue, the default answer being Yes. Give it a go, and good luck!

---

### Post by timmins on 2006-10-11
you're a genious, it worked. now, how do I add codec support? both audio and video?

---

### Post by timmins on 2006-10-11
I've downloaded the codecs, now what pls?

---

### Post by timmins on 2006-10-11
any more ideas?

---

### Post by Perfect Storm on 2006-10-11
You might to check this site: [https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats) for codecs etc.

---

### Post by encompass on 2006-10-11
[https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)
Try these instructions... be sure to read threw the forums before posting questions.  This is suck a common question they have an entire webpage devoted to it. Good luck.
(beat to the punch... man is AI quick.)

---

### Post by timmins on 2006-10-11
thanks guys, I'll get into this tomorrow when I have more time. Do you have any ideas in regards to the two other questions I asked at the top of the page.

-Kyle

---

### Post by encompass on 2006-10-11
For question two... I will need the specs... it really depends on your card.  The more details you can give the better.
And 3? Double check your settings an dtalk to them if it is setup correctly.

---

### Post by timmins on 2006-10-11
ok, I'll find out the specs

---

