---
title: "Devede questions and performance!"
date: 2008-04-01
forum: Absolute Beginner Talk
---

### Post by darkerlink on 2008-04-01
I was a former windows XP user (about 3 days ago). So usually, when I want to make a DVD, I use ConvertXtoDVD and DVDShrink to first convert the AVI file to .VOB files/folder and then I would use DVDShrink to convert those folders into one ISO file. This process usually takes about 1 hours and 30 minutes.

I found out that I couldn't use ConvertXtoDVD even with WINE(the file location gets messed up or something) I decided to try out Devede from the add/remove programs list. One thing that I did notice, sadly, that it took about 2 hours and a couple of minutes to do a job and make the ISO. Considerably longer than what I am used to. I've also notice that Devede converts my AVI to MPG for some reason. I think this conversion process adds to the longer time frame. Also, when I checkmark the option to delete temp files after the iso/cue is completed, the MPG and a .XML file still remains in the directory. The MPG added with the completed ISO takes up what is suppose to be twice the intended space.

So my questions are: Why does Devede convert the AVI to MPG in order to make the ISO? Why doesn't Devede delete that MPG after the ISO is created even when I have checked the option to delete the temp files. 

While Benchmarking Devede, I unchecked the option of "Trillus searched Quantization" and I selected the option of "Use MBCMP (faster)".

Overall, the program is easy to use. These things are really frustrating me though since I have many movies to make and the extra time really does add up.

---

### Post by joshrobinson on 2008-04-01
i had horrible audio sync problems with devede, so i dont use it.

a vob file is pretty much an mpeg2 file
so it has to convert the avi, into an mpg file, then turn the mpg into vob's

your windows programs were doing this also, you just never noticed because it must have hid the files

why it wont delete the tmp files, i have no idea.. have you tried tovid? thats what i use to make my dvd's

```
sudo apt-get install tovidgui
```

---

### Post by darkerlink on 2008-04-01
I would like to try Tovid now that you mention it. However I am a complete NOOB with Ubuntu and linux altogether. I copied and pasted that string into terminal and got

"[sudo] password for set:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package tovidgui"

Did I missspell something or am I suppose to type that string somewhere else?

---

### Post by joshrobinson on 2008-04-01
go to system > administration > synaptic package manager
click settings, then repositories
on the ubuntu software tab, make sure there is a check next to: main universe restricted multiverse

on the third party software tab, make sure the first one is checked
click close, then click reload on synaptic
click search, and type tovidgui
and see if it comes up with a result

---

### Post by darkerlink on 2008-04-01
I found Tovidgui but when I tried to mark for installation, I got a prompt about dependacies and things that needed to be "uninstalled"? Ehh, im not to fond of the hassle right now. Thanks anyways! you're the only one that replied to my questions :( I'd rather keep this Devede program for now. I love Ubuntu so far and I don't want to mess anything up by doing things I am not familiar with. Also, not that it may matter now, I checked all the parameters but main universe restricted multiverse was not listed. I am running 7.10. If anyone can answer my original questions feel free :)

---

### Post by mridkash on 2008-04-01
Get the latest devede package (.deb file) from [http://getdeb.net](http://getdeb.net) search for devede. The version in add remove is old.

Yes, it takes too much time. But nearly all open source video etc software depend on a software called mencoder to do all encoding stuff. The slowness can be attributed to that. On my pentium 4 pc a full sized dvd from 4 source videos in avi format, take about 3 hrs. I don't think the time used for encoding will vary with software, whether you use tovid or devede unless it depends upon some other encoder. 

Try kdenlive software, also in add remove.

---

### Post by darkerlink on 2008-04-01
I upgraded to the 3.6 version and it now deletes the temp files! thanks. Speed went down a bit, now just under 2 hours 1 hr 50 min clocked.

---

### Post by digger95 on 2008-04-20
Convertxtodvd does in fact work very well under wine.  The only thing you don't get is video preview during the encoding process.  I tried devede several times on my machine (I really wanted a Linux solution) but the output was not the best and the discs were oftentimes unreadable by my standalone.

---

