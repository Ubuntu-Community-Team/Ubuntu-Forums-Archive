---
title: "Linux Usenet Binary Auto Poster??"
date: 2007-08-27
forum: Absolute Beginner Talk
---

### Post by chrome307 on 2007-08-27
I regularly use Newsgroups and since my move over to Ubuntu I'm missing the use of these great piece of freeware

**[COLOR="Red"]Yenc Power Post A&A 11b[/COLOR]**

[img]http://alt.bin.justforgaurav.com/filesqueuedinpowerpost.png[/img]

Can anyone recommend me a program similar to this for Ubuntu ??

---

### Post by Cypher on 2007-08-27
Torrents..

---

### Post by Terl on 2007-08-27
Have you tried PAN?  It is a little like Agent.  It works for what it looks like you want to do.

---

### Post by chrome307 on 2007-08-27
Terl .... I just need it to Post Binaries to NewsGroups ..... for downloading I'm using KLibido.

I've visited the PAN Newsreader homepage and they do not mention the ability to post articles (Binaries).

Are you using this yourself?

---

### Post by XTREEM|RAGE on 2007-08-29
> **chrome307 said:**
> Terl .... I just need it to Post Binaries to NewsGroups ..... for downloading I'm using KLibido.

I've visited the PAN Newsreader homepage and they do not mention the ability to post articles (Binaries).

Are you using this yourself?

With pan you can post, atleast i have seen that option. Not used the post option myself (yet).
Btw cant u use that program in wine?

---

### Post by chrome307 on 2007-08-29
Unfortunately the program I mention does not work within WINE or with CrossOver.

PAN cannot as yet post Binary attachments :(

---

### Post by Devils2day on 2007-08-31
Hello,

I am quite new with linux and i also used to work with yenc powerpost ( mostly dutch version camelsystem).

In linux i had the same problems, but after 5 days being a die hard (ahum...), i found out there is a bug (i think) in knewspost.

What i did: i used newspost from the commandline and it posted perfectly.
I hope there will come a new version of knewspost and it help us out.

I hope it helped you a bit.

Greetings Devils2day

---

### Post by chrome307 on 2007-08-31
Looking at SourceForge this application has not been updated in 6 years :(

Can you let me know how you got it to work via the command line?

---

### Post by antharr on 2007-08-31
> **chrome307 said:**
> Terl .... I just need it to Post Binaries to NewsGroups ..... for downloading I'm **using KLibido.**

I've visited the PAN Newsreader homepage and they do not mention the ability to post articles (Binaries).

Are you using this yourself?

Do you know of any good tutorials on using Klibido for downloading binaries. I want to use Usenet access to find files but it has been a headache trying to get anything to work. Thanks

---

### Post by chrome307 on 2007-08-31
I use KLibido daily to download NZB's and PyPAR2 to verfiy/repair the downloads if needed.

What problems are you having??

---

### Post by antharr on 2007-09-01
I just have no idea have to configure it. Just need a basic tutorial on how to get started.

---

### Post by chrome307 on 2007-09-01
Do you have access to a News Server?

If so, once you have entered in your login details, you simply have to click on FILE --> Download NZB and then locate your NZB on your PC.

It should begin downloading to the 'specified' folder

I only use it to download binaries and that works for me ......... what else did you need to know??

---

### Post by sanskritter on 2007-10-28
Hey, I don't know if anyone is still following this thread, but posting with newspost is actually very simple, here are some examples taken from the man page

EXAMPLES


Save your news server, e-mail address, and name as default:
             newspost -d -i news.myisp.com -f [email]newspost@sdf.lonestar.org[/email] -F
              'Your Name'

Post some files to alt.binaries.test:
              newspost -n alt.binaries.test -s 'Here are some songs'
              /nfs/music/*.mp3

       A subject line from the above post may look like this:
              Here are some songs - track01.mp3 (01/15)
 
Post some files to alt.binaries.test.yenc using yencoding:
              newspost -y -n alt.binaries.test.yenc -s 'Here are some more
              songs' /nfs/music/*.mp3

       A subject line from the above post may look like this:
              Here are some more songs - "track01.mp3" yEnc (01/12)

Include "File x of y" in the subject:
              newspost -q -y -n alt.binaries.test.yenc -s 'Here are some
              more songs' track01.mp3 track02.mp3 track03.mp3

       A subject line from the above post may look like this:
              Here are some more songs - File 1 of 3: "track01.mp3" yEnc
              (01/12)

etc etc

I usually create par2 files first using par2 like this: 
par2 create -s107200 -r55 /path/file.mp3
read the manual to understand the options: man par2
... and then when the parity files are done post everything with wildcards, like this:
 newspost -y -n alt.binaries.test -s 'Your header here' /nfs/music/file.mp3*
the asterisk tells newspost to post everything beginning with file.mp3, which will include your par files.
If you REALLY don't want to take you first tentative steps to becoming a command line hero, and why don't you? Then here is an RPM for knewspost (buggy I'm told)

[http://rpmfind.net/linux/RPM/sourceforge/k/kn/knewspost/knewspost-0.8-1.i386.html](http://rpmfind.net/linux/RPM/sourceforge/k/kn/knewspost/knewspost-0.8-1.i386.html)

once downloaded you can use alien to debianise it, like this
sudo alien /path/knewspost-0.8-1.i386.rpm 
which will create a .deb package file which you can install as normal using dpkg or whatever gui association you have by clicking on it.
hope this helps.
S

*note
knewspost won't work unless you have a fairly old system ... so you'll have to work on the command line
which is fast, powerful and strangely satisfying!

---

